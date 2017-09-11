---
title: "Comando dotnet list reference – CLI do .NET Core"
description: "O comando dotnet list reference fornece uma opção conveniente para listar referências projeto a projeto."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.translationtype: HT
ms.sourcegitcommit: a19ab54a6cc44bd7acd1e40a4ca94da52bf14297
ms.openlocfilehash: b3e903c15a7486faa279d47ad5e2e00c090b19af
ms.contentlocale: pt-br
ms.lasthandoff: 08/14/2017

---
# <a name="dotnet-list-reference"></a><span data-ttu-id="a53a9-103">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="a53a9-103">dotnet list reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="a53a9-104">Nome</span><span class="sxs-lookup"><span data-stu-id="a53a9-104">Name</span></span>

<span data-ttu-id="a53a9-105">`dotnet list reference` – lista as referências projeto a projeto.</span><span class="sxs-lookup"><span data-stu-id="a53a9-105">`dotnet list reference` - Lists project to project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a53a9-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="a53a9-106">Synopsis</span></span>

`dotnet list [<PROJECT>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="a53a9-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a53a9-107">Description</span></span>

<span data-ttu-id="a53a9-108">O comando `dotnet list reference` fornece uma opção conveniente para listar as referências de projeto de determinado projeto.</span><span class="sxs-lookup"><span data-stu-id="a53a9-108">The `dotnet list reference` command provides a convenient option to list project references for a given project.</span></span>

## <a name="arguments"></a><span data-ttu-id="a53a9-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="a53a9-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="a53a9-110">Especifica o arquivo de projeto para usar para listar referências.</span><span class="sxs-lookup"><span data-stu-id="a53a9-110">Specifies the project file to use for listing references.</span></span> <span data-ttu-id="a53a9-111">Se não for especificado, o comando procurará um arquivo de projeto no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="a53a9-111">If not specified, the command will search the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="a53a9-112">Opções</span><span class="sxs-lookup"><span data-stu-id="a53a9-112">Options</span></span>

`-h|--help`

<span data-ttu-id="a53a9-113">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="a53a9-113">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="a53a9-114">Exemplos</span><span class="sxs-lookup"><span data-stu-id="a53a9-114">Examples</span></span>

<span data-ttu-id="a53a9-115">Listar as referências de projeto do projeto especificado:</span><span class="sxs-lookup"><span data-stu-id="a53a9-115">List the project references for the specified project:</span></span>

`dotnet list app/app.csproj reference`

<span data-ttu-id="a53a9-116">Listar as referências de projeto do projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="a53a9-116">List the project references for the project in the current directory:</span></span>

`dotnet list reference`

