---
title: Comando dotnet list reference
description: O comando dotnet list reference fornece uma opção conveniente para listar referências projeto a projeto.
ms.date: 12/03/2018
ms.openlocfilehash: d22ea27f8e8f6b94d763e44a6d8644f814663797
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169827"
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="fd2e4-103">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="fd2e4-103">dotnet list reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="fd2e4-104">Nome</span><span class="sxs-lookup"><span data-stu-id="fd2e4-104">Name</span></span>

<span data-ttu-id="fd2e4-105">`dotnet list reference` – lista as referências projeto a projeto.</span><span class="sxs-lookup"><span data-stu-id="fd2e4-105">`dotnet list reference` - Lists project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="fd2e4-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="fd2e4-106">Synopsis</span></span>

`dotnet list [<PROJECT>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="fd2e4-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="fd2e4-107">Description</span></span>

<span data-ttu-id="fd2e4-108">O comando `dotnet list reference` fornece uma opção conveniente para listar as referências de projeto de determinado projeto ou solução.</span><span class="sxs-lookup"><span data-stu-id="fd2e4-108">The `dotnet list reference` command provides a convenient option to list project references for a given project or solution.</span></span>

## <a name="arguments"></a><span data-ttu-id="fd2e4-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="fd2e4-109">Arguments</span></span>

* **`PROJECT`**

  <span data-ttu-id="fd2e4-110">Especifica o arquivo de projeto para usar para listar referências.</span><span class="sxs-lookup"><span data-stu-id="fd2e4-110">Specifies the project file to use for listing references.</span></span> <span data-ttu-id="fd2e4-111">Se não é especificado, o comando pesquisa um arquivo de projeto no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="fd2e4-111">If not specified, the command searches the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="fd2e4-112">Opções</span><span class="sxs-lookup"><span data-stu-id="fd2e4-112">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="fd2e4-113">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="fd2e4-113">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="fd2e4-114">Exemplos</span><span class="sxs-lookup"><span data-stu-id="fd2e4-114">Examples</span></span>

* <span data-ttu-id="fd2e4-115">Listar as referências de projeto do projeto especificado:</span><span class="sxs-lookup"><span data-stu-id="fd2e4-115">List the project references for the specified project:</span></span>

  ```console
  dotnet list app/app.csproj reference
  ```

* <span data-ttu-id="fd2e4-116">Listar as referências de projeto do projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="fd2e4-116">List the project references for the project in the current directory:</span></span>

  ```console
  dotnet list reference
  ```