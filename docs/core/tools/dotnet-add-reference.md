---
title: Comando dotnet-add reference – CLI do .NET Core
description: O comando dotnet add reference fornece uma opção conveniente para adicionar referências projeto a projeto.
author: mairaw
ms.author: mairaw
ms.date: 09/19/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: c82696eee2fbe4bbad86e59cf5de1c2e74d048f6
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-add-reference"></a><span data-ttu-id="383d0-103">Referência dotnet-add</span><span class="sxs-lookup"><span data-stu-id="383d0-103">dotnet-add reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="383d0-104">Nome</span><span class="sxs-lookup"><span data-stu-id="383d0-104">Name</span></span>

<span data-ttu-id="383d0-105">`dotnet add reference` – Adiciona as referências P2P (projeto a projeto).</span><span class="sxs-lookup"><span data-stu-id="383d0-105">`dotnet add reference` - Adds project-to-project (P2P) references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="383d0-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="383d0-106">Synopsis</span></span>

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="383d0-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="383d0-107">Description</span></span>

<span data-ttu-id="383d0-108">O comando `dotnet add reference` fornece uma opção conveniente para adicionar referências de projeto a um projeto.</span><span class="sxs-lookup"><span data-stu-id="383d0-108">The `dotnet add reference` command provides a convenient option to add project references to a project.</span></span> <span data-ttu-id="383d0-109">Depois de executar o comando, os elementos [`<ProjectReference>`](/visualstudio/msbuild/common-msbuild-project-items) são adicionados ao arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="383d0-109">After running the command, the [`<ProjectReference>`](/visualstudio/msbuild/common-msbuild-project-items) elements are added to the project file.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a><span data-ttu-id="383d0-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="383d0-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="383d0-111">Especifica o arquivo do projeto.</span><span class="sxs-lookup"><span data-stu-id="383d0-111">Specifies the project file.</span></span> <span data-ttu-id="383d0-112">Se não for especificado, o comando pesquisará um no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="383d0-112">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="383d0-113">Referências P2P (projeto a projeto) a serem adicionadas.</span><span class="sxs-lookup"><span data-stu-id="383d0-113">Project-to-project (P2P) references to add.</span></span> <span data-ttu-id="383d0-114">Especifique um ou mais projetos.</span><span class="sxs-lookup"><span data-stu-id="383d0-114">Specify one or more projects.</span></span> <span data-ttu-id="383d0-115">Os [padrões Glob](https://en.wikipedia.org/wiki/Glob_(programming)) são compatíveis com sistemas baseados em Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="383d0-115">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux-based systems.</span></span>

## <a name="options"></a><span data-ttu-id="383d0-116">Opções</span><span class="sxs-lookup"><span data-stu-id="383d0-116">Options</span></span>

`-h|--help`

<span data-ttu-id="383d0-117">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="383d0-117">Prints out a short help for the command.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="383d0-118">Adiciona referências de projeto somente quando há uma [estrutura](../../standard/frameworks.md) específica como destino.</span><span class="sxs-lookup"><span data-stu-id="383d0-118">Adds project references only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="383d0-119">Exemplos</span><span class="sxs-lookup"><span data-stu-id="383d0-119">Examples</span></span>

<span data-ttu-id="383d0-120">Adicionar referência de projeto:</span><span class="sxs-lookup"><span data-stu-id="383d0-120">Add a project reference:</span></span>

`dotnet add app/app.csproj reference lib/lib.csproj`

<span data-ttu-id="383d0-121">Adicionar várias referências de projeto ao projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="383d0-121">Add multiple project references to the project in the current directory:</span></span>

`dotnet add reference lib1/lib1.csproj lib2/lib2.csproj`

<span data-ttu-id="383d0-122">Adicionar várias referências de projeto usando um padrão de recurso de curinga no Linux/Unix:</span><span class="sxs-lookup"><span data-stu-id="383d0-122">Add multiple project references using a globbing pattern on Linux/Unix:</span></span>

`dotnet add app/app.csproj reference **/*.csproj`
