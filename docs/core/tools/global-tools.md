---
title: " Ferramentas do .NET Core"
description: Como instalar, usar, atualizar e remover as ferramentas do .NET Core. Aborda ferramentas globais, ferramentas de caminho de ferramenta e ferramentas locais.
author: KathleenDollard
ms.topic: how-to
ms.date: 02/12/2020
ms.openlocfilehash: 08277ed791036201d1dfa30c21799db1c21a924e
ms.sourcegitcommit: 43d5aca3fda42bad8843f6c4e72f6bd52daa55f1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89598127"
---
# <a name="how-to-manage-net-core-tools"></a><span data-ttu-id="0f5a2-104">Como gerenciar as ferramentas do .NET Core</span><span class="sxs-lookup"><span data-stu-id="0f5a2-104">How to manage .NET Core tools</span></span>

<span data-ttu-id="0f5a2-105">**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,1 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="0f5a2-105">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="0f5a2-106">Uma ferramenta .NET Core é um pacote NuGet especial que contém um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-106">A .NET Core tool is a special NuGet package that contains a console application.</span></span> <span data-ttu-id="0f5a2-107">Uma ferramenta pode ser instalada em seu computador das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="0f5a2-107">A tool can be installed on your machine in the following ways:</span></span>

* <span data-ttu-id="0f5a2-108">Como uma ferramenta global.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-108">As a global tool.</span></span>

  <span data-ttu-id="0f5a2-109">Os binários de ferramenta são instalados em um diretório padrão que é adicionado à variável de ambiente PATH.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-109">The tool binaries are installed in a default directory that is added to the PATH environment variable.</span></span> <span data-ttu-id="0f5a2-110">Você pode invocar a ferramenta de qualquer diretório no computador sem especificar seu local.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-110">You can invoke the tool from any directory on the machine without specifying its location.</span></span> <span data-ttu-id="0f5a2-111">Uma versão de uma ferramenta é usada para todos os diretórios no computador.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-111">One version of a tool is used for all directories on the machine.</span></span>

* <span data-ttu-id="0f5a2-112">Como uma ferramenta global em um local personalizado (também conhecido como ferramenta de caminho de ferramenta).</span><span class="sxs-lookup"><span data-stu-id="0f5a2-112">As a global tool in a custom location (also known as a tool-path tool).</span></span>

  <span data-ttu-id="0f5a2-113">Os binários de ferramenta são instalados em um local que você especificar.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-113">The tool binaries are installed in a location that you specify.</span></span> <span data-ttu-id="0f5a2-114">Você pode invocar a ferramenta no diretório de instalação ou fornecendo o diretório com o nome do comando ou adicionando o diretório à variável de ambiente PATH.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-114">You can invoke the tool from the installation directory or by providing the directory with the command name or by adding the directory to the PATH environment variable.</span></span> <span data-ttu-id="0f5a2-115">Uma versão de uma ferramenta é usada para todos os diretórios no computador.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-115">One version of a tool is used for all directories on the machine.</span></span>

* <span data-ttu-id="0f5a2-116">Como uma ferramenta local (aplica-se a SDK do .NET Core 3,0 e posterior).</span><span class="sxs-lookup"><span data-stu-id="0f5a2-116">As a local tool (applies to .NET Core SDK 3.0 and later).</span></span>

  <span data-ttu-id="0f5a2-117">Os binários de ferramenta são instalados em um diretório padrão.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-117">The tool binaries are installed in a default directory.</span></span> <span data-ttu-id="0f5a2-118">Você invoca a ferramenta no diretório de instalação ou em qualquer um de seus subdiretórios.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-118">You invoke the tool from the installation directory or any of its subdirectories.</span></span> <span data-ttu-id="0f5a2-119">Diretórios diferentes podem usar versões diferentes da mesma ferramenta.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-119">Different directories can use different versions of the same tool.</span></span>
  
  <span data-ttu-id="0f5a2-120">A CLI do .NET usa arquivos de manifesto para controlar quais ferramentas são instaladas como locais em um diretório.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-120">The .NET CLI uses manifest files to keep track of which tools are installed as local to a directory.</span></span> <span data-ttu-id="0f5a2-121">Quando o arquivo de manifesto é salvo no diretório raiz de um repositório de código-fonte, um colaborador pode clonar o repositório e invocar um único comando CLI do .NET Core que instala todas as ferramentas listadas nos arquivos de manifesto.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-121">When the manifest file is saved in the root directory of a source code repository, a contributor can clone the repository and invoke a single .NET Core CLI command that installs all of the tools listed in the manifest files.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0f5a2-122">As ferramentas do .NET Core são executadas com confiança total.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-122">.NET Core tools run in full trust.</span></span> <span data-ttu-id="0f5a2-123">Não instale uma ferramenta do .NET Core, a menos que você confie no autor.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-123">Do not install a .NET Core tool unless you trust the author.</span></span>

## <a name="find-a-tool"></a><span data-ttu-id="0f5a2-124">Encontrar uma ferramenta</span><span class="sxs-lookup"><span data-stu-id="0f5a2-124">Find a tool</span></span>

<span data-ttu-id="0f5a2-125">Atualmente, o .NET Core não tem um recurso de pesquisa de ferramenta.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-125">Currently, .NET Core doesn't have a tool search feature.</span></span> <span data-ttu-id="0f5a2-126">Aqui estão algumas maneiras de encontrar ferramentas:</span><span class="sxs-lookup"><span data-stu-id="0f5a2-126">Here are some ways to find tools:</span></span>

* <span data-ttu-id="0f5a2-127">Pesquise o site do [NuGet](https://www.nuget.org) usando o filtro de tipo de pacote "ferramenta .net".</span><span class="sxs-lookup"><span data-stu-id="0f5a2-127">Search the [NuGet](https://www.nuget.org) website by using the ".NET tool" package type filter.</span></span> <span data-ttu-id="0f5a2-128">Para obter mais informações, consulte [Localizando e escolhendo pacotes](/nuget/consume-packages/finding-and-choosing-packages).</span><span class="sxs-lookup"><span data-stu-id="0f5a2-128">For more information, see [Finding and choosing packages](/nuget/consume-packages/finding-and-choosing-packages).</span></span>
* <span data-ttu-id="0f5a2-129">Consulte a lista de ferramentas no repositório GitHub [natemcmaster/dotnet-Tools](https://github.com/natemcmaster/dotnet-tools) .</span><span class="sxs-lookup"><span data-stu-id="0f5a2-129">See the list of tools in the [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) GitHub repository.</span></span>
* <span data-ttu-id="0f5a2-130">Use [ToolGet](https://www.toolget.net/) para procurar ferramentas .net.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-130">Use [ToolGet](https://www.toolget.net/) to search for .NET tools.</span></span>
* <span data-ttu-id="0f5a2-131">Consulte o código-fonte para as ferramentas criadas pela equipe de ASP.NET Core no [diretório de ferramentas do repositório do GitHub dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/tree/master/src/Tools).</span><span class="sxs-lookup"><span data-stu-id="0f5a2-131">See the source code for the tools created by the ASP.NET Core team in the [Tools directory of the dotnet/aspnetcore GitHub repository](https://github.com/dotnet/aspnetcore/tree/master/src/Tools).</span></span>
* <span data-ttu-id="0f5a2-132">Saiba mais sobre as ferramentas de diagnóstico nas [ferramentas de diagnóstico do .NET Core dotnet](../diagnostics/index.md#net-core-diagnostic-global-tools).</span><span class="sxs-lookup"><span data-stu-id="0f5a2-132">Learn about diagnostic tools at [.NET Core dotnet diagnostic tools](../diagnostics/index.md#net-core-diagnostic-global-tools).</span></span>

## <a name="check-the-author-and-statistics"></a><span data-ttu-id="0f5a2-133">Verificar o autor e as estatísticas</span><span class="sxs-lookup"><span data-stu-id="0f5a2-133">Check the author and statistics</span></span>

<span data-ttu-id="0f5a2-134">Como as ferramentas do .NET Core são executadas com confiança total e as ferramentas globais são adicionadas à variável de ambiente PATH, elas podem ser muito poderosas.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-134">Since .NET Core tools run in full trust, and global tools are added to the PATH environment variable, they can be very powerful.</span></span> <span data-ttu-id="0f5a2-135">Não baixe ferramentas de pessoas em quem você não confia.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-135">Don't download tools from people you don't trust.</span></span>

<span data-ttu-id="0f5a2-136">Se a ferramenta estiver hospedada no NuGet, você pode verificar o autor e as estatísticas pesquisando a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-136">If the tool is hosted on NuGet, you can check the author and statistics by searching for the tool.</span></span>

## <a name="install-a-global-tool"></a><span data-ttu-id="0f5a2-137">Instalar uma ferramenta global</span><span class="sxs-lookup"><span data-stu-id="0f5a2-137">Install a global tool</span></span>

<span data-ttu-id="0f5a2-138">Para instalar uma ferramenta como uma ferramenta global, use a `-g` `--global` opção ou da [instalação da ferramenta dotnet](dotnet-tool-install.md), conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="0f5a2-138">To install a tool as a global tool, use the `-g` or `--global` option of [dotnet tool install](dotnet-tool-install.md), as shown in the following example:</span></span>

```dotnetcli
dotnet tool install -g dotnetsay
```

<span data-ttu-id="0f5a2-139">A saída mostra o comando usado para invocar a ferramenta e a versão instalada, semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="0f5a2-139">The output shows the command used to invoke the tool and the version installed, similar to the following example:</span></span>

```output
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
```

<span data-ttu-id="0f5a2-140">O local padrão para os binários de uma ferramenta depende do sistema operacional:</span><span class="sxs-lookup"><span data-stu-id="0f5a2-140">The default location for a tool's binaries depends on the operating system:</span></span>

| <span data-ttu-id="0f5a2-141">Sistema operacional</span><span class="sxs-lookup"><span data-stu-id="0f5a2-141">OS</span></span>          | <span data-ttu-id="0f5a2-142">Caminho</span><span class="sxs-lookup"><span data-stu-id="0f5a2-142">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="0f5a2-143">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="0f5a2-143">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="0f5a2-144">Windows</span><span class="sxs-lookup"><span data-stu-id="0f5a2-144">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="0f5a2-145">Esse local é adicionado ao caminho do usuário quando o SDK é executado pela primeira vez, portanto, as ferramentas globais podem ser invocadas de qualquer diretório sem especificar o local da ferramenta.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-145">This location is added to the user's path when the SDK is first run, so global tools can be invoked from any directory without specifying the tool location.</span></span>

<span data-ttu-id="0f5a2-146">O acesso à ferramenta é específico do usuário, não do computador global.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-146">Tool access is user-specific, not machine global.</span></span> <span data-ttu-id="0f5a2-147">Uma ferramenta global só está disponível para o usuário que instalou a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-147">A global tool is only available to the user that installed the tool.</span></span>

### <a name="install-a-global-tool-in-a-custom-location"></a><span data-ttu-id="0f5a2-148">Instalar uma ferramenta global em um local personalizado</span><span class="sxs-lookup"><span data-stu-id="0f5a2-148">Install a global tool in a custom location</span></span>

<span data-ttu-id="0f5a2-149">Para instalar uma ferramenta como uma ferramenta global em um local personalizado, use a `--tool-path` opção de [instalação da ferramenta dotnet](dotnet-tool-install.md), conforme mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-149">To install a tool as a global tool in a custom location, use the `--tool-path` option of [dotnet tool install](dotnet-tool-install.md), as shown in the following examples.</span></span>

<span data-ttu-id="0f5a2-150">No Windows:</span><span class="sxs-lookup"><span data-stu-id="0f5a2-150">On Windows:</span></span>

```dotnetcli
dotnet tool install dotnetsay --tool-path c:\dotnet-tools
```

<span data-ttu-id="0f5a2-151">No Linux ou macOS:</span><span class="sxs-lookup"><span data-stu-id="0f5a2-151">On Linux or macOS:</span></span>

```dotnetcli
dotnet tool install dotnetsay --tool-path ~/bin
```

<span data-ttu-id="0f5a2-152">O SDK do .NET Core não adiciona esse local automaticamente à variável de ambiente PATH.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-152">The .NET Core SDK doesn't add this location automatically to the PATH environment variable.</span></span> <span data-ttu-id="0f5a2-153">Para [invocar uma ferramenta de caminho de ferramenta](#invoke-a-tool-path-tool), você precisa certificar-se de que o comando está disponível usando um dos seguintes métodos:</span><span class="sxs-lookup"><span data-stu-id="0f5a2-153">To [invoke a tool-path tool](#invoke-a-tool-path-tool), you have to make sure the command is available by using one of the following methods:</span></span>

* <span data-ttu-id="0f5a2-154">Adicione o diretório de instalação à variável de ambiente PATH.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-154">Add the installation directory to the PATH environment variable.</span></span>
* <span data-ttu-id="0f5a2-155">Especifique o caminho completo para a ferramenta ao chamá-lo.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-155">Specify the full path to the tool when you invoke it.</span></span>
* <span data-ttu-id="0f5a2-156">Invoque a ferramenta de dentro do diretório de instalação.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-156">Invoke the tool from within the installation directory.</span></span>

## <a name="install-a-local-tool"></a><span data-ttu-id="0f5a2-157">Instalar uma ferramenta local</span><span class="sxs-lookup"><span data-stu-id="0f5a2-157">Install a local tool</span></span>

<span data-ttu-id="0f5a2-158">**Aplica-se ao SDK do .NET Core 3,0 e posterior.**</span><span class="sxs-lookup"><span data-stu-id="0f5a2-158">**Applies to .NET Core 3.0 SDK and later.**</span></span>

<span data-ttu-id="0f5a2-159">Para instalar uma ferramenta somente para acesso local (para o diretório e subdiretórios atuais), ela deve ser adicionada a um arquivo de manifesto da ferramenta.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-159">To install a tool for local access only (for the current directory and subdirectories), it has to be added to a tool manifest file.</span></span> <span data-ttu-id="0f5a2-160">Para criar um arquivo de manifesto da ferramenta, execute o `dotnet new tool-manifest` comando:</span><span class="sxs-lookup"><span data-stu-id="0f5a2-160">To create a tool manifest file, run the `dotnet new tool-manifest` command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="0f5a2-161">Este comando cria um arquivo de manifesto chamado *dotnet-tools.jsno* diretório *. config* .</span><span class="sxs-lookup"><span data-stu-id="0f5a2-161">This command creates a manifest file named *dotnet-tools.json* under the *.config* directory.</span></span> <span data-ttu-id="0f5a2-162">Para adicionar uma ferramenta local ao arquivo de manifesto, use o comando de [instalação da ferramenta dotnet](dotnet-tool-install.md) e **omita** as `--global` `--tool-path` Opções e, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="0f5a2-162">To add a local tool to the manifest file, use the [dotnet tool install](dotnet-tool-install.md) command and **omit** the `--global` and `--tool-path` options, as shown in the following example:</span></span>

```dotnetcli
dotnet tool install dotnetsay
```

<span data-ttu-id="0f5a2-163">A saída do comando mostra em qual arquivo de manifesto a ferramenta recém-instalada está, semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="0f5a2-163">The command output shows which manifest file the newly installed tool is in, similar to the following example:</span></span>

```console
You can invoke the tool from this directory using the following command:
dotnet tool run dotnetsay
Tool 'dotnetsay' (version '2.1.4') was successfully installed.
Entry is added to the manifest file /home/name/botsay/.config/dotnet-tools.json.
```

<span data-ttu-id="0f5a2-164">O exemplo a seguir mostra um arquivo de manifesto com duas ferramentas locais instaladas:</span><span class="sxs-lookup"><span data-stu-id="0f5a2-164">The following example shows a manifest file with two local tools installed:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "botsay": {
      "version": "1.0.0",
      "commands": [
        "botsay"
      ]
    },
    "dotnetsay": {
      "version": "2.1.3",
      "commands": [
        "dotnetsay"
      ]
    }
  }
}
```

<span data-ttu-id="0f5a2-165">Normalmente, você adiciona uma ferramenta local ao diretório raiz do repositório.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-165">You typically add a local tool to the root directory of the repository.</span></span> <span data-ttu-id="0f5a2-166">Depois de fazer o check-in do arquivo de manifesto para o repositório, os desenvolvedores que confiram o código do repositório obtêm o arquivo de manifesto mais recente.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-166">After you check in the manifest file to the repository, developers who check out code from the repository get the latest manifest file.</span></span> <span data-ttu-id="0f5a2-167">Para instalar todas as ferramentas listadas no arquivo de manifesto, elas executam o `dotnet tool restore` comando:</span><span class="sxs-lookup"><span data-stu-id="0f5a2-167">To install all of the tools listed in the manifest file, they run the `dotnet tool restore` command:</span></span>

```dotnetcli
dotnet tool restore
```

<span data-ttu-id="0f5a2-168">A saída indica quais ferramentas foram restauradas:</span><span class="sxs-lookup"><span data-stu-id="0f5a2-168">The output indicates which tools were restored:</span></span>

```console
Tool 'botsay' (version '1.0.0') was restored. Available commands: botsay
Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
Restore was successful.
```

## <a name="install-a-specific-tool-version"></a><span data-ttu-id="0f5a2-169">Instalar uma versão específica da ferramenta</span><span class="sxs-lookup"><span data-stu-id="0f5a2-169">Install a specific tool version</span></span>

<span data-ttu-id="0f5a2-170">Para instalar uma versão de pré-lançamento ou uma versão específica de uma ferramenta, especifique o número de versão usando a `--version` opção, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="0f5a2-170">To install a pre-release version or a specific version of a tool, specify the version number by using the `--version` option, as shown in the following example:</span></span>

```dotnetcli
dotnet tool install dotnetsay --version 2.1.3
```

## <a name="use-a-tool"></a><span data-ttu-id="0f5a2-171">Usar uma ferramenta</span><span class="sxs-lookup"><span data-stu-id="0f5a2-171">Use a tool</span></span>

<span data-ttu-id="0f5a2-172">O comando que você usa para invocar uma ferramenta pode ser diferente do nome do pacote que você instalar.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-172">The command that you use to invoke a tool may be different from the name of the package that you install.</span></span> <span data-ttu-id="0f5a2-173">Para exibir todas as ferramentas atualmente instaladas no computador para o usuário atual, use o comando [dotnet da lista de ferramentas](dotnet-tool-list.md) :</span><span class="sxs-lookup"><span data-stu-id="0f5a2-173">To display all of the tools currently installed on the machine for the current user, use the [dotnet tool list](dotnet-tool-list.md) command:</span></span>

```dotnetcli
dotnet tool list
```

<span data-ttu-id="0f5a2-174">A saída mostra a versão e o comando de cada ferramenta, semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="0f5a2-174">The output shows each tool's version and command, similar to the following example:</span></span>

```console
Package Id      Version      Commands       Manifest
-------------------------------------------------------------------------------------------
botsay          1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
dotnetsay       2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
```

<span data-ttu-id="0f5a2-175">Conforme mostrado neste exemplo, a lista mostra as ferramentas locais.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-175">As shown in this example, the list shows local tools.</span></span> <span data-ttu-id="0f5a2-176">Para ver as ferramentas globais, use a `--global` opção e para ver as ferramentas de caminho de ferramenta, use a `--tool-path` opção.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-176">To see global tools, use the `--global` option, and to see tool-path tools, use the `--tool-path` option.</span></span>

### <a name="invoke-a-global-tool"></a><span data-ttu-id="0f5a2-177">Invocar uma ferramenta global</span><span class="sxs-lookup"><span data-stu-id="0f5a2-177">Invoke a global tool</span></span>

<span data-ttu-id="0f5a2-178">Para ferramentas globais, use o comando de ferramenta por si só.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-178">For global tools, use the tool command by itself.</span></span> <span data-ttu-id="0f5a2-179">Por exemplo, se o comando for `dotnetsay` ou `dotnet-doc` , é isso que você usa para invocar o comando:</span><span class="sxs-lookup"><span data-stu-id="0f5a2-179">For example, if the command is `dotnetsay` or `dotnet-doc`, that's what you use to invoke the command:</span></span>

```console
dotnetsay
dotnet-doc
```

<span data-ttu-id="0f5a2-180">Se o comando começar com o prefixo `dotnet-` , uma maneira alternativa de invocar a ferramenta é usar o `dotnet` comando e omitir o prefixo de comando da ferramenta.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-180">If the command begins with the prefix `dotnet-`, an alternative way to invoke the tool is to use the `dotnet` command and omit the tool command prefix.</span></span> <span data-ttu-id="0f5a2-181">Por exemplo, se o comando for `dotnet-doc` , o comando a seguir invocará a ferramenta:</span><span class="sxs-lookup"><span data-stu-id="0f5a2-181">For example, if the command is `dotnet-doc`, the following command invokes the tool:</span></span>

```dotnetcli
dotnet doc
```

<span data-ttu-id="0f5a2-182">No entanto, no cenário a seguir, você não pode usar o `dotnet` comando para invocar uma ferramenta global:</span><span class="sxs-lookup"><span data-stu-id="0f5a2-182">However, in the following scenario you can't use the `dotnet` command to invoke a global tool:</span></span>

* <span data-ttu-id="0f5a2-183">Uma ferramenta global e uma ferramenta local têm o mesmo comando prefixado pelo `dotnet-` .</span><span class="sxs-lookup"><span data-stu-id="0f5a2-183">A global tool and a local tool have the same command prefixed by `dotnet-`.</span></span>
* <span data-ttu-id="0f5a2-184">Você deseja invocar a ferramenta global de um diretório que está no escopo da ferramenta local.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-184">You want to invoke the global tool from a directory that is in scope for the local tool.</span></span>

<span data-ttu-id="0f5a2-185">Nesse cenário, `dotnet doc` e `dotnet dotnet-doc` invoca a ferramenta local.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-185">In this scenario, `dotnet doc` and `dotnet dotnet-doc` invoke the local tool.</span></span> <span data-ttu-id="0f5a2-186">Para invocar a ferramenta global, use o comando por si só:</span><span class="sxs-lookup"><span data-stu-id="0f5a2-186">To invoke the global tool, use the command by itself:</span></span>

```dotnetcli
dotnet-doc
```

### <a name="invoke-a-tool-path-tool"></a><span data-ttu-id="0f5a2-187">Invocar uma ferramenta de caminho de ferramenta</span><span class="sxs-lookup"><span data-stu-id="0f5a2-187">Invoke a tool-path tool</span></span>

<span data-ttu-id="0f5a2-188">Para invocar uma ferramenta global que é instalada usando a `tool-path` opção, verifique se o comando está disponível, conforme explicado [anteriormente neste artigo](#install-a-global-tool-in-a-custom-location).</span><span class="sxs-lookup"><span data-stu-id="0f5a2-188">To invoke a global tool that is installed by using the `tool-path` option, make sure the command is available, as explained [earlier in this article](#install-a-global-tool-in-a-custom-location).</span></span>

### <a name="invoke-a-local-tool"></a><span data-ttu-id="0f5a2-189">Invocar uma ferramenta local</span><span class="sxs-lookup"><span data-stu-id="0f5a2-189">Invoke a local tool</span></span>

<span data-ttu-id="0f5a2-190">Para invocar uma ferramenta local, você precisa usar o `dotnet` comando de dentro do diretório de instalação.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-190">To invoke a local tool, you have to use the `dotnet` command from within the installation directory.</span></span> <span data-ttu-id="0f5a2-191">Você pode usar a forma longa ( `dotnet tool run <COMMAND_NAME>` ) ou a forma abreviada ( `dotnet <COMMAND_NAME>` ), conforme mostrado nos exemplos a seguir:</span><span class="sxs-lookup"><span data-stu-id="0f5a2-191">You can use the long form (`dotnet tool run <COMMAND_NAME>`) or the short form (`dotnet <COMMAND_NAME>`), as shown in the following examples:</span></span>

```dotnetcli
dotnet tool run dotnetsay
dotnet dotnetsay
```

<span data-ttu-id="0f5a2-192">Se o comando for prefixado pelo `dotnet-` , você poderá incluir ou omitir o prefixo ao invocar a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-192">If the command is prefixed by `dotnet-`, you can include or omit the prefix when you invoke the tool.</span></span> <span data-ttu-id="0f5a2-193">Por exemplo, se o comando for `dotnet-doc` , qualquer um dos seguintes exemplos invocará a ferramenta local:</span><span class="sxs-lookup"><span data-stu-id="0f5a2-193">For example, if the command is `dotnet-doc`, any of the following examples invokes the local tool:</span></span>

```dotnetcli
dotnet tool run dotnet-doc
dotnet dotnet-doc
dotnet doc
```

## <a name="update-a-tool"></a><span data-ttu-id="0f5a2-194">Atualizar uma ferramenta</span><span class="sxs-lookup"><span data-stu-id="0f5a2-194">Update a tool</span></span>

<span data-ttu-id="0f5a2-195">A atualização de uma ferramenta envolve a desinstalação e a reinstalação com a versão estável mais recente.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-195">Updating a tool involves uninstalling and reinstalling it with the latest stable version.</span></span> <span data-ttu-id="0f5a2-196">Para atualizar uma ferramenta, use o comando [dotnet ferramenta de atualização](dotnet-tool-update.md) com a mesma opção usada para instalar a ferramenta:</span><span class="sxs-lookup"><span data-stu-id="0f5a2-196">To update a tool, use the [dotnet tool update](dotnet-tool-update.md) command with the same option that you used to install the tool:</span></span>

```dotnetcli
dotnet tool update --global <packagename>
dotnet tool update --tool-path <packagename>
dotnet tool update <packagename>
```

<span data-ttu-id="0f5a2-197">Para uma ferramenta local, o SDK encontra o primeiro arquivo de manifesto que contém a ID do pacote examinando o diretório atual e os diretórios pai.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-197">For a local tool, the SDK finds the first manifest file that contains the package ID by looking in the current directory and parent directories.</span></span> <span data-ttu-id="0f5a2-198">Se não houver nenhuma ID de pacote em nenhum arquivo de manifesto, o SDK adicionará uma nova entrada ao arquivo de manifesto mais próximo.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-198">If there is no such package ID in any manifest file, the SDK adds a new entry to the closest manifest file.</span></span>

## <a name="uninstall-a-tool"></a><span data-ttu-id="0f5a2-199">Desinstalar uma ferramenta</span><span class="sxs-lookup"><span data-stu-id="0f5a2-199">Uninstall a tool</span></span>

<span data-ttu-id="0f5a2-200">Remova uma ferramenta usando o comando [dotnet ferramenta de desinstalação](dotnet-tool-uninstall.md) com a mesma opção usada para instalar a ferramenta:</span><span class="sxs-lookup"><span data-stu-id="0f5a2-200">Remove a tool by using the [dotnet tool uninstall](dotnet-tool-uninstall.md) command with the same option that you used to install the tool:</span></span>

```dotnetcli
dotnet tool uninstall --global <packagename>
dotnet tool uninstall --tool-path <packagename>
dotnet tool uninstall <packagename>
```

<span data-ttu-id="0f5a2-201">Para uma ferramenta local, o SDK encontra o primeiro arquivo de manifesto que contém a ID do pacote examinando o diretório atual e os diretórios pai.</span><span class="sxs-lookup"><span data-stu-id="0f5a2-201">For a local tool, the SDK finds the first manifest file that contains the package ID by looking in the current directory and parent directories.</span></span>

## <a name="get-help-and-troubleshoot"></a><span data-ttu-id="0f5a2-202">Obter ajuda e solucionar problemas</span><span class="sxs-lookup"><span data-stu-id="0f5a2-202">Get help and troubleshoot</span></span>

<span data-ttu-id="0f5a2-203">Para obter uma lista de `dotnet tool` comandos disponíveis, digite o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="0f5a2-203">To get a list of available `dotnet tool` commands, enter the following command:</span></span>

```dotnetcli
dotnet tool --help
```

<span data-ttu-id="0f5a2-204">Para obter instruções de uso da ferramenta, insira um dos comandos a seguir ou consulte o site da ferramenta:</span><span class="sxs-lookup"><span data-stu-id="0f5a2-204">To get tool usage instructions, enter one of the following commands or see the tool's website:</span></span>

```dotnetcli
<command> --help
dotnet <command> --help
```

<span data-ttu-id="0f5a2-205">Se uma ferramenta não for instalada ou executada, consulte [solucionar problemas de uso da ferramenta .NET Core](troubleshoot-usage-issues.md).</span><span class="sxs-lookup"><span data-stu-id="0f5a2-205">If a tool fails to install or run, see [Troubleshoot .NET Core tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0f5a2-206">Confira também</span><span class="sxs-lookup"><span data-stu-id="0f5a2-206">See also</span></span>

- [<span data-ttu-id="0f5a2-207">Tutorial: criar uma ferramenta do .NET Core usando o CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="0f5a2-207">Tutorial: Create a .NET Core tool using the .NET Core CLI</span></span>](global-tools-how-to-create.md)
- [<span data-ttu-id="0f5a2-208">Tutorial: instalar e usar uma ferramenta global do .NET Core usando o CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="0f5a2-208">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="0f5a2-209">Tutorial: instalar e usar uma ferramenta local do .NET Core usando o CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="0f5a2-209">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
