# Abrindo o repositorio (Local ou GitHub Codespaces)

Escolha o fluxo de trabalho que melhor se encaixa no seu setup. Se voce estiver trabalhando localmente no seu ambiente de desenvolvimento, assumimos que todas as ferramentas necessarias ja estao instaladas (veja a pagina de Resources para um checklist rapido de pre-requisitos). Se preferir uma experiencia totalmente hospedada, siga o caminho do GitHub Codespaces.

!!! note "Participantes do evento"
    Se voce estiver participando deste workshop em um evento da Microsoft (com um ambiente de laboratorio pre-provisionado), ainda pode seguir as instrucoes de **Ambiente local** se preferir trabalhar na sua propria maquina. As etapas de Ambiente local assumem que voce fornecera quaisquer credenciais e recursos localmente em vez de usar o laboratorio do evento. Veja a orientacao do evento para detalhes sobre recursos e credenciais do laboratorio.

=== "Ambiente local"

    1. Abra a pagina do repositorio: [Real World Code Migration with GitHub Copilot Agent Mode](https://github.com/microsoft/aitour26-WRK541-real-world-code-migration-with-github-copilot-agent-mode){:target="_blank"}
    
    1. Clone o repo para uma pasta de trabalho na sua maquina:
    
        ```bash
        git clone https://github.com/microsoft/aitour26-WRK541-real-world-code-migration-with-github-copilot-agent-mode.git
        ```
    
    1. No VS Code, escolha **File > Open Folder** e selecione a pasta clonada.
    
    1. Faça login no GitHub no VS Code e garanta que o GitHub Copilot esteja habilitado. (Command Palette → **GitHub: Sign in**.)
    
    1. Restaure dependencias do projeto Python:
    
        ```bash
        cd src/python-app && pip install -r requirements.txt`
        ```
    
    1. Voce esta pronto para seguir o restante do workshop localmente. Se voce precisar da lista de ferramentas, veja a secao **Pre-requisitos para ambiente local** na pagina de Resources.

=== "GitHub Codespaces"

    1. Visite o repositorio: [Real World Code Migration with GitHub Copilot Agent Mode](https://github.com/microsoft/aitour26-WRK541-real-world-code-migration-with-github-copilot-agent-mode){:target="_blank"}
    2. Faça login na sua conta GitHub.
    3. Clique no botao **Star** no canto superior direito — isso facilita encontrar o repo depois.
    4. Clique no botao **<> Code**, abra a aba **Codespaces**, depois selecione **+** para criar um novo Codespace.
    
        ![Create a new Codespace](./media/create-new-codespace.png)
    
    5. Aguarde o Codespace concluir o provisionamento no navegador.
    6. Quando o Codespace estiver pronto, voce vera uma experiencia do VS Code no navegador. Voce pode continuar por la ou clicar em **Open in VS Code** para conectar a partir do desktop.
    
        ![Open in VS Code button](./media/open-in-vscode.png)

!!! success
    Para voltar ao workshop mais tarde, clique na sua foto de perfil no GitHub e selecione **Your stars**.
