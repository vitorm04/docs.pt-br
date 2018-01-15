---
title: Usando componentes atendidos com o cache de assemblies global
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache), serviced components
- serviced components, global assembly cache
- global assembly cache, serviced components
ms.assetid: 3423e5d9-234c-4571-8161-e35f6d130128
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fb9bd85797dd129f6f34992c58c9772668ce2cb0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="using-serviced-components-with-the-global-assembly-cache"></a><span data-ttu-id="86d0b-102">Usando componentes atendidos com o cache de assemblies global</span><span class="sxs-lookup"><span data-stu-id="86d0b-102">Using Serviced Components with the Global Assembly Cache</span></span>
<span data-ttu-id="86d0b-103">Componentes atendidos (componentes COM+ com código gerenciado) devem ser colocados no Cache de Assembly Global.</span><span class="sxs-lookup"><span data-stu-id="86d0b-103">Serviced components (managed code COM+ components) should be put in the Global Assembly Cache.</span></span> <span data-ttu-id="86d0b-104">Em alguns cenários, o Common Language Runtime e os Serviços COM+ podem manipular componentes atendidos que não estão no Cache de Assembly Global; em outros cenários, eles não podem.</span><span class="sxs-lookup"><span data-stu-id="86d0b-104">In some scenarios, the Common Language Runtime and COM+ Services can handle serviced components that are not in the Global Assembly Cache; in other scenarios, they cannot.</span></span> <span data-ttu-id="86d0b-105">Os seguintes cenários ilustram isso:</span><span class="sxs-lookup"><span data-stu-id="86d0b-105">The following scenarios illustrate this:</span></span>  
  
-   <span data-ttu-id="86d0b-106">Para componentes atendidos em um aplicativo COM+ para Servidor, o assembly que contém os componentes deve estar no Cache de Assembly Global, pois Dllhost.exe não é executado no mesmo diretório que contém os componentes atendidos.</span><span class="sxs-lookup"><span data-stu-id="86d0b-106">For serviced components in a COM+ Server application, the assembly containing the components must be in the Global Assembly Cache, because Dllhost.exe does not run in the same directory as the one that contains the serviced components.</span></span>  
  
-   <span data-ttu-id="86d0b-107">Para componentes atendidos em um aplicativo de COM+ Library, o tempo de execução e COM+ Services podem resolver as referências ao assembly que contém os componentes pesquisando o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="86d0b-107">For serviced components in a COM+ Library application, the runtime and COM+ Services can resolve the reference to the assembly containing the components by searching in the current directory.</span></span> <span data-ttu-id="86d0b-108">Nesse caso, o assembly não precisa estar no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="86d0b-108">In this case, the assembly does not have to be in the global assembly cache.</span></span>  
  
-   <span data-ttu-id="86d0b-109">Para componentes atendidos em um aplicativo ASP.NET, a situação é diferente.</span><span class="sxs-lookup"><span data-stu-id="86d0b-109">For serviced components in an ASP.NET application, the situation is different.</span></span> <span data-ttu-id="86d0b-110">Se você colocar o assembly que contém os componentes atendidos no diretório bin da base de aplicativo e usar o registro sob demanda, o assembly será copiado por sombra para o cache de download, pois o ASP.NET aproveita os recursos de sombra do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="86d0b-110">If you place the assembly containing the serviced components in the bin directory of the application base and use on-demand registration, the assembly will be shadow-copied into the download cache because ASP.NET leverages the shadow capabilities of the runtime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86d0b-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="86d0b-111">See Also</span></span>  
 [<span data-ttu-id="86d0b-112">Como trabalhar com assemblies e o cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="86d0b-112">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [<span data-ttu-id="86d0b-113">Gacutil.exe (Ferramenta do Cache de Assemblies Global)</span><span class="sxs-lookup"><span data-stu-id="86d0b-113">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
