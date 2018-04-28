---
title: Comando dotnet list reference – CLI do .NET Core
description: O comando dotnet list reference fornece uma opção conveniente para listar referências projeto a projeto.
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 946d3d523443fbe673b95dba95dbca327fde1699
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="f5bff-103">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="f5bff-103">dotnet list reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="f5bff-104">Nome</span><span class="sxs-lookup"><span data-stu-id="f5bff-104">Name</span></span>

<span data-ttu-id="f5bff-105">`dotnet list reference` – lista as referências projeto a projeto.</span><span class="sxs-lookup"><span data-stu-id="f5bff-105">`dotnet list reference` - Lists project to project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f5bff-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="f5bff-106">Synopsis</span></span>

`dotnet list [<PROJECT>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="f5bff-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f5bff-107">Description</span></span>

<span data-ttu-id="f5bff-108">O comando `dotnet list reference` fornece uma opção conveniente para listar as referências de projeto de determinado projeto.</span><span class="sxs-lookup"><span data-stu-id="f5bff-108">The `dotnet list reference` command provides a convenient option to list project references for a given project.</span></span>

## <a name="arguments"></a><span data-ttu-id="f5bff-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="f5bff-109">Arguments</span></span>

`PROJECT`

<span data-ttu-id="f5bff-110">Especifica o arquivo de projeto para usar para listar referências.</span><span class="sxs-lookup"><span data-stu-id="f5bff-110">Specifies the project file to use for listing references.</span></span> <span data-ttu-id="f5bff-111">Se não for especificado, o comando procurará um arquivo de projeto no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="f5bff-111">If not specified, the command will search the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="f5bff-112">Opções</span><span class="sxs-lookup"><span data-stu-id="f5bff-112">Options</span></span>

`-h|--help`

<span data-ttu-id="f5bff-113">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="f5bff-113">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="f5bff-114">Exemplos</span><span class="sxs-lookup"><span data-stu-id="f5bff-114">Examples</span></span>

<span data-ttu-id="f5bff-115">Listar as referências de projeto do projeto especificado:</span><span class="sxs-lookup"><span data-stu-id="f5bff-115">List the project references for the specified project:</span></span>

`dotnet list app/app.csproj reference`

<span data-ttu-id="f5bff-116">Listar as referências de projeto do projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="f5bff-116">List the project references for the project in the current directory:</span></span>

`dotnet list reference`
