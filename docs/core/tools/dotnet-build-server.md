---
title: Comando dotnet build-server
description: O comando dotnet build-server interage com os servidores iniciados por um build.
ms.date: 02/14/2020
ms.openlocfilehash: a6a9cd6de66371caef66d1101b3f844dffc771ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503782"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="c3ac4-103">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="c3ac4-103">dotnet build-server</span></span>

<span data-ttu-id="c3ac4-104">**Este artigo se aplica a:** ✔️ .NET Core 2.1 SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="c3ac4-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="c3ac4-105">Nome</span><span class="sxs-lookup"><span data-stu-id="c3ac4-105">Name</span></span>

<span data-ttu-id="c3ac4-106">`dotnet build-server` – interage com servidores iniciados por um build.</span><span class="sxs-lookup"><span data-stu-id="c3ac4-106">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c3ac4-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="c3ac4-107">Synopsis</span></span>

```dotnetcli
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="c3ac4-108">Comandos</span><span class="sxs-lookup"><span data-stu-id="c3ac4-108">Commands</span></span>

- **`shutdown`**

  <span data-ttu-id="c3ac4-109">Desliga servidores de build iniciados por meio do dotnet.</span><span class="sxs-lookup"><span data-stu-id="c3ac4-109">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="c3ac4-110">Por padrão, todos os servidores estão desligados.</span><span class="sxs-lookup"><span data-stu-id="c3ac4-110">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="c3ac4-111">Opções</span><span class="sxs-lookup"><span data-stu-id="c3ac4-111">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="c3ac4-112">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="c3ac4-112">Prints out a short help for the command.</span></span>

- **`--msbuild`**

  <span data-ttu-id="c3ac4-113">Desliga o servidor de build do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="c3ac4-113">Shuts down the MSBuild build server.</span></span>

- **`--razor`**

  <span data-ttu-id="c3ac4-114">Desliga o servidor de build do Razor.</span><span class="sxs-lookup"><span data-stu-id="c3ac4-114">Shuts down the Razor build server.</span></span>

- **`--vbcscompiler`**

  <span data-ttu-id="c3ac4-115">Desliga o servidor de build do compilador do VB/C#.</span><span class="sxs-lookup"><span data-stu-id="c3ac4-115">Shuts down the VB/C# compiler build server.</span></span>
