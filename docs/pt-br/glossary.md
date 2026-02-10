# Glossario

Este glossario fornece definicoes de termos-chave usados ao longo do workshop. Use como referencia rapida quando encontrar terminologia desconhecida.

## Terminologia de API

**API (Application Programming Interface)**
: Conjunto de regras e protocolos que permite que diferentes aplicativos de software se comuniquem entre si.

**Endpoint**
: Um caminho de URL especifico em uma API que executa uma funcao especifica (por exemplo, `/countries` ou `/weather`).

**REST (Representational State Transfer)**
: Um estilo arquitetural para projetar aplicativos em rede, usando metodos HTTP padrao (GET, POST, PUT, DELETE).

**JSON (JavaScript Object Notation)**
: Um formato de dados leve que e facil para humanos lerem e escreverem e facil para maquinas analisarem e gerarem.

**HTTP Methods**
: Tipos padrao de requisicao incluindo GET (recuperar dados), POST (criar dados), PUT (atualizar dados), DELETE (remover dados).

**Status Code**
: Um numero de tres digitos retornado por um servidor indicando o resultado de uma requisicao (por exemplo, 200 OK, 404 Not Found, 500 Internal Server Error).

**Swagger/OpenAPI**
: Uma especificacao e conjunto de ferramentas para documentar APIs REST, fornecendo documentacao interativa e interfaces de teste.

## Terminologia .NET e C#

**ASP.NET Core**
: Um framework cross-platform e de alta performance para criar aplicativos web e APIs modernos.

**Minimal APIs**
: Uma abordagem simplificada no ASP.NET Core para criar APIs com codigo e configuracao minimos.

**.NET SDK (Software Development Kit)**
: Um conjunto de ferramentas, bibliotecas e runtime necessario para criar e executar aplicativos .NET.

**Runtime**
: O ambiente de execucao que roda aplicativos .NET e gerencia memoria, seguranca e outros servicos do sistema.

**NuGet**
: O gerenciador de pacotes do .NET, usado para instalar e gerenciar bibliotecas e dependencias de terceiros.

**System.Text.Json**
: Uma biblioteca nativa do .NET para serializar e desserializar dados JSON.

**Program.cs**
: O arquivo de entrada para aplicativos .NET, onde a aplicacao e configurada e iniciada.

**Namespace**
: Uma forma de organizar codigo no .NET, evitando conflitos de nome ao agrupar classes relacionadas.

## Terminologia de Python

**FastAPI**
: Um framework web moderno e rapido em Python para criar APIs com documentacao interativa automatica.

**Uvicorn**
: Um servidor web ASGI (Asynchronous Server Gateway Interface) para executar aplicacoes web em Python.

**pip**
: O instalador de pacotes do Python, usado para instalar bibliotecas e dependencias.

**requirements.txt**
: Um arquivo que lista dependencias de pacotes Python para um projeto.

**Virtual Environment (venv)**
: Um ambiente Python isolado que mantem dependencias separadas de outros projetos.

## Terminologia de testes

**Unit Test**
: Um teste que valida uma unica unidade de codigo (funcao, metodo ou classe) de forma isolada.

**Integration Test**
: Um teste que valida como multiplos componentes ou sistemas funcionam juntos.

**Test Client**
: Uma ferramenta que simula requisicoes HTTP para testar endpoints de API sem executar um servidor real.

**Assertion**
: Uma instrucao em um teste que verifica se uma condicao e verdadeira; testes falham se assercoes forem falsas.

**Test Coverage**
: Uma medida de quanto do seu codigo e executado pelos testes.

**pytest**
: Um framework popular de testes em Python usado para escrever e executar testes.

**MSTest**
: O framework de testes da Microsoft para aplicativos .NET.

**WebApplicationFactory**
: Um utilitario de testes .NET que cria um servidor de testes em memoria para testes de integracao.

## Terminologia do GitHub Copilot

**GitHub Copilot**
: Uma ferramenta de conclusao de codigo com IA que sugere codigo e funcoes inteiras em tempo real.

**Copilot Chat**
: Uma interface de chat interativa onde voce pode fazer perguntas ao GitHub Copilot e receber explicacoes.

**Context**
: As informacoes que o GitHub Copilot usa para gerar sugestoes, incluindo arquivos abertos, codigo selecionado e historico do chat.

**Prompt**
: Uma pergunta ou instrucao que voce fornece ao GitHub Copilot para gerar codigo ou obter informacoes.

**Ask Mode**
: Um modo do Copilot para obter explicacoes, fazer perguntas e aprender sobre codigo sem fazer mudancas.

**Edit Mode**
: Um modo do Copilot para fazer modificacoes direcionadas de codigo com base em instrucoes em linguagem natural.

**Agent Mode**
: Um modo autonomo do Copilot que pode planejar tarefas, fazer edicoes, executar comandos e iterar ate atingir objetivos.

**Plan Mode**
: Um modo do Copilot que ajuda a delinear tarefas e dividir trabalho complexo em etapas estruturadas.

**#file: Reference**
: Uma sintaxe no chat do Copilot (por exemplo, `#file:main.py`) que fornece contexto especifico de arquivo para melhorar a precisao das sugestoes.

**#codebase Tool**
: Um recurso do Copilot que analisa todo o repositorio para responder perguntas sobre a estrutura do projeto e o codigo.

## Ferramentas de desenvolvimento

**VS Code (Visual Studio Code)**
: Um editor de codigo leve, mas poderoso, com amplo suporte a extensoes.

**GitHub Codespaces**
: Um ambiente de desenvolvimento em nuvem que roda no navegador com ferramentas pre-configuradas.

**Git**
: Um sistema de controle de versao para rastrear mudancas no codigo e colaborar com outras pessoas.

**Terminal/Command Line**
: Uma interface baseada em texto para executar comandos e interagir com o sistema operacional.

**Port**
: Um endpoint de comunicacao numerado onde aplicativos escutam por requisicoes de rede (por exemplo, porta 8000 ou 5000).

## Conceitos gerais de programacao

**Migration**
: O processo de mover codigo de uma linguagem, framework ou plataforma para outra.

**Scaffolding**
: Gerar a estrutura basica do projeto e o boilerplate para iniciar o desenvolvimento rapidamente.

**Serialization**
: Converter estruturas de dados ou objetos para um formato (como JSON) que pode ser armazenado ou transmitido.

**Deserialization**
: Converter dados de um formato armazenado ou transmitido (como JSON) de volta para estruturas de dados ou objetos.

**Type Safety**
: Um recurso de linguagem que evita erros de tipo ao verificar tipos em tempo de compilacao.

**Compile-time**
: A fase em que o codigo-fonte e convertido para codigo executavel; erros aqui impedem problemas em runtime.

**Runtime**
: A fase em que um programa esta realmente executando; erros aqui ocorrem durante a execucao do programa.

**Dependency**
: Uma biblioteca externa ou pacote que seu projeto precisa para funcionar.

**Boilerplate Code**
: Codigo padrao e repetitivo que e necessario, mas nao contem a logica unica da sua aplicacao.

---

!!! tip "Nao encontrou um termo?"
    Se voce encontrar um termo que nao esta listado aqui, tente pedir uma definicao ao GitHub Copilot ou consulte a pagina de Resources para links para a documentacao oficial.
