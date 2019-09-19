---
title: Assemblies e execução lado a lado
ms.date: 08/20/2019
helpviewer_keywords:
- side-by-side execution [.NET Framework]
- assemblies [.NET Framework], side-by-side execution
ms.assetid: e42036ee-7590-47d1-b884-cc856e39bd5d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d4f246108768dcebf51348f67c4523cb83df4f9d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053975"
---
# <a name="assemblies-and-side-by-side-execution"></a><span data-ttu-id="c3908-102">Assemblies e execução lado a lado</span><span class="sxs-lookup"><span data-stu-id="c3908-102">Assemblies and side-by-side execution</span></span>

<span data-ttu-id="c3908-103">Execução lado a lado é a capacidade de armazenar e executar várias versões de um aplicativo ou componente no mesmo computador.</span><span class="sxs-lookup"><span data-stu-id="c3908-103">Side-by-side execution is the ability to store and execute multiple versions of an application or component on the same computer.</span></span> <span data-ttu-id="c3908-104">Isso significa que você pode ter várias versões do tempo de execução e várias versões de aplicativos e componentes que usam uma versão do tempo de execução no mesmo computador ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="c3908-104">This means that you can have multiple versions of the runtime, and multiple versions of applications and components that use a version of the runtime, on the same computer at the same time.</span></span> <span data-ttu-id="c3908-105">A execução lado a lado confere mais controle sobre a quais versões de um componente um aplicativo está associado e mais controle sobre qual versão do tempo de execução um aplicativo usa.</span><span class="sxs-lookup"><span data-stu-id="c3908-105">Side-by-side execution gives you more control over what versions of a component an application binds to, and more control over what version of the runtime an application uses.</span></span>  
  
<span data-ttu-id="c3908-106">O suporte para armazenamento lado a lado e execução de diferentes versões do mesmo assembly é uma parte integrante da nomenclatura forte e está integrada à infraestrutura do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c3908-106">Support for side-by-side storage and execution of different versions of the same assembly is an integral part of strong naming and is built into the infrastructure of the runtime.</span></span> <span data-ttu-id="c3908-107">Como o número de versão do assembly de nome forte faz parte de sua identidade, o tempo de execução pode armazenar várias versões do mesmo assembly no cache de assembly global e carregar esses módulos em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c3908-107">Because the strong-named assembly's version number is part of its identity, the runtime can store multiple versions of the same assembly in the global assembly cache and load those assemblies at run time.</span></span>  
  
<span data-ttu-id="c3908-108">Embora o tempo de execução ofereça a capacidade de criar aplicativos lado a lado, a execução lado a lado não é automática.</span><span class="sxs-lookup"><span data-stu-id="c3908-108">Although the runtime provides you with the ability to create side-by-side applications, side-by-side execution is not automatic.</span></span> <span data-ttu-id="c3908-109">Para obter mais informações sobre como criar aplicativos para execução lado a lado, consulte [diretrizes para criar componentes para execução lado a lado](../../framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).</span><span class="sxs-lookup"><span data-stu-id="c3908-109">For more information on creating applications for side-by-side execution, see [Guidelines for creating components for side-by-side execution](../../framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3908-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3908-110">See also</span></span>

- [<span data-ttu-id="c3908-111">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="c3908-111">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="c3908-112">Assemblies no .NET</span><span class="sxs-lookup"><span data-stu-id="c3908-112">Assemblies in .NET</span></span>](index.md)
