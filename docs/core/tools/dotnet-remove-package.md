---
title: Comando dotnet remove package
description: O comando dotnet remove package fornece uma opção conveniente para remover uma referência de pacote NuGet de um projeto.
ms.date: 05/29/2018
ms.openlocfilehash: cbdeacff78ef20c9a73010e10a771a724b23792e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632428"
---
# <a name="dotnet-remove-package"></a><span data-ttu-id="da6cc-103">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="da6cc-103">dotnet remove package</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="da6cc-104">Nome</span><span class="sxs-lookup"><span data-stu-id="da6cc-104">Name</span></span>

<span data-ttu-id="da6cc-105">`dotnet remove package` – remove a referência de pacote de um arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="da6cc-105">`dotnet remove package` - Removes package reference from a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="da6cc-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="da6cc-106">Synopsis</span></span>

`dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]`

## <a name="description"></a><span data-ttu-id="da6cc-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="da6cc-107">Description</span></span>

<span data-ttu-id="da6cc-108">O comando `dotnet remove package` fornece uma opção conveniente para remover uma referência de pacote NuGet de um projeto.</span><span class="sxs-lookup"><span data-stu-id="da6cc-108">The `dotnet remove package` command provides a convenient option to remove a NuGet package reference from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="da6cc-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="da6cc-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="da6cc-110">Especifica o arquivo do projeto.</span><span class="sxs-lookup"><span data-stu-id="da6cc-110">Specifies the project file.</span></span> <span data-ttu-id="da6cc-111">Se não for especificado, o comando pesquisará um no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="da6cc-111">If not specified, the command searches the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="da6cc-112">A referência de pacote a ser removida.</span><span class="sxs-lookup"><span data-stu-id="da6cc-112">The package reference to remove.</span></span>

## <a name="options"></a><span data-ttu-id="da6cc-113">Opções</span><span class="sxs-lookup"><span data-stu-id="da6cc-113">Options</span></span>

`-h|--help`

<span data-ttu-id="da6cc-114">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="da6cc-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="da6cc-115">Exemplos</span><span class="sxs-lookup"><span data-stu-id="da6cc-115">Examples</span></span>

<span data-ttu-id="da6cc-116">Remover o pacote NuGet `Newtonsoft.Json` de um projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="da6cc-116">Removes `Newtonsoft.Json` NuGet package from a project in the current directory:</span></span>

`dotnet remove package Newtonsoft.Json`
