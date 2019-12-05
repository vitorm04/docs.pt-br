---
title: Definições de configuração de compilação
description: Saiba mais sobre as configurações de tempo de execução que configuram como o compilador JIT funciona para aplicativos .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: bcc445b6edc48d9432ee614b0b19c9c25621f4a0
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802816"
---
# <a name="run-time-configuration-options-for-compilation"></a><span data-ttu-id="0232b-103">Opções de configuração de tempo de execução para compilação</span><span class="sxs-lookup"><span data-stu-id="0232b-103">Run-time configuration options for compilation</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="0232b-104">Compilação em camadas</span><span class="sxs-lookup"><span data-stu-id="0232b-104">Tiered compilation</span></span>

- <span data-ttu-id="0232b-105">Configura se o compilador JIT usa compilação em [camadas](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="0232b-105">Configures whether the JIT compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span>
- <span data-ttu-id="0232b-106">No .NET Core 3,0 e posterior, a compilação em camadas está habilitada por padrão.</span><span class="sxs-lookup"><span data-stu-id="0232b-106">In .NET Core 3.0 and later, tiered compilation is enabled by default.</span></span>
- <span data-ttu-id="0232b-107">No .NET Core 2,1 e 2,2, a compilação em camadas está desabilitada por padrão.</span><span class="sxs-lookup"><span data-stu-id="0232b-107">In .NET Core 2.1 and 2.2, tiered compilation is disabled by default.</span></span>

| | <span data-ttu-id="0232b-108">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="0232b-108">Setting name</span></span> | <span data-ttu-id="0232b-109">Valores</span><span class="sxs-lookup"><span data-stu-id="0232b-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="0232b-110">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="0232b-110">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation` | <span data-ttu-id="0232b-111">habilitado para `true`</span><span class="sxs-lookup"><span data-stu-id="0232b-111">`true` - enabled</span></span><br/><span data-ttu-id="0232b-112">`false`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="0232b-112">`false` - disabled</span></span> |
| <span data-ttu-id="0232b-113">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="0232b-113">**Environment variable**</span></span> | `COMPlus_TieredCompilation` | <span data-ttu-id="0232b-114">habilitado para `1`</span><span class="sxs-lookup"><span data-stu-id="0232b-114">`1` - enabled</span></span><br/><span data-ttu-id="0232b-115">`0`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="0232b-115">`0` - disabled</span></span> |
