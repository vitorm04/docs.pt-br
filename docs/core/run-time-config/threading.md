---
title: Configurações de configuração de rosca
description: Saiba mais sobre as configurações de tempo de execução que configuram o threading para aplicativos .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 68b8e93ca6ec3f708a7a627307655ada1955500a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789850"
---
# <a name="run-time-configuration-options-for-threading"></a><span data-ttu-id="eabea-103">Opções de configuração em tempo de execução para rosca</span><span class="sxs-lookup"><span data-stu-id="eabea-103">Run-time configuration options for threading</span></span>

## <a name="cpu-groups"></a><span data-ttu-id="eabea-104">Grupos de CPU</span><span class="sxs-lookup"><span data-stu-id="eabea-104">CPU groups</span></span>

- <span data-ttu-id="eabea-105">Configura se os threads são distribuídos automaticamente entre grupos de CPU.</span><span class="sxs-lookup"><span data-stu-id="eabea-105">Configures whether threads are automatically distributed across CPU groups.</span></span>
- <span data-ttu-id="eabea-106">Padrão: Desabilitado ( ).`0`</span><span class="sxs-lookup"><span data-stu-id="eabea-106">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="eabea-107">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="eabea-107">Setting name</span></span> | <span data-ttu-id="eabea-108">Valores</span><span class="sxs-lookup"><span data-stu-id="eabea-108">Values</span></span> |
| - | - | - |
| <span data-ttu-id="eabea-109">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="eabea-109">**runtimeconfig.json**</span></span> | <span data-ttu-id="eabea-110">N/D</span><span class="sxs-lookup"><span data-stu-id="eabea-110">N/A</span></span> | <span data-ttu-id="eabea-111">N/D</span><span class="sxs-lookup"><span data-stu-id="eabea-111">N/A</span></span> |
| <span data-ttu-id="eabea-112">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="eabea-112">**Environment variable**</span></span> | `COMPlus_Thread_UseAllCpuGroups` | <span data-ttu-id="eabea-113">`0`- deficientes</span><span class="sxs-lookup"><span data-stu-id="eabea-113">`0` - disabled</span></span><br/><span data-ttu-id="eabea-114">`1`- habilitado</span><span class="sxs-lookup"><span data-stu-id="eabea-114">`1` - enabled</span></span> |

## <a name="minimum-threads"></a><span data-ttu-id="eabea-115">Roscas mínimas</span><span class="sxs-lookup"><span data-stu-id="eabea-115">Minimum threads</span></span>

- <span data-ttu-id="eabea-116">Especifica o número mínimo de threads para o pool de segmentos do trabalhador.</span><span class="sxs-lookup"><span data-stu-id="eabea-116">Specifies the minimum number of threads for the worker thread pool.</span></span>
- <span data-ttu-id="eabea-117">Corresponde ao <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="eabea-117">Corresponds to the <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="eabea-118">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="eabea-118">Setting name</span></span> | <span data-ttu-id="eabea-119">Valores</span><span class="sxs-lookup"><span data-stu-id="eabea-119">Values</span></span> |
| - | - | - |
| <span data-ttu-id="eabea-120">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="eabea-120">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MinThreads` | <span data-ttu-id="eabea-121">Um inteiro que representa o número mínimo de threads</span><span class="sxs-lookup"><span data-stu-id="eabea-121">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="eabea-122">**Propriedade MSBuild**</span><span class="sxs-lookup"><span data-stu-id="eabea-122">**MSBuild property**</span></span> | `ThreadPoolMinThreads` | <span data-ttu-id="eabea-123">Um inteiro que representa o número mínimo de threads</span><span class="sxs-lookup"><span data-stu-id="eabea-123">An integer that represents the minimum number of threads</span></span> |
| <span data-ttu-id="eabea-124">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="eabea-124">**Environment variable**</span></span> | <span data-ttu-id="eabea-125">N/D</span><span class="sxs-lookup"><span data-stu-id="eabea-125">N/A</span></span> | <span data-ttu-id="eabea-126">N/D</span><span class="sxs-lookup"><span data-stu-id="eabea-126">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="eabea-127">Exemplos</span><span class="sxs-lookup"><span data-stu-id="eabea-127">Examples</span></span>

<span data-ttu-id="eabea-128">*arquivo runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="eabea-128">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MinThreads": 4
      }
   }
}
```

<span data-ttu-id="eabea-129">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="eabea-129">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  </PropertyGroup>

</Project>
```

## <a name="maximum-threads"></a><span data-ttu-id="eabea-130">Roscas máximas</span><span class="sxs-lookup"><span data-stu-id="eabea-130">Maximum threads</span></span>

- <span data-ttu-id="eabea-131">Especifica o número máximo de threads para o pool de segmentos do trabalhador.</span><span class="sxs-lookup"><span data-stu-id="eabea-131">Specifies the maximum number of threads for the worker thread pool.</span></span>
- <span data-ttu-id="eabea-132">Corresponde ao <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="eabea-132">Corresponds to the <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="eabea-133">Nome da configuração</span><span class="sxs-lookup"><span data-stu-id="eabea-133">Setting name</span></span> | <span data-ttu-id="eabea-134">Valores</span><span class="sxs-lookup"><span data-stu-id="eabea-134">Values</span></span> |
| - | - | - |
| <span data-ttu-id="eabea-135">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="eabea-135">**runtimeconfig.json**</span></span> | `System.Threading.ThreadPool.MaxThreads` | <span data-ttu-id="eabea-136">Um inteiro que representa o número máximo de threads</span><span class="sxs-lookup"><span data-stu-id="eabea-136">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="eabea-137">**Propriedade MSBuild**</span><span class="sxs-lookup"><span data-stu-id="eabea-137">**MSBuild property**</span></span> | `ThreadPoolMaxThreads` | <span data-ttu-id="eabea-138">Um inteiro que representa o número máximo de threads</span><span class="sxs-lookup"><span data-stu-id="eabea-138">An integer that represents the maximum number of threads</span></span> |
| <span data-ttu-id="eabea-139">**Variável de ambiente**</span><span class="sxs-lookup"><span data-stu-id="eabea-139">**Environment variable**</span></span> | <span data-ttu-id="eabea-140">N/D</span><span class="sxs-lookup"><span data-stu-id="eabea-140">N/A</span></span> | <span data-ttu-id="eabea-141">N/D</span><span class="sxs-lookup"><span data-stu-id="eabea-141">N/A</span></span> |

### <a name="examples"></a><span data-ttu-id="eabea-142">Exemplos</span><span class="sxs-lookup"><span data-stu-id="eabea-142">Examples</span></span>

<span data-ttu-id="eabea-143">*arquivo runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="eabea-143">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Threading.ThreadPool.MaxThreads": 20
      }
   }
}
```

<span data-ttu-id="eabea-144">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="eabea-144">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
  </PropertyGroup>

</Project>
```
