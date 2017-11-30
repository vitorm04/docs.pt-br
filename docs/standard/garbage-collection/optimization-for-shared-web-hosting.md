---
title: "Otimização da hospedagem Web compartilhada"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- garbage collection, Web hosting
- garbage collection, optimizing
- garbage collection, shared Web hosting
ms.assetid: be98c0ab-7ef8-409f-8a0d-cb6e5b75ff20
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1f423d867d4fada075800650627c94f9d09e9e7a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="optimization-for-shared-web-hosting"></a><span data-ttu-id="58eae-102">Otimização da hospedagem Web compartilhada</span><span class="sxs-lookup"><span data-stu-id="58eae-102">Optimization for Shared Web Hosting</span></span>
<span data-ttu-id="58eae-103">Se você for o administrador de um servidor que é compartilhado por vários pequenos sites da Web de hospedagem, você pode otimizar o desempenho e aumentar a capacidade do site adicionando o seguinte `gcTrimCommitOnLowMemory` definir como o `runtime` nó no arquivo ASPNET no .NET diretório:</span><span class="sxs-lookup"><span data-stu-id="58eae-103">If you are the administrator for a server that is shared by hosting several small Web sites, you can optimize performance and increase site capacity by adding the following `gcTrimCommitOnLowMemory` setting to the `runtime` node in the Aspnet.config file in the .NET directory:</span></span>  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
>  <span data-ttu-id="58eae-104">Essa configuração é recomendada somente para Web compartilhada cenários de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="58eae-104">This setting is recommended only for shared Web hosting scenarios.</span></span>  
  
 <span data-ttu-id="58eae-105">Como o coletor de lixo retém a memória para alocações futuras, seu espaço confirmado pode ser mais do que o que é estritamente necessário.</span><span class="sxs-lookup"><span data-stu-id="58eae-105">Because the garbage collector retains memory for future allocations, its committed space can be more than what is strictly needed.</span></span> <span data-ttu-id="58eae-106">Você pode reduzir esse espaço para acomodar vezes quando houver uma carga pesada na memória do sistema.</span><span class="sxs-lookup"><span data-stu-id="58eae-106">You can reduce this space to accommodate times when there is a heavy load on system memory.</span></span> <span data-ttu-id="58eae-107">Reduzir esse espaço confirmado melhora o desempenho e expande a capacidade de hospedar mais sites.</span><span class="sxs-lookup"><span data-stu-id="58eae-107">Reducing this committed space improves performance and expands the capacity to host more sites.</span></span>  
  
 <span data-ttu-id="58eae-108">Quando o `gcTrimCommitOnLowMemory` configuração estiver habilitada, o coletor de lixo avalia a carga de memória do sistema e entra em um modo de corte, quando a carga atinge 90%.</span><span class="sxs-lookup"><span data-stu-id="58eae-108">When the `gcTrimCommitOnLowMemory` setting is enabled, the garbage collector evaluates the system memory load and enters a trimming mode when the load reaches 90%.</span></span> <span data-ttu-id="58eae-109">Ele mantém o modo de corte até que a carga em descarta 85%.</span><span class="sxs-lookup"><span data-stu-id="58eae-109">It maintains the trimming mode until the load drops under 85%.</span></span>  
  
 <span data-ttu-id="58eae-110">Quando as condições permitirem, o coletor de lixo pode decidir que o `gcTrimCommitOnLowMemory` configuração não ajudar o aplicativo atual e ignorá-lo.</span><span class="sxs-lookup"><span data-stu-id="58eae-110">When conditions permit, the garbage collector can decide that the `gcTrimCommitOnLowMemory` setting will not help the current application and ignore it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58eae-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="58eae-111">Example</span></span>  
 <span data-ttu-id="58eae-112">O fragmento XML a seguir mostra como habilitar o `gcTrimCommitOnLowMemory` configuração.</span><span class="sxs-lookup"><span data-stu-id="58eae-112">The following XML fragment shows how to enable the `gcTrimCommitOnLowMemory` setting.</span></span> <span data-ttu-id="58eae-113">As reticências indicam outras configurações que devem ser o `runtime` nó.</span><span class="sxs-lookup"><span data-stu-id="58eae-113">Ellipses indicate other settings that would be in the `runtime` node.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="58eae-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="58eae-114">See Also</span></span>  
 [<span data-ttu-id="58eae-115">Coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="58eae-115">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
