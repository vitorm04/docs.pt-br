---
title: Comando dotnet clean
description: O comando dotnet clean limpa o diretório atual.
ms.date: 06/26/2019
ms.openlocfilehash: 113bc076b9f14a471c631801fe4a7cb1e044a411
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168053"
---
# <a name="dotnet-clean"></a><span data-ttu-id="c8c8f-103">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="c8c8f-103">dotnet clean</span></span>

<span data-ttu-id="c8c8f-104">**Este tópico aplica-se a: ✓** SDK do .NET Core 1.x e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="c8c8f-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="c8c8f-105">Nome</span><span class="sxs-lookup"><span data-stu-id="c8c8f-105">Name</span></span>

<span data-ttu-id="c8c8f-106">`dotnet clean` – limpa a saída de um projeto.</span><span class="sxs-lookup"><span data-stu-id="c8c8f-106">`dotnet clean` - Cleans the output of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c8c8f-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="c8c8f-107">Synopsis</span></span>

```console
dotnet clean [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--interactive] 
    [--nologo] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```

## <a name="description"></a><span data-ttu-id="c8c8f-108">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="c8c8f-108">Description</span></span>

<span data-ttu-id="c8c8f-109">O comando `dotnet clean` limpará a saída da compilação anterior.</span><span class="sxs-lookup"><span data-stu-id="c8c8f-109">The `dotnet clean` command cleans the output of the previous build.</span></span> <span data-ttu-id="c8c8f-110">Ele é implementado como um [destino de MSBuild](/visualstudio/msbuild/msbuild-targets), para que o projeto seja avaliado durante a execução do comando.</span><span class="sxs-lookup"><span data-stu-id="c8c8f-110">It's implemented as an [MSBuild target](/visualstudio/msbuild/msbuild-targets), so the project is evaluated when the command is run.</span></span> <span data-ttu-id="c8c8f-111">Apenas as saídas criadas durante a compilação são limpas.</span><span class="sxs-lookup"><span data-stu-id="c8c8f-111">Only the outputs created during the build are cleaned.</span></span> <span data-ttu-id="c8c8f-112">As pastas de saídas intermediária (*obj*) e final (*bin*) serão limpas.</span><span class="sxs-lookup"><span data-stu-id="c8c8f-112">Both intermediate (*obj*) and final output (*bin*) folders are cleaned.</span></span>

## <a name="arguments"></a><span data-ttu-id="c8c8f-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="c8c8f-113">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="c8c8f-114">O projeto do MSBuild ou a solução para limpar.</span><span class="sxs-lookup"><span data-stu-id="c8c8f-114">The MSBuild project or solution to clean.</span></span> <span data-ttu-id="c8c8f-115">Se um arquivo de solução ou projeto não for especificado, o MSBuild pesquisará no diretório de trabalho atual por um arquivo que tenha uma extensão terminada em *proj* ou *sln* e usará esse arquivo.</span><span class="sxs-lookup"><span data-stu-id="c8c8f-115">If a project or solution file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* or *sln*, and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="c8c8f-116">Opções</span><span class="sxs-lookup"><span data-stu-id="c8c8f-116">Options</span></span>

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="c8c8f-117">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="c8c8f-117">Defines the build configuration.</span></span> <span data-ttu-id="c8c8f-118">O valor padrão é `Debug`.</span><span class="sxs-lookup"><span data-stu-id="c8c8f-118">The default value is `Debug`.</span></span> <span data-ttu-id="c8c8f-119">Essa opção só será exigida na limpeza se você especificá-la durante o momento do build.</span><span class="sxs-lookup"><span data-stu-id="c8c8f-119">This option is only required when cleaning if you specified it during build time.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c8c8f-120">A [estrutura](../../standard/frameworks.md) que foi especificada no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="c8c8f-120">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="c8c8f-121">A estrutura precisa ser definida no [arquivo de projeto](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="c8c8f-121">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="c8c8f-122">Se você especificou a estrutura no momento da compilação, especifique a estrutura ao limpar.</span><span class="sxs-lookup"><span data-stu-id="c8c8f-122">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

* **`-h|--help`**

  <span data-ttu-id="c8c8f-123">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="c8c8f-123">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="c8c8f-124">Permite que o comando pare e aguarde entrada ou ação do usuário.</span><span class="sxs-lookup"><span data-stu-id="c8c8f-124">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="c8c8f-125">Por exemplo, para concluir a autenticação.</span><span class="sxs-lookup"><span data-stu-id="c8c8f-125">For example, to complete authentication.</span></span> <span data-ttu-id="c8c8f-126">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="c8c8f-126">Available since .NET Core 3.0 SDK.</span></span>

* **`--nologo`**

  <span data-ttu-id="c8c8f-127">Não exibe a faixa de inicialização nem a mensagem de direitos autorais.</span><span class="sxs-lookup"><span data-stu-id="c8c8f-127">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="c8c8f-128">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="c8c8f-128">Available since .NET Core 3.0 SDK.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="c8c8f-129">O diretório que contém os artefatos de build a serem limpos.</span><span class="sxs-lookup"><span data-stu-id="c8c8f-129">The directory that contains the build artifacts to clean.</span></span> <span data-ttu-id="c8c8f-130">Especifique a opção `-f|--framework <FRAMEWORK>` com a opção de diretório de saída se você tiver especificado a estrutura durante a compilação do projeto.</span><span class="sxs-lookup"><span data-stu-id="c8c8f-130">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="c8c8f-131">Limpa a pasta de saída do tempo de execução especificado.</span><span class="sxs-lookup"><span data-stu-id="c8c8f-131">Cleans the output folder of the specified runtime.</span></span> <span data-ttu-id="c8c8f-132">Isso é usado quando uma [implantação autocontida](../deploying/index.md#self-contained-deployments-scd) foi criada.</span><span class="sxs-lookup"><span data-stu-id="c8c8f-132">This is used when a [self-contained deployment](../deploying/index.md#self-contained-deployments-scd) was created.</span></span> <span data-ttu-id="c8c8f-133">Opção disponível desde o SDK do .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="c8c8f-133">Option available since .NET Core 2.0 SDK.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="c8c8f-134">Define o nível de detalhamento do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="c8c8f-134">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="c8c8f-135">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="c8c8f-135">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="c8c8f-136">O padrão é `normal`.</span><span class="sxs-lookup"><span data-stu-id="c8c8f-136">The default is `normal`.</span></span>

## <a name="examples"></a><span data-ttu-id="c8c8f-137">Exemplos</span><span class="sxs-lookup"><span data-stu-id="c8c8f-137">Examples</span></span>

* <span data-ttu-id="c8c8f-138">Limpe uma compilação padrão do projeto:</span><span class="sxs-lookup"><span data-stu-id="c8c8f-138">Clean a default build of the project:</span></span>

  ```console
  dotnet clean
  ```

* <span data-ttu-id="c8c8f-139">Limpe um projeto compilado usando a configuração da Versão:</span><span class="sxs-lookup"><span data-stu-id="c8c8f-139">Clean a project built using the Release configuration:</span></span>

  ```console
  dotnet clean --configuration Release
  ```
