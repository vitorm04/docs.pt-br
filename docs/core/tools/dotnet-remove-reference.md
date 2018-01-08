---
title: "Comando dotnet remove reference – CLI do .NET Core"
description: "O comando dotnet remove reference fornece uma opção conveniente para remover referências projeto a projeto."
keywords: dotnet-remove, CLI, comando da CLI, .NET Core
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 691fd77c7605b6476adc764f20e59b51abd7d914
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-remove-reference"></a><span data-ttu-id="2c62f-104">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="2c62f-104">dotnet remove reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="2c62f-105">Nome</span><span class="sxs-lookup"><span data-stu-id="2c62f-105">Name</span></span>

<span data-ttu-id="2c62f-106">`dotnet remove reference` – Remove as referências projeto a projeto.</span><span class="sxs-lookup"><span data-stu-id="2c62f-106">`dotnet remove reference` - Removes project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2c62f-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="2c62f-107">Synopsis</span></span>

`dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="2c62f-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="2c62f-108">Description</span></span>

<span data-ttu-id="2c62f-109">O comando `dotnet remove reference` fornece uma opção conveniente para remover referências de projeto de um projeto.</span><span class="sxs-lookup"><span data-stu-id="2c62f-109">The `dotnet remove reference` command provides a convenient option to remove project references from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="2c62f-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="2c62f-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="2c62f-111">Arquivo de projeto de destino.</span><span class="sxs-lookup"><span data-stu-id="2c62f-111">Target project file.</span></span> <span data-ttu-id="2c62f-112">Se não for especificado, o comando pesquisará um no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="2c62f-112">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="2c62f-113">Projeto a projeto (Referências de P2P a serem removidas).</span><span class="sxs-lookup"><span data-stu-id="2c62f-113">Project to project (P2P references to remove.</span></span> <span data-ttu-id="2c62f-114">É possível especificar um ou vários projetos.</span><span class="sxs-lookup"><span data-stu-id="2c62f-114">You can specify one or multiple projects.</span></span> <span data-ttu-id="2c62f-115">Os [padrões Glob](https://en.wikipedia.org/wiki/Glob_(programming)) são compatíveis com terminais baseados em Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="2c62f-115">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

## <a name="options"></a><span data-ttu-id="2c62f-116">Opções</span><span class="sxs-lookup"><span data-stu-id="2c62f-116">Options</span></span>

`-h|--help`

<span data-ttu-id="2c62f-117">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="2c62f-117">Prints out a short help for the command.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="2c62f-118">Remove a referência somente quando houver uma [estrutura](../../standard/frameworks.md) específica como destino.</span><span class="sxs-lookup"><span data-stu-id="2c62f-118">Removes the reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="2c62f-119">Exemplos</span><span class="sxs-lookup"><span data-stu-id="2c62f-119">Examples</span></span>

<span data-ttu-id="2c62f-120">Remover uma referência de projeto do projeto especificado:</span><span class="sxs-lookup"><span data-stu-id="2c62f-120">Remove a project reference from the specified project:</span></span>

`dotnet remove app/app.csproj reference lib/lib.csproj`

<span data-ttu-id="2c62f-121">Remover várias referências de projeto do projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="2c62f-121">Remove multiple project references from the project in the current directory:</span></span>

`dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj`

<span data-ttu-id="2c62f-122">Remova várias referências de projeto usando o padrão glob em Unix/Linux:</span><span class="sxs-lookup"><span data-stu-id="2c62f-122">Remove multiple project references using a glob pattern on Unix/Linux:</span></span>

`dotnet remove app/app.csproj reference **/*.csproj`
