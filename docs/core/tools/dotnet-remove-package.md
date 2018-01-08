---
title: "Comando dotnet remove package – CLI do .NET Core"
description: "O comando dotnet remove package fornece uma opção conveniente para remover uma referência de pacote NuGet de um projeto."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 1bc8d9cdc4db1f103b73116b43e630185a2c35de
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-remove-package"></a><span data-ttu-id="09862-103">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="09862-103">dotnet remove package</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="09862-104">Nome</span><span class="sxs-lookup"><span data-stu-id="09862-104">Name</span></span>

<span data-ttu-id="09862-105">`dotnet remove package` – remove a referência de pacote de um arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="09862-105">`dotnet remove package` - Removes package reference from a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="09862-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="09862-106">Synopsis</span></span>

`dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]`

## <a name="description"></a><span data-ttu-id="09862-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="09862-107">Description</span></span>

<span data-ttu-id="09862-108">O comando `dotnet remove package` fornece uma opção conveniente para remover uma referência de pacote NuGet de um projeto.</span><span class="sxs-lookup"><span data-stu-id="09862-108">The `dotnet remove package` command provides a convenient option to remove a NuGet package reference from a project.</span></span>

## <a name="arguments"></a><span data-ttu-id="09862-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="09862-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="09862-110">Especifica o arquivo do projeto.</span><span class="sxs-lookup"><span data-stu-id="09862-110">Specifies the project file.</span></span> <span data-ttu-id="09862-111">Se não for especificado, o comando irá procurar um no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="09862-111">If not specified, the command will search the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="09862-112">A referência de pacote a ser removida.</span><span class="sxs-lookup"><span data-stu-id="09862-112">The package reference to remove.</span></span>

## <a name="options"></a><span data-ttu-id="09862-113">Opções</span><span class="sxs-lookup"><span data-stu-id="09862-113">Options</span></span>

`-h|--help`

<span data-ttu-id="09862-114">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="09862-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="09862-115">Exemplos</span><span class="sxs-lookup"><span data-stu-id="09862-115">Examples</span></span>

<span data-ttu-id="09862-116">Remover o pacote NuGet `Newtonsoft.Json` de um projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="09862-116">Removes `Newtonsoft.Json` NuGet package from a project in the current directory:</span></span>

`dotnet remove package Newtonsoft.Json`
