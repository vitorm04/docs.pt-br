---
title: Comando dotnet remove reference – CLI do .NET Core
description: O comando dotnet remove reference fornece uma opção conveniente para remover referências projeto a projeto.
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 0b7fb2788ccc04b54bf02f0387141d501612c16d
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-remove-reference"></a><span data-ttu-id="cf6c4-103">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="cf6c4-103">dotnet remove reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="cf6c4-104">Nome</span><span class="sxs-lookup"><span data-stu-id="cf6c4-104">Name</span></span>

<span data-ttu-id="cf6c4-105">`dotnet remove reference` – Remove as referências projeto a projeto.</span><span class="sxs-lookup"><span data-stu-id="cf6c4-105">`dotnet remove reference` - Removes project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="cf6c4-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="cf6c4-106">Synopsis</span></span>

`dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="cf6c4-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="cf6c4-107">Description</span></span>

<span data-ttu-id="cf6c4-108">O comando `dotnet remove reference` fornece uma opção conveniente para remover referências de projeto de um projeto.</span><span class="sxs-lookup"><span data-stu-id="cf6c4-108">The `dotnet remove reference` command provides a convenient option to remove project references from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="cf6c4-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="cf6c4-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="cf6c4-110">Arquivo de projeto de destino.</span><span class="sxs-lookup"><span data-stu-id="cf6c4-110">Target project file.</span></span> <span data-ttu-id="cf6c4-111">Se não for especificado, o comando pesquisará um no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="cf6c4-111">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="cf6c4-112">Projeto a projeto (Referências de P2P a serem removidas).</span><span class="sxs-lookup"><span data-stu-id="cf6c4-112">Project to project (P2P references to remove.</span></span> <span data-ttu-id="cf6c4-113">É possível especificar um ou vários projetos.</span><span class="sxs-lookup"><span data-stu-id="cf6c4-113">You can specify one or multiple projects.</span></span> <span data-ttu-id="cf6c4-114">Os [padrões Glob](https://en.wikipedia.org/wiki/Glob_(programming)) são compatíveis com terminais baseados em Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="cf6c4-114">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

## <a name="options"></a><span data-ttu-id="cf6c4-115">Opções</span><span class="sxs-lookup"><span data-stu-id="cf6c4-115">Options</span></span>

`-h|--help`

<span data-ttu-id="cf6c4-116">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="cf6c4-116">Prints out a short help for the command.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="cf6c4-117">Remove a referência somente quando houver uma [estrutura](../../standard/frameworks.md) específica como destino.</span><span class="sxs-lookup"><span data-stu-id="cf6c4-117">Removes the reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="cf6c4-118">Exemplos</span><span class="sxs-lookup"><span data-stu-id="cf6c4-118">Examples</span></span>

<span data-ttu-id="cf6c4-119">Remover uma referência de projeto do projeto especificado:</span><span class="sxs-lookup"><span data-stu-id="cf6c4-119">Remove a project reference from the specified project:</span></span>

`dotnet remove app/app.csproj reference lib/lib.csproj`

<span data-ttu-id="cf6c4-120">Remover várias referências de projeto do projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="cf6c4-120">Remove multiple project references from the project in the current directory:</span></span>

`dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj`

<span data-ttu-id="cf6c4-121">Remova várias referências de projeto usando o padrão glob em Unix/Linux:</span><span class="sxs-lookup"><span data-stu-id="cf6c4-121">Remove multiple project references using a glob pattern on Unix/Linux:</span></span>

`dotnet remove app/app.csproj reference **/*.csproj`
