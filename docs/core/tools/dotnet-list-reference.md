---
title: Comando dotnet list reference
description: O comando dotnet list reference fornece uma opção conveniente para listar referências projeto a projeto.
ms.date: 02/14/2020
ms.openlocfilehash: b9b34c17102c6218f3d99f6e2620e99f70140284
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83802759"
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="c71be-103">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="c71be-103">dotnet list reference</span></span>

<span data-ttu-id="c71be-104">**Este artigo aplica-se a:** ✔️ SDK do .NET Core 2. x e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="c71be-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="c71be-105">Nome</span><span class="sxs-lookup"><span data-stu-id="c71be-105">Name</span></span>

<span data-ttu-id="c71be-106">`dotnet list reference` – lista as referências projeto a projeto.</span><span class="sxs-lookup"><span data-stu-id="c71be-106">`dotnet list reference` - Lists project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c71be-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="c71be-107">Synopsis</span></span>

```dotnetcli
dotnet list [<PROJECT>] reference

dotnet list -h|--help
```

## <a name="description"></a><span data-ttu-id="c71be-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="c71be-108">Description</span></span>

<span data-ttu-id="c71be-109">O comando `dotnet list reference` fornece uma opção conveniente para listar as referências de projeto de determinado projeto.</span><span class="sxs-lookup"><span data-stu-id="c71be-109">The `dotnet list reference` command provides a convenient option to list project references for a given project.</span></span>

## <a name="arguments"></a><span data-ttu-id="c71be-110">Argumentos</span><span class="sxs-lookup"><span data-stu-id="c71be-110">Arguments</span></span>

* **`PROJECT`**

  <span data-ttu-id="c71be-111">O arquivo de projeto no qual operar.</span><span class="sxs-lookup"><span data-stu-id="c71be-111">The project file to operate on.</span></span> <span data-ttu-id="c71be-112">Se um arquivo não for especificado, o comando pesquisará o diretório atual em busca de um.</span><span class="sxs-lookup"><span data-stu-id="c71be-112">If a file is not specified, the command will search the current directory for one.</span></span>

## <a name="options"></a><span data-ttu-id="c71be-113">Opções</span><span class="sxs-lookup"><span data-stu-id="c71be-113">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="c71be-114">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="c71be-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="c71be-115">Exemplos</span><span class="sxs-lookup"><span data-stu-id="c71be-115">Examples</span></span>

* <span data-ttu-id="c71be-116">Listar as referências de projeto do projeto especificado:</span><span class="sxs-lookup"><span data-stu-id="c71be-116">List the project references for the specified project:</span></span>

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* <span data-ttu-id="c71be-117">Listar as referências de projeto do projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="c71be-117">List the project references for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet list reference
  ```
