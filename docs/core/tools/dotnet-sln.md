---
title: Comando dotnet sln – CLI do .NET Core
description: O comando dotnet-sln oferece uma opção conveniente para adicionar, remover e listar projetos em um arquivo de solução.
author: mairaw
ms.author: mairaw
ms.date: 06/13/2018
ms.openlocfilehash: 2651e8e14ad43f41354b8165179f95f65e732f4c
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49121214"
---
# <a name="dotnet-sln"></a><span data-ttu-id="9a13d-103">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="9a13d-103">dotnet sln</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="9a13d-104">Nome</span><span class="sxs-lookup"><span data-stu-id="9a13d-104">Name</span></span>

<span data-ttu-id="9a13d-105">`dotnet sln` – modifica um arquivo de solução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9a13d-105">`dotnet sln` - Modifies a .NET Core solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9a13d-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="9a13d-106">Synopsis</span></span>

```
dotnet sln [<SOLUTION_NAME>] add <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] add <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] remove <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] remove <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] list
dotnet sln [-h|--help]
```

## <a name="description"></a><span data-ttu-id="9a13d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="9a13d-107">Description</span></span>

<span data-ttu-id="9a13d-108">O comando `dotnet sln` oferece uma maneira conveniente de adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="9a13d-108">The `dotnet sln` command provides a convenient way to add, remove, and list projects in a solution file.</span></span>

<span data-ttu-id="9a13d-109">Para usar o comando `dotnet sln`, o arquivo de solução já deve existir.</span><span class="sxs-lookup"><span data-stu-id="9a13d-109">To use the `dotnet sln` command, the solution file must already exist.</span></span> <span data-ttu-id="9a13d-110">Se você precisar criar um, use o comando [dotnet new](dotnet-new.md), como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="9a13d-110">If you need to create one, use the [dotnet new](dotnet-new.md) command, like in the following example:</span></span>

```
dotnet new sln
```

## <a name="commands"></a><span data-ttu-id="9a13d-111">Comandos</span><span class="sxs-lookup"><span data-stu-id="9a13d-111">Commands</span></span>

`add <PROJECT> ...`

`add <GLOBBING_PATTERN>`

<span data-ttu-id="9a13d-112">Adiciona um projeto ou vários projetos ao arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="9a13d-112">Adds a project or multiple projects to the solution file.</span></span> <span data-ttu-id="9a13d-113">Os [padrões de recurso de curinga](https://en.wikipedia.org/wiki/Glob_(programming)) são compatíveis com terminais baseados em Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="9a13d-113">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`remove <PROJECT> ...`

`remove <GLOBBING_PATTERN>`

<span data-ttu-id="9a13d-114">Remova um projeto ou vários projetos do arquivo da solução.</span><span class="sxs-lookup"><span data-stu-id="9a13d-114">Removes a project or multiple projects from the solution file.</span></span> <span data-ttu-id="9a13d-115">Os [padrões de recurso de curinga](https://en.wikipedia.org/wiki/Glob_(programming)) são compatíveis com terminais baseados em Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="9a13d-115">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`list`

<span data-ttu-id="9a13d-116">Lista todos os projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="9a13d-116">Lists all projects in a solution file.</span></span>

## <a name="arguments"></a><span data-ttu-id="9a13d-117">Arguments</span><span class="sxs-lookup"><span data-stu-id="9a13d-117">Arguments</span></span>

`SOLUTION_NAME`

<span data-ttu-id="9a13d-118">Arquivo de solução a ser usado.</span><span class="sxs-lookup"><span data-stu-id="9a13d-118">Solution file to use.</span></span> <span data-ttu-id="9a13d-119">Se não for especificado, o comando pesquisará um no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="9a13d-119">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="9a13d-120">Se houver vários arquivos de solução no diretório, um deles deverá ser especificado.</span><span class="sxs-lookup"><span data-stu-id="9a13d-120">If there are multiple solution files in the directory, one must be specified.</span></span>

## <a name="options"></a><span data-ttu-id="9a13d-121">Opções</span><span class="sxs-lookup"><span data-stu-id="9a13d-121">Options</span></span>

`-h|--help`

<span data-ttu-id="9a13d-122">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="9a13d-122">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="9a13d-123">Exemplos</span><span class="sxs-lookup"><span data-stu-id="9a13d-123">Examples</span></span>

<span data-ttu-id="9a13d-124">Adicione um projeto C# a uma solução:</span><span class="sxs-lookup"><span data-stu-id="9a13d-124">Add a C# project to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj`

<span data-ttu-id="9a13d-125">Remova um projeto C# de uma solução:</span><span class="sxs-lookup"><span data-stu-id="9a13d-125">Remove a C# project from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

<span data-ttu-id="9a13d-126">Adicione vários projetos C# a uma solução:</span><span class="sxs-lookup"><span data-stu-id="9a13d-126">Add multiple C# projects to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="9a13d-127">Remova vários projetos C# de uma solução:</span><span class="sxs-lookup"><span data-stu-id="9a13d-127">Remove multiple C# projects from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="9a13d-128">Adicione vários projetos C# a uma solução usando um padrão de recurso de curinga:</span><span class="sxs-lookup"><span data-stu-id="9a13d-128">Add multiple C# projects to a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln add **/*.csproj`

<span data-ttu-id="9a13d-129">Remova vários projetos C# de uma solução usando um padrão de recurso de curinga:</span><span class="sxs-lookup"><span data-stu-id="9a13d-129">Remove multiple C# projects from a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln remove **/*.csproj`

> [!NOTE]
> <span data-ttu-id="9a13d-130">O recurso de curinga não é um recurso CLI, mas do shell de comando.</span><span class="sxs-lookup"><span data-stu-id="9a13d-130">Globbing is not a CLI feature but rather a feature of the command shell.</span></span> <span data-ttu-id="9a13d-131">Para expandir os arquivos com êxito, você deve usar um shell que dê suporte ao recurso de curinga.</span><span class="sxs-lookup"><span data-stu-id="9a13d-131">To successfully expand the files, you must use a shell that supports globbing.</span></span> <span data-ttu-id="9a13d-132">Para saber mais sobre o recurso de curinga, confira [Wikipédia](https://en.wikipedia.org/wiki/Glob_(programming)).</span><span class="sxs-lookup"><span data-stu-id="9a13d-132">For more information about globbing, see [Wikipedia](https://en.wikipedia.org/wiki/Glob_(programming)).</span></span>
