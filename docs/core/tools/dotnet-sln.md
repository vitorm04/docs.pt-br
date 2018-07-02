---
title: Comando dotnet sln – CLI do .NET Core
description: O comando dotnet-sln oferece uma opção conveniente para adicionar, remover e listar projetos em um arquivo de solução.
author: mairaw
ms.author: mairaw
ms.date: 06/13/2018
ms.openlocfilehash: 65ae402ef5519863886c8cf833598f5314b4bdad
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207754"
---
# <a name="dotnet-sln"></a><span data-ttu-id="1193b-103">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="1193b-103">dotnet sln</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="1193b-104">Nome</span><span class="sxs-lookup"><span data-stu-id="1193b-104">Name</span></span>

<span data-ttu-id="1193b-105">`dotnet sln` – modifica um arquivo de solução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1193b-105">`dotnet sln` - Modifies a .NET Core solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="1193b-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="1193b-106">Synopsis</span></span>

```
dotnet sln [<SOLUTION_NAME>] add <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] add <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] remove <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] remove <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] list
dotnet sln [-h|--help]
```

## <a name="description"></a><span data-ttu-id="1193b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="1193b-107">Description</span></span>

<span data-ttu-id="1193b-108">O comando `dotnet sln` oferece uma maneira conveniente de adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="1193b-108">The `dotnet sln` command provides a convenient way to add, remove, and list projects in a solution file.</span></span>

<span data-ttu-id="1193b-109">Para usar o comando `dotnet sln`, o arquivo de solução já deve existir.</span><span class="sxs-lookup"><span data-stu-id="1193b-109">To use the `dotnet sln` command, the solution file must already exist.</span></span> <span data-ttu-id="1193b-110">Se você precisar criar um, use o comando [dotnet new](dotnet-new.md), como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="1193b-110">If you need to create one, use the [dotnet new](dotnet-new.md) command, like in the following example:</span></span>

```
dotnet new sln
```

## <a name="commands"></a><span data-ttu-id="1193b-111">Comandos</span><span class="sxs-lookup"><span data-stu-id="1193b-111">Commands</span></span>

`add <PROJECT> ...`

`add <GLOBBING_PATTERN>`

<span data-ttu-id="1193b-112">Adiciona um projeto ou vários projetos ao arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="1193b-112">Adds a project or multiple projects to the solution file.</span></span> <span data-ttu-id="1193b-113">Os [padrões de recurso de curinga](https://en.wikipedia.org/wiki/Glob_(programming)) são compatíveis com terminais baseados em Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="1193b-113">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`remove <PROJECT> ...`

`remove <GLOBBING_PATTERN>`

<span data-ttu-id="1193b-114">Remova um projeto ou vários projetos do arquivo da solução.</span><span class="sxs-lookup"><span data-stu-id="1193b-114">Removes a project or multiple projects from the solution file.</span></span> <span data-ttu-id="1193b-115">Os [padrões de recurso de curinga](https://en.wikipedia.org/wiki/Glob_(programming)) são compatíveis com terminais baseados em Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="1193b-115">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`list`

<span data-ttu-id="1193b-116">Lista todos os projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="1193b-116">Lists all projects in a solution file.</span></span>

## <a name="arguments"></a><span data-ttu-id="1193b-117">Arguments</span><span class="sxs-lookup"><span data-stu-id="1193b-117">Arguments</span></span>

`SOLUTION_NAME`

<span data-ttu-id="1193b-118">Arquivo de solução a ser usado.</span><span class="sxs-lookup"><span data-stu-id="1193b-118">Solution file to use.</span></span> <span data-ttu-id="1193b-119">Se não for especificado, o comando pesquisará um no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="1193b-119">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="1193b-120">Se houver vários arquivos de solução no diretório, um deles deverá ser especificado.</span><span class="sxs-lookup"><span data-stu-id="1193b-120">If there are multiple solution files in the directory, one must be specified.</span></span>

## <a name="options"></a><span data-ttu-id="1193b-121">Opções</span><span class="sxs-lookup"><span data-stu-id="1193b-121">Options</span></span>

`-h|--help`

<span data-ttu-id="1193b-122">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="1193b-122">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="1193b-123">Exemplos</span><span class="sxs-lookup"><span data-stu-id="1193b-123">Examples</span></span>

<span data-ttu-id="1193b-124">Adicione um projeto C# a uma solução:</span><span class="sxs-lookup"><span data-stu-id="1193b-124">Add a C# project to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj`

<span data-ttu-id="1193b-125">Remova um projeto C# de uma solução:</span><span class="sxs-lookup"><span data-stu-id="1193b-125">Remove a C# project from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

<span data-ttu-id="1193b-126">Adicione vários projetos C# a uma solução:</span><span class="sxs-lookup"><span data-stu-id="1193b-126">Add multiple C# projects to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="1193b-127">Remova vários projetos C# de uma solução:</span><span class="sxs-lookup"><span data-stu-id="1193b-127">Remove multiple C# projects from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="1193b-128">Adicione vários projetos C# a uma solução usando um padrão de recurso de curinga:</span><span class="sxs-lookup"><span data-stu-id="1193b-128">Add multiple C# projects to a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln add **/*.csproj`

<span data-ttu-id="1193b-129">Remova vários projetos C# de uma solução usando um padrão de recurso de curinga:</span><span class="sxs-lookup"><span data-stu-id="1193b-129">Remove multiple C# projects from a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln remove **/*.csproj`
