---
title: Comando dotnet build-server
description: O comando dotnet build-server interage com os servidores iniciados por um build.
ms.date: 04/24/2019
ms.openlocfilehash: 89d1aba104e2cb07b46766a3768eed68d85a7aa7
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117769"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="53e40-103">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="53e40-103">dotnet build-server</span></span>

<span data-ttu-id="53e40-104">**Este artigo se aplica a: ✓** SDK do .NET Core 2.1 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="53e40-104">**This article applies to: ✓** .NET Core 2.1 SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]
-->

## <a name="name"></a><span data-ttu-id="53e40-105">Nome</span><span class="sxs-lookup"><span data-stu-id="53e40-105">Name</span></span>

<span data-ttu-id="53e40-106">`dotnet build-server` – interage com servidores iniciados por um build.</span><span class="sxs-lookup"><span data-stu-id="53e40-106">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="53e40-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="53e40-107">Synopsis</span></span>

```dotnetcli
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="53e40-108">Comandos</span><span class="sxs-lookup"><span data-stu-id="53e40-108">Commands</span></span>

* **`shutdown`**

  <span data-ttu-id="53e40-109">Desliga servidores de build iniciados por meio do dotnet.</span><span class="sxs-lookup"><span data-stu-id="53e40-109">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="53e40-110">Por padrão, todos os servidores estão desligados.</span><span class="sxs-lookup"><span data-stu-id="53e40-110">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="53e40-111">Opções</span><span class="sxs-lookup"><span data-stu-id="53e40-111">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="53e40-112">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="53e40-112">Prints out a short help for the command.</span></span>

* **`--msbuild`**

  <span data-ttu-id="53e40-113">Desliga o servidor de build do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="53e40-113">Shuts down the MSBuild build server.</span></span>

* **`--razor`**

  <span data-ttu-id="53e40-114">Desliga o servidor de build do Razor.</span><span class="sxs-lookup"><span data-stu-id="53e40-114">Shuts down the Razor build server.</span></span>

* **`--vbcscompiler`**

  <span data-ttu-id="53e40-115">Desliga o servidor de build do compilador do VB/C#.</span><span class="sxs-lookup"><span data-stu-id="53e40-115">Shuts down the VB/C# compiler build server.</span></span>
