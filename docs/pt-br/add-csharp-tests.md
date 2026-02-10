# Adicionando testes em C#

### 11. Finalizando o projeto com testes em C#

Agora que voce validou todos os endpoints com testes Python, voce pode opcionalmente adicionar testes nativos em C# para validar a corretude diretamente no codebase C#. Os testes Python foram suficientes para validar Python e C# usando a API HTTP. Mas se voce quiser, pode usar testes MSTest (ou xUnit/NUnit) para validar a corretude do projeto C# com seus proprios testes.

- Pergunte ao Copilot onde voce pode adicionar testes para o projeto C#. Testes normalmente ficam em um projeto de testes separado (por exemplo, `WeatherApi.Tests`).
- Pergunte como executar os testes para validacao
- Voce pode adotar a abordagem de adicionar um teste por vez e validar. Esse e o mesmo processo de antes e vai ajudar voce a focar em uma coisa de cada vez.
- Ou voce pode pedir ao Copilot para criar o projeto de testes inteiro e adicionar testes para todos os endpoints de uma vez.

Tente usar Plan Mode nesta etapa. Lembre-se, primeiro voce deve pedir ao GitHub Copilot para criar um plano com seus requisitos, e uma vez que o plano esteja criado e validado, voce pode pedir para executar o plano.

??? question "Tip"
    Prompt *(Plan Mode)*

    ```text
    Now that we have all endpoints in C# I want native C# unit tests using MSTest.
    Create a test project so that I can verify correctness with C# tests alongside the Python tests.
    If not existing, create a new solution at the root of the c# app [src\csharp-app] and add the main project and the new test project to it.
    Create tests for each endpoint, one at a time, and validate them.
    ```

Voce deve ter um aplicativo C# totalmente funcional e bem testado agora.
Se voce chegou ate aqui, parabens! Voce pode tentar realizar essas tarefas antes que o tempo acabe ou tentar depois no seu proprio tempo.
