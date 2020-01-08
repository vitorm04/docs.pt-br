---
title: Ferramenta de desinstalação
description: Uma visão geral da ferramenta de desinstalação do .NET Core, uma ferramenta guiada que permite a limpeza controlada de SDKs e tempos de execução do .NET Core.
author: sfoslund
ms.date: 12/17/2019
ms.openlocfilehash: 5a1a419d5ad09643a7063cc03ec727c547268cc6
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75443543"
---
# <a name="net-core-uninstall-tool"></a><span data-ttu-id="99145-103">Ferramenta de desinstalação do .NET Core</span><span class="sxs-lookup"><span data-stu-id="99145-103">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="99145-104">A [ferramenta de desinstalação do .NET Core](https://github.com/dotnet/cli-lab/releases) (`dotnet-core-uninstall`) permite remover SDKs do .NET Core e tempos de execução de um sistema.</span><span class="sxs-lookup"><span data-stu-id="99145-104">The [.NET Core Uninstall Tool](https://github.com/dotnet/cli-lab/releases) (`dotnet-core-uninstall`) lets you remove .NET Core SDKs and Runtimes from a system.</span></span> <span data-ttu-id="99145-105">Uma coleção de opções está disponível para especificar quais versões você deseja desinstalar.</span><span class="sxs-lookup"><span data-stu-id="99145-105">A collection of options is available to specify which versions you want to uninstall.</span></span>

<span data-ttu-id="99145-106">A ferramenta dá suporte ao Windows e ao macOS.</span><span class="sxs-lookup"><span data-stu-id="99145-106">The tool supports Windows and macOS.</span></span> <span data-ttu-id="99145-107">O Linux não tem suporte no momento.</span><span class="sxs-lookup"><span data-stu-id="99145-107">Linux is currently not supported.</span></span>

<span data-ttu-id="99145-108">No Windows, a ferramenta só pode desinstalar SDKs e tempos de execução que foram instalados usando um dos seguintes instaladores:</span><span class="sxs-lookup"><span data-stu-id="99145-108">On Windows, the tool can only uninstall SDKs and Runtimes that were installed using one of the following installers:</span></span>

- <span data-ttu-id="99145-109">O SDK do .NET Core e o instalador de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="99145-109">The .NET Core SDK and runtime installer.</span></span>
- <span data-ttu-id="99145-110">O instalador do Visual Studio em versões anteriores ao Visual Studio 2019 versão 16,3.</span><span class="sxs-lookup"><span data-stu-id="99145-110">The Visual Studio installer in versions earlier than Visual Studio 2019 version 16.3.</span></span>

<span data-ttu-id="99145-111">No macOS, a ferramenta só pode desinstalar SDKs e tempos de execução localizados na pasta */usr/local/share/dotnet*</span><span class="sxs-lookup"><span data-stu-id="99145-111">On macOS, the tool can only uninstall SDKs and runtimes located in the */usr/local/share/dotnet* folder.</span></span>

<span data-ttu-id="99145-112">Devido a essas limitações, a ferramenta pode não ser capaz de desinstalar todos os SDKs do .NET Core e os tempos de execução em seu computador.</span><span class="sxs-lookup"><span data-stu-id="99145-112">Because of these limitations, the tool may not be able to uninstall all of the .NET Core SDKs and runtimes on your machine.</span></span> <span data-ttu-id="99145-113">Você pode usar o comando `dotnet --info` para localizar todos os SDKs do .NET Core e os tempos de execução instalados, incluindo os SDKs e os tempos de execução que essa ferramenta não pode remover.</span><span class="sxs-lookup"><span data-stu-id="99145-113">You can use the `dotnet --info` command to find all of the .NET Core SDKs and runtimes installed, including those SDKs and runtimes that this tool can't remove.</span></span> <span data-ttu-id="99145-114">O comando `dotnet-core-uninstall list` exibe quais SDKs podem ser desinstalados com a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="99145-114">The `dotnet-core-uninstall list` command displays which SDKs can be uninstalled with the tool.</span></span>

## <a name="install-the-tool"></a><span data-ttu-id="99145-115">Instalar a ferramenta</span><span class="sxs-lookup"><span data-stu-id="99145-115">Install the tool</span></span>

<span data-ttu-id="99145-116">Você pode baixar a ferramenta de desinstalação do .NET Core no repositório do GitHub [dotnet/CLI-Lab](https://github.com/dotnet/cli-lab/releases) .</span><span class="sxs-lookup"><span data-stu-id="99145-116">You can download the .NET Core Uninstall Tool from the [dotnet/cli-lab](https://github.com/dotnet/cli-lab/releases) GitHub repository.</span></span>

> [!NOTE]
> <span data-ttu-id="99145-117">A ferramenta requer elevação para desinstalar SDKs e tempos de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="99145-117">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="99145-118">Portanto, ele deve ser instalado em um diretório protegido contra gravação, como *c:\Arquivos de programas* no Windows ou */usr/local/bin* no MacOS.</span><span class="sxs-lookup"><span data-stu-id="99145-118">Therefore, it should be installed in a write-protected directory such as *C:\Program Files* on Windows or */usr/local/bin* on macOS.</span></span> <span data-ttu-id="99145-119">Consulte também [acesso elevado para comandos dotnet](../tools/elevated-access.md).</span><span class="sxs-lookup"><span data-stu-id="99145-119">See also [Elevated access for dotnet commands](../tools/elevated-access.md).</span></span> <span data-ttu-id="99145-120">As instruções de instalação detalhadas estão disponíveis na [página versões do GitHub](https://github.com/dotnet/cli-lab/releases).</span><span class="sxs-lookup"><span data-stu-id="99145-120">Detailed installation instructions are available on the [GitHub Releases page](https://github.com/dotnet/cli-lab/releases).</span></span>

## <a name="run-the-tool"></a><span data-ttu-id="99145-121">Executar a ferramenta</span><span class="sxs-lookup"><span data-stu-id="99145-121">Run the tool</span></span>

<span data-ttu-id="99145-122">As etapas a seguir mostram a abordagem recomendada para executar a ferramenta de desinstalação:</span><span class="sxs-lookup"><span data-stu-id="99145-122">The following steps show the recommended approach for running the uninstall tool:</span></span>

- [<span data-ttu-id="99145-123">Etapa 1-exibir os SDKs e os tempos de execução do .NET Core instalados</span><span class="sxs-lookup"><span data-stu-id="99145-123">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>](#step-1---display-installed-net-core-sdks-and-runtimes)
- [<span data-ttu-id="99145-124">Etapa 2 – fazer uma simulação</span><span class="sxs-lookup"><span data-stu-id="99145-124">Step 2 - Do a dry run</span></span>](#step-2---do-a-dry-run)
- [<span data-ttu-id="99145-125">Etapa 3-desinstalar SDKs e tempos de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="99145-125">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>](#step-3---uninstall-net-core-sdks-and-runtimes)
- [<span data-ttu-id="99145-126">Etapa 4-excluir a pasta de fallback do NuGet (opcional)</span><span class="sxs-lookup"><span data-stu-id="99145-126">Step 4 - Delete the NuGet fallback folder (optional)</span></span>](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-core-sdks-and-runtimes"></a><span data-ttu-id="99145-127">Etapa 1-exibir os SDKs e os tempos de execução do .NET Core instalados</span><span class="sxs-lookup"><span data-stu-id="99145-127">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>

<span data-ttu-id="99145-128">O comando `dotnet-core-uninstall list` lista os SDKs e os tempos de execução do .NET Core instalados que podem ser removidos com essa ferramenta.</span><span class="sxs-lookup"><span data-stu-id="99145-128">The `dotnet-core-uninstall list` command lists the installed .NET Core SDKs and runtimes that can be removed with this tool.</span></span> <span data-ttu-id="99145-129">Alguns SDKs e tempos de execução podem ser exigidos pelo Visual Studio e são exibidos com uma observação de por que não é recomendável desinstalá-los.</span><span class="sxs-lookup"><span data-stu-id="99145-129">Some SDKs and runtimes may be required by Visual Studio and they're displayed with a note of why it isn't recommended to uninstall them.</span></span>

<span data-ttu-id="99145-130">**dotnet-núcleo-desinstalação da lista**</span><span class="sxs-lookup"><span data-stu-id="99145-130">**dotnet-core-uninstall list**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="99145-131">Sinopse</span><span class="sxs-lookup"><span data-stu-id="99145-131">Synopsis</span></span>

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a><span data-ttu-id="99145-132">Opções</span><span class="sxs-lookup"><span data-stu-id="99145-132">Options</span></span>

## <a name="windowstabwindows"></a>[<span data-ttu-id="99145-133">Windows</span><span class="sxs-lookup"><span data-stu-id="99145-133">Windows</span></span>](#tab/windows)

* **`--aspnet-runtime`**

  <span data-ttu-id="99145-134">Lista todos os tempos de execução de ASP.NET Core que podem ser desinstalados com essa ferramenta.</span><span class="sxs-lookup"><span data-stu-id="99145-134">Lists all the ASP.NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="99145-135">Lista todos os pacotes de hospedagem e de tempo de execução do .NET Core que podem ser desinstalados com essa ferramenta.</span><span class="sxs-lookup"><span data-stu-id="99145-135">Lists all the .NET Core runtime and hosting bundles that can be uninstalled with this tool.</span></span>

* **`--runtime`**

  <span data-ttu-id="99145-136">Lista todos os tempos de execução do .NET Core que podem ser desinstalados com essa ferramenta.</span><span class="sxs-lookup"><span data-stu-id="99145-136">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="99145-137">Lista todos os SDKs do .NET Core que podem ser desinstalados com essa ferramenta.</span><span class="sxs-lookup"><span data-stu-id="99145-137">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="99145-138">Define o nível de detalhes.</span><span class="sxs-lookup"><span data-stu-id="99145-138">Sets the verbosity level.</span></span> <span data-ttu-id="99145-139">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="99145-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="99145-140">O valor padrão é `normal`.</span><span class="sxs-lookup"><span data-stu-id="99145-140">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="99145-141">Lista todos os SDKs e tempos de execução do .NET Core x64 que podem ser desinstalados com essa ferramenta.</span><span class="sxs-lookup"><span data-stu-id="99145-141">Lists all x64 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

* **`--x86`**

  <span data-ttu-id="99145-142">Lista todos os SDKs e tempos de execução do .NET Core x86 que podem ser desinstalados com essa ferramenta.</span><span class="sxs-lookup"><span data-stu-id="99145-142">Lists all x86 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

## <a name="macostabmacos"></a>[<span data-ttu-id="99145-143">macOS</span><span class="sxs-lookup"><span data-stu-id="99145-143">macOS</span></span>](#tab/macos)

* **`--runtime`**

  <span data-ttu-id="99145-144">Lista todos os tempos de execução do .NET Core que podem ser desinstalados com essa ferramenta.</span><span class="sxs-lookup"><span data-stu-id="99145-144">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="99145-145">Lista todos os SDKs do .NET Core que podem ser desinstalados com essa ferramenta.</span><span class="sxs-lookup"><span data-stu-id="99145-145">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="99145-146">Define o nível de detalhes.</span><span class="sxs-lookup"><span data-stu-id="99145-146">Sets the verbosity level.</span></span> <span data-ttu-id="99145-147">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="99145-147">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="99145-148">O valor padrão é `normal`.</span><span class="sxs-lookup"><span data-stu-id="99145-148">The default value is `normal`.</span></span>
  
---

#### <a name="examples"></a><span data-ttu-id="99145-149">Exemplos</span><span class="sxs-lookup"><span data-stu-id="99145-149">Examples</span></span>

* <span data-ttu-id="99145-150">Listar todos os SDKs e tempos de execução do .NET Core que podem ser removidos com esta ferramenta:</span><span class="sxs-lookup"><span data-stu-id="99145-150">List all .NET Core SDKs and runtimes that can be removed with this tool:</span></span>

  ```console
  dotnet-core-uninstall list
  ```

* <span data-ttu-id="99145-151">Listar todos os SDKs e tempos de execução do .NET Core x64:</span><span class="sxs-lookup"><span data-stu-id="99145-151">List all x64 .NET Core SDKs and runtimes:</span></span>

  ```console
  dotnet-core-uninstall list --x64
  ```

* <span data-ttu-id="99145-152">Listar todos os SDKs do .NET Core x86:</span><span class="sxs-lookup"><span data-stu-id="99145-152">List all x86 .NET Core SDKs:</span></span>

  ```console
  dotnet-core-uninstall list --sdk --x86
  ```

### <a name="step-2---do-a-dry-run"></a><span data-ttu-id="99145-153">Etapa 2 – fazer uma simulação</span><span class="sxs-lookup"><span data-stu-id="99145-153">Step 2 - Do a dry run</span></span>

<span data-ttu-id="99145-154">Os comandos `dotnet-core-uninstall dry-run` e `dotnet-core-uninstall whatif` exibem os SDKs e os tempos de execução do .NET Core que serão removidos com base nas opções fornecidas sem executar a desinstalação.</span><span class="sxs-lookup"><span data-stu-id="99145-154">The `dotnet-core-uninstall dry-run` and `dotnet-core-uninstall whatif` commands display the .NET Core SDKs and runtimes that will be removed based on the options provided without performing the uninstall.</span></span> <span data-ttu-id="99145-155">Esses comandos são sinônimos.</span><span class="sxs-lookup"><span data-stu-id="99145-155">These commands are synonyms.</span></span>

<span data-ttu-id="99145-156">**dotnet-Core-Uninstall secat-Run e dotnet-Core-Uninstall WhatIf**</span><span class="sxs-lookup"><span data-stu-id="99145-156">**dotnet-core-uninstall dry-run and dotnet-core-uninstall whatif**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="99145-157">Sinopse</span><span class="sxs-lookup"><span data-stu-id="99145-157">Synopsis</span></span>

```console
dotnet-core-uninstall dry-run [options] [<VERSION>...]

dotnet-core-uninstall whatif [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="99145-158">Arguments</span><span class="sxs-lookup"><span data-stu-id="99145-158">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="99145-159">A versão especificada a ser desinstalada.</span><span class="sxs-lookup"><span data-stu-id="99145-159">The specified version to uninstall.</span></span> <span data-ttu-id="99145-160">Você pode listar várias versões uma após a outra, separadas por espaços.</span><span class="sxs-lookup"><span data-stu-id="99145-160">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="99145-161">Também há suporte para arquivos de resposta.</span><span class="sxs-lookup"><span data-stu-id="99145-161">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="99145-162">Os arquivos de resposta são uma alternativa para colocar todas as versões na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="99145-162">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="99145-163">São arquivos de texto, normalmente com uma extensão \*. rsp, e cada versão é listada em uma linha separada.</span><span class="sxs-lookup"><span data-stu-id="99145-163">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="99145-164">Para especificar um arquivo de resposta para o argumento `VERSION`, use o caractere \@ seguido imediatamente pelo nome do arquivo de resposta.</span><span class="sxs-lookup"><span data-stu-id="99145-164">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="99145-165">Opções</span><span class="sxs-lookup"><span data-stu-id="99145-165">Options</span></span>

## <a name="windowstabwindows"></a>[<span data-ttu-id="99145-166">Windows</span><span class="sxs-lookup"><span data-stu-id="99145-166">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="99145-167">Remove todos os SDKs e tempos de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="99145-167">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="99145-168">Remove somente os SDKs do .NET Core e os tempos de execução com uma versão menor do que a versão especificada.</span><span class="sxs-lookup"><span data-stu-id="99145-168">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="99145-169">A versão especificada permanece instalada.</span><span class="sxs-lookup"><span data-stu-id="99145-169">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="99145-170">Remove todos os SDKs e tempos de execução do .NET Core, exceto as versões especificadas.</span><span class="sxs-lookup"><span data-stu-id="99145-170">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="99145-171">Remove SDKs e tempos de execução do .NET Core, exceto a versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="99145-171">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="99145-172">Remove os SDKs do .NET Core e os tempos de execução substituídos por patches mais altos.</span><span class="sxs-lookup"><span data-stu-id="99145-172">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="99145-173">Essa opção protege global. JSON.</span><span class="sxs-lookup"><span data-stu-id="99145-173">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="99145-174">Remove SDKs e tempos de execução do .NET Core marcados como visualizações.</span><span class="sxs-lookup"><span data-stu-id="99145-174">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="99145-175">Remove os SDKs e os tempos de execução do .NET Core marcados como versões prévias, exceto a visualização mais alta.</span><span class="sxs-lookup"><span data-stu-id="99145-175">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="99145-176">Remove somente ASP.NET Core tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="99145-176">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="99145-177">Remove somente os agrupamentos de hospedagem e de tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="99145-177">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="99145-178">Remove SDKs e tempos de execução do .NET Core que correspondem à versão de `major.minor` especificada.</span><span class="sxs-lookup"><span data-stu-id="99145-178">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="99145-179">Remove somente os tempos de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="99145-179">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="99145-180">Remove somente SDKs do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="99145-180">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="99145-181">Define o nível de detalhes.</span><span class="sxs-lookup"><span data-stu-id="99145-181">Sets the verbosity level.</span></span> <span data-ttu-id="99145-182">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="99145-182">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="99145-183">O valor padrão é `normal`.</span><span class="sxs-lookup"><span data-stu-id="99145-183">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="99145-184">Deve ser usado com `--sdk`, `--runtime`e `--aspnet-runtime` para remover SDKs ou tempos de execução de x64.</span><span class="sxs-lookup"><span data-stu-id="99145-184">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="99145-185">Deve ser usado com `--sdk`, `--runtime`e `--aspnet-runtime` para remover SDKs ou tempos de execução do x86.</span><span class="sxs-lookup"><span data-stu-id="99145-185">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="99145-186">**`--force`** Força a remoção de versões que podem ser usadas pelo Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="99145-186">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="99145-187">Observações:</span><span class="sxs-lookup"><span data-stu-id="99145-187">Notes:</span></span>

1. <span data-ttu-id="99145-188">É necessário ter exatamente um dos `--sdk`, `--runtime`, `--aspnet-runtime`e `--hosting-bundle`.</span><span class="sxs-lookup"><span data-stu-id="99145-188">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="99145-189">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`e `[<VERSION>...]` são exclusivos.</span><span class="sxs-lookup"><span data-stu-id="99145-189">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="99145-190">Se `--x64` ou `--x86` não forem especificados, tanto o x64 quanto o x86 serão removidos.</span><span class="sxs-lookup"><span data-stu-id="99145-190">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macostabmacos"></a>[<span data-ttu-id="99145-191">macOS</span><span class="sxs-lookup"><span data-stu-id="99145-191">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="99145-192">Remove todos os SDKs e tempos de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="99145-192">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="99145-193">Remove os SDKs do .NET Core e os tempos de execução abaixo da versão especificada.</span><span class="sxs-lookup"><span data-stu-id="99145-193">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="99145-194">A versão especificada permanecerá.</span><span class="sxs-lookup"><span data-stu-id="99145-194">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="99145-195">Remove SDKs e tempos de execução do .NET Core, exceto as versões especificadas.</span><span class="sxs-lookup"><span data-stu-id="99145-195">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="99145-196">Remove SDKs e tempos de execução do .NET Core, exceto a versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="99145-196">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="99145-197">Remove os SDKs do .NET Core e os tempos de execução substituídos por patches mais altos.</span><span class="sxs-lookup"><span data-stu-id="99145-197">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="99145-198">Essa opção protege global. JSON.</span><span class="sxs-lookup"><span data-stu-id="99145-198">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="99145-199">Remove SDKs e tempos de execução do .NET Core marcados como visualizações.</span><span class="sxs-lookup"><span data-stu-id="99145-199">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="99145-200">Remove os SDKs e os tempos de execução do .NET Core marcados como versões prévias, exceto a visualização mais alta.</span><span class="sxs-lookup"><span data-stu-id="99145-200">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="99145-201">Remove SDKs e tempos de execução do .NET Core que correspondem à versão de `major.minor` especificada.</span><span class="sxs-lookup"><span data-stu-id="99145-201">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="99145-202">Remove somente os tempos de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="99145-202">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="99145-203">Remove somente SDKs do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="99145-203">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="99145-204">Define o nível de detalhes.</span><span class="sxs-lookup"><span data-stu-id="99145-204">Sets the verbosity level.</span></span> <span data-ttu-id="99145-205">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="99145-205">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="99145-206">O valor padrão é `normal`.</span><span class="sxs-lookup"><span data-stu-id="99145-206">The default value is `normal`.</span></span>
  
* <span data-ttu-id="99145-207">**`--force`** Força a remoção de versões que podem ser usadas pelo Visual Studio ou SDKs.</span><span class="sxs-lookup"><span data-stu-id="99145-207">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="99145-208">Observações:</span><span class="sxs-lookup"><span data-stu-id="99145-208">Notes:</span></span>

1. <span data-ttu-id="99145-209">É necessário ter exatamente um dos `--sdk` e `--runtime`.</span><span class="sxs-lookup"><span data-stu-id="99145-209">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="99145-210">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`e `[<VERSION>...]` são exclusivos.</span><span class="sxs-lookup"><span data-stu-id="99145-210">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="99145-211">Exemplos</span><span class="sxs-lookup"><span data-stu-id="99145-211">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="99145-212">Por padrão, os SDKs do .NET Core e os tempos de execução que podem ser exigidos pelo Visual Studio ou outros SDKs não são incluídos na saída `dotnet-core-uninstall dry-run`.</span><span class="sxs-lookup"><span data-stu-id="99145-212">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are not included in `dotnet-core-uninstall dry-run` output.</span></span> <span data-ttu-id="99145-213">Nos exemplos a seguir, alguns dos SDKs e tempos de execução especificados podem não ser incluídos na saída, dependendo do estado do computador.</span><span class="sxs-lookup"><span data-stu-id="99145-213">In the following examples, some of the specified SDKs and runtimes may not be included in the output, depending on the state of the machine.</span></span> <span data-ttu-id="99145-214">Para incluir todos os SDKs e tempos de execução, liste-os explicitamente como argumentos ou use a opção `--force`.</span><span class="sxs-lookup"><span data-stu-id="99145-214">To include all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="99145-215">Simulação da execução da remoção de todos os tempos de execução do .NET Core que foram substituídos por patches mais altos:</span><span class="sxs-lookup"><span data-stu-id="99145-215">Dry run of removing all .NET Core runtimes that have been superseded by higher patches:</span></span>

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* <span data-ttu-id="99145-216">Simulação da execução da remoção de todos os SDKs do .NET Core abaixo da versão `2.2.301`:</span><span class="sxs-lookup"><span data-stu-id="99145-216">Dry run of removing all .NET Core SDKs below the version `2.2.301`:</span></span>

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-core-sdks-and-runtimes"></a><span data-ttu-id="99145-217">Etapa 3-desinstalar SDKs e tempos de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="99145-217">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>

<span data-ttu-id="99145-218">`dotnet-core-uninstall remove` desinstala SDKs e tempos de execução do .NET Core que são especificados por uma coleção de opções.</span><span class="sxs-lookup"><span data-stu-id="99145-218">`dotnet-core-uninstall remove` uninstalls .NET Core SDKs and Runtimes that are specified by a collection of options.</span></span> <span data-ttu-id="99145-219">A ferramenta não pode ser usada para desinstalar SDKs e tempos de execução com a versão 5,0 ou superior.</span><span class="sxs-lookup"><span data-stu-id="99145-219">The tool can't be used to uninstall SDKs and Runtimes with version 5.0 or above.</span></span>

<span data-ttu-id="99145-220">Como essa ferramenta tem um comportamento destrutivo, é **altamente** recomendável que você execute uma simulação antes de executar o comando remover.</span><span class="sxs-lookup"><span data-stu-id="99145-220">Since this tool has a destructive behavior, it's **highly** recommended that you do a dry run before running the remove command.</span></span> <span data-ttu-id="99145-221">A execução seca mostrará quais SDKs e tempos de execução do .NET Core serão removidos quando você usar o comando `remove`.</span><span class="sxs-lookup"><span data-stu-id="99145-221">The dry run will show you what .NET Core SDKs and runtimes will be removed when you use the `remove` command.</span></span> <span data-ttu-id="99145-222">Consulte devo [remover uma versão?](../versions/remove-runtime-sdk-versions.md#should-i-remove-a-version) para saber quais SDKs e tempos de execução são seguros de remover.</span><span class="sxs-lookup"><span data-stu-id="99145-222">Refer to [Should I remove a version?](../versions/remove-runtime-sdk-versions.md#should-i-remove-a-version) to learn which SDKs and runtimes are safe to remove.</span></span>

> [!CAUTION]
> <span data-ttu-id="99145-223">Tenha em mente as seguintes advertências:</span><span class="sxs-lookup"><span data-stu-id="99145-223">Keep in mind the following caveats:</span></span>
>
>- <span data-ttu-id="99145-224">Essa ferramenta pode desinstalar versões do SDK do .NET Core que são necessárias para `global.json` arquivos em seu computador.</span><span class="sxs-lookup"><span data-stu-id="99145-224">This tool can uninstall versions of the .NET Core SDK that are required by `global.json` files on your machine.</span></span> <span data-ttu-id="99145-225">Você pode reinstalar SDKs do .NET Core na página [baixar o .NET Core](https://dotnet.microsoft.com/download/dotnet-core) .</span><span class="sxs-lookup"><span data-stu-id="99145-225">You can reinstall .NET Core SDKs from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="99145-226">Essa ferramenta pode desinstalar versões do tempo de execução do .NET Core que são exigidas por aplicativos dependentes da estrutura em seu computador.</span><span class="sxs-lookup"><span data-stu-id="99145-226">This tool can uninstall versions of the .NET Core runtime that are required by framework dependent applications on your machine.</span></span> <span data-ttu-id="99145-227">Você pode reinstalar os tempos de execução do .NET Core na página [baixar o .NET Core](https://dotnet.microsoft.com/download/dotnet-core) .</span><span class="sxs-lookup"><span data-stu-id="99145-227">You can reinstall .NET Core runtimes from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="99145-228">Essa ferramenta pode desinstalar versões do SDK do .NET Core e do tempo de execução dos quais o Visual Studio depende.</span><span class="sxs-lookup"><span data-stu-id="99145-228">This tool can uninstall versions of the .NET Core SDK and runtime that Visual Studio relies on.</span></span> <span data-ttu-id="99145-229">Se você interromper a instalação do Visual Studio, execute "reparar" no instalador do Visual Studio para voltar a um estado de funcionamento.</span><span class="sxs-lookup"><span data-stu-id="99145-229">If you break your Visual Studio installation, run "Repair" in the Visual Studio installer to get back to a working state.</span></span>

<span data-ttu-id="99145-230">Por padrão, todos os comandos mantêm os SDKs do .NET Core e os tempos de execução que podem ser exigidos pelo Visual Studio ou outros SDKs.</span><span class="sxs-lookup"><span data-stu-id="99145-230">By default, all commands keep the .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs.</span></span> <span data-ttu-id="99145-231">Esses SDKs e tempos de execução podem ser desinstalados, listando-os explicitamente como argumentos ou usando a opção `--force`.</span><span class="sxs-lookup"><span data-stu-id="99145-231">These SDKs and runtimes can be uninstalled by listing them explicitly as arguments or by using the `--force` option.</span></span>

<span data-ttu-id="99145-232">A ferramenta requer elevação para desinstalar SDKs e tempos de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="99145-232">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="99145-233">Execute a ferramenta em um prompt de comando do administrador no Windows e com `sudo` no macOS.</span><span class="sxs-lookup"><span data-stu-id="99145-233">Run the tool in an Administrator command prompt on Windows and with `sudo` on macOS.</span></span> <span data-ttu-id="99145-234">Os comandos `dry-run` e `whatif` não exigem elevação.</span><span class="sxs-lookup"><span data-stu-id="99145-234">The `dry-run` and `whatif` commands don't require elevation.</span></span>

<span data-ttu-id="99145-235">**dotnet-núcleo-desinstalar remover**</span><span class="sxs-lookup"><span data-stu-id="99145-235">**dotnet-core-uninstall remove**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="99145-236">Sinopse</span><span class="sxs-lookup"><span data-stu-id="99145-236">Synopsis</span></span>

```console
dotnet-core-uninstall remove [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="99145-237">Arguments</span><span class="sxs-lookup"><span data-stu-id="99145-237">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="99145-238">A versão especificada a ser desinstalada.</span><span class="sxs-lookup"><span data-stu-id="99145-238">The specified version to uninstall.</span></span> <span data-ttu-id="99145-239">Você pode listar várias versões uma após a outra, separadas por espaços.</span><span class="sxs-lookup"><span data-stu-id="99145-239">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="99145-240">Também há suporte para arquivos de resposta.</span><span class="sxs-lookup"><span data-stu-id="99145-240">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="99145-241">Os arquivos de resposta são uma alternativa para colocar todas as versões na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="99145-241">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="99145-242">São arquivos de texto, normalmente com uma extensão \*. rsp, e cada versão é listada em uma linha separada.</span><span class="sxs-lookup"><span data-stu-id="99145-242">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="99145-243">Para especificar um arquivo de resposta para o argumento `VERSION`, use o caractere \@ seguido imediatamente pelo nome do arquivo de resposta.</span><span class="sxs-lookup"><span data-stu-id="99145-243">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="99145-244">Opções</span><span class="sxs-lookup"><span data-stu-id="99145-244">Options</span></span>

## <a name="windowstabwindows"></a>[<span data-ttu-id="99145-245">Windows</span><span class="sxs-lookup"><span data-stu-id="99145-245">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="99145-246">Remove todos os SDKs e tempos de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="99145-246">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="99145-247">Remove somente os SDKs do .NET Core e os tempos de execução com uma versão menor do que a versão especificada.</span><span class="sxs-lookup"><span data-stu-id="99145-247">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="99145-248">A versão especificada permanece instalada.</span><span class="sxs-lookup"><span data-stu-id="99145-248">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="99145-249">Remove todos os SDKs e tempos de execução do .NET Core, exceto as versões especificadas.</span><span class="sxs-lookup"><span data-stu-id="99145-249">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="99145-250">Remove SDKs e tempos de execução do .NET Core, exceto a versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="99145-250">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="99145-251">Remove os SDKs do .NET Core e os tempos de execução substituídos por patches mais altos.</span><span class="sxs-lookup"><span data-stu-id="99145-251">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="99145-252">Essa opção protege global. JSON.</span><span class="sxs-lookup"><span data-stu-id="99145-252">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="99145-253">Remove SDKs e tempos de execução do .NET Core marcados como visualizações.</span><span class="sxs-lookup"><span data-stu-id="99145-253">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="99145-254">Remove os SDKs e os tempos de execução do .NET Core marcados como versões prévias, exceto a visualização mais alta.</span><span class="sxs-lookup"><span data-stu-id="99145-254">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="99145-255">Remove somente ASP.NET Core tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="99145-255">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="99145-256">Remove somente os agrupamentos de hospedagem e de tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="99145-256">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="99145-257">Remove SDKs e tempos de execução do .NET Core que correspondem à versão de `major.minor` especificada.</span><span class="sxs-lookup"><span data-stu-id="99145-257">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="99145-258">Remove somente os tempos de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="99145-258">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="99145-259">Remove somente SDKs do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="99145-259">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="99145-260">Define o nível de detalhes.</span><span class="sxs-lookup"><span data-stu-id="99145-260">Sets the verbosity level.</span></span> <span data-ttu-id="99145-261">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="99145-261">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="99145-262">O valor padrão é `normal`.</span><span class="sxs-lookup"><span data-stu-id="99145-262">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="99145-263">Deve ser usado com `--sdk`, `--runtime`e `--aspnet-runtime` para remover SDKs ou tempos de execução de x64.</span><span class="sxs-lookup"><span data-stu-id="99145-263">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="99145-264">Deve ser usado com `--sdk`, `--runtime`e `--aspnet-runtime` para remover SDKs ou tempos de execução do x86.</span><span class="sxs-lookup"><span data-stu-id="99145-264">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="99145-265">**`-y, --yes`** Executa o comando sem a necessidade de uma confirmação Sim ou não.</span><span class="sxs-lookup"><span data-stu-id="99145-265">**`-y, --yes`** Executes the command without requiring a yes or no confirmation.</span></span>

* <span data-ttu-id="99145-266">**`--force`** Força a remoção de versões que podem ser usadas pelo Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="99145-266">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="99145-267">Observações:</span><span class="sxs-lookup"><span data-stu-id="99145-267">Notes:</span></span>

1. <span data-ttu-id="99145-268">É necessário ter exatamente um dos `--sdk`, `--runtime`, `--aspnet-runtime`e `--hosting-bundle`.</span><span class="sxs-lookup"><span data-stu-id="99145-268">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="99145-269">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`e `[<VERSION>...]` são exclusivos.</span><span class="sxs-lookup"><span data-stu-id="99145-269">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="99145-270">Se `--x64` ou `--x86` não forem especificados, tanto o x64 quanto o x86 serão removidos.</span><span class="sxs-lookup"><span data-stu-id="99145-270">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macostabmacos"></a>[<span data-ttu-id="99145-271">macOS</span><span class="sxs-lookup"><span data-stu-id="99145-271">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="99145-272">Remove todos os SDKs e tempos de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="99145-272">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="99145-273">Remove os SDKs do .NET Core e os tempos de execução abaixo da versão especificada.</span><span class="sxs-lookup"><span data-stu-id="99145-273">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="99145-274">A versão especificada permanecerá.</span><span class="sxs-lookup"><span data-stu-id="99145-274">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="99145-275">Remove SDKs e tempos de execução do .NET Core, exceto as versões especificadas.</span><span class="sxs-lookup"><span data-stu-id="99145-275">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="99145-276">Remove SDKs e tempos de execução do .NET Core, exceto a versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="99145-276">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="99145-277">Remove os SDKs do .NET Core e os tempos de execução substituídos por patches mais altos.</span><span class="sxs-lookup"><span data-stu-id="99145-277">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="99145-278">Essa opção protege global. JSON.</span><span class="sxs-lookup"><span data-stu-id="99145-278">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="99145-279">Remove SDKs e tempos de execução do .NET Core marcados como visualizações.</span><span class="sxs-lookup"><span data-stu-id="99145-279">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="99145-280">Remove os SDKs e os tempos de execução do .NET Core marcados como versões prévias, exceto a visualização mais alta.</span><span class="sxs-lookup"><span data-stu-id="99145-280">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="99145-281">Remove SDKs e tempos de execução do .NET Core que correspondem à versão de `major.minor` especificada.</span><span class="sxs-lookup"><span data-stu-id="99145-281">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="99145-282">Remove somente os tempos de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="99145-282">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="99145-283">Remove somente SDKs do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="99145-283">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="99145-284">Define o nível de detalhes.</span><span class="sxs-lookup"><span data-stu-id="99145-284">Sets the verbosity level.</span></span> <span data-ttu-id="99145-285">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="99145-285">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="99145-286">O valor padrão é `normal`.</span><span class="sxs-lookup"><span data-stu-id="99145-286">The default value is `normal`.</span></span>

* <span data-ttu-id="99145-287">**`-y, --yes`** Executa o comando sem a necessidade de confirmação de Y/n.</span><span class="sxs-lookup"><span data-stu-id="99145-287">**`-y, --yes`** Executes the command without requiring Y/n confirmation.</span></span>
  
* <span data-ttu-id="99145-288">**`--force`** Força a remoção de versões que podem ser usadas pelo Visual Studio ou SDKs.</span><span class="sxs-lookup"><span data-stu-id="99145-288">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="99145-289">Observações:</span><span class="sxs-lookup"><span data-stu-id="99145-289">Notes:</span></span>

1. <span data-ttu-id="99145-290">É necessário ter exatamente um dos `--sdk` e `--runtime`.</span><span class="sxs-lookup"><span data-stu-id="99145-290">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="99145-291">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`e `[<VERSION>...]` são exclusivos.</span><span class="sxs-lookup"><span data-stu-id="99145-291">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="99145-292">Exemplos</span><span class="sxs-lookup"><span data-stu-id="99145-292">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="99145-293">Por padrão, os SDKs do .NET Core e os tempos de execução que podem ser exigidos pelo Visual Studio ou outros SDKs são mantidos.</span><span class="sxs-lookup"><span data-stu-id="99145-293">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are kept.</span></span> <span data-ttu-id="99145-294">Nos exemplos a seguir, alguns dos SDKs e tempos de execução especificados podem permanecer, dependendo do estado do computador.</span><span class="sxs-lookup"><span data-stu-id="99145-294">In the following examples, some of the specified SDKs and runtimes may remain, depending on the state of the machine.</span></span> <span data-ttu-id="99145-295">Para remover todos os SDKs e tempos de execução, liste-os explicitamente como argumentos ou use a opção `--force`.</span><span class="sxs-lookup"><span data-stu-id="99145-295">To remove all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="99145-296">Remova todos os tempos de execução do .NET Core x86, exceto a versão `3.0.0-preview6-27804-01` sem exigir confirmação de Y/n:</span><span class="sxs-lookup"><span data-stu-id="99145-296">Remove all x86 .NET Core runtimes except the version `3.0.0-preview6-27804-01` without requiring Y/n confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --all-but 3.0.0-preview6-27804-01 --runtime --yes
  ```

* <span data-ttu-id="99145-297">Remova todos os SDKs do .NET Core 1,1 sem exigir confirmação de s/n:</span><span class="sxs-lookup"><span data-stu-id="99145-297">Remove all .NET Core 1.1 SDKs without requiring Y/n confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --sdk --major-minor 1.1 -y
  ```

* <span data-ttu-id="99145-298">Remova o SDK do .NET Core 1.1.11 sem saída de console:</span><span class="sxs-lookup"><span data-stu-id="99145-298">Remove the .NET Core 1.1.11 SDK with no console output:</span></span>

  ```console
  dotnet-core-uninstall remove 1.1.11 --sdk --yes -verbosity q
  ```

* <span data-ttu-id="99145-299">Remova todos os SDKs do .NET Core que podem ser removidos com segurança por essa ferramenta:</span><span class="sxs-lookup"><span data-stu-id="99145-299">Remove all .NET Core SDKs that can safely be removed by this tool:</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk
  ```

* <span data-ttu-id="99145-300">Remova todos os SDKs do .NET Core que podem ser removidos por essa ferramenta, incluindo os SDKs que podem ser exigidos pelo Visual Studio (não recomendado):</span><span class="sxs-lookup"><span data-stu-id="99145-300">Remove all .NET Core SDKs that can be removed by this tool, including those SDKs that may be required by Visual Studio (not recommended):</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk --force
  ```

* <span data-ttu-id="99145-301">Remova todos os SDKs do .NET Core especificados no arquivo de resposta `versions.rsp`</span><span class="sxs-lookup"><span data-stu-id="99145-301">Remove all .NET Core SDKs that are specified in the response file `versions.rsp`</span></span>

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  <span data-ttu-id="99145-302">O conteúdo de *Versions. rsp* é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="99145-302">The content of *versions.rsp* is as follows:</span></span>
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a><span data-ttu-id="99145-303">Etapa 4-excluir a pasta de fallback do NuGet (opcional)</span><span class="sxs-lookup"><span data-stu-id="99145-303">Step 4 - Delete the NuGet fallback folder (optional)</span></span>

<span data-ttu-id="99145-304">Em alguns casos, você não precisa mais do `NuGetFallbackFolder` e talvez queira excluí-lo.</span><span class="sxs-lookup"><span data-stu-id="99145-304">In some cases, you no longer need the `NuGetFallbackFolder` and may wish to delete it.</span></span> <span data-ttu-id="99145-305">Para obter mais informações sobre como excluir essa pasta, consulte [remover o NuGetFallbackFolder](../versions/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span><span class="sxs-lookup"><span data-stu-id="99145-305">For more information about deleting this folder, see [Remove the NuGetFallbackFolder](../versions/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span></span>

## <a name="uninstall-the-tool"></a><span data-ttu-id="99145-306">Desinstalar a ferramenta</span><span class="sxs-lookup"><span data-stu-id="99145-306">Uninstall the tool</span></span>

## <a name="windowstabwindows"></a>[<span data-ttu-id="99145-307">Windows</span><span class="sxs-lookup"><span data-stu-id="99145-307">Windows</span></span>](#tab/windows)

1. <span data-ttu-id="99145-308">Abra **Adicionar ou remover programas**.</span><span class="sxs-lookup"><span data-stu-id="99145-308">Open **Add or Remove Programs**.</span></span>
2. <span data-ttu-id="99145-309">Pesquise por `Microsoft .NET Core SDK Uninstall Tool`.</span><span class="sxs-lookup"><span data-stu-id="99145-309">Search for `Microsoft .NET Core SDK Uninstall Tool`.</span></span>
3. <span data-ttu-id="99145-310">Selecione **Desinstalar**.</span><span class="sxs-lookup"><span data-stu-id="99145-310">Select **Uninstall**.</span></span>

## <a name="macostabmacos"></a>[<span data-ttu-id="99145-311">macOS</span><span class="sxs-lookup"><span data-stu-id="99145-311">macOS</span></span>](#tab/macos)

<span data-ttu-id="99145-312">Exclua o arquivo *dotnet-Core-Uninstall. tar. gz* baixado do diretório em que ele foi instalado.</span><span class="sxs-lookup"><span data-stu-id="99145-312">Delete the downloaded *dotnet-core-uninstall.tar.gz* file from the directory where it was installed.</span></span> <span data-ttu-id="99145-313">Se você descompactou o conteúdo desse arquivo em outro diretório, certifique-se de excluir esse conteúdo também.</span><span class="sxs-lookup"><span data-stu-id="99145-313">If you unzipped the contents of this file into another directory, be sure to delete that content as well.</span></span>

---
