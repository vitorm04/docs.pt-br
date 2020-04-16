---
title: Comando dotnet build-server
description: O comando dotnet build-server interage com os servidores iniciados por um build.
ms.date: 02/14/2020
ms.openlocfilehash: 882b697c07aac0e20266f3ad4e6c11888a0b7acc
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463731"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="c6999-103">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="c6999-103">dotnet build-server</span></span>

<span data-ttu-id="c6999-104">**Este artigo se aplica a:** ✔️ .NET Core 2.1 SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="c6999-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="c6999-105">Nome</span><span class="sxs-lookup"><span data-stu-id="c6999-105">Name</span></span>

<span data-ttu-id="c6999-106">`dotnet build-server` – interage com servidores iniciados por um build.</span><span class="sxs-lookup"><span data-stu-id="c6999-106">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c6999-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="c6999-107">Synopsis</span></span>

```dotnetcli
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]

dotnet build-server shutdown -h|--help

dotnet build-server -h|--help
```

## <a name="commands"></a><span data-ttu-id="c6999-108">Comandos</span><span class="sxs-lookup"><span data-stu-id="c6999-108">Commands</span></span>

- **`shutdown`**

  <span data-ttu-id="c6999-109">Desliga servidores de build iniciados por meio do dotnet.</span><span class="sxs-lookup"><span data-stu-id="c6999-109">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="c6999-110">Por padrão, todos os servidores estão desligados.</span><span class="sxs-lookup"><span data-stu-id="c6999-110">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="c6999-111">Opções</span><span class="sxs-lookup"><span data-stu-id="c6999-111">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="c6999-112">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="c6999-112">Prints out a short help for the command.</span></span>

- **`--msbuild`**

  <span data-ttu-id="c6999-113">Desliga o servidor de build do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="c6999-113">Shuts down the MSBuild build server.</span></span>

- **`--razor`**

  <span data-ttu-id="c6999-114">Desliga o servidor de build do Razor.</span><span class="sxs-lookup"><span data-stu-id="c6999-114">Shuts down the Razor build server.</span></span>

- **`--vbcscompiler`**

  <span data-ttu-id="c6999-115">Desliga o servidor de build do compilador do VB/C#.</span><span class="sxs-lookup"><span data-stu-id="c6999-115">Shuts down the VB/C# compiler build server.</span></span>
