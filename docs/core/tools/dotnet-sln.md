---
title: Comando dotnet sln
description: O comando dotnet-sln oferece uma opção conveniente para adicionar, remover e listar projetos em um arquivo de solução.
ms.date: 06/13/2018
ms.openlocfilehash: 84508aaefff61b31e2965576ebc2daaae7331951
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117591"
---
# <a name="dotnet-sln"></a><span data-ttu-id="042ad-103">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="042ad-103">dotnet sln</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="042ad-104">Nome</span><span class="sxs-lookup"><span data-stu-id="042ad-104">Name</span></span>

<span data-ttu-id="042ad-105">`dotnet sln` – modifica um arquivo de solução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="042ad-105">`dotnet sln` - Modifies a .NET Core solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="042ad-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="042ad-106">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_NAME>] add <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] add <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] remove <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] remove <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] list
dotnet sln [-h|--help]
```

## <a name="description"></a><span data-ttu-id="042ad-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="042ad-107">Description</span></span>

<span data-ttu-id="042ad-108">O comando `dotnet sln` oferece uma maneira conveniente de adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="042ad-108">The `dotnet sln` command provides a convenient way to add, remove, and list projects in a solution file.</span></span>

<span data-ttu-id="042ad-109">Para usar o comando `dotnet sln`, o arquivo de solução já deve existir.</span><span class="sxs-lookup"><span data-stu-id="042ad-109">To use the `dotnet sln` command, the solution file must already exist.</span></span> <span data-ttu-id="042ad-110">Se você precisar criar um, use o comando [dotnet new](dotnet-new.md), como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="042ad-110">If you need to create one, use the [dotnet new](dotnet-new.md) command, like in the following example:</span></span>

```dotnetcli
dotnet new sln
```

## <a name="commands"></a><span data-ttu-id="042ad-111">Comandos</span><span class="sxs-lookup"><span data-stu-id="042ad-111">Commands</span></span>

`add <PROJECT> ...`

`add <GLOBBING_PATTERN>`

<span data-ttu-id="042ad-112">Adiciona um projeto ou vários projetos ao arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="042ad-112">Adds a project or multiple projects to the solution file.</span></span> <span data-ttu-id="042ad-113">Os [padrões de recurso de curinga](https://en.wikipedia.org/wiki/Glob_(programming)) são compatíveis com terminais baseados em Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="042ad-113">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`remove <PROJECT> ...`

`remove <GLOBBING_PATTERN>`

<span data-ttu-id="042ad-114">Remova um projeto ou vários projetos do arquivo da solução.</span><span class="sxs-lookup"><span data-stu-id="042ad-114">Removes a project or multiple projects from the solution file.</span></span> <span data-ttu-id="042ad-115">Os [padrões de recurso de curinga](https://en.wikipedia.org/wiki/Glob_(programming)) são compatíveis com terminais baseados em Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="042ad-115">[Globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

`list`

<span data-ttu-id="042ad-116">Lista todos os projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="042ad-116">Lists all projects in a solution file.</span></span>

## <a name="arguments"></a><span data-ttu-id="042ad-117">Arguments</span><span class="sxs-lookup"><span data-stu-id="042ad-117">Arguments</span></span>

`SOLUTION_NAME`

<span data-ttu-id="042ad-118">Arquivo de solução a ser usado.</span><span class="sxs-lookup"><span data-stu-id="042ad-118">Solution file to use.</span></span> <span data-ttu-id="042ad-119">Se não for especificado, o comando pesquisará um no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="042ad-119">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="042ad-120">Se houver vários arquivos de solução no diretório, um deles deverá ser especificado.</span><span class="sxs-lookup"><span data-stu-id="042ad-120">If there are multiple solution files in the directory, one must be specified.</span></span>

## <a name="options"></a><span data-ttu-id="042ad-121">Opções</span><span class="sxs-lookup"><span data-stu-id="042ad-121">Options</span></span>

`-h|--help`

<span data-ttu-id="042ad-122">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="042ad-122">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="042ad-123">Exemplos</span><span class="sxs-lookup"><span data-stu-id="042ad-123">Examples</span></span>

<span data-ttu-id="042ad-124">Adicione um projeto C# a uma solução:</span><span class="sxs-lookup"><span data-stu-id="042ad-124">Add a C# project to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj`

<span data-ttu-id="042ad-125">Remova um projeto C# de uma solução:</span><span class="sxs-lookup"><span data-stu-id="042ad-125">Remove a C# project from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

<span data-ttu-id="042ad-126">Adicione vários projetos C# a uma solução:</span><span class="sxs-lookup"><span data-stu-id="042ad-126">Add multiple C# projects to a solution:</span></span>

`dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="042ad-127">Remova vários projetos C# de uma solução:</span><span class="sxs-lookup"><span data-stu-id="042ad-127">Remove multiple C# projects from a solution:</span></span>

`dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj`

<span data-ttu-id="042ad-128">Adicione vários projetos C# a uma solução usando um padrão de recurso de curinga:</span><span class="sxs-lookup"><span data-stu-id="042ad-128">Add multiple C# projects to a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln add **/*.csproj`

<span data-ttu-id="042ad-129">Remova vários projetos C# de uma solução usando um padrão de recurso de curinga:</span><span class="sxs-lookup"><span data-stu-id="042ad-129">Remove multiple C# projects from a solution using a globbing pattern:</span></span>

`dotnet sln todo.sln remove **/*.csproj`

> [!NOTE]
> <span data-ttu-id="042ad-130">O recurso de curinga não é um recurso CLI, mas do shell de comando.</span><span class="sxs-lookup"><span data-stu-id="042ad-130">Globbing is not a CLI feature but rather a feature of the command shell.</span></span> <span data-ttu-id="042ad-131">Para expandir os arquivos com êxito, você deve usar um shell que dê suporte ao recurso de curinga.</span><span class="sxs-lookup"><span data-stu-id="042ad-131">To successfully expand the files, you must use a shell that supports globbing.</span></span> <span data-ttu-id="042ad-132">Para saber mais sobre o recurso de curinga, confira [Wikipédia](https://en.wikipedia.org/wiki/Glob_(programming)).</span><span class="sxs-lookup"><span data-stu-id="042ad-132">For more information about globbing, see [Wikipedia](https://en.wikipedia.org/wiki/Glob_(programming)).</span></span>
