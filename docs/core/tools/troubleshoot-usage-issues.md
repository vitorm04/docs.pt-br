---
title: Solucionar problemas de uso da ferramenta .NET Core
description: Descubra os problemas comuns ao executar as ferramentas do .NET Core e as possíveis soluções.
author: kdollard
ms.date: 09/23/2019
ms.openlocfilehash: fc6c520ab57235c78148a6b77717cbd80a989451
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318293"
---
# <a name="troubleshoot-net-core-tool-usage-issues"></a><span data-ttu-id="6ca04-103">Solucionar problemas de uso da ferramenta .NET Core</span><span class="sxs-lookup"><span data-stu-id="6ca04-103">Troubleshoot .NET Core tool usage issues</span></span>

<span data-ttu-id="6ca04-104">Você pode encontrar problemas ao tentar instalar ou executar uma ferramenta .NET Core, que pode ser uma ferramenta global ou uma ferramenta local.</span><span class="sxs-lookup"><span data-stu-id="6ca04-104">You might come across issues when trying to install or run a .NET Core tool, which can be a global tool or a local tool.</span></span> <span data-ttu-id="6ca04-105">Este artigo descreve as causas raiz comuns e algumas soluções possíveis.</span><span class="sxs-lookup"><span data-stu-id="6ca04-105">This article describes the common root causes and some possible solutions.</span></span>

## <a name="installed-net-core-tool-fails-to-run"></a><span data-ttu-id="6ca04-106">Falha na execução da ferramenta .NET Core instalada</span><span class="sxs-lookup"><span data-stu-id="6ca04-106">Installed .NET Core tool fails to run</span></span>

<span data-ttu-id="6ca04-107">Quando uma ferramenta do .NET Core não é executada, é muito provável que você tenha executado um dos seguintes problemas:</span><span class="sxs-lookup"><span data-stu-id="6ca04-107">When a .NET Core tool fails to run, most likely you ran into one of the following issues:</span></span>

* <span data-ttu-id="6ca04-108">O arquivo executável da ferramenta não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="6ca04-108">The executable file for the tool wasn't found.</span></span>
* <span data-ttu-id="6ca04-109">A versão correta do tempo de execução do .NET Core não foi encontrada.</span><span class="sxs-lookup"><span data-stu-id="6ca04-109">The correct version of the .NET Core runtime wasn't found.</span></span>

### <a name="executable-file-not-found"></a><span data-ttu-id="6ca04-110">Arquivo executável não encontrado</span><span class="sxs-lookup"><span data-stu-id="6ca04-110">Executable file not found</span></span>

<span data-ttu-id="6ca04-111">Se o arquivo executável não for encontrado, você verá uma mensagem semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="6ca04-111">If the executable file isn't found, you'll see a message similar to the following:</span></span>

```
Could not execute because the specified command or file was not found.
Possible reasons for this include:
  * You misspelled a built-in dotnet command.
  * You intended to execute a .NET Core program, but dotnet-xyz does not exist.
  * You intended to run a global tool, but a dotnet-prefixed executable with this name could not be found on the PATH.
```

<span data-ttu-id="6ca04-112">O nome do executável determina como você invoca a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="6ca04-112">The name of the executable determines how you invoke the tool.</span></span> <span data-ttu-id="6ca04-113">A tabela a seguir descreve o formato:</span><span class="sxs-lookup"><span data-stu-id="6ca04-113">The following table describes the format:</span></span>

| <span data-ttu-id="6ca04-114">Formato do nome do executável</span><span class="sxs-lookup"><span data-stu-id="6ca04-114">Executable name format</span></span>  | <span data-ttu-id="6ca04-115">Formato de invocação</span><span class="sxs-lookup"><span data-stu-id="6ca04-115">Invocation format</span></span>   |
|-------------------------|---------------------|
| `dotnet-<toolName>.exe` | `dotnet <toolName>` |
| `<toolName>.exe`        | `<toolName>`        |

* <span data-ttu-id="6ca04-116">Ferramentas globais</span><span class="sxs-lookup"><span data-stu-id="6ca04-116">Global tools</span></span>

    <span data-ttu-id="6ca04-117">As ferramentas globais podem ser instaladas no diretório padrão ou em um local específico.</span><span class="sxs-lookup"><span data-stu-id="6ca04-117">Global tools can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="6ca04-118">Os diretórios padrão são:</span><span class="sxs-lookup"><span data-stu-id="6ca04-118">The default directories are:</span></span>

    | <span data-ttu-id="6ca04-119">Sistema operacional</span><span class="sxs-lookup"><span data-stu-id="6ca04-119">OS</span></span>          | <span data-ttu-id="6ca04-120">Caminho</span><span class="sxs-lookup"><span data-stu-id="6ca04-120">Path</span></span>                          |
    |-------------|-------------------------------|
    | <span data-ttu-id="6ca04-121">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="6ca04-121">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
    | <span data-ttu-id="6ca04-122">Windows</span><span class="sxs-lookup"><span data-stu-id="6ca04-122">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

    <span data-ttu-id="6ca04-123">Se você estiver tentando executar uma ferramenta global, verifique se a variável de ambiente `PATH` em seu computador contém o caminho em que você instalou a ferramenta global e se o executável está nesse caminho.</span><span class="sxs-lookup"><span data-stu-id="6ca04-123">If you're trying to run a global tool, check that the `PATH` environment variable on your machine contains the path where you installed the global tool and that the executable is in that path.</span></span>

    <span data-ttu-id="6ca04-124">A CLI do .NET Core tenta adicionar as localizações padrão à variável de ambiente PATH em seu primeiro uso.</span><span class="sxs-lookup"><span data-stu-id="6ca04-124">The .NET Core CLI tries to add the default locations to the PATH environment variable on its first usage.</span></span> <span data-ttu-id="6ca04-125">No entanto, há alguns cenários em que o local pode não ser adicionado ao caminho automaticamente, portanto, você precisará editar o caminho para configurá-lo para os seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="6ca04-125">However, there are a couple of scenarios where the location might not be added to PATH automatically, so you'll have to edit PATH to configure it for the following cases:</span></span>

  * <span data-ttu-id="6ca04-126">Se você estiver usando o Linux e tiver instalado o SDK do .NET Core usando arquivos *. tar. gz* e não apt-get ou RPM.</span><span class="sxs-lookup"><span data-stu-id="6ca04-126">If you're using Linux and you've installed the .NET Core SDK using *.tar.gz* files and not apt-get or rpm.</span></span>
  * <span data-ttu-id="6ca04-127">Se você estiver usando o macOS 10,15 "Catalina" ou versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="6ca04-127">If you're using macOS 10.15 "Catalina" or later versions.</span></span>
  * <span data-ttu-id="6ca04-128">Se você estiver usando o macOS 10,14 "Mojave" ou versões anteriores, e tiver instalado o SDK do .NET Core usando arquivos *. tar. gz* e não *. pkg*.</span><span class="sxs-lookup"><span data-stu-id="6ca04-128">If you're using macOS 10.14 "Mojave" or earlier versions, and you've installed the .NET Core SDK using *.tar.gz* files and not *.pkg*.</span></span>
  * <span data-ttu-id="6ca04-129">Se você instalou o SDK do .NET Core 3,0 e definiu a variável de ambiente `DOTNET_ADD_GLOBAL_TOOLS_TO_PATH` como `false`.</span><span class="sxs-lookup"><span data-stu-id="6ca04-129">If you've installed the .NET Core 3.0 SDK and you've set the `DOTNET_ADD_GLOBAL_TOOLS_TO_PATH` environment variable to `false`.</span></span>
  * <span data-ttu-id="6ca04-130">Se você tiver instalado o SDK do .NET Core 2,2 ou versões anteriores, e tiver definido a variável de ambiente `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` como `true`.</span><span class="sxs-lookup"><span data-stu-id="6ca04-130">If you've installed .NET Core 2.2 SDK or earlier versions, and you've set the `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` environment variable to `true`.</span></span>

  <span data-ttu-id="6ca04-131">Para obter mais informações sobre ferramentas globais, consulte [visão geral das ferramentas globais do .NET Core](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="6ca04-131">For more information about global tools, see [.NET Core Global Tools overview](global-tools.md).</span></span>

* <span data-ttu-id="6ca04-132">Ferramentas locais</span><span class="sxs-lookup"><span data-stu-id="6ca04-132">Local tools</span></span>

  <span data-ttu-id="6ca04-133">Se você estiver tentando executar uma ferramenta local, verifique se há um arquivo de manifesto chamado *dotnet-Tools. JSON* no diretório atual ou em qualquer um de seus diretórios pai.</span><span class="sxs-lookup"><span data-stu-id="6ca04-133">If you're trying to run a local tool, verify that there's a manifest file called *dotnet-tools.json* in the current directory or any of its parent directories.</span></span> <span data-ttu-id="6ca04-134">Esse arquivo também pode residir em uma pasta chamada *. config* em qualquer lugar na hierarquia de pastas do projeto, em vez da pasta raiz.</span><span class="sxs-lookup"><span data-stu-id="6ca04-134">This file can also live under a folder named *.config* anywhere in the project folder hierarchy, instead of the root folder.</span></span> <span data-ttu-id="6ca04-135">Se *dotnet-Tools. JSON* existir, abra-o e verifique a ferramenta que você está tentando executar.</span><span class="sxs-lookup"><span data-stu-id="6ca04-135">If *dotnet-tools.json* exists, open it and check for the tool you're trying to run.</span></span> <span data-ttu-id="6ca04-136">Se o arquivo não contiver uma entrada para `"isRoot": true`, verifique também a hierarquia de arquivos para arquivos de manifesto da ferramenta adicional.</span><span class="sxs-lookup"><span data-stu-id="6ca04-136">If the file doesn't contain an entry for `"isRoot": true`, then also check further up the file hierarchy for additional tool manifest files.</span></span>

  <span data-ttu-id="6ca04-137">Se você estiver tentando executar uma ferramenta do .NET Core que foi instalada com um caminho especificado, precisará incluir esse caminho ao usar a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="6ca04-137">If you're trying to run a .NET Core tool that was installed with a specified path, you need to include that path when using the tool.</span></span> <span data-ttu-id="6ca04-138">Um exemplo de como usar uma ferramenta instalada por caminho de ferramenta é:</span><span class="sxs-lookup"><span data-stu-id="6ca04-138">An example of using a tool-path installed tool is:</span></span>

  ```console
  ..\<toolDirectory>\dotnet-<toolName>
  ```

### <a name="runtime-not-found"></a><span data-ttu-id="6ca04-139">Tempo de execução não encontrado</span><span class="sxs-lookup"><span data-stu-id="6ca04-139">Runtime not found</span></span>

<span data-ttu-id="6ca04-140">As ferramentas do .NET Core são [aplicativos dependentes da estrutura](../deploying/index.md#framework-dependent-deployments-fdd), o que significa que eles dependem de um tempo de execução do .NET Core instalado em seu computador.</span><span class="sxs-lookup"><span data-stu-id="6ca04-140">.NET Core tools are [framework-dependent applications](../deploying/index.md#framework-dependent-deployments-fdd), which means they rely on a .NET Core runtime installed on your machine.</span></span> <span data-ttu-id="6ca04-141">Se o tempo de execução esperado não for encontrado, siga as regras normais de roll-forward do tempo de execução do .NET Core, como:</span><span class="sxs-lookup"><span data-stu-id="6ca04-141">If the expected runtime isn't found, they follow normal .NET Core runtime roll-forward rules such as:</span></span>

* <span data-ttu-id="6ca04-142">Um aplicativo efetua roll forward até a versão de patch mais recente da versão principal e secundária especificadas.</span><span class="sxs-lookup"><span data-stu-id="6ca04-142">An application rolls forward to the highest patch release of the specified major and minor version.</span></span>
* <span data-ttu-id="6ca04-143">Se não houver nenhum tempo de execução correspondente com um número de versão principal e secundária correspondente, a próxima versão secundária mais alta será usada.</span><span class="sxs-lookup"><span data-stu-id="6ca04-143">If there's no matching runtime with a matching major and minor version number, the next higher minor version is used.</span></span>
* <span data-ttu-id="6ca04-144">O roll forward não ocorre entre versões prévias do tempo de execução ou entre versões prévias e versões de lançamento.</span><span class="sxs-lookup"><span data-stu-id="6ca04-144">Roll forward doesn't occur between preview versions of the runtime or between preview versions and release versions.</span></span> <span data-ttu-id="6ca04-145">Portanto, as ferramentas do .NET Core criadas usando versões prévias devem ser recriadas e republicadas pelo autor e reinstaladas.</span><span class="sxs-lookup"><span data-stu-id="6ca04-145">So, .NET Core tools created using preview versions must be rebuilt and republished by the author and reinstalled.</span></span>

<span data-ttu-id="6ca04-146">O roll-forward não ocorrerá por padrão em dois cenários comuns:</span><span class="sxs-lookup"><span data-stu-id="6ca04-146">Roll-forward won't occur by default in two common scenarios:</span></span>

* <span data-ttu-id="6ca04-147">Somente versões inferiores do tempo de execução estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="6ca04-147">Only lower versions of the runtime are available.</span></span> <span data-ttu-id="6ca04-148">O roll-forward só seleciona versões posteriores do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="6ca04-148">Roll-forward only selects later versions of the runtime.</span></span>
* <span data-ttu-id="6ca04-149">Somente as versões principais mais altas do tempo de execução estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="6ca04-149">Only higher major versions of the runtime are available.</span></span> <span data-ttu-id="6ca04-150">Roll forward não cruza os limites de versão principais.</span><span class="sxs-lookup"><span data-stu-id="6ca04-150">Roll-forward doesn't cross major version boundaries.</span></span>

<span data-ttu-id="6ca04-151">Se um aplicativo não conseguir encontrar um tempo de execução apropriado, ele não executará e relatará um erro.</span><span class="sxs-lookup"><span data-stu-id="6ca04-151">If an application can't find an appropriate runtime, it fails to run and reports an error.</span></span>

<span data-ttu-id="6ca04-152">Você pode descobrir quais tempos de execução do .NET Core estão instalados em seu computador usando um dos seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="6ca04-152">You can find out which .NET Core runtimes are installed on your machine using one of the following commands:</span></span>

```dotnetcli
dotnet --list-runtimes
dotnet --info
```

<span data-ttu-id="6ca04-153">Se você considerar que a ferramenta deve dar suporte à versão de tempo de execução instalada atualmente, entre em contato com o autor da ferramenta e veja se eles podem atualizar o número de versão ou vários destinos.</span><span class="sxs-lookup"><span data-stu-id="6ca04-153">If you think the tool should support the runtime version you currently have installed, you can contact the tool author and see if they can update the version number or multi-target.</span></span> <span data-ttu-id="6ca04-154">Depois de recompilar e republicar seu pacote de ferramentas no NuGet com um número de versão atualizado, você pode atualizar sua cópia.</span><span class="sxs-lookup"><span data-stu-id="6ca04-154">Once they've recompiled and republished their tool package to NuGet with an updated version number, you can update your copy.</span></span> <span data-ttu-id="6ca04-155">Embora isso não aconteça, a solução mais rápida para você é instalar uma versão do tempo de execução que funcionaria com a ferramenta que você está tentando executar.</span><span class="sxs-lookup"><span data-stu-id="6ca04-155">While that doesn't happen, the quickest solution for you is to install a version of the runtime that would work with the tool you're trying to run.</span></span> <span data-ttu-id="6ca04-156">Para baixar uma versão específica do tempo de execução do .NET Core, visite a [página de download do .NET Core](https://dotnet.microsoft.com/download/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="6ca04-156">To download a specific .NET Core runtime version, visit the [.NET Core download page](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

<span data-ttu-id="6ca04-157">Se você instalar o SDK do .NET Core em um local não padrão, precisará definir a variável de ambiente `DOTNET_ROOT` para o diretório que contém o executável `dotnet`.</span><span class="sxs-lookup"><span data-stu-id="6ca04-157">If you install the .NET Core SDK to a non-default location, you need to set the environment variable `DOTNET_ROOT` to the directory that contains the `dotnet` executable.</span></span>

## <a name="net-core-tool-installation-fails"></a><span data-ttu-id="6ca04-158">Falha na instalação da ferramenta .NET Core</span><span class="sxs-lookup"><span data-stu-id="6ca04-158">.NET Core tool installation fails</span></span>

<span data-ttu-id="6ca04-159">Há vários motivos pelos quais a instalação de uma ferramenta global ou local do .NET Core pode falhar.</span><span class="sxs-lookup"><span data-stu-id="6ca04-159">There are a number of reasons the installation of a .NET Core global or local tool may fail.</span></span> <span data-ttu-id="6ca04-160">Quando a instalação da ferramenta falhar, você verá uma mensagem semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="6ca04-160">When the tool installation fails, you'll see a message similar to following one:</span></span>

```
Tool '{0}' failed to install. This failure may have been caused by:

* You are attempting to install a preview release and did not use the --version option to specify the version.
* A package by this name was found, but it was not a .NET Core tool.
* The required NuGet feed cannot be accessed, perhaps because of an Internet connection problem.
* You mistyped the name of the tool.

For more reasons, including package naming enforcement, visit https://aka.ms/failure-installing-tool
```

<span data-ttu-id="6ca04-161">Para ajudar a diagnosticar essas falhas, as mensagens do NuGet são mostradas diretamente para o usuário, juntamente com a mensagem anterior.</span><span class="sxs-lookup"><span data-stu-id="6ca04-161">To help diagnose these failures, NuGet messages are shown directly to the user, along with the previous message.</span></span> <span data-ttu-id="6ca04-162">A mensagem do NuGet pode ajudá-lo a identificar o problema.</span><span class="sxs-lookup"><span data-stu-id="6ca04-162">The NuGet message may help you identify the problem.</span></span>

### <a name="package-naming-enforcement"></a><span data-ttu-id="6ca04-163">Imposição de nomenclatura de pacote</span><span class="sxs-lookup"><span data-stu-id="6ca04-163">Package naming enforcement</span></span>

<span data-ttu-id="6ca04-164">A Microsoft alterou suas diretrizes sobre a ID do pacote para ferramentas, resultando em várias ferramentas não encontradas com o nome previsto.</span><span class="sxs-lookup"><span data-stu-id="6ca04-164">Microsoft has changed its guidance on the Package ID for tools, resulting in a number of tools not being found with the predicted name.</span></span> <span data-ttu-id="6ca04-165">A nova diretriz é que todas as ferramentas da Microsoft sejam prefixadas com "Microsoft".</span><span class="sxs-lookup"><span data-stu-id="6ca04-165">The new guidance is that all Microsoft tools be prefixed with "Microsoft."</span></span> <span data-ttu-id="6ca04-166">Esse prefixo é reservado e só pode ser usado para pacotes assinados com um certificado autorizado da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="6ca04-166">This prefix is reserved and can only be used for packages signed with a Microsoft authorized certificate.</span></span>

<span data-ttu-id="6ca04-167">Durante a transição, algumas ferramentas da Microsoft terão a forma antiga da ID do pacote, enquanto outras terão o novo formulário:</span><span class="sxs-lookup"><span data-stu-id="6ca04-167">During the transition, some Microsoft tools will have the old form of the package ID, while others will have the new form:</span></span>

```dotnetcli
dotnet tool install -g Microsoft.<toolName>
dotnet tool install -g <toolName>
```

<span data-ttu-id="6ca04-168">Como as IDs de pacote são atualizadas, você precisará alterar para a nova ID do pacote para obter as atualizações mais recentes.</span><span class="sxs-lookup"><span data-stu-id="6ca04-168">As package IDs are updated, you'll need to change to the new package ID to get the latest updates.</span></span> <span data-ttu-id="6ca04-169">Os pacotes com o nome da ferramenta simplificada serão preteridos.</span><span class="sxs-lookup"><span data-stu-id="6ca04-169">Packages with the simplified tool name will be deprecated.</span></span>

### <a name="preview-releases"></a><span data-ttu-id="6ca04-170">Versões de visualização</span><span class="sxs-lookup"><span data-stu-id="6ca04-170">Preview releases</span></span>

* <span data-ttu-id="6ca04-171">Você está tentando instalar uma versão prévia e não usou a opção `--version` para especificar a versão.</span><span class="sxs-lookup"><span data-stu-id="6ca04-171">You're attempting to install a preview release and didn't use the `--version` option to specify the version.</span></span>

<span data-ttu-id="6ca04-172">As ferramentas do .NET Core que estão em visualização devem ser especificadas com uma parte do nome para indicar que estão na versão prévia.</span><span class="sxs-lookup"><span data-stu-id="6ca04-172">.NET Core tools that are in preview must be specified with a portion of the name to indicate that they are in preview.</span></span> <span data-ttu-id="6ca04-173">Você não precisa incluir a visualização inteira.</span><span class="sxs-lookup"><span data-stu-id="6ca04-173">You don't need to include the entire preview.</span></span> <span data-ttu-id="6ca04-174">Supondo que os números de versão estejam no formato esperado, você pode usar algo semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="6ca04-174">Assuming the version numbers are in the expected format, you can use something like the following example:</span></span>

```dotnetcli
dotnet tool install -g --version 1.1.0-pre <toolName>
```

> [!NOTE]
> <span data-ttu-id="6ca04-175">A equipe de CLI do .NET Core está planejando adicionar uma opção de `--preview` em uma versão futura para facilitar isso.</span><span class="sxs-lookup"><span data-stu-id="6ca04-175">The .NET Core CLI team is planning to add a `--preview` switch in a future release to make this easier.</span></span>

### <a name="package-isnt-a-net-core-tool"></a><span data-ttu-id="6ca04-176">O pacote não é uma ferramenta .NET Core</span><span class="sxs-lookup"><span data-stu-id="6ca04-176">Package isn't a .NET Core tool</span></span>

* <span data-ttu-id="6ca04-177">Um pacote NuGet com esse nome foi encontrado, mas não era uma ferramenta .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6ca04-177">A NuGet package by this name was found, but it wasn't a .NET Core tool.</span></span>

<span data-ttu-id="6ca04-178">Se você tentar instalar um pacote NuGet que é um pacote NuGet regular e não uma ferramenta .NET Core, verá um erro semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="6ca04-178">If you try to install a NuGet package that is a regular NuGet package and not a .NET Core tool, you'll see an error similar to the following:</span></span>

> <span data-ttu-id="6ca04-179">NU1212: combinação de pacote de projeto inválida para `<ToolName>`.</span><span class="sxs-lookup"><span data-stu-id="6ca04-179">NU1212: Invalid project-package combination for `<ToolName>`.</span></span> <span data-ttu-id="6ca04-180">O estilo de projeto DotnetToolReference só pode conter referências do tipo DotnetTool.</span><span class="sxs-lookup"><span data-stu-id="6ca04-180">DotnetToolReference project style can only contain references of the DotnetTool type.</span></span>

### <a name="nuget-feed-cant-be-accessed"></a><span data-ttu-id="6ca04-181">O feed do NuGet não pode ser acessado</span><span class="sxs-lookup"><span data-stu-id="6ca04-181">NuGet feed can't be accessed</span></span>

* <span data-ttu-id="6ca04-182">O feed NuGet necessário não pode ser acessado, talvez devido a um problema de conexão com a Internet.</span><span class="sxs-lookup"><span data-stu-id="6ca04-182">The required NuGet feed can't be accessed, perhaps because of an Internet connection problem.</span></span>

<span data-ttu-id="6ca04-183">A instalação da ferramenta requer acesso ao feed do NuGet que contém o pacote de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="6ca04-183">Tool installation requires access to the NuGet feed that contains the tool package.</span></span> <span data-ttu-id="6ca04-184">Ele falhará se o feed não estiver disponível.</span><span class="sxs-lookup"><span data-stu-id="6ca04-184">It fails if the feed isn't available.</span></span> <span data-ttu-id="6ca04-185">Você pode alterar feeds com `nuget.config`, solicitar um arquivo `nuget.config` específico ou especificar Feeds adicionais com a opção `--add-source`.</span><span class="sxs-lookup"><span data-stu-id="6ca04-185">You can alter feeds with `nuget.config`, request a specific `nuget.config` file, or specify additional feeds with the `--add-source` switch.</span></span> <span data-ttu-id="6ca04-186">Por padrão, o NuGet gera um erro para qualquer feed que não pode se conectar.</span><span class="sxs-lookup"><span data-stu-id="6ca04-186">By default, NuGet throws an error for any feed that can't connect.</span></span> <span data-ttu-id="6ca04-187">O sinalizador `--ignore-failed-sources` pode ignorar essas fontes não acessíveis.</span><span class="sxs-lookup"><span data-stu-id="6ca04-187">The flag `--ignore-failed-sources` can skip these non-reachable sources.</span></span>

### <a name="package-id-incorrect"></a><span data-ttu-id="6ca04-188">ID de pacote incorreta</span><span class="sxs-lookup"><span data-stu-id="6ca04-188">Package ID incorrect</span></span>

* <span data-ttu-id="6ca04-189">Você digitou indigitadamente o nome da ferramenta.</span><span class="sxs-lookup"><span data-stu-id="6ca04-189">You mistyped the name of the tool.</span></span>

<span data-ttu-id="6ca04-190">Um motivo comum para a falha é que o nome da ferramenta não está correto.</span><span class="sxs-lookup"><span data-stu-id="6ca04-190">A common reason for failure is that the tool name isn't correct.</span></span> <span data-ttu-id="6ca04-191">Isso pode ocorrer devido a digitação incorreta ou porque a ferramenta foi movida ou foi preterida.</span><span class="sxs-lookup"><span data-stu-id="6ca04-191">This can happen because of mistyping, or because the tool has moved or been deprecated.</span></span> <span data-ttu-id="6ca04-192">Para ferramentas no NuGet.org, uma maneira de garantir que você tenha o nome correto é Pesquisar a ferramenta em NuGet.org e copiar o comando de instalação.</span><span class="sxs-lookup"><span data-stu-id="6ca04-192">For tools on NuGet.org, one way to ensure you have the name correct is to search for the tool at NuGet.org and copy the installation command.</span></span>

## <a name="see-also"></a><span data-ttu-id="6ca04-193">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6ca04-193">See also</span></span>

* [<span data-ttu-id="6ca04-194">Visão geral das Ferramentas Globais do .NET Core</span><span class="sxs-lookup"><span data-stu-id="6ca04-194">.NET Core Global Tools overview</span></span>](global-tools.md)
