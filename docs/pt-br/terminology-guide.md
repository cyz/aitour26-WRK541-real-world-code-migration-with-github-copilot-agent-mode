# Guia de Terminologia para Documentacao

Este guia estabelece terminologia consistente para a documentacao do workshop WRK541 para garantir clareza e profissionalismo.

## Nomes oficiais de produtos

### Sempre use nomes completos na primeira referencia

**GitHub Copilot**
: Use o nome completo "GitHub Copilot" na primeira mencao em cada documento, depois "Copilot" nas mencoes seguintes.
: ✅ Correto: "GitHub Copilot ajuda voce a escrever codigo. Copilot usa IA..."
: ❌ Incorreto: "Copilot ajuda voce a escrever codigo" (na primeira mencao)

**ASP.NET Core Minimal APIs**
: Sempre capitalize "ASP.NET Core" e "Minimal APIs"
: ✅ Correto: "ASP.NET Core Minimal APIs"
: ❌ Incorreto: "Asp.net core minimal apis" ou "minimal API"

**FastAPI**
: Escreva como uma unica palavra com F maiusculo e API
: ✅ Correto: "FastAPI"
: ❌ Incorreto: "Fast API" ou "fast-api"

**.NET**
: Sempre inclua o ponto antes de NET e use letras maiusculas
: ✅ Correto: ".NET 10" ou ".NET SDK"
: ❌ Incorreto: "dotnet" ou "Net" (exceto ao se referir ao comando `dotnet`)

**Visual Studio Code**
: Use o nome completo na primeira referencia, depois "VS Code"
: ✅ Correto: "Visual Studio Code" (primeiro uso), "VS Code" (usos seguintes)
: ❌ Incorreto: "VSCode" ou "Visual Studio" (produto diferente)

## Modos do Copilot

Sempre capitalize os nomes dos modos ao se referir a recursos especificos do Copilot:

- **Ask Mode** (nao "ask mode" ou "Ask mode")
- **Edit Mode** (nao "edit mode")
- **Agent Mode** (nao "agent mode")
- **Plan Mode** (nao "plan mode")

Exemplo: "Use Agent Mode para criar o scaffolding do projeto" ✅

## Nomes de frameworks e bibliotecas

**Python**
: Sempre capitalizado
: ✅ "Python 3.12"
: ❌ "python"

**C#**
: Use C maiusculo seguido do simbolo #
: ✅ "C#"
: ❌ "c#" ou "csharp" (exceto em caminhos de arquivo)

**JSON**
: Sempre em maiusculas
: ✅ "Arquivo JSON"
: ❌ "json" ou "Json"

**Swagger**
: Capitalize ao se referir a ferramenta
: ✅ "Documentacao Swagger"

**OpenAPI**
: Capitalize O e API
: ✅ "Especificacao OpenAPI"
: ❌ "Open API" ou "openapi"

## Frameworks de teste

**pytest**
: Minusculo, uma palavra
: ✅ "pytest"
: ❌ "PyTest" ou "Pytest"

**MSTest**
: MS maiusculo seguido de T maiusculo
: ✅ "MSTest"
: ❌ "mstest" ou "Ms Test"

## Referencias a arquivos e codigo

**Program.cs**
: Use a capitalizacao exata ao se referir ao arquivo
: ✅ "`Program.cs`"
: ❌ "`program.cs`" ou "Program.CS"

**main.py**
: Use minusculas ao se referir ao arquivo
: ✅ "`main.py`"
: ❌ "`Main.py`"

**weather.json**
: Use minusculas para arquivos de dados
: ✅ "`weather.json`"

## Termos tecnicos

**API Endpoint**
: Duas palavras, capitalizar quando iniciar uma frase
: ✅ "O API endpoint retorna dados de clima"
: ❌ "api-endpoint" ou "APIEndpoint"

**Repository/Repo**
: Use "repository" em documentacao formal, "repo" em contextos informais
: ✅ "Clone o repository" (formal)
: ✅ "O repo contem..." (informal)

**GitHub Codespaces**
: Duas palavras, ambas capitalizadas
: ✅ "GitHub Codespaces"
: ❌ "Github Codespaces" ou "GitHub codespaces"

**Port Number**
: Use "porta" ao se referir a portas de rede
: ✅ "porta 8000"
: ❌ "Port: 8000" ou "PORT 8000" (exceto em variaveis de ambiente)

## Ferramentas de linha de comando

**dotnet**
: Minusculo ao se referir ao comando
: ✅ "`dotnet build`"
: ❌ "`Dotnet build`" ou "`DOTNET build`"

**git**
: Minusculo ao se referir ao comando
: ✅ "`git status`"
: ❌ "`Git status`"

**pip**
: Minusculo
: ✅ "`pip install`"
: ❌ "`PIP install`"

## Estilo de documentacao

### Capitalizacao em titulos

Use Title Case para titulos principais:
✅ "Understanding the Project"
❌ "Understanding The Project" (nao capitalizar artigos)

### Listas e bullets

- Comece cada bullet com letra maiuscula
- Termine com ponto se for uma frase completa
- Sem ponto se for fragmento ou palavra unica

### Blocos de codigo

Sempre especifique a linguagem para syntax highlighting:

✅ 
```csharp
var app = WebApplication.Create();
```

✅ 
```python
app = FastAPI()
```

## Erros comuns a evitar

| ❌ Incorreto | ✅ Correto | Observacao |
|--------------|-----------|------------|
| Copilot Chat | GitHub Copilot Chat | Use nome completo primeiro |
| .Net | .NET | Deve ser capitalizado |
| Minimal api | Minimal API | Capitalize API |
| fast api | FastAPI | Uma palavra |
| Github | GitHub | H maiusculo |
| VScode | VS Code | Espaco entre |
| Csharp | C# | Use # |

## Numeros de versao

Sempre inclua numero de versao quando relevante:

✅ "Python 3.12"
✅ ".NET 10"
✅ "VS Code 1.85"
❌ "Python 3"
❌ ".NET"

## Plataforma e referencias de SO

**Windows**
: ✅ "Windows 10/11"

**macOS**
: ✅ "macOS" (mac minusculo, OS maiusculo)
: ❌ "MacOS" ou "Mac OS"

**Linux**
: ✅ "Linux" ou "Ubuntu 20.04"

## Resumo

Terminologia consistente melhora:
- **Profissionalismo**: nomes corretos de produtos mostram atencao a detalhes
- **Clareza**: leitores sabem exatamente ao que voce se refere
- **Facilidade de busca**: termos corretos ajudam usuarios a encontrar informacoes
- **Credibilidade**: uso correto demonstra expertise

Em caso de duvida, consulte a documentacao oficial do produto para a grafia e capitalizacao corretas.
