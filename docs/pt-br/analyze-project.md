### 4. Estrategize com GitHub Copilot

> *Tente usar o GitHub Copilot em Ask Mode nesta etapa.*

Agora que voce tem um bom entendimento do projeto, voce pode comecar a estrategizar com o GitHub Copilot. Usando **Ask Mode**, faca perguntas sobre por que os testes Python podem ser uteis ao reescrever o projeto em C#.

- Peça ao GitHub Copilot um resumo dos testes

??? question "Tip"
    Prompt *(Ask Mode)*

    ```text
    #file:test_main.py provide a summary of the tests for the python application in this repository
    ```

- Peça ao GitHub Copilot para explicar por que os testes sao uma boa forma de validar a migracao para C#

??? question "Tip"
    Prompt *(Ask Mode)*

    ```text
    #file:test_main.py why are the Python tests in test_main.py a good way to validate the C# rewrite?
    ```

- Peça sugestoes de como reescrever corretamente este projeto em C#

!!! note
    As vezes, o GitHub Copilot pode ficar ansioso para fornecer muita informacao, incluindo arquivos inteiros com codigo. Isso provavelmente nao e o que voce quer ao tentar pensar nas suas opcoes.
    Garanta que voce diga ao Copilot para evitar gerar codigo ao fazer brainstorming e estrategia.

??? question "Tip"
    Prompt *(Ask Mode)*

    ```text
    Just provide suggestions on how to properly rewrite this project in C#.
    Keep this high level.
    Do not change any code.
    ```

### 5. Identifique testes faltantes

Os testes Python podem nao estar completos e pode haver casos ausentes. Use o GitHub Copilot para identificar os testes faltantes. Isso ajuda a obter cobertura completa do aplicativo antes de comecar a reescrever em C#.

Para esta etapa, voce deve usar **Agent Mode**.

- Abra o arquivo de testes (`test_main.py`) e peça ao GitHub Copilot para identificar testes faltantes
- Implemente os testes faltantes
- Execute os testes para garantir que estao passando, corrija quaisquer problemas que surgirem

??? question "Tip"
    Prompt *(Agent Mode)*

    ```text
    Analyze the python application.
    Help me run the Python tests in src/python-app/webapp/test_main.py and check that they pass.
    In case of failure, help me address the failures to get the tests passing
    ```
