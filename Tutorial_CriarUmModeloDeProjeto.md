# Tutorial: criar um modelo de projeto

Com o .NET, você pode criar e implantar modelos que geram projetos, arquivos e, até mesmo, recursos. Este tutorial é a parte dois de uma série que ensina como criar, instalar e desinstalar modelos para usar com o comando dotnet new.

Nesta parte da série, você aprenderá a:

:heavy_check_mark: Criar os recursos de um modelo de projeto
:heavy_check_mark: Criar a pasta e o arquivo de configuração do modelo
:heavy_check_mark: Instalar um modelo a partir de um caminho de arquivos
:heavy_check_mark: Testar um modelo de item
:heavy_check_mark: Desinstalar um modelo de item

## Pré-requisitos

- Conclua a parte 1 desta série de tutoriais.
- Abra um terminal e navegue até a pasta working\templates.

## Criar um modelo de projeto

Os modelos de projeto produzem projetos prontos para execução que ajudam os usuários a começar com um conjunto de códigos de trabalho. O .NET inclui alguns modelos de projeto, como um aplicativo de console ou uma biblioteca de classes. Neste exemplo, você criará um novo projeto de console que habilita o C# 9,0 e produz um async main ponto de entrada.

No terminal, navegue até a pasta working\templates e crie uma nova subpasta chamada consoleasync. Insira a subpasta e execute dotnet new console para gerar o aplicativo de console padrão. Você editará os arquivos produzidos por este modelo para criar um novo modelo.

*Console*

working
└───templates
    └───consoleasync
            consoleasync.csproj
            Program.cs

### Modificar o Program.cs

Abra o arquivo program.cs. O projeto do console não usa um ponto de entrada assíncrono, então vamos adicionar isso. Altere seu código para o seguinte e salve o arquivo.

*C#*

using System;
using System.Threading.Tasks;

namespace consoleasync
{
    class Program
    {
        static async Task Main(string[] args)
        {
            await Console.Out.WriteAsync("Hello World with C# 9.0!");
        }
    }
}

### Modificar consoleasync.csproj

Vamos atualizar a versão da linguagem C# que o projeto usa para a versão 9,0. Edite o arquivo consoleasync.csproj e adicione a configuração <LangVersion> a um nó <PropertyGroup>.

*XML*

<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>

    <LangVersion>9.0</LangVersion>

  </PropertyGroup>
  
</Project>

## Compilar o projeto

Antes de concluir um modelo de projeto, você deve testá-lo para garantir que ele seja compilado e executado corretamente.

No seu terminal, execute o comando a seguir.

*CLI do .NET*

**dotnet run**

Você Obtém a saída a seguir.

*Console*

*Hello World with C# 9.0!*

Você pode excluir as pastas obj e bin criadas usando dotnet run. A exclusão desses arquivos garante que o modelo inclua apenas os arquivos relacionados ao seu modelo e não todos os arquivos resultantes de uma ação de compilação.

Agora que você tem o conteúdo do modelo criado, é necessário criar a configuração do modelo na pasta raiz do modelo.

## Criar a configuração do modelo

Os modelos são reconhecidos no .NET por uma pasta especial e um arquivo de configuração que existem na raiz do modelo. Neste tutorial, a pasta de modelos está localizada em working\templates\consoleasync.

Quando você cria um modelo, todos os arquivos e pastas na pasta de modelos são incluídos como parte do modelo, exceto a pasta de configuração especial. Esta pasta de configuração chama-se .template.config.

Primeiro, crie uma nova subpasta chamada .template.config, insira-a. Em seguida, crie um novo arquivo chamado template.json. A estrutura de pastas deve ser parecida com esta.

*Console*

working
└───templates
    └───consoleasync
        └───.template.config
                template.json

Abra o template.jsem com seu editor de texto favorito e cole o código JSON a seguir e salve-o.

*JSON*

{
  "$schema": "http://json.schemastore.org/template",
  "author": "Me",
  "classifications": [ "Common", "Console", "C#9" ],
  "identity": "ExampleTemplate.AsyncProject",
  "name": "Example templates: async project",
  "shortName": "consoleasync",
  "tags": {
    "language": "C#",
    "type": "project"
  }
}

Esse arquivo de configuração contém todas as configurações do modelo. Você pode ver as configurações básicas, como name e shortName, mas também há um valor tags/type que é definido como project. Isso designa seu modelo como um modelo de projeto. Não há restrições quanto ao tipo do modelo criado. Os item project valores e são nomes comuns que o .net recomenda para que os usuários possam filtrar facilmente o tipo de modelo que estão procurando.

O item classifications representa a coluna marcações que você vê quando executa dotnet new e obtém uma lista de modelos. Os usuários também podem pesquisar com base nas marcações de classificação. Não confunda a propriedade tags no arquivo json com a lista de marcações classifications. São duas coisas diferentes, mas, infelizmente, nomeadas da mesma forma. O esquema completo do arquivo template.json é encontrado no Repositório de Esquema JSON. Para saber mais sobre o arquivo template.json, veja o wiki de modelagem dotnet.

Agora que você já tem um arquivo .template.config/template.json válido, seu modelo está pronto para ser instalado. Antes de instalar o modelo, exclua todas as pastas e arquivos extras que você não deseja incluir no modelo, como as pastas bin ou obj. No terminal, navegue até a pasta consoleasync e execute dotnet new -i .\ para instalar o modelo localizado na pasta atual. Se você estiver usando um sistema operacional Linux ou macOS, use uma barra invertida: dotnet new -i ./ .

Esse comando gera a lista de modelos instalados que deve incluir o seu.

*CLI do .NET*

**dotnet new -i .\**

Você Obtém uma saída semelhante à seguinte.

*Console*

**Usage: new [options]**

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.

... cut to save space ...

Templates                                         Short Name               Language          Tags
--------------------------------------------      -------------------      ------------      ----------------------
Console Application                               console                  [C#], F#, VB      Common/Console
Example templates: async project                  consoleasync             [C#]              Common/Console/C#9
Class library                                     classlib                 [C#], F#, VB      Common/Library
WPF Application                                   wpf                      [C#], VB          Common/WPF

## Testar o modelo do projeto

Agora que você tem um modelo de projeto instalado, teste-o.

Navegue até a pasta de teste

Crie um novo aplicativo de console com o comando a seguir, que gera um projeto em funcionamento que você pode testar facilmente com o dotnet run comando.

*CLI do .NET*

**dotnet new consoleasync**

Você Obtém a saída a seguir.

*Console*

**The template "Example templates: async project" was created successfully.**

Execute o projeto usando o comando a seguir.

*CLI do .NET*

**dotnet run**

Você Obtém a saída a seguir.

*Console*

**Hello World with C# 9.0!**

Parabéns! Você criou e implantou um modelo de projeto com o .NET. Para se preparar para a próxima parte desta série de tutoriais, você deverá desinstalar o modelo criado. Lembre-se de também excluir todos os arquivos da pasta test. Isso levará você de volta a um estado limpo, pronto para a próxima seção principal deste tutorial.

## Desinstalar o modelo

Como você instalou o modelo usando um caminho de arquivo, você deve desinstalá-lo com o caminho de arquivo absoluto. Você pode ver uma lista de modelos instalados executando o comando dotnet new -u. Seu modelo deve ser listado por último. Use o Uninstall Command listado para desinstalar o modelo.

*CLI do .NET*

**dotnet new -u**

Você obterá uma saída semelhante à seguinte.

*Console*

**Template Instantiation Commands for .NET Core CLI**

Currently installed items:
  Microsoft.DotNet.Common.ProjectTemplates.2.2
    Details:
      NuGetPackageId: Microsoft.DotNet.Common.ProjectTemplates.2.2
      Version: 1.0.2-beta4
      Author: Microsoft
    Templates:
      Class library (classlib) C#
      Class library (classlib) F#
      Class library (classlib) VB
      Console Application (console) C#
      Console Application (console) F#
      Console Application (console) VB
    Uninstall Command:
      dotnet new -u Microsoft.DotNet.Common.ProjectTemplates.2.2

... cut to save space ...

  C:\Test\templatetutorial\working\templates\consoleasync
    Templates:
      Example templates: async project (consoleasync) C#
    Uninstall Command:
      dotnet new -u C:\working\templates\consoleasync

Para desinstalar o modelo que você criou, execute Uninstall Command o mostrado na saída.

*CLI do .NET*

**dotnet new -u C:\working\templates\consoleasync**

[Artigo Original](https://docs.microsoft.com/pt-br/dotnet/core/tutorials/cli-templates-create-project-template)