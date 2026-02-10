Agora que voce tem o scaffolding, pode comecar criando um unico endpoint. Use o Copilot para sugerir a primeira versao do arquivo `Program.cs`, que vai conter seu primeiro endpoint. Garanta que o Copilot entenda que nao deve gerar o arquivo inteiro, apenas o endpoint principal `/`.

### 6. Crie um unico endpoint

- Abra o arquivo `Program.cs` e peça ao Copilot para gerar *apenas* o endpoint `/`

!!! important
    Voce pode ficar tentado a pedir para o Copilot gerar o arquivo inteiro, mas voce deve validar cada parte conforme avanca. E mais facil validar pequenas partes do que um arquivo inteiro com varios endpoints e logica.

??? question "Tip"
    Prompt *(Agent Mode)*

    ```text
    #file:Program.cs add the root of the API only.
    This is the '/' endpoint, do not generate other endpoints yet, focus only on the single root endpoint for now.
    ```

O codigo minimo para o endpoint raiz deve ser assim:

```csharp
var builder = WebApplication.CreateBuilder(args);

var app = builder.Build();

if (app.Environment.IsDevelopment())
{
    app.UseDeveloperExceptionPage();
}

app.MapGet("/", () => Results.Ok(new { message = "Welcome to the C# minimal API root." }))
   .WithName("Root");

app.Run();
```

### 7. Valide seu primeiro endpoint em C#

Agora que voce tem o primeiro endpoint em C#, e hora de validar. Esse processo de criar codigo e validar e iterativo e uma pratica solida quando voce precisa desenvolver um novo projeto. E ainda mais crucial agora que voce esta reescrevendo um projeto em uma nova linguagem.

- Garanta que o projeto Python nao esteja mais em execucao
- Peça ajuda ao Copilot para executar o projeto C# no mesmo endereco e porta do projeto Python para que os testes possam rodar
- Execute os testes Python para garantir que estao passando, corrija quaisquer problemas que surgirem

- Voce pode abrir 2 terminais e executar estes comandos:
- No primeiro terminal, execute o app C#:

```bash
cd src/csharp-app
dotnet run --urls "http://localhost:8000"
```

- No segundo terminal, execute os testes Python:

```bash
cd src/python-app/webapp
pytest test_main.py -v
```

??? question "Tip"
    Prompt *(Agent Mode)*

    ```text
    Please stop any process on port `8000`, then start the C# minimal API in `src\csharp-app` with `ASPNETCORE_URLS=http://0.0.0.0:8000`. Do not change any C# code.
    Start the C# app in the foreground in one terminal and open a second terminal to run the Python tests so they can execute while the app is running.
    In the second terminal, run the Python tests from `src/python-app/webapp/test_main.py` using pytest. Only verify the `/` endpoint for now and report the test output.
    Use the workspace root and a shell.
    ```

### 8 Implemente os endpoints restantes

Implemente todos os outros endpoints usando Agent Mode ou Plan Mode. Em cada cenario, adicione tambem as anotacoes do Swagger correspondentes.

#### 8.1 Continue com todos os endpoints usando Agent Mode

Use o mesmo processo acima para criar todos os outros endpoints. Adicione um endpoint por vez, valide, e execute os testes Python para garantir compatibilidade.

!!! important
    Durante esse processo, o GitHub Copilot vai pedir sua aprovacao antes de realizar varias acoes, como:

    - Editar arquivos (Program.cs, weather.json, etc.)
    - Executar comandos no terminal
    - Criar novos arquivos ou diretorios
    - Instalar pacotes ou dependencias
    
    Fique atento as solicitacoes do Copilot e aprove as acoes conforme necessario. Revise cada mudanca proposta cuidadosamente para garantir que o Copilot esta implementando a solucao corretamente. Sua participacao ativa ajuda o Copilot a concluir a tarefa com sucesso.

!!! tip
    Ao implementar o proximo endpoint - por exemplo, '/countries' - especifique no seu prompt ao Copilot que ele deve usar os mesmos dados usados pelo app Python, hospedados no arquivo 'weather.json'.

Para o arquivo JSON, voce precisara desserializa-lo. Se voce nao estiver familiarizado com esse processo, precisara se apoiar nas orientacoes do Copilot. Garanta que voce gere o menor codigo possivel e valide imediatamente.

!!! success "Validar partes menores do codigo e mais facil do que validar um arquivo inteiro. Tambem e mais facil debugar partes menores do codigo. Essa e uma boa pratica ao usar o GitHub Copilot e vai ajudar voce no longo prazo."

#### 8.2 Implementacao usando Plan Mode

> *Voce pode tentar usar o GitHub Copilot em Plan Mode nesta etapa.*

Ao implementar os proximos endpoints, voce pode usar **Plan Mode** para ajudar a definir as etapas necessarias para cada endpoint. Esse modo ajuda a dividir a implementacao em tarefas gerenciaveis.

Vamos comecar pedindo ao GitHub Copilot para ajudar a planejar a implementacao dos endpoints faltantes.

??? question "Tip"
    Prompt *(Plan Mode)*

    Analyze the other endpoints in the #file:main.py and implement this in the #file:Program.cs file using .NET Minimal APIs.
    Implement the swagger annotations for each endpoint.
    The root of the API should redirect to the swagger UI page.

Uma vez que o plano estiver pronto, voce deve ver o plano, e pode pedir ao GitHub Copilot para comecar a implementar os passos mudando para **Agent Mode** e pedindo para seguir o plano passo a passo.

!!! important
    Conforme o Copilot executa o plano, ele vai pedir sua aprovacao para varias acoes:

    - Modificacoes em arquivos (editar Program.cs, adicionar classes de modelo, etc.)
    - Comandos de terminal (executar comandos dotnet, testes, etc.)
    - Criacao de arquivos (novas classes, arquivos de configuracao)
    - Instalacao de pacotes
    
    Acompanhe de perto a janela do Copilot e revise cada acao proposta antes de aprovar. Esse processo interativo garante que o Copilot siga o caminho correto e permite que voce identifique problemas cedo. Sua orientacao ajuda o Copilot a concluir a implementacao com sucesso.

![Start Implementation](./media/start_plan_implementation.png){ target="_blank" }
