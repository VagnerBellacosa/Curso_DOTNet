# Chocolatey

## Utilizando Chocolatey para Windows

##### Daniel Padua Ferreira

### Introdução

Bom, vamos começar pela pergunta básica: "O que seria o Chocolatey?" Assim como a pergunta a resposta é bem direta: "é um gerenciador de pacotes desenvolvido para Windows".

Sim, agora (nem tão agora pois jã vem rolando desde antes de 2014 minimamente) temos um gerenciador de pacotes para Windows nos moldes do apt-get ou yum para Linux ou o Homebrew para Mac. E o assim como nos mencionados, podemos utilizá-lo em ferramentas automação de infraestrutura (ou infraestrutura como código) como o Puppet, Chef e Ansible

Neste guia irei mostrar o básico para começar a utilizar o Chocolatey, como instalação e principais comandos para manipulação de pacotes.

## Pré-Requisitos

- Windows 7 ou superior / Windows Server 2003 ou superior
- Powershell v2 ou superior
- .NET Framework 4 ou superior (a instalação do Chocolatey irá tentar instalar esta dependência caso você não possua)

### Instalação

Primeiramente é necessário executar o Powershell ou o Cmd em modo administrador, para isto pesquise por Powershell ou Cmd no Menu Iniciar, clique com o botão direito e selecione Executar como administrador.

Para Powershell utilize a linha de comando:

...
Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
...

Para Cmd utilize a linha de comando:

...
@"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"
...

### Utilização

E pronto, a instalação é apenas isto. Agora vamos aos comandos básicos para manipular os pacotes:

Pesquisar pacotes choco search <nome aproximado do pacote> ou visite <https://chocolatey.org> e pesquise

Listar pacotes instalados

...
choco list --local-only
...

### Instalação de pacotes

...
choco install <nome do pacote>
...

obs.: Utilize -y caso deseje ignorar as confirmações

### Remoção de pacotes

...
choco uninstall <nome do pacote>
...

obs.: Utilize -y caso deseje ignorar as confirmações

### Atualização de pacotes

...
choco upgrade <nome do pacote>
...

para atualizar todos os pacotes use:

...
choco upgrade all
...

obs.: Utilize -y caso deseje ignorar as confirmações

## Conclusão

O Chocolatey veio para facilitar a vida dos usuários de Windows e principalmente dos administradores. E também tornou mais viável a utilização de ambientes windows para esteiras devops.

[Artigo original](https://medium.com/danielpadua/utilizando-chocolatey-para-windows-2b51c0ba9b31)
