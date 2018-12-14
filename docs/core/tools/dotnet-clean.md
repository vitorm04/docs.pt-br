---
title: Comando dotnet clean – CLI do .NET Core
description: O comando dotnet clean limpa o diretório atual.
ms.date: 12/04/2018
ms.openlocfilehash: 9930d2905f234e7125f27367cda36aa85ae23b87
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53144449"
---
# <a name="dotnet-clean"></a><span data-ttu-id="3c79a-103">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="3c79a-103">dotnet clean</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="3c79a-104">Nome</span><span class="sxs-lookup"><span data-stu-id="3c79a-104">Name</span></span>

<span data-ttu-id="3c79a-105">`dotnet clean` – limpa a saída de um projeto.</span><span class="sxs-lookup"><span data-stu-id="3c79a-105">`dotnet clean` - Cleans the output of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3c79a-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="3c79a-106">Synopsis</span></span>

```
dotnet clean [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
dotnet clean [-h|--help]
```

## <a name="description"></a><span data-ttu-id="3c79a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="3c79a-107">Description</span></span>

<span data-ttu-id="3c79a-108">O comando `dotnet clean` limpará a saída da compilação anterior.</span><span class="sxs-lookup"><span data-stu-id="3c79a-108">The `dotnet clean` command cleans the output of the previous build.</span></span> <span data-ttu-id="3c79a-109">Ele é implementado como um [destino de MSBuild](/visualstudio/msbuild/msbuild-targets), para que o projeto seja avaliado durante a execução do comando.</span><span class="sxs-lookup"><span data-stu-id="3c79a-109">It's implemented as an [MSBuild target](/visualstudio/msbuild/msbuild-targets), so the project is evaluated when the command is run.</span></span> <span data-ttu-id="3c79a-110">Apenas as saídas criadas durante a compilação são limpas.</span><span class="sxs-lookup"><span data-stu-id="3c79a-110">Only the outputs created during the build are cleaned.</span></span> <span data-ttu-id="3c79a-111">As pastas de saídas intermediária (*obj*) e final (*bin*) serão limpas.</span><span class="sxs-lookup"><span data-stu-id="3c79a-111">Both intermediate (*obj*) and final output (*bin*) folders are cleaned.</span></span>

## <a name="arguments"></a><span data-ttu-id="3c79a-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="3c79a-112">Arguments</span></span>

`PROJECT`

<span data-ttu-id="3c79a-113">O projeto do MSBuild a ser limpo.</span><span class="sxs-lookup"><span data-stu-id="3c79a-113">The MSBuild project to clean.</span></span> <span data-ttu-id="3c79a-114">Se um arquivo de projeto não for especificado, o MSBuild pesquisará o diretório de trabalho atual em busca de um arquivo que tem uma extensão de arquivo que termina em *proj* e que usa esse arquivo.</span><span class="sxs-lookup"><span data-stu-id="3c79a-114">If a project file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="3c79a-115">Opções</span><span class="sxs-lookup"><span data-stu-id="3c79a-115">Options</span></span>

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="3c79a-116">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="3c79a-116">Defines the build configuration.</span></span> <span data-ttu-id="3c79a-117">O valor padrão é `Debug`.</span><span class="sxs-lookup"><span data-stu-id="3c79a-117">The default value is `Debug`.</span></span> <span data-ttu-id="3c79a-118">Essa opção só será exigida na limpeza se você especificá-la durante o momento do build.</span><span class="sxs-lookup"><span data-stu-id="3c79a-118">This option is only required when cleaning if you specified it during build time.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="3c79a-119">A [estrutura](../../standard/frameworks.md) que foi especificada no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="3c79a-119">The [framework](../../standard/frameworks.md) that was specified at build time.</span></span> <span data-ttu-id="3c79a-120">A estrutura precisa ser definida no [arquivo de projeto](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="3c79a-120">The framework must be defined in the [project file](csproj.md).</span></span> <span data-ttu-id="3c79a-121">Se você especificou a estrutura no momento da compilação, especifique a estrutura ao limpar.</span><span class="sxs-lookup"><span data-stu-id="3c79a-121">If you specified the framework at build time, you must specify the framework when cleaning.</span></span>

* **`-h|--help`**

  <span data-ttu-id="3c79a-122">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="3c79a-122">Prints out a short help for the command.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="3c79a-123">O diretório no qual as saídas compiladas são colocadas.</span><span class="sxs-lookup"><span data-stu-id="3c79a-123">Directory in which the build outputs are placed.</span></span> <span data-ttu-id="3c79a-124">Especifique a opção `-f|--framework <FRAMEWORK>` com a opção de diretório de saída se você tiver especificado a estrutura durante a compilação do projeto.</span><span class="sxs-lookup"><span data-stu-id="3c79a-124">Specify the `-f|--framework <FRAMEWORK>` switch with the output directory switch if you specified the framework when the project was built.</span></span>

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="3c79a-125">Limpa a pasta de saída do tempo de execução especificado.</span><span class="sxs-lookup"><span data-stu-id="3c79a-125">Cleans the output folder of the specified runtime.</span></span> <span data-ttu-id="3c79a-126">Isso é usado quando uma [implantação autocontida](../deploying/index.md#self-contained-deployments-scd) foi criada.</span><span class="sxs-lookup"><span data-stu-id="3c79a-126">This is used when a [self-contained deployment](../deploying/index.md#self-contained-deployments-scd) was created.</span></span> <span data-ttu-id="3c79a-127">Opção disponível desde o SDK do .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="3c79a-127">Option available since .NET Core 2.0 SDK.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="3c79a-128">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="3c79a-128">Sets the verbosity level of the command.</span></span> <span data-ttu-id="3c79a-129">Os níveis permitidos são q[uiet], m[inimal], n[ormal], d[etailed] e diag[nostic].</span><span class="sxs-lookup"><span data-stu-id="3c79a-129">Allowed levels are q[uiet], m[inimal], n[ormal], d[etailed], and diag[nostic].</span></span>

## <a name="examples"></a><span data-ttu-id="3c79a-130">Exemplos</span><span class="sxs-lookup"><span data-stu-id="3c79a-130">Examples</span></span>

* <span data-ttu-id="3c79a-131">Limpe uma compilação padrão do projeto:</span><span class="sxs-lookup"><span data-stu-id="3c79a-131">Clean a default build of the project:</span></span>

  ```console
  dotnet clean
  ```

* <span data-ttu-id="3c79a-132">Limpe um projeto compilado usando a configuração da Versão:</span><span class="sxs-lookup"><span data-stu-id="3c79a-132">Clean a project built using the Release configuration:</span></span>

  ```console
  dotnet clean --configuration Release
  ```