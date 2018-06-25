---
title: Comando dotnet nuget delete – CLI do .NET Core
description: O comando dotnet-nuget-delete exclui ou retira da lista um pacote do servidor.
author: karann-msft
ms.author: mairaw
ms.date: 06/01/2018
ms.openlocfilehash: 1b58136d0bc04947f0a5baba320e5e6b3e45e2f1
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34728408"
---
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="985c4-103">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="985c4-103">dotnet nuget delete</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="985c4-104">Nome</span><span class="sxs-lookup"><span data-stu-id="985c4-104">Name</span></span>

<span data-ttu-id="985c4-105">`dotnet nuget delete` – Exclui ou retira da lista um pacote do servidor.</span><span class="sxs-lookup"><span data-stu-id="985c4-105">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="985c4-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="985c4-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="985c4-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="985c4-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="985c4-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="985c4-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="985c4-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="985c4-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="985c4-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="985c4-110">Description</span></span>

<span data-ttu-id="985c4-111">O comando `dotnet nuget delete` exclui ou retira da lista um pacote do servidor.</span><span class="sxs-lookup"><span data-stu-id="985c4-111">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="985c4-112">Para [nuget.org](https://www.nuget.org/), a ação é remover o pacote da lista.</span><span class="sxs-lookup"><span data-stu-id="985c4-112">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="985c4-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="985c4-113">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="985c4-114">Nome/ID do pacote a ser excluído.</span><span class="sxs-lookup"><span data-stu-id="985c4-114">Name/ID of the package to delete.</span></span>

`PACKAGE_VERSION`

<span data-ttu-id="985c4-115">Versão do pacote a ser excluído.</span><span class="sxs-lookup"><span data-stu-id="985c4-115">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="985c4-116">Opções</span><span class="sxs-lookup"><span data-stu-id="985c4-116">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="985c4-117">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="985c4-117">.NET Core 2.1</span></span>](#tab/netcore21)

`--force-english-output`

 <span data-ttu-id="985c4-118">Força a execução do aplicativo usando uma cultura invariável com base em inglês.</span><span class="sxs-lookup"><span data-stu-id="985c4-118">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="985c4-119">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="985c4-119">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="985c4-120">A chave da API para o servidor.</span><span class="sxs-lookup"><span data-stu-id="985c4-120">The API key for the server.</span></span>

<span data-ttu-id="985c4-121">`--no-service-endpoint` Não acrescenta "api/v2/package" à URL de origem.</span><span class="sxs-lookup"><span data-stu-id="985c4-121">`--no-service-endpoint` Doesn't append "api/v2/package" to the source URL.</span></span>

`--non-interactive`

<span data-ttu-id="985c4-122">Não solicita entrada do usuário ou confirmações.</span><span class="sxs-lookup"><span data-stu-id="985c4-122">Doesn't prompt for user input or confirmations.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="985c4-123">Especifica a URL do servidor.</span><span class="sxs-lookup"><span data-stu-id="985c4-123">Specifies the server URL.</span></span> <span data-ttu-id="985c4-124">URLs com suporte para nuget.org incluem `http://www.nuget.org`, `http://www.nuget.org/api/v3` e `http://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="985c4-124">Supported URLs for nuget.org include `http://www.nuget.org`, `http://www.nuget.org/api/v3`, and `http://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="985c4-125">Para feeds privados, substitua o nome do host (por exemplo, `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="985c4-125">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="985c4-126">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="985c4-126">.NET Core 2.0</span></span>](#tab/netcore20)

`--force-english-output`

 <span data-ttu-id="985c4-127">Força a execução do aplicativo usando uma cultura invariável com base em inglês.</span><span class="sxs-lookup"><span data-stu-id="985c4-127">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="985c4-128">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="985c4-128">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="985c4-129">A chave da API para o servidor.</span><span class="sxs-lookup"><span data-stu-id="985c4-129">The API key for the server.</span></span>

`--non-interactive`

<span data-ttu-id="985c4-130">Não solicita entrada do usuário ou confirmações.</span><span class="sxs-lookup"><span data-stu-id="985c4-130">Doesn't prompt for user input or confirmations.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="985c4-131">Especifica a URL do servidor.</span><span class="sxs-lookup"><span data-stu-id="985c4-131">Specifies the server URL.</span></span> <span data-ttu-id="985c4-132">URLs com suporte para nuget.org incluem `http://www.nuget.org`, `http://www.nuget.org/api/v3` e `http://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="985c4-132">Supported URLs for nuget.org include `http://www.nuget.org`, `http://www.nuget.org/api/v3`, and `http://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="985c4-133">Para feeds privados, substitua o nome do host (por exemplo, `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="985c4-133">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="985c4-134">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="985c4-134">.NET Core 1.x</span></span>](#tab/netcore1x)

`--force-english-output`

 <span data-ttu-id="985c4-135">Força a execução do aplicativo usando uma cultura invariável com base em inglês.</span><span class="sxs-lookup"><span data-stu-id="985c4-135">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="985c4-136">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="985c4-136">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="985c4-137">A chave da API para o servidor.</span><span class="sxs-lookup"><span data-stu-id="985c4-137">The API key for the server.</span></span>

`--non-interactive`

<span data-ttu-id="985c4-138">Não solicita entrada do usuário ou confirmações.</span><span class="sxs-lookup"><span data-stu-id="985c4-138">Doesn't prompt for user input or confirmations.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="985c4-139">Especifica a URL do servidor.</span><span class="sxs-lookup"><span data-stu-id="985c4-139">Specifies the server URL.</span></span> <span data-ttu-id="985c4-140">URLs com suporte para nuget.org incluem `http://www.nuget.org`, `http://www.nuget.org/api/v3` e `http://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="985c4-140">Supported URLs for nuget.org include `http://www.nuget.org`, `http://www.nuget.org/api/v3`, and `http://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="985c4-141">Para feeds privados, substitua o nome do host (por exemplo, `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="985c4-141">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

---

## <a name="examples"></a><span data-ttu-id="985c4-142">Exemplos</span><span class="sxs-lookup"><span data-stu-id="985c4-142">Examples</span></span>

<span data-ttu-id="985c4-143">Exclui a versão 1.0 do pacote `Microsoft.AspNetCore.Mvc`:</span><span class="sxs-lookup"><span data-stu-id="985c4-143">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0`

<span data-ttu-id="985c4-144">Exclui a versão 1.0 do pacote `Microsoft.AspNetCore.Mvc`, não solicita ao usuário credenciais ou outra entrada:</span><span class="sxs-lookup"><span data-stu-id="985c4-144">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

`dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive`
