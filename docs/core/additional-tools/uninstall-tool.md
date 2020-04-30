---
title: Ferramenta de desinstalação
description: Uma visão geral da ferramenta de desinstalação do .NET Core, uma ferramenta guiada que permite a limpeza controlada de SDKs e tempos de execução do .NET Core.
author: sfoslund
ms.date: 01/06/2020
ms.openlocfilehash: 45cf0841391d02636770e98666e2897d2598fab4
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595709"
---
# <a name="net-core-uninstall-tool"></a><span data-ttu-id="e0f5f-103">Ferramenta de Desinstalação do .NET Core</span><span class="sxs-lookup"><span data-stu-id="e0f5f-103">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="e0f5f-104">A [ferramenta de desinstalação do .NET Core](https://aka.ms/dotnet-core-uninstall-tool) (`dotnet-core-uninstall`) permite que você remova os SDKs do .NET Core e os tempos de execução de um sistema.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-104">The [.NET Core Uninstall Tool](https://aka.ms/dotnet-core-uninstall-tool) (`dotnet-core-uninstall`) lets you remove .NET Core SDKs and Runtimes from a system.</span></span> <span data-ttu-id="e0f5f-105">Uma coleção de opções está disponível para especificar quais versões você deseja desinstalar.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-105">A collection of options is available to specify which versions you want to uninstall.</span></span>

<span data-ttu-id="e0f5f-106">A ferramenta dá suporte ao Windows e ao macOS.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-106">The tool supports Windows and macOS.</span></span> <span data-ttu-id="e0f5f-107">O Linux não tem suporte no momento.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-107">Linux is currently not supported.</span></span>

<span data-ttu-id="e0f5f-108">No Windows, a ferramenta só pode desinstalar SDKs e tempos de execução que foram instalados usando um dos seguintes instaladores:</span><span class="sxs-lookup"><span data-stu-id="e0f5f-108">On Windows, the tool can only uninstall SDKs and Runtimes that were installed using one of the following installers:</span></span>

- <span data-ttu-id="e0f5f-109">O SDK do .NET Core e o instalador de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-109">The .NET Core SDK and runtime installer.</span></span>
- <span data-ttu-id="e0f5f-110">O instalador do Visual Studio em versões anteriores ao Visual Studio 2019 versão 16,3.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-110">The Visual Studio installer in versions earlier than Visual Studio 2019 version 16.3.</span></span>

<span data-ttu-id="e0f5f-111">No macOS, a ferramenta só pode desinstalar SDKs e tempos de execução localizados na pasta */usr/local/share/dotnet*</span><span class="sxs-lookup"><span data-stu-id="e0f5f-111">On macOS, the tool can only uninstall SDKs and runtimes located in the */usr/local/share/dotnet* folder.</span></span>

<span data-ttu-id="e0f5f-112">Devido a essas limitações, a ferramenta pode não ser capaz de desinstalar todos os SDKs do .NET Core e os tempos de execução em seu computador.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-112">Because of these limitations, the tool may not be able to uninstall all of the .NET Core SDKs and runtimes on your machine.</span></span> <span data-ttu-id="e0f5f-113">Você pode usar o `dotnet --info` comando para localizar todos os SDKs do .NET Core e os tempos de execução instalados, incluindo os SDKs e os tempos de execução que essa ferramenta não pode remover.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-113">You can use the `dotnet --info` command to find all of the .NET Core SDKs and runtimes installed, including those SDKs and runtimes that this tool can't remove.</span></span> <span data-ttu-id="e0f5f-114">O `dotnet-core-uninstall list` comando exibe quais SDKs podem ser desinstalados com a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-114">The `dotnet-core-uninstall list` command displays which SDKs can be uninstalled with the tool.</span></span>

## <a name="install-the-tool"></a><span data-ttu-id="e0f5f-115">Instalar a ferramenta</span><span class="sxs-lookup"><span data-stu-id="e0f5f-115">Install the tool</span></span>

<span data-ttu-id="e0f5f-116">Você pode baixar a ferramenta de desinstalação do .NET Core [aqui](https://aka.ms/dotnet-core-uninstall-tool) e encontrar o código-fonte no repositório do GitHub [dotnet/CLI-Lab](https://github.com/dotnet/cli-lab) .</span><span class="sxs-lookup"><span data-stu-id="e0f5f-116">You can download the .NET Core Uninstall Tool from [here](https://aka.ms/dotnet-core-uninstall-tool) and find the source code at the [dotnet/cli-lab](https://github.com/dotnet/cli-lab) GitHub repository.</span></span>

> [!NOTE]
> <span data-ttu-id="e0f5f-117">A ferramenta requer elevação para desinstalar SDKs e tempos de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-117">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="e0f5f-118">Portanto, ele deve ser instalado em um diretório protegido contra gravação, como *c:\Arquivos de programas* no Windows ou */usr/local/bin* no MacOS.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-118">Therefore, it should be installed in a write-protected directory such as *C:\Program Files* on Windows or */usr/local/bin* on macOS.</span></span> <span data-ttu-id="e0f5f-119">Consulte também [acesso elevado para comandos dotnet](../tools/elevated-access.md).</span><span class="sxs-lookup"><span data-stu-id="e0f5f-119">See also [Elevated access for dotnet commands](../tools/elevated-access.md).</span></span> <span data-ttu-id="e0f5f-120">Para obter mais informações, consulte as [instruções detalhadas de instalação](https://aka.ms/dotnet-core-uninstall-tool).</span><span class="sxs-lookup"><span data-stu-id="e0f5f-120">For more information, see the [detailed installation instructions](https://aka.ms/dotnet-core-uninstall-tool).</span></span>

## <a name="run-the-tool"></a><span data-ttu-id="e0f5f-121">Executar a ferramenta</span><span class="sxs-lookup"><span data-stu-id="e0f5f-121">Run the tool</span></span>

<span data-ttu-id="e0f5f-122">As etapas a seguir mostram a abordagem recomendada para executar a ferramenta de desinstalação:</span><span class="sxs-lookup"><span data-stu-id="e0f5f-122">The following steps show the recommended approach for running the uninstall tool:</span></span>

- [<span data-ttu-id="e0f5f-123">Etapa 1-exibir os SDKs e os tempos de execução do .NET Core instalados</span><span class="sxs-lookup"><span data-stu-id="e0f5f-123">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>](#step-1---display-installed-net-core-sdks-and-runtimes)
- [<span data-ttu-id="e0f5f-124">Etapa 2 – fazer uma simulação</span><span class="sxs-lookup"><span data-stu-id="e0f5f-124">Step 2 - Do a dry run</span></span>](#step-2---do-a-dry-run)
- [<span data-ttu-id="e0f5f-125">Etapa 3-desinstalar SDKs e tempos de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="e0f5f-125">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>](#step-3---uninstall-net-core-sdks-and-runtimes)
- [<span data-ttu-id="e0f5f-126">Etapa 4-excluir a pasta de fallback do NuGet (opcional)</span><span class="sxs-lookup"><span data-stu-id="e0f5f-126">Step 4 - Delete the NuGet fallback folder (optional)</span></span>](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-core-sdks-and-runtimes"></a><span data-ttu-id="e0f5f-127">Etapa 1-exibir os SDKs e os tempos de execução do .NET Core instalados</span><span class="sxs-lookup"><span data-stu-id="e0f5f-127">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>

<span data-ttu-id="e0f5f-128">O `dotnet-core-uninstall list` comando lista os SDKs e os tempos de execução do .NET Core instalados que podem ser removidos com essa ferramenta.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-128">The `dotnet-core-uninstall list` command lists the installed .NET Core SDKs and runtimes that can be removed with this tool.</span></span> <span data-ttu-id="e0f5f-129">Alguns SDKs e tempos de execução podem ser exigidos pelo Visual Studio e são exibidos com uma observação de por que não é recomendável desinstalá-los.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-129">Some SDKs and runtimes may be required by Visual Studio and they're displayed with a note of why it isn't recommended to uninstall them.</span></span>

> [!NOTE]
> <span data-ttu-id="e0f5f-130">A saída do `dotnet-core-uninstall list` comando não corresponderá à lista de versões instaladas na saída de `dotnet --info` , na maioria dos casos.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-130">The output of the `dotnet-core-uninstall list` command will not match the list of installed versions in the output of `dotnet --info` in most cases.</span></span> <span data-ttu-id="e0f5f-131">Especificamente, essa ferramenta não exibirá versões instaladas por arquivos zip ou gerenciados pelo Visual Studio (qualquer versão instalada com o Visual Studio 2019 16,3 ou posterior).</span><span class="sxs-lookup"><span data-stu-id="e0f5f-131">Specifically, this tool will not display versions installed by zip files or managed by Visual Studio (any version installed with Visual Studio 2019 16.3 or later).</span></span> <span data-ttu-id="e0f5f-132">Uma maneira de verificar se uma versão é gerenciada pelo Visual Studio é exibi-la `Add or Remove Programs`no, onde as versões gerenciadas do Visual Studio são marcadas como tais em seus nomes de exibição.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-132">One way to check if a version is managed by Visual Studio is to view it in `Add or Remove Programs`, where Visual Studio managed versions are marked as such in their display names.</span></span>

<span data-ttu-id="e0f5f-133">**dotnet-núcleo-desinstalação da lista**</span><span class="sxs-lookup"><span data-stu-id="e0f5f-133">**dotnet-core-uninstall list**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="e0f5f-134">Sinopse</span><span class="sxs-lookup"><span data-stu-id="e0f5f-134">Synopsis</span></span>

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a><span data-ttu-id="e0f5f-135">Opções</span><span class="sxs-lookup"><span data-stu-id="e0f5f-135">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="e0f5f-136">Windows</span><span class="sxs-lookup"><span data-stu-id="e0f5f-136">Windows</span></span>](#tab/windows)

* **`--aspnet-runtime`**

  <span data-ttu-id="e0f5f-137">Lista todos os tempos de execução de ASP.NET Core que podem ser desinstalados com essa ferramenta.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-137">Lists all the ASP.NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="e0f5f-138">Lista todos os pacotes de hospedagem e de tempo de execução do .NET Core que podem ser desinstalados com essa ferramenta.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-138">Lists all the .NET Core runtime and hosting bundles that can be uninstalled with this tool.</span></span>

* **`--runtime`**

  <span data-ttu-id="e0f5f-139">Lista todos os tempos de execução do .NET Core que podem ser desinstalados com essa ferramenta.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-139">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="e0f5f-140">Lista todos os SDKs do .NET Core que podem ser desinstalados com essa ferramenta.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-140">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="e0f5f-141">Define o nível de detalhes.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-141">Sets the verbosity level.</span></span> <span data-ttu-id="e0f5f-142">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-142">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="e0f5f-143">O valor padrão é `normal`.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-143">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="e0f5f-144">Lista todos os SDKs e tempos de execução do .NET Core x64 que podem ser desinstalados com essa ferramenta.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-144">Lists all x64 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

* **`--x86`**

  <span data-ttu-id="e0f5f-145">Lista todos os SDKs e tempos de execução do .NET Core x86 que podem ser desinstalados com essa ferramenta.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-145">Lists all x86 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

## <a name="macos"></a>[<span data-ttu-id="e0f5f-146">macOS</span><span class="sxs-lookup"><span data-stu-id="e0f5f-146">macOS</span></span>](#tab/macos)

* **`--runtime`**

  <span data-ttu-id="e0f5f-147">Lista todos os tempos de execução do .NET Core que podem ser desinstalados com essa ferramenta.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-147">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="e0f5f-148">Lista todos os SDKs do .NET Core que podem ser desinstalados com essa ferramenta.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-148">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="e0f5f-149">Define o nível de detalhes.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-149">Sets the verbosity level.</span></span> <span data-ttu-id="e0f5f-150">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-150">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="e0f5f-151">O valor padrão é `normal`.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-151">The default value is `normal`.</span></span>
  
---

#### <a name="examples"></a><span data-ttu-id="e0f5f-152">Exemplos</span><span class="sxs-lookup"><span data-stu-id="e0f5f-152">Examples</span></span>

* <span data-ttu-id="e0f5f-153">Listar todos os SDKs e tempos de execução do .NET Core que podem ser removidos com esta ferramenta:</span><span class="sxs-lookup"><span data-stu-id="e0f5f-153">List all .NET Core SDKs and runtimes that can be removed with this tool:</span></span>

  ```console
  dotnet-core-uninstall list
  ```

* <span data-ttu-id="e0f5f-154">Listar todos os SDKs e tempos de execução do .NET Core x64:</span><span class="sxs-lookup"><span data-stu-id="e0f5f-154">List all x64 .NET Core SDKs and runtimes:</span></span>

  ```console
  dotnet-core-uninstall list --x64
  ```

* <span data-ttu-id="e0f5f-155">Listar todos os SDKs do .NET Core x86:</span><span class="sxs-lookup"><span data-stu-id="e0f5f-155">List all x86 .NET Core SDKs:</span></span>

  ```console
  dotnet-core-uninstall list --sdk --x86
  ```

### <a name="step-2---do-a-dry-run"></a><span data-ttu-id="e0f5f-156">Etapa 2 – fazer uma simulação</span><span class="sxs-lookup"><span data-stu-id="e0f5f-156">Step 2 - Do a dry run</span></span>

<span data-ttu-id="e0f5f-157">Os `dotnet-core-uninstall dry-run` comandos `dotnet-core-uninstall whatif` e exibem os SDKs e os tempos de execução do .NET Core que serão removidos com base nas opções fornecidas sem executar a desinstalação.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-157">The `dotnet-core-uninstall dry-run` and `dotnet-core-uninstall whatif` commands display the .NET Core SDKs and runtimes that will be removed based on the options provided without performing the uninstall.</span></span> <span data-ttu-id="e0f5f-158">Esses comandos são sinônimos.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-158">These commands are synonyms.</span></span>

<span data-ttu-id="e0f5f-159">**dotnet-Core-Uninstall secat-Run e dotnet-Core-Uninstall WhatIf**</span><span class="sxs-lookup"><span data-stu-id="e0f5f-159">**dotnet-core-uninstall dry-run and dotnet-core-uninstall whatif**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="e0f5f-160">Sinopse</span><span class="sxs-lookup"><span data-stu-id="e0f5f-160">Synopsis</span></span>

```console
dotnet-core-uninstall dry-run [options] [<VERSION>...]

dotnet-core-uninstall whatif [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="e0f5f-161">Argumentos</span><span class="sxs-lookup"><span data-stu-id="e0f5f-161">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="e0f5f-162">A versão especificada a ser desinstalada.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-162">The specified version to uninstall.</span></span> <span data-ttu-id="e0f5f-163">Você pode listar várias versões uma após a outra, separadas por espaços.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-163">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="e0f5f-164">Também há suporte para arquivos de resposta.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-164">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="e0f5f-165">Os arquivos de resposta são uma alternativa para colocar todas as versões na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-165">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="e0f5f-166">Eles são arquivos de texto, normalmente com \*uma extensão. rsp, e cada versão é listada em uma linha separada.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-166">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="e0f5f-167">Para especificar um arquivo de resposta para `VERSION` o argumento, use \@ o caractere imediatamente seguido pelo nome do arquivo de resposta.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-167">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="e0f5f-168">Opções</span><span class="sxs-lookup"><span data-stu-id="e0f5f-168">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="e0f5f-169">Windows</span><span class="sxs-lookup"><span data-stu-id="e0f5f-169">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="e0f5f-170">Remove todos os SDKs e tempos de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-170">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="e0f5f-171">Remove somente os SDKs do .NET Core e os tempos de execução com uma versão menor do que a versão especificada.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-171">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="e0f5f-172">A versão especificada permanece instalada.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-172">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="e0f5f-173">Remove todos os SDKs e tempos de execução do .NET Core, exceto as versões especificadas.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-173">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="e0f5f-174">Remove SDKs e tempos de execução do .NET Core, exceto a versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-174">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="e0f5f-175">Remove os SDKs do .NET Core e os tempos de execução substituídos por patches mais altos.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-175">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="e0f5f-176">Essa opção protege global. JSON.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-176">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="e0f5f-177">Remove SDKs e tempos de execução do .NET Core marcados como visualizações.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-177">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="e0f5f-178">Remove os SDKs e os tempos de execução do .NET Core marcados como versões prévias, exceto a visualização mais alta.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-178">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="e0f5f-179">Remove somente ASP.NET Core tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-179">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="e0f5f-180">Remove somente os agrupamentos de hospedagem e de tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-180">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="e0f5f-181">Remove SDKs e tempos de execução do .NET Core que correspondem `major.minor` à versão especificada.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-181">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="e0f5f-182">Remove somente os tempos de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-182">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="e0f5f-183">Remove somente SDKs do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-183">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="e0f5f-184">Define o nível de detalhes.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-184">Sets the verbosity level.</span></span> <span data-ttu-id="e0f5f-185">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-185">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="e0f5f-186">O valor padrão é `normal`.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-186">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="e0f5f-187">Deve ser usado com `--sdk`, `--runtime`e `--aspnet-runtime` para remover SDKs ou tempos de execução do x64.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-187">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="e0f5f-188">Deve ser usado com `--sdk`, `--runtime`e `--aspnet-runtime` para remover SDKs ou tempos de execução do x86.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-188">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="e0f5f-189">**`--force`** Força a remoção de versões que podem ser usadas pelo Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-189">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="e0f5f-190">Observações:</span><span class="sxs-lookup"><span data-stu-id="e0f5f-190">Notes:</span></span>

1. <span data-ttu-id="e0f5f-191">Exatamente um de `--sdk`, `--runtime`, `--aspnet-runtime`e `--hosting-bundle` é necessário.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-191">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="e0f5f-192">`--all``--all-previews` `--all-previews-but-latest` `--major-minor` `[<VERSION>...]` ,,,,,,, e são exclusivos. `--all-below` `--all-but` `--all-but-latest` `--all-lower-patches`</span><span class="sxs-lookup"><span data-stu-id="e0f5f-192">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="e0f5f-193">Se `--x64` ou `--x86` não for especificado, tanto o x64 quanto o x86 serão removidos.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-193">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="e0f5f-194">macOS</span><span class="sxs-lookup"><span data-stu-id="e0f5f-194">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="e0f5f-195">Remove todos os SDKs e tempos de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-195">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="e0f5f-196">Remove os SDKs do .NET Core e os tempos de execução abaixo da versão especificada.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-196">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="e0f5f-197">A versão especificada permanecerá.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-197">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="e0f5f-198">Remove SDKs e tempos de execução do .NET Core, exceto as versões especificadas.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-198">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="e0f5f-199">Remove SDKs e tempos de execução do .NET Core, exceto a versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-199">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="e0f5f-200">Remove os SDKs do .NET Core e os tempos de execução substituídos por patches mais altos.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-200">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="e0f5f-201">Essa opção protege global. JSON.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-201">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="e0f5f-202">Remove SDKs e tempos de execução do .NET Core marcados como visualizações.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-202">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="e0f5f-203">Remove os SDKs e os tempos de execução do .NET Core marcados como versões prévias, exceto a visualização mais alta.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-203">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="e0f5f-204">Remove SDKs e tempos de execução do .NET Core que correspondem `major.minor` à versão especificada.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-204">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="e0f5f-205">Remove somente os tempos de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-205">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="e0f5f-206">Remove somente SDKs do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-206">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="e0f5f-207">Define o nível de detalhes.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-207">Sets the verbosity level.</span></span> <span data-ttu-id="e0f5f-208">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-208">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="e0f5f-209">O valor padrão é `normal`.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-209">The default value is `normal`.</span></span>
  
* <span data-ttu-id="e0f5f-210">**`--force`** Força a remoção de versões que podem ser usadas pelo Visual Studio ou SDKs.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-210">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="e0f5f-211">Observações:</span><span class="sxs-lookup"><span data-stu-id="e0f5f-211">Notes:</span></span>

1. <span data-ttu-id="e0f5f-212">Exatamente um de `--sdk` e `--runtime` é necessário.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-212">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="e0f5f-213">`--all``--all-previews` `--all-previews-but-latest` `--major-minor` `[<VERSION>...]` ,,,,,,, e são exclusivos. `--all-below` `--all-but` `--all-but-latest` `--all-lower-patches`</span><span class="sxs-lookup"><span data-stu-id="e0f5f-213">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="e0f5f-214">Exemplos</span><span class="sxs-lookup"><span data-stu-id="e0f5f-214">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="e0f5f-215">Por padrão, os SDKs do .NET Core e os tempos de execução que podem ser exigidos pelo Visual Studio ou outros `dotnet-core-uninstall dry-run` SDKs não são incluídos na saída.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-215">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are not included in `dotnet-core-uninstall dry-run` output.</span></span> <span data-ttu-id="e0f5f-216">Nos exemplos a seguir, alguns dos SDKs e tempos de execução especificados podem não ser incluídos na saída, dependendo do estado do computador.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-216">In the following examples, some of the specified SDKs and runtimes may not be included in the output, depending on the state of the machine.</span></span> <span data-ttu-id="e0f5f-217">Para incluir todos os SDKs e tempos de execução, liste-os explicitamente como `--force` argumentos ou use a opção.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-217">To include all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="e0f5f-218">Simulação da execução da remoção de todos os tempos de execução do .NET Core que foram substituídos por patches mais altos:</span><span class="sxs-lookup"><span data-stu-id="e0f5f-218">Dry run of removing all .NET Core runtimes that have been superseded by higher patches:</span></span>

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* <span data-ttu-id="e0f5f-219">Simulação da execução da remoção de todos os SDKs do .NET `2.2.301`Core abaixo da versão:</span><span class="sxs-lookup"><span data-stu-id="e0f5f-219">Dry run of removing all .NET Core SDKs below the version `2.2.301`:</span></span>

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-core-sdks-and-runtimes"></a><span data-ttu-id="e0f5f-220">Etapa 3-desinstalar SDKs e tempos de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="e0f5f-220">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>

<span data-ttu-id="e0f5f-221">`dotnet-core-uninstall remove`desinstala SDKs e tempos de execução do .NET Core que são especificados por uma coleção de opções.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-221">`dotnet-core-uninstall remove` uninstalls .NET Core SDKs and Runtimes that are specified by a collection of options.</span></span> <span data-ttu-id="e0f5f-222">A ferramenta não pode ser usada para desinstalar SDKs e tempos de execução com a versão 5,0 ou superior.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-222">The tool can't be used to uninstall SDKs and Runtimes with version 5.0 or above.</span></span>

<span data-ttu-id="e0f5f-223">Como essa ferramenta tem um comportamento destrutivo, é **altamente** recomendável que você execute uma simulação antes de executar o comando remover.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-223">Since this tool has a destructive behavior, it's **highly** recommended that you do a dry run before running the remove command.</span></span> <span data-ttu-id="e0f5f-224">A execução seca mostrará quais SDKs e tempos de execução do .NET Core serão removidos quando você usar o `remove` comando.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-224">The dry run will show you what .NET Core SDKs and runtimes will be removed when you use the `remove` command.</span></span> <span data-ttu-id="e0f5f-225">Consulte devo [remover uma versão?](../install/remove-runtime-sdk-versions.md#should-i-remove-a-version) para saber quais SDKs e tempos de execução são seguros de remover.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-225">Refer to [Should I remove a version?](../install/remove-runtime-sdk-versions.md#should-i-remove-a-version) to learn which SDKs and runtimes are safe to remove.</span></span>

> [!CAUTION]
> <span data-ttu-id="e0f5f-226">Tenha em mente as seguintes advertências:</span><span class="sxs-lookup"><span data-stu-id="e0f5f-226">Keep in mind the following caveats:</span></span>
>
>- <span data-ttu-id="e0f5f-227">Essa ferramenta pode desinstalar versões do SDK do .NET Core que são exigidas pelos `global.json` arquivos em seu computador.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-227">This tool can uninstall versions of the .NET Core SDK that are required by `global.json` files on your machine.</span></span> <span data-ttu-id="e0f5f-228">Você pode reinstalar SDKs do .NET Core na página [baixar o .NET Core](https://dotnet.microsoft.com/download/dotnet-core) .</span><span class="sxs-lookup"><span data-stu-id="e0f5f-228">You can reinstall .NET Core SDKs from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="e0f5f-229">Essa ferramenta pode desinstalar versões do tempo de execução do .NET Core que são exigidas por aplicativos dependentes da estrutura em seu computador.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-229">This tool can uninstall versions of the .NET Core runtime that are required by framework dependent applications on your machine.</span></span> <span data-ttu-id="e0f5f-230">Você pode reinstalar os tempos de execução do .NET Core na página [baixar o .NET Core](https://dotnet.microsoft.com/download/dotnet-core) .</span><span class="sxs-lookup"><span data-stu-id="e0f5f-230">You can reinstall .NET Core runtimes from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="e0f5f-231">Essa ferramenta pode desinstalar versões do SDK do .NET Core e do tempo de execução dos quais o Visual Studio depende.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-231">This tool can uninstall versions of the .NET Core SDK and runtime that Visual Studio relies on.</span></span> <span data-ttu-id="e0f5f-232">Se você interromper a instalação do Visual Studio, execute "reparar" no instalador do Visual Studio para voltar a um estado de funcionamento.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-232">If you break your Visual Studio installation, run "Repair" in the Visual Studio installer to get back to a working state.</span></span>

<span data-ttu-id="e0f5f-233">Por padrão, todos os comandos mantêm os SDKs do .NET Core e os tempos de execução que podem ser exigidos pelo Visual Studio ou outros SDKs.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-233">By default, all commands keep the .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs.</span></span> <span data-ttu-id="e0f5f-234">Esses SDKs e tempos de execução podem ser desinstalados, listando-os explicitamente como argumentos ou `--force` usando a opção.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-234">These SDKs and runtimes can be uninstalled by listing them explicitly as arguments or by using the `--force` option.</span></span>

<span data-ttu-id="e0f5f-235">A ferramenta requer elevação para desinstalar SDKs e tempos de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-235">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="e0f5f-236">Execute a ferramenta em um prompt de comando de administrador no Windows `sudo` e com no MacOS.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-236">Run the tool in an Administrator command prompt on Windows and with `sudo` on macOS.</span></span> <span data-ttu-id="e0f5f-237">Os `dry-run` comandos `whatif` e não exigem elevação.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-237">The `dry-run` and `whatif` commands don't require elevation.</span></span>

<span data-ttu-id="e0f5f-238">**dotnet-núcleo-desinstalar remover**</span><span class="sxs-lookup"><span data-stu-id="e0f5f-238">**dotnet-core-uninstall remove**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="e0f5f-239">Sinopse</span><span class="sxs-lookup"><span data-stu-id="e0f5f-239">Synopsis</span></span>

```console
dotnet-core-uninstall remove [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="e0f5f-240">Argumentos</span><span class="sxs-lookup"><span data-stu-id="e0f5f-240">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="e0f5f-241">A versão especificada a ser desinstalada.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-241">The specified version to uninstall.</span></span> <span data-ttu-id="e0f5f-242">Você pode listar várias versões uma após a outra, separadas por espaços.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-242">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="e0f5f-243">Também há suporte para arquivos de resposta.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-243">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="e0f5f-244">Os arquivos de resposta são uma alternativa para colocar todas as versões na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-244">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="e0f5f-245">Eles são arquivos de texto, normalmente com \*uma extensão. rsp, e cada versão é listada em uma linha separada.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-245">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="e0f5f-246">Para especificar um arquivo de resposta para `VERSION` o argumento, use \@ o caractere imediatamente seguido pelo nome do arquivo de resposta.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-246">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="e0f5f-247">Opções</span><span class="sxs-lookup"><span data-stu-id="e0f5f-247">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="e0f5f-248">Windows</span><span class="sxs-lookup"><span data-stu-id="e0f5f-248">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="e0f5f-249">Remove todos os SDKs e tempos de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-249">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="e0f5f-250">Remove somente os SDKs do .NET Core e os tempos de execução com uma versão menor do que a versão especificada.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-250">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="e0f5f-251">A versão especificada permanece instalada.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-251">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="e0f5f-252">Remove todos os SDKs e tempos de execução do .NET Core, exceto as versões especificadas.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-252">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="e0f5f-253">Remove SDKs e tempos de execução do .NET Core, exceto a versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-253">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="e0f5f-254">Remove os SDKs do .NET Core e os tempos de execução substituídos por patches mais altos.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-254">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="e0f5f-255">Essa opção protege global. JSON.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-255">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="e0f5f-256">Remove SDKs e tempos de execução do .NET Core marcados como visualizações.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-256">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="e0f5f-257">Remove os SDKs e os tempos de execução do .NET Core marcados como versões prévias, exceto a visualização mais alta.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-257">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="e0f5f-258">Remove somente ASP.NET Core tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-258">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="e0f5f-259">Remove somente os agrupamentos de hospedagem e de tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-259">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="e0f5f-260">Remove SDKs e tempos de execução do .NET Core que correspondem `major.minor` à versão especificada.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-260">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="e0f5f-261">Remove somente os tempos de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-261">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="e0f5f-262">Remove somente SDKs do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-262">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="e0f5f-263">Define o nível de detalhes.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-263">Sets the verbosity level.</span></span> <span data-ttu-id="e0f5f-264">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-264">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="e0f5f-265">O valor padrão é `normal`.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-265">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="e0f5f-266">Deve ser usado com `--sdk`, `--runtime`e `--aspnet-runtime` para remover SDKs ou tempos de execução do x64.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-266">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="e0f5f-267">Deve ser usado com `--sdk`, `--runtime`e `--aspnet-runtime` para remover SDKs ou tempos de execução do x86.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-267">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="e0f5f-268">**`-y, --yes`** Executa o comando sem a necessidade de uma confirmação Sim ou não.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-268">**`-y, --yes`** Executes the command without requiring a yes or no confirmation.</span></span>

* <span data-ttu-id="e0f5f-269">**`--force`** Força a remoção de versões que podem ser usadas pelo Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-269">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="e0f5f-270">Observações:</span><span class="sxs-lookup"><span data-stu-id="e0f5f-270">Notes:</span></span>

1. <span data-ttu-id="e0f5f-271">Exatamente um de `--sdk`, `--runtime`, `--aspnet-runtime`e `--hosting-bundle` é necessário.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-271">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="e0f5f-272">`--all``--all-previews` `--all-previews-but-latest` `--major-minor` `[<VERSION>...]` ,,,,,,, e são exclusivos. `--all-below` `--all-but` `--all-but-latest` `--all-lower-patches`</span><span class="sxs-lookup"><span data-stu-id="e0f5f-272">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="e0f5f-273">Se `--x64` ou `--x86` não for especificado, tanto o x64 quanto o x86 serão removidos.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-273">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="e0f5f-274">macOS</span><span class="sxs-lookup"><span data-stu-id="e0f5f-274">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="e0f5f-275">Remove todos os SDKs e tempos de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-275">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="e0f5f-276">Remove os SDKs do .NET Core e os tempos de execução abaixo da versão especificada.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-276">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="e0f5f-277">A versão especificada permanecerá.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-277">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="e0f5f-278">Remove SDKs e tempos de execução do .NET Core, exceto as versões especificadas.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-278">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="e0f5f-279">Remove SDKs e tempos de execução do .NET Core, exceto a versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-279">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="e0f5f-280">Remove os SDKs do .NET Core e os tempos de execução substituídos por patches mais altos.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-280">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="e0f5f-281">Essa opção protege global. JSON.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-281">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="e0f5f-282">Remove SDKs e tempos de execução do .NET Core marcados como visualizações.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-282">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="e0f5f-283">Remove os SDKs e os tempos de execução do .NET Core marcados como versões prévias, exceto a visualização mais alta.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-283">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="e0f5f-284">Remove SDKs e tempos de execução do .NET Core que correspondem `major.minor` à versão especificada.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-284">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="e0f5f-285">Remove somente os tempos de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-285">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="e0f5f-286">Remove somente SDKs do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-286">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="e0f5f-287">Define o nível de detalhes.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-287">Sets the verbosity level.</span></span> <span data-ttu-id="e0f5f-288">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-288">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="e0f5f-289">O valor padrão é `normal`.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-289">The default value is `normal`.</span></span>

* <span data-ttu-id="e0f5f-290">**`-y, --yes`** Executa o comando sem a necessidade de confirmação de Y/N.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-290">**`-y, --yes`** Executes the command without requiring Y/N confirmation.</span></span>
  
* <span data-ttu-id="e0f5f-291">**`--force`** Força a remoção de versões que podem ser usadas pelo Visual Studio ou SDKs.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-291">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="e0f5f-292">Observações:</span><span class="sxs-lookup"><span data-stu-id="e0f5f-292">Notes:</span></span>

1. <span data-ttu-id="e0f5f-293">Exatamente um de `--sdk` e `--runtime` é necessário.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-293">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="e0f5f-294">`--all``--all-previews` `--all-previews-but-latest` `--major-minor` `[<VERSION>...]` ,,,,,,, e são exclusivos. `--all-below` `--all-but` `--all-but-latest` `--all-lower-patches`</span><span class="sxs-lookup"><span data-stu-id="e0f5f-294">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="e0f5f-295">Exemplos</span><span class="sxs-lookup"><span data-stu-id="e0f5f-295">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="e0f5f-296">Por padrão, os SDKs do .NET Core e os tempos de execução que podem ser exigidos pelo Visual Studio ou outros SDKs são mantidos.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-296">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are kept.</span></span> <span data-ttu-id="e0f5f-297">Nos exemplos a seguir, alguns dos SDKs e tempos de execução especificados podem permanecer, dependendo do estado do computador.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-297">In the following examples, some of the specified SDKs and runtimes may remain, depending on the state of the machine.</span></span> <span data-ttu-id="e0f5f-298">Para remover todos os SDKs e tempos de execução, liste-os explicitamente como `--force` argumentos ou use a opção.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-298">To remove all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="e0f5f-299">Remova todos os tempos de execução do .NET Core `3.0.0-preview6-27804-01` , exceto a versão, sem exigir confirmação de Y/N:</span><span class="sxs-lookup"><span data-stu-id="e0f5f-299">Remove all .NET Core runtimes except the version `3.0.0-preview6-27804-01` without requiring Y/N confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --all-but 3.0.0-preview6-27804-01 --runtime --yes
  ```

* <span data-ttu-id="e0f5f-300">Remova todos os SDKs do .NET Core 1,1 sem exigir confirmação de s/n:</span><span class="sxs-lookup"><span data-stu-id="e0f5f-300">Remove all .NET Core 1.1 SDKs without requiring Y/n confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --sdk --major-minor 1.1 -y
  ```

* <span data-ttu-id="e0f5f-301">Remova o SDK do .NET Core 1.1.11 sem saída de console:</span><span class="sxs-lookup"><span data-stu-id="e0f5f-301">Remove the .NET Core 1.1.11 SDK with no console output:</span></span>

  ```console
  dotnet-core-uninstall remove 1.1.11 --sdk --yes --verbosity q
  ```

* <span data-ttu-id="e0f5f-302">Remova todos os SDKs do .NET Core que podem ser removidos com segurança por essa ferramenta:</span><span class="sxs-lookup"><span data-stu-id="e0f5f-302">Remove all .NET Core SDKs that can safely be removed by this tool:</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk
  ```

* <span data-ttu-id="e0f5f-303">Remova todos os SDKs do .NET Core que podem ser removidos por essa ferramenta, incluindo os SDKs que podem ser exigidos pelo Visual Studio (não recomendado):</span><span class="sxs-lookup"><span data-stu-id="e0f5f-303">Remove all .NET Core SDKs that can be removed by this tool, including those SDKs that may be required by Visual Studio (not recommended):</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk --force
  ```

* <span data-ttu-id="e0f5f-304">Remover todos os SDKs do .NET Core especificados no arquivo de resposta`versions.rsp`</span><span class="sxs-lookup"><span data-stu-id="e0f5f-304">Remove all .NET Core SDKs that are specified in the response file `versions.rsp`</span></span>

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  <span data-ttu-id="e0f5f-305">O conteúdo de *Versions. rsp* é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e0f5f-305">The content of *versions.rsp* is as follows:</span></span>
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a><span data-ttu-id="e0f5f-306">Etapa 4-excluir a pasta de fallback do NuGet (opcional)</span><span class="sxs-lookup"><span data-stu-id="e0f5f-306">Step 4 - Delete the NuGet fallback folder (optional)</span></span>

<span data-ttu-id="e0f5f-307">Em alguns casos, você não precisa mais do `NuGetFallbackFolder` e pode desejar excluí-lo.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-307">In some cases, you no longer need the `NuGetFallbackFolder` and may wish to delete it.</span></span> <span data-ttu-id="e0f5f-308">Para obter mais informações sobre como excluir essa pasta, consulte [remover o NuGetFallbackFolder](../install/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span><span class="sxs-lookup"><span data-stu-id="e0f5f-308">For more information about deleting this folder, see [Remove the NuGetFallbackFolder](../install/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span></span>

## <a name="uninstall-the-tool"></a><span data-ttu-id="e0f5f-309">Desinstalar a ferramenta</span><span class="sxs-lookup"><span data-stu-id="e0f5f-309">Uninstall the tool</span></span>

## <a name="windows"></a>[<span data-ttu-id="e0f5f-310">Windows</span><span class="sxs-lookup"><span data-stu-id="e0f5f-310">Windows</span></span>](#tab/windows)

1. <span data-ttu-id="e0f5f-311">Abra **Adicionar ou remover programas**.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-311">Open **Add or Remove Programs**.</span></span>
2. <span data-ttu-id="e0f5f-312">Pesquise `Microsoft .NET Core SDK Uninstall Tool`.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-312">Search for `Microsoft .NET Core SDK Uninstall Tool`.</span></span>
3. <span data-ttu-id="e0f5f-313">Selecionar **Desinstalar**.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-313">Select **Uninstall**.</span></span>

## <a name="macos"></a>[<span data-ttu-id="e0f5f-314">macOS</span><span class="sxs-lookup"><span data-stu-id="e0f5f-314">macOS</span></span>](#tab/macos)

<span data-ttu-id="e0f5f-315">Exclua o arquivo *dotnet-Core-Uninstall. tar. gz* baixado do diretório em que ele foi instalado.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-315">Delete the downloaded *dotnet-core-uninstall.tar.gz* file from the directory where it was installed.</span></span> <span data-ttu-id="e0f5f-316">Se você descompactou o conteúdo desse arquivo em outro diretório, certifique-se de excluir esse conteúdo também.</span><span class="sxs-lookup"><span data-stu-id="e0f5f-316">If you unzipped the contents of this file into another directory, be sure to delete that content as well.</span></span>

---
