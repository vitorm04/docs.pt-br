---
title: Definições de configuração de Threading
description: Saiba mais sobre as configurações de tempo de execução que configuram Threading para aplicativos .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 6a920dbc301830e3f4c95bf637ff3de6d4f464ff
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802760"
---
# <a name="run-time-configuration-options-for-threading"></a><span data-ttu-id="51566-103">Opções de configuração de tempo de execução para Threading</span><span class="sxs-lookup"><span data-stu-id="51566-103">Run-time configuration options for threading</span></span>

## <a name="cpu-groups"></a><span data-ttu-id="51566-104">Grupos de CPU</span><span class="sxs-lookup"><span data-stu-id="51566-104">CPU groups</span></span>

- <span data-ttu-id="51566-105">Define se os threads são distribuídos automaticamente entre grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="51566-105">Configures whether threads are automatically distributed across CPU groups.</span></span>
- <span data-ttu-id="51566-106">Padrão: desabilitado (`0`).</span><span class="sxs-lookup"><span data-stu-id="51566-106">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="51566-107">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="51566-107">Setting name</span></span> | <span data-ttu-id="51566-108">Valores</span><span class="sxs-lookup"><span data-stu-id="51566-108">Values</span></span> |
| - | - | - |
| <span data-ttu-id="51566-109">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="51566-109">**runtimeconfig.json**</span></span> | <span data-ttu-id="51566-110">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="51566-110">N/A</span></span> | <span data-ttu-id="51566-111">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="51566-111">N/A</span></span> |
| <span data-ttu-id="51566-112">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="51566-112">**Environment variable**</span></span> | `COMPlus_Thread_UseAllCpuGroups` | <span data-ttu-id="51566-113">`0`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="51566-113">`0` - disabled</span></span><br/><span data-ttu-id="51566-114">habilitado para `1`</span><span class="sxs-lookup"><span data-stu-id="51566-114">`1` - enabled</span></span> |

## <a name="minimum-threads"></a><span data-ttu-id="51566-115">Mínimo de threads</span><span class="sxs-lookup"><span data-stu-id="51566-115">Minimum threads</span></span>

- <span data-ttu-id="51566-116">Especifica o número mínimo de threads para o ThreadPool de trabalho.</span><span class="sxs-lookup"><span data-stu-id="51566-116">Specifies the minimum number of threads for the worker threadpool.</span></span>
- <span data-ttu-id="51566-117">Corresponde ao método de <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="51566-117">Corresponds to the <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="51566-118">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="51566-118">Setting name</span></span> | <span data-ttu-id="51566-119">Valores</span><span class="sxs-lookup"><span data-stu-id="51566-119">Values</span></span> |
| - | - | - |
| <span data-ttu-id="51566-120">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="51566-120">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MinThreads` | <span data-ttu-id="51566-121">Um inteiro que representa o número mínimo de threads</span><span class="sxs-lookup"><span data-stu-id="51566-121">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="51566-122">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="51566-122">**Environment variable**</span></span> | <span data-ttu-id="51566-123">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="51566-123">N/A</span></span> | <span data-ttu-id="51566-124">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="51566-124">N/A</span></span> |

## <a name="maximum-threads"></a><span data-ttu-id="51566-125">Máximo de threads</span><span class="sxs-lookup"><span data-stu-id="51566-125">Maximum threads</span></span>

- <span data-ttu-id="51566-126">Especifica o número máximo de threads para o ThreadPool de trabalho.</span><span class="sxs-lookup"><span data-stu-id="51566-126">Specifies the maximum number of threads for the worker threadpool.</span></span>
- <span data-ttu-id="51566-127">Corresponde ao método de <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="51566-127">Corresponds to the <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="51566-128">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="51566-128">Setting name</span></span> | <span data-ttu-id="51566-129">Valores</span><span class="sxs-lookup"><span data-stu-id="51566-129">Values</span></span> |
| - | - | - |
| <span data-ttu-id="51566-130">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="51566-130">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MaxThreads` | <span data-ttu-id="51566-131">Um inteiro que representa o número máximo de threads</span><span class="sxs-lookup"><span data-stu-id="51566-131">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="51566-132">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="51566-132">**Environment variable**</span></span> | <span data-ttu-id="51566-133">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="51566-133">N/A</span></span> | <span data-ttu-id="51566-134">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="51566-134">N/A</span></span> |
