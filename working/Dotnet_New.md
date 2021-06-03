# dotnet new

Este artigo se aplica a: ✔️ SDK do .NET Core 2.0 e versões posteriores

## Name

*dotnet new* – Cria um novo projeto, arquivo de configuração ou solução com base no modelo especificado.

## Sinopse

*CLI do .NET*

dotnet new <TEMPLATE> [--dry-run] [--force] [-lang|--language {"C#"|"F#"|VB}] 
    [-n|--name <OUTPUT_NAME>] [-o|--output <OUTPUT_DIRECTORY>] [Template options]

dotnet new -h|--help

## Descrição

O *dotnet new* comando cria um projeto .NET ou outros artefatos com base em um modelo.

O comando chama o mecanismo de modelo para criar os artefatos em disco com base no modelo e nas opções especificadas.

## Restauração implícita

Você não precisa executar *dotnet restore* o porque ele é executado implicitamente por todos os comandos que exigem a ocorrência de uma restauração, como,,,, dotnet new dotnet build dotnet run dotnet test dotnet publish e dotnet pack . Para desabilitar a restauração implícita, use a --no-restore opção.

O dotnet restore comando ainda é útil em determinados cenários em que a restauração explícita faz sentido, como compilações de integração contínua em Azure DevOps Services ou em sistemas de compilação que precisam controlar explicitamente quando a restauração ocorre.

Para obter informações sobre como gerenciar feeds do NuGet, consulte a dotnet restore documentação.

## Argumentos

- TEMPLATE

O modelo para o qual criar uma instância quando o comando é invocado. Cada modelo pode ter opções específicas que podem ser passadas. Para obter mais informações, consulte Opções de modelo.

Você pode executar *dotnet new --list* para ver uma lista de todos os modelos instalados.

Começando com o SDK do .NET Core 3.0 e terminando com o SDK do .NET Core 5.0.300, a CLI pesquisa modelos no NuGet.org quando você invoca o comando nas *dotnet new* seguintes condições:

- Se a CLI não conseguir encontrar uma combinação de modelo ao invocar *dotnet new* , nem mesmo parcial.
- Se houver uma versão mais recente do modelo disponível. Nesse caso, o projeto ou artefato é criado, mas a CLI avisa sobre uma versão atualizada do modelo.

A partir do SDK do .NET Core 5.0.300, a opção deve ser usada para pesquisar modelos no NuGet.org.. **--search**

A tabela a seguir mostra os modelos que vêm pré-instalados com o SDK do .NET. O idioma padrão do modelo é mostrado entre parênteses. Clique no link de nome curto para ver as opções de modelo específicas.

### ARGUMENTOS
| Modelos	| Nome curto	| Idioma	| Marcações	| Introduzida |
|---|---|---|---|---|
| Aplicativo do Console	|console	| [C#], F#, VB	| Comum/Console	| 1.0 |
| Biblioteca de classes	| classlib	| [C#], F#, VB	| Comum/Library	| 1.0 | 
| Aplicativo WPF	| wpf	| [C#], VB	| Common/WPF	| 3.0 (5.0 para VB) | 
| Biblioteca de classes do WPF	| wpflib	| [C#], VB	| Common/WPF	3.0 (5.0 para VB) | 
| Biblioteca de Controles Personalizados do WPF	| wpfcustomcontrollib	| [C#], VB	| Comum/WPF	| 3,0 (5,0 para VB) | 
| Biblioteca de controle de usuário WPF	| wpfusercontrollib	| [C#], VB	| Comum/WPF	| 3,0 (5,0 para VB) | 
| Aplicativo Windows Forms (WinForms)	| winforms	| [C#], VB	| Comum/WinForms	| 3,0 (5,0 para VB) | 
| Biblioteca de classes do Windows Forms (WinForms)	| winformslib	| [C#], VB	| Comum/WinForms	| 3,0 (5,0 para VB) | 
| Serviço de trabalho	| worker	| [C#]	| Comum/de trabalho/Web	| 3.0 | 
| Projeto de Teste de Unidade	| mstest	| [C#], F#, VB	| Teste/MSTest	| 1.0 | 
| Projeto de Teste do NUnit 3	| nunit	| [C#], F#, VB	| Teste/NUnit	| 2.1.400 | 
| Item de Teste do NUnit 3	| nunit-test	| [C#], F#, VB	| Teste/NUnit	| 2.2 | 
| Projeto de Teste xUnit	| xunit	| [C#], F#, VB	| Teste/xUnit	| 1.0 | 
| Componente Razor	| razorcomponent	| [C#]	| Web/ASP.NET	| 3.0 | 
| Página do Razor	| page	| [C#]	| Web/ASP.NET	| 2,0 | 
| Importações de Exibição do MVC	| viewimports	| [C#]	| Web/ASP.NET	| 2,0 | 
| MVC ViewStart	| viewstart	| [C#]	| Web/ASP.NET	| 2,0 | 
| Blazor Aplicativo de servidor	| blazorserver	| [C#]	| SiteBlazor	| 3.0 | 
| BlazorDo WebAssembly aplicativo	| blazorwasm	| [C#]	| Web/Blazor/WebAssembly	| 3.1.300 | 
| ASP.NET Core Vazio	| web	| [C#], F#	| Web/Vazio	| 1.0 | 
| Aplicativo Web ASP.NET Core (Modelo-Exibição-Controlador)	| mvc	| [C#], F#	| Web/MVC	| 1.0 | 
| Aplicativo Web ASP.NET Core	| webapp, razor	| [C#]	| Web/MVC/Razor Pages	| 2.2, 2.0 | 
| ASP.NET Core com Angular	| angular	| [C#]	| Web/MVC/SPA	| 2,0 | 
| ASP.NET Core com React.js	| react	| [C#]	| Web/MVC/SPA	| 2,0 | 
| ASP.NET Core com React.js e Redux	| reactredux	| [C#]	| Web/MVC/SPA	| 2,0 | 
| Biblioteca de Classes do Razor	| razorclasslib	| [C#]	| Web/Razor/Biblioteca/Biblioteca de Classes do Razor	| 2.1 | 
| API Web do ASP.NET Core	| webapi	| [C#], F#	| Web/WebAPI	| 1.0 | 
| ASP.NET Core gRPC Service	| grpc	| [C#]	| Web/gRPC	| 3.0 | 
| arquivo dotnet gitignore	| gitignore	| 	| Config	| 3.0 | 
| Arquivo global.json	| globaljson	| 	| Config	| 2,0 | 
| Configuração do NuGet	| nugetconfig	| 	| Config	| 1.0 | 
| Arquivo de manifesto da ferramenta local Dotnet	| tool-manifest	| 	| Config	| 3.0 | 
| Configuração da Web	| webconfig	| 	| Config	| 1.0 | 
| Arquivo de Solução	| sln	| 	| Solução	| 1.0 | 
| Arquivo de buffer de protocolo	| proto	| 	| Web/gRPC	| 3.0 | 

### Opções

*--dry-run*

Exibe um resumo do que ocorreria se o comando fornecido fosse executado se resultasse na criação de um modelo. Disponível desde o SDK do .NET Core 2.2.

*--force*

Força o conteúdo a ser gerado mesmo se ele alterasse os arquivos existentes. Isso é necessário quando o modelo escolhido substituiria os arquivos existentes no diretório de saída.

*-h|--help*

Imprime uma ajuda para o comando. Ele pode ser invocado para o dotnet new próprio comando ou para qualquer modelo. Por exemplo, dotnet new mvc --help.

*-lang|--language {C#|F#|VB}*

A linguagem do modelo a ser criada. A linguagem aceita varia de acordo com o modelo (consulte os padrões na seção Argumentos). Não é válida para alguns modelos.

 #### Observação

Alguns shells interpretam # como um caractere especial. Nesses casos, coloque o valor do parâmetro language entre aspas. Por exemplo, **dotnet new console -lang "F#"**.

*-n|--name <OUTPUT_NAME>*

O nome para a saída criada. Se nenhum nome for especificado, o nome do diretório atual será usado.

*-o|--output <OUTPUT_DIRECTORY>*

Local para colocar a saída gerada. O padrão é o diretório atual.

#### Opções de modelo

Cada modelo pode ter opções adicionais definidas. Para obter mais informações, consulte Modelos padrão do .NET para *dotnet new* .

*Exemplos*

Criar um projeto de aplicativo de console C#:

*CLI do .NET*

**dotnet new console**

Crie um projeto de aplicativo de console F# no diretório atual:

*CLI do .NET*

**dotnet new console --language "F#"**

Crie um .NET Standard de biblioteca de classes no diretório especificado:

*CLI do .NET*

**dotnet new classlib --language VB -o MyLibrary**

Crie um projeto de MVC em C# do ASP.NET Core no diretório atual sem autenticação:

*CLI do .NET*

**dotnet new mvc -au None**

Crie um projeto de xUnit:

*CLI do .NET*

**dotnet new xunit**

Crie um global.jsno diretório atual definindo a versão do SDK como 3.1.101:

*CLI do .NET*

**dotnet new globaljson --sdk-version 3.1.101**

[Artigo original](https://docs.microsoft.com/pt-br/dotnet/core/tools/dotnet-new)