---
title: Comando dotnet sln
description: O comando dotnet-sln oferece uma opção conveniente para adicionar, remover e listar projetos em um arquivo de solução.
ms.date: 02/14/2020
ms.openlocfilehash: b2455c04a46b2a10b8142d8ddc2d8129f2154b27
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77543476"
---
# <a name="dotnet-sln"></a><span data-ttu-id="7dc87-103">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="7dc87-103">dotnet sln</span></span>

<span data-ttu-id="7dc87-104">**Este artigo se aplica a:** ✔️ .NET Core 2.x SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="7dc87-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="7dc87-105">Nome</span><span class="sxs-lookup"><span data-stu-id="7dc87-105">Name</span></span>

<span data-ttu-id="7dc87-106">`dotnet sln`- Lista ou modifica os projetos em um arquivo de solução .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7dc87-106">`dotnet sln` - Lists or modifies the projects in a .NET Core solution file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="7dc87-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="7dc87-107">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command] [-h|--help]
```

## <a name="description"></a><span data-ttu-id="7dc87-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="7dc87-108">Description</span></span>

<span data-ttu-id="7dc87-109">O `dotnet sln` comando fornece uma maneira conveniente de listar e modificar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="7dc87-109">The `dotnet sln` command provides a convenient way to list and modify projects in a solution file.</span></span>

<span data-ttu-id="7dc87-110">Para usar o comando `dotnet sln`, o arquivo de solução já deve existir.</span><span class="sxs-lookup"><span data-stu-id="7dc87-110">To use the `dotnet sln` command, the solution file must already exist.</span></span> <span data-ttu-id="7dc87-111">Se você precisar criar um, use o novo comando [dotnet,](dotnet-new.md) como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="7dc87-111">If you need to create one, use the [dotnet new](dotnet-new.md) command, as in the following example:</span></span>

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a><span data-ttu-id="7dc87-112">Argumentos</span><span class="sxs-lookup"><span data-stu-id="7dc87-112">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="7dc87-113">O arquivo de solução para usar.</span><span class="sxs-lookup"><span data-stu-id="7dc87-113">The solution file to use.</span></span> <span data-ttu-id="7dc87-114">Se esse argumento for omitido, o comando procurará o diretório atual por um.</span><span class="sxs-lookup"><span data-stu-id="7dc87-114">If this argument is omitted, the command searches the current directory for one.</span></span> <span data-ttu-id="7dc87-115">Se não encontrar nenhum arquivo de solução ou vários arquivos de solução, o comando falhará.</span><span class="sxs-lookup"><span data-stu-id="7dc87-115">If it finds no solution file or multiple solution files, the command fails.</span></span>

## <a name="options"></a><span data-ttu-id="7dc87-116">Opções</span><span class="sxs-lookup"><span data-stu-id="7dc87-116">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="7dc87-117">Imprime uma descrição de como usar o comando.</span><span class="sxs-lookup"><span data-stu-id="7dc87-117">Prints out a description of how to use the command.</span></span>

## <a name="commands"></a><span data-ttu-id="7dc87-118">Comandos</span><span class="sxs-lookup"><span data-stu-id="7dc87-118">Commands</span></span>

### `list`

<span data-ttu-id="7dc87-119">Lista todos os projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="7dc87-119">Lists all projects in a solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="7dc87-120">Sinopse</span><span class="sxs-lookup"><span data-stu-id="7dc87-120">Synopsis</span></span>

```dotnetcli
dotnet sln list [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="7dc87-121">Argumentos</span><span class="sxs-lookup"><span data-stu-id="7dc87-121">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="7dc87-122">O arquivo de solução para usar.</span><span class="sxs-lookup"><span data-stu-id="7dc87-122">The solution file to use.</span></span> <span data-ttu-id="7dc87-123">Se esse argumento for omitido, o comando procurará o diretório atual por um.</span><span class="sxs-lookup"><span data-stu-id="7dc87-123">If this argument is omitted, the command searches the current directory for one.</span></span> <span data-ttu-id="7dc87-124">Se não encontrar nenhum arquivo de solução ou vários arquivos de solução, o comando falhará.</span><span class="sxs-lookup"><span data-stu-id="7dc87-124">If it finds no solution file or multiple solution files, the command fails.</span></span>

#### <a name="options"></a><span data-ttu-id="7dc87-125">Opções</span><span class="sxs-lookup"><span data-stu-id="7dc87-125">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="7dc87-126">Imprime uma descrição de como usar o comando.</span><span class="sxs-lookup"><span data-stu-id="7dc87-126">Prints out a description of how to use the command.</span></span>
  
### `add`

<span data-ttu-id="7dc87-127">Adiciona um ou mais projetos ao arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="7dc87-127">Adds one or more projects to the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="7dc87-128">Sinopse</span><span class="sxs-lookup"><span data-stu-id="7dc87-128">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder] <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="7dc87-129">Argumentos</span><span class="sxs-lookup"><span data-stu-id="7dc87-129">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="7dc87-130">O arquivo de solução para usar.</span><span class="sxs-lookup"><span data-stu-id="7dc87-130">The solution file to use.</span></span> <span data-ttu-id="7dc87-131">Se não for especificado, o comando procura o diretório atual por um e falha se houver vários arquivos de solução.</span><span class="sxs-lookup"><span data-stu-id="7dc87-131">If it is unspecified, the command searches the current directory for one and fails if there are multiple solution files.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="7dc87-132">O caminho para o projeto ou projetos para adicionar à solução.</span><span class="sxs-lookup"><span data-stu-id="7dc87-132">The path to the project or projects to add to the solution.</span></span> <span data-ttu-id="7dc87-133">As expansões de [padrão de globbing](https://en.wikipedia.org/wiki/Glob_(programming)) de shell `dotnet sln` Unix/Linux são processadas corretamente pelo comando.</span><span class="sxs-lookup"><span data-stu-id="7dc87-133">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="7dc87-134">Opções</span><span class="sxs-lookup"><span data-stu-id="7dc87-134">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="7dc87-135">Imprime uma descrição de como usar o comando.</span><span class="sxs-lookup"><span data-stu-id="7dc87-135">Prints out a description of how to use the command.</span></span>

- **`--in-root`**

  <span data-ttu-id="7dc87-136">Coloca os projetos na raiz da solução, em vez de criar uma pasta de solução.</span><span class="sxs-lookup"><span data-stu-id="7dc87-136">Places the projects in the root of the solution, rather than creating a solution folder.</span></span> <span data-ttu-id="7dc87-137">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="7dc87-137">Available since .NET Core 3.0 SDK.</span></span>

- **`-s|--solution-folder`**

  <span data-ttu-id="7dc87-138">O caminho da pasta de solução de destino para adicionar os projetos.</span><span class="sxs-lookup"><span data-stu-id="7dc87-138">The destination solution folder path to add the projects to.</span></span> <span data-ttu-id="7dc87-139">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="7dc87-139">Available since .NET Core 3.0 SDK.</span></span>

### `remove`

<span data-ttu-id="7dc87-140">Remova um projeto ou vários projetos do arquivo da solução.</span><span class="sxs-lookup"><span data-stu-id="7dc87-140">Removes a project or multiple projects from the solution file.</span></span>

#### <a name="synopsis"></a><span data-ttu-id="7dc87-141">Sinopse</span><span class="sxs-lookup"><span data-stu-id="7dc87-141">Synopsis</span></span>

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a><span data-ttu-id="7dc87-142">Argumentos</span><span class="sxs-lookup"><span data-stu-id="7dc87-142">Arguments</span></span>

- **`SOLUTION_FILE`**

  <span data-ttu-id="7dc87-143">O arquivo de solução para usar.</span><span class="sxs-lookup"><span data-stu-id="7dc87-143">The solution file to use.</span></span> <span data-ttu-id="7dc87-144">Se for deixado não especificado, o comando procura o diretório atual por um e falha se houver vários arquivos de solução.</span><span class="sxs-lookup"><span data-stu-id="7dc87-144">If is left unspecified, the command searches the current directory for one and fails if there are multiple solution files.</span></span>

- **`PROJECT_PATH`**

  <span data-ttu-id="7dc87-145">O caminho para o projeto ou projetos para adicionar à solução.</span><span class="sxs-lookup"><span data-stu-id="7dc87-145">The path to the project or projects to add to the solution.</span></span> <span data-ttu-id="7dc87-146">As expansões de [padrão de globbing](https://en.wikipedia.org/wiki/Glob_(programming)) de shell `dotnet sln` Unix/Linux são processadas corretamente pelo comando.</span><span class="sxs-lookup"><span data-stu-id="7dc87-146">Unix/Linux shell [globbing pattern](https://en.wikipedia.org/wiki/Glob_(programming)) expansions are processed correctly by the `dotnet sln` command.</span></span>

#### <a name="options"></a><span data-ttu-id="7dc87-147">Opções</span><span class="sxs-lookup"><span data-stu-id="7dc87-147">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="7dc87-148">Imprime uma descrição de como usar o comando.</span><span class="sxs-lookup"><span data-stu-id="7dc87-148">Prints out a description of how to use the command.</span></span>

## <a name="examples"></a><span data-ttu-id="7dc87-149">Exemplos</span><span class="sxs-lookup"><span data-stu-id="7dc87-149">Examples</span></span>

- <span data-ttu-id="7dc87-150">Liste os projetos em uma solução:</span><span class="sxs-lookup"><span data-stu-id="7dc87-150">List the projects in a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln list
  ```

- <span data-ttu-id="7dc87-151">Adicione um projeto C# a uma solução:</span><span class="sxs-lookup"><span data-stu-id="7dc87-151">Add a C# project to a solution:</span></span>

  ```dotnetcli
  dotnet sln add todo-app/todo-app.csproj
  ```

- <span data-ttu-id="7dc87-152">Remova um projeto C# de uma solução:</span><span class="sxs-lookup"><span data-stu-id="7dc87-152">Remove a C# project from a solution:</span></span>

  ```dotnetcli
  dotnet sln remove todo-app/todo-app.csproj
  ```

- <span data-ttu-id="7dc87-153">Adicionar vários projetos C# à raiz de uma solução:</span><span class="sxs-lookup"><span data-stu-id="7dc87-153">Add multiple C# projects to the root of a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj --in-root
  ```

- <span data-ttu-id="7dc87-154">Adicione vários projetos C# a uma solução:</span><span class="sxs-lookup"><span data-stu-id="7dc87-154">Add multiple C# projects to a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="7dc87-155">Remova vários projetos C# de uma solução:</span><span class="sxs-lookup"><span data-stu-id="7dc87-155">Remove multiple C# projects from a solution:</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- <span data-ttu-id="7dc87-156">Adicionar vários projetos C# a uma solução usando um padrão globbing (somente Unix/Linux):</span><span class="sxs-lookup"><span data-stu-id="7dc87-156">Add multiple C# projects to a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln add **/*.csproj
  ```

- <span data-ttu-id="7dc87-157">Remova vários projetos C# de uma solução usando um padrão globbing (somente Unix/Linux):</span><span class="sxs-lookup"><span data-stu-id="7dc87-157">Remove multiple C# projects from a solution using a globbing pattern (Unix/Linux only):</span></span>

  ```dotnetcli
  dotnet sln todo.sln remove **/*.csproj
  ```
