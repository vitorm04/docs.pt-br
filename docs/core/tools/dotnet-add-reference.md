---
title: "Comando dotnet-add reference – CLI do .NET Core"
description: "O comando dotnet add reference fornece uma opção conveniente para adicionar referências projeto a projeto."
author: mairaw
ms.author: mairaw
ms.date: 08/13/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.translationtype: HT
ms.sourcegitcommit: a19ab54a6cc44bd7acd1e40a4ca94da52bf14297
ms.openlocfilehash: 18e3ce22c1b9a4506b2690262d8d0c4e13a58ed1
ms.contentlocale: pt-br
ms.lasthandoff: 08/14/2017

---
# <a name="dotnet-add-reference"></a><span data-ttu-id="e7a6e-103">Referência dotnet-add</span><span class="sxs-lookup"><span data-stu-id="e7a6e-103">dotnet-add reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="e7a6e-104">Nome</span><span class="sxs-lookup"><span data-stu-id="e7a6e-104">Name</span></span>

<span data-ttu-id="e7a6e-105">`dotnet add reference` – Adiciona as referências P2P (projeto a projeto).</span><span class="sxs-lookup"><span data-stu-id="e7a6e-105">`dotnet add reference` - Adds project-to-project (P2P) references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e7a6e-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="e7a6e-106">Synopsis</span></span>

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="e7a6e-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e7a6e-107">Description</span></span>

<span data-ttu-id="e7a6e-108">O comando `dotnet add reference` fornece uma opção conveniente para adicionar referências de projeto a um projeto.</span><span class="sxs-lookup"><span data-stu-id="e7a6e-108">The `dotnet add reference` command provides a convenient option to add project references to a project.</span></span> <span data-ttu-id="e7a6e-109">Depois de executar o comando, os elementos [`<ProjectReference>`](/visualstudio/msbuild/common-msbuild-project-items) são adicionados ao arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="e7a6e-109">After running the command, the [`<ProjectReference>`](/visualstudio/msbuild/common-msbuild-project-items) elements are added to the project file.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a><span data-ttu-id="e7a6e-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="e7a6e-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="e7a6e-111">Especifica o arquivo do projeto.</span><span class="sxs-lookup"><span data-stu-id="e7a6e-111">Specifies the project file.</span></span> <span data-ttu-id="e7a6e-112">Se não for especificado, o comando irá procurar um no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="e7a6e-112">If not specified, the command will search the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="e7a6e-113">Referências P2P (projeto a projeto) a serem adicionadas.</span><span class="sxs-lookup"><span data-stu-id="e7a6e-113">Project-to-project (P2P) references to add.</span></span> <span data-ttu-id="e7a6e-114">Especifique um ou mais projetos.</span><span class="sxs-lookup"><span data-stu-id="e7a6e-114">Specify one or more projects.</span></span> <span data-ttu-id="e7a6e-115">Os [padrões Glob](https://en.wikipedia.org/wiki/Glob_(programming)) são compatíveis com sistemas baseados em Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="e7a6e-115">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux-based systems.</span></span>

## <a name="options"></a><span data-ttu-id="e7a6e-116">Opções</span><span class="sxs-lookup"><span data-stu-id="e7a6e-116">Options</span></span>

`-h|--help`

<span data-ttu-id="e7a6e-117">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="e7a6e-117">Prints out a short help for the command.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="e7a6e-118">Adiciona referências de projeto somente quando há uma [estrutura](../../standard/frameworks.md) específica como destino.</span><span class="sxs-lookup"><span data-stu-id="e7a6e-118">Adds project references only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="e7a6e-119">Exemplos</span><span class="sxs-lookup"><span data-stu-id="e7a6e-119">Examples</span></span>

<span data-ttu-id="e7a6e-120">Adicionar referência de projeto:</span><span class="sxs-lookup"><span data-stu-id="e7a6e-120">Add a project reference:</span></span>

`dotnet add app/app.csproj reference lib/lib.csproj`

<span data-ttu-id="e7a6e-121">Adicionar várias referências de projeto:</span><span class="sxs-lookup"><span data-stu-id="e7a6e-121">Add multiple project references:</span></span>

`dotnet add reference lib1/lib1.csproj lib2/lib2.csproj`

<span data-ttu-id="e7a6e-122">Adicionar várias referências de projeto usando um padrão de recurso de curinga no Linux/Unix:</span><span class="sxs-lookup"><span data-stu-id="e7a6e-122">Add multiple project references using a globbing pattern on Linux/Unix:</span></span>

`dotnet add app/app.csproj reference **/*.csproj`
