---
title: Ferramentas Globais do .NET Core
description: Uma visão geral do que são as Ferramentas Globais do .NET Core e os comandos da CLI do .NET Core disponíveis para elas.
author: KathleenDollard
ms.date: 05/29/2018
ms.custom: seodec18
ms.openlocfilehash: 116739f80d5157632a8e44a19cbef6ba7971d339
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318309"
---
# <a name="net-core-global-tools-overview"></a><span data-ttu-id="ae1f4-103">Visão geral das Ferramentas Globais do .NET Core</span><span class="sxs-lookup"><span data-stu-id="ae1f4-103">.NET Core Global Tools overview</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

<span data-ttu-id="ae1f4-104">Uma Ferramenta Global do .NET Core é um pacote NuGet especial que contém um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="ae1f4-104">A .NET Core Global Tool is a special NuGet package that contains a console application.</span></span> <span data-ttu-id="ae1f4-105">Uma Ferramenta Global pode ser instalada no computador em uma localização padrão que está incluída na variável de ambiente PATH ou em um local personalizado.</span><span class="sxs-lookup"><span data-stu-id="ae1f4-105">A Global Tool can be installed on your machine on a default location that is included in the PATH environment variable or on a custom location.</span></span>

<span data-ttu-id="ae1f4-106">Caso deseje usar uma Ferramenta Global do .NET Core:</span><span class="sxs-lookup"><span data-stu-id="ae1f4-106">If you want to use a .NET Core Global Tool:</span></span>

* <span data-ttu-id="ae1f4-107">Encontre informações sobre a ferramenta (geralmente um site ou uma página do GitHub).</span><span class="sxs-lookup"><span data-stu-id="ae1f4-107">Find information about the tool (usually a website or GitHub page).</span></span>
* <span data-ttu-id="ae1f4-108">Verifique o autor e as estatísticas na página inicial do feed (geralmente, NuGet.org).</span><span class="sxs-lookup"><span data-stu-id="ae1f4-108">Check the author and statistics in the home for the feed (usually NuGet.org).</span></span>
* <span data-ttu-id="ae1f4-109">Instale a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="ae1f4-109">Install the tool.</span></span>
* <span data-ttu-id="ae1f4-110">Chame a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="ae1f4-110">Call the tool.</span></span>
* <span data-ttu-id="ae1f4-111">Atualize a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="ae1f4-111">Update the tool.</span></span>
* <span data-ttu-id="ae1f4-112">Desinstale a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="ae1f4-112">Uninstall the tool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ae1f4-113">As Ferramentas Globais do .NET Core são exibidas no caminho e executadas com confiança total.</span><span class="sxs-lookup"><span data-stu-id="ae1f4-113">.NET Core Global Tools appear on your path and run in full trust.</span></span> <span data-ttu-id="ae1f4-114">Não instale as Ferramentas Globais do .NET Core, a menos que você confie no autor.</span><span class="sxs-lookup"><span data-stu-id="ae1f4-114">Do not install .NET Core Global Tools unless you trust the author.</span></span>

## <a name="find-a-net-core-global-tool"></a><span data-ttu-id="ae1f4-115">Encontrar uma Ferramenta Global do .NET Core</span><span class="sxs-lookup"><span data-stu-id="ae1f4-115">Find a .NET Core Global Tool</span></span>

<span data-ttu-id="ae1f4-116">Atualmente, há não uma funcionalidade de pesquisa de Ferramenta Global na CLI (interface de linha de comando) do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ae1f4-116">Currently, there isn't a Global Tool search feature in the .NET Core Command-line Interface (CLI).</span></span> <span data-ttu-id="ae1f4-117">Veja a seguir algumas recomendações sobre como encontrar ferramentas:</span><span class="sxs-lookup"><span data-stu-id="ae1f4-117">The following are some recommendations on how to find tools:</span></span>

* <span data-ttu-id="ae1f4-118">Encontre Ferramentas Globais do .NET Core no [NuGet](https://www.nuget.org).</span><span class="sxs-lookup"><span data-stu-id="ae1f4-118">You can find .NET Core Global Tools on [NuGet](https://www.nuget.org).</span></span> <span data-ttu-id="ae1f4-119">No entanto, o NuGet ainda não permite a pesquisa especificamente de Ferramentas Globais do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ae1f4-119">However, NuGet doesn't yet allow you to search specifically for .NET Core Global Tools.</span></span>
* <span data-ttu-id="ae1f4-120">Você pode encontrar recomendações de ferramentas em Postagens de blog ou no repositório GitHub [natemcmaster/dotnet-Tools](https://github.com/natemcmaster/dotnet-tools) .</span><span class="sxs-lookup"><span data-stu-id="ae1f4-120">You may find tool recommendations in blog posts or in the [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) GitHub repository.</span></span>
* <span data-ttu-id="ae1f4-121">Você pode ver o código-fonte das ferramentas globais criadas pela equipe do ASP.NET no repositório GitHub do [ASPNET/DotNetTools](https://github.com/aspnet/DotNetTools/) .</span><span class="sxs-lookup"><span data-stu-id="ae1f4-121">You can see the source code for the Global Tools created by the ASP.NET team at the [aspnet/DotNetTools](https://github.com/aspnet/DotNetTools/) GitHub repository.</span></span>
* <span data-ttu-id="ae1f4-122">Você pode aprender sobre as ferramentas de diagnóstico em [ferramentas globais de diagnóstico dotnet do .NET Core](../diagnostics/index.md#net-core-dotnet-diagnostic-global-tools).</span><span class="sxs-lookup"><span data-stu-id="ae1f4-122">You can learn about diagnostic tools at [.NET Core dotnet diagnostic Global Tools](../diagnostics/index.md#net-core-dotnet-diagnostic-global-tools).</span></span>

## <a name="check-the-author-and-statistics"></a><span data-ttu-id="ae1f4-123">Verificar o autor e as estatísticas</span><span class="sxs-lookup"><span data-stu-id="ae1f4-123">Check the author and statistics</span></span>

<span data-ttu-id="ae1f4-124">Como as Ferramentas Globais do .NET Core são executadas em confiança total e geralmente são instaladas no caminho, elas podem ser muito eficientes.</span><span class="sxs-lookup"><span data-stu-id="ae1f4-124">Since .NET Core Global Tools run in full trust and are generally installed on your path, they can be very powerful.</span></span> <span data-ttu-id="ae1f4-125">Não baixe ferramentas de pessoas em quem você não confia.</span><span class="sxs-lookup"><span data-stu-id="ae1f4-125">Don't download tools from people you don't trust.</span></span>

<span data-ttu-id="ae1f4-126">Se a ferramenta estiver hospedada no NuGet, você pode verificar o autor e as estatísticas pesquisando a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="ae1f4-126">If the tool is hosted on NuGet, you can check the author and statistics by searching for the tool.</span></span>

## <a name="install-a-global-tool"></a><span data-ttu-id="ae1f4-127">Instalar uma Ferramenta Global</span><span class="sxs-lookup"><span data-stu-id="ae1f4-127">Install a Global Tool</span></span>

<span data-ttu-id="ae1f4-128">Para instalar uma Ferramenta Global, use o comando [dotnet tool install](dotnet-tool-install.md) da CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ae1f4-128">To install a Global Tool, you use the [dotnet tool install](dotnet-tool-install.md) .NET Core CLI command.</span></span> <span data-ttu-id="ae1f4-129">O seguinte exemplo mostra como instalar uma Ferramenta Global na localização padrão:</span><span class="sxs-lookup"><span data-stu-id="ae1f4-129">The following example shows how to install a Global Tool in the default location:</span></span>

```dotnetcli
dotnet tool install -g dotnetsay
```

<span data-ttu-id="ae1f4-130">Se a ferramenta não puder ser instalada, mensagens de erro serão exibidas.</span><span class="sxs-lookup"><span data-stu-id="ae1f4-130">If the tool can't be installed, error messages are displayed.</span></span> <span data-ttu-id="ae1f4-131">Verifique se os feeds esperados estão sendo verificados.</span><span class="sxs-lookup"><span data-stu-id="ae1f4-131">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="ae1f4-132">Se estiver tentando instalar uma versão de pré-lançamento ou uma versão específica da ferramenta, especifique o número de versão usando o seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="ae1f4-132">If you're trying to install a pre-release version or a specific version of the tool, you can specify the version number using the following format:</span></span>

```dotnetcli
dotnet tool install -g <package-name> --version <version-number>
```

<span data-ttu-id="ae1f4-133">Se a instalação for bem-sucedida, será exibida uma mensagem mostrando o comando usado para chamar a ferramenta e a versão instalada, de maneira semelhante ao seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="ae1f4-133">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```output
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.0.0') was successfully installed.
```

<span data-ttu-id="ae1f4-134">As Ferramentas Globais podem ser instaladas no diretório padrão ou em um local específico.</span><span class="sxs-lookup"><span data-stu-id="ae1f4-134">Global Tools can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="ae1f4-135">Os diretórios padrão são:</span><span class="sxs-lookup"><span data-stu-id="ae1f4-135">The default directories are:</span></span>

| <span data-ttu-id="ae1f4-136">Sistema operacional</span><span class="sxs-lookup"><span data-stu-id="ae1f4-136">OS</span></span>          | <span data-ttu-id="ae1f4-137">Caminho</span><span class="sxs-lookup"><span data-stu-id="ae1f4-137">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="ae1f4-138">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="ae1f4-138">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="ae1f4-139">Windows</span><span class="sxs-lookup"><span data-stu-id="ae1f4-139">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="ae1f4-140">Esses locais são adicionados ao caminho do usuário quando o SDK é executado pela primeira vez e, portanto, as Ferramentas Globais instaladas nesses locais podem ser chamadas diretamente.</span><span class="sxs-lookup"><span data-stu-id="ae1f4-140">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="ae1f4-141">Observe que as Ferramentas Globais são específicas ao usuário e não globais no computador.</span><span class="sxs-lookup"><span data-stu-id="ae1f4-141">Note that the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="ae1f4-142">Ser específico ao usuário significa que não é possível instalar uma Ferramenta Global que esteja disponível para todos os usuários do computador.</span><span class="sxs-lookup"><span data-stu-id="ae1f4-142">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="ae1f4-143">A ferramenta só fica disponível para cada perfil de usuário no qual a ferramenta foi instalada.</span><span class="sxs-lookup"><span data-stu-id="ae1f4-143">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="ae1f4-144">As Ferramentas Globais também podem ser instaladas em um diretório específico.</span><span class="sxs-lookup"><span data-stu-id="ae1f4-144">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="ae1f4-145">Quando elas forem instaladas em um diretório específico, o usuário precisará garantir que o comando esteja disponível, incluindo o diretório no caminho, chamando o comando com o diretório especificado ou chamando a ferramenta no diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="ae1f4-145">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="ae1f4-146">Nesse caso, a CLI do .NET Core não adiciona esse local automaticamente à variável de ambiente PATH.</span><span class="sxs-lookup"><span data-stu-id="ae1f4-146">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="use-the-tool"></a><span data-ttu-id="ae1f4-147">Usar a ferramenta</span><span class="sxs-lookup"><span data-stu-id="ae1f4-147">Use the tool</span></span>

<span data-ttu-id="ae1f4-148">Depois de instalar a ferramenta, chame-a usando seu comando.</span><span class="sxs-lookup"><span data-stu-id="ae1f4-148">Once the tool is installed, you can call it by using its command.</span></span> <span data-ttu-id="ae1f4-149">Observe que o comando pode não ser o mesmo que o nome do pacote.</span><span class="sxs-lookup"><span data-stu-id="ae1f4-149">Note that the command may not be the same as the package name.</span></span>

<span data-ttu-id="ae1f4-150">Se o comando for `dotnetsay`, chame a ferramenta com:</span><span class="sxs-lookup"><span data-stu-id="ae1f4-150">If the command is `dotnetsay`, you call it with:</span></span>

```console
dotnetsay
```

<span data-ttu-id="ae1f4-151">Se o autor da ferramenta desejou que a ferramenta fosse exibida no contexto do prompt do `dotnet`, ele pode ter escrito a ferramenta de modo que você a chame como `dotnet <command>`, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="ae1f4-151">If the tool author wanted the tool to appear in the context of the `dotnet` prompt, they may have written it in a way that you call it as `dotnet <command>`, such as:</span></span>

```dotnetcli
dotnet doc
```

<span data-ttu-id="ae1f4-152">Encontre quais ferramentas estão incluídas em um pacote de Ferramentais Global instalado por meio da listagem dos pacotes instalados usando o comando [dotnet tool list](dotnet-tool-list.md).</span><span class="sxs-lookup"><span data-stu-id="ae1f4-152">You can find which tools are included in an installed Global Tool package by listing the installed packages using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

<span data-ttu-id="ae1f4-153">Procure também instruções de uso no site da ferramenta ou digitando um dos seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="ae1f4-153">You can also look for usage instructions at the tool's website or by typing one of the following commands:</span></span>

```console
<command> --help
dotnet <command> --help
```

## <a name="other-cli-commands"></a><span data-ttu-id="ae1f4-154">Outros comandos da CLI</span><span class="sxs-lookup"><span data-stu-id="ae1f4-154">Other CLI commands</span></span>

<span data-ttu-id="ae1f4-155">O SDK do .NET Core contém outros comandos que dão suporte às Ferramentas Globais do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ae1f4-155">The .NET Core SDK contains other commands that support .NET Core Global Tools.</span></span> <span data-ttu-id="ae1f4-156">Use um dos comandos `dotnet tool` com uma das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="ae1f4-156">Use any of the `dotnet tool` commands with one of the following options:</span></span>

* <span data-ttu-id="ae1f4-157">`--global` ou `-g` especifica que o comando é aplicável às Ferramentas Globais de todos os usuários.</span><span class="sxs-lookup"><span data-stu-id="ae1f4-157">`--global` or `-g` specifies that the command is applicable to user-wide Global Tools.</span></span>
* <span data-ttu-id="ae1f4-158">`--tool-path` especifica um local personalizado para as Ferramentas Globais.</span><span class="sxs-lookup"><span data-stu-id="ae1f4-158">`--tool-path` specifies a custom location for Global Tools.</span></span>

<span data-ttu-id="ae1f4-159">Para descobrir quais comandos estão disponíveis para as Ferramentas Globais:</span><span class="sxs-lookup"><span data-stu-id="ae1f4-159">To find out which commands are available for Global Tools:</span></span>

```dotnetcli
dotnet tool --help
```

<span data-ttu-id="ae1f4-160">A atualização de uma Ferramenta Global envolve sua desinstalação e reinstalação com a última versão estável.</span><span class="sxs-lookup"><span data-stu-id="ae1f4-160">Updating a Global Tool involves uninstalling and reinstalling it with the latest stable version.</span></span> <span data-ttu-id="ae1f4-161">Para atualizar uma Ferramenta Global, use o comando [dotnet tool update](dotnet-tool-update.md):</span><span class="sxs-lookup"><span data-stu-id="ae1f4-161">To update a Global Tool, use the [dotnet tool update](dotnet-tool-update.md) command:</span></span>

```dotnetcli
dotnet tool update -g <packagename>
```

<span data-ttu-id="ae1f4-162">Remova uma Ferramenta Global usando [dotnet tool uninstall](dotnet-tool-uninstall.md):</span><span class="sxs-lookup"><span data-stu-id="ae1f4-162">Remove a Global Tool using the [dotnet tool uninstall](dotnet-tool-uninstall.md):</span></span>

```dotnetcli
dotnet tool uninstall -g <packagename>
```

<span data-ttu-id="ae1f4-163">Para exibir todas as Ferramentas Globais atualmente instaladas no computador, junto com as versões e os comandos, use o comando [dotnet tool list](dotnet-tool-list.md):</span><span class="sxs-lookup"><span data-stu-id="ae1f4-163">To display all of the Global Tools currently installed on the machine, along with their version and commands, use the [dotnet tool list](dotnet-tool-list.md) command:</span></span>

```dotnetcli
dotnet tool list -g
```

## <a name="see-also"></a><span data-ttu-id="ae1f4-164">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae1f4-164">See also</span></span>

* [<span data-ttu-id="ae1f4-165">Solucionar problemas de uso da ferramenta .NET Core</span><span class="sxs-lookup"><span data-stu-id="ae1f4-165">Troubleshoot .NET Core tool usage issues</span></span>](troubleshoot-usage-issues.md)
