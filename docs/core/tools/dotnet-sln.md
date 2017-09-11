---
title: "Comando dotnet sln – CLI do .NET Core"
description: "O comando dotnet-sln oferece uma opção conveniente para adicionar, remover e listar projetos em um arquivo de solução."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.translationtype: HT
ms.sourcegitcommit: a19ab54a6cc44bd7acd1e40a4ca94da52bf14297
ms.openlocfilehash: 5071cb80be0fb14829a0fdffd0f5a2d2371b6ba8
ms.contentlocale: pt-br
ms.lasthandoff: 08/14/2017

---
# <a name="dotnet-sln"></a><span data-ttu-id="2a621-103">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="2a621-103">dotnet sln</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="2a621-104">Nome</span><span class="sxs-lookup"><span data-stu-id="2a621-104">Name</span></span>

<span data-ttu-id="2a621-105">`dotnet-sln` – modifica um arquivo de solução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2a621-105">`dotnet-sln` - Modifies a .NET Core solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2a621-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="2a621-106">Synopsis</span></span>

```
dotnet sln [<SOLUTION_NAME>] add <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] add <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] remove <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] remove <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] list
dotnet sln [-h|--help]
```

## <a name="description"></a><span data-ttu-id="2a621-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="2a621-107">Description</span></span>

<span data-ttu-id="2a621-108">O comando `dotnet sln` oferece uma maneira conveniente de adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="2a621-108">The `dotnet sln` command provides a convenient way to add, remove, and list projects in a solution file.</span></span>

## <a name="commands"></a><span data-ttu-id="2a621-109">Comandos</span><span class="sxs-lookup"><span data-stu-id="2a621-109">Commands</span></span>

`add <PROJECT> ...`

`add <GLOBBING_PATTERN>`

<span data-ttu-id="2a621-110">Adiciona um projeto ou vários projetos ao arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="2a621-110">Adds a project or multiple projects to the solution file.</span></span> <span data-ttu-id="2a621-111">Os [padrões de recurso de curinga](https://en.wikipedia.org/wiki/Glob_(programming)) são compatíveis com terminais baseados em Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="2a621-111">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`remove <PROJECT> ...`

`remove <GLOBBING_PATTERN>`

<span data-ttu-id="2a621-112">Remova um projeto ou vários projetos do arquivo da solução.</span><span class="sxs-lookup"><span data-stu-id="2a621-112">Removes a project or multiple projects from the solution file.</span></span> <span data-ttu-id="2a621-113">Os [padrões de recurso de curinga](https://en.wikipedia.org/wiki/Glob_(programming)) são compatíveis com terminais baseados em Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="2a621-113">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`list`

<span data-ttu-id="2a621-114">Lista todos os projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="2a621-114">Lists all projects in a solution file.</span></span>

## <a name="arguments"></a><span data-ttu-id="2a621-115">Arguments</span><span class="sxs-lookup"><span data-stu-id="2a621-115">Arguments</span></span>

`SOLUTION_NAME`

<span data-ttu-id="2a621-116">Arquivo de solução a ser usado.</span><span class="sxs-lookup"><span data-stu-id="2a621-116">Solution file to use.</span></span> <span data-ttu-id="2a621-117">Se não for especificado, o comando pesquisará um no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="2a621-117">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="2a621-118">Se houver vários arquivos de solução no diretório, um deles deverá ser especificado.</span><span class="sxs-lookup"><span data-stu-id="2a621-118">If there are multiple solution files in the directory, one must be specified.</span></span>

## <a name="options"></a><span data-ttu-id="2a621-119">Opções</span><span class="sxs-lookup"><span data-stu-id="2a621-119">Options</span></span>

`-h|--help`

<span data-ttu-id="2a621-120">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="2a621-120">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="2a621-121">Exemplos</span><span class="sxs-lookup"><span data-stu-id="2a621-121">Examples</span></span>

<span data-ttu-id="2a621-122">Adicione um projeto C# a uma solução:</span><span class="sxs-lookup"><span data-stu-id="2a621-122">Add a C# project to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj`

<span data-ttu-id="2a621-123">Remova um projeto C# de uma solução:</span><span class="sxs-lookup"><span data-stu-id="2a621-123">Remove a C# project from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

<span data-ttu-id="2a621-124">Adicione vários projetos C# a uma solução:</span><span class="sxs-lookup"><span data-stu-id="2a621-124">Add multiple C# projects to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="2a621-125">Remova vários projetos C# de uma solução:</span><span class="sxs-lookup"><span data-stu-id="2a621-125">Remove multiple C# projects from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="2a621-126">Adicione vários projetos C# a uma solução usando um padrão de recurso de curinga:</span><span class="sxs-lookup"><span data-stu-id="2a621-126">Add multiple C# projects to a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln add **/*.csproj`

<span data-ttu-id="2a621-127">Remova vários projetos C# de uma solução usando um padrão de recurso de curinga:</span><span class="sxs-lookup"><span data-stu-id="2a621-127">Remove multiple C# projects from a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln remove **/*.csproj`
