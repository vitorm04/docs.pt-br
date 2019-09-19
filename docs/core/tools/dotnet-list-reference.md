---
title: Comando dotnet list reference
description: O comando dotnet list reference fornece uma opção conveniente para listar referências projeto a projeto.
ms.date: 06/26/2019
ms.openlocfilehash: b4b82ca1e7aeb2b73d9f99aff1c97452b2166770
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117679"
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="957b4-103">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="957b4-103">dotnet list reference</span></span>

<span data-ttu-id="957b4-104">**Este tópico aplica-se a: ✓** SDK do .NET Core 1.x e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="957b4-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="957b4-105">Nome</span><span class="sxs-lookup"><span data-stu-id="957b4-105">Name</span></span>

<span data-ttu-id="957b4-106">`dotnet list reference` – lista as referências projeto a projeto.</span><span class="sxs-lookup"><span data-stu-id="957b4-106">`dotnet list reference` - Lists project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="957b4-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="957b4-107">Synopsis</span></span>

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="957b4-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="957b4-108">Description</span></span>

<span data-ttu-id="957b4-109">O comando `dotnet list reference` fornece uma opção conveniente para listar as referências de projeto de determinado projeto ou solução.</span><span class="sxs-lookup"><span data-stu-id="957b4-109">The `dotnet list reference` command provides a convenient option to list project references for a given project or solution.</span></span>

## <a name="arguments"></a><span data-ttu-id="957b4-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="957b4-110">Arguments</span></span>

* **`PROJECT | SOLUTION`**

  <span data-ttu-id="957b4-111">Especifica o arquivo de solução ou de projeto para usar para listar referências.</span><span class="sxs-lookup"><span data-stu-id="957b4-111">Specifies the project or solution file to use for listing references.</span></span> <span data-ttu-id="957b4-112">Se não é especificado, o comando pesquisa um arquivo de projeto no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="957b4-112">If not specified, the command searches the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="957b4-113">Opções</span><span class="sxs-lookup"><span data-stu-id="957b4-113">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="957b4-114">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="957b4-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="957b4-115">Exemplos</span><span class="sxs-lookup"><span data-stu-id="957b4-115">Examples</span></span>

* <span data-ttu-id="957b4-116">Listar as referências de projeto do projeto especificado:</span><span class="sxs-lookup"><span data-stu-id="957b4-116">List the project references for the specified project:</span></span>

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* <span data-ttu-id="957b4-117">Listar as referências de projeto do projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="957b4-117">List the project references for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet list reference
  ```
