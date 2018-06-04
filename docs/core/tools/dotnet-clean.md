---
title: Comando dotnet clean – CLI do .NET Core
description: O comando dotnet clean limpa o diretório atual.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: 9e68781fe00590f3c8d429631a3f72d525d29fa9
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34697025"
---
# <a name="dotnet-clean"></a><span data-ttu-id="1792f-103">dotnet-clean</span><span class="sxs-lookup"><span data-stu-id="1792f-103">dotnet-clean</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="1792f-104">Nome</span><span class="sxs-lookup"><span data-stu-id="1792f-104">Name</span></span>

<span data-ttu-id="1792f-105">`dotnet clean` – limpa a saída de um projeto.</span><span class="sxs-lookup"><span data-stu-id="1792f-105">`dotnet clean` - Cleans the output of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="1792f-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="1792f-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="1792f-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="1792f-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="1792f-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="1792f-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-v|--verbosity]
dotnet clean [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="1792f-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="1792f-109">Description</span></span>

<span data-ttu-id="1792f-110">O comando `dotnet clean` limpará a saída da compilação anterior.</span><span class="sxs-lookup"><span data-stu-id="1792f-110">The `dotnet clean` command cleans the output of the previous build.</span></span> <span data-ttu-id="1792f-111">Ele é implementado como um [destino de MSBuild](/visualstudio/msbuild/msbuild-targets), para que o projeto seja avaliado durante a execução do comando.</span><span class="sxs-lookup"><span data-stu-id="1792f-111">It's implemented as an [MSBuild target](/visualstudio/msbuild/msbuild-targets), so the project is evaluated when the command is run.</span></span> <span data-ttu-id="1792f-112">Apenas as saídas criadas durante a compilação são limpas.</span><span class="sxs-lookup"><span data-stu-id="1792f-112">Only the outputs created during the build are cleaned.</span></span> <span data-ttu-id="1792f-113">As pastas de saídas intermediária (*obj*) e final (*bin*) serão limpas.</span><span class="sxs-lookup"><span data-stu-id="1792f-113">Both intermediate (*obj*) and final output (*bin*) folders are cleaned.</span></span>

## <a name="arguments"></a><span data-ttu-id="1792f-114">Arguments</span><span class="sxs-lookup"><span data-stu-id="1792f-114">Arguments</span></span>

`PROJECT`

<span data-ttu-id="1792f-115">O projeto do MSBuild a ser limpo.</span><span class="sxs-lookup"><span data-stu-id="1792f-115">The MSBuild project to clean.</span></span> <span data-ttu-id="1792f-116">Se um arquivo de projeto não for especificado, o MSBuild pesquisará o diretório de trabalho atual em busca de um arquivo que tem uma extensão de arquivo que termina em *proj* e que usa esse arquivo.</span><span class="sxs-lookup"><span data-stu-id="1792f-116">If a project file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="1792f-117">Opções</span><span class="sxs-lookup"><span data-stu-id="1792f-117">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="1792f-118">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="1792f-118">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="1792f-119">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="1792f-119">Defines the build configuration.</span></span> <span data-ttu-id="1792f-120">O valor padrão é `Debug`.</span><span class="sxs-lookup"><span data-stu-id="1792f-120">The default value is `Debug`.</span></span> <span data-ttu-id="1792f-121">Essa opção só será exigida na limpeza se você especificá-la durante o momento do build.</span><span class="sxs-lookup"><span data-stu-id="1792f-121">This option is only required when cleaning if you specified it during build time.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="1792f-122">A [estrutura](../../standard/frameworks.md) que foi especificada no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="1792f-122">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="1792f-123">A estrutura precisa ser definida no [arquivo de projeto](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="1792f-123">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="1792f-124">Se você especificou a estrutura no momento da compilação, especifique a estrutura ao limpar.</span><span class="sxs-lookup"><span data-stu-id="1792f-124">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

`-h|--help`

<span data-ttu-id="1792f-125">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="1792f-125">Prints out a short help for the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="1792f-126">O diretório no qual as saídas compiladas são colocadas.</span><span class="sxs-lookup"><span data-stu-id="1792f-126">Directory in which the build outputs are placed.</span></span> <span data-ttu-id="1792f-127">Especifique a opção `-f|--framework <FRAMEWORK>` com a opção de diretório de saída se você tiver especificado a estrutura durante a compilação do projeto.</span><span class="sxs-lookup"><span data-stu-id="1792f-127">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="1792f-128">Limpa a pasta de saída do tempo de execução especificado.</span><span class="sxs-lookup"><span data-stu-id="1792f-128">Cleans the output folder of the specified runtime.</span></span> <span data-ttu-id="1792f-129">Isso é usado quando uma [implantação autocontida](../deploying/index.md#self-contained-deployments-scd) foi criada.</span><span class="sxs-lookup"><span data-stu-id="1792f-129">This is used when a [self-contained deployment](../deploying/index.md#self-contained-deployments-scd) was created.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="1792f-130">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="1792f-130">Sets the verbosity level of the command.</span></span> <span data-ttu-id="1792f-131">Os níveis permitidos são q[uiet], m[inimal], n[ormal], d[etailed] e diag[nostic].</span><span class="sxs-lookup"><span data-stu-id="1792f-131">Allowed levels are q[uiet], m[inimal], n[ormal], d[etailed], and diag[nostic].</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="1792f-132">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="1792f-132">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="1792f-133">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="1792f-133">Defines the build configuration.</span></span> <span data-ttu-id="1792f-134">O valor padrão é `Debug`.</span><span class="sxs-lookup"><span data-stu-id="1792f-134">The default value is `Debug`.</span></span> <span data-ttu-id="1792f-135">Essa opção só será exigida na limpeza se você especificá-la durante o momento do build.</span><span class="sxs-lookup"><span data-stu-id="1792f-135">This option is only required when cleaning if you specified it during build time.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="1792f-136">A [estrutura](../../standard/frameworks.md) que foi especificada no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="1792f-136">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="1792f-137">A estrutura precisa ser definida no [arquivo de projeto](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="1792f-137">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="1792f-138">Se você especificou a estrutura no momento da compilação, especifique a estrutura ao limpar.</span><span class="sxs-lookup"><span data-stu-id="1792f-138">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

`-h|--help`

<span data-ttu-id="1792f-139">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="1792f-139">Prints out a short help for the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="1792f-140">O diretório no qual as saídas compiladas são colocadas.</span><span class="sxs-lookup"><span data-stu-id="1792f-140">Directory in which the build outputs are placed.</span></span> <span data-ttu-id="1792f-141">Especifique a opção `-f|--framework <FRAMEWORK>` com a opção de diretório de saída se você tiver especificado a estrutura durante a compilação do projeto.</span><span class="sxs-lookup"><span data-stu-id="1792f-141">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="1792f-142">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="1792f-142">Sets the verbosity level of the command.</span></span> <span data-ttu-id="1792f-143">Os níveis permitidos são q[uiet], m[inimal], n[ormal], d[etailed] e diag[nostic].</span><span class="sxs-lookup"><span data-stu-id="1792f-143">Allowed levels are q[uiet], m[inimal], n[ormal], d[etailed], and diag[nostic].</span></span>

---

## <a name="examples"></a><span data-ttu-id="1792f-144">Exemplos</span><span class="sxs-lookup"><span data-stu-id="1792f-144">Examples</span></span>

<span data-ttu-id="1792f-145">Limpe uma compilação padrão do projeto:</span><span class="sxs-lookup"><span data-stu-id="1792f-145">Clean a default build of the project:</span></span>

`dotnet clean`

<span data-ttu-id="1792f-146">Limpe um projeto compilado usando a configuração da Versão:</span><span class="sxs-lookup"><span data-stu-id="1792f-146">Clean a project built using the Release configuration:</span></span>

`dotnet clean --configuration Release`
