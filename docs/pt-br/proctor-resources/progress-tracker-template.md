# Modelo de acompanhamento de progresso dos participantes

Este modelo ajuda proctors a acompanhar o progresso dos participantes durante o workshop e identificar quando ajustar o ritmo ou oferecer suporte adicional.

## Marcos de progresso do workshop

Use este modelo durante o workshop para acompanhar quantos participantes completaram cada marco principal. Isso ajuda voce a:

- Saber quando avancar vs desacelerar
- Identificar quem precisa de ajuda adicional
- Ajustar o tempo para as secoes restantes
- Oferecer assistencia direcionada

---

## Rastreador rapido de progresso

**Data do workshop:** ________________  
**Total de participantes:** ______  
**Proctors:** ________________

### Checkpoint 1: Setup do ambiente (Meta: 10 minutos)

**Check de tempo:** ______

"Levante a mao: quem ja esta com o ambiente pronto?"

- [ ] Codespace/Ambiente local rodando: ______ / ______
- [ ] VS Code aberto: ______ / ______
- [ ] GitHub Copilot funcionando: ______ / ______

**Status:**  
☐ >80% pronto → Avancar  
☐ 60-80% pronto → Dar mais 5 minutos  
☐ <60% pronto → Troubleshooting em grupo necessario  

**Notas:** ___________________________________________

---

### Checkpoint 2: App Python rodando (Meta: 25 minutos)

**Check de tempo:** ______

"Levante a mao: quem ja esta com o app Python rodando e testado?"

- [ ] App Python iniciado com sucesso: ______ / ______
- [ ] Swagger UI acessado: ______ / ______
- [ ] Testes Python executados (pytest): ______ / ______

**Status:**  
☐ >80% pronto → Avancar para o scaffolding C#  
☐ 60-80% pronto → Parear quem esta com dificuldade  
☐ <60% pronto → Demo em grupo necessario  

**Problemas comuns vistos:**
- [ ] Dependencias nao instaladas
- [ ] Diretorio errado
- [ ] Porta ja em uso
- [ ] Outro: _________________

**Notas:** ___________________________________________

---

### Checkpoint 3: Scaffolding C# criado (Meta: 40 minutos)

**Check de tempo:** ______

"Levante a mao: quem ja criou o scaffolding em C#?"

- [ ] Pasta csharp-app criada: ______ / ______
- [ ] Arquivo .csproj presente: ______ / ______
- [ ] Program.cs criado: ______ / ______
- [ ] Consegue rodar `dotnet build`: ______ / ______

**Status:**  
☐ >80% pronto → Avancar para o primeiro endpoint  
☐ 60-80% pronto → Fornecer template/orientacao  
☐ <60% pronto → Considerar demo  

**Notas:** ___________________________________________

---

### Checkpoint 4: Primeiro endpoint funcionando (Meta: 55 minutos)

**Check de tempo:** ______

"Levante a mao: quem ja tem o endpoint raiz (/) funcionando?"

- [ ] Endpoint raiz implementado: ______ / ______
- [ ] App C# rodando na porta 8000: ______ / ______
- [ ] Teste Python do endpoint raiz passou: ______ / ______

**Status:**  
☐ >80% pronto → Avancar para os endpoints restantes  
☐ 60-80% pronto → Pausa rapida para troubleshooting  
☐ <60% pronto → Revisar processo de validacao  

**Problemas comuns vistos:**
- [ ] Configuracao de porta errada
- [ ] Testes nao encontram o app rodando
- [ ] Problemas de serializacao JSON
- [ ] Outro: _________________

**Notas:** ___________________________________________

---

### Checkpoint 5: Todos os endpoints migrados (Meta: 70 minutos)

**Check de tempo:** ______

"Levante a mao: quem ja migrou todos os endpoints com testes Python passando?"

- [ ] Todos os endpoints implementados: ______ / ______
- [ ] Todos os testes Python passando: ______ / ______
- [ ] Documentacao Swagger funcionando: ______ / ______

**Status:**  
☐ >80% completo → Avancar para encerramento/desafios  
☐ 60-80% completo → Quem terminou pode iniciar o Desafio 1  
☐ <60% completo → Estender tempo ou priorizar endpoints nucleares  

**Notas:** ___________________________________________

---

### Status final: Conclusao do workshop

**Check de tempo:** ______

"Levante a mao: em que ponto voce esta?"

- [ ] Conclusao do core (todos os endpoints): ______ / ______
- [ ] Concluiu a maior parte (3+ endpoints funcionando): ______ / ______
- [ ] Conclusao parcial (1-2 endpoints): ______ / ______
- [ ] Comecou o Desafio 1 ou 2: ______ / ______
- [ ] Adicionou testes C#: ______ / ______

**Taxa geral de sucesso:** ______%

**Notas:** ___________________________________________

---

## Planilha de acompanhamento detalhado

Para workshops com lugares marcados ou quando voce precisa de acompanhamento detalhado:

| Participante # | Nome | Ambiente pronto | Python rodando | Scaffolding | 1o Endpoint | Todos endpoints | Notas |
|--------------|------|-----------------|---------------|------------|------------|----------------|------|
| 1 | | ☐ | ☐ | ☐ | ☐ | ☐ | |
| 2 | | ☐ | ☐ | ☐ | ☐ | ☐ | |
| 3 | | ☐ | ☐ | ☐ | ☐ | ☐ | |
| 4 | | ☐ | ☐ | ☐ | ☐ | ☐ | |
| 5 | | ☐ | ☐ | ☐ | ☐ | ☐ | |
| 6 | | ☐ | ☐ | ☐ | ☐ | ☐ | |
| 7 | | ☐ | ☐ | ☐ | ☐ | ☐ | |
| 8 | | ☐ | ☐ | ☐ | ☐ | ☐ | |
| 9 | | ☐ | ☐ | ☐ | ☐ | ☐ | |
| 10 | | ☐ | ☐ | ☐ | ☐ | ☐ | |

*(Continue conforme o tamanho do seu workshop)*

---

## Matriz de decisao de ritmo

Use este guia para decidir se deve avancar ou pausar:

### Quando 80%+ completar
✅ **Avancar para a proxima secao**
- Recap rapido para quem esta pronto
- Atribuir ajudantes para apoiar quem falta
- Quem terminar pode iniciar desafios

### Quando 60-79% completar
⚠️ **Dar mais 5-10 minutos**
- Anunciar: "Vamos dar mais 5 minutos neste checkpoint"
- Parear participantes avancados com quem precisa de ajuda
- Circular para dar suporte direcionado

### Quando <60% completar
🛑 **Intervencao em grupo necessaria**
- Pausar o workshop
- Fazer uma demo/explicacao em grupo
- Abordar problemas comuns publicamente
- Ajustar o cronograma se necessario

---

## Rastreamento de issues

Registre issues conforme surgirem para identificar padroes:

| Hora | Descricao do issue | # afetados | Resolucao | Tempo para corrigir |
|------|-------------------|-----------|----------|--------------------|
| | | | | |
| | | | | |
| | | | | |
| | | | | |
| | | | | |

**Analise de padroes:**

- Problema mais comum: ________________
- Tempo medio de resolucao: ______
- Issues que exigiram explicacao em grupo: ________________

---

## Ajustes de tempo

Se voce estiver atrasado, use este guia de prioridade:

### Deve cobrir (Objetivos principais de aprendizagem)
- [ ] Entender a estrutura do projeto Python
- [ ] Criar scaffolding C# com Agent Mode
- [ ] Implementar pelo menos 2 endpoints
- [ ] Validar com testes Python
- [ ] Entender os modos do Copilot

### Deveria cobrir (Workshop completo)
- [ ] Todos os endpoints migrados
- [ ] Todos os testes passando
- [ ] Discussao sobre otimizacao de codigo

### Bom ter (Se houver tempo)
- [ ] Testes unitarios em C#
- [ ] Introducao ao Desafio 1
- [ ] Discussao do Desafio 2

**Recomendacao:** Se estiver atrasado, foque em qualidade em vez de quantidade. E melhor ter 2-3 endpoints bem entendidos do que correr para todos.

---

## Resumo pos-workshop

**Data:** ________________  
**Duracao:** ______ horas ______ minutos  

**Taxas de conclusao:**
- Conclusao total (todos os endpoints): ______%
- Conclusao parcial (2+ endpoints): ______%
- Iniciou mas nao concluiu: ______%

**Avaliacao de ritmo:**
☐ Rapido demais - muitos tiveram dificuldade  
☐ No ritmo certo - a maioria concluiu com bom entendimento  
☐ Lento demais - muitos terminaram cedo e ficaram ociosos  

**Secoes mais efetivas:**
1. ________________
2. ________________
3. ________________

**Secoes que precisam de melhoria:**
1. ________________
2. ________________
3. ________________

**Resumo de problemas tecnicos:**
- Problema mais frequente: ________________
- Maior perda de tempo: ________________
- Problemas inesperados: ________________

**Recomendacoes para a proxima sessao:**
1. ________________
2. ________________
3. ________________

**Destaques de feedback dos participantes:**
- Positivo: ________________
- Sugestoes: ________________
- Preocupacoes: ________________

---

## Frases de checagem rapida

Use estas frases durante o workshop para medir rapidamente:

**Checagem de ambiente:**
> "Mostrem com as maos: verde - tudo funcionando. Amarelo - problemas pequenos. Vermelho - bloqueado."

**Checagem de compreensao:**
> "Polegar para cima se fez sentido, polegar para baixo se precisar de mais explicacao."

**Checagem de progresso:**
> "Vamos ver onde todos estao. Mãos para cima se voce concluiu [checkpoint]."

**Checagem de ritmo:**
> "Pulso rapido: estamos indo rapido demais, lento demais ou no ritmo certo?"

**Checagem de energia:**
> "Como voces estao? Precisam de uma pausa rapida?"

---

## Alternativa digital de acompanhamento

Se voce preferir acompanhamento digital, considere usar:

**Planilha (Google Sheets):**
- Compartilhe com todos os proctors
- Atualizacoes em tempo real
- Facil de analisar depois

**Formulario simples:**
- Crie um Google Form
- Participantes auto-reportam progresso
- Visao rapida agregada

**Ferramenta de enquete:**
- Mentimeter, Slido ou Poll Everywhere
- Respostas anonimas
- Resultados visuais

**Exemplo de estrutura de Google Sheet:**
```
Coluna A: ID do participante
Coluna B: Checkpoint 1 (S/N)
Coluna C: Checkpoint 2 (S/N)
Coluna D: Checkpoint 3 (S/N)
Coluna E: Checkpoint 4 (S/N)
Coluna F: Checkpoint 5 (S/N)
Coluna G: Notas
```

---

## Dicas para um acompanhamento eficaz

1. **Cheque com frequencia** - Pelo menos a cada 15-20 minutos
2. **Seja visivel** - Facilite para os participantes pedirem ajuda
3. **Use ajudantes** - Participantes avancados podem ajudar outros
4. **Seja flexivel** - Ajuste o ritmo com base nos dados em tempo real
5. **Documente** - Notas ajudam a melhorar futuros workshops

**Lembrete:** Acompanhamento de progresso nao e sobre julgar participantes - e sobre garantir que todos tenham uma experiencia de aprendizado bem-sucedida.
