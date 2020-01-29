---
title: Comando dotnet sln
description: O comando dotnet-sln oferece uma opção conveniente para adicionar, remover e listar projetos em um arquivo de solução.
ms.date: 10/29/2019
ms.openlocfilehash: e344deaae0867202a79a3c38df48a2be8d4d7d13
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733074"
---
# <a name="dotnet-sln"></a><span data-ttu-id="e2b6a-103">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="e2b6a-103">dotnet sln</span></span>

<span data-ttu-id="e2b6a-104">**Este artigo aplica-se a:** ✔️ SDK do .NET Core 1. x e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="e2b6a-104">**This article applies to:** ✔️ .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="e2b6a-105">Name</span><span class="sxs-lookup"><span data-stu-id="e2b6a-105">Name</span></span>

<span data-ttu-id="e2b6a-106">`dotnet sln` – modifica um arquivo de solução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e2b6a-106">`dotnet sln` - Modifies a .NET Core solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e2b6a-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="e2b6a-107">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command] [-h|--help]
```

## <a name="description"></a><span data-ttu-id="e2b6a-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="e2b6a-108">Description</span></span>

<span data-ttu-id="e2b6a-109">O comando `dotnet sln` oferece uma maneira conveniente de adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="e2b6a-109">The `dotnet sln` command provides a convenient way to add, remove, and list projects in a solution file.</span></span>

<span data-ttu-id="e2b6a-110">Para usar o comando `dotnet sln`, o arquivo de solução já deve existir.</span><span class="sxs-lookup"><span data-stu-id="e2b6a-110">To use the `dotnet sln` command, the solution file must already exist.</span></span> <span data-ttu-id="e2b6a-111">Se você precisar criar um, use o comando [dotnet new](dotnet-new.md), como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="e2b6a-111">If you need to create one, use the [dotnet new](dotnet-new.md) command, like in the following example:</span></span>

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a><span data-ttu-id="e2b6a-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="e2b6a-112">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="e2b6a-113">O arquivo de solução a ser usado.</span><span class="sxs-lookup"><span data-stu-id="e2b6a-113">The solution file to use.</span></span> <span data-ttu-id="e2b6a-114">Se não for especificado, o comando pesquisará um no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="e2b6a-114">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="e2b6a-115">Se houver vários arquivos de solução no diretório, um deles deverá ser especificado.</span><span class="sxs-lookup"><span data-stu-id="e2b6a-115">If there are multiple solution files in the directory, one must be specified.</span></span>

## <a name="options"></a><span data-ttu-id="e2b6a-116">Opções</span><span class="sxs-lookup"><span data-stu-id="e2b6a-116">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="e2b6a-117">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="e2b6a-117">Prints out a short help for the command.</span></span>

## <a name="commands"></a><span data-ttu-id="e2b6a-118">Comandos</span><span class="sxs-lookup"><span data-stu-id="e2b6a-118">Commands</span></span>

### `add`

<span data-ttu-id="e2b6a-119">Adiciona um projeto ou vários projetos ao arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="e2b6a-119">Adds a project or multiple projects to the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="e2b6a-120">Sinopse</span><span class="sxs-lookup"><span data-stu-id="e2b6a-120">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder] <PROJECT_PATH>
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="e2b6a-121">Arguments</span><span class="sxs-lookup"><span data-stu-id="e2b6a-121">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="e2b6a-122">O arquivo de solução a ser usado.</span><span class="sxs-lookup"><span data-stu-id="e2b6a-122">The solution file to use.</span></span> <span data-ttu-id="e2b6a-123">Se não for especificado, o comando pesquisará um no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="e2b6a-123">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="e2b6a-124">Se houver vários arquivos de solução no diretório, um deles deverá ser especificado.</span><span class="sxs-lookup"><span data-stu-id="e2b6a-124">If there are multiple solution files in the directory, one must be specified.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="e2b6a-125">O caminho para o projeto a ser adicionado à solução.</span><span class="sxs-lookup"><span data-stu-id="e2b6a-125">The path to the project to add to the solution.</span></span> <span data-ttu-id="e2b6a-126">Adicione vários projetos adicionando um após o outro separado por espaços.</span><span class="sxs-lookup"><span data-stu-id="e2b6a-126">Add multiple projects by adding one after the other separated by spaces.</span></span> <span data-ttu-id="e2b6a-127">As expansões de [padrão de mascaramento](https://en.wikipedia.org/wiki/Glob_(programming)) do shell do UNIX/Linux são processadas corretamente pelo comando `dotnet sln`.</span><span class="sxs-lookup"><span data-stu-id="e2b6a-127">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="e2b6a-128">Opções</span><span class="sxs-lookup"><span data-stu-id="e2b6a-128">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="e2b6a-129">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="e2b6a-129">Prints out a short help for the command.</span></span>

- **`--in-root`**

  <span data-ttu-id="e2b6a-130">Coloca os projetos na raiz da solução, em vez de criar uma pasta de solução.</span><span class="sxs-lookup"><span data-stu-id="e2b6a-130">Places the projects in the root of the solution, rather than creating a solution folder.</span></span> <span data-ttu-id="e2b6a-131">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="e2b6a-131">Available since .NET Core 3.0 SDK.</span></span>

- **`-s|--solution-folder`**

  <span data-ttu-id="e2b6a-132">O caminho da pasta da solução de destino para a qual adicionar os projetos.</span><span class="sxs-lookup"><span data-stu-id="e2b6a-132">The destination solution folder path to add the projects to.</span></span> <span data-ttu-id="e2b6a-133">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="e2b6a-133">Available since .NET Core 3.0 SDK.</span></span>

### `remove`

<span data-ttu-id="e2b6a-134">Remova um projeto ou vários projetos do arquivo da solução.</span><span class="sxs-lookup"><span data-stu-id="e2b6a-134">Removes a project or multiple projects from the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="e2b6a-135">Sinopse</span><span class="sxs-lookup"><span data-stu-id="e2b6a-135">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH>
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="e2b6a-136">Arguments</span><span class="sxs-lookup"><span data-stu-id="e2b6a-136">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="e2b6a-137">O arquivo de solução a ser usado.</span><span class="sxs-lookup"><span data-stu-id="e2b6a-137">The solution file to use.</span></span> <span data-ttu-id="e2b6a-138">Se não for especificado, o comando pesquisará um no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="e2b6a-138">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="e2b6a-139">Se houver vários arquivos de solução no diretório, um deles deverá ser especificado.</span><span class="sxs-lookup"><span data-stu-id="e2b6a-139">If there are multiple solution files in the directory, one must be specified.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="e2b6a-140">O caminho para o projeto a ser removido da solução.</span><span class="sxs-lookup"><span data-stu-id="e2b6a-140">The path to the project to remove from the solution.</span></span> <span data-ttu-id="e2b6a-141">Remova vários projetos adicionando um após o outro separado por espaços.</span><span class="sxs-lookup"><span data-stu-id="e2b6a-141">Remove multiple projects by adding one after the other separated by spaces.</span></span> <span data-ttu-id="e2b6a-142">As expansões de [padrão de mascaramento](https://en.wikipedia.org/wiki/Glob_(programming)) do shell do UNIX/Linux são processadas corretamente pelo comando `dotnet sln`.</span><span class="sxs-lookup"><span data-stu-id="e2b6a-142">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="e2b6a-143">Opções</span><span class="sxs-lookup"><span data-stu-id="e2b6a-143">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="e2b6a-144">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="e2b6a-144">Prints out a short help for the command.</span></span>

### `list`

<span data-ttu-id="e2b6a-145">Lista todos os projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="e2b6a-145">Lists all projects in a solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="e2b6a-146">Sinopse</span><span class="sxs-lookup"><span data-stu-id="e2b6a-146">Synopsis</span></span>

```dotnetcli
dotnet sln list [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="e2b6a-147">Arguments</span><span class="sxs-lookup"><span data-stu-id="e2b6a-147">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="e2b6a-148">O arquivo de solução a ser usado.</span><span class="sxs-lookup"><span data-stu-id="e2b6a-148">The solution file to use.</span></span> <span data-ttu-id="e2b6a-149">Se não for especificado, o comando pesquisará um no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="e2b6a-149">If not specified, the command searches the current directory for one.</span></span> <span data-ttu-id="e2b6a-150">Se houver vários arquivos de solução no diretório, um deles deverá ser especificado.</span><span class="sxs-lookup"><span data-stu-id="e2b6a-150">If there are multiple solution files in the directory, one must be specified.</span></span>

#### <a name="options"></a><span data-ttu-id="e2b6a-151">Opções</span><span class="sxs-lookup"><span data-stu-id="e2b6a-151">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="e2b6a-152">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="e2b6a-152">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="e2b6a-153">Exemplos</span><span class="sxs-lookup"><span data-stu-id="e2b6a-153">Examples</span></span>

- <span data-ttu-id="e2b6a-154">Adicione um projeto C# a uma solução:</span><span class="sxs-lookup"><span data-stu-id="e2b6a-154">Add a C# project to a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj
  ```

- <span data-ttu-id="e2b6a-155">Remova um projeto C# de uma solução:</span><span class="sxs-lookup"><span data-stu-id="e2b6a-155">Remove a C# project from a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove todo-app/todo-app.csproj
  ```

- <span data-ttu-id="e2b6a-156">Adicione vários projetos C# a uma solução:</span><span class="sxs-lookup"><span data-stu-id="e2b6a-156">Add multiple C# projects to a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="e2b6a-157">Remova vários projetos C# de uma solução:</span><span class="sxs-lookup"><span data-stu-id="e2b6a-157">Remove multiple C# projects from a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="e2b6a-158">Adicionar vários C# projetos a uma solução usando um padrão de mascaramento (somente UNIX/Linux):</span><span class="sxs-lookup"><span data-stu-id="e2b6a-158">Add multiple C# projects to a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln add **/*.csproj
  ```

- <span data-ttu-id="e2b6a-159">Remover vários C# projetos de uma solução usando um padrão de mascaramento (somente UNIX/Linux):</span><span class="sxs-lookup"><span data-stu-id="e2b6a-159">Remove multiple C# projects from a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove **/*.csproj
  ```
