---
title: Assemblies e execução lado a lado
description: Saiba mais sobre a execução lado a lado, que é a capacidade de armazenar e executar várias versões de um aplicativo ou componente no mesmo computador.
ms.date: 08/20/2019
helpviewer_keywords:
- side-by-side execution [.NET Framework]
- assemblies [.NET Framework], side-by-side execution
ms.assetid: e42036ee-7590-47d1-b884-cc856e39bd5d
ms.openlocfilehash: 74b5710c7e8ad60873fb83a3699ce3992ead6e07
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378638"
---
# <a name="assemblies-and-side-by-side-execution"></a><span data-ttu-id="dd1d9-103">Assemblies e execução lado a lado</span><span class="sxs-lookup"><span data-stu-id="dd1d9-103">Assemblies and side-by-side execution</span></span>

<span data-ttu-id="dd1d9-104">Execução lado a lado é a capacidade de armazenar e executar várias versões de um aplicativo ou componente no mesmo computador.</span><span class="sxs-lookup"><span data-stu-id="dd1d9-104">Side-by-side execution is the ability to store and execute multiple versions of an application or component on the same computer.</span></span> <span data-ttu-id="dd1d9-105">Isso significa que você pode ter várias versões do runtime e várias versões de aplicativos e componentes que usam uma versão do runtime no mesmo computador ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="dd1d9-105">This means that you can have multiple versions of the runtime, and multiple versions of applications and components that use a version of the runtime, on the same computer at the same time.</span></span> <span data-ttu-id="dd1d9-106">A execução lado a lado confere mais controle sobre a quais versões de um componente um aplicativo está associado e mais controle sobre qual versão do runtime um aplicativo usa.</span><span class="sxs-lookup"><span data-stu-id="dd1d9-106">Side-by-side execution gives you more control over what versions of a component an application binds to, and more control over what version of the runtime an application uses.</span></span>  
  
<span data-ttu-id="dd1d9-107">O suporte para armazenamento lado a lado e execução de diferentes versões do mesmo assembly é uma parte integrante da nomenclatura forte e está integrada à infraestrutura do runtime.</span><span class="sxs-lookup"><span data-stu-id="dd1d9-107">Support for side-by-side storage and execution of different versions of the same assembly is an integral part of strong naming and is built into the infrastructure of the runtime.</span></span> <span data-ttu-id="dd1d9-108">Como o número de versão do assembly de nome forte faz parte de sua identidade, o runtime pode armazenar várias versões do mesmo assembly no cache de assembly global e carregar esses módulos em runtime.</span><span class="sxs-lookup"><span data-stu-id="dd1d9-108">Because the strong-named assembly's version number is part of its identity, the runtime can store multiple versions of the same assembly in the global assembly cache and load those assemblies at run time.</span></span>  
  
<span data-ttu-id="dd1d9-109">Embora o runtime ofereça a capacidade de criar aplicativos lado a lado, a execução lado a lado não é automática.</span><span class="sxs-lookup"><span data-stu-id="dd1d9-109">Although the runtime provides you with the ability to create side-by-side applications, side-by-side execution is not automatic.</span></span> <span data-ttu-id="dd1d9-110">Para obter mais informações sobre como criar aplicativos para execução lado a lado, consulte [diretrizes para criar componentes para execução lado a lado](../../framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).</span><span class="sxs-lookup"><span data-stu-id="dd1d9-110">For more information on creating applications for side-by-side execution, see [Guidelines for creating components for side-by-side execution](../../framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd1d9-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="dd1d9-111">See also</span></span>

- [<span data-ttu-id="dd1d9-112">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="dd1d9-112">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="dd1d9-113">Assemblies no .NET</span><span class="sxs-lookup"><span data-stu-id="dd1d9-113">Assemblies in .NET</span></span>](index.md)
