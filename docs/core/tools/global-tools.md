---
title: Ferramentas Globais do .NET Core
description: Uma visão geral do que são as Ferramentas Globais do .NET Core e os comandos da CLI do .NET Core disponíveis para elas.
author: KathleenDollard
ms.date: 05/29/2018
ms.custom: seodec18
ms.openlocfilehash: 29499d28629e483d66e25b8ecdbd5817effba439
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65631733"
---
# <a name="net-core-global-tools-overview"></a><span data-ttu-id="d6e85-103">Visão geral das Ferramentas Globais do .NET Core</span><span class="sxs-lookup"><span data-stu-id="d6e85-103">.NET Core Global Tools overview</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

<span data-ttu-id="d6e85-104">Uma Ferramenta Global do .NET Core é um pacote NuGet especial que contém um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="d6e85-104">A .NET Core Global Tool is a special NuGet package that contains a console application.</span></span> <span data-ttu-id="d6e85-105">Uma Ferramenta Global pode ser instalada no computador em uma localização padrão que está incluída na variável de ambiente PATH ou em um local personalizado.</span><span class="sxs-lookup"><span data-stu-id="d6e85-105">A Global Tool can be installed on your machine on a default location that is included in the PATH environment variable or on a custom location.</span></span>

<span data-ttu-id="d6e85-106">Caso deseje usar uma Ferramenta Global do .NET Core:</span><span class="sxs-lookup"><span data-stu-id="d6e85-106">If you want to use a .NET Core Global Tool:</span></span>

* <span data-ttu-id="d6e85-107">Encontre informações sobre a ferramenta (geralmente um site ou uma página do GitHub).</span><span class="sxs-lookup"><span data-stu-id="d6e85-107">Find information about the tool (usually a website or GitHub page).</span></span>
* <span data-ttu-id="d6e85-108">Verifique o autor e as estatísticas na página inicial do feed (geralmente, NuGet.org).</span><span class="sxs-lookup"><span data-stu-id="d6e85-108">Check the author and statistics in the home for the feed (usually NuGet.org).</span></span>
* <span data-ttu-id="d6e85-109">Instale a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="d6e85-109">Install the tool.</span></span>
* <span data-ttu-id="d6e85-110">Chame a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="d6e85-110">Call the tool.</span></span>
* <span data-ttu-id="d6e85-111">Atualize a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="d6e85-111">Update the tool.</span></span>
* <span data-ttu-id="d6e85-112">Desinstale a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="d6e85-112">Uninstall the tool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d6e85-113">As Ferramentas Globais do .NET Core são exibidas no caminho e executadas com confiança total.</span><span class="sxs-lookup"><span data-stu-id="d6e85-113">.NET Core Global Tools appear on your path and run in full trust.</span></span> <span data-ttu-id="d6e85-114">Não instale as Ferramentas Globais do .NET Core, a menos que você confie no autor.</span><span class="sxs-lookup"><span data-stu-id="d6e85-114">Do not install .NET Core Global Tools unless you trust the author.</span></span>

## <a name="find-a-net-core-global-tool"></a><span data-ttu-id="d6e85-115">Encontrar uma Ferramenta Global do .NET Core</span><span class="sxs-lookup"><span data-stu-id="d6e85-115">Find a .NET Core Global Tool</span></span>

<span data-ttu-id="d6e85-116">Atualmente, há não uma funcionalidade de pesquisa de Ferramenta Global na CLI (interface de linha de comando) do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6e85-116">Currently, there isn't a Global Tool search feature in the .NET Core Command-line Interface (CLI).</span></span>

<span data-ttu-id="d6e85-117">Encontre Ferramentas Globais do .NET Core no [NuGet](https://www.nuget.org).</span><span class="sxs-lookup"><span data-stu-id="d6e85-117">You can find .NET Core Global Tools on [NuGet](https://www.nuget.org).</span></span> <span data-ttu-id="d6e85-118">No entanto, o NuGet ainda não permite a pesquisa especificamente de Ferramentas Globais do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6e85-118">However, NuGet doesn't yet allow you to search specifically for .NET Core Global Tools.</span></span>

<span data-ttu-id="d6e85-119">Você também pode encontrar recomendações de ferramentas em postagens no blog ou no repositório [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) do GitHub.</span><span class="sxs-lookup"><span data-stu-id="d6e85-119">You may also find tool recommendations in blog posts or in the [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) GitHub repository.</span></span>

<span data-ttu-id="d6e85-120">Veja também o código-fonte das Ferramentas Globais criadas pela equipe do ASP.NET no repositório [aspnet/DotNetTools](https://github.com/aspnet/DotNetTools/) do GitHub.</span><span class="sxs-lookup"><span data-stu-id="d6e85-120">You can also see the source code for the Global Tools created by the ASP.NET team at the [aspnet/DotNetTools](https://github.com/aspnet/DotNetTools/) GitHub repository.</span></span>

## <a name="check-the-author-and-statistics"></a><span data-ttu-id="d6e85-121">Verificar o autor e as estatísticas</span><span class="sxs-lookup"><span data-stu-id="d6e85-121">Check the author and statistics</span></span>

<span data-ttu-id="d6e85-122">Como as Ferramentas Globais do .NET Core são executadas em confiança total e geralmente são instaladas no caminho, elas podem ser muito eficientes.</span><span class="sxs-lookup"><span data-stu-id="d6e85-122">Since .NET Core Global Tools run in full trust and are generally installed on your path, they can be very powerful.</span></span> <span data-ttu-id="d6e85-123">Não baixe ferramentas de pessoas em quem você não confia.</span><span class="sxs-lookup"><span data-stu-id="d6e85-123">Don't download tools from people you don't trust.</span></span>

<span data-ttu-id="d6e85-124">Se a ferramenta estiver hospedada no NuGet, você pode verificar o autor e as estatísticas pesquisando a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="d6e85-124">If the tool is hosted on NuGet, you can check the author and statistics by searching for the tool.</span></span>

## <a name="install-a-global-tool"></a><span data-ttu-id="d6e85-125">Instalar uma Ferramenta Global</span><span class="sxs-lookup"><span data-stu-id="d6e85-125">Install a Global Tool</span></span>

<span data-ttu-id="d6e85-126">Para instalar uma Ferramenta Global, use o comando [dotnet tool install](dotnet-tool-install.md) da CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6e85-126">To install a Global Tool, you use the [dotnet tool install](dotnet-tool-install.md) .NET Core CLI command.</span></span> <span data-ttu-id="d6e85-127">O seguinte exemplo mostra como instalar uma Ferramenta Global na localização padrão:</span><span class="sxs-lookup"><span data-stu-id="d6e85-127">The following example shows how to install a Global Tool in the default location:</span></span>

```console
dotnet tool install -g dotnetsay
```

<span data-ttu-id="d6e85-128">Se a ferramenta não puder ser instalada, mensagens de erro serão exibidas.</span><span class="sxs-lookup"><span data-stu-id="d6e85-128">If the tool can't be installed, error messages are displayed.</span></span> <span data-ttu-id="d6e85-129">Verifique se os feeds esperados estão sendo verificados.</span><span class="sxs-lookup"><span data-stu-id="d6e85-129">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="d6e85-130">Se estiver tentando instalar uma versão de pré-lançamento ou uma versão específica da ferramenta, especifique o número de versão usando o seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="d6e85-130">If you're trying to install a pre-release version or a specific version of the tool, you can specify the version number using the following format:</span></span>

```console
dotnet tool install -g <package-name> --version <version-number>
```

<span data-ttu-id="d6e85-131">Se a instalação for bem-sucedida, será exibida uma mensagem mostrando o comando usado para chamar a ferramenta e a versão instalada, de maneira semelhante ao seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="d6e85-131">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.0.0') was successfully installed.
```

<span data-ttu-id="d6e85-132">As Ferramentas Globais podem ser instaladas no diretório padrão ou em um local específico.</span><span class="sxs-lookup"><span data-stu-id="d6e85-132">Global Tools can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="d6e85-133">Os diretórios padrão são:</span><span class="sxs-lookup"><span data-stu-id="d6e85-133">The default directories are:</span></span>

| <span data-ttu-id="d6e85-134">Sistema operacional</span><span class="sxs-lookup"><span data-stu-id="d6e85-134">OS</span></span>          | <span data-ttu-id="d6e85-135">Caminho</span><span class="sxs-lookup"><span data-stu-id="d6e85-135">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="d6e85-136">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="d6e85-136">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="d6e85-137">Windows</span><span class="sxs-lookup"><span data-stu-id="d6e85-137">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="d6e85-138">Esses locais são adicionados ao caminho do usuário quando o SDK é executado pela primeira vez e, portanto, as Ferramentas Globais instaladas nesses locais podem ser chamadas diretamente.</span><span class="sxs-lookup"><span data-stu-id="d6e85-138">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="d6e85-139">Observe que as Ferramentas Globais são específicas ao usuário e não globais no computador.</span><span class="sxs-lookup"><span data-stu-id="d6e85-139">Note that the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="d6e85-140">Ser específico ao usuário significa que não é possível instalar uma Ferramenta Global que esteja disponível para todos os usuários do computador.</span><span class="sxs-lookup"><span data-stu-id="d6e85-140">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="d6e85-141">A ferramenta só fica disponível para cada perfil de usuário no qual a ferramenta foi instalada.</span><span class="sxs-lookup"><span data-stu-id="d6e85-141">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="d6e85-142">As Ferramentas Globais também podem ser instaladas em um diretório específico.</span><span class="sxs-lookup"><span data-stu-id="d6e85-142">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="d6e85-143">Quando elas forem instaladas em um diretório específico, o usuário precisará garantir que o comando esteja disponível, incluindo o diretório no caminho, chamando o comando com o diretório especificado ou chamando a ferramenta no diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="d6e85-143">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="d6e85-144">Nesse caso, a CLI do .NET Core não adiciona esse local automaticamente à variável de ambiente PATH.</span><span class="sxs-lookup"><span data-stu-id="d6e85-144">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="use-the-tool"></a><span data-ttu-id="d6e85-145">Usar a ferramenta</span><span class="sxs-lookup"><span data-stu-id="d6e85-145">Use the tool</span></span>

<span data-ttu-id="d6e85-146">Depois de instalar a ferramenta, chame-a usando seu comando.</span><span class="sxs-lookup"><span data-stu-id="d6e85-146">Once the tool is installed, you can call it by using its command.</span></span> <span data-ttu-id="d6e85-147">Observe que o comando pode não ser o mesmo que o nome do pacote.</span><span class="sxs-lookup"><span data-stu-id="d6e85-147">Note that the command may not be the same as the package name.</span></span>

<span data-ttu-id="d6e85-148">Se o comando for `dotnetsay`, chame a ferramenta com:</span><span class="sxs-lookup"><span data-stu-id="d6e85-148">If the command is `dotnetsay`, you call it with:</span></span>

```console
dotnetsay
```

<span data-ttu-id="d6e85-149">Se o autor da ferramenta desejou que a ferramenta fosse exibida no contexto do prompt do `dotnet`, ele pode ter escrito a ferramenta de modo que você a chame como `dotnet <command>`, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="d6e85-149">If the tool author wanted the tool to appear in the context of the `dotnet` prompt, they may have written it in a way that you call it as `dotnet <command>`, such as:</span></span>

```console
dotnet doc
```

<span data-ttu-id="d6e85-150">Encontre quais ferramentas estão incluídas em um pacote de Ferramentais Global instalado por meio da listagem dos pacotes instalados usando o comando [dotnet tool list](dotnet-tool-list.md).</span><span class="sxs-lookup"><span data-stu-id="d6e85-150">You can find which tools are included in an installed Global Tool package by listing the installed packages using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

<span data-ttu-id="d6e85-151">Procure também instruções de uso no site da ferramenta ou digitando um dos seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="d6e85-151">You can also look for usage instructions at the tool's website or by typing one of the following commands:</span></span>

```console
<command> --help
dotnet <command> --help
```

### <a name="what-could-go-wrong"></a><span data-ttu-id="d6e85-152">O que pode dar errado</span><span class="sxs-lookup"><span data-stu-id="d6e85-152">What could go wrong</span></span>

<span data-ttu-id="d6e85-153">As Ferramentas Globais são [aplicativos dependentes de estrutura](../deploying/index.md#framework-dependent-deployments-fdd), o que significa que elas dependem de um tempo de execução do .NET Core instalado no computador.</span><span class="sxs-lookup"><span data-stu-id="d6e85-153">Global Tools are [framework-dependent applications](../deploying/index.md#framework-dependent-deployments-fdd), which means they rely on a .NET Core runtime installed on your machine.</span></span> <span data-ttu-id="d6e85-154">Se o tempo de execução esperado não for encontrado, elas seguirão as regras normais de roll forward do tempo de execução do .NET Core, como:</span><span class="sxs-lookup"><span data-stu-id="d6e85-154">If the expected runtime is not found, they follow normal .NET Core runtime roll-forward rules such as:</span></span>

* <span data-ttu-id="d6e85-155">Um aplicativo efetua roll forward até a versão de patch mais recente da versão principal e secundária especificadas.</span><span class="sxs-lookup"><span data-stu-id="d6e85-155">An application rolls forward to the highest patch release of the specified major and minor version.</span></span>
* <span data-ttu-id="d6e85-156">Se não houver nenhum tempo de execução correspondente com números da versão principal e secundária correspondentes, a próxima versão secundária mais recente será usada.</span><span class="sxs-lookup"><span data-stu-id="d6e85-156">If there is no matching runtime with a matching major and minor version number, the next higher minor version is used.</span></span>
* <span data-ttu-id="d6e85-157">O roll forward não ocorre entre versões prévias do tempo de execução ou entre versões prévias e versões de lançamento.</span><span class="sxs-lookup"><span data-stu-id="d6e85-157">Roll forward doesn't occur between preview versions of the runtime or between preview versions and release versions.</span></span> <span data-ttu-id="d6e85-158">Portanto, as Ferramentas Globais criadas com versões anteriores precisam ser recompiladas e publicadas novamente pelo autor e reinstaladas.</span><span class="sxs-lookup"><span data-stu-id="d6e85-158">Thus, Global Tools created using preview versions must be rebuilt and republished by the author and reinstalled.</span></span>
* <span data-ttu-id="d6e85-159">Outros problemas podem ocorrer com as Ferramentas Globais criadas no .NET Core 2.1 Preview 1.</span><span class="sxs-lookup"><span data-stu-id="d6e85-159">Additional issues can occur with Global Tools created in .NET Core 2.1 Preview 1.</span></span> <span data-ttu-id="d6e85-160">Para obter mais informações, confira [Problemas conhecidos do .NET Core 2.1 Preview 2](https://github.com/dotnet/core/blob/master/release-notes/2.1/Preview/2.1.0-preview2-known-issues.md).</span><span class="sxs-lookup"><span data-stu-id="d6e85-160">For more information, see [.NET Core 2.1 Preview 2 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/2.1/Preview/2.1.0-preview2-known-issues.md).</span></span>

<span data-ttu-id="d6e85-161">Se um aplicativo não pode encontrar um tempo de execução apropriado, ele não é executado e relata um erro.</span><span class="sxs-lookup"><span data-stu-id="d6e85-161">If an application cannot find an appropriate runtime, it fails to run and reports an error.</span></span>

<span data-ttu-id="d6e85-162">Outro problema pode ocorrer é que uma Ferramenta Global criada durante uma versão prévia anterior pode não ser executada com os tempos de execução do .NET Core atualmente instalados.</span><span class="sxs-lookup"><span data-stu-id="d6e85-162">Another issue that might happen is that a Global Tool that was created during an earlier preview may not run with your currently installed .NET Core runtimes.</span></span> <span data-ttu-id="d6e85-163">Veja quais tempos de execução estão instalados no computador usando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="d6e85-163">You can see which runtimes are installed on your machine using the following command:</span></span>

```console
dotnet --list-runtimes
```

<span data-ttu-id="d6e85-164">Contate o autor da Ferramenta Global e veja se ele pode recompilar e publicar novamente o pacote de ferramentas no NuGet com um número de versão atualizado.</span><span class="sxs-lookup"><span data-stu-id="d6e85-164">Contact the author of the Global Tool and see if they can recompile and republish their tool package to NuGet with an updated version number.</span></span> <span data-ttu-id="d6e85-165">Depois que ele atualizar o pacote NuGet, atualize sua cópia.</span><span class="sxs-lookup"><span data-stu-id="d6e85-165">Once they have updated the package on NuGet, you can update your copy.</span></span>

<span data-ttu-id="d6e85-166">A CLI do .NET Core tenta adicionar as localizações padrão à variável de ambiente PATH em seu primeiro uso.</span><span class="sxs-lookup"><span data-stu-id="d6e85-166">The .NET Core CLI tries to add the default locations to the PATH environment variable on its first usage.</span></span> <span data-ttu-id="d6e85-167">No entanto, existem alguns cenários em que o local pode não ser adicionado a PATH automaticamente, como:</span><span class="sxs-lookup"><span data-stu-id="d6e85-167">However, there are a couple of scenarios where the location might not be added to PATH automatically, such as:</span></span>

* <span data-ttu-id="d6e85-168">Se você definiu a variável de ambiente `DOTNET_SKIP_FIRST_TIME_EXPERIENCE`.</span><span class="sxs-lookup"><span data-stu-id="d6e85-168">If you've set the `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` environment variable.</span></span>
* <span data-ttu-id="d6e85-169">No macOS, se você instalou o SDK do .NET Core usando arquivos *.tar.gz* e não *.pkg*.</span><span class="sxs-lookup"><span data-stu-id="d6e85-169">On macOS, if you've installed the .NET Core SDK using *.tar.gz* files and not *.pkg*.</span></span>
* <span data-ttu-id="d6e85-170">No Linux, você precisa editar o arquivo do ambiente do shell para configurar o PATH.</span><span class="sxs-lookup"><span data-stu-id="d6e85-170">On Linux, you need to edit the shell environment file to configure the PATH.</span></span>

## <a name="other-cli-commands"></a><span data-ttu-id="d6e85-171">Outros comandos da CLI</span><span class="sxs-lookup"><span data-stu-id="d6e85-171">Other CLI commands</span></span>

<span data-ttu-id="d6e85-172">O SDK do .NET Core contém outros comandos que dão suporte às Ferramentas Globais do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d6e85-172">The .NET Core SDK contains other commands that support .NET Core Global Tools.</span></span> <span data-ttu-id="d6e85-173">Use um dos comandos `dotnet tool` com uma das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="d6e85-173">Use any of the `dotnet tool` commands with one of the following options:</span></span>

* <span data-ttu-id="d6e85-174">`--global` ou `-g` especifica que o comando é aplicável às Ferramentas Globais de todos os usuários.</span><span class="sxs-lookup"><span data-stu-id="d6e85-174">`--global` or `-g` specifies that the command is applicable to user-wide Global Tools.</span></span>
* <span data-ttu-id="d6e85-175">`--tool-path` especifica um local personalizado para as Ferramentas Globais.</span><span class="sxs-lookup"><span data-stu-id="d6e85-175">`--tool-path` specifies a custom location for Global Tools.</span></span>

<span data-ttu-id="d6e85-176">Para descobrir quais comandos estão disponíveis para as Ferramentas Globais:</span><span class="sxs-lookup"><span data-stu-id="d6e85-176">To find out which commands are available for Global Tools:</span></span>

```console
dotnet tool --help
```

<span data-ttu-id="d6e85-177">A atualização de uma Ferramenta Global envolve sua desinstalação e reinstalação com a última versão estável.</span><span class="sxs-lookup"><span data-stu-id="d6e85-177">Updating a Global Tool involves uninstalling and reinstalling it with the latest stable version.</span></span> <span data-ttu-id="d6e85-178">Para atualizar uma Ferramenta Global, use o comando [dotnet tool update](dotnet-tool-update.md):</span><span class="sxs-lookup"><span data-stu-id="d6e85-178">To update a Global Tool, use the [dotnet tool update](dotnet-tool-update.md) command:</span></span>

```console
dotnet tool update -g <packagename>
```

<span data-ttu-id="d6e85-179">Remova uma Ferramenta Global usando [dotnet tool uninstall](dotnet-tool-uninstall.md):</span><span class="sxs-lookup"><span data-stu-id="d6e85-179">Remove a Global Tool using the [dotnet tool uninstall](dotnet-tool-uninstall.md):</span></span>

```console
dotnet tool uninstall -g <packagename>
```

<span data-ttu-id="d6e85-180">Para exibir todas as Ferramentas Globais atualmente instaladas no computador, junto com as versões e os comandos, use o comando [dotnet tool list](dotnet-tool-list.md):</span><span class="sxs-lookup"><span data-stu-id="d6e85-180">To display all of the Global Tools currently installed on the machine, along with their version and commands, use the [dotnet tool list](dotnet-tool-list.md) command:</span></span>

```console
dotnet tool list -g
```
