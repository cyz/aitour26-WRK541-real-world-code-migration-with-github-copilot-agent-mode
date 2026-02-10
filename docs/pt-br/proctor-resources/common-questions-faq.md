# Perguntas comuns dos participantes - FAQ para proctors

Este documento fornece aos proctors respostas prontas para perguntas frequentes durante o workshop. Use como referencia rapida para fornecer respostas consistentes e uteis aos participantes.

## Perguntas sobre GitHub Copilot

### P: "Por que o Copilot nao esta sugerindo nada?"

**Verificacao rapida:**
- O Copilot esta habilitado no VS Code? (procure o icone do Copilot na barra de status)
- O arquivo esta salvo? O Copilot funciona melhor com arquivos salvos
- Ha contexto suficiente? Abra arquivos relevantes ou use referencias `#file:`

**Etapas de troubleshooting:**
1. Verifique se o Copilot esta ativo (o icone nao deve mostrar erro)
2. Verifique o modelo selecionado - tente mudar para outro modelo
3. Recarregue a janela do VS Code (`Ctrl+Shift+P` → "Reload Window")
4. Verifique a conexao com a internet
5. Saia e entre novamente na conta GitHub

**Resposta para dar:**
"Vamos checar algumas coisas. Primeiro, voce consegue ver o icone do Copilot na barra de status? Vamos garantir que seu arquivo esteja salvo e tentar fornecer mais contexto usando referencias #file: no prompt."

---

### P: "Posso usar um modelo diferente? Qual e o melhor?"

**Resposta:**
"Sim! O GitHub Copilot suporta varios modelos. Para este workshop, testamos com GPT-4o-mini, mas voce pode experimentar outros modelos como Claude ou Gemini. Modelos diferentes podem dar sugestoes diferentes - nao existe um unico 'melhor' modelo, mas o GPT-4o tende a ser mais preciso para tarefas complexas enquanto o GPT-4o-mini e mais rapido."

**Como trocar:**
- Clique no nome do modelo no Copilot Chat
- Selecione entre os modelos disponiveis
- Tente um modelo diferente se as sugestoes nao estiverem ajudando

---

### P: "Agent Mode e 'cola'? Nao deveria eu mesmo escrever o codigo?"

**Resposta:**
"Otima pergunta! O Agent Mode nao e cola - e uma ferramenta que simula como voce trabalharia com um dev senior. O aprendizado acontece em:

- Entender o que pedir
- Validar o codigo gerado
- Debugar quando algo nao funciona
- Decidir quando confiar vs verificar

Pense nisso como pair programming com IA. Voce ainda toma todas as decisoes importantes e aprende padroes que pode aplicar depois."

---

### P: "A sugestao do Copilot nao corresponde as instrucoes. O que devo fazer?"

**Resposta:**
"Esse e um otimo momento de aprendizado! Lembre-se:

1. **Verifique primeiro**: Compare a saida do Copilot com o comportamento esperado
2. **Refine seu prompt**: Seja mais especifico sobre o que voce quer
3. **Itere**: Dê feedback ao Copilot e peça ajustes
4. **Use validacao**: Execute os testes para verificar a corretude

As sugestoes da IA nem sempre sao perfeitas. Aprender quando aceitar, modificar ou rejeitar sugestoes e uma habilidade valiosa."

---

## Perguntas sobre testes

### P: "Meus testes falharam mas eu fiz exatamente o que o Copilot disse. E agora?"

**Guia de troubleshooting:**

1. **Verifique se o app esta em execucao:**
   - Os testes Python exigem que o app esteja rodando primeiro
   - Verifique: `curl http://localhost:8000` deve retornar uma resposta

2. **Verifique a porta:**
   - O app Python roda na porta 8000
   - O app C# tambem deve rodar na porta 8000 para compatibilidade dos testes
   - Use `--urls "http://localhost:8000"` ao rodar o app C#

3. **Verifique a variavel de ambiente BASE_URL:**
   - Windows: `$env:BASE_URL="http://localhost:8000"`
   - Linux/Mac: `export BASE_URL="http://localhost:8000"`

4. **Revise a saida dos testes:**
   - Veja a assercao especifica que falhou
   - Compare valores esperados vs reais
   - Peça ao Copilot sobre a mensagem de erro especifica

**Resposta para dar:**
"Vamos debugar isso juntos. Primeiro, seu app esta rodando? Deixe-me ver a saida do teste para entender exatamente o que falhou."

---

### P: "Posso usar um framework de testes diferente? Prefiro xUnit/NUnit."

**Resposta:**
"Sim, voce pode usar xUnit ou NUnit se preferir! No entanto, para validar a migracao, voce **deve** manter os testes Python funcionando, pois eles verificam a compatibilidade da API. Os testes C# (MSTest, xUnit ou NUnit) sao opcionais. Os testes Python sao sua 'fonte da verdade' para corretude."

---

### P: "Preciso escrever testes para todos os endpoints?"

**Resposta:**
"Os testes Python ja testam todos os endpoints via requisicoes HTTP. Para o workshop:

- **Obrigatorio**: Manter os testes Python passando (eles validam sua migracao C#)
- **Opcional**: Adicionar testes unitarios em C# (boa pratica, mas nao obrigatorio para concluir)

Se voce terminar cedo, adicionar testes C# e um otimo Desafio!"

---

## Perguntas sobre ambiente e setup

### P: "Devo usar Codespaces ou desenvolvimento local?"

**Resposta:**
"Recomendamos GitHub Codespaces para este workshop porque:

- ✅ Zero setup - tudo ja vem pre-configurado
- ✅ Ambiente consistente para todos
- ✅ Funciona em qualquer dispositivo com navegador
- ✅ Nao precisa instalar nada

Desenvolvimento local e ok se voce ja tem Python 3.12 e .NET 10 SDK instalados e funcionando."

---

### P: "Meu Codespace esta lento/travado. O que faco?"

**Solucoes imediatas:**

1. **Recarregue a pagina** - muitas vezes resolve problemas temporarios
2. **Pare e reinicie o Codespace** - pela pagina do GitHub Codespaces
3. **Crie um novo Codespace** - ultimo recurso, mas efetivo

**Dicas preventivas:**
- Feche abas de navegador nao usadas
- Pare processos em execucao quando nao precisar
- Use `Ctrl+C` para parar servidores

**Resposta para dar:**
"Vamos tentar recarregar a pagina primeiro. Se isso nao ajudar, podemos reiniciar seu Codespace."

---

### P: "A porta 8000 ja esta em uso. Como resolver?"

**Solucoes:**

**Windows PowerShell:**
```powershell
# Encontrar processo
Get-NetTCPConnection -LocalPort 8000

# Finalizar processo (substitua PID)
Stop-Process -Id <PID> -Force
```

**Linux/Mac:**
```bash
# Encontrar processo
lsof -i :8000

# Finalizar processo
kill -9 <PID>
```

**Ou use outra porta:**
```bash
# Python
uvicorn main:app --port 8001

# C#
dotnet run --urls "http://localhost:8001"
```

**Resposta para dar:**
"Vamos encontrar o que esta usando a porta 8000 e parar. Ou podemos usar outra porta - so lembre de atualizar a variavel BASE_URL para os testes."

---

## Perguntas sobre migracao de codigo

### P: "Como sei qual modo do Copilot usar?"

**Guia de decisao rapida:**

| Tarefa | Modo | Por que |
|------|------|-----|
| "O que este codigo faz?" | **Ask** | Apenas aprendizagem, sem mudancas |
| "Adicione tratamento de erro nesta funcao" | **Edit** | Mudanca unica e direcionada |
| "Crie o scaffolding em C#" | **Agent** | Tarefa em varias etapas com comandos |
| "Qual o plano de migracao?" | **Plan** | Estrategia antes da implementacao |

**Resposta para dar:**
"Use Ask para perguntas, Edit para pequenas mudancas, Agent para tarefas em varias etapas e Plan quando voce precisa pensar na abordagem antes."

---

### P: "Posso migrar para outra linguagem em vez de C#?"

**Resposta:**
"O workshop foi desenhado especificamente para migracao de Python para C#. No entanto, as tecnicas que voce aprende (migracao incremental, validacao orientada a testes, uso de ferramentas de IA) se aplicam a qualquer migracao de linguagem. Depois do workshop, voce pode aplicar esses padroes para migrar para Java, Go, Rust ou qualquer linguagem que preferir!"

---

### P: "Por que estamos mantendo os testes Python em vez de reescreve-los em C#?"

**Resposta:**
"Otima pergunta! Os testes Python servem como nossa 'fonte da verdade' porque:

1. **Eles testam a implementacao original funcionando**
2. **Eles validam o comportamento HTTP** (o que os usuarios realmente veem)
3. **Eles comprovam que a nova API e compativel** com a original
4. **Independentes de linguagem** - eles funcionam para qualquer implementacao

Esse e um padrao real: usar os testes originais para validar uma reescrita."

---

## Referencias de arquivo do GitHub Copilot

### P: "O que significa #file: nos prompts?"

**Resposta:**
"A sintaxe `#file:` indica ao Copilot qual arquivo especifico voce esta usando. Veja como:

1. Digite `#` no chat do Copilot
2. Aparece um seletor de arquivos
3. Selecione o arquivo (como `Program.cs`)
4. Em seguida, digite o restante do prompt

Isso da ao Copilot um contexto importante sobre a estrutura do seu codigo."

**Demo:**
Mostre: digitar `#` → selecionar arquivo → adicionar prompt

---

### P: "Preciso usar #file: toda vez?"

**Resposta:**
"Nem sempre! Use `#file:` quando:

- Trabalhar com arquivos especificos (que nao estao abertos)
- O Copilot precisa de contexto sobre um arquivo especifico
- Voce quer geracao de codigo bem precisa

Nao e necessario para perguntas gerais ou quando o arquivo ja esta aberto e selecionado."

---

## Perguntas sobre gestao de tempo

### P: "Estou atrasado no cronograma. O que devo pular?"

**Ordem de prioridade:**

1. **Deve completar** (Nucleo do workshop):
   - Entender o projeto Python ✅
   - Criar scaffolding em C# ✅
   - Migrar pelo menos 2-3 endpoints ✅
   - Testes Python passando ✅
   - Entender os modos do Copilot ✅

2. **Deveria completar** (Workshop completo):
   - Todos os endpoints migrados
   - Todos os testes Python passando
   - Entender o processo de validacao

3. **Bom ter** (Se houver tempo):
   - Testes unitarios em C#
   - Otimizacao de codigo
   - Desafio 1 ou 2

**Resposta para dar:**
"Foque em criar o scaffolding e ter pelo menos 2-3 endpoints funcionando com testes passando. Isso cobre os conceitos principais. Voce pode concluir o restante depois do workshop."

---

### P: "Terminei cedo! O que faco?"

**Sugestoes:**

1. **Tente o Desafio 1** (Containerizacao) - 🔥 Intermediario
2. **Tente o Desafio 2** (Integracao com banco) - 🔥🔥 Avancado
3. **Adicione testes unitarios em C#** - Pratique MSTest
4. **Otimize seu codigo** - Peça ao Copilot melhorias
5. **Ajude um colega** - Ensinar reforca aprendizado
6. **Experimente modelos diferentes** - Compare sugestoes

**Resposta para dar:**
"Otimo progresso! Confira o Desafio 1 ou 2, ou tente adicionar testes unitarios em C#. Voce tambem pode experimentar modelos diferentes do Copilot para ver como as sugestoes variam."

---

## Troubleshooting geral

### P: "Nada funciona. Posso comecar do zero?"

**Antes de recomecar:**

1. Revise mudancas recentes com `git status` e `git diff`
2. Tente reverter a ultima mudanca: `git checkout -- <file>`
3. Verifique se e um problema simples de ambiente (porta, caminho, etc.)
4. Peça a um proctor para fazer pair debug por 5 minutos

**Se for recomecar:**
- Crie um novo Codespace (ambiente limpo)
- Ou use `git reset --hard` para voltar ao ultimo commit funcional
- Consulte o exemplo concluido em `src/csharp-app-complete`

**Resposta para dar:**
"Vamos tentar corrigir primeiro - recomecar significa perder seu progresso de aprendizado. Deixe-me ajudar a debugar por alguns minutos."

---

## Dicas para proctors

### Quando alguem estiver travado

1. **Peça para explicar o problema** - muitas vezes a pessoa resolve sozinha
2. **Cheque o basico primeiro** - app rodando? diretorio certo? arquivo salvo?
3. **Olhe a mensagem de erro juntos** - ensine habilidades de debugging
4. **Use o Copilot para ajudar** - mostre como perguntar ao Copilot sobre o erro
5. **Pair debug** - caminhe junto em vez de consertar por ela

### Quando varias pessoas tiverem o mesmo problema

- Pare e faca uma explicacao em grupo
- Adicione em um quadro de "Common Issues"
- Atualize o doc de troubleshooting
- Considere se as instrucoes precisam de clarificacao

### Incentive bons habitos

- ✅ Validar apos cada mudanca
- ✅ Ler mensagens de erro com atencao
- ✅ Usar o Copilot para explicar erros
- ✅ Testar incrementalmente
- ✅ Fazer perguntas cedo

---

## Cartao de referencia rapida

Imprima ou exiba isto para consulta rapida:

```
COPILOT NAO FUNCIONA?
→ Verifique o icone na barra de status
→ Recarregue a janela
→ Salve o arquivo primeiro

TESTES FALHANDO?
→ O app esta rodando?
→ Porta correta (8000)?
→ Verifique a variavel BASE_URL

PORTA EM USO?
→ lsof -i :8000 (achar)
→ kill -9 <PID> (parar)
→ Ou use outra porta

TRAVADO?
→ Verifique a mensagem de erro
→ Pergunte ao Copilot sobre o erro
→ Revise a saida do teste
→ Cheque o basico (caminho, porta)

TERMINOU CEDO?
→ Tente Desafio 1 ou 2
→ Adicione testes unitarios em C#
→ Ajude um colega
```
