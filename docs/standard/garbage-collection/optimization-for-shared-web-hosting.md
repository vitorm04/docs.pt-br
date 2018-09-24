---
title: Otimização da hospedagem Web compartilhada
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, Web hosting
- garbage collection, optimizing
- garbage collection, shared Web hosting
ms.assetid: be98c0ab-7ef8-409f-8a0d-cb6e5b75ff20
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7831e383a3048523909b79ac5a4706f3c1c48371
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46586366"
---
# <a name="optimization-for-shared-web-hosting"></a><span data-ttu-id="c3a0d-102">Otimização da hospedagem Web compartilhada</span><span class="sxs-lookup"><span data-stu-id="c3a0d-102">Optimization for Shared Web Hosting</span></span>
<span data-ttu-id="c3a0d-103">Se você for o administrador de um servidor que é compartilhado ao hospedar vários sites pequenos, poderá otimizar o desempenho e aumentar a capacidade do site adicionando a seguinte configuração `gcTrimCommitOnLowMemory` ao nó `runtime` no arquivo Aspnet.config no diretório .NET:</span><span class="sxs-lookup"><span data-stu-id="c3a0d-103">If you are the administrator for a server that is shared by hosting several small Web sites, you can optimize performance and increase site capacity by adding the following `gcTrimCommitOnLowMemory` setting to the `runtime` node in the Aspnet.config file in the .NET directory:</span></span>  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
>  <span data-ttu-id="c3a0d-104">Essa configuração é recomendada somente para cenários de hospedagem na Web compartilhada.</span><span class="sxs-lookup"><span data-stu-id="c3a0d-104">This setting is recommended only for shared Web hosting scenarios.</span></span>  
  
 <span data-ttu-id="c3a0d-105">Como o coletor de lixo retém a memória para alocações futuras, seu espaço confirmado pode ser superior a o que é estritamente necessário.</span><span class="sxs-lookup"><span data-stu-id="c3a0d-105">Because the garbage collector retains memory for future allocations, its committed space can be more than what is strictly needed.</span></span> <span data-ttu-id="c3a0d-106">Você pode reduzir esse espaço para acomodar quando houver uma carga pesada na memória do sistema.</span><span class="sxs-lookup"><span data-stu-id="c3a0d-106">You can reduce this space to accommodate times when there is a heavy load on system memory.</span></span> <span data-ttu-id="c3a0d-107">Reduzir esse espaço confirmado melhora o desempenho e expande a capacidade de hospedar mais sites.</span><span class="sxs-lookup"><span data-stu-id="c3a0d-107">Reducing this committed space improves performance and expands the capacity to host more sites.</span></span>  
  
 <span data-ttu-id="c3a0d-108">Quando a configuração `gcTrimCommitOnLowMemory` estiver habilitada, o coletor de lixo avaliará a carga de memória do sistema e entrará em um modo de corte, quando a carga atinge 90%.</span><span class="sxs-lookup"><span data-stu-id="c3a0d-108">When the `gcTrimCommitOnLowMemory` setting is enabled, the garbage collector evaluates the system memory load and enters a trimming mode when the load reaches 90%.</span></span> <span data-ttu-id="c3a0d-109">Ele mantém o modo de corte até que a carga fique abaixo de 85%.</span><span class="sxs-lookup"><span data-stu-id="c3a0d-109">It maintains the trimming mode until the load drops under 85%.</span></span>  
  
 <span data-ttu-id="c3a0d-110">Quando as condições permitirem, o coletor de lixo poderá decidir que a configuração `gcTrimCommitOnLowMemory` não ajudará o aplicativo atual e poderá ignorá-lo.</span><span class="sxs-lookup"><span data-stu-id="c3a0d-110">When conditions permit, the garbage collector can decide that the `gcTrimCommitOnLowMemory` setting will not help the current application and ignore it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3a0d-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c3a0d-111">Example</span></span>  
 <span data-ttu-id="c3a0d-112">O fragmento XML a seguir mostra como habilitar a configuração `gcTrimCommitOnLowMemory`.</span><span class="sxs-lookup"><span data-stu-id="c3a0d-112">The following XML fragment shows how to enable the `gcTrimCommitOnLowMemory` setting.</span></span> <span data-ttu-id="c3a0d-113">As reticências indicam outras configurações que estariam no nó `runtime`.</span><span class="sxs-lookup"><span data-stu-id="c3a0d-113">Ellipses indicate other settings that would be in the `runtime` node.</span></span>  
  
```xml  
<?xml version="1.0" encoding="UTF-8"?>  
<configuration>  
    <runtime>  
    . . .  
    <gcTrimCommitOnLowMemory enabled="true"/>  
    </runtime>  
    . . .  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c3a0d-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3a0d-114">See also</span></span>

- [<span data-ttu-id="c3a0d-115">Coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="c3a0d-115">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
