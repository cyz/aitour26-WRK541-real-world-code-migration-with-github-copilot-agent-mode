# Criar Scaffolding em Rust

> *Voce deve usar o GitHub Copilot em Agent Mode para esta etapa e as seguintes.*

Agora que voce tem um bom entendimento do projeto e de seus testes, voce pode comecar a criar o scaffolding em Rust. Voce vai iniciar criando um arquivo especial com instrucoes. Esse arquivo se chama _Copilot Instructions_ e deve ficar na raiz do repositorio atual. Ja criamos um arquivo vazio para voce, entao basta preenche-lo com novas instrucoes.

Para esta etapa, abra o arquivo `.github/copilot-instructions.md` e adicione o seguinte:

```markdown
Whenever you are providing suggestions for a Rust project always use the
actix-web framework using serde for serialization
```

??? warning
     Criar uma nova conversa neste ponto pode ser util. Isso limpa parte do contexto anterior e permite que o GitHub Copilot comece do zero. Se quiser fazer isso, basta clicar no botao ![New Chat Button on GitHub Copilot](./media/copilot-newchat.png) no topo da janela de chat do Copilot.

Como vamos realizar um conjunto mais complexo de tarefas, vamos sair do **Edit Mode** e trabalhar apenas em **Agent Mode**. Depois de mudar, peça ao GitHub Copilot para criar o scaffolding necessario para seu projeto Rust. Peça tambem um passo a passo para iniciar o projeto e os comandos para comecar.

??? question "Tip"
     Prompt *(Agent Mode)*

     ```text
     #file:rust-app create the Rust scaffolding in rust-app folder, where we are going to migrate the python project. Don't perform any code migration for now. Provide me with guided steps to run the project afterwards.
     ```

O framework e o serializer devem ser incluidos automaticamente sem que voce precise especifica-los. Esse arquivo pode ser usado para qualquer outra instrucao que voce nao queira repetir.

Depois que o GitHub Copilot criar o scaffolding, verifique os arquivos criados na pasta `rust-app`. Voce deve ver um arquivo `Cargo.toml` e uma pasta `src` com um arquivo `main.rs`.
Peça ao GitHub Copilot para esclarecer qualquer duvida que voce tenha sobre os arquivos criados e seu proposito.
