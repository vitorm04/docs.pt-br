---
title: Comando dotnet remove reference
description: O comando dotnet remove reference fornece uma opção conveniente para remover referências projeto a projeto.
ms.date: 02/14/2020
ms.openlocfilehash: fcadf677faaf9281fb019c3c4bb16efc906b1aa1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503624"
---
# <a name="dotnet-remove-reference"></a><span data-ttu-id="99226-103">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="99226-103">dotnet remove reference</span></span>

<span data-ttu-id="99226-104">**Este artigo se aplica a:** ✔️ .NET Core 2.x SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="99226-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="99226-105">Nome</span><span class="sxs-lookup"><span data-stu-id="99226-105">Name</span></span>

<span data-ttu-id="99226-106">`dotnet remove reference` – Remove as referências projeto a projeto.</span><span class="sxs-lookup"><span data-stu-id="99226-106">`dotnet remove reference` - Removes project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="99226-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="99226-107">Synopsis</span></span>

```dotnetcli
dotnet remove [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]
```

## <a name="description"></a><span data-ttu-id="99226-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="99226-108">Description</span></span>

<span data-ttu-id="99226-109">O comando `dotnet remove reference` fornece uma opção conveniente para remover referências de projeto de um projeto.</span><span class="sxs-lookup"><span data-stu-id="99226-109">The `dotnet remove reference` command provides a convenient option to remove project references from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="99226-110">Argumentos</span><span class="sxs-lookup"><span data-stu-id="99226-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="99226-111">Arquivo de projeto de destino.</span><span class="sxs-lookup"><span data-stu-id="99226-111">Target project file.</span></span> <span data-ttu-id="99226-112">Se não for especificado, o comando pesquisará um no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="99226-112">If not specified, the command searches the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="99226-113">Referências P2P (projeto a projeto) a serem removidas.</span><span class="sxs-lookup"><span data-stu-id="99226-113">Project-to-project (P2P) references to remove.</span></span> <span data-ttu-id="99226-114">É possível especificar um ou vários projetos.</span><span class="sxs-lookup"><span data-stu-id="99226-114">You can specify one or multiple projects.</span></span> <span data-ttu-id="99226-115">Os [padrões Glob](https://en.wikipedia.org/wiki/Glob_(programming)) são compatíveis com terminais baseados em Unix/Linux.</span><span class="sxs-lookup"><span data-stu-id="99226-115">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux based terminals.</span></span>

## <a name="options"></a><span data-ttu-id="99226-116">Opções</span><span class="sxs-lookup"><span data-stu-id="99226-116">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="99226-117">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="99226-117">Prints out a short help for the command.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="99226-118">Remove a referência somente quando houver uma [estrutura](../../standard/frameworks.md) específica como destino.</span><span class="sxs-lookup"><span data-stu-id="99226-118">Removes the reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="99226-119">Exemplos</span><span class="sxs-lookup"><span data-stu-id="99226-119">Examples</span></span>

- <span data-ttu-id="99226-120">Remover uma referência de projeto do projeto especificado:</span><span class="sxs-lookup"><span data-stu-id="99226-120">Remove a project reference from the specified project:</span></span>

  ```dotnetcli
  dotnet remove app/app.csproj reference lib/lib.csproj
  ```

- <span data-ttu-id="99226-121">Remover várias referências de projeto do projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="99226-121">Remove multiple project references from the project in the current directory:</span></span>

  ```dotnetcli
  dotnet remove reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- <span data-ttu-id="99226-122">Remova várias referências de projeto usando o padrão glob em Unix/Linux:</span><span class="sxs-lookup"><span data-stu-id="99226-122">Remove multiple project references using a glob pattern on Unix/Linux:</span></span>

  ```dotnetcli
  dotnet remove app/app.csproj reference **/*.csproj`
  ```
