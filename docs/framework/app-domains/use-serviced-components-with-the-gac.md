---
title: Usando componentes atendidos com o cache de assemblies global
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache), serviced components
- serviced components, global assembly cache
- global assembly cache, serviced components
ms.assetid: 3423e5d9-234c-4571-8161-e35f6d130128
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4bb09f827726f759383598d18fb80657a7e2ff04
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59179056"
---
# <a name="using-serviced-components-with-the-global-assembly-cache"></a><span data-ttu-id="2dcd8-102">Usando componentes atendidos com o cache de assemblies global</span><span class="sxs-lookup"><span data-stu-id="2dcd8-102">Using Serviced Components with the Global Assembly Cache</span></span>
<span data-ttu-id="2dcd8-103">Componentes atendidos (componentes COM+ com código gerenciado) devem ser colocados no Cache de Assembly Global.</span><span class="sxs-lookup"><span data-stu-id="2dcd8-103">Serviced components (managed code COM+ components) should be put in the Global Assembly Cache.</span></span> <span data-ttu-id="2dcd8-104">Em alguns cenários, o Common Language Runtime e os Serviços COM+ podem manipular componentes atendidos que não estão no Cache de Assembly Global; em outros cenários, eles não podem.</span><span class="sxs-lookup"><span data-stu-id="2dcd8-104">In some scenarios, the Common Language Runtime and COM+ Services can handle serviced components that are not in the Global Assembly Cache; in other scenarios, they cannot.</span></span> <span data-ttu-id="2dcd8-105">Os seguintes cenários ilustram isso:</span><span class="sxs-lookup"><span data-stu-id="2dcd8-105">The following scenarios illustrate this:</span></span>  
  
-   <span data-ttu-id="2dcd8-106">Para componentes atendidos em um aplicativo COM+ para Servidor, o assembly que contém os componentes deve estar no Cache de Assembly Global, pois Dllhost.exe não é executado no mesmo diretório que contém os componentes atendidos.</span><span class="sxs-lookup"><span data-stu-id="2dcd8-106">For serviced components in a COM+ Server application, the assembly containing the components must be in the Global Assembly Cache, because Dllhost.exe does not run in the same directory as the one that contains the serviced components.</span></span>  
  
-   <span data-ttu-id="2dcd8-107">Para componentes atendidos em um aplicativo de COM+ Library, o tempo de execução e COM+ Services podem resolver as referências ao assembly que contém os componentes pesquisando o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="2dcd8-107">For serviced components in a COM+ Library application, the runtime and COM+ Services can resolve the reference to the assembly containing the components by searching in the current directory.</span></span> <span data-ttu-id="2dcd8-108">Nesse caso, o assembly não precisa estar no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="2dcd8-108">In this case, the assembly does not have to be in the global assembly cache.</span></span>  
  
-   <span data-ttu-id="2dcd8-109">Para componentes atendidos em um aplicativo ASP.NET, a situação é diferente.</span><span class="sxs-lookup"><span data-stu-id="2dcd8-109">For serviced components in an ASP.NET application, the situation is different.</span></span> <span data-ttu-id="2dcd8-110">Se você colocar o assembly que contém os componentes atendidos no diretório bin da base de aplicativo e usar o registro sob demanda, o assembly será copiado por sombra para o cache de download, pois o ASP.NET aproveita os recursos de sombra do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="2dcd8-110">If you place the assembly containing the serviced components in the bin directory of the application base and use on-demand registration, the assembly will be shadow-copied into the download cache because ASP.NET leverages the shadow capabilities of the runtime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dcd8-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2dcd8-111">See also</span></span>

- [<span data-ttu-id="2dcd8-112">Trabalhando com assemblies e o cache de assemblies global</span><span class="sxs-lookup"><span data-stu-id="2dcd8-112">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="2dcd8-113">Gacutil.exe (Ferramenta do Cache de Assemblies Global)</span><span class="sxs-lookup"><span data-stu-id="2dcd8-113">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
