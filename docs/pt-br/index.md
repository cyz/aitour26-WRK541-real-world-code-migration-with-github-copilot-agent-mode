# WRK541 - Migracao de Codigo do Mundo Real com GitHub Copilot Agent Mode

![Microsoft AI Tour Banner](./media/aitour-banner.png)

### Realize uma migracao desafiadora para uma linguagem completamente diferente

- **Para quem e**: Qualquer profissional de tecnologia que queira aplicar tecnicas de pair-programming com IA usando o GitHub Copilot para tarefas complexas como migrar ou traduzir de uma linguagem para outra.
- **O que voce vai aprender**: Voce vai usar tecnicas avancadas do GitHub Copilot que sao especialmente uteis ao traduzir projetos entre linguagens diferentes, alem de conhecer os modos que o GitHub Copilot oferece.
- **No que voce vai trabalhar**: Uma API HTTP usada para coletar dados sazonais de clima, usando C# com .NET Minimal APIs e compatibilidade total com a API HTTP original escrita em Python.

## Objetivos de Aprendizagem

Neste workshop, voce vai:

- Aprender as diferencas entre cada um dos modos do GitHub Copilot, quando usar cada um, boas praticas e ferramentas para aproveitar ao maximo suas interacoes.
- Entender as diferencas entre Python e C# para desenvolvimento web.
- Aprender as principais diferencas de sintaxe, bibliotecas e frameworks ao transicionar do FastAPI em Python para o ASP.NET Core Minimal APIs em C#.
- Implementar serializacao e desserializacao de JSON em C#.
- Ganhar experiencia pratica usando System.Text.Json para lidar com dados JSON, garantindo compatibilidade com a API Python original.
- Desenvolver e validar endpoints incrementalmente em C#.
- Praticar a criacao e teste de endpoints individualmente, garantindo corretude e alinhamento com a API Python original.
- Integrar documentacao Swagger/OpenAPI: aprender a adicionar documentacao completa com Swashbuckle e o suporte nativo do ASP.NET Core a OpenAPI.

## 📣 Pre-requisitos

Antes de participar do workshop, ha apenas um pre-requisito: voce deve ter sua propria conta GitHub. Todos os recursos, dependencias e dados fazem parte do proprio repositorio. Garanta que voce tem uma licenca do GitHub Copilot, trial ou a versao gratuita.

### ✅ Antes de comecar - Checklist rapido

Garanta que voce tem o seguinte pronto antes de iniciar o workshop:

- [ ] **Conta GitHub**: Voce tem uma conta GitHub criada e consegue fazer login
- [ ] **Acesso ao GitHub Copilot**: Voce tem o GitHub Copilot habilitado (assinatura paga, trial ou versao gratuita)
- [ ] **Escolha do ambiente**: Voce decidiu entre:
  - ☁️ **GitHub Codespaces** (recomendado - zero configuracao)
  - 💻 **Desenvolvimento local** (requer Python 3.12, .NET 10 SDK, VS Code - veja [resources.md](./resources.md) para detalhes)
- [ ] **Para setup local**: Todos os pre-requisitos estao instalados e verificados (se voce escolheu desenvolvimento local)

!!! tip "Nao sabe qual ambiente escolher?"
    Recomendamos GitHub Codespaces para este workshop, pois ele fornece um ambiente pre-configurado com todas as ferramentas prontas. Sem necessidade de instalacao!

### Criando uma conta GitHub

Se voce ainda nao tem uma conta GitHub, voce pode criar uma gratuitamente seguindo as instrucoes abaixo.

1. Acesse a pagina de cadastro do GitHub: <https://github.com/join>.
2. Informe seu email, crie uma senha e escolha um nome de usuario. Recomendamos usar um *email pessoal* em vez de um email corporativo para simplificar o processo de cadastro.
3. Selecione seu Pais/Regiao e aceite os termos de servico.
4. Clique no botao **Create account** e aguarde o email de verificacao chegar na sua caixa de entrada.

    ![GitHub Account Sign Up](./media/github_signup.png)

5. Copie o codigo de verificacao do email e cole no campo de verificacao no site do GitHub. Em seguida, clique em **Continue**.
6. Pronto! Agora voce esta pronto para comecar.

Vamos comecar clicando no *botao Next* no canto inferior direito, que diz **"Workshop Navigation"**.
