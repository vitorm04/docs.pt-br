---
title: Comando dotnet build-server
description: O comando dotnet build-server interage com os servidores iniciados por um build.
ms.date: 04/24/2019
ms.openlocfilehash: e77a4d9f49f555ac847bb13380380599eef881b1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734383"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="42cf8-103">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="42cf8-103">dotnet build-server</span></span>

<span data-ttu-id="42cf8-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,1 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="42cf8-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]
-->

## <a name="name"></a><span data-ttu-id="42cf8-105">{1&gt;Nome&lt;1}</span><span class="sxs-lookup"><span data-stu-id="42cf8-105">Name</span></span>

<span data-ttu-id="42cf8-106">`dotnet build-server` – interage com servidores iniciados por um build.</span><span class="sxs-lookup"><span data-stu-id="42cf8-106">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="42cf8-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="42cf8-107">Synopsis</span></span>

```dotnetcli
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="42cf8-108">Commands</span><span class="sxs-lookup"><span data-stu-id="42cf8-108">Commands</span></span>

- **`shutdown`**

  <span data-ttu-id="42cf8-109">Desliga servidores de build iniciados por meio do dotnet.</span><span class="sxs-lookup"><span data-stu-id="42cf8-109">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="42cf8-110">Por padrão, todos os servidores estão desligados.</span><span class="sxs-lookup"><span data-stu-id="42cf8-110">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="42cf8-111">{1&gt;Opções&lt;1}</span><span class="sxs-lookup"><span data-stu-id="42cf8-111">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="42cf8-112">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="42cf8-112">Prints out a short help for the command.</span></span>

- **`--msbuild`**

  <span data-ttu-id="42cf8-113">Desliga o servidor de build do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="42cf8-113">Shuts down the MSBuild build server.</span></span>

- **`--razor`**

  <span data-ttu-id="42cf8-114">Desliga o servidor de build do Razor.</span><span class="sxs-lookup"><span data-stu-id="42cf8-114">Shuts down the Razor build server.</span></span>

- **`--vbcscompiler`**

  <span data-ttu-id="42cf8-115">Desliga o servidor de build do compilador do VB/C#.</span><span class="sxs-lookup"><span data-stu-id="42cf8-115">Shuts down the VB/C# compiler build server.</span></span>
