---
title: Solucionar problemas de uso da ferramenta .NET Core
description: Descubra os problemas comuns ao executar ferramentas do .NET Core e possíveis soluções.
author: kdollard
ms.date: 02/14/2020
ms.openlocfilehash: ed6243f802c4d3ce56a742916a1a28676e3cd876
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146444"
---
# <a name="troubleshoot-net-core-tool-usage-issues"></a><span data-ttu-id="6ba0f-103">Solucionar problemas de uso da ferramenta .NET Core</span><span class="sxs-lookup"><span data-stu-id="6ba0f-103">Troubleshoot .NET Core tool usage issues</span></span>

<span data-ttu-id="6ba0f-104">Você pode encontrar problemas ao tentar instalar ou executar uma ferramenta .NET Core, que pode ser uma ferramenta global ou uma ferramenta local.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-104">You might come across issues when trying to install or run a .NET Core tool, which can be a global tool or a local tool.</span></span> <span data-ttu-id="6ba0f-105">Este artigo descreve as causas básicas comuns e algumas soluções possíveis.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-105">This article describes the common root causes and some possible solutions.</span></span>

## <a name="installed-net-core-tool-fails-to-run"></a><span data-ttu-id="6ba0f-106">A ferramenta .NET Core instalada não é executada</span><span class="sxs-lookup"><span data-stu-id="6ba0f-106">Installed .NET Core tool fails to run</span></span>

<span data-ttu-id="6ba0f-107">Quando uma ferramenta .NET Core falha em ser executada, provavelmente você encontrou um dos seguintes problemas:</span><span class="sxs-lookup"><span data-stu-id="6ba0f-107">When a .NET Core tool fails to run, most likely you ran into one of the following issues:</span></span>

* <span data-ttu-id="6ba0f-108">O arquivo executável da ferramenta não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-108">The executable file for the tool wasn't found.</span></span>
* <span data-ttu-id="6ba0f-109">A versão correta do tempo de execução do .NET Core não foi encontrada.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-109">The correct version of the .NET Core runtime wasn't found.</span></span>

### <a name="executable-file-not-found"></a><span data-ttu-id="6ba0f-110">Arquivo executável não encontrado</span><span class="sxs-lookup"><span data-stu-id="6ba0f-110">Executable file not found</span></span>

<span data-ttu-id="6ba0f-111">Se o arquivo executável não for encontrado, você verá uma mensagem semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="6ba0f-111">If the executable file isn't found, you'll see a message similar to the following:</span></span>

```console
Could not execute because the specified command or file was not found.
Possible reasons for this include:
  * You misspelled a built-in dotnet command.
  * You intended to execute a .NET Core program, but dotnet-xyz does not exist.
  * You intended to run a global tool, but a dotnet-prefixed executable with this name could not be found on the PATH.
```

<span data-ttu-id="6ba0f-112">O nome do executável determina como você invoca a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-112">The name of the executable determines how you invoke the tool.</span></span> <span data-ttu-id="6ba0f-113">A tabela a seguir descreve o formato:</span><span class="sxs-lookup"><span data-stu-id="6ba0f-113">The following table describes the format:</span></span>

| <span data-ttu-id="6ba0f-114">Formato de nome executável</span><span class="sxs-lookup"><span data-stu-id="6ba0f-114">Executable name format</span></span>  | <span data-ttu-id="6ba0f-115">Formato de invocação</span><span class="sxs-lookup"><span data-stu-id="6ba0f-115">Invocation format</span></span>   |
|-------------------------|---------------------|
| `dotnet-<toolName>.exe` | `dotnet <toolName>` |
| `<toolName>.exe`        | `<toolName>`        |

* <span data-ttu-id="6ba0f-116">Ferramentas globais</span><span class="sxs-lookup"><span data-stu-id="6ba0f-116">Global tools</span></span>

  <span data-ttu-id="6ba0f-117">Ferramentas globais podem ser instaladas no diretório padrão ou em um local específico.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-117">Global tools can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="6ba0f-118">Os diretórios padrão são:</span><span class="sxs-lookup"><span data-stu-id="6ba0f-118">The default directories are:</span></span>

  | <span data-ttu-id="6ba0f-119">Sistema operacional</span><span class="sxs-lookup"><span data-stu-id="6ba0f-119">OS</span></span>          | <span data-ttu-id="6ba0f-120">Caminho</span><span class="sxs-lookup"><span data-stu-id="6ba0f-120">Path</span></span>                          |
  |-------------|-------------------------------|
  | <span data-ttu-id="6ba0f-121">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="6ba0f-121">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
  | <span data-ttu-id="6ba0f-122">Windows</span><span class="sxs-lookup"><span data-stu-id="6ba0f-122">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

  <span data-ttu-id="6ba0f-123">Se você está tentando executar uma ferramenta `PATH` global, verifique se a variável de ambiente em sua máquina contém o caminho onde você instalou a ferramenta global e se o executável está nesse caminho.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-123">If you're trying to run a global tool, check that the `PATH` environment variable on your machine contains the path where you installed the global tool and that the executable is in that path.</span></span>

  <span data-ttu-id="6ba0f-124">O .NET Core CLI tenta adicionar o local padrão à variável ambiente PATH em seu primeiro uso.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-124">The .NET Core CLI tries to add the default location to the PATH environment variable on its first usage.</span></span> <span data-ttu-id="6ba0f-125">No entanto, existem alguns cenários em que o local pode não ser adicionado automaticamente ao PATH:</span><span class="sxs-lookup"><span data-stu-id="6ba0f-125">However, there are some scenarios where the location might not be added to PATH automatically:</span></span>

  * <span data-ttu-id="6ba0f-126">Se você estiver usando o Linux e tiver instalado o .NET Core SDK usando arquivos *.tar.gz* e não apt-get ou rpm.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-126">If you're using Linux and you've installed the .NET Core SDK using *.tar.gz* files and not apt-get or rpm.</span></span>
  * <span data-ttu-id="6ba0f-127">Se você estiver usando o macOS 10.15 "Catalina" ou versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-127">If you're using macOS 10.15 "Catalina" or later versions.</span></span>
  * <span data-ttu-id="6ba0f-128">Se você estiver usando macOS 10.14 "Mojave" ou versões anteriores, e você instalou o .NET Core SDK usando arquivos *.tar.gz* e não *.pkg*.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-128">If you're using macOS 10.14 "Mojave" or earlier versions, and you've installed the .NET Core SDK using *.tar.gz* files and not *.pkg*.</span></span>
  * <span data-ttu-id="6ba0f-129">Se você instalou o .NET Core 3.0 SDK `DOTNET_ADD_GLOBAL_TOOLS_TO_PATH` e definiu `false`a variável de ambiente para .</span><span class="sxs-lookup"><span data-stu-id="6ba0f-129">If you've installed the .NET Core 3.0 SDK and you've set the `DOTNET_ADD_GLOBAL_TOOLS_TO_PATH` environment variable to `false`.</span></span>
  * <span data-ttu-id="6ba0f-130">Se você instalou o .NET Core 2.2 SDK ou versões anteriores, e definiu a `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` variável de ambiente para `true`.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-130">If you've installed .NET Core 2.2 SDK or earlier versions, and you've set the `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` environment variable to `true`.</span></span>

  <span data-ttu-id="6ba0f-131">Nesses cenários ou se `--tool-path` você especificou a opção, a `PATH` variável de ambiente na sua máquina não contém automaticamente o caminho onde você instalou a ferramenta global.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-131">In these scenarios or if you specified the `--tool-path` option, the `PATH` environment variable on your machine doesn't automatically contain the path where you installed the global tool.</span></span> <span data-ttu-id="6ba0f-132">Nesse caso, anexar a localização da `$HOME/.dotnet/tools`ferramenta (por exemplo, ) à variável `PATH` ambiente usando qualquer método que seu shell forneça para atualizar variáveis do ambiente.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-132">In that case, append the tool location (for example, `$HOME/.dotnet/tools`) to the `PATH` environment variable by using whatever method your shell provides for updating environment variables.</span></span> <span data-ttu-id="6ba0f-133">Para obter mais informações, consulte [as ferramentas .NET Core](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="6ba0f-133">For more information, see [.NET Core tools](global-tools.md).</span></span>

* <span data-ttu-id="6ba0f-134">Ferramentas locais</span><span class="sxs-lookup"><span data-stu-id="6ba0f-134">Local tools</span></span>

  <span data-ttu-id="6ba0f-135">Se você está tentando executar uma ferramenta local, verifique se há um arquivo manifesto chamado *dotnet-tools.json* no diretório atual ou em qualquer um de seus diretórios-pai.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-135">If you're trying to run a local tool, verify that there's a manifest file called *dotnet-tools.json* in the current directory or any of its parent directories.</span></span> <span data-ttu-id="6ba0f-136">Este arquivo também pode viver em uma pasta chamada *.config* em qualquer lugar na hierarquia da pasta do projeto, em vez da pasta raiz.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-136">This file can also live under a folder named *.config* anywhere in the project folder hierarchy, instead of the root folder.</span></span> <span data-ttu-id="6ba0f-137">Se *o dotnet-tools.json* existir, abra-o e verifique se há a ferramenta que você está tentando executar.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-137">If *dotnet-tools.json* exists, open it and check for the tool you're trying to run.</span></span> <span data-ttu-id="6ba0f-138">Se o arquivo não contiver `"isRoot": true`uma entrada para, então verifique também a hierarquia do arquivo para obter arquivos de manifesto de ferramentas adicionais.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-138">If the file doesn't contain an entry for `"isRoot": true`, then also check further up the file hierarchy for additional tool manifest files.</span></span>

  <span data-ttu-id="6ba0f-139">Se você está tentando executar uma ferramenta .NET Core que foi instalada com um caminho especificado, você precisa incluir esse caminho ao usar a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-139">If you're trying to run a .NET Core tool that was installed with a specified path, you need to include that path when using the tool.</span></span> <span data-ttu-id="6ba0f-140">Um exemplo de uso de uma ferramenta instalada de caminho de ferramenta é:</span><span class="sxs-lookup"><span data-stu-id="6ba0f-140">An example of using a tool-path installed tool is:</span></span>

  ```console
  ..\<toolDirectory>\dotnet-<toolName>
  ```

### <a name="runtime-not-found"></a><span data-ttu-id="6ba0f-141">Tempo de execução não encontrado</span><span class="sxs-lookup"><span data-stu-id="6ba0f-141">Runtime not found</span></span>

<span data-ttu-id="6ba0f-142">As ferramentas .NET Core são [aplicativos dependentes de framework,](../deploying/index.md#publish-runtime-dependent)o que significa que eles dependem de um tempo de execução do .NET Core instalado na máquina.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-142">.NET Core tools are [framework-dependent applications](../deploying/index.md#publish-runtime-dependent), which means they rely on a .NET Core runtime installed on your machine.</span></span> <span data-ttu-id="6ba0f-143">Se o tempo de execução esperado não for encontrado, eles seguirão as regras normais de andamento do .NET Core, como:</span><span class="sxs-lookup"><span data-stu-id="6ba0f-143">If the expected runtime isn't found, they follow normal .NET Core runtime roll-forward rules such as:</span></span>

* <span data-ttu-id="6ba0f-144">Um aplicativo efetua roll forward até a versão de patch mais recente da versão principal e secundária especificadas.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-144">An application rolls forward to the highest patch release of the specified major and minor version.</span></span>
* <span data-ttu-id="6ba0f-145">Se não houver tempo de execução correspondente com um número de versão maior e menor correspondente, a próxima versão menor superior é usada.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-145">If there's no matching runtime with a matching major and minor version number, the next higher minor version is used.</span></span>
* <span data-ttu-id="6ba0f-146">O roll forward não ocorre entre versões prévias do runtime ou entre versões prévias e versões de lançamento.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-146">Roll forward doesn't occur between preview versions of the runtime or between preview versions and release versions.</span></span> <span data-ttu-id="6ba0f-147">Assim, as ferramentas .NET Core criadas usando versões de pré-visualização devem ser reconstruídas e republicadas pelo autor e reinstaladas.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-147">So, .NET Core tools created using preview versions must be rebuilt and republished by the author and reinstalled.</span></span>

<span data-ttu-id="6ba0f-148">O roll-forward não ocorrerá por padrão em dois cenários comuns:</span><span class="sxs-lookup"><span data-stu-id="6ba0f-148">Roll-forward won't occur by default in two common scenarios:</span></span>

* <span data-ttu-id="6ba0f-149">Apenas versões inferiores do tempo de execução estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-149">Only lower versions of the runtime are available.</span></span> <span data-ttu-id="6ba0f-150">O roll-forward só seleciona versões posteriores do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-150">Roll-forward only selects later versions of the runtime.</span></span>
* <span data-ttu-id="6ba0f-151">Apenas versões principais mais altas do tempo de execução estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-151">Only higher major versions of the runtime are available.</span></span> <span data-ttu-id="6ba0f-152">Roll-forward não ultrapassa os principais limites da versão.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-152">Roll-forward doesn't cross major version boundaries.</span></span>

<span data-ttu-id="6ba0f-153">Se um aplicativo não consegue encontrar um tempo de execução apropriado, ele falha ao executar e relata um erro.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-153">If an application can't find an appropriate runtime, it fails to run and reports an error.</span></span>

<span data-ttu-id="6ba0f-154">Você pode descobrir quais tempos de execução do .NET Core estão instalados na sua máquina usando um dos seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="6ba0f-154">You can find out which .NET Core runtimes are installed on your machine using one of the following commands:</span></span>

```dotnetcli
dotnet --list-runtimes
dotnet --info
```

<span data-ttu-id="6ba0f-155">Se você acha que a ferramenta deve suportar a versão em tempo de execução que você instalou atualmente, você pode entrar em contato com o autor da ferramenta e ver se eles podem atualizar o número da versão ou o multi-alvo.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-155">If you think the tool should support the runtime version you currently have installed, you can contact the tool author and see if they can update the version number or multi-target.</span></span> <span data-ttu-id="6ba0f-156">Uma vez que eles tenham recompilado e republicado seu pacote de ferramentas para NuGet com um número de versão atualizado, você pode atualizar sua cópia.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-156">Once they've recompiled and republished their tool package to NuGet with an updated version number, you can update your copy.</span></span> <span data-ttu-id="6ba0f-157">Enquanto isso não acontece, a solução mais rápida para você é instalar uma versão do tempo de execução que funcionaria com a ferramenta que você está tentando executar.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-157">While that doesn't happen, the quickest solution for you is to install a version of the runtime that would work with the tool you're trying to run.</span></span> <span data-ttu-id="6ba0f-158">Para baixar uma versão específica do .NET Core runtime, visite a [página de download do .NET Core](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="6ba0f-158">To download a specific .NET Core runtime version, visit the [.NET Core download page](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

<span data-ttu-id="6ba0f-159">Se você instalar o .NET Core SDK em um local não `DOTNET_ROOT` padrão, você precisará `dotnet` definir a variável de ambiente para o diretório que contém o executável.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-159">If you install the .NET Core SDK to a non-default location, you need to set the environment variable `DOTNET_ROOT` to the directory that contains the `dotnet` executable.</span></span>

## <a name="net-core-tool-installation-fails"></a><span data-ttu-id="6ba0f-160">Falha na instalação da ferramenta .NET Core</span><span class="sxs-lookup"><span data-stu-id="6ba0f-160">.NET Core tool installation fails</span></span>

<span data-ttu-id="6ba0f-161">Há uma série de razões pelas quais a instalação de uma ferramenta global ou local do .NET Core pode falhar.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-161">There are a number of reasons the installation of a .NET Core global or local tool may fail.</span></span> <span data-ttu-id="6ba0f-162">Quando a instalação da ferramenta falhar, você verá uma mensagem semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="6ba0f-162">When the tool installation fails, you'll see a message similar to the following one:</span></span>

```console
Tool '{0}' failed to install. This failure may have been caused by:

* You are attempting to install a preview release and did not use the --version option to specify the version.
* A package by this name was found, but it was not a .NET Core tool.
* The required NuGet feed cannot be accessed, perhaps because of an Internet connection problem.
* You mistyped the name of the tool.

For more reasons, including package naming enforcement, visit https://aka.ms/failure-installing-tool
```

<span data-ttu-id="6ba0f-163">Para ajudar a diagnosticar essas falhas, as mensagens NuGet são mostradas diretamente ao usuário, juntamente com a mensagem anterior.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-163">To help diagnose these failures, NuGet messages are shown directly to the user, along with the previous message.</span></span> <span data-ttu-id="6ba0f-164">A mensagem NuGet pode ajudá-lo a identificar o problema.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-164">The NuGet message may help you identify the problem.</span></span>

### <a name="package-naming-enforcement"></a><span data-ttu-id="6ba0f-165">Aplicação de nomeação de pacotes</span><span class="sxs-lookup"><span data-stu-id="6ba0f-165">Package naming enforcement</span></span>

<span data-ttu-id="6ba0f-166">A Microsoft mudou sua orientação sobre o ID do pacote para ferramentas, resultando em uma série de ferramentas não encontradas com o nome previsto.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-166">Microsoft has changed its guidance on the Package ID for tools, resulting in a number of tools not being found with the predicted name.</span></span> <span data-ttu-id="6ba0f-167">A nova orientação é que todas as ferramentas da Microsoft sejam prefixadas com "Microsoft".</span><span class="sxs-lookup"><span data-stu-id="6ba0f-167">The new guidance is that all Microsoft tools be prefixed with "Microsoft."</span></span> <span data-ttu-id="6ba0f-168">Este prefixo é reservado e só pode ser usado para pacotes assinados com um certificado autorizado pela Microsoft.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-168">This prefix is reserved and can only be used for packages signed with a Microsoft authorized certificate.</span></span>

<span data-ttu-id="6ba0f-169">Durante a transição, algumas ferramentas da Microsoft terão a forma antiga do ID do pacote, enquanto outras terão a nova forma:</span><span class="sxs-lookup"><span data-stu-id="6ba0f-169">During the transition, some Microsoft tools will have the old form of the package ID, while others will have the new form:</span></span>

```dotnetcli
dotnet tool install -g Microsoft.<toolName>
dotnet tool install -g <toolName>
```

<span data-ttu-id="6ba0f-170">À medida que os IDs do pacote são atualizados, você precisará mudar para o novo ID do pacote para obter as atualizações mais recentes.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-170">As package IDs are updated, you'll need to change to the new package ID to get the latest updates.</span></span> <span data-ttu-id="6ba0f-171">Os pacotes com o nome da ferramenta simplificada serão depreciados.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-171">Packages with the simplified tool name will be deprecated.</span></span>

### <a name="preview-releases"></a><span data-ttu-id="6ba0f-172">Versões de pré-visualização</span><span class="sxs-lookup"><span data-stu-id="6ba0f-172">Preview releases</span></span>

* <span data-ttu-id="6ba0f-173">Você está tentando instalar uma versão de pré-visualização e não usou a `--version` opção de especificar a versão.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-173">You're attempting to install a preview release and didn't use the `--version` option to specify the version.</span></span>

<span data-ttu-id="6ba0f-174">As ferramentas .NET Core que estão em pré-visualização devem ser especificadas com uma parte do nome para indicar que estão em pré-visualização.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-174">.NET Core tools that are in preview must be specified with a portion of the name to indicate that they are in preview.</span></span> <span data-ttu-id="6ba0f-175">Você não precisa incluir toda a pré-visualização.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-175">You don't need to include the entire preview.</span></span> <span data-ttu-id="6ba0f-176">Supondo que os números da versão estejam no formato esperado, você pode usar algo como o seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="6ba0f-176">Assuming the version numbers are in the expected format, you can use something like the following example:</span></span>

```dotnetcli
dotnet tool install -g --version 1.1.0-pre <toolName>
```

### <a name="package-isnt-a-net-core-tool"></a><span data-ttu-id="6ba0f-177">O pacote não é uma ferramenta .NET Core</span><span class="sxs-lookup"><span data-stu-id="6ba0f-177">Package isn't a .NET Core tool</span></span>

* <span data-ttu-id="6ba0f-178">Um pacote NuGet com esse nome foi encontrado, mas não era uma ferramenta .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-178">A NuGet package by this name was found, but it wasn't a .NET Core tool.</span></span>

<span data-ttu-id="6ba0f-179">Se você tentar instalar um pacote NuGet que seja um pacote NuGet normal e não uma ferramenta .NET Core, você verá um erro semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="6ba0f-179">If you try to install a NuGet package that is a regular NuGet package and not a .NET Core tool, you'll see an error similar to the following:</span></span>

> <span data-ttu-id="6ba0f-180">NU1212: Combinação inválida de `<ToolName>`pacote de projeto para .</span><span class="sxs-lookup"><span data-stu-id="6ba0f-180">NU1212: Invalid project-package combination for `<ToolName>`.</span></span> <span data-ttu-id="6ba0f-181">O estilo de projeto DotnetToolReference só pode conter referências do tipo DotnetTool.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-181">DotnetToolReference project style can only contain references of the DotnetTool type.</span></span>

### <a name="nuget-feed-cant-be-accessed"></a><span data-ttu-id="6ba0f-182">O feed NuGet não pode ser acessado</span><span class="sxs-lookup"><span data-stu-id="6ba0f-182">NuGet feed can't be accessed</span></span>

* <span data-ttu-id="6ba0f-183">O feed NuGet necessário não pode ser acessado, talvez por causa de um problema de conexão à Internet.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-183">The required NuGet feed can't be accessed, perhaps because of an Internet connection problem.</span></span>

<span data-ttu-id="6ba0f-184">A instalação da ferramenta requer acesso ao feed NuGet que contém o pacote da ferramenta.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-184">Tool installation requires access to the NuGet feed that contains the tool package.</span></span> <span data-ttu-id="6ba0f-185">Falha se a ração não estiver disponível.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-185">It fails if the feed isn't available.</span></span> <span data-ttu-id="6ba0f-186">Você pode alterar `nuget.config`feeds com, solicitar um arquivo `nuget.config` específico `--add-source` ou especificar feeds adicionais com o switch.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-186">You can alter feeds with `nuget.config`, request a specific `nuget.config` file, or specify additional feeds with the `--add-source` switch.</span></span> <span data-ttu-id="6ba0f-187">Por padrão, nuGet lança um erro para qualquer feed que não possa se conectar.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-187">By default, NuGet throws an error for any feed that can't connect.</span></span> <span data-ttu-id="6ba0f-188">A `--ignore-failed-sources` bandeira pode pular essas fontes não alcançáveis.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-188">The flag `--ignore-failed-sources` can skip these non-reachable sources.</span></span>

### <a name="package-id-incorrect"></a><span data-ttu-id="6ba0f-189">ID do pacote incorreto</span><span class="sxs-lookup"><span data-stu-id="6ba0f-189">Package ID incorrect</span></span>

* <span data-ttu-id="6ba0f-190">Você digitou mal o nome da ferramenta.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-190">You mistyped the name of the tool.</span></span>

<span data-ttu-id="6ba0f-191">Uma razão comum para o fracasso é que o nome da ferramenta não está correto.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-191">A common reason for failure is that the tool name isn't correct.</span></span> <span data-ttu-id="6ba0f-192">Isso pode acontecer por causa da mistyping, ou porque a ferramenta se moveu ou foi preterida.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-192">This can happen because of mistyping, or because the tool has moved or been deprecated.</span></span> <span data-ttu-id="6ba0f-193">Para ferramentas no NuGet.org, uma maneira de garantir que você tenha o nome correto é procurar a ferramenta em NuGet.org e copiar o comando de instalação.</span><span class="sxs-lookup"><span data-stu-id="6ba0f-193">For tools on NuGet.org, one way to ensure you have the name correct is to search for the tool at NuGet.org and copy the installation command.</span></span>

## <a name="see-also"></a><span data-ttu-id="6ba0f-194">Confira também</span><span class="sxs-lookup"><span data-stu-id="6ba0f-194">See also</span></span>

* [<span data-ttu-id="6ba0f-195">.NET Core ferramentas</span><span class="sxs-lookup"><span data-stu-id="6ba0f-195">.NET Core tools</span></span>](global-tools.md)
