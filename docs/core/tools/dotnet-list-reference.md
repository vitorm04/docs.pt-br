---
title: "Comando dotnet list reference – CLI do .NET Core"
description: "O comando dotnet list reference fornece uma opção conveniente para listar referências projeto a projeto."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: a4ceadb6d070d7997e75b472624bbe2c1650396d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="96a34-103">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="96a34-103">dotnet list reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="96a34-104">Nome</span><span class="sxs-lookup"><span data-stu-id="96a34-104">Name</span></span>

<span data-ttu-id="96a34-105">`dotnet list reference` – lista as referências projeto a projeto.</span><span class="sxs-lookup"><span data-stu-id="96a34-105">`dotnet list reference` - Lists project to project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="96a34-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="96a34-106">Synopsis</span></span>

`dotnet list [<PROJECT>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="96a34-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="96a34-107">Description</span></span>

<span data-ttu-id="96a34-108">O comando `dotnet list reference` fornece uma opção conveniente para listar as referências de projeto de determinado projeto.</span><span class="sxs-lookup"><span data-stu-id="96a34-108">The `dotnet list reference` command provides a convenient option to list project references for a given project.</span></span>

## <a name="arguments"></a><span data-ttu-id="96a34-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="96a34-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="96a34-110">Especifica o arquivo de projeto para usar para listar referências.</span><span class="sxs-lookup"><span data-stu-id="96a34-110">Specifies the project file to use for listing references.</span></span> <span data-ttu-id="96a34-111">Se não for especificado, o comando procurará um arquivo de projeto no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="96a34-111">If not specified, the command will search the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="96a34-112">Opções</span><span class="sxs-lookup"><span data-stu-id="96a34-112">Options</span></span>

`-h|--help`

<span data-ttu-id="96a34-113">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="96a34-113">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="96a34-114">Exemplos</span><span class="sxs-lookup"><span data-stu-id="96a34-114">Examples</span></span>

<span data-ttu-id="96a34-115">Listar as referências de projeto do projeto especificado:</span><span class="sxs-lookup"><span data-stu-id="96a34-115">List the project references for the specified project:</span></span>

`dotnet list app/app.csproj reference`

<span data-ttu-id="96a34-116">Listar as referências de projeto do projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="96a34-116">List the project references for the project in the current directory:</span></span>

`dotnet list reference`
