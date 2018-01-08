---
title: "Comando dotnet nuget delete – CLI do .NET Core"
description: O comando dotnet-nuget-delete exclui ou retira da lista um pacote do servidor.
author: karann-msft
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 3c09556fe90a5c447b181bc1ac5b36f014399e4f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="eb4f9-103">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="eb4f9-103">dotnet nuget delete</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="eb4f9-104">Nome</span><span class="sxs-lookup"><span data-stu-id="eb4f9-104">Name</span></span>

<span data-ttu-id="eb4f9-105">`dotnet nuget delete` – Exclui ou retira da lista um pacote do servidor.</span><span class="sxs-lookup"><span data-stu-id="eb4f9-105">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="eb4f9-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="eb4f9-106">Synopsis</span></span>

`dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [-s|--source] [--non-interactive] [-k|--api-key] [--force-english-output] [-h|--help]`

## <a name="description"></a><span data-ttu-id="eb4f9-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="eb4f9-107">Description</span></span>

<span data-ttu-id="eb4f9-108">O comando `dotnet nuget delete` exclui ou retira da lista um pacote do servidor.</span><span class="sxs-lookup"><span data-stu-id="eb4f9-108">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="eb4f9-109">Para [nuget.org](https://www.nuget.org/), a ação é remover o pacote da lista.</span><span class="sxs-lookup"><span data-stu-id="eb4f9-109">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="eb4f9-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="eb4f9-110">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="eb4f9-111">Pacote a ser excluído.</span><span class="sxs-lookup"><span data-stu-id="eb4f9-111">Package to delete.</span></span>

`PACKAGE_VERSION`

<span data-ttu-id="eb4f9-112">Versão do pacote a ser excluído.</span><span class="sxs-lookup"><span data-stu-id="eb4f9-112">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="eb4f9-113">Opções</span><span class="sxs-lookup"><span data-stu-id="eb4f9-113">Options</span></span>

`-h|--help`

<span data-ttu-id="eb4f9-114">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="eb4f9-114">Prints out a short help for the command.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="eb4f9-115">Especifica a URL do servidor.</span><span class="sxs-lookup"><span data-stu-id="eb4f9-115">Specifies the server URL.</span></span> <span data-ttu-id="eb4f9-116">URLs com suporte para nuget.org incluem `http://www.nuget.org`, `http://www.nuget.org/api/v3` e `http://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="eb4f9-116">Supported URLs for nuget.org include `http://www.nuget.org`, `http://www.nuget.org/api/v3`, and `http://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="eb4f9-117">Para feeds privados, substitua o nome do host (por exemplo, `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="eb4f9-117">For private feeds, substitute the host name (for example, `%hostname%/api/v3`).</span></span>

`--non-interactive`

<span data-ttu-id="eb4f9-118">Não solicita entrada do usuário ou confirmações.</span><span class="sxs-lookup"><span data-stu-id="eb4f9-118">Doesn't prompt for user input or confirmations.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="eb4f9-119">A chave da API para o servidor.</span><span class="sxs-lookup"><span data-stu-id="eb4f9-119">The API key for the server.</span></span>

`--force-english-output`

<span data-ttu-id="eb4f9-120">Força a saída da linha de comando em inglês.</span><span class="sxs-lookup"><span data-stu-id="eb4f9-120">Forces command-line output in English.</span></span>

## <a name="examples"></a><span data-ttu-id="eb4f9-121">Exemplos</span><span class="sxs-lookup"><span data-stu-id="eb4f9-121">Examples</span></span>

<span data-ttu-id="eb4f9-122">Exclui a versão 1.0 do pacote `Microsoft.AspNetCore.Mvc`:</span><span class="sxs-lookup"><span data-stu-id="eb4f9-122">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0` 

<span data-ttu-id="eb4f9-123">Exclui a versão 1.0 do pacote `Microsoft.AspNetCore.Mvc`, não solicita ao usuário credenciais ou outra entrada:</span><span class="sxs-lookup"><span data-stu-id="eb4f9-123">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive`