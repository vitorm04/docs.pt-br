---
title: Comando dotnet remove reference – CLI do .NET Core
description: O comando dotnet remove reference fornece uma opção conveniente para remover referências projeto a projeto.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: b281b255be7f49a99a6b4928c340cd4fb085f085
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696225"
---
# <a name="dotnet-remove-reference"></a><span data-ttu-id="d3908-103">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="d3908-103">dotnet remove reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="d3908-104">Nome</span><span class="sxs-lookup"><span data-stu-id="d3908-104">Name</span></span>

<span data-ttu-id="d3908-105">`dotnet remove reference` – Remove as referências projeto a projeto.</span><span class="sxs-lookup"><span data-stu-id="d3908-105">`dotnet remove reference` - Removes project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d3908-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="d3908-106">Synopsis</span></span>

`dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="d3908-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d3908-107">Description</span></span>

<span data-ttu-id="d3908-108">O comando `dotnet remove reference` fornece uma opção conveniente para remover referências de projeto de um projeto.</span><span class="sxs-lookup"><span data-stu-id="d3908-108">The `dotnet remove reference` command provides a convenient option to remove project references from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="d3908-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="d3908-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="d3908-110">Arquivo de projeto de destino.</span><span class="sxs-lookup"><span data-stu-id="d3908-110">Target project file.</span></span> <span data-ttu-id="d3908-111">Se não for especificado, o comando pesquisará um no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="d3908-111">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="d3908-112">Referências P2P (projeto a projeto) a serem removidas.</span><span class="sxs-lookup"><span data-stu-id="d3908-112">Project-to-project (P2P) references to remove.</span></span> <span data-ttu-id="d3908-113">É possível especificar um ou vários projetos.</span><span class="sxs-lookup"><span data-stu-id="d3908-113">You can specify one or multiple projects.</span></span> <span data-ttu-id="d3908-114">Os [padrões Glob](https://en.wikipedia.org/wiki/Glob_(programming)) são compatíveis com terminais baseados em Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="d3908-114">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

## <a name="options"></a><span data-ttu-id="d3908-115">Opções</span><span class="sxs-lookup"><span data-stu-id="d3908-115">Options</span></span>

`-h|--help`

<span data-ttu-id="d3908-116">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="d3908-116">Prints out a short help for the command.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="d3908-117">Remove a referência somente quando houver uma [estrutura](../../standard/frameworks.md) específica como destino.</span><span class="sxs-lookup"><span data-stu-id="d3908-117">Removes the reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="d3908-118">Exemplos</span><span class="sxs-lookup"><span data-stu-id="d3908-118">Examples</span></span>

<span data-ttu-id="d3908-119">Remover uma referência de projeto do projeto especificado:</span><span class="sxs-lookup"><span data-stu-id="d3908-119">Remove a project reference from the specified project:</span></span>

`dotnet remove app/app.csproj reference lib/lib.csproj`

<span data-ttu-id="d3908-120">Remover várias referências de projeto do projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="d3908-120">Remove multiple project references from the project in the current directory:</span></span>

`dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj`

<span data-ttu-id="d3908-121">Remova várias referências de projeto usando o padrão glob em Unix/Linux:</span><span class="sxs-lookup"><span data-stu-id="d3908-121">Remove multiple project references using a glob pattern on Unix/Linux:</span></span>

`dotnet remove app/app.csproj reference **/*.csproj`
