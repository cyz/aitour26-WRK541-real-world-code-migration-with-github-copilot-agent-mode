# Validar corretude e adicionar mais endpoints

### 9. Validar corretude

Quando voce tiver todos os endpoints em C# com os testes Python passando, entao voce pode pedir ao Copilot para fazer uma revisao do arquivo inteiro. Identifique possiveis alertas e problemas ou questões de performance. Por exemplo, imagine se cada endpoint desserializa o arquivo toda vez. Isso e um problema de performance e voce pode pedir ao Copilot para identifica-lo.

??? question "Tip"
    Prompt *(Agent Mode)*

    ```text
    Identify any potential problems with my Program.cs file.
    Specifically I am interested in understanding redundancy and any code that is doing unnecessary work.
    Do not generate any code, just explain.
    ```

### 10. Adicione mais endpoints com testes

Finalmente, voce tem um mapeamento 1:1 do projeto Python para o projeto C#. Agora voce pode comecar a adicionar mais endpoints e testes. Por exemplo, o endpoint `/countries/{country}`. Esse endpoint nao esta presente no projeto Python, mas voce pode adiciona-lo no projeto C#.

- Com o arquivo `Program.cs` aberto, pergunte ao Copilot sobre outros endpoints possiveis
- Abra o arquivo `test_main.py` no app Python e peça ao Copilot para adicionar mais testes para os novos endpoints
- Execute os testes para garantir que estao passando, corrija quaisquer problemas que surgirem

??? question "Tip"
    Prompt *(Ask Mode)*

    ```text
    The C# API now has full parity with the Python application, but I want you to
    suggest me other potential endpoints that might be useful.
    ```

??? question "Tip"
    Prompt *(Agent Mode)*

    ```text
    #file:Program.cs implement /countries/{country} endpoint and add a test to assess it.
    ```
