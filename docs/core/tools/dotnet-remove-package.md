---
title: Comando dotnet remove package
description: O comando dotnet remove package fornece uma opção conveniente para remover uma referência de pacote NuGet de um projeto.
ms.date: 05/29/2018
ms.openlocfilehash: 4cc8ac927b761547dc5e53be9abeba827bf1e1d9
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53168722"
---
# <a name="dotnet-remove-package"></a><span data-ttu-id="024a4-103">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="024a4-103">dotnet remove package</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="024a4-104">Nome</span><span class="sxs-lookup"><span data-stu-id="024a4-104">Name</span></span>

<span data-ttu-id="024a4-105">`dotnet remove package` – remove a referência de pacote de um arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="024a4-105">`dotnet remove package` - Removes package reference from a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="024a4-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="024a4-106">Synopsis</span></span>

`dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]`

## <a name="description"></a><span data-ttu-id="024a4-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="024a4-107">Description</span></span>

<span data-ttu-id="024a4-108">O comando `dotnet remove package` fornece uma opção conveniente para remover uma referência de pacote NuGet de um projeto.</span><span class="sxs-lookup"><span data-stu-id="024a4-108">The `dotnet remove package` command provides a convenient option to remove a NuGet package reference from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="024a4-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="024a4-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="024a4-110">Especifica o arquivo do projeto.</span><span class="sxs-lookup"><span data-stu-id="024a4-110">Specifies the project file.</span></span> <span data-ttu-id="024a4-111">Se não for especificado, o comando pesquisará um no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="024a4-111">If not specified, the command searches the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="024a4-112">A referência de pacote a ser removida.</span><span class="sxs-lookup"><span data-stu-id="024a4-112">The package reference to remove.</span></span>

## <a name="options"></a><span data-ttu-id="024a4-113">Opções</span><span class="sxs-lookup"><span data-stu-id="024a4-113">Options</span></span>

`-h|--help`

<span data-ttu-id="024a4-114">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="024a4-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="024a4-115">Exemplos</span><span class="sxs-lookup"><span data-stu-id="024a4-115">Examples</span></span>

<span data-ttu-id="024a4-116">Remover o pacote NuGet `Newtonsoft.Json` de um projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="024a4-116">Removes `Newtonsoft.Json` NuGet package from a project in the current directory:</span></span>

`dotnet remove package Newtonsoft.Json`