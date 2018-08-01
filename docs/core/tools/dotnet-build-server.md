---
title: Comando dotnet build-server – CLI do .NET Core
description: O comando dotnet build-server interage com os servidores iniciados por um build.
author: mairaw
ms.author: mairaw
ms.date: 07/02/2018
ms.openlocfilehash: 1c59c85f246b79c7e2552f704db5b4f076f9b502
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404327"
---
# <a name="dotnet-build-server"></a><span data-ttu-id="7be89-103">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="7be89-103">dotnet build-server</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="7be89-104">Nome</span><span class="sxs-lookup"><span data-stu-id="7be89-104">Name</span></span>

<span data-ttu-id="7be89-105">`dotnet build-server` – interage com servidores iniciados por um build.</span><span class="sxs-lookup"><span data-stu-id="7be89-105">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="7be89-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="7be89-106">Synopsis</span></span>

```
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="7be89-107">Comandos</span><span class="sxs-lookup"><span data-stu-id="7be89-107">Commands</span></span>

`shutdown`

<span data-ttu-id="7be89-108">Desliga servidores de build iniciados por meio do dotnet.</span><span class="sxs-lookup"><span data-stu-id="7be89-108">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="7be89-109">Por padrão, todos os servidores estão desligados.</span><span class="sxs-lookup"><span data-stu-id="7be89-109">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="7be89-110">Opções</span><span class="sxs-lookup"><span data-stu-id="7be89-110">Options</span></span>

`-h|--help`

<span data-ttu-id="7be89-111">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="7be89-111">Prints out a short help for the command.</span></span>

`--msbuild`

<span data-ttu-id="7be89-112">Desliga o servidor de build do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="7be89-112">Shuts down the MSBuild build server.</span></span>

`--razor`

<span data-ttu-id="7be89-113">Desliga o servidor de build do Razor.</span><span class="sxs-lookup"><span data-stu-id="7be89-113">Shuts down the Razor build server.</span></span>

`--vbcscompiler`

<span data-ttu-id="7be89-114">Desliga o servidor de build do compilador do VB/C#.</span><span class="sxs-lookup"><span data-stu-id="7be89-114">Shuts down the VB/C# compiler build server.</span></span>
