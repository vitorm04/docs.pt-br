---
title: Definições de configuração de Threading
description: Saiba mais sobre as configurações de tempo de execução que configuram Threading para aplicativos .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 1c7c16993a07ef95223481791153b75ab2f61533
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761922"
---
# <a name="run-time-configuration-options-for-threading"></a><span data-ttu-id="0fad2-103">Opções de configuração de tempo de execução para Threading</span><span class="sxs-lookup"><span data-stu-id="0fad2-103">Run-time configuration options for threading</span></span>

## <a name="cpu-groups"></a><span data-ttu-id="0fad2-104">Grupos de CPU</span><span class="sxs-lookup"><span data-stu-id="0fad2-104">CPU groups</span></span>

- <span data-ttu-id="0fad2-105">Define se os threads são distribuídos automaticamente entre grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="0fad2-105">Configures whether threads are automatically distributed across CPU groups.</span></span>
- <span data-ttu-id="0fad2-106">Se você omitir essa configuração, os threads não serão distribuídos em grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="0fad2-106">If you omit this setting, threads are not distributed across CPU groups.</span></span> <span data-ttu-id="0fad2-107">Isso é equivalente a definir o valor como `0` .</span><span class="sxs-lookup"><span data-stu-id="0fad2-107">This is equivalent to setting the value to `0`.</span></span>

| | <span data-ttu-id="0fad2-108">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="0fad2-108">Setting name</span></span> | <span data-ttu-id="0fad2-109">Valores</span><span class="sxs-lookup"><span data-stu-id="0fad2-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="0fad2-110">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="0fad2-110">**runtimeconfig.json**</span></span> | <span data-ttu-id="0fad2-111">N/D</span><span class="sxs-lookup"><span data-stu-id="0fad2-111">N/A</span></span> | <span data-ttu-id="0fad2-112">N/D</span><span class="sxs-lookup"><span data-stu-id="0fad2-112">N/A</span></span> |
| <span data-ttu-id="0fad2-113">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="0fad2-113">**Environment variable**</span></span> | `COMPlus_Thread_UseAllCpuGroups` | <span data-ttu-id="0fad2-114">`0`-desabilitado</span><span class="sxs-lookup"><span data-stu-id="0fad2-114">`0` - disabled</span></span><br/><span data-ttu-id="0fad2-115">`1`-habilitado</span><span class="sxs-lookup"><span data-stu-id="0fad2-115">`1` - enabled</span></span> |

## <a name="minimum-threads"></a><span data-ttu-id="0fad2-116">Mínimo de threads</span><span class="sxs-lookup"><span data-stu-id="0fad2-116">Minimum threads</span></span>

- <span data-ttu-id="0fad2-117">Especifica o número mínimo de threads para o pool de threads de trabalho.</span><span class="sxs-lookup"><span data-stu-id="0fad2-117">Specifies the minimum number of threads for the worker thread pool.</span></span>
- <span data-ttu-id="0fad2-118">Corresponde ao <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="0fad2-118">Corresponds to the <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="0fad2-119">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="0fad2-119">Setting name</span></span> | <span data-ttu-id="0fad2-120">Valores</span><span class="sxs-lookup"><span data-stu-id="0fad2-120">Values</span></span> |
| - | - | - |
| <span data-ttu-id="0fad2-121">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="0fad2-121">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MinThreads` | <span data-ttu-id="0fad2-122">Um inteiro que representa o número mínimo de threads</span><span class="sxs-lookup"><span data-stu-id="0fad2-122">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="0fad2-123">**Propriedade do MSBuild**</span><span class="sxs-lookup"><span data-stu-id="0fad2-123">**MSBuild property**</span></span> | `ThreadPoolMinThreads` | <span data-ttu-id="0fad2-124">Um inteiro que representa o número mínimo de threads</span><span class="sxs-lookup"><span data-stu-id="0fad2-124">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="0fad2-125">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="0fad2-125">**Environment variable**</span></span> | <span data-ttu-id="0fad2-126">N/D</span><span class="sxs-lookup"><span data-stu-id="0fad2-126">N/A</span></span> | <span data-ttu-id="0fad2-127">N/D</span><span class="sxs-lookup"><span data-stu-id="0fad2-127">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="0fad2-128">Exemplos</span><span class="sxs-lookup"><span data-stu-id="0fad2-128">Examples</span></span>

<span data-ttu-id="0fad2-129">arquivo *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="0fad2-129">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MinThreads": 4
      }
   }
}
```

<span data-ttu-id="0fad2-130">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="0fad2-130">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  </PropertyGroup>

</Project>
```

## <a name="maximum-threads"></a><span data-ttu-id="0fad2-131">Máximo de threads</span><span class="sxs-lookup"><span data-stu-id="0fad2-131">Maximum threads</span></span>

- <span data-ttu-id="0fad2-132">Especifica o número máximo de threads para o pool de threads de trabalho.</span><span class="sxs-lookup"><span data-stu-id="0fad2-132">Specifies the maximum number of threads for the worker thread pool.</span></span>
- <span data-ttu-id="0fad2-133">Corresponde ao <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="0fad2-133">Corresponds to the <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="0fad2-134">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="0fad2-134">Setting name</span></span> | <span data-ttu-id="0fad2-135">Valores</span><span class="sxs-lookup"><span data-stu-id="0fad2-135">Values</span></span> |
| - | - | - |
| <span data-ttu-id="0fad2-136">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="0fad2-136">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MaxThreads` | <span data-ttu-id="0fad2-137">Um inteiro que representa o número máximo de threads</span><span class="sxs-lookup"><span data-stu-id="0fad2-137">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="0fad2-138">**Propriedade do MSBuild**</span><span class="sxs-lookup"><span data-stu-id="0fad2-138">**MSBuild property**</span></span> | `ThreadPoolMaxThreads` | <span data-ttu-id="0fad2-139">Um inteiro que representa o número máximo de threads</span><span class="sxs-lookup"><span data-stu-id="0fad2-139">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="0fad2-140">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="0fad2-140">**Environment variable**</span></span> | <span data-ttu-id="0fad2-141">N/D</span><span class="sxs-lookup"><span data-stu-id="0fad2-141">N/A</span></span> | <span data-ttu-id="0fad2-142">N/D</span><span class="sxs-lookup"><span data-stu-id="0fad2-142">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="0fad2-143">Exemplos</span><span class="sxs-lookup"><span data-stu-id="0fad2-143">Examples</span></span>

<span data-ttu-id="0fad2-144">arquivo *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="0fad2-144">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MaxThreads": 20
      }
   }
}
```

<span data-ttu-id="0fad2-145">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="0fad2-145">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
  </PropertyGroup>

</Project>
```
