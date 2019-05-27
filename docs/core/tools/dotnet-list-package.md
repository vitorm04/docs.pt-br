---
title: Comando dotnet list package
description: O comando 'dotnet list package' fornece uma opção conveniente para listar as referências de pacote de um projeto ou solução.
ms.date: 04/09/2019
ms.openlocfilehash: 88ef3302a955eadc4167384312e4eb721dd496fb
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65631760"
---
# <a name="dotnet-list-package"></a><span data-ttu-id="cf264-103">dotnet list package</span><span class="sxs-lookup"><span data-stu-id="cf264-103">dotnet list package</span></span>

[!INCLUDE [topic-appliesto-net-core-22plus](../../../includes/topic-appliesto-net-core-22plus.md)]

## <a name="name"></a><span data-ttu-id="cf264-104">Nome</span><span class="sxs-lookup"><span data-stu-id="cf264-104">Name</span></span>

<span data-ttu-id="cf264-105">`dotnet list package` – Lista as referências de pacote para um projeto ou solução.</span><span class="sxs-lookup"><span data-stu-id="cf264-105">`dotnet list package` - Lists the package references for a project or solution.</span></span>

## <a name="synopsis"></a><span data-ttu-id="cf264-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="cf264-106">Synopsis</span></span>

```
dotnet list [<PROJECT | SOLUTION>] package [--config] [--framework] [--highest-minor] [--highest-patch] 
   [--include-prerelease] [--include-transitive] [--outdated] [--source]
dotnet list package [-h|--help]
```

## <a name="description"></a><span data-ttu-id="cf264-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="cf264-107">Description</span></span>

<span data-ttu-id="cf264-108">O comando `dotnet list package` fornece uma opção conveniente para listar todas as referências de pacotes do NuGet para um projeto específico ou uma solução.</span><span class="sxs-lookup"><span data-stu-id="cf264-108">The `dotnet list package` command provides a convenient option to list all NuGet package references for a specific project or a solution.</span></span> <span data-ttu-id="cf264-109">Primeiro, você precisa criar o projeto para ter os recursos necessários para que esse comando seja processado.</span><span class="sxs-lookup"><span data-stu-id="cf264-109">You first need to build the project in order to have the assets needed for this command to process.</span></span> <span data-ttu-id="cf264-110">O exemplo a seguir mostra a saída do comando `dotnet list package` para o projeto [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis):</span><span class="sxs-lookup"><span data-stu-id="cf264-110">The following example shows the output of the `dotnet list package` command for the [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) project:</span></span>

```output
Project 'SentimentAnalysis' has the following package references
   [netcoreapp2.1]:
   Top-level Package               Requested   Resolved
   > Microsoft.ML                  0.11.0      0.11.0
   > Microsoft.NETCore.App   (A)   [2.1.0, )   2.1.0

(A) : Auto-referenced package.
```

<span data-ttu-id="cf264-111">A coluna **Requested** refere-se à versão do pacote especificada no arquivo de projeto e pode ser um intervalo.</span><span class="sxs-lookup"><span data-stu-id="cf264-111">The **Requested** column refers to the package version specified in the project file and can be a range.</span></span> <span data-ttu-id="cf264-112">A coluna **Resolved** lista a versão que o projeto está usando atualmente e é sempre um valor único.</span><span class="sxs-lookup"><span data-stu-id="cf264-112">The **Resolved** column lists the version that the project is currently using and is always a single value.</span></span> <span data-ttu-id="cf264-113">Os pacotes que exibem um `(A)` ao lado de seus nomes representam [referências de pacotes implícitas](csproj.md#implicit-package-references) que são inferidas das configurações do seu projeto (tipo `Sdk`, propriedade `<TargetFramework>` ou `<TargetFrameworks>`, etc.)</span><span class="sxs-lookup"><span data-stu-id="cf264-113">The packages displaying an `(A)` right next to their names represent [implicit package references](csproj.md#implicit-package-references) that are inferred from your project settings (`Sdk` type, `<TargetFramework>` or `<TargetFrameworks>` property, etc.)</span></span>

<span data-ttu-id="cf264-114">Use a opção `--outdated` para descobrir se existem versões mais recentes dos pacotes que você está usando em seus projetos.</span><span class="sxs-lookup"><span data-stu-id="cf264-114">Use the `--outdated` option to find out if there are newer versions available of the packages you're using in your projects.</span></span> <span data-ttu-id="cf264-115">Por padrão, `--outdated` lista os pacotes estáveis mais recentes, a menos que a versão resolvida também seja uma versão de pré-lançamento.</span><span class="sxs-lookup"><span data-stu-id="cf264-115">By default, `--outdated` lists the latest stable packages unless the resolved version is also a prerelease version.</span></span> <span data-ttu-id="cf264-116">Para incluir versões de pré-lançamento ao listar versões mais recentes, especifique também a opção `--include-prerelease`.</span><span class="sxs-lookup"><span data-stu-id="cf264-116">To include prerelease versions when listing newer versions, also specify the `--include-prerelease` option.</span></span> <span data-ttu-id="cf264-117">Os exemplos a seguir mostram a saída do comando `dotnet list package --outdated --include-prerelease` para o mesmo projeto do exemplo anterior:</span><span class="sxs-lookup"><span data-stu-id="cf264-117">The following examples shows the output of the `dotnet list package --outdated --include-prerelease` command for the same project as the previous example:</span></span>

```output
The following sources were used:
   https://api.nuget.org/v3/index.json

Project `SentimentAnalysis` has the following updates to its packages
   [netcoreapp2.1]:
   Top-level Package      Requested   Resolved   Latest
   > Microsoft.ML         0.11.0      0.11.0     1.0.0-preview
```

<span data-ttu-id="cf264-118">Se você precisa descobrir se seu projeto tem dependências transitivas, use a opção `--include-transitive`.</span><span class="sxs-lookup"><span data-stu-id="cf264-118">If you need to find out whether your project has transitive dependencies, use the `--include-transitive` option.</span></span> <span data-ttu-id="cf264-119">Dependências transitivas ocorrem quando você adiciona um pacote ao seu projeto que, por sua vez, depende de outro pacote.</span><span class="sxs-lookup"><span data-stu-id="cf264-119">Transitive dependencies occur when you add a package to your project that in turn relies on another package.</span></span> <span data-ttu-id="cf264-120">O exemplo a seguir mostra a saída da execução do comando `dotnet list package --include-transitive` para o projeto [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin), que exibe os pacotes de nível superior e os pacotes dos quais eles dependem:</span><span class="sxs-lookup"><span data-stu-id="cf264-120">The following example shows the output from running the `dotnet list package --include-transitive` command for the [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) project, which displays top-level packages and the packages they depend on:</span></span>

```output
Project 'HelloPlugin' has the following package references
   [netcoreapp3.0]:
   Top-level Package                      Requested                    Resolved
   > Microsoft.NETCore.Platforms    (A)   [3.0.0-preview3.19128.7, )   3.0.0-preview3.19128.7
   > Microsoft.WindowsDesktop.App   (A)   [3.0.0-preview3-27504-2, )   3.0.0-preview3-27504-2

   Transitive Package               Resolved
   > Microsoft.NETCore.Targets      2.0.0
   > PluginBase                     1.0.0

(A) : Auto-referenced package.
```

## <a name="arguments"></a><span data-ttu-id="cf264-121">Arguments</span><span class="sxs-lookup"><span data-stu-id="cf264-121">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="cf264-122">O arquivo de projeto ou solução para operar.</span><span class="sxs-lookup"><span data-stu-id="cf264-122">The project or solution file to operate on.</span></span> <span data-ttu-id="cf264-123">Se não for especificado, o comando pesquisará um no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="cf264-123">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="cf264-124">Se mais de uma solução ou projeto for encontrado, um erro será lançado.</span><span class="sxs-lookup"><span data-stu-id="cf264-124">If more than one solution or project is found, an error is thrown.</span></span>

## <a name="options"></a><span data-ttu-id="cf264-125">Opções</span><span class="sxs-lookup"><span data-stu-id="cf264-125">Options</span></span>

* **`--config <SOURCE>`**

  <span data-ttu-id="cf264-126">A fontes do NuGet a serem usadas ao procurar pacotes mais novos.</span><span class="sxs-lookup"><span data-stu-id="cf264-126">The NuGet sources to use when searching for newer packages.</span></span> <span data-ttu-id="cf264-127">Requer a opção `--outdated`.</span><span class="sxs-lookup"><span data-stu-id="cf264-127">Requires the `--outdated` option.</span></span>

* **`--framework <FRAMEWORK>`**

  <span data-ttu-id="cf264-128">Exibe apenas os pacotes aplicáveis para a [estrutura de destino](../../standard/frameworks.md) especificada.</span><span class="sxs-lookup"><span data-stu-id="cf264-128">Displays only the packages applicable for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="cf264-129">Para especificar várias estruturas, repita a opção várias vezes.</span><span class="sxs-lookup"><span data-stu-id="cf264-129">To specify multiple frameworks, repeat the option multiple times.</span></span> <span data-ttu-id="cf264-130">Por exemplo: `--framework netcoreapp2.2 --framework netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="cf264-130">For example: `--framework netcoreapp2.2 --framework netstandard2.0`.</span></span>

* **`-h|--help`**

  <span data-ttu-id="cf264-131">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="cf264-131">Prints out a short help for the command.</span></span>

* **`--highest-minor`**

  <span data-ttu-id="cf264-132">Ao procurar pacotes mais novos, considerar apenas os pacotes com um número de versão principal correspondente.</span><span class="sxs-lookup"><span data-stu-id="cf264-132">Considers only the packages with a matching major version number when searching for newer packages.</span></span> <span data-ttu-id="cf264-133">Requer a opção `--outdated`.</span><span class="sxs-lookup"><span data-stu-id="cf264-133">Requires the `--outdated` option.</span></span>

* **`--highest-patch`**

  <span data-ttu-id="cf264-134">Ao procurar pacotes mais novos, considerar apenas os pacotes com números de versão principais e secundários correspondentes.</span><span class="sxs-lookup"><span data-stu-id="cf264-134">Considers only the packages with a matching major and minor version numbers when searching for newer packages.</span></span> <span data-ttu-id="cf264-135">Requer a opção `--outdated`.</span><span class="sxs-lookup"><span data-stu-id="cf264-135">Requires the `--outdated` option.</span></span>

* **`--include-prerelease`**

  <span data-ttu-id="cf264-136">Ao procurar pacotes mais novos, considere pacotes com versões de pré-lançamento.</span><span class="sxs-lookup"><span data-stu-id="cf264-136">Considers packages with prerelease versions when searching for newer packages.</span></span> <span data-ttu-id="cf264-137">Requer a opção `--outdated`.</span><span class="sxs-lookup"><span data-stu-id="cf264-137">Requires the `--outdated` option.</span></span>

* **`--include-transitive`**

  <span data-ttu-id="cf264-138">Lista pacotes transitivos, além dos pacotes de nível superior.</span><span class="sxs-lookup"><span data-stu-id="cf264-138">Lists transitive packages, in addition to the top-level packages.</span></span> <span data-ttu-id="cf264-139">Ao especificar essa opção, você obtém uma lista de pacotes dos quais os pacotes de nível superior dependem.</span><span class="sxs-lookup"><span data-stu-id="cf264-139">When specifying this option, you get a list of packages that the top-level packages depend on.</span></span>

* **`--outdated`**

  <span data-ttu-id="cf264-140">Lista os pacotes que têm as versões mais recentes disponíveis.</span><span class="sxs-lookup"><span data-stu-id="cf264-140">Lists packages that have newer versions available.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="cf264-141">A fontes do NuGet a serem usadas ao procurar pacotes mais novos.</span><span class="sxs-lookup"><span data-stu-id="cf264-141">The NuGet sources to use when searching for newer packages.</span></span> <span data-ttu-id="cf264-142">Requer a opção `--outdated`.</span><span class="sxs-lookup"><span data-stu-id="cf264-142">Requires the `--outdated` option.</span></span>

## <a name="examples"></a><span data-ttu-id="cf264-143">Exemplos</span><span class="sxs-lookup"><span data-stu-id="cf264-143">Examples</span></span>

* <span data-ttu-id="cf264-144">Listar referências de pacote de um projeto específico:</span><span class="sxs-lookup"><span data-stu-id="cf264-144">List package references of a specific project:</span></span>

  ```console
  dotnet list SentimentAnalysis.csproj package
  ```

* <span data-ttu-id="cf264-145">Listar referências de pacote com versões mais recentes disponíveis, incluindo versões de pré-lançamento:</span><span class="sxs-lookup"><span data-stu-id="cf264-145">List package references that have newer versions available, including prerelease versions:</span></span>

  ```console
  dotnet list package --outdated --include-prerelease
  ```

* <span data-ttu-id="cf264-146">Listar referências de pacotes para uma estrutura de destino específica:</span><span class="sxs-lookup"><span data-stu-id="cf264-146">List package references for a specific target framework:</span></span>

  ```console
  dotnet list package --framework netcoreapp3.0
  ```
