---
title: Comando dotnet nuget delete
description: O comando dotnet-nuget-delete exclui ou retira da lista um pacote do servidor.
author: karann-msft
ms.date: 12/04/2018
ms.openlocfilehash: 827d295d7a52b6c9c82adbcf3d25281bd1cc98fd
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53168306"
---
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="76b74-103">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="76b74-103">dotnet nuget delete</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="76b74-104">Nome</span><span class="sxs-lookup"><span data-stu-id="76b74-104">Name</span></span>

<span data-ttu-id="76b74-105">`dotnet nuget delete` – Exclui ou retira da lista um pacote do servidor.</span><span class="sxs-lookup"><span data-stu-id="76b74-105">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="76b74-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="76b74-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="76b74-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="76b74-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [--interactive] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="76b74-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="76b74-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="76b74-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="76b74-109">Description</span></span>

<span data-ttu-id="76b74-110">O comando `dotnet nuget delete` exclui ou retira da lista um pacote do servidor.</span><span class="sxs-lookup"><span data-stu-id="76b74-110">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="76b74-111">Para [nuget.org](https://www.nuget.org/), a ação é remover o pacote da lista.</span><span class="sxs-lookup"><span data-stu-id="76b74-111">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="76b74-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="76b74-112">Arguments</span></span>

* **`PACKAGE_NAME`**

  <span data-ttu-id="76b74-113">Nome/ID do pacote a ser excluído.</span><span class="sxs-lookup"><span data-stu-id="76b74-113">Name/ID of the package to delete.</span></span>

* **`PACKAGE_VERSION`**

  <span data-ttu-id="76b74-114">Versão do pacote a ser excluído.</span><span class="sxs-lookup"><span data-stu-id="76b74-114">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="76b74-115">Opções</span><span class="sxs-lookup"><span data-stu-id="76b74-115">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="76b74-116">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="76b74-116">.NET Core 2.x</span></span>](#tab/netcore2x)

* **`--force-english-output`**

  <span data-ttu-id="76b74-117">Força a execução do aplicativo usando uma cultura invariável com base em inglês.</span><span class="sxs-lookup"><span data-stu-id="76b74-117">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="76b74-118">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="76b74-118">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="76b74-119">Permite que o comando bloqueie e exija ação manual para operações como a autenticação.</span><span class="sxs-lookup"><span data-stu-id="76b74-119">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="76b74-120">Opção disponível desde o SDK 2.2 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="76b74-120">Option available since .NET Core 2.2 SDK.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="76b74-121">A chave da API para o servidor.</span><span class="sxs-lookup"><span data-stu-id="76b74-121">The API key for the server.</span></span>

* **`--no-service-endpoint`**

  <span data-ttu-id="76b74-122">Não acrescenta "api/v2/package" à URL de origem.</span><span class="sxs-lookup"><span data-stu-id="76b74-122">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="76b74-123">Opção disponível desde o SDK do .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="76b74-123">Option available since .NET Core 2.1 SDK.</span></span>

* **`--non-interactive`**

  <span data-ttu-id="76b74-124">Não solicita entrada do usuário ou confirmações.</span><span class="sxs-lookup"><span data-stu-id="76b74-124">Doesn't prompt for user input or confirmations.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="76b74-125">Especifica a URL do servidor.</span><span class="sxs-lookup"><span data-stu-id="76b74-125">Specifies the server URL.</span></span> <span data-ttu-id="76b74-126">URLs com suporte para nuget.org incluem `https://www.nuget.org`, `https://www.nuget.org/api/v3` e `https://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="76b74-126">Supported URLs for nuget.org include `https://www.nuget.org`, `https://www.nuget.org/api/v3`, and `https://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="76b74-127">Para feeds privados, substitua o nome do host (por exemplo, `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="76b74-127">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="76b74-128">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="76b74-128">.NET Core 1.x</span></span>](#tab/netcore1x)

* **`--force-english-output`**

  <span data-ttu-id="76b74-129">Força a execução do aplicativo usando uma cultura invariável com base em inglês.</span><span class="sxs-lookup"><span data-stu-id="76b74-129">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="76b74-130">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="76b74-130">Prints out a short help for the command.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="76b74-131">A chave da API para o servidor.</span><span class="sxs-lookup"><span data-stu-id="76b74-131">The API key for the server.</span></span>

* **`--non-interactive`**

  <span data-ttu-id="76b74-132">Não solicita entrada do usuário ou confirmações.</span><span class="sxs-lookup"><span data-stu-id="76b74-132">Doesn't prompt for user input or confirmations.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="76b74-133">Especifica a URL do servidor.</span><span class="sxs-lookup"><span data-stu-id="76b74-133">Specifies the server URL.</span></span> <span data-ttu-id="76b74-134">URLs com suporte para nuget.org incluem `https://www.nuget.org`, `https://www.nuget.org/api/v3` e `https://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="76b74-134">Supported URLs for nuget.org include `https://www.nuget.org`, `https://www.nuget.org/api/v3`, and `https://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="76b74-135">Para feeds privados, substitua o nome do host (por exemplo, `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="76b74-135">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

---

## <a name="examples"></a><span data-ttu-id="76b74-136">Exemplos</span><span class="sxs-lookup"><span data-stu-id="76b74-136">Examples</span></span>

* <span data-ttu-id="76b74-137">Exclui a versão 1.0 do pacote `Microsoft.AspNetCore.Mvc`:</span><span class="sxs-lookup"><span data-stu-id="76b74-137">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

  ```console
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* <span data-ttu-id="76b74-138">Exclui a versão 1.0 do pacote `Microsoft.AspNetCore.Mvc`, não solicita ao usuário credenciais ou outra entrada:</span><span class="sxs-lookup"><span data-stu-id="76b74-138">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

  ```console
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```