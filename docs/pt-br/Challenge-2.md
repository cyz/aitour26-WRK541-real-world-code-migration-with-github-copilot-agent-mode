# Desafios Bonus

## Desafio 2: Integracao com Banco de Dados usando Entity Framework Core

**Dificuldade:** 🔥🔥 Avancado

!!! info
    Leve este desafio adiante substituindo a fonte de dados JSON estatica por um banco de dados real.

Neste desafio, voce vai aprimorar a API de clima em C# substituindo o arquivo JSON estatico por um banco SQL Server ou SQLite usando Entity Framework Core (EF Core). Esse e um cenario realista onde voce aprende a trabalhar com persistencia de dados, migrations e operacoes async no banco.

### Objetivos de aprendizagem

Ao concluir este desafio, voce vai:

- Entender como integrar o Entity Framework Core em uma ASP.NET Core Minimal API
- Criar modelos de dados e um DbContext para gerenciar operacoes de banco
- Aprender sobre migrations e gerenciamento de schema
- Implementar padroes async/await para consultas ao banco
- Usar injecao de dependencia para padroes de repositorio

#### Etapas do desafio

**Passo 1: Configurar Entity Framework Core**

Use o GitHub Copilot em Agent Mode para:

1. Adicionar os pacotes NuGet do Entity Framework Core ao seu projeto C# (por exemplo, `Microsoft.EntityFrameworkCore`, `Microsoft.EntityFrameworkCore.Sqlite` ou `Microsoft.EntityFrameworkCore.SqlServer`)
2. Criar modelos de dados apropriados (entidades Country, Weather, City) com base na estrutura do `weather.json`
3. Criar uma classe `WeatherDbContext` que herda de `DbContext` e define as tabelas do banco

!!! tip
    Peça ao Copilot para analisar o arquivo `weather.json` e sugerir modelos e relacionamentos de entidades apropriados.

**Passo 2: Configurar banco e criar migrations**

Use Agent Mode para:

1. Configurar a conexao do banco em `Program.cs`
2. Criar uma migration inicial usando `dotnet ef migrations add`
3. Atualizar o schema do banco usando `dotnet ef database update`

!!! important
    Acompanhe as acoes do Copilot quando ele modificar seu `Program.cs` e criar arquivos de migration. Revise o codigo de migration gerado para entender as mudancas de schema que estao sendo aplicadas.

**Passo 3: Semear dados iniciais**

Use Agent Mode para:

1. Criar um mecanismo de seed que popula o banco com os dados de clima do `weather.json`
2. Chamar a logica de seed durante o startup da aplicacao

!!! note
    Voce pode semear dados a partir do JSON existente para garantir que o banco contenha as mesmas informacoes da fonte de dados estatica original.

**Passo 4: Atualizar endpoints para usar o banco**

Use Agent Mode para atualizar seus endpoints para:

1. Injetar `WeatherDbContext` nos handlers dos endpoints
2. Substituir leituras do arquivo JSON por consultas ao banco via EF Core
3. Usar async/await para todas as operacoes de banco
4. Garantir que todos os endpoints retornem as mesmas respostas de antes

!!! success
    Depois de atualizar os endpoints, execute os testes Python para garantir que a API ainda funciona corretamente com o backend de banco de dados.

**Passo 5: Validacao e testes**

Use a suite de testes Python para validar que:

1. O endpoint `/` retorna 200
2. O endpoint `/countries` retorna a lista correta de paises
3. O endpoint de clima retorna dados corretos para paises validos
4. Paises invalidos continuam retornando 404

Execute os testes como antes:

```bash
cd src/python-app/webapp
pytest test_main.py -v
```

### Melhorias opcionais

- Adicionar filtragem e paginacao ao endpoint de paises
- Implementar um modelo de dados mais sofisticado com relacionamentos
- Criar testes unitarios em C# usando xUnit com DbContext mockado
- Adicionar otimizacoes de performance com indexacao
