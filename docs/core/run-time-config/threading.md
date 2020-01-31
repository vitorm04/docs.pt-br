---
title: Definições de configuração de Threading
description: Saiba mais sobre as configurações de tempo de execução que configuram Threading para aplicativos .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 68b8e93ca6ec3f708a7a627307655ada1955500a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789850"
---
# <a name="run-time-configuration-options-for-threading"></a><span data-ttu-id="76fa9-103">Opções de configuração de tempo de execução para Threading</span><span class="sxs-lookup"><span data-stu-id="76fa9-103">Run-time configuration options for threading</span></span>

## <a name="cpu-groups"></a><span data-ttu-id="76fa9-104">Grupos de CPU</span><span class="sxs-lookup"><span data-stu-id="76fa9-104">CPU groups</span></span>

- <span data-ttu-id="76fa9-105">Define se os threads são distribuídos automaticamente entre grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="76fa9-105">Configures whether threads are automatically distributed across CPU groups.</span></span>
- <span data-ttu-id="76fa9-106">Padrão: desabilitado (`0`).</span><span class="sxs-lookup"><span data-stu-id="76fa9-106">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="76fa9-107">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="76fa9-107">Setting name</span></span> | <span data-ttu-id="76fa9-108">Valores</span><span class="sxs-lookup"><span data-stu-id="76fa9-108">Values</span></span> |
| - | - | - |
| <span data-ttu-id="76fa9-109">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="76fa9-109">**runtimeconfig.json**</span></span> | <span data-ttu-id="76fa9-110">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="76fa9-110">N/A</span></span> | <span data-ttu-id="76fa9-111">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="76fa9-111">N/A</span></span> |
| <span data-ttu-id="76fa9-112">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="76fa9-112">**Environment variable**</span></span> | `COMPlus_Thread_UseAllCpuGroups` | <span data-ttu-id="76fa9-113">`0`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="76fa9-113">`0` - disabled</span></span><br/><span data-ttu-id="76fa9-114">habilitado para `1`</span><span class="sxs-lookup"><span data-stu-id="76fa9-114">`1` - enabled</span></span> |

## <a name="minimum-threads"></a><span data-ttu-id="76fa9-115">Mínimo de threads</span><span class="sxs-lookup"><span data-stu-id="76fa9-115">Minimum threads</span></span>

- <span data-ttu-id="76fa9-116">Especifica o número mínimo de threads para o pool de threads de trabalho.</span><span class="sxs-lookup"><span data-stu-id="76fa9-116">Specifies the minimum number of threads for the worker thread pool.</span></span>
- <span data-ttu-id="76fa9-117">Corresponde ao método de <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="76fa9-117">Corresponds to the <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="76fa9-118">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="76fa9-118">Setting name</span></span> | <span data-ttu-id="76fa9-119">Valores</span><span class="sxs-lookup"><span data-stu-id="76fa9-119">Values</span></span> |
| - | - | - |
| <span data-ttu-id="76fa9-120">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="76fa9-120">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MinThreads` | <span data-ttu-id="76fa9-121">Um inteiro que representa o número mínimo de threads</span><span class="sxs-lookup"><span data-stu-id="76fa9-121">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="76fa9-122">**Propriedade do MSBuild**</span><span class="sxs-lookup"><span data-stu-id="76fa9-122">**MSBuild property**</span></span> | `ThreadPoolMinThreads` | <span data-ttu-id="76fa9-123">Um inteiro que representa o número mínimo de threads</span><span class="sxs-lookup"><span data-stu-id="76fa9-123">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="76fa9-124">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="76fa9-124">**Environment variable**</span></span> | <span data-ttu-id="76fa9-125">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="76fa9-125">N/A</span></span> | <span data-ttu-id="76fa9-126">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="76fa9-126">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="76fa9-127">Exemplos</span><span class="sxs-lookup"><span data-stu-id="76fa9-127">Examples</span></span>

<span data-ttu-id="76fa9-128">arquivo *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="76fa9-128">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MinThreads": 4
      }
   }
}
```

<span data-ttu-id="76fa9-129">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="76fa9-129">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  </PropertyGroup>

</Project>
```

## <a name="maximum-threads"></a><span data-ttu-id="76fa9-130">Máximo de threads</span><span class="sxs-lookup"><span data-stu-id="76fa9-130">Maximum threads</span></span>

- <span data-ttu-id="76fa9-131">Especifica o número máximo de threads para o pool de threads de trabalho.</span><span class="sxs-lookup"><span data-stu-id="76fa9-131">Specifies the maximum number of threads for the worker thread pool.</span></span>
- <span data-ttu-id="76fa9-132">Corresponde ao método de <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="76fa9-132">Corresponds to the <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="76fa9-133">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="76fa9-133">Setting name</span></span> | <span data-ttu-id="76fa9-134">Valores</span><span class="sxs-lookup"><span data-stu-id="76fa9-134">Values</span></span> |
| - | - | - |
| <span data-ttu-id="76fa9-135">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="76fa9-135">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MaxThreads` | <span data-ttu-id="76fa9-136">Um inteiro que representa o número máximo de threads</span><span class="sxs-lookup"><span data-stu-id="76fa9-136">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="76fa9-137">**Propriedade do MSBuild**</span><span class="sxs-lookup"><span data-stu-id="76fa9-137">**MSBuild property**</span></span> | `ThreadPoolMaxThreads` | <span data-ttu-id="76fa9-138">Um inteiro que representa o número máximo de threads</span><span class="sxs-lookup"><span data-stu-id="76fa9-138">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="76fa9-139">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="76fa9-139">**Environment variable**</span></span> | <span data-ttu-id="76fa9-140">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="76fa9-140">N/A</span></span> | <span data-ttu-id="76fa9-141">{1&gt;N/A&lt;1}</span><span class="sxs-lookup"><span data-stu-id="76fa9-141">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="76fa9-142">Exemplos</span><span class="sxs-lookup"><span data-stu-id="76fa9-142">Examples</span></span>

<span data-ttu-id="76fa9-143">arquivo *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="76fa9-143">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MaxThreads": 20
      }
   }
}
```

<span data-ttu-id="76fa9-144">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="76fa9-144">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
  </PropertyGroup>

</Project>
```
