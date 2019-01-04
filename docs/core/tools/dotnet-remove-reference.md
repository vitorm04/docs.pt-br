---
title: Comando dotnet remove reference
description: O comando dotnet remove reference fornece uma opção conveniente para remover referências projeto a projeto.
ms.date: 05/29/2018
ms.openlocfilehash: bfac4721743babcf48fd8e86a50c8df136e1bfce
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170607"
---
# <a name="dotnet-remove-reference"></a><span data-ttu-id="32003-103">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="32003-103">dotnet remove reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="32003-104">Nome</span><span class="sxs-lookup"><span data-stu-id="32003-104">Name</span></span>

<span data-ttu-id="32003-105">`dotnet remove reference` – Remove as referências projeto a projeto.</span><span class="sxs-lookup"><span data-stu-id="32003-105">`dotnet remove reference` - Removes project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="32003-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="32003-106">Synopsis</span></span>

`dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="32003-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="32003-107">Description</span></span>

<span data-ttu-id="32003-108">O comando `dotnet remove reference` fornece uma opção conveniente para remover referências de projeto de um projeto.</span><span class="sxs-lookup"><span data-stu-id="32003-108">The `dotnet remove reference` command provides a convenient option to remove project references from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="32003-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="32003-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="32003-110">Arquivo de projeto de destino.</span><span class="sxs-lookup"><span data-stu-id="32003-110">Target project file.</span></span> <span data-ttu-id="32003-111">Se não for especificado, o comando pesquisará um no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="32003-111">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="32003-112">Referências P2P (projeto a projeto) a serem removidas.</span><span class="sxs-lookup"><span data-stu-id="32003-112">Project-to-project (P2P) references to remove.</span></span> <span data-ttu-id="32003-113">É possível especificar um ou vários projetos.</span><span class="sxs-lookup"><span data-stu-id="32003-113">You can specify one or multiple projects.</span></span> <span data-ttu-id="32003-114">Os [padrões Glob](https://en.wikipedia.org/wiki/Glob_(programming)) são compatíveis com terminais baseados em Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="32003-114">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

## <a name="options"></a><span data-ttu-id="32003-115">Opções</span><span class="sxs-lookup"><span data-stu-id="32003-115">Options</span></span>

`-h|--help`

<span data-ttu-id="32003-116">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="32003-116">Prints out a short help for the command.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="32003-117">Remove a referência somente quando houver uma [estrutura](../../standard/frameworks.md) específica como destino.</span><span class="sxs-lookup"><span data-stu-id="32003-117">Removes the reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="32003-118">Exemplos</span><span class="sxs-lookup"><span data-stu-id="32003-118">Examples</span></span>

<span data-ttu-id="32003-119">Remover uma referência de projeto do projeto especificado:</span><span class="sxs-lookup"><span data-stu-id="32003-119">Remove a project reference from the specified project:</span></span>

`dotnet remove app/app.csproj reference lib/lib.csproj`

<span data-ttu-id="32003-120">Remover várias referências de projeto do projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="32003-120">Remove multiple project references from the project in the current directory:</span></span>

`dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj`

<span data-ttu-id="32003-121">Remova várias referências de projeto usando o padrão glob em Unix/Linux:</span><span class="sxs-lookup"><span data-stu-id="32003-121">Remove multiple project references using a glob pattern on Unix/Linux:</span></span>

`dotnet remove app/app.csproj reference **/*.csproj`
