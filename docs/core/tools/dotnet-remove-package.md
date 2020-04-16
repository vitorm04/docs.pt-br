---
title: Comando dotnet remove package
description: O comando dotnet remove package fornece uma opção conveniente para remover uma referência de pacote NuGet de um projeto.
ms.date: 02/14/2020
ms.openlocfilehash: fc74ac1364a0ed027b83dab270d382f238dc00e5
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463450"
---
# <a name="dotnet-remove-package"></a><span data-ttu-id="a38fe-103">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="a38fe-103">dotnet remove package</span></span>

<span data-ttu-id="a38fe-104">**Este artigo se aplica a:** ✔️ .NET Core 2.x SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="a38fe-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="a38fe-105">Nome</span><span class="sxs-lookup"><span data-stu-id="a38fe-105">Name</span></span>

<span data-ttu-id="a38fe-106">`dotnet remove package` – remove a referência de pacote de um arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="a38fe-106">`dotnet remove package` - Removes package reference from a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a38fe-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="a38fe-107">Synopsis</span></span>

```dotnetcli
dotnet remove [<PROJECT>] package <PACKAGE_NAME>

dotnet remove package -h|--help
```

## <a name="description"></a><span data-ttu-id="a38fe-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="a38fe-108">Description</span></span>

<span data-ttu-id="a38fe-109">O comando `dotnet remove package` fornece uma opção conveniente para remover uma referência de pacote NuGet de um projeto.</span><span class="sxs-lookup"><span data-stu-id="a38fe-109">The `dotnet remove package` command provides a convenient option to remove a NuGet package reference from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="a38fe-110">Argumentos</span><span class="sxs-lookup"><span data-stu-id="a38fe-110">Arguments</span></span>

`PROJECT`

<span data-ttu-id="a38fe-111">Especifica o arquivo do projeto.</span><span class="sxs-lookup"><span data-stu-id="a38fe-111">Specifies the project file.</span></span> <span data-ttu-id="a38fe-112">Se não for especificado, o comando pesquisará um no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="a38fe-112">If not specified, the command searches the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="a38fe-113">A referência de pacote a ser removida.</span><span class="sxs-lookup"><span data-stu-id="a38fe-113">The package reference to remove.</span></span>

## <a name="options"></a><span data-ttu-id="a38fe-114">Opções</span><span class="sxs-lookup"><span data-stu-id="a38fe-114">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="a38fe-115">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="a38fe-115">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="a38fe-116">Exemplos</span><span class="sxs-lookup"><span data-stu-id="a38fe-116">Examples</span></span>

- <span data-ttu-id="a38fe-117">Remover `Newtonsoft.Json` o pacote NuGet de um projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="a38fe-117">Remove `Newtonsoft.Json` NuGet package from a project in the current directory:</span></span>

  ```dotnetcli
  dotnet remove package Newtonsoft.Json
  ```
