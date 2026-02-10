# Criar Scaffolding em C#

> *Voce deve usar o GitHub Copilot em Agent Mode para esta etapa e as seguintes.*

Agora que voce tem um bom entendimento do projeto e de seus testes, voce pode comecar a criar o scaffolding em C#. Voce vai iniciar criando um arquivo especial com instrucoes. Esse arquivo se chama *Copilot Instructions* e deve ficar na pasta [.github\instructions]. Ja criamos um arquivo vazio para voce, entao basta preenche-lo com novas instrucoes.

Para esta etapa, abra o arquivo `.github\instructions\instructions.md` e adicione o seguinte:

```markdown
# C# .NET 10 WebApi Migration Instructions

## Overview

This guide helps developers migrate the Python Weather API to C# .NET 10 using ASP.NET Core Minimal APIs.

## Requirements

- **Framework**: ASP.NET Core Minimal APIs (.NET 10)
- **JSON Serialization**: System.Text.Json (built-in)
- **API Documentation**: Swashbuckle (OpenAPI/Swagger support)

## Development Workflow

- **Build**: `dotnet build`
- **Run**: `dotnet run`
- **Test**: `dotnet test` (tests in `WeatherApi.Tests` directory)
- **API Docs**: Available at `/swagger` endpoint when running

## C# API Guidelines

- Use **Minimal APIs** for endpoint definitions in `Program.cs`
- Use **System.Text.Json** for all serialization
- Add Swashbuckle attributes to endpoints for automatic Swagger documentation
- Follow PascalCase for class names, camelCase for methods
- Example: See `src/csharp-app/WeatherApi/Program.cs`

## Key Files

- `src/csharp-app/WeatherApi/Program.cs` - API configuration and endpoints
- `src/csharp-app/WeatherApi.Tests/` - Unit tests
- `src/csharp-app/WeatherApi/Models.cs` - Data models
- `src/csharp-app/WeatherApi/weather.json` - Sample data
```

??? warning
     Criar uma nova conversa neste ponto pode ser util. Isso limpa parte do contexto anterior e permite que o GitHub Copilot comece do zero. Se quiser fazer isso, basta clicar no botao ![New Chat Button on GitHub Copilot](./media/copilot-newchat.png) no topo da janela de chat do Copilot.

Como vamos realizar um conjunto mais complexo de tarefas, vamos trabalhar em **Agent Mode**. Depois de mudar para esse modo, peça ao GitHub Copilot para criar o scaffolding necessario para seu projeto C#. Peça tambem um passo a passo para iniciar o projeto e os comandos para comecar.

??? question "Tip"
     Prompt *(Agent Mode)*

    ```text
    Create a new folder named `csharp-app` in the `src` directory.
    Create the C# scaffolding in csharp-app folder, where we are going to migrate the python project.
    Use .NET Minimal APIs.
    Don't perform any code migration for now.
    Provide me with guided steps to run the project afterwards.
    Create the minimal code necessary to have a running C# .NET 10 Web API project.
    ```

Depois que o GitHub Copilot criar o scaffolding, verifique os arquivos criados na pasta `csharp-app`. Voce deve ver um arquivo `.csproj` e um arquivo `Program.cs`.

(Opcional) Peça ao GitHub Copilot para esclarecer qualquer duvida que voce tenha sobre os arquivos criados e seu proposito.
