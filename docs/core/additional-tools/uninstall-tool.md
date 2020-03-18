---
title: Desinstalar ferramenta
description: Uma visão geral da Ferramenta de Desinstalação do Núcleo .NET, uma ferramenta guiada que permite a limpeza controlada de SDKs e tempos de execução do Núcleo .NET.
author: sfoslund
ms.date: 01/06/2020
ms.openlocfilehash: bd20cba133cbb754dcca48e48b76a391a9efacba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846992"
---
# <a name="net-core-uninstall-tool"></a><span data-ttu-id="85f02-103">Ferramenta de Desinstalação do .NET Core</span><span class="sxs-lookup"><span data-stu-id="85f02-103">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="85f02-104">A`dotnet-core-uninstall` [ferramenta de desinstalação do núcleo .NET](https://aka.ms/dotnet-core-uninstall-tool) permite remover SDKs e runtimes do .NET Core de um sistema.</span><span class="sxs-lookup"><span data-stu-id="85f02-104">The [.NET Core Uninstall Tool](https://aka.ms/dotnet-core-uninstall-tool) (`dotnet-core-uninstall`) lets you remove .NET Core SDKs and Runtimes from a system.</span></span> <span data-ttu-id="85f02-105">Uma coleção de opções está disponível para especificar quais versões você deseja desinstalar.</span><span class="sxs-lookup"><span data-stu-id="85f02-105">A collection of options is available to specify which versions you want to uninstall.</span></span>

<span data-ttu-id="85f02-106">A ferramenta suporta Windows e macOS.</span><span class="sxs-lookup"><span data-stu-id="85f02-106">The tool supports Windows and macOS.</span></span> <span data-ttu-id="85f02-107">O Linux não tem suporte no momento.</span><span class="sxs-lookup"><span data-stu-id="85f02-107">Linux is currently not supported.</span></span>

<span data-ttu-id="85f02-108">No Windows, a ferramenta só pode desinstalar SDKs e Runtimes que foram instalados usando um dos seguintes instaladores:</span><span class="sxs-lookup"><span data-stu-id="85f02-108">On Windows, the tool can only uninstall SDKs and Runtimes that were installed using one of the following installers:</span></span>

- <span data-ttu-id="85f02-109">O .NET Core SDK e o instalador de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="85f02-109">The .NET Core SDK and runtime installer.</span></span>
- <span data-ttu-id="85f02-110">O instalador do Visual Studio em versões anteriores ao Visual Studio 2019 versão 16.3.</span><span class="sxs-lookup"><span data-stu-id="85f02-110">The Visual Studio installer in versions earlier than Visual Studio 2019 version 16.3.</span></span>

<span data-ttu-id="85f02-111">No macOS, a ferramenta só pode desinstalar SDKs e runtimes localizados na pasta */usr/local/share/dotnet.*</span><span class="sxs-lookup"><span data-stu-id="85f02-111">On macOS, the tool can only uninstall SDKs and runtimes located in the */usr/local/share/dotnet* folder.</span></span>

<span data-ttu-id="85f02-112">Devido a essas limitações, a ferramenta pode não ser capaz de desinstalar todos os SDKs e tempos de execução do .NET Core na sua máquina.</span><span class="sxs-lookup"><span data-stu-id="85f02-112">Because of these limitations, the tool may not be able to uninstall all of the .NET Core SDKs and runtimes on your machine.</span></span> <span data-ttu-id="85f02-113">Você pode `dotnet --info` usar o comando para encontrar todos os SDKs e tempos de execução do .NET Core instalados, incluindo os SDKs e tempos de execução que esta ferramenta não pode remover.</span><span class="sxs-lookup"><span data-stu-id="85f02-113">You can use the `dotnet --info` command to find all of the .NET Core SDKs and runtimes installed, including those SDKs and runtimes that this tool can't remove.</span></span> <span data-ttu-id="85f02-114">O `dotnet-core-uninstall list` comando exibe quais SDKs podem ser desinstalados com a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="85f02-114">The `dotnet-core-uninstall list` command displays which SDKs can be uninstalled with the tool.</span></span>

## <a name="install-the-tool"></a><span data-ttu-id="85f02-115">Instale a ferramenta</span><span class="sxs-lookup"><span data-stu-id="85f02-115">Install the tool</span></span>

<span data-ttu-id="85f02-116">Você pode baixar a Ferramenta de Desinstalação do Núcleo .NET [daqui](https://aka.ms/dotnet-core-uninstall-tool) e encontrar o código-fonte no repositório [dotnet/cli-lab](https://github.com/dotnet/cli-lab) GitHub.</span><span class="sxs-lookup"><span data-stu-id="85f02-116">You can download the .NET Core Uninstall Tool from [here](https://aka.ms/dotnet-core-uninstall-tool) and find the source code at the [dotnet/cli-lab](https://github.com/dotnet/cli-lab) GitHub repository.</span></span>

> [!NOTE]
> <span data-ttu-id="85f02-117">A ferramenta requer elevação para desinstalar SDKs e tempos de execução do Núcleo .NET.</span><span class="sxs-lookup"><span data-stu-id="85f02-117">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="85f02-118">Portanto, ele deve ser instalado em um diretório protegido por gravação, como *C:\Arquivos de programa* no Windows ou */usr/local/bin* no macOS.</span><span class="sxs-lookup"><span data-stu-id="85f02-118">Therefore, it should be installed in a write-protected directory such as *C:\Program Files* on Windows or */usr/local/bin* on macOS.</span></span> <span data-ttu-id="85f02-119">Veja também [acesso elevado para comandos dotnet](../tools/elevated-access.md).</span><span class="sxs-lookup"><span data-stu-id="85f02-119">See also [Elevated access for dotnet commands](../tools/elevated-access.md).</span></span> <span data-ttu-id="85f02-120">Para obter mais informações, consulte as [instruções detalhadas de instalação](https://aka.ms/dotnet-core-uninstall-tool).</span><span class="sxs-lookup"><span data-stu-id="85f02-120">For more information, see the [detailed installation instructions](https://aka.ms/dotnet-core-uninstall-tool).</span></span>

## <a name="run-the-tool"></a><span data-ttu-id="85f02-121">Execute a ferramenta</span><span class="sxs-lookup"><span data-stu-id="85f02-121">Run the tool</span></span>

<span data-ttu-id="85f02-122">As etapas a seguir mostram a abordagem recomendada para executar a ferramenta de desinstalação:</span><span class="sxs-lookup"><span data-stu-id="85f02-122">The following steps show the recommended approach for running the uninstall tool:</span></span>

- [<span data-ttu-id="85f02-123">Passo 1 - Exibir SDKs e tempos de execução instalados .NET Core</span><span class="sxs-lookup"><span data-stu-id="85f02-123">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>](#step-1---display-installed-net-core-sdks-and-runtimes)
- [<span data-ttu-id="85f02-124">Passo 2 - Faça uma corrida a seco</span><span class="sxs-lookup"><span data-stu-id="85f02-124">Step 2 - Do a dry run</span></span>](#step-2---do-a-dry-run)
- [<span data-ttu-id="85f02-125">Passo 3 - Desinstalar SDKs e runtimes do núcleo .NET</span><span class="sxs-lookup"><span data-stu-id="85f02-125">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>](#step-3---uninstall-net-core-sdks-and-runtimes)
- [<span data-ttu-id="85f02-126">Passo 4 - Excluir a pasta de recuo NuGet (opcional)</span><span class="sxs-lookup"><span data-stu-id="85f02-126">Step 4 - Delete the NuGet fallback folder (optional)</span></span>](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-core-sdks-and-runtimes"></a><span data-ttu-id="85f02-127">Passo 1 - Exibir SDKs e tempos de execução instalados .NET Core</span><span class="sxs-lookup"><span data-stu-id="85f02-127">Step 1 - Display installed .NET Core SDKs and runtimes</span></span>

<span data-ttu-id="85f02-128">O `dotnet-core-uninstall list` comando lista os SDKs do Núcleo .NET instalados e os tempos de execução que podem ser removidos com esta ferramenta.</span><span class="sxs-lookup"><span data-stu-id="85f02-128">The `dotnet-core-uninstall list` command lists the installed .NET Core SDKs and runtimes that can be removed with this tool.</span></span> <span data-ttu-id="85f02-129">Alguns SDKs e tempos de execução podem ser exigidos pelo Visual Studio e eles são exibidos com uma nota de por que não é recomendado desinstalá-los.</span><span class="sxs-lookup"><span data-stu-id="85f02-129">Some SDKs and runtimes may be required by Visual Studio and they're displayed with a note of why it isn't recommended to uninstall them.</span></span>

<span data-ttu-id="85f02-130">**dotnet-core-uninstall list**</span><span class="sxs-lookup"><span data-stu-id="85f02-130">**dotnet-core-uninstall list**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="85f02-131">Sinopse</span><span class="sxs-lookup"><span data-stu-id="85f02-131">Synopsis</span></span>

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a><span data-ttu-id="85f02-132">Opções</span><span class="sxs-lookup"><span data-stu-id="85f02-132">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="85f02-133">Windows</span><span class="sxs-lookup"><span data-stu-id="85f02-133">Windows</span></span>](#tab/windows)

* **`--aspnet-runtime`**

  <span data-ttu-id="85f02-134">Lista todos os tempos de execução do ASP.NET Core que podem ser desinstalados com esta ferramenta.</span><span class="sxs-lookup"><span data-stu-id="85f02-134">Lists all the ASP.NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="85f02-135">Lista todos os pacotes de tempo de execução do .NET Core e de hospedagem que podem ser desinstalados com esta ferramenta.</span><span class="sxs-lookup"><span data-stu-id="85f02-135">Lists all the .NET Core runtime and hosting bundles that can be uninstalled with this tool.</span></span>

* **`--runtime`**

  <span data-ttu-id="85f02-136">Lista todos os tempos de execução do .NET Core que podem ser desinstalados com esta ferramenta.</span><span class="sxs-lookup"><span data-stu-id="85f02-136">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="85f02-137">Lista todos os SDKs do Núcleo .NET que podem ser desinstalados com esta ferramenta.</span><span class="sxs-lookup"><span data-stu-id="85f02-137">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="85f02-138">Define o nível de verbosidade.</span><span class="sxs-lookup"><span data-stu-id="85f02-138">Sets the verbosity level.</span></span> <span data-ttu-id="85f02-139">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="85f02-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="85f02-140">O valor padrão é `normal`.</span><span class="sxs-lookup"><span data-stu-id="85f02-140">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="85f02-141">Lista todos os SDKs do Núcleo .NET x64 e tempos de execução que podem ser desinstalados com esta ferramenta.</span><span class="sxs-lookup"><span data-stu-id="85f02-141">Lists all x64 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

* **`--x86`**

  <span data-ttu-id="85f02-142">Lista todos os SDKs do Núcleo .NET x86 e tempos de execução que podem ser desinstalados com esta ferramenta.</span><span class="sxs-lookup"><span data-stu-id="85f02-142">Lists all x86 .NET Core SDKs and runtimes that can be uninstalled with this tool.</span></span>

## <a name="macos"></a>[<span data-ttu-id="85f02-143">macOS</span><span class="sxs-lookup"><span data-stu-id="85f02-143">macOS</span></span>](#tab/macos)

* **`--runtime`**

  <span data-ttu-id="85f02-144">Lista todos os tempos de execução do .NET Core que podem ser desinstalados com esta ferramenta.</span><span class="sxs-lookup"><span data-stu-id="85f02-144">Lists all .NET Core runtimes that can be uninstalled with this tool.</span></span>

* **`--sdk`**

  <span data-ttu-id="85f02-145">Lista todos os SDKs do Núcleo .NET que podem ser desinstalados com esta ferramenta.</span><span class="sxs-lookup"><span data-stu-id="85f02-145">Lists all .NET Core SDKs that can be uninstalled with this tool.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="85f02-146">Define o nível de verbosidade.</span><span class="sxs-lookup"><span data-stu-id="85f02-146">Sets the verbosity level.</span></span> <span data-ttu-id="85f02-147">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="85f02-147">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="85f02-148">O valor padrão é `normal`.</span><span class="sxs-lookup"><span data-stu-id="85f02-148">The default value is `normal`.</span></span>
  
---

#### <a name="examples"></a><span data-ttu-id="85f02-149">Exemplos</span><span class="sxs-lookup"><span data-stu-id="85f02-149">Examples</span></span>

* <span data-ttu-id="85f02-150">Liste todos os SDKs e tempos de execução do .NET Core que podem ser removidos com esta ferramenta:</span><span class="sxs-lookup"><span data-stu-id="85f02-150">List all .NET Core SDKs and runtimes that can be removed with this tool:</span></span>

  ```console
  dotnet-core-uninstall list
  ```

* <span data-ttu-id="85f02-151">Liste todos os SDKs do Núcleo .NET x64 e tempos de execução:</span><span class="sxs-lookup"><span data-stu-id="85f02-151">List all x64 .NET Core SDKs and runtimes:</span></span>

  ```console
  dotnet-core-uninstall list --x64
  ```

* <span data-ttu-id="85f02-152">Liste todos os SDKs do núcleo x86 .NET:</span><span class="sxs-lookup"><span data-stu-id="85f02-152">List all x86 .NET Core SDKs:</span></span>

  ```console
  dotnet-core-uninstall list --sdk --x86
  ```

### <a name="step-2---do-a-dry-run"></a><span data-ttu-id="85f02-153">Passo 2 - Faça uma corrida a seco</span><span class="sxs-lookup"><span data-stu-id="85f02-153">Step 2 - Do a dry run</span></span>

<span data-ttu-id="85f02-154">Os `dotnet-core-uninstall dry-run` `dotnet-core-uninstall whatif` comandos exibem os SDKs do Núcleo .NET e os tempos de execução que serão removidos com base nas opções fornecidas sem realizar a desinstalação.</span><span class="sxs-lookup"><span data-stu-id="85f02-154">The `dotnet-core-uninstall dry-run` and `dotnet-core-uninstall whatif` commands display the .NET Core SDKs and runtimes that will be removed based on the options provided without performing the uninstall.</span></span> <span data-ttu-id="85f02-155">Esses comandos são sinônimos.</span><span class="sxs-lookup"><span data-stu-id="85f02-155">These commands are synonyms.</span></span>

<span data-ttu-id="85f02-156">**dotnet-core-desinstalar dry-run e dotnet-core-desinstalar whatif**</span><span class="sxs-lookup"><span data-stu-id="85f02-156">**dotnet-core-uninstall dry-run and dotnet-core-uninstall whatif**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="85f02-157">Sinopse</span><span class="sxs-lookup"><span data-stu-id="85f02-157">Synopsis</span></span>

```console
dotnet-core-uninstall dry-run [options] [<VERSION>...]

dotnet-core-uninstall whatif [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="85f02-158">Argumentos</span><span class="sxs-lookup"><span data-stu-id="85f02-158">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="85f02-159">A versão especificada para desinstalar.</span><span class="sxs-lookup"><span data-stu-id="85f02-159">The specified version to uninstall.</span></span> <span data-ttu-id="85f02-160">Você pode listar várias versões uma após a outra, separadas por espaços.</span><span class="sxs-lookup"><span data-stu-id="85f02-160">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="85f02-161">Os arquivos de resposta também são suportados.</span><span class="sxs-lookup"><span data-stu-id="85f02-161">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="85f02-162">Os arquivos de resposta são uma alternativa para colocar todas as versões na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="85f02-162">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="85f02-163">São arquivos de texto, normalmente com uma \*extensão .rsp, e cada versão é listada em uma linha separada.</span><span class="sxs-lookup"><span data-stu-id="85f02-163">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="85f02-164">Para especificar um `VERSION` arquivo de \@ resposta para o argumento, use o caractere imediatamente seguido pelo nome do arquivo de resposta.</span><span class="sxs-lookup"><span data-stu-id="85f02-164">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="85f02-165">Opções</span><span class="sxs-lookup"><span data-stu-id="85f02-165">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="85f02-166">Windows</span><span class="sxs-lookup"><span data-stu-id="85f02-166">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="85f02-167">Remove todos os SDKs do Núcleo .NET e tempos de execução.</span><span class="sxs-lookup"><span data-stu-id="85f02-167">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="85f02-168">Remove apenas os SDKs do Núcleo .NET e os tempos de execução com uma versão menor que a especificada.</span><span class="sxs-lookup"><span data-stu-id="85f02-168">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="85f02-169">A versão especificada permanece instalada.</span><span class="sxs-lookup"><span data-stu-id="85f02-169">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="85f02-170">Remove todos os SDKs e tempos de execução do .NET Core, exceto as versões especificadas.</span><span class="sxs-lookup"><span data-stu-id="85f02-170">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="85f02-171">Remove SDKs e tempos de execução do .NET Core, exceto a versão mais alta.</span><span class="sxs-lookup"><span data-stu-id="85f02-171">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="85f02-172">Remove SDKs do Núcleo .NET e tempos de execução substituídos por patches mais altos.</span><span class="sxs-lookup"><span data-stu-id="85f02-172">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="85f02-173">Esta opção protege global.json.</span><span class="sxs-lookup"><span data-stu-id="85f02-173">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="85f02-174">Remove SDKs do Núcleo .NET e tempos de execução marcados como visualizações.</span><span class="sxs-lookup"><span data-stu-id="85f02-174">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="85f02-175">Remove SDKs do Núcleo .NET e tempos de execução marcados como visualizações, exceto a visualização mais alta.</span><span class="sxs-lookup"><span data-stu-id="85f02-175">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="85f02-176">Remove apenas ASP.NET tempos de execução do Core.</span><span class="sxs-lookup"><span data-stu-id="85f02-176">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="85f02-177">Remove apenas o tempo de execução do .NET Core e os pacotes de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="85f02-177">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="85f02-178">Remove SDKs do Núcleo .NET e tempos `major.minor` de execução que correspondem à versão especificada.</span><span class="sxs-lookup"><span data-stu-id="85f02-178">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="85f02-179">Remove apenas os tempos de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="85f02-179">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="85f02-180">Remove apenas SDKs do Núcleo .NET.</span><span class="sxs-lookup"><span data-stu-id="85f02-180">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="85f02-181">Define o nível de verbosidade.</span><span class="sxs-lookup"><span data-stu-id="85f02-181">Sets the verbosity level.</span></span> <span data-ttu-id="85f02-182">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="85f02-182">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="85f02-183">O valor padrão é `normal`.</span><span class="sxs-lookup"><span data-stu-id="85f02-183">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="85f02-184">Deve ser `--sdk`usado `--runtime`com `--aspnet-runtime` , e para remover sdks x64 ou tempos de execução.</span><span class="sxs-lookup"><span data-stu-id="85f02-184">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="85f02-185">Deve ser `--sdk`usado `--runtime`com `--aspnet-runtime` , e para remover sdks x86 ou tempos de execução.</span><span class="sxs-lookup"><span data-stu-id="85f02-185">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="85f02-186">**`--force`** Força a remoção de versões que podem ser usadas pelo Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="85f02-186">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="85f02-187">Observações:</span><span class="sxs-lookup"><span data-stu-id="85f02-187">Notes:</span></span>

1. <span data-ttu-id="85f02-188">Exatamente um `--sdk` `--runtime`dos `--aspnet-runtime`, `--hosting-bundle` , e é necessário.</span><span class="sxs-lookup"><span data-stu-id="85f02-188">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="85f02-189">`--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , , , , , e são exclusivos.</span><span class="sxs-lookup"><span data-stu-id="85f02-189">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="85f02-190">Se `--x64` `--x86` ou não forem especificados, então tanto x64 quanto x86 serão removidos.</span><span class="sxs-lookup"><span data-stu-id="85f02-190">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="85f02-191">macOS</span><span class="sxs-lookup"><span data-stu-id="85f02-191">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="85f02-192">Remove todos os SDKs do Núcleo .NET e tempos de execução.</span><span class="sxs-lookup"><span data-stu-id="85f02-192">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="85f02-193">Remove SDKs do Núcleo .NET e tempos de execução abaixo da versão especificada.</span><span class="sxs-lookup"><span data-stu-id="85f02-193">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="85f02-194">A versão especificada permanecerá.</span><span class="sxs-lookup"><span data-stu-id="85f02-194">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="85f02-195">Remove SDKs e tempos de execução do .NET Core, exceto as versões especificadas.</span><span class="sxs-lookup"><span data-stu-id="85f02-195">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="85f02-196">Remove SDKs e tempos de execução do .NET Core, exceto a versão mais alta.</span><span class="sxs-lookup"><span data-stu-id="85f02-196">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="85f02-197">Remove SDKs do Núcleo .NET e tempos de execução substituídos por patches mais altos.</span><span class="sxs-lookup"><span data-stu-id="85f02-197">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="85f02-198">Esta opção protege global.json.</span><span class="sxs-lookup"><span data-stu-id="85f02-198">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="85f02-199">Remove SDKs do Núcleo .NET e tempos de execução marcados como visualizações.</span><span class="sxs-lookup"><span data-stu-id="85f02-199">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="85f02-200">Remove SDKs do Núcleo .NET e tempos de execução marcados como visualizações, exceto a visualização mais alta.</span><span class="sxs-lookup"><span data-stu-id="85f02-200">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="85f02-201">Remove SDKs do Núcleo .NET e tempos `major.minor` de execução que correspondem à versão especificada.</span><span class="sxs-lookup"><span data-stu-id="85f02-201">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="85f02-202">Remove apenas os tempos de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="85f02-202">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="85f02-203">Remove apenas SDKs do Núcleo .NET.</span><span class="sxs-lookup"><span data-stu-id="85f02-203">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="85f02-204">Define o nível de verbosidade.</span><span class="sxs-lookup"><span data-stu-id="85f02-204">Sets the verbosity level.</span></span> <span data-ttu-id="85f02-205">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="85f02-205">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="85f02-206">O valor padrão é `normal`.</span><span class="sxs-lookup"><span data-stu-id="85f02-206">The default value is `normal`.</span></span>
  
* <span data-ttu-id="85f02-207">**`--force`** Força a remoção de versões que podem ser usadas pelo Visual Studio ou SDKs.</span><span class="sxs-lookup"><span data-stu-id="85f02-207">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="85f02-208">Observações:</span><span class="sxs-lookup"><span data-stu-id="85f02-208">Notes:</span></span>

1. <span data-ttu-id="85f02-209">Exatamente um `--sdk` `--runtime` dos mais necessários.</span><span class="sxs-lookup"><span data-stu-id="85f02-209">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="85f02-210">`--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , , , , , e são exclusivos.</span><span class="sxs-lookup"><span data-stu-id="85f02-210">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="85f02-211">Exemplos</span><span class="sxs-lookup"><span data-stu-id="85f02-211">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="85f02-212">Por padrão, Os SDKs do Núcleo .NET e os tempos de execução `dotnet-core-uninstall dry-run` que podem ser exigidos pelo Visual Studio ou outros SDKs não estão incluídos na saída.</span><span class="sxs-lookup"><span data-stu-id="85f02-212">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are not included in `dotnet-core-uninstall dry-run` output.</span></span> <span data-ttu-id="85f02-213">Nos exemplos a seguir, alguns dos SDKs e tempos de execução especificados podem não ser incluídos na saída, dependendo do estado da máquina.</span><span class="sxs-lookup"><span data-stu-id="85f02-213">In the following examples, some of the specified SDKs and runtimes may not be included in the output, depending on the state of the machine.</span></span> <span data-ttu-id="85f02-214">Para incluir todos os SDKs e tempos de execução, liste-os explicitamente como argumentos ou use a `--force` opção.</span><span class="sxs-lookup"><span data-stu-id="85f02-214">To include all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="85f02-215">Dry run of removeall .NET Core runtimes que foram substituídos por patches mais altos:</span><span class="sxs-lookup"><span data-stu-id="85f02-215">Dry run of removing all .NET Core runtimes that have been superseded by higher patches:</span></span>

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* <span data-ttu-id="85f02-216">Dry run de remover todos os SDKs `2.2.301`do Núcleo .NET abaixo da versão :</span><span class="sxs-lookup"><span data-stu-id="85f02-216">Dry run of removing all .NET Core SDKs below the version `2.2.301`:</span></span>

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-core-sdks-and-runtimes"></a><span data-ttu-id="85f02-217">Passo 3 - Desinstalar SDKs e runtimes do núcleo .NET</span><span class="sxs-lookup"><span data-stu-id="85f02-217">Step 3 - Uninstall .NET Core SDKs and Runtimes</span></span>

<span data-ttu-id="85f02-218">`dotnet-core-uninstall remove`desinstala SDKs e Runtimes do Núcleo .NET especificados por uma coleção de opções.</span><span class="sxs-lookup"><span data-stu-id="85f02-218">`dotnet-core-uninstall remove` uninstalls .NET Core SDKs and Runtimes that are specified by a collection of options.</span></span> <span data-ttu-id="85f02-219">A ferramenta não pode ser usada para desinstalar SDKs e Runtimes com a versão 5.0 ou superior.</span><span class="sxs-lookup"><span data-stu-id="85f02-219">The tool can't be used to uninstall SDKs and Runtimes with version 5.0 or above.</span></span>

<span data-ttu-id="85f02-220">Uma vez que esta ferramenta tem um comportamento destrutivo, é **altamente** recomendável que você faça uma corrida a seco antes de executar o comando remover.</span><span class="sxs-lookup"><span data-stu-id="85f02-220">Since this tool has a destructive behavior, it's **highly** recommended that you do a dry run before running the remove command.</span></span> <span data-ttu-id="85f02-221">A corrida a seco mostrará quais SDKs e tempos de `remove` execução do .NET Core serão removidos quando você usar o comando.</span><span class="sxs-lookup"><span data-stu-id="85f02-221">The dry run will show you what .NET Core SDKs and runtimes will be removed when you use the `remove` command.</span></span> <span data-ttu-id="85f02-222">Consulte [Devo remover uma versão?](../versions/remove-runtime-sdk-versions.md#should-i-remove-a-version)</span><span class="sxs-lookup"><span data-stu-id="85f02-222">Refer to [Should I remove a version?](../versions/remove-runtime-sdk-versions.md#should-i-remove-a-version) to learn which SDKs and runtimes are safe to remove.</span></span>

> [!CAUTION]
> <span data-ttu-id="85f02-223">Tenha em mente as seguintes advertências:</span><span class="sxs-lookup"><span data-stu-id="85f02-223">Keep in mind the following caveats:</span></span>
>
>- <span data-ttu-id="85f02-224">Esta ferramenta pode desinstalar versões do .NET `global.json` Core SDK que são exigidas por arquivos em sua máquina.</span><span class="sxs-lookup"><span data-stu-id="85f02-224">This tool can uninstall versions of the .NET Core SDK that are required by `global.json` files on your machine.</span></span> <span data-ttu-id="85f02-225">Você pode reinstalar SDKs do Núcleo .NET na página [Download .NET Core.](https://dotnet.microsoft.com/download/dotnet-core)</span><span class="sxs-lookup"><span data-stu-id="85f02-225">You can reinstall .NET Core SDKs from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="85f02-226">Esta ferramenta pode desinstalar versões do tempo de execução do .NET Core que são exigidas por aplicativos dependentes de framework na sua máquina.</span><span class="sxs-lookup"><span data-stu-id="85f02-226">This tool can uninstall versions of the .NET Core runtime that are required by framework dependent applications on your machine.</span></span> <span data-ttu-id="85f02-227">Você pode reinstalar os tempos de execução do .NET Core a partir da página [Download .NET Core.](https://dotnet.microsoft.com/download/dotnet-core)</span><span class="sxs-lookup"><span data-stu-id="85f02-227">You can reinstall .NET Core runtimes from the [Download .NET Core](https://dotnet.microsoft.com/download/dotnet-core) page.</span></span>
>- <span data-ttu-id="85f02-228">Esta ferramenta pode desinstalar versões do .NET Core SDK e tempo de execução que o Visual Studio conta.</span><span class="sxs-lookup"><span data-stu-id="85f02-228">This tool can uninstall versions of the .NET Core SDK and runtime that Visual Studio relies on.</span></span> <span data-ttu-id="85f02-229">Se você interromper a instalação do Visual Studio, execute "Repair" no instalador do Visual Studio para voltar a um estado de trabalho.</span><span class="sxs-lookup"><span data-stu-id="85f02-229">If you break your Visual Studio installation, run "Repair" in the Visual Studio installer to get back to a working state.</span></span>

<span data-ttu-id="85f02-230">Por padrão, todos os comandos mantêm os SDKs do Núcleo .NET e os tempos de execução que podem ser exigidos pelo Visual Studio ou outros SDKs.</span><span class="sxs-lookup"><span data-stu-id="85f02-230">By default, all commands keep the .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs.</span></span> <span data-ttu-id="85f02-231">Esses SDKs e tempos de execução podem ser desinstalados `--force` listando-os explicitamente como argumentos ou usando a opção.</span><span class="sxs-lookup"><span data-stu-id="85f02-231">These SDKs and runtimes can be uninstalled by listing them explicitly as arguments or by using the `--force` option.</span></span>

<span data-ttu-id="85f02-232">A ferramenta requer elevação para desinstalar SDKs e tempos de execução do Núcleo .NET.</span><span class="sxs-lookup"><span data-stu-id="85f02-232">The tool requires elevation to uninstall .NET Core SDKs and runtimes.</span></span> <span data-ttu-id="85f02-233">Execute a ferramenta em um prompt `sudo` de comando administrador no Windows e com o macOS.</span><span class="sxs-lookup"><span data-stu-id="85f02-233">Run the tool in an Administrator command prompt on Windows and with `sudo` on macOS.</span></span> <span data-ttu-id="85f02-234">Os `dry-run` `whatif` comandos não requerem elevação.</span><span class="sxs-lookup"><span data-stu-id="85f02-234">The `dry-run` and `whatif` commands don't require elevation.</span></span>

<span data-ttu-id="85f02-235">**dotnet-core-desinstalar remover**</span><span class="sxs-lookup"><span data-stu-id="85f02-235">**dotnet-core-uninstall remove**</span></span>

#### <a name="synopsis"></a><span data-ttu-id="85f02-236">Sinopse</span><span class="sxs-lookup"><span data-stu-id="85f02-236">Synopsis</span></span>

```console
dotnet-core-uninstall remove [options] [<VERSION>...]
```

#### <a name="arguments"></a><span data-ttu-id="85f02-237">Argumentos</span><span class="sxs-lookup"><span data-stu-id="85f02-237">Arguments</span></span>

* **`VERSION`**

  <span data-ttu-id="85f02-238">A versão especificada para desinstalar.</span><span class="sxs-lookup"><span data-stu-id="85f02-238">The specified version to uninstall.</span></span> <span data-ttu-id="85f02-239">Você pode listar várias versões uma após a outra, separadas por espaços.</span><span class="sxs-lookup"><span data-stu-id="85f02-239">You may list several versions one after the other, separated by spaces.</span></span> <span data-ttu-id="85f02-240">Os arquivos de resposta também são suportados.</span><span class="sxs-lookup"><span data-stu-id="85f02-240">Response files are also supported.</span></span>

  > [!TIP]
  > <span data-ttu-id="85f02-241">Os arquivos de resposta são uma alternativa para colocar todas as versões na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="85f02-241">Response files are an alternative to placing all the versions on the command line.</span></span>
  > <span data-ttu-id="85f02-242">São arquivos de texto, normalmente com uma \*extensão .rsp, e cada versão é listada em uma linha separada.</span><span class="sxs-lookup"><span data-stu-id="85f02-242">They're text files, typically with a \*.rsp extension, and each version is listed on a separate line.</span></span>
  > <span data-ttu-id="85f02-243">Para especificar um `VERSION` arquivo de \@ resposta para o argumento, use o caractere imediatamente seguido pelo nome do arquivo de resposta.</span><span class="sxs-lookup"><span data-stu-id="85f02-243">To specify a response file for the `VERSION` argument, use the \@ character immediately followed by the response file name.</span></span>

#### <a name="options"></a><span data-ttu-id="85f02-244">Opções</span><span class="sxs-lookup"><span data-stu-id="85f02-244">Options</span></span>

## <a name="windows"></a>[<span data-ttu-id="85f02-245">Windows</span><span class="sxs-lookup"><span data-stu-id="85f02-245">Windows</span></span>](#tab/windows)

* **`--all`**

  <span data-ttu-id="85f02-246">Remove todos os SDKs do Núcleo .NET e tempos de execução.</span><span class="sxs-lookup"><span data-stu-id="85f02-246">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="85f02-247">Remove apenas os SDKs do Núcleo .NET e os tempos de execução com uma versão menor que a especificada.</span><span class="sxs-lookup"><span data-stu-id="85f02-247">Removes only the .NET Core SDKs and runtimes with a version smaller than the specified version.</span></span> <span data-ttu-id="85f02-248">A versão especificada permanece instalada.</span><span class="sxs-lookup"><span data-stu-id="85f02-248">The specified version remains installed.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="85f02-249">Remove todos os SDKs e tempos de execução do .NET Core, exceto as versões especificadas.</span><span class="sxs-lookup"><span data-stu-id="85f02-249">Removes all .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="85f02-250">Remove SDKs e tempos de execução do .NET Core, exceto a versão mais alta.</span><span class="sxs-lookup"><span data-stu-id="85f02-250">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="85f02-251">Remove SDKs do Núcleo .NET e tempos de execução substituídos por patches mais altos.</span><span class="sxs-lookup"><span data-stu-id="85f02-251">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="85f02-252">Esta opção protege global.json.</span><span class="sxs-lookup"><span data-stu-id="85f02-252">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="85f02-253">Remove SDKs do Núcleo .NET e tempos de execução marcados como visualizações.</span><span class="sxs-lookup"><span data-stu-id="85f02-253">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="85f02-254">Remove SDKs do Núcleo .NET e tempos de execução marcados como visualizações, exceto a visualização mais alta.</span><span class="sxs-lookup"><span data-stu-id="85f02-254">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--aspnet-runtime`**

  <span data-ttu-id="85f02-255">Remove apenas ASP.NET tempos de execução do Core.</span><span class="sxs-lookup"><span data-stu-id="85f02-255">Removes ASP.NET Core runtimes only.</span></span>

* **`--hosting-bundle`**

  <span data-ttu-id="85f02-256">Remove apenas o tempo de execução do .NET Core e os pacotes de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="85f02-256">Removes .NET Core runtime and hosting bundles only.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="85f02-257">Remove SDKs do Núcleo .NET e tempos `major.minor` de execução que correspondem à versão especificada.</span><span class="sxs-lookup"><span data-stu-id="85f02-257">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="85f02-258">Remove apenas os tempos de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="85f02-258">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="85f02-259">Remove apenas SDKs do Núcleo .NET.</span><span class="sxs-lookup"><span data-stu-id="85f02-259">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="85f02-260">Define o nível de verbosidade.</span><span class="sxs-lookup"><span data-stu-id="85f02-260">Sets the verbosity level.</span></span> <span data-ttu-id="85f02-261">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="85f02-261">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="85f02-262">O valor padrão é `normal`.</span><span class="sxs-lookup"><span data-stu-id="85f02-262">The default value is `normal`.</span></span>

* **`--x64`**

  <span data-ttu-id="85f02-263">Deve ser `--sdk`usado `--runtime`com `--aspnet-runtime` , e para remover sdks x64 ou tempos de execução.</span><span class="sxs-lookup"><span data-stu-id="85f02-263">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x64 SDKs or runtimes.</span></span>

* **`--x86`**

  <span data-ttu-id="85f02-264">Deve ser `--sdk`usado `--runtime`com `--aspnet-runtime` , e para remover sdks x86 ou tempos de execução.</span><span class="sxs-lookup"><span data-stu-id="85f02-264">Must be used with `--sdk`, `--runtime`, and `--aspnet-runtime` to remove x86 SDKs or runtimes.</span></span>

* <span data-ttu-id="85f02-265">**`-y, --yes`** Executa o comando sem exigir uma confirmação de sim ou não.</span><span class="sxs-lookup"><span data-stu-id="85f02-265">**`-y, --yes`** Executes the command without requiring a yes or no confirmation.</span></span>

* <span data-ttu-id="85f02-266">**`--force`** Força a remoção de versões que podem ser usadas pelo Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="85f02-266">**`--force`** Forces removal of versions that might be used by Visual Studio.</span></span>

<span data-ttu-id="85f02-267">Observações:</span><span class="sxs-lookup"><span data-stu-id="85f02-267">Notes:</span></span>

1. <span data-ttu-id="85f02-268">Exatamente um `--sdk` `--runtime`dos `--aspnet-runtime`, `--hosting-bundle` , e é necessário.</span><span class="sxs-lookup"><span data-stu-id="85f02-268">Exactly one of `--sdk`, `--runtime`, `--aspnet-runtime`, and `--hosting-bundle` is required.</span></span>
2. <span data-ttu-id="85f02-269">`--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , , , , , e são exclusivos.</span><span class="sxs-lookup"><span data-stu-id="85f02-269">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>
3. <span data-ttu-id="85f02-270">Se `--x64` `--x86` ou não forem especificados, então tanto x64 quanto x86 serão removidos.</span><span class="sxs-lookup"><span data-stu-id="85f02-270">If `--x64` or `--x86` aren't specified, then both x64 and x86 will be removed.</span></span>

## <a name="macos"></a>[<span data-ttu-id="85f02-271">macOS</span><span class="sxs-lookup"><span data-stu-id="85f02-271">macOS</span></span>](#tab/macos)

* **`--all`**

  <span data-ttu-id="85f02-272">Remove todos os SDKs do Núcleo .NET e tempos de execução.</span><span class="sxs-lookup"><span data-stu-id="85f02-272">Removes all .NET Core SDKs and runtimes.</span></span>

* **`--all-below <VERSION>`**

  <span data-ttu-id="85f02-273">Remove SDKs do Núcleo .NET e tempos de execução abaixo da versão especificada.</span><span class="sxs-lookup"><span data-stu-id="85f02-273">Removes .NET Core SDKs and runtimes below the specified version.</span></span> <span data-ttu-id="85f02-274">A versão especificada permanecerá.</span><span class="sxs-lookup"><span data-stu-id="85f02-274">The specified version will remain.</span></span>

* **`--all-but <VERSIONS>`**

  <span data-ttu-id="85f02-275">Remove SDKs e tempos de execução do .NET Core, exceto as versões especificadas.</span><span class="sxs-lookup"><span data-stu-id="85f02-275">Removes .NET Core SDKs and runtimes, except those versions specified.</span></span>

* **`--all-but-latest`**

  <span data-ttu-id="85f02-276">Remove SDKs e tempos de execução do .NET Core, exceto a versão mais alta.</span><span class="sxs-lookup"><span data-stu-id="85f02-276">Removes .NET Core SDKs and runtimes, except the one highest version.</span></span>

* **`--all-lower-patches`**

  <span data-ttu-id="85f02-277">Remove SDKs do Núcleo .NET e tempos de execução substituídos por patches mais altos.</span><span class="sxs-lookup"><span data-stu-id="85f02-277">Removes .NET Core SDKs and runtimes superseded by higher patches.</span></span> <span data-ttu-id="85f02-278">Esta opção protege global.json.</span><span class="sxs-lookup"><span data-stu-id="85f02-278">This option protects global.json.</span></span>

* **`--all-previews`**

  <span data-ttu-id="85f02-279">Remove SDKs do Núcleo .NET e tempos de execução marcados como visualizações.</span><span class="sxs-lookup"><span data-stu-id="85f02-279">Removes .NET Core SDKs and runtimes marked as previews.</span></span>

* **`--all-previews-but-latest`**

  <span data-ttu-id="85f02-280">Remove SDKs do Núcleo .NET e tempos de execução marcados como visualizações, exceto a visualização mais alta.</span><span class="sxs-lookup"><span data-stu-id="85f02-280">Removes .NET Core SDKs and runtimes marked as previews except the one highest preview.</span></span>

* **`--major-minor <MAJOR_MINOR>`**

  <span data-ttu-id="85f02-281">Remove SDKs do Núcleo .NET e tempos `major.minor` de execução que correspondem à versão especificada.</span><span class="sxs-lookup"><span data-stu-id="85f02-281">Removes .NET Core SDKs and runtimes that match the specified `major.minor` version.</span></span>

* **`--runtime`**

  <span data-ttu-id="85f02-282">Remove apenas os tempos de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="85f02-282">Removes .NET Core runtimes only.</span></span>

* **`--sdk`**

  <span data-ttu-id="85f02-283">Remove apenas SDKs do Núcleo .NET.</span><span class="sxs-lookup"><span data-stu-id="85f02-283">Removes .NET Core SDKs only.</span></span>

* **`-v, --verbosity <LEVEL>`**

  <span data-ttu-id="85f02-284">Define o nível de verbosidade.</span><span class="sxs-lookup"><span data-stu-id="85f02-284">Sets the verbosity level.</span></span> <span data-ttu-id="85f02-285">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="85f02-285">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="85f02-286">O valor padrão é `normal`.</span><span class="sxs-lookup"><span data-stu-id="85f02-286">The default value is `normal`.</span></span>

* <span data-ttu-id="85f02-287">**`-y, --yes`** Executa o comando sem exigir confirmação de Y/N.</span><span class="sxs-lookup"><span data-stu-id="85f02-287">**`-y, --yes`** Executes the command without requiring Y/N confirmation.</span></span>
  
* <span data-ttu-id="85f02-288">**`--force`** Força a remoção de versões que podem ser usadas pelo Visual Studio ou SDKs.</span><span class="sxs-lookup"><span data-stu-id="85f02-288">**`--force`** Forces removal of versions that might be used by Visual Studio or SDKs.</span></span>

<span data-ttu-id="85f02-289">Observações:</span><span class="sxs-lookup"><span data-stu-id="85f02-289">Notes:</span></span>

1. <span data-ttu-id="85f02-290">Exatamente um `--sdk` `--runtime` dos mais necessários.</span><span class="sxs-lookup"><span data-stu-id="85f02-290">Exactly one of `--sdk` and `--runtime` is required.</span></span>
2. <span data-ttu-id="85f02-291">`--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , , , , , e são exclusivos.</span><span class="sxs-lookup"><span data-stu-id="85f02-291">`--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`, and `[<VERSION>...]` are exclusive.</span></span>

---

#### <a name="examples"></a><span data-ttu-id="85f02-292">Exemplos</span><span class="sxs-lookup"><span data-stu-id="85f02-292">Examples</span></span>

> [!NOTE]
> <span data-ttu-id="85f02-293">Por padrão, os SDKs do Núcleo .NET e os tempos de execução que podem ser exigidos pelo Visual Studio ou outros SDKs são mantidos.</span><span class="sxs-lookup"><span data-stu-id="85f02-293">By default, .NET Core SDKs and runtimes that may be required by Visual Studio or other SDKs are kept.</span></span> <span data-ttu-id="85f02-294">Nos exemplos a seguir, alguns dos SDKs e tempos de execução especificados podem permanecer, dependendo do estado da máquina.</span><span class="sxs-lookup"><span data-stu-id="85f02-294">In the following examples, some of the specified SDKs and runtimes may remain, depending on the state of the machine.</span></span> <span data-ttu-id="85f02-295">Para remover todos os SDKs e tempos de execução, liste-os explicitamente como argumentos ou use a `--force` opção.</span><span class="sxs-lookup"><span data-stu-id="85f02-295">To remove all SDKs and runtimes, list them explicitly as arguments or use the `--force` option.</span></span>

* <span data-ttu-id="85f02-296">Remova todos os tempos de `3.0.0-preview6-27804-01` execução do .NET Core, exceto a versão, sem exigir a confirmação de Y/N:</span><span class="sxs-lookup"><span data-stu-id="85f02-296">Remove all .NET Core runtimes except the version `3.0.0-preview6-27804-01` without requiring Y/N confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --all-but 3.0.0-preview6-27804-01 --runtime --yes
  ```

* <span data-ttu-id="85f02-297">Remova todos os SDKs .NET Core 1.1 sem exigir confirmação de Y/n:</span><span class="sxs-lookup"><span data-stu-id="85f02-297">Remove all .NET Core 1.1 SDKs without requiring Y/n confirmation:</span></span>

  ```console
  dotnet-core-uninstall remove --sdk --major-minor 1.1 -y
  ```

* <span data-ttu-id="85f02-298">Remova o SDK .NET Core 1.1.11 sem saída do console:</span><span class="sxs-lookup"><span data-stu-id="85f02-298">Remove the .NET Core 1.1.11 SDK with no console output:</span></span>

  ```console
  dotnet-core-uninstall remove 1.1.11 --sdk --yes --verbosity q
  ```

* <span data-ttu-id="85f02-299">Remova todos os SDKs do Núcleo .NET que podem ser removidos com segurança por esta ferramenta:</span><span class="sxs-lookup"><span data-stu-id="85f02-299">Remove all .NET Core SDKs that can safely be removed by this tool:</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk
  ```

* <span data-ttu-id="85f02-300">Remova todos os SDKs do Núcleo .NET que podem ser removidos por esta ferramenta, incluindo os SDKs que podem ser exigidos pelo Visual Studio (não recomendado):</span><span class="sxs-lookup"><span data-stu-id="85f02-300">Remove all .NET Core SDKs that can be removed by this tool, including those SDKs that may be required by Visual Studio (not recommended):</span></span>

  ```console
  dotnet-core-uninstall remove --all --sdk --force
  ```

* <span data-ttu-id="85f02-301">Remova todos os SDKs do Núcleo .NET especificados no arquivo de resposta`versions.rsp`</span><span class="sxs-lookup"><span data-stu-id="85f02-301">Remove all .NET Core SDKs that are specified in the response file `versions.rsp`</span></span>

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  <span data-ttu-id="85f02-302">O conteúdo de *versions.rsp* é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="85f02-302">The content of *versions.rsp* is as follows:</span></span>
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a><span data-ttu-id="85f02-303">Passo 4 - Excluir a pasta de recuo NuGet (opcional)</span><span class="sxs-lookup"><span data-stu-id="85f02-303">Step 4 - Delete the NuGet fallback folder (optional)</span></span>

<span data-ttu-id="85f02-304">Em alguns casos, você `NuGetFallbackFolder` não precisa mais e pode querer excluí-lo.</span><span class="sxs-lookup"><span data-stu-id="85f02-304">In some cases, you no longer need the `NuGetFallbackFolder` and may wish to delete it.</span></span> <span data-ttu-id="85f02-305">Para obter mais informações sobre a exclusão desta pasta, consulte [Remover a pasta NuGetFallback](../versions/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span><span class="sxs-lookup"><span data-stu-id="85f02-305">For more information about deleting this folder, see [Remove the NuGetFallbackFolder](../versions/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).</span></span>

## <a name="uninstall-the-tool"></a><span data-ttu-id="85f02-306">Desinstale a ferramenta</span><span class="sxs-lookup"><span data-stu-id="85f02-306">Uninstall the tool</span></span>

## <a name="windows"></a>[<span data-ttu-id="85f02-307">Windows</span><span class="sxs-lookup"><span data-stu-id="85f02-307">Windows</span></span>](#tab/windows)

1. <span data-ttu-id="85f02-308">Abra **adicionar ou remover programas**.</span><span class="sxs-lookup"><span data-stu-id="85f02-308">Open **Add or Remove Programs**.</span></span>
2. <span data-ttu-id="85f02-309">Pesquise `Microsoft .NET Core SDK Uninstall Tool`.</span><span class="sxs-lookup"><span data-stu-id="85f02-309">Search for `Microsoft .NET Core SDK Uninstall Tool`.</span></span>
3. <span data-ttu-id="85f02-310">Selecionar **Desinstalar**.</span><span class="sxs-lookup"><span data-stu-id="85f02-310">Select **Uninstall**.</span></span>

## <a name="macos"></a>[<span data-ttu-id="85f02-311">macOS</span><span class="sxs-lookup"><span data-stu-id="85f02-311">macOS</span></span>](#tab/macos)

<span data-ttu-id="85f02-312">Exclua o arquivo *dotnet-core-uninstall.tar.gz* baixado do diretório onde ele foi instalado.</span><span class="sxs-lookup"><span data-stu-id="85f02-312">Delete the downloaded *dotnet-core-uninstall.tar.gz* file from the directory where it was installed.</span></span> <span data-ttu-id="85f02-313">Se você descompactou o conteúdo deste arquivo em outro diretório, certifique-se de excluir esse conteúdo também.</span><span class="sxs-lookup"><span data-stu-id="85f02-313">If you unzipped the contents of this file into another directory, be sure to delete that content as well.</span></span>

---
