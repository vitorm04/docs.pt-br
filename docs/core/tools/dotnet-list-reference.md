---
title: Comando dotnet list reference
description: O comando dotnet list reference fornece uma opção conveniente para listar referências projeto a projeto.
ms.date: 02/14/2020
ms.openlocfilehash: 43c4dbc94b33e717c6ba0a1c1c5317ac006f5bba
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503709"
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="dd133-103">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="dd133-103">dotnet list reference</span></span>

<span data-ttu-id="dd133-104">**Este artigo aplica-se a:** ✔️ SDK do .NET Core 2. x e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="dd133-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="dd133-105">Nome</span><span class="sxs-lookup"><span data-stu-id="dd133-105">Name</span></span>

<span data-ttu-id="dd133-106">`dotnet list reference` – lista as referências projeto a projeto.</span><span class="sxs-lookup"><span data-stu-id="dd133-106">`dotnet list reference` - Lists project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="dd133-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="dd133-107">Synopsis</span></span>

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="dd133-108">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="dd133-108">Description</span></span>

<span data-ttu-id="dd133-109">O comando `dotnet list reference` fornece uma opção conveniente para listar as referências de projeto de determinado projeto ou solução.</span><span class="sxs-lookup"><span data-stu-id="dd133-109">The `dotnet list reference` command provides a convenient option to list project references for a given project or solution.</span></span>

## <a name="arguments"></a><span data-ttu-id="dd133-110">Argumentos</span><span class="sxs-lookup"><span data-stu-id="dd133-110">Arguments</span></span>

* **`PROJECT | SOLUTION`**

  <span data-ttu-id="dd133-111">Especifica o arquivo de solução ou de projeto para usar para listar referências.</span><span class="sxs-lookup"><span data-stu-id="dd133-111">Specifies the project or solution file to use for listing references.</span></span> <span data-ttu-id="dd133-112">Se não é especificado, o comando pesquisa um arquivo de projeto no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="dd133-112">If not specified, the command searches the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="dd133-113">Opções</span><span class="sxs-lookup"><span data-stu-id="dd133-113">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="dd133-114">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="dd133-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="dd133-115">Exemplos</span><span class="sxs-lookup"><span data-stu-id="dd133-115">Examples</span></span>

* <span data-ttu-id="dd133-116">Listar as referências de projeto do projeto especificado:</span><span class="sxs-lookup"><span data-stu-id="dd133-116">List the project references for the specified project:</span></span>

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* <span data-ttu-id="dd133-117">Listar as referências de projeto do projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="dd133-117">List the project references for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet list reference
  ```
