---
title: Comando dotnet build-server
description: O comando dotnet build-server interage com os servidores iniciados por um build.
ms.date: 12/04/2018
ms.openlocfilehash: 7f78a0cae6e3297f3084754dc56b0da4eac38caf
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169645"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="ab9ff-103">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="ab9ff-103">dotnet build-server</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="ab9ff-104">Nome</span><span class="sxs-lookup"><span data-stu-id="ab9ff-104">Name</span></span>

<span data-ttu-id="ab9ff-105">`dotnet build-server` – interage com servidores iniciados por um build.</span><span class="sxs-lookup"><span data-stu-id="ab9ff-105">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ab9ff-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="ab9ff-106">Synopsis</span></span>

```
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="ab9ff-107">Comandos</span><span class="sxs-lookup"><span data-stu-id="ab9ff-107">Commands</span></span>

* **`shutdown`**

  <span data-ttu-id="ab9ff-108">Desliga servidores de build iniciados por meio do dotnet.</span><span class="sxs-lookup"><span data-stu-id="ab9ff-108">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="ab9ff-109">Por padrão, todos os servidores estão desligados.</span><span class="sxs-lookup"><span data-stu-id="ab9ff-109">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="ab9ff-110">Opções</span><span class="sxs-lookup"><span data-stu-id="ab9ff-110">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="ab9ff-111">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="ab9ff-111">Prints out a short help for the command.</span></span>

* **`--msbuild`**

  <span data-ttu-id="ab9ff-112">Desliga o servidor de build do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="ab9ff-112">Shuts down the MSBuild build server.</span></span>

* **`--razor`**

  <span data-ttu-id="ab9ff-113">Desliga o servidor de build do Razor.</span><span class="sxs-lookup"><span data-stu-id="ab9ff-113">Shuts down the Razor build server.</span></span>

* **`--vbcscompiler`**

  <span data-ttu-id="ab9ff-114">Desliga o servidor de build do compilador do VB/C#.</span><span class="sxs-lookup"><span data-stu-id="ab9ff-114">Shuts down the VB/C# compiler build server.</span></span>