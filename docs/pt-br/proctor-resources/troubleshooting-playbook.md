# Playbook de Troubleshooting para Proctors

Este playbook fornece aos proctors solucoes rapidas para problemas tecnicos comuns que surgem durante o workshop. Use para resolucao rapida de issues e para minimizar interrupcoes no fluxo do workshop.

## 🚨 Issues criticas (acao imediata necessaria)

### Issue: Codespace do participante nao inicia

**Sintomas:**
- Codespace preso em "Starting..."
- Mensagem de erro durante criacao do Codespace
- Codespace inicia mas para imediatamente

**Passos de solucao:**

1. **Verificar o status do GitHub** (30 segundos)
   - Acesse [githubstatus.com](https://githubstatus.com)
   - Se Codespaces estiver indisponivel, mude para o guia de desenvolvimento local

2. **Tentar outro navegador** (1 minuto)
   - Extensoes podem interferir
   - Tente modo anonimo/privado
   - Chrome e Edge funcionam melhor

3. **Excluir e recriar** (2 minutos)
   ```
   1. Va para github.com/codespaces
   2. Exclua o Codespace com problema
   3. Volte ao repositorio
   4. Clique "Code" → "Codespaces" → "New codespace"
   ```

4. **Fallback para local** (se o problema persistir)
   - Guie o participante para PREREQUISITES.md
   - Peça para clonar o repositorio localmente
   - Verifique se Python 3.12 e .NET 10 SDK estao instalados

**Prevencao:**
- Antes do workshop: teste a criacao de Codespaces voce mesmo
- Tenha o guia de desenvolvimento local pronto como plano B

---

### Issue: Copilot nao ativado/funcionando

**Sintomas:**
- Icone do Copilot com erro
- Nenhuma sugestao aparecendo
- Mensagem "Copilot is not available"

**Passos de solucao:**

1. **Checar status do Copilot** (30 segundos)
   ```
   - Olhe a barra de status (parte inferior do VS Code)
   - O icone do Copilot nao deve ter um X vermelho
   - Clique no icone para ver status detalhado
   ```

2. **Verificar assinatura** (1 minuto)
   ```
   - Va para github.com/settings/copilot
   - Verifique se a assinatura/trial esta ativa
   - Veja se expirou hoje
   ```

3. **Reautenticar** (2 minutos)
   ```
   1. Ctrl+Shift+P → "Sign out of GitHub"
   2. Aguarde 10 segundos
   3. Ctrl+Shift+P → "Sign in to GitHub"
   4. Complete o fluxo de autenticacao
   ```

4. **Recarregar o VS Code** (30 segundos)
   ```
   Ctrl+Shift+P → "Reload Window"
   ```

5. **Verificar extensoes** (1 minuto)
   ```
   - Verifique se a extensao GitHub Copilot esta instalada
   - Verifique se a extensao GitHub Copilot Chat esta instalada
   - Atualize extensoes se houver updates
   ```

**Workaround:**
- Se o Copilot Chat funciona mas o inline nao (ou vice-versa), use o que estiver funcionando
- O participante pode concluir o workshop apenas com Chat

**Prevencao:**
- Em email pre-workshop: lembre participantes de verificar acesso ao Copilot
- Peça para testar o Copilot antes do dia do workshop

---

### Issue: Falhas de teste generalizadas (varios participantes)

**Sintomas:**
- Muitos participantes relatando o mesmo teste falhando
- Padrao de falhas pelo grupo

**Causas raizes e solucoes:**

1. **App nao esta rodando** (mais comum)
   ```
   Solucao: Lembrar todos de iniciar o app primeiro
   
   Terminal 1:
   cd src/csharp-app
   dotnet run --urls "http://localhost:8000"
   
   Terminal 2:
   cd src/python-app/webapp
   pytest test_main.py -v
   ```

2. **Porta errada**
   ```
   Solucao: Verificar se estao usando a porta 8000
   
   # Ao rodar o app C#:
   dotnet run --urls "http://localhost:8000"
   
   # Nao:
   dotnet run  # (usa porta 5000 por padrao)
   ```

3. **Variavel de ambiente nao definida**
   ```
   Solucao: Definir BASE_URL se necessario
   
   Windows PowerShell:
   $env:BASE_URL="http://localhost:8000"
   
   Linux/Mac:
   export BASE_URL="http://localhost:8000"
   ```

**Aviso rapido para o grupo:**
```
"Se os testes estao falhando, por favor verifique:
1. Seu app esta rodando em um terminal?
2. Esta na porta 8000?
3. Voce consegue dar curl http://localhost:8000 e obter uma resposta?
Me avise se ainda tiver problemas apos checar isso."
```

---

### Issue: Problemas de conectividade com a internet

**Sintomas:**
- Nao consegue acessar GitHub
- Copilot nao responde
- Instalacao de pacotes falha

**Passos de solucao:**

1. **Verificar conectividade** (1 minuto)
   ```bash
   ping github.com
   curl https://api.github.com
   ```

2. **Checar proxy/firewall** (se em ambiente corporativo)
   - Pergunte ao TI do local sobre configuracoes de proxy
   - Pode ser necessario configurar proxy do git/npm

3. **Usar modo offline** (fallback)
   ```
   - Consulte o codigo concluido em src/csharp-app-complete
   - Trabalhe com materiais impressos se houver
   - Faça pair com alguem com conexao funcionando
   ```

**Prevencao:**
- Teste o WiFi do local antes do workshop
- Tenha materiais offline prontos (codigo concluido, guias impressos)
- Considere hotspot movel como backup

---

## ⚠️ Issues comuns (frequentes, mas nao criticas)

### Issue: Porta 8000 ja esta em uso

**Sintomas:**
- Erro: "Address already in use"
- Nao consegue iniciar o app na porta 8000

**Solucao:**

**Windows PowerShell:**
```powershell
# Encontrar quem esta usando a porta 8000
Get-NetTCPConnection -LocalPort 8000

# Finalizar processo (substitua <PID>)
Stop-Process -Id <PID> -Force
```

**Linux/Mac:**
```bash
# Encontrar quem esta usando a porta 8000
lsof -i :8000

# Finalizar processo
kill -9 <PID>
```

**Alternativa:**
```bash
# Use outra porta
dotnet run --urls "http://localhost:8001"

# Lembre de atualizar BASE_URL
export BASE_URL="http://localhost:8001"
```

---

### Issue: Dependencias Python nao instaladas

**Sintomas:**
- `ModuleNotFoundError: No module named 'fastapi'`
- Erros de importacao ao rodar o app Python

**Solucao:**
```bash
cd src/python-app/webapp
pip3 install -r ../requirements.txt

# Ou no diretorio pai:
cd src/python-app
pip3 install -r requirements.txt
```

**Verificar:**
```bash
pip3 list | grep fastapi
# Deve mostrar fastapi==0.103.2
```

---

### Issue: .NET SDK nao encontrado (desenvolvimento local)

**Sintomas:**
- `dotnet: command not found`
- `The specified SDK version is not available`

**Solucao:**

1. **Verificar instalacao:**
   ```bash
   dotnet --version
   # Deve mostrar 10.0.x
   ```

2. **Se nao estiver instalado:**
   - Direcione para: https://dotnet.microsoft.com/download/dotnet/10.0
   - Baixe e instale o .NET 10 SDK
   - Reinicie terminal/VS Code apos a instalacao

3. **Problemas de PATH:**
   ```bash
   # Adicione ao PATH se necessario
   export PATH="$PATH:/usr/share/dotnet"
   ```

---

### Issue: Erros de desserializacao JSON

**Sintomas:**
- Erro ao ler weather.json
- Null reference exceptions
- Dados nao carregam

**Causas comuns:**

1. **Caminho do arquivo errado:**
   ```csharp
   // Errado (pode nao funcionar quando roda de outro diretorio)
   var json = File.ReadAllText("weather.json");
   
   // Melhor
   var json = File.ReadAllText("weather.json");  // Na mesma pasta
   // Ou use caminho completo a partir da raiz do projeto
   ```

2. **Problemas de formato JSON:**
   - Verifique se weather.json e um JSON valido
   - Confira se as classes modelo correspondem a estrutura do JSON

3. **Problemas de encoding:**
   - Use UTF8: `File.ReadAllText("weather.json", Encoding.UTF8)`

**Correção rapida:**
```csharp
// Adicione null checks
if (weatherData == null)
{
    return Results.Problem("Failed to load weather data");
}
```

---

### Issue: VS Code nao mostra o Copilot Chat

**Sintomas:**
- Icone de chat ausente
- Nao consegue abrir o painel do Copilot Chat
- Extensao instalada mas nao visivel

**Solucao:**

1. **Abrir painel do chat:**
   ```
   Ctrl+Alt+I (Windows/Linux)
   Cmd+Shift+I (Mac)
   
   Ou: View → Command Palette → "GitHub Copilot: Open Chat"
   ```

2. **Verificar extensao:**
   ```
   Extensions → Procurar "GitHub Copilot Chat"
   Deve aparecer como instalada e habilitada
   Se nao, instale
   ```

3. **Recarregar janela:**
   ```
   Ctrl+Shift+P → "Reload Window"
   ```

---

### Issue: Testes passam localmente mas falham em CI/CD

**Nao se aplica a este workshop, mas bom saber:**

**Causas comuns:**
- Diferencas de ambiente
- Conflitos de porta no CI
- Problemas de timing (app nao iniciou completamente)

**Para o workshop:**
- Nao usamos CI/CD
- Testes rodam localmente apenas
- Se alguem mencionar, explique que esta fora do escopo

---

## 🛠️ Tecnicas de debugging para proctors

### Protocolo de debug de 5 minutos

Quando um participante estiver travado, use esta abordagem sistematica:

1. **Entenda o problema (1 min)**
   - Peça para descrever o que esta tentando fazer
   - Qual erro esta vendo?
   - Qual foi a ultima coisa que funcionou?

2. **Cheque o basico (1 min)**
   - O app esta rodando?
   - Diretorio correto? (`pwd`)
   - Arquivo salvo?
   - Porta correta?

3. **Leia o erro (1 min)**
   - Olhe a mensagem de erro juntos
   - Identifique a linha/arquivo especifico
   - Procure o erro no Google se necessario

4. **Teste a hipotese (1 min)**
   - Faça uma pequena mudanca
   - Teste imediatamente
   - Observe o resultado

5. **Itere ou escale (1 min)**
   - Se estiver melhorando: continue debuggando
   - Se estiver travado: escale para o instrutor lider
   - Se resolver: documente o issue

### Usando o Copilot para debugar

**Ensine participantes a perguntar ao Copilot:**
```
"Estou recebendo este erro: [cole a mensagem de erro]
Aqui esta meu codigo: [cole o codigo]
O que esta errado e como posso corrigir?"
```

Isso ensina uma habilidade valiosa enquanto resolve o problema.

---

## 📊 Acompanhando issues durante o workshop

### Modelo de log de issues

Mantenha um log durante o workshop:

```
Hora | Issue | Participantes afetados | Solucao | Tempo para resolver
-----|-------|------------------------|--------|--------------------
9:15 | Porta 8000 em uso | 3 | Encerrar processo | 2 min
9:30 | Copilot nao funcionando | 1 | Reautenticar | 5 min
9:45 | Testes falhando | 5 | App nao rodando | 1 min
```

**Use isso para:**
- Identificar padroes (mesmo issue varias vezes = precisa de aviso)
- Gestao de tempo (se resolucao estiver demorando)
- Melhorar materiais (issues frequentes precisam de docs melhores)

---

## 🎯 Prevencao proativa de issues

### Checagens pre-workshop (1 hora antes)

- [ ] Testar criacao de Codespaces
- [ ] Verificar acesso ao GitHub.com
- [ ] Testar Copilot em um Codespace novo
- [ ] Executar as 3 primeiras etapas do workshop
- [ ] Verificar se todos os links da documentacao funcionam
- [ ] Checar qualidade do WiFi do local

### Anuncios de abertura

**Antes de comecar:**
```
"Algumas dicas tecnicas antes de comecarmos:

1. Se aparecer erros, LEIA a mensagem - ela geralmente diz o que esta errado
2. Se testes falharem, garanta que seu app esta rodando primeiro
3. Se o Copilot nao estiver funcionando, cheque o icone na barra de status
4. Salve seus arquivos antes de pedir ajuda ao Copilot
5. Nao hesite em pedir ajuda - estamos aqui para isso!

Alguma pergunta antes de comecarmos?"
```

### Checkpoints no meio do workshop

**Depois de secoes importantes:**
```
"Vamos fazer um checkpoint rapido. Levante a mao se:
- Seu app Python esta rodando e testado ✓
- Voce criou o scaffolding C# ✓
- Voce tem pelo menos um endpoint C# funcionando ✓

Se voce nao levantou a mao, vamos pausar e colocar todo mundo no mesmo ritmo."
```

---

## 🚀 Referencia rapida de comandos

### Para proctors ajudarem participantes rapidamente

**Checar processos rodando:**
```bash
# Ver o que esta rodando na porta 8000
lsof -i :8000          # Mac/Linux
netstat -ano | findstr :8000  # Windows

# Ver todos os processos rodando
ps aux | grep python   # Processos Python
ps aux | grep dotnet   # Processos .NET
```

**Encerrar processos:**
```bash
# Por PID
kill -9 <PID>          # Mac/Linux
Stop-Process -Id <PID> -Force  # Windows PowerShell

# Por nome (cuidado!)
pkill python           # Encerra todos os Python
pkill dotnet           # Encerra todos os .NET
```

**Checar instalacoes:**
```bash
python3 --version      # Deve ser 3.12.x
dotnet --version       # Deve ser 10.0.x
git --version          # Qualquer versao recente
code --version         # Versao do VS Code
```

**Testar endpoints:**
```bash
# Testar se o app responde
curl http://localhost:8000
curl http://localhost:8000/countries

# Saida formatada
curl http://localhost:8000/countries | jq
```

**Ajudas do Git:**
```bash
# Ver o que mudou
git status
git diff

# Desfazer mudancas
git checkout -- <file>
git reset --hard HEAD

# Ver codigo concluido
ls src/csharp-app-complete
```

---

## 📞 Guia de escalonamento

### Quando escalar para o instrutor lider

- Issue afeta varios participantes (>3)
- Issue bloqueia progresso
- Problema de seguranca/acesso
- Problema de local/equipamento
- Participante gastou >10 minutos no mesmo problema

### Quando sugerir seguir em frente

- Issue e "bom ter" (nao critica)
- Tempo esta limitado
- Existe abordagem alternativa
- E possivel concluir o workshop sem resolver isso

**Frase positiva:**
```
"Vamos seguir em frente e voltar a isso depois. Voce consegue terminar o
workshop e depois lidar com esse problema especifico. Funciona para voce?"
```

---

## 💡 Dicas para proctors

### Para proctors novos

1. **Nao apenas conserte** - ensine a debugar
2. **Use o Copilot** - mostre como perguntar ao Copilot sobre erros
3. **Mantenha a calma** - problemas tecnicos sao normais
4. **Documente** - anote novos issues para futuros workshops
5. **Time-box** - nao gaste mais que 5 min em um unico problema

### Para proctors experientes

1. **Antecipe** - observe issues comuns antes de serem reportados
2. **Resolva em grupo** - se o mesmo issue afetar 3+ pessoas, faça explicacao em grupo
3. **Empodere** - ensine participantes a se ajudarem
4. **Melhore** - sugira melhorias nos docs para issues recorrentes
5. **Compartilhe** - informe outros proctors sobre padroes observados

---

## Resumo

**Issues mais comuns (em ordem de frequencia):**

1. App nao rodando quando testes executam
2. Porta errada (nao 8000)
3. Copilot nao autenticado
4. Porta 8000 ja em uso
5. Dependencias nao instaladas

**Correcoes rapidas:**
- 90% dos issues sao resolvidos ao: verificar app rodando, checar porta, recarregar janela
- Em caso de duvida: leia a mensagem de erro com atencao
- Use o Copilot para explicar erros - ensina habilidade de debugging

**Lembrete:**
- Issues tecnicos sao oportunidades de aprendizado
- Seja paciente e positivo
- Documente novos issues
- Compartilhe insights com outros proctors
