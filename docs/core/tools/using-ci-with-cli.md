---
title: "Usando ferramentas e SDK do .NET Core na CI (Integração Contínua)"
description: "Informações sobre o uso do SDK do .NET Core e as respectivas ferramentas no servidor de build."
keywords: ".NET, .NET Core, integração contínua, CI, build, automação, Travis CI, AppVeyor, Visual Studio Team Services, VSTS"
author: guardrex
ms.author: mairaw
ms.date: 05/18/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 0d6e1e34-277c-4aaf-9880-3ebf81023857
ms.openlocfilehash: 596bc689e423082dcae0c79801e9f796b398391e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="using-net-core-sdk-and-tools-in-continuous-integration-ci"></a>Usando ferramentas e SDK do .NET Core na CI (Integração Contínua)

## <a name="overview"></a>Visão Geral

Este documento descreve o uso do SDK do .NET Core e as respectivas ferramentas em um servidor de build. O conjunto de ferramentas do .NET Core funciona de forma interativa, quando o desenvolvedor digita comandos em um prompt de comando, e de forma automática, quando um servidor de CI (integração contínua) executa um script de build. As opções, entradas, saídas e os comandos são os mesmos. Você só precisa fornecer uma maneira de obter as ferramentas e um sistema para criar o aplicativo. Este documento se refere aos cenários de aquisição de ferramentas para CI com recomendações sobre como projetar e estruturar os scripts de build.

## <a name="installation-options-for-ci-build-servers"></a>Opções de instalação para servidores de build de CI

### <a name="using-the-native-installers"></a>Usando os instaladores nativos

Há instaladores nativos disponíveis para macOS, Linux e Windows. Os instaladores exigem acesso de administrador (sudo) para o servidor de build. A vantagem de usar um instalador nativo é que ele instala todas as dependências nativas necessárias para execução das ferramentas. Além disso, os instaladores nativos viabilizam a instalação geral do sistema do SDK.

Os usuários de macOS devem usar os instaladores de pacotes. No Linux, há a opção de usar um gerenciador de pacotes baseado em feed, como apt-get para Ubuntu e YUM para CentOS, ou usar os pacotes em si, ou seja, DEB ou RPM. No Windows, use o instalador MSI.

Você pode encontrar os binários estáveis mais recentes em [Introdução ao .NET Core](https://aka.ms/dotnetcoregs). Caso prefira usar as ferramentas de pré-lançamento mais recentes (possivelmente instáveis), use os links fornecidos em [Repositório do GitHub dotnet/CLI](https://github.com/dotnet/cli#installers-and-binaries). Para distribuições do Linux, há arquivos `tar.gz` disponíveis, também conhecidos como `tarballs`; use os scripts de instalação nos arquivos para instalar o .NET Core.

### <a name="using-the-installer-script"></a>Usando o script do instalador

Usando o script do instalador, você viabiliza a instalação não-administrativa no servidor de build e facilita a automação para obter as ferramentas. O script trata de baixar as ferramentas e extrai-las em um local especificado ou padrão para uso. Você pode também especificar uma versão das ferramentas que deseja instalar e se deseja instalar o SDK inteiro ou apenas o tempo de execução compartilhado.

O script do instalador é automatizado para execução no início do build para buscar e instalar a versão desejada do SDK. A *versão desejada* é qualquer versão do SDK necessária para a criação dos projetos. Com o script, você pode instalar o SDK em um diretório local no servidor, executar as ferramentas no local de instalação e fazer uma limpeza (ou deixar que o serviço CI faça a limpeza) após a criação. Ele proporciona o encapsulamento e isolamento de todo o processo de build. Você pode encontrar a referência do script de instalação no tópico [dotnet-install](dotnet-install-script.md).

> [!NOTE]
> Quando você usa o script do instalador, as dependências nativas não são instaladas automaticamente. Instale as dependências nativas, caso elas estejam ausentes no sistema operacional. Confira a lista de pré-requisitos no tópico [Pré-requisitos nativos do .NET Core](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).

## <a name="ci-setup-examples"></a>Exemplos de instalação de CI

Esta seção descreve uma instalação manual usando um script do PowerShell ou de bash, juntamente com uma descrição de várias soluções de CI para SaaS (software como serviço). As soluções de CI para SaaS descritas são [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/) e [Build do Visual Studio Team Services](https://www.visualstudio.com/docs/build/overview).

### <a name="manual-setup"></a>Instalação manual

Todos os serviços SaaS têm métodos próprios para criar e configurar um processo de build. Se usa uma solução de SaaS não descrita ou que exija um nível de personalização adicional ao suporte pré-empacotado, você deve realizar pelo menos algumas configurações manuais.

De modo geral, uma instalação manual exige adquirir uma versão das ferramentas (ou os builds noturnos mais recentes das ferramentas) e executar o script de build. Você pode usar um script do PowerShell ou de bash para orquestrar os comandos do .NET Core ou usar um arquivo de projeto que descreva o processo de build. A [seção de orquestração](#orchestrating-the-build) fornece mais detalhes sobre essas opções.

Depois de criar um script que executa uma instalação manual do servidor de build de CI, use-o na máquina de desenvolvimento para criar o código localmente para fins de teste. Quando confirmar que o script está em plena execução no local, implante-o no servidor de build de CI. Um script do PowerShell relativamente simples demonstra como obter o SDK do .NET Core e instalá-lo em um servidor de build do Windows:

```powershell
$ErrorActionPreference="Stop"
$ProgressPreference="SilentlyContinue"

# $LocalDotnet is the path to the locally-installed SDK to ensure the 
#   correct version of the tools are executed.
$LocalDotnet=""
# $InstallDir and $CliVersion variables can come from options to the 
#   script.
$InstallDir = "./cli-tools"
$CliVersion = "1.0.1"

# Test the path provided by $InstallDir to confirm it exists. If it 
#   does, it's removed. This is not strictly required, but it's a 
#   good way to reset the environment.
if (Test-Path $InstallDir)
{
    rm -Recurse $InstallDir
}
New-Item -Type "directory" -Path $InstallDir

Write-Host "Downloading the CLI installer..."

# Use the Invoke-WebRequest PowerShell cmdlet to obtain the 
#   installation script and save it into the installation directory.
Invoke-WebRequest `
    -Uri "https://dot.net/v1/dotnet-install.ps1" `
    -OutFile "$InstallDir/dotnet-install.ps1"

Write-Host "Installing the CLI requested version ($CliVersion) ..."

# Install the SDK of the version specified in $CliVersion into the 
#   specified location ($InstallDir).
& $InstallDir/dotnet-install.ps1 -Version $CliVersion `
    -InstallDir $InstallDir

Write-Host "Downloading and installation of the SDK is complete."

# $LocalDotnet holds the path to dotnet.exe for future use by the 
#   script.
$LocalDotnet = "$InstallDir/dotnet"

# Run the build process now. Implement your build script here.
```

Você realizará a implementação do processo de build no final do script. O script obtém as ferramentas e executa o processo de build. No caso de máquinas UNIX, o script de bash a seguir executa as ações descritas no script do PowerShell de maneira semelhante:

```bash
#!/bin/bash
INSTALLDIR="cli-tools"
CLI_VERSION=1.0.1
DOWNLOADER=$(which curl)
if [ -d "$INSTALLDIR" ]
then
    rm -rf "$INSTALLDIR"
fi
mkdir -p "$INSTALLDIR"
echo Downloading the CLI installer.
$DOWNLOADER https://dot.net/v1/dotnet-install.sh > "$INSTALLDIR/dotnet-install.sh"
chmod +x "$INSTALLDIR/dotnet-install.sh"
echo Installing the CLI requested version $CLI_VERSION. Please wait, installation may take a few minutes.
"$INSTALLDIR/dotnet-install.sh" --install-dir "$INSTALLDIR" --version $CLI_VERSION
if [ $? -ne 0 ]
then
    echo Download of $CLI_VERSION version of the CLI failed. Exiting now.
    exit 0
fi
echo The CLI has been installed.
LOCALDOTNET="$INSTALLDIR/dotnet"
# Run the build process now. Implement your build script here.
```

### <a name="travis-ci"></a>Travis CI

Você pode configurar o [Travis CI](https://travis-ci.org/) para instalar o SDK do .NET Core usando a linguagem `csharp` e chave `dotnet`. Para saber mais, confira a documentação oficial do Travis CI no tópico [Criando um projeto do C#, do F# ou do Visual Basic Project](https://docs.travis-ci.com/user/languages/csharp/). Observe que, quando você acessa as informações do Travis CI fornecidas pela comunidade, o identificador de idioma `language: csharp` funciona para todas as linguagens .NET., inclusive F# e Mono.

O Travis CI é executado em trabalhos do macOS (OS X 10.11, OS X 10.12) e do Linux (Ubuntu 14.04) em uma *matriz de builds*, na qual você especifica uma combinação de tempo de execução, ambiente e exclusões/inclusões para incluir as combinações de build do aplicativo. Para saber mais, confira o arquivo de [exemplo .travis.yml](https://github.com/dotnet/docs/blob/master/.travis.yml) e o tópico [Personalizando o build](https://docs.travis-ci.com/user/customizing-the-build) na documentação do Travis CI. As ferramentas baseadas no MSBuild incluem o LTS (1.0.x) e tempos de execução atuais (1.1.x) no pacote. Por isso, instalando o SDK, você recebe todo o conteúdo necessário para o build.

### <a name="appveyor"></a>AppVeyor

[O AppVeyor](https://www.appveyor.com/) instala o SDK do .NET Core 1.0.1 com o modelo “build worker image” do `Visual Studio 2017`. Há outras imagens de build disponíveis com diferentes versões do SDK do .NET Core. Para saber mais, confira o [exemplo .travis.yml](https://github.com/dotnet/docs/blob/master/appveyor.yml) e o tópico [Build worker image](https://www.appveyor.com/docs/build-environment/#build-worker-images) na documentação do AppVeyor.

Os binários do SDK do .NET Core são baixados e descompactados em um subdiretório por meio do script de instalação e, em seguida, são adicionados à variável de ambiente `PATH`. Adicione uma matriz de builds para executar testes de integração com várias versões do SDK do .NET Core:

```yaml
environment:
  matrix:
    - CLI_VERSION: 1.0.1
    - CLI_VERSION: Latest

install:
  # See appveyor.yml example for install script
```

### <a name="visual-studio-team-services-vsts"></a>VSTS (Visual Studio Team Services)

Configure o VSTS (Visual Studio Team Services) para criar projetos do .NET Core usando uma das seguintes abordagens:

1. Execute o script na [etapa de instalação manual](#manual-setup) usando os comandos.
1. Crie um build composto por várias tarefas de build internas do VSTS, que são configuradas para usar as ferramentas do .NET Core.

As duas soluções são válidas. Usando um script de instalação manual, você controla a versão das ferramentas que receberá quando baixá-las como parte do build. Você deve criar um script para executar o build. Este tópico descreve apenas a opção manual. Para saber mais sobre a composição de builds com tarefas de build do VSTS, confira o tópico [Implantação e integração contínua](https://www.visualstudio.com/docs/build/overview) do VSTS.

Para usar um script de instalação manual no VSTS, crie uma nova definição de build e especifique o script que deve ser executado na etapa de build. Para fazer isso, use a interface do usuário do VSTS:

1. comece criando uma nova definição de build. Quando estiver na tela que exibe opções para definir o tipo de build que deseja criar, escolha a opção **Vazio**.

   ![Escolhendo uma definição de build vazia](./media/using-ci-with-cli/screen1.png)

1. Depois de configurar o repositório do build, você será direcionado para as definições de build. Escolha **Adicionar etapa de build**:

   ![Adicionando uma etapa de build](./media/using-ci-with-cli/screen2.png)

1. Apresentamos o **Catálogo de tarefas**. O catálogo contém tarefas que você pode usar no build. Quando tiver um script, escolha o botão **Adicionar** para o **PowerShell: execute um script do PowerShell**.

   ![Adicionando uma etapa de script do PowerShell](./media/using-ci-with-cli/screen3.png)

1. Configure a etapa de build. Adicione o script do repositório que você está criando:

   ![Especificando o script do PowerShell para executar](./media/using-ci-with-cli/screen4.png)

## <a name="orchestrating-the-build"></a>Orquestrando o build

A maior parte deste documento descreve como adquirir as ferramentas do .NET Core e configurar diversos serviços de CI sem fornecer informações sobre como orquestrar ou *realmente criar* o código usando o .NET Core. As opções sobre como estruturar o processo de build dependem de vários fatores que não podem ser abordados de maneira geral aqui. Explore os recursos e exemplos fornecidos nos conjuntos de documentações do [Travis CI](https://travis-ci.org/), do [AppVeyor](https://www.appveyor.com/) e do [VSTS](https://www.visualstudio.com/docs/build/overview) para saber mais sobre como orquestrar os builds com cada tecnologia.

Duas abordagens gerais para a estruturação do processo de build para o código do .NET Core usando as ferramentas do .NET Core estão usando o MSBuild diretamente ou estão usando os comandos da linha de comando do .NET Core. A abordagem que você usará é determinada pelo seu nível de conforto e pelas vantagens e desvantagens de acordo com a complexidade. O MSBuild fornece a capacidade de expressar o processo de build como destinos e tarefas, embora apresente uma complexidade acrescida na aprendizagem da sintaxe de arquivo de projeto do MSBuild. Usando as ferramentas de linha de comando do .NET Core talvez seja mais simples, mas exige gravar a lógica de orquestração em uma linguagem de scripts, como `bash` ou PowerShell.

## <a name="see-also"></a>Consulte também

[Etapas de aquisição do Ubuntu](https://www.microsoft.com/net/core#linuxubuntu)   
