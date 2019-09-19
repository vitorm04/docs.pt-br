---
title: Comando dotnet nuget delete
description: O comando dotnet-nuget-delete exclui ou retira da lista um pacote do servidor.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 79634baa9d6d7ff1f388f6a794ffd816687be105
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117637"
---
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="fc7b5-103">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="fc7b5-103">dotnet nuget delete</span></span>

<span data-ttu-id="fc7b5-104">**Este tópico aplica-se a: ✓** SDK do .NET Core 1.x e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="fc7b5-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="fc7b5-105">Nome</span><span class="sxs-lookup"><span data-stu-id="fc7b5-105">Name</span></span>

<span data-ttu-id="fc7b5-106">`dotnet nuget delete` – Exclui ou retira da lista um pacote do servidor.</span><span class="sxs-lookup"><span data-stu-id="fc7b5-106">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="fc7b5-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="fc7b5-107">Synopsis</span></span>

```dotnetcli
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [--interactive] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```

## <a name="description"></a><span data-ttu-id="fc7b5-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="fc7b5-108">Description</span></span>

<span data-ttu-id="fc7b5-109">O comando `dotnet nuget delete` exclui ou retira da lista um pacote do servidor.</span><span class="sxs-lookup"><span data-stu-id="fc7b5-109">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="fc7b5-110">Para [nuget.org](https://www.nuget.org/), a ação é remover o pacote da lista.</span><span class="sxs-lookup"><span data-stu-id="fc7b5-110">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="fc7b5-111">Arguments</span><span class="sxs-lookup"><span data-stu-id="fc7b5-111">Arguments</span></span>

* **`PACKAGE_NAME`**

  <span data-ttu-id="fc7b5-112">Nome/ID do pacote a ser excluído.</span><span class="sxs-lookup"><span data-stu-id="fc7b5-112">Name/ID of the package to delete.</span></span>

* **`PACKAGE_VERSION`**

  <span data-ttu-id="fc7b5-113">Versão do pacote a ser excluído.</span><span class="sxs-lookup"><span data-stu-id="fc7b5-113">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="fc7b5-114">Opções</span><span class="sxs-lookup"><span data-stu-id="fc7b5-114">Options</span></span>

* **`--force-english-output`**

  <span data-ttu-id="fc7b5-115">Força a execução do aplicativo usando uma cultura invariável com base em inglês.</span><span class="sxs-lookup"><span data-stu-id="fc7b5-115">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="fc7b5-116">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="fc7b5-116">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="fc7b5-117">Permite que o comando bloqueie e exija ação manual para operações como a autenticação.</span><span class="sxs-lookup"><span data-stu-id="fc7b5-117">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="fc7b5-118">Opção disponível desde o SDK 2.2 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fc7b5-118">Option available since .NET Core 2.2 SDK.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="fc7b5-119">A chave da API para o servidor.</span><span class="sxs-lookup"><span data-stu-id="fc7b5-119">The API key for the server.</span></span>

* **`--no-service-endpoint`**

  <span data-ttu-id="fc7b5-120">Não acrescenta "api/v2/package" à URL de origem.</span><span class="sxs-lookup"><span data-stu-id="fc7b5-120">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="fc7b5-121">Opção disponível desde o SDK do .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="fc7b5-121">Option available since .NET Core 2.1 SDK.</span></span>

* **`--non-interactive`**

  <span data-ttu-id="fc7b5-122">Não solicita entrada do usuário ou confirmações.</span><span class="sxs-lookup"><span data-stu-id="fc7b5-122">Doesn't prompt for user input or confirmations.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="fc7b5-123">Especifica a URL do servidor.</span><span class="sxs-lookup"><span data-stu-id="fc7b5-123">Specifies the server URL.</span></span> <span data-ttu-id="fc7b5-124">URLs com suporte para nuget.org incluem `https://www.nuget.org`, `https://www.nuget.org/api/v3` e `https://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="fc7b5-124">Supported URLs for nuget.org include `https://www.nuget.org`, `https://www.nuget.org/api/v3`, and `https://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="fc7b5-125">Para feeds privados, substitua o nome do host (por exemplo, `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="fc7b5-125">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

## <a name="examples"></a><span data-ttu-id="fc7b5-126">Exemplos</span><span class="sxs-lookup"><span data-stu-id="fc7b5-126">Examples</span></span>

* <span data-ttu-id="fc7b5-127">Exclui a versão 1.0 do pacote `Microsoft.AspNetCore.Mvc`:</span><span class="sxs-lookup"><span data-stu-id="fc7b5-127">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* <span data-ttu-id="fc7b5-128">Exclui a versão 1.0 do pacote `Microsoft.AspNetCore.Mvc`, não solicita ao usuário credenciais ou outra entrada:</span><span class="sxs-lookup"><span data-stu-id="fc7b5-128">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```
