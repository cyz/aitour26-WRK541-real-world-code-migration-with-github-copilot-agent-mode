# Entendendo o Projeto

Antes de comecar a migrar codigo, e crucial entender com o que estamos trabalhando.

## Comece com o projeto Python

Familiarize-se com o projeto e sua estrutura. O arquivo principal e o `main.py`, localizado no diretorio `src`, dentro da pasta `python-app\webapp`. Esse arquivo contem a logica principal da aplicacao.

### 1. Explore o projeto

> *Tente usar o GitHub Copilot em Ask Mode nesta etapa.*

Primeiro, abra o GitHub Copilot pressionando `Ctrl + Alt + I` no Windows, ou `Command + Shift + I` no Mac, e garanta que voce esta no **Ask** Mode:

![An image showcasing the three different modes within the GitHub Copilot Chat window](./media/chat-mode-dropdown-ask.png)

!!! Note
    O GitHub Copilot e baseado em LLMs e, portanto, tem comportamento nao deterministico; voce pode obter respostas diferentes para o mesmo prompt. Os prompts sugeridos neste repo foram testados com o modelo **GPT-5-mini**, entao voce pode escolher esse modelo no menu suspenso. No entanto, voce tambem pode explorar outros modelos.

![Model choice dropdown](./media/model-picker.png)

Use a ferramenta `#codebase` para fornecer contexto ao Copilot e explicar o que esta acontecendo neste projeto.

- Abra o GitHub Copilot Chat e prefixe seu prompt com `#codebase`
- Faca perguntas como: como executar o projeto

??? question "Tip"

    Prompt (Ask Mode)

    ```text
    #codebase provide me a detailed summary of what this Python project is about
    ```

### 2. Determine os endpoints da API

> *Tente usar o GitHub Copilot em Ask Mode nesta etapa.*

Em seguida, vamos iniciar o projeto e executar o aplicativo web. Use o GitHub Copilot chat com o arquivo `main.py` aberto, ou digite `#main.py` para fornecer contexto e pergunte sobre os endpoints.

!!! tip "Quando a saida do Copilot incluir um comando de terminal, voce pode clicar no botao no canto superior direito para colar diretamente no terminal. ![Paste to terminal](./media/paste_to_terminal.png)"

- Pergunte como executar o aplicativo web

??? question "Tip"

    Prompt (Ask Mode)

    ```text
    #main.py how do I run the python webapp?
    ```

- Tente executar o projeto com base nas sugestoes do Copilot

!!! tip
    Voce precisara de um terminal aberto e do **uvicorn** para executar a aplicacao FastAPI.

!!! warning
    Se voce estiver recebendo a mensagem "Error loading ASGI app. Could not import module (...)", garanta que o caminho sugerido pelo Copilot aponta para o arquivo correto (main.py).
    Certifique-se de estar no diretorio correto: `src\python-app\webapp` para executar o app.

- Veja todos os endpoints e seus tipos de requisicao, acessando a pagina do Swagger UI cujo URL e exibido na saida de inicializacao do app.

!!! tip "Dê uma olhada no arquivo [weather.json](https://github.com/microsoft/aitour26-WRK541-real-world-code-migration-with-github-copilot-agent-mode/blob/main/src/python-app/webapp/weather.json) para conferir os parametros permitidos para testar os endpoints."

### 3. Explore e execute os testes Python

> *Tente usar o GitHub Copilot em Agent Mode nesta etapa.*

Os testes estao no arquivo `src/python-app/webapp/test_main.py`. Esse arquivo de testes em Python usa o TestClient do FastAPI para validar os endpoints da API. Execute os testes e inspecione a saida.

Com o app ja em execucao em um terminal, abra um novo terminal e execute os testes Python com pytest:

```bash
cd src/python-app/webapp
pytest test_main.py -v
```

- Se algum teste nao estiver passando, use o GitHub Copilot para ajudar a corrigir e depois execute novamente.

!!! note
    Esses testes usam requisicoes HTTP e exigem que o aplicativo esteja em execucao antes de executar os testes. Os testes serao automaticamente ignorados se o app nao estiver em execucao no BASE_URL configurado (padrao: <http://localhost:8000>).

    Esses mesmos testes serao usados para validar o app C# ao definir a variavel de ambiente BASE_URL para corresponder a porta do app C# (por exemplo, `$env:BASE_URL="http://localhost:5000"` no Windows ou `export BASE_URL="http://localhost:5000"` no Linux/Mac).
