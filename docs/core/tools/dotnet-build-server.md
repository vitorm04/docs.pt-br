---
title: Comando dotnet build-server – CLI do .NET Core
description: O comando dotnet build-server interage com os servidores iniciados por um build.
ms.date: 12/04/2018
ms.openlocfilehash: 2746ade12cc819089258483e84a8c0f02a64c755
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53125672"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="0ae8d-103">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="0ae8d-103">dotnet build-server</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="0ae8d-104">Nome</span><span class="sxs-lookup"><span data-stu-id="0ae8d-104">Name</span></span>

<span data-ttu-id="0ae8d-105">`dotnet build-server` – interage com servidores iniciados por um build.</span><span class="sxs-lookup"><span data-stu-id="0ae8d-105">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0ae8d-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="0ae8d-106">Synopsis</span></span>

```
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="0ae8d-107">Comandos</span><span class="sxs-lookup"><span data-stu-id="0ae8d-107">Commands</span></span>

* **`shutdown`**

  <span data-ttu-id="0ae8d-108">Desliga servidores de build iniciados por meio do dotnet.</span><span class="sxs-lookup"><span data-stu-id="0ae8d-108">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="0ae8d-109">Por padrão, todos os servidores estão desligados.</span><span class="sxs-lookup"><span data-stu-id="0ae8d-109">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="0ae8d-110">Opções</span><span class="sxs-lookup"><span data-stu-id="0ae8d-110">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="0ae8d-111">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="0ae8d-111">Prints out a short help for the command.</span></span>

* **`--msbuild`**

  <span data-ttu-id="0ae8d-112">Desliga o servidor de build do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="0ae8d-112">Shuts down the MSBuild build server.</span></span>

* **`--razor`**

  <span data-ttu-id="0ae8d-113">Desliga o servidor de build do Razor.</span><span class="sxs-lookup"><span data-stu-id="0ae8d-113">Shuts down the Razor build server.</span></span>

* **`--vbcscompiler`**

  <span data-ttu-id="0ae8d-114">Desliga o servidor de build do compilador do VB/C#.</span><span class="sxs-lookup"><span data-stu-id="0ae8d-114">Shuts down the VB/C# compiler build server.</span></span>