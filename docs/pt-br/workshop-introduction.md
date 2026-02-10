# Introducao ao Workshop

## Migrando a API de Temperatura da Zava de Python para C#

A Zava recentemente adquiriu uma empresa externa cujos apps e servicos foram implementados principalmente em Python. Muitos desses servicos incluem endpoints de temperatura, estacao e localizacao que sao uteis para a linha de produtos da Zava. Como o backend principal e as ferramentas operacionais da Zava sao baseados em C#, a lideranca de engenharia iniciou um processo deliberado de migracao para trazer os servicos em Python para o ecossistema C#/.NET.

Esse esforco de migracao tem o objetivo de unificar o stack tecnologico da plataforma da Zava, simplificar a manutencao operacional e permitir uma integracao mais fluida entre os servicos adquiridos e o backend existente em .NET. Migrar a API de temperatura baseada em Python para C# oferece maior seguranca de tipos via verificacao em tempo de compilacao, melhor performance em tempo de execucao e maior alinhamento com as praticas de implantacao e ferramentas empresariais da Zava no Azure. A API fornece dados historicos de clima em varios paises, cidades e meses — dados essenciais para os produtos de fibra inteligente da Zava se adaptarem a diferentes condicoes ambientais.

Este workshop vai guiar voce por um cenario realista de migracao usando GitHub Copilot: pegar uma API Python existente (de um codigo adquirido), reimplementa-la incrementalmente em C# e validar que o comportamento foi preservado enquanto se melhora a manutencao e a integracao com o backend principal da Zava.

### 🎯 Por que isso importa: contexto do mundo real

!!! info "Entendendo migracao de linguagem em producao"

    **Por que a Zava escolheu C# para esta migracao?**
    
    - Integracao mais facil com o backend C# existente e ferramentas internas apos a aquisicao, reduzindo atrito e time-to-market
    - Suporte de primeira classe ao ecossistema Azure (Application Insights, integracao com Azure AD, ferramentas de IaC) para implantacoes corporativas
    - Ferramentas corporativas robustas (Visual Studio, JetBrains Rider, analyzers do .NET) que aumentam a produtividade, debug e refatoracao em escala
    
    **Por que a validacao incremental importa em producao:**
    
    - **Gestao de risco**: testar cada endpoint individualmente reduz o raio de impacto de erros
    - **Verificacao continua**: manter testes Python garante que a nova implementacao corresponde ao comportamento original
    - **Construcao de confianca**: validacao passo a passo cria checkpoints claros e pontos de rollback
    - **Aprendizado com IA**: validar pequenas mudancas ajuda a aprender quando confiar e quando questionar sugestoes de IA

Vamos passar por algumas solicitacoes desafiadoras para o GitHub Copilot e trata-las conforme aparecem.

!!! note
    Este repo foi criado para introduzir varios recursos do **GitHub Copilot**, como **Copilot Chat**, **inline chat** e **Agent Mode** dentro do **Visual Studio Code**. Por isso, os guias passo a passo abaixo contem a descricao geral do que deve ser feito, e o Copilot pode ajudar a gerar os comandos necessarios.

    Cada etapa (quando aplicavel) tambem contem um `Cheatsheet / Tip` que pode ser usado para validar as sugestoes do Copilot em relacao ao comando correto.

    💡 Experimente diferentes prompts e veja como isso afeta a precisao das sugestoes do GitHub Copilot. Por exemplo, ao usar o inline chat, voce pode adicionar um prompt extra para refinar a resposta sem ter que reescrever tudo.

## Recursos do workshop

Voce vai trabalhar com um projeto Python (representando um servico adquirido) que expoe uma API HTTP. Esse projeto precisa ser migrado e sua tarefa principal sera reimplementa-lo e integra-lo usando a linguagem C# com .NET Minimal APIs para que se encaixe no backend principal da Zava.

### Padroes corporativos da Zava — Como esta migracao ajuda

A Zava aplica um conjunto de padroes corporativos para servicos em producao. Abaixo estao os padroes principais e como a migracao para C#/.NET ajuda a atende-los com mais eficacia do que a implementacao atual em Python:

- Seguranca e identidade: .NET possui bibliotecas maduras para autenticacao/autorizacao segura (integracao com Azure AD, validacao de token, bibliotecas de criptografia robustas) e um ecossistema forte de ferramentas de scanning e enforcement de politicas.
- Observabilidade e diagnosticos: Integracao profunda com Application Insights, logging estruturado (ILogger), tracing distribuido e SDKs de telemetria de primeira classe facilitam cumprir SLAs de observabilidade da Zava.
- Confiabilidade e performance: Primitivas de concorrencia robustas, otimizacoes do runtime .NET e compilacao ahead-of-time opcional reduzem latencia e aumentam throughput para cargas empresariais.
- Manutenibilidade e governanca: Tipagem estatica, analyzers do Roslyn, gerenciamento padronizado de pacotes NuGet e checks de qualidade obrigatorios ajudam a Zava a manter um codigo consistente e auditavel entre times.
- CI/CD e automacao de implantacao: Suporte nativo ao Azure DevOps / GitHub Actions, tooling para containers e padroes de configuracao de ambiente tornam simples automatizar implantacoes blue/green ou canary seguras.
- Conformidade e auditabilidade: Ferramentas para analise estatica, code scanning e assinatura de binarios, combinadas com politicas centralizadas de dependencias, ajudam a satisfazer requisitos regulatorio e de auditoria interna.
- Produtividade e onboarding: Suporte rico de IDE, builds deterministicas e ferramentas avancadas de refatoracao reduzem o tempo de onboarding de desenvolvedores que entram nos times da Zava.

Embora Python seja excelente para muitos dominios, alinhar os servicos aos padroes corporativos da Zava e mais facil e consistente dentro do ecossistema C#/.NET para essa organizacao. A estrategia de migracao deste workshop destaca a validacao incremental para preservar comportamento enquanto se obtém esses beneficios empresariais.

Aqui estao alguns recursos:

1. Executar o aplicativo web e abrir o navegador
1. Usar o endpoint /docs no app em execucao para ver os endpoints
1. Todas as dependencias e bibliotecas ja estao pre-instaladas para Python
1. Testes Python sao fornecidos para validar a corretude das implementacoes Python e C#

## Modos do GitHub Copilot

O GitHub Copilot oferece modos distintos: **Ask**, **Edit**, **Plan** e **Agent**, cada um projetado para melhorar seu fluxo de trabalho de formas diferentes. Esses modos atendem diferentes niveis de assistencia, desde responder perguntas ate gerenciar tarefas complexas de forma autonoma.

### Ask Mode

**Ask Mode** e um assistente de perguntas e respostas que ajuda voce a entender codigo, resolver problemas ou aprender conceitos. Ele permite fazer perguntas em linguagem natural, e o Copilot responde com explicacoes, trechos ou sugestoes. Ele nao modifica codigo diretamente.

!!! tip
    Ask Mode funciona melhor para esclarecimentos rapidos, brainstorm de solucoes e fornecimento de implementacoes de exemplo.

### Edit Mode

**Edit Mode** permite *modificacoes diretas no codigo* com base em instrucoes em linguagem natural. Voce pode selecionar blocos de codigo ou arquivos, descrever as mudancas desejadas, e o Copilot vai propor edits. Essas mudancas sao apresentadas como diffs para sua revisao, garantindo que voce mantenha controle sobre a implementacao final.

!!! tip
    Use Edit Mode para atualizacoes direcionadas, como refatoracao ou adicionar tratamento de erros. Na maioria das vezes, o Agent Mode e a opcao preferida para tarefas mais complexas.

### Agent Mode

**Agent Mode** e o modo mais autonomo e poderoso. Ele permite que o Copilot analise seu projeto inteiro, planeje tarefas, edite arquivos, execute comandos e itere ate que o objetivo seja alcançado. Esse modo e ideal para tarefas com varios passos, como construir features, corrigir bugs ou criar scaffolding de componentes. Embora o Agent Mode automatize boa parte do processo, ele ainda exibe acoes potencialmente arriscadas para sua aprovacao, garantindo seguranca e corretude.

!!! tip
    Agent Mode executa acoes alem de edicao, como escrever codigo e criar novos arquivos. Ele e melhor usado para tarefas que envolvem mais do que apenas prompts de conhecimento ou edicoes de linhas isoladas.

### Plan Mode

**Plan Mode** e um novo recurso do GitHub Copilot que ajuda usuarios a definir seus objetivos de codificacao de forma mais eficaz. Nesse modo, o Copilot ajuda a criar um plano estruturado para seu projeto, dividindo tarefas complexas em etapas gerenciaveis. Isso pode incluir gerar boilerplate, sugerir estruturas de projeto e ate identificar desafios antes de comecar a codificar.

!!! tip
    Use Plan Mode para melhorar seu fluxo de trabalho definindo objetivos claros e recebendo sugestoes alinhadas ao seu projeto.

## Usando referencias de arquivo em prompts

Ao trabalhar com o GitHub Copilot durante este workshop, voce encontrara prompts que usam a sintaxe `#file:filename`. Esse padrao e importante:

!!! tip "Como usar #file: - Guia rapido"
    **O que faz:** A sintaxe `#file:filename` fornece contexto especifico de arquivo ao GitHub Copilot, ajudando-o a entender exatamente em qual arquivo voce esta trabalhando.

    **Como usar:**
    
    1. Digite `#` na janela de chat do Copilot
    2. Um seletor de arquivos vai aparecer automaticamente
    3. Selecione o arquivo que deseja referenciar (por exemplo, `main.py` ou `Program.cs`)
    4. Em seguida, digite ou cole o restante do seu prompt
    
    **Por que isso importa:** Fornecer contexto de arquivo ajuda o Copilot a gerar sugestoes mais precisas e relevantes ao entender a estrutura do seu projeto e o codigo especifico em que voce esta trabalhando.
    
    **Exemplo:** Em vez de perguntar "adicione um endpoint", pergunte "#file:Program.cs add the root endpoint only"

!!! note
    Nos prompts em que `#file:filename` e usado, isso indica ao Copilot o arquivo onde o codigo deve ser gerado.
    Voce deve digitar manualmente o `#` e selecionar o arquivo, e depois copiar e colar o restante do prompt.
    Isso e util quando voce tem varios arquivos no seu projeto e quer fornecer contexto especifico ao Copilot sobre o arquivo em que esta trabalhando.

## Modelos disponiveis

Este workshop e independente de modelo, e portanto nao exigimos que os participantes escolham um modelo especifico durante o trabalho. Ainda assim, vale lembrar que o GitHub Copilot suporta uma variedade de modelos (como modelos GPT, Claude, Gemini, etc.) com capacidades diferentes. Para saber mais sobre o GitHub Copilot e seus diferentes planos, visite a secao **Resources** ou este link: [GitHub Copilot Plans](https://github.com/features/copilot/plans)
