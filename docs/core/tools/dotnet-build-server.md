---
title: Comando dotnet build-server
description: O comando dotnet build-server interage com os servidores iniciados por um build.
ms.date: 04/24/2019
ms.openlocfilehash: b2dfd5f317466f18d9246bd1fb281a92c42f6d9d
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168103"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="019f6-103">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="019f6-103">dotnet build-server</span></span>

<span data-ttu-id="019f6-104">**Este artigo se aplica a: ✓** SDK do .NET Core 2.1 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="019f6-104">**This article applies to: ✓** .NET Core 2.1 SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]
-->

## <a name="name"></a><span data-ttu-id="019f6-105">Nome</span><span class="sxs-lookup"><span data-stu-id="019f6-105">Name</span></span>

<span data-ttu-id="019f6-106">`dotnet build-server` – interage com servidores iniciados por um build.</span><span class="sxs-lookup"><span data-stu-id="019f6-106">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="019f6-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="019f6-107">Synopsis</span></span>

```console
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="019f6-108">Comandos</span><span class="sxs-lookup"><span data-stu-id="019f6-108">Commands</span></span>

* **`shutdown`**

  <span data-ttu-id="019f6-109">Desliga servidores de build iniciados por meio do dotnet.</span><span class="sxs-lookup"><span data-stu-id="019f6-109">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="019f6-110">Por padrão, todos os servidores estão desligados.</span><span class="sxs-lookup"><span data-stu-id="019f6-110">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="019f6-111">Opções</span><span class="sxs-lookup"><span data-stu-id="019f6-111">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="019f6-112">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="019f6-112">Prints out a short help for the command.</span></span>

* **`--msbuild`**

  <span data-ttu-id="019f6-113">Desliga o servidor de build do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="019f6-113">Shuts down the MSBuild build server.</span></span>

* **`--razor`**

  <span data-ttu-id="019f6-114">Desliga o servidor de build do Razor.</span><span class="sxs-lookup"><span data-stu-id="019f6-114">Shuts down the Razor build server.</span></span>

* **`--vbcscompiler`**

  <span data-ttu-id="019f6-115">Desliga o servidor de build do compilador do VB/C#.</span><span class="sxs-lookup"><span data-stu-id="019f6-115">Shuts down the VB/C# compiler build server.</span></span>
