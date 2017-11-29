---
title: Interfaces de hospedagem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- interfaces [.NET Framework hosting]
- hosting interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], hosting
ms.assetid: cc64cb05-38da-418e-815a-daac8e8e26e5
caps.latest.revision: "23"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a3cad92c204fa10f72d7a9a61460f1234206cb39
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="hosting-interfaces"></a><span data-ttu-id="20c1f-102">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="20c1f-102">Hosting Interfaces</span></span>
<span data-ttu-id="20c1f-103">Esta seção descreve as interfaces não gerenciadas hosts podem usar para integrar o common language runtime (CLR) em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="20c1f-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span>  
  
 <span data-ttu-id="20c1f-104">As interfaces de hospedagem do .NET Framework versão 2.0 substituem as interfaces do .NET Framework versão 1.0 e 1.1.</span><span class="sxs-lookup"><span data-stu-id="20c1f-104">The .NET Framework version 2.0 hosting interfaces supersede the .NET Framework version 1.0 and 1.1 interfaces.</span></span> <span data-ttu-id="20c1f-105">Há diferenças significativas entre os dois conjuntos de interfaces.</span><span class="sxs-lookup"><span data-stu-id="20c1f-105">There are significant differences between the two sets of interfaces.</span></span> <span data-ttu-id="20c1f-106">Mesclando-los pode causar um comportamento inesperado e não é recomendado.</span><span class="sxs-lookup"><span data-stu-id="20c1f-106">Mixing them could cause unexpected behavior and is not recommended.</span></span>  
  
 <span data-ttu-id="20c1f-107">As versões do .NET Framework 3.0 e 3.5 usam as interfaces de hospedagem do .NET Framework versão 2.0 e não apresenta os recursos de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="20c1f-107">The .NET Framework versions 3.0 and 3.5 use the .NET Framework version 2.0 hosting interfaces, and do not introduce any hosting features.</span></span>  
  
 <span data-ttu-id="20c1f-108">O [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] interfaces de hospedagem substituem as interfaces do .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="20c1f-108">The [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] hosting interfaces supersede the .NET Framework 2.0 interfaces.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="20c1f-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="20c1f-109">In This Section</span></span>  
 [<span data-ttu-id="20c1f-110">Interfaces e coclasse de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="20c1f-110">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="20c1f-111">Descreve as interfaces de hospedagem introduzidas nas versões do .NET Framework 1.0 e 1.1.</span><span class="sxs-lookup"><span data-stu-id="20c1f-111">Describes the hosting interfaces introduced in the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="20c1f-112">Interfaces de hospedagem CLR</span><span class="sxs-lookup"><span data-stu-id="20c1f-112">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 <span data-ttu-id="20c1f-113">Descreve as interfaces de hospedagem introduzidas no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="20c1f-113">Describes the hosting interfaces introduced in the .NET Framework version 2.0.</span></span>  
  
 [<span data-ttu-id="20c1f-114">Interfaces de hospedagem CLR adicionadas no .NET Framework 4 e 4.5</span><span class="sxs-lookup"><span data-stu-id="20c1f-114">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="20c1f-115">Descreve as interfaces de hospedagem introduzidas no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="20c1f-115">Describes the hosting interfaces introduced in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="20c1f-116">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="20c1f-116">Related Sections</span></span>  
 [<span data-ttu-id="20c1f-117">Coclasses de hospedagem</span><span class="sxs-lookup"><span data-stu-id="20c1f-117">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)  
  
 [<span data-ttu-id="20c1f-118">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="20c1f-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
  
 [<span data-ttu-id="20c1f-119">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="20c1f-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
  
 [<span data-ttu-id="20c1f-120">Estruturas de hospedagem</span><span class="sxs-lookup"><span data-stu-id="20c1f-120">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
  
 [<span data-ttu-id="20c1f-121">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="20c1f-121">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
  
 [<span data-ttu-id="20c1f-122">Hosts de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="20c1f-122">Runtime Hosts</span></span>](http://msdn.microsoft.com/en-us/99d9246a-b994-4fe5-985c-8588d1d59998)
