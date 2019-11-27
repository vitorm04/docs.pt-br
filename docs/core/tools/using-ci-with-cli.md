---
title: Usando ferramentas e SDK do .NET Core na CI (Integração Contínua)
description: Informações sobre o uso do SDK do .NET Core e as respectivas ferramentas no servidor de build.
author: mairaw
ms.date: 05/18/2017
ms.custom: seodec18
ms.openlocfilehash: 481d54904192ee82da1f9d34bbf62fa8ffe1cd3b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428602"
---
# <a name="using-net-core-sdk-and-tools-in-continuous-integration-ci"></a><span data-ttu-id="677f9-103">Usando ferramentas e SDK do .NET Core na CI (Integração Contínua)</span><span class="sxs-lookup"><span data-stu-id="677f9-103">Using .NET Core SDK and tools in Continuous Integration (CI)</span></span>

<span data-ttu-id="677f9-104">Este documento descreve o uso do SDK do .NET Core e as respectivas ferramentas em um servidor de build.</span><span class="sxs-lookup"><span data-stu-id="677f9-104">This document outlines using the .NET Core SDK and its tools on a build server.</span></span> <span data-ttu-id="677f9-105">O conjunto de ferramentas do .NET Core funciona de forma interativa, quando o desenvolvedor digita comandos em um prompt de comando, e de forma automática, quando um servidor de CI (integração contínua) executa um script de build.</span><span class="sxs-lookup"><span data-stu-id="677f9-105">The .NET Core toolset works both interactively, where a developer types commands at a command prompt, and automatically, where a Continuous Integration (CI) server runs a build script.</span></span> <span data-ttu-id="677f9-106">As opções, entradas, saídas e os comandos são os mesmos. Você só precisa fornecer uma maneira de obter as ferramentas e um sistema para criar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="677f9-106">The commands, options, inputs, and outputs are the same, and the only things you supply are a way to acquire the tooling and a system to build your app.</span></span> <span data-ttu-id="677f9-107">Este documento se refere aos cenários de aquisição de ferramentas para CI com recomendações sobre como projetar e estruturar os scripts de build.</span><span class="sxs-lookup"><span data-stu-id="677f9-107">This document focuses on scenarios of tool acquisition for CI with recommendations on how to design and structure your build scripts.</span></span>

## <a name="installation-options-for-ci-build-servers"></a><span data-ttu-id="677f9-108">Opções de instalação para servidores de build de CI</span><span class="sxs-lookup"><span data-stu-id="677f9-108">Installation options for CI build servers</span></span>

### <a name="using-the-native-installers"></a><span data-ttu-id="677f9-109">Usando os instaladores nativos</span><span class="sxs-lookup"><span data-stu-id="677f9-109">Using the native installers</span></span>

<span data-ttu-id="677f9-110">Há instaladores nativos disponíveis para macOS, Linux e Windows.</span><span class="sxs-lookup"><span data-stu-id="677f9-110">Native installers are available for macOS, Linux, and Windows.</span></span> <span data-ttu-id="677f9-111">Os instaladores exigem acesso de administrador (sudo) para o servidor de build.</span><span class="sxs-lookup"><span data-stu-id="677f9-111">The installers require admin (sudo) access to the build server.</span></span> <span data-ttu-id="677f9-112">A vantagem de usar um instalador nativo é que ele instala todas as dependências nativas necessárias para execução das ferramentas.</span><span class="sxs-lookup"><span data-stu-id="677f9-112">The advantage of using a native installer is that it installs all of the native dependencies required for the tooling to run.</span></span> <span data-ttu-id="677f9-113">Além disso, os instaladores nativos viabilizam a instalação geral do sistema do SDK.</span><span class="sxs-lookup"><span data-stu-id="677f9-113">Native installers also provide a system-wide installation of the SDK.</span></span>

<span data-ttu-id="677f9-114">Os usuários de macOS devem usar os instaladores de pacotes.</span><span class="sxs-lookup"><span data-stu-id="677f9-114">macOS users should use the PKG installers.</span></span> <span data-ttu-id="677f9-115">No Linux, há a opção de usar um gerenciador de pacotes baseado em feed, como apt-get para Ubuntu e YUM para CentOS, ou usar os pacotes em si, ou seja, DEB ou RPM.</span><span class="sxs-lookup"><span data-stu-id="677f9-115">On Linux, there's a choice of using a feed-based package manager, such as apt-get for Ubuntu or yum for CentOS, or using the packages themselves, DEB or RPM.</span></span> <span data-ttu-id="677f9-116">No Windows, use o instalador MSI.</span><span class="sxs-lookup"><span data-stu-id="677f9-116">On Windows, use the MSI installer.</span></span>

<span data-ttu-id="677f9-117">Você pode encontrar os binários estáveis mais recentes em [Downloads do .NET](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="677f9-117">The latest stable binaries are found at [.NET downloads](https://dotnet.microsoft.com/download).</span></span> <span data-ttu-id="677f9-118">Caso prefira usar as ferramentas de pré-lançamento mais recentes (possivelmente instáveis), use os links fornecidos no [Repositório dotnet/core-sdk do GitHub](https://github.com/dotnet/core-sdk#installers-and-binaries).</span><span class="sxs-lookup"><span data-stu-id="677f9-118">If you wish to use the latest (and potentially unstable) pre-release tooling, use the links provided at the [dotnet/core-sdk GitHub repository](https://github.com/dotnet/core-sdk#installers-and-binaries).</span></span> <span data-ttu-id="677f9-119">Para distribuições do Linux, há arquivos `tar.gz` disponíveis, também conhecidos como `tarballs`; use os scripts de instalação nos arquivos para instalar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="677f9-119">For Linux distributions, `tar.gz` archives (also known as `tarballs`) are available; use the installation scripts within the archives to install .NET Core.</span></span>

### <a name="using-the-installer-script"></a><span data-ttu-id="677f9-120">Usando o script do instalador</span><span class="sxs-lookup"><span data-stu-id="677f9-120">Using the installer script</span></span>

<span data-ttu-id="677f9-121">Usando o script do instalador, você viabiliza a instalação não-administrativa no servidor de build e facilita a automação para obter as ferramentas.</span><span class="sxs-lookup"><span data-stu-id="677f9-121">Using the installer script allows for non-administrative installation on your build server and easy automation for obtaining the tooling.</span></span> <span data-ttu-id="677f9-122">O script trata de baixar as ferramentas e extrai-las em um local especificado ou padrão para uso.</span><span class="sxs-lookup"><span data-stu-id="677f9-122">The script takes care of downloading the tooling and extracting it into a default or specified location for use.</span></span> <span data-ttu-id="677f9-123">Você pode também especificar uma versão das ferramentas que deseja instalar e se deseja instalar o SDK inteiro ou apenas o runtime compartilhado.</span><span class="sxs-lookup"><span data-stu-id="677f9-123">You can also specify a version of the tooling that you wish to install and whether you want to install the entire SDK or only the shared runtime.</span></span>

<span data-ttu-id="677f9-124">O script do instalador é automatizado para execução no início do build para buscar e instalar a versão desejada do SDK.</span><span class="sxs-lookup"><span data-stu-id="677f9-124">The installer script is automated to run at the start of the build to fetch and install the desired version of the SDK.</span></span> <span data-ttu-id="677f9-125">A *versão desejada* é qualquer versão do SDK necessária para a criação dos projetos.</span><span class="sxs-lookup"><span data-stu-id="677f9-125">The *desired version* is whatever version of the SDK your projects require to build.</span></span> <span data-ttu-id="677f9-126">Com o script, você pode instalar o SDK em um diretório local no servidor, executar as ferramentas no local de instalação e fazer uma limpeza (ou deixar que o serviço CI faça a limpeza) após a criação.</span><span class="sxs-lookup"><span data-stu-id="677f9-126">The script allows you to install the SDK in a local directory on the server, run the tools from the installed location, and then clean up (or let the CI service clean up) after the build.</span></span> <span data-ttu-id="677f9-127">Ele proporciona o encapsulamento e isolamento de todo o processo de build.</span><span class="sxs-lookup"><span data-stu-id="677f9-127">This provides encapsulation and isolation to your entire build process.</span></span> <span data-ttu-id="677f9-128">Você pode encontrar a referência do script de instalação no artigo [dotnet-install](dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="677f9-128">The installation script reference is found in the [dotnet-install](dotnet-install-script.md) article.</span></span>

> [!NOTE]
> <span data-ttu-id="677f9-129">**Azure DevOps Services**</span><span class="sxs-lookup"><span data-stu-id="677f9-129">**Azure DevOps Services**</span></span>
>
> <span data-ttu-id="677f9-130">Quando você usa o script do instalador, as dependências nativas não são instaladas automaticamente.</span><span class="sxs-lookup"><span data-stu-id="677f9-130">When using the installer script, native dependencies aren't installed automatically.</span></span> <span data-ttu-id="677f9-131">Instale as dependências nativas, caso elas estejam ausentes no sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="677f9-131">You must install the native dependencies if the operating system doesn't have them.</span></span> <span data-ttu-id="677f9-132">Para obter mais informações, consulte [dependências e requisitos do .NET Core](../install/dependencies.md?tabs=netcore30&pivots=os-linux).</span><span class="sxs-lookup"><span data-stu-id="677f9-132">For more information, see [.NET Core dependencies and requirements](../install/dependencies.md?tabs=netcore30&pivots=os-linux).</span></span>

## <a name="ci-setup-examples"></a><span data-ttu-id="677f9-133">Exemplos de instalação de CI</span><span class="sxs-lookup"><span data-stu-id="677f9-133">CI setup examples</span></span>

<span data-ttu-id="677f9-134">Esta seção descreve uma instalação manual usando um script do PowerShell ou de bash, juntamente com uma descrição de várias soluções de CI para SaaS (software como serviço).</span><span class="sxs-lookup"><span data-stu-id="677f9-134">This section describes a manual setup using a PowerShell or bash script, along with a description of several software as a service (SaaS) CI solutions.</span></span> <span data-ttu-id="677f9-135">As soluções de CI para SaaS descritas são [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/) e [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).</span><span class="sxs-lookup"><span data-stu-id="677f9-135">The SaaS CI solutions covered are [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).</span></span>

### <a name="manual-setup"></a><span data-ttu-id="677f9-136">Instalação manual</span><span class="sxs-lookup"><span data-stu-id="677f9-136">Manual setup</span></span>

<span data-ttu-id="677f9-137">Todos os serviços SaaS têm métodos próprios para criar e configurar um processo de build.</span><span class="sxs-lookup"><span data-stu-id="677f9-137">Each SaaS service has its own methods for creating and configuring a build process.</span></span> <span data-ttu-id="677f9-138">Se usa uma solução de SaaS não descrita ou que exija um nível de personalização adicional ao suporte pré-empacotado, você deve realizar pelo menos algumas configurações manuais.</span><span class="sxs-lookup"><span data-stu-id="677f9-138">If you use different SaaS solution than those listed or require customization beyond the pre-packaged support, you must perform at least some manual configuration.</span></span>

<span data-ttu-id="677f9-139">De modo geral, uma instalação manual exige adquirir uma versão das ferramentas (ou os builds noturnos mais recentes das ferramentas) e executar o script de build.</span><span class="sxs-lookup"><span data-stu-id="677f9-139">In general, a manual setup requires you to acquire a version of the tools (or the latest nightly builds of the tools) and run your build script.</span></span> <span data-ttu-id="677f9-140">Você pode usar um script do PowerShell ou de bash para orquestrar os comandos do .NET Core ou usar um arquivo de projeto que descreva o processo de build.</span><span class="sxs-lookup"><span data-stu-id="677f9-140">You can use a PowerShell or bash script to orchestrate the .NET Core commands or use a project file that outlines the build process.</span></span> <span data-ttu-id="677f9-141">A [seção de orquestração](#orchestrating-the-build) fornece mais detalhes sobre essas opções.</span><span class="sxs-lookup"><span data-stu-id="677f9-141">The [orchestration section](#orchestrating-the-build) provides more detail on these options.</span></span>

<span data-ttu-id="677f9-142">Depois de criar um script que executa uma instalação manual do servidor de build de CI, use-o na máquina de desenvolvimento para criar o código localmente para fins de teste.</span><span class="sxs-lookup"><span data-stu-id="677f9-142">After you create a script that performs a manual CI build server setup, use it on your dev machine to build your code locally for testing purposes.</span></span> <span data-ttu-id="677f9-143">Quando confirmar que o script está em plena execução no local, implante-o no servidor de build de CI.</span><span class="sxs-lookup"><span data-stu-id="677f9-143">Once you confirm that the script is running well locally, deploy it to your CI build server.</span></span> <span data-ttu-id="677f9-144">Um script do PowerShell relativamente simples demonstra como obter o SDK do .NET Core e instalá-lo em um servidor de build do Windows:</span><span class="sxs-lookup"><span data-stu-id="677f9-144">A relatively simple PowerShell script demonstrates how to obtain the .NET Core SDK and install it on a Windows build server:</span></span>

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

<span data-ttu-id="677f9-145">Você realizará a implementação do processo de build no final do script.</span><span class="sxs-lookup"><span data-stu-id="677f9-145">You provide the implementation for your build process at the end of the script.</span></span> <span data-ttu-id="677f9-146">O script obtém as ferramentas e executa o processo de build.</span><span class="sxs-lookup"><span data-stu-id="677f9-146">The script acquires the tools and then executes your build process.</span></span> <span data-ttu-id="677f9-147">No caso de máquinas UNIX, o script de bash a seguir executa as ações descritas no script do PowerShell de maneira semelhante:</span><span class="sxs-lookup"><span data-stu-id="677f9-147">For UNIX machines, the following bash script performs the actions described in the PowerShell script in a similar manner:</span></span>

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

### <a name="travis-ci"></a><span data-ttu-id="677f9-148">Travis CI</span><span class="sxs-lookup"><span data-stu-id="677f9-148">Travis CI</span></span>

<span data-ttu-id="677f9-149">Você pode configurar o [Travis CI](https://travis-ci.org/) para instalar o SDK do .NET Core usando a linguagem `csharp` e chave `dotnet`.</span><span class="sxs-lookup"><span data-stu-id="677f9-149">You can configure [Travis CI](https://travis-ci.org/) to install the .NET Core SDK using the `csharp` language and the `dotnet` key.</span></span> <span data-ttu-id="677f9-150">Para saber mais, confira a documentação oficial do Travis CI no tópico [Criação de um projeto do C#, F# ou Visual Basic](https://docs.travis-ci.com/user/languages/csharp/).</span><span class="sxs-lookup"><span data-stu-id="677f9-150">For more information, see the official Travis CI docs on [Building a C#, F#, or Visual Basic Project](https://docs.travis-ci.com/user/languages/csharp/).</span></span> <span data-ttu-id="677f9-151">Observe que, quando você acessa as informações do Travis CI fornecidas pela comunidade, o identificador de idioma `language: csharp` funciona para todas as linguagens .NET., inclusive F# e Mono.</span><span class="sxs-lookup"><span data-stu-id="677f9-151">Note as you access the Travis CI information that the community-maintained `language: csharp` language identifier works for all .NET languages, including F#, and Mono.</span></span>

<span data-ttu-id="677f9-152">O Travis CI é executado em trabalhos do macOS e do Linux em uma *matriz de builds*, na qual você especifica uma combinação de runtime, ambiente e exclusões/inclusões para incluir as combinações de build do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="677f9-152">Travis CI runs both macOS and Linux jobs in a *build matrix*, where you specify a combination of runtime, environment, and exclusions/inclusions to cover your build combinations for your app.</span></span> <span data-ttu-id="677f9-153">Para obter mais informações, confira o artigo [Personalizando o build](https://docs.travis-ci.com/user/customizing-the-build) na documentação do Travis CI.</span><span class="sxs-lookup"><span data-stu-id="677f9-153">For more information, see the [Customizing the Build](https://docs.travis-ci.com/user/customizing-the-build) article in the Travis CI documentation.</span></span> <span data-ttu-id="677f9-154">As ferramentas baseadas no MSBuild incluem o LTS (1.0.x) e runtimes atuais (1.1.x) no pacote. Por isso, instalando o SDK, você recebe todo o conteúdo necessário para o build.</span><span class="sxs-lookup"><span data-stu-id="677f9-154">The MSBuild-based tools include the LTS (1.0.x) and Current (1.1.x) runtimes in the package; so by installing the SDK, you receive everything you need to build.</span></span>

### <a name="appveyor"></a><span data-ttu-id="677f9-155">AppVeyor</span><span class="sxs-lookup"><span data-stu-id="677f9-155">AppVeyor</span></span>

<span data-ttu-id="677f9-156">[O AppVeyor](https://www.appveyor.com/) instala o SDK do .NET Core 1.0.1 com o modelo “build worker image” do `Visual Studio 2017`.</span><span class="sxs-lookup"><span data-stu-id="677f9-156">[AppVeyor](https://www.appveyor.com/) installs the .NET Core 1.0.1 SDK with the `Visual Studio 2017` build worker image.</span></span> <span data-ttu-id="677f9-157">Outras imagens de build com diferentes versões do SDK do .NET Core estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="677f9-157">Other build images with different versions of the .NET Core SDK are available.</span></span> <span data-ttu-id="677f9-158">Para saber mais, consulte o [exemplo de appveyor.yml](https://github.com/dotnet/docs/blob/master/appveyor.yml) e o artigo [Criar imagens do trabalhador](https://www.appveyor.com/docs/build-environment/#build-worker-images) na documentação do AppVeyor.</span><span class="sxs-lookup"><span data-stu-id="677f9-158">For more information, see the [appveyor.yml example](https://github.com/dotnet/docs/blob/master/appveyor.yml) and the [Build worker images](https://www.appveyor.com/docs/build-environment/#build-worker-images) article in the AppVeyor docs.</span></span>

<span data-ttu-id="677f9-159">Os binários do SDK do .NET Core são baixados e descompactados em um subdiretório por meio do script de instalação e, em seguida, são adicionados à variável de ambiente `PATH`.</span><span class="sxs-lookup"><span data-stu-id="677f9-159">The .NET Core SDK binaries are downloaded and unzipped in a subdirectory using the install script, and then they're added to the `PATH` environment variable.</span></span> <span data-ttu-id="677f9-160">Adicione uma matriz de builds para executar testes de integração com várias versões do SDK do .NET Core:</span><span class="sxs-lookup"><span data-stu-id="677f9-160">Add a build matrix to run integration tests with multiple versions of the .NET Core SDK:</span></span>

```yaml
environment:
  matrix:
    - CLI_VERSION: 1.0.1
    - CLI_VERSION: Latest

install:
  # See appveyor.yml example for install script
```

### <a name="azure-devops-services"></a><span data-ttu-id="677f9-161">Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="677f9-161">Azure DevOps Services</span></span>

<span data-ttu-id="677f9-162">Configure os Azure DevOps Services para criar projetos do .NET Core usando uma das seguintes abordagens:</span><span class="sxs-lookup"><span data-stu-id="677f9-162">Configure Azure DevOps Services to build .NET Core projects using one of these approaches:</span></span>

1. <span data-ttu-id="677f9-163">Execute o script na [etapa de instalação manual](#manual-setup) usando os comandos.</span><span class="sxs-lookup"><span data-stu-id="677f9-163">Run the script from the [manual setup step](#manual-setup) using your commands.</span></span>
1. <span data-ttu-id="677f9-164">Crie um build composto por várias tarefas de build internas dos Azure DevOps Services, que são configuradas para usar as ferramentas do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="677f9-164">Create a build composed of several Azure DevOps Services built-in build tasks that are configured to use .NET Core tools.</span></span>

<span data-ttu-id="677f9-165">As duas soluções são válidas.</span><span class="sxs-lookup"><span data-stu-id="677f9-165">Both solutions are valid.</span></span> <span data-ttu-id="677f9-166">Usando um script de instalação manual, você controla a versão das ferramentas que receberá quando baixá-las como parte do build.</span><span class="sxs-lookup"><span data-stu-id="677f9-166">Using a manual setup script, you control the version of the tools that you receive, since you download them as part of the build.</span></span> <span data-ttu-id="677f9-167">Você deve criar um script para executar o build.</span><span class="sxs-lookup"><span data-stu-id="677f9-167">The build is run from a script that you must create.</span></span> <span data-ttu-id="677f9-168">Este artigo descreve apenas a opção manual.</span><span class="sxs-lookup"><span data-stu-id="677f9-168">This article only covers the manual option.</span></span> <span data-ttu-id="677f9-169">Para saber mais sobre a composição de builds com tarefas de build do Azure DevOps Services, consulte a documentação do [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).</span><span class="sxs-lookup"><span data-stu-id="677f9-169">For more information on composing a build with Azure DevOps Services build tasks, see the [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index) documentation.</span></span>

<span data-ttu-id="677f9-170">Para usar um script de instalação manual no Azure DevOps Services, crie uma nova definição de build e especifique o script que deve ser executado na etapa de build.</span><span class="sxs-lookup"><span data-stu-id="677f9-170">To use a manual setup script in Azure DevOps Services, create a new build definition and specify the script to run for the build step.</span></span> <span data-ttu-id="677f9-171">Para fazer isso, use a interface do usuário do Azure DevOps Services:</span><span class="sxs-lookup"><span data-stu-id="677f9-171">This is accomplished using the Azure DevOps Services user interface:</span></span>

1. <span data-ttu-id="677f9-172">comece criando uma nova definição de build.</span><span class="sxs-lookup"><span data-stu-id="677f9-172">Start by creating a new build definition.</span></span> <span data-ttu-id="677f9-173">Quando estiver na tela que exibe opções para definir o tipo de build que deseja criar, escolha a opção **Vazio**.</span><span class="sxs-lookup"><span data-stu-id="677f9-173">Once you reach the screen that provides you an option to define what kind of a build you wish to create, select the **Empty** option.</span></span>

   ![Escolhendo uma definição de build vazia](./media/using-ci-with-cli/select-empty-build-definition.png)

1. <span data-ttu-id="677f9-175">Depois de configurar o repositório do build, você será direcionado para as definições de build.</span><span class="sxs-lookup"><span data-stu-id="677f9-175">After configuring the repository to build, you're directed to the build definitions.</span></span> <span data-ttu-id="677f9-176">Escolha **Adicionar etapa de build**:</span><span class="sxs-lookup"><span data-stu-id="677f9-176">Select **Add build step**:</span></span>

   ![Adicionando uma etapa de build](./media/using-ci-with-cli/add-build-step.png)

1. <span data-ttu-id="677f9-178">Apresentamos o **Catálogo de tarefas**.</span><span class="sxs-lookup"><span data-stu-id="677f9-178">You're presented with the **Task catalog**.</span></span> <span data-ttu-id="677f9-179">O catálogo contém tarefas que você pode usar no build.</span><span class="sxs-lookup"><span data-stu-id="677f9-179">The catalog contains tasks that you use in the build.</span></span> <span data-ttu-id="677f9-180">Quando tiver um script, escolha o botão **Adicionar** para o **PowerShell: execute um script do PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="677f9-180">Since you have a script, select the **Add** button for **PowerShell: Run a PowerShell script**.</span></span>

   ![Adicionando uma etapa de script do PowerShell](./media/using-ci-with-cli/add-powershell-script.png)

1. <span data-ttu-id="677f9-182">Configure a etapa de build.</span><span class="sxs-lookup"><span data-stu-id="677f9-182">Configure the build step.</span></span> <span data-ttu-id="677f9-183">Adicione o script do repositório que você está criando:</span><span class="sxs-lookup"><span data-stu-id="677f9-183">Add the script from the repository that you're building:</span></span>

   ![Especificando o script do PowerShell para executar](./media/using-ci-with-cli/powershell-script-path.png)

## <a name="orchestrating-the-build"></a><span data-ttu-id="677f9-185">Orquestrando o build</span><span class="sxs-lookup"><span data-stu-id="677f9-185">Orchestrating the build</span></span>

<span data-ttu-id="677f9-186">A maior parte deste documento descreve como adquirir as ferramentas do .NET Core e configurar diversos serviços de CI sem fornecer informações sobre como orquestrar ou *realmente criar* o código usando o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="677f9-186">Most of this document describes how to acquire the .NET Core tools and configure various CI services without providing information on how to orchestrate, or *actually build*, your code with .NET Core.</span></span> <span data-ttu-id="677f9-187">As opções sobre como estruturar o processo de build dependem de vários fatores que não podem ser abordados de maneira geral aqui.</span><span class="sxs-lookup"><span data-stu-id="677f9-187">The choices on how to structure the build process depend on many factors that can't be covered in a general way here.</span></span> <span data-ttu-id="677f9-188">Para saber mais sobre como orquestrar os builds com cada tecnologia, explore os recursos e exemplos fornecidos nos conjuntos de documentações do [Travis CI](https://travis-ci.org/), do [AppVeyor](https://www.appveyor.com/) e do [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).</span><span class="sxs-lookup"><span data-stu-id="677f9-188">For more information on orchestrating your builds with each technology, explore the resources and samples provided in the documentation sets of [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).</span></span>

<span data-ttu-id="677f9-189">Duas abordagens gerais para a estruturação do processo de build para o código do .NET Core usando as ferramentas do .NET Core estão usando o MSBuild diretamente ou estão usando os comandos da linha de comando do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="677f9-189">Two general approaches that you take in structuring the build process for .NET Core code using the .NET Core tools are using MSBuild directly or using the .NET Core command-line commands.</span></span> <span data-ttu-id="677f9-190">A abordagem que você usará é determinada pelo seu nível de conforto e pelas vantagens e desvantagens de acordo com a complexidade.</span><span class="sxs-lookup"><span data-stu-id="677f9-190">Which approach you should take is determined by your comfort level with the approaches and trade-offs in complexity.</span></span> <span data-ttu-id="677f9-191">O MSBuild fornece a capacidade de expressar o processo de build como destinos e tarefas, embora apresente uma complexidade acrescida na aprendizagem da sintaxe de arquivo de projeto do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="677f9-191">MSBuild provides you the ability to express your build process as tasks and targets, but it comes with the added complexity of learning MSBuild project file syntax.</span></span> <span data-ttu-id="677f9-192">Usando as ferramentas de linha de comando do .NET Core talvez seja mais simples, mas exige gravar a lógica de orquestração em uma linguagem de scripts, como `bash` ou PowerShell.</span><span class="sxs-lookup"><span data-stu-id="677f9-192">Using the .NET Core command-line tools is perhaps simpler, but it requires you to write orchestration logic in a scripting language like `bash` or PowerShell.</span></span>

## <a name="see-also"></a><span data-ttu-id="677f9-193">Consulte também</span><span class="sxs-lookup"><span data-stu-id="677f9-193">See also</span></span>

- [<span data-ttu-id="677f9-194">Downloads do .NET: Linux</span><span class="sxs-lookup"><span data-stu-id="677f9-194">.NET downloads - Linux</span></span>](https://dotnet.microsoft.com/download?initial-os=linux)
