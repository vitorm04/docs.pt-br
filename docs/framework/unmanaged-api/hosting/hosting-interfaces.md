---
title: Interfaces de hospedagem
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting]
- hosting interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], hosting
ms.assetid: cc64cb05-38da-418e-815a-daac8e8e26e5
ms.openlocfilehash: b1459bf78276abe0daefd7a7ee814841f3c65dfb
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550658"
---
# <a name="hosting-interfaces"></a><span data-ttu-id="d9973-102">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="d9973-102">Hosting Interfaces</span></span>
<span data-ttu-id="d9973-103">Esta seção descreve as interfaces que os hosts não gerenciados podem usar para integrar o Common Language Runtime (CLR) em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="d9973-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span>  
  
 <span data-ttu-id="d9973-104">As interfaces de hospedagem do .NET Framework versão 2,0 substituem as interfaces da versão 1,0 e 1,1 do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d9973-104">The .NET Framework version 2.0 hosting interfaces supersede the .NET Framework version 1.0 and 1.1 interfaces.</span></span> <span data-ttu-id="d9973-105">Há diferenças significativas entre os dois conjuntos de interfaces.</span><span class="sxs-lookup"><span data-stu-id="d9973-105">There are significant differences between the two sets of interfaces.</span></span> <span data-ttu-id="d9973-106">A combinação deles pode causar um comportamento inesperado e não é recomendável.</span><span class="sxs-lookup"><span data-stu-id="d9973-106">Mixing them could cause unexpected behavior and is not recommended.</span></span>  
  
 <span data-ttu-id="d9973-107">As versões 3,0 e 3,5 do .NET Framework usam as interfaces de hospedagem 2,0 da versão .NET Framework e não introduzem nenhum recurso de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="d9973-107">The .NET Framework versions 3.0 and 3.5 use the .NET Framework version 2.0 hosting interfaces, and do not introduce any hosting features.</span></span>  
  
 <span data-ttu-id="d9973-108">As interfaces de hospedagem do .NET Framework 4 substituem as interfaces .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="d9973-108">The .NET Framework 4 hosting interfaces supersede the .NET Framework 2.0 interfaces.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="d9973-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="d9973-109">In This Section</span></span>  
 [<span data-ttu-id="d9973-110">Interfaces e coclasse de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="d9973-110">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="d9973-111">Descreve as interfaces de hospedagem introduzidas no .NET Framework versões 1,0 e 1,1.</span><span class="sxs-lookup"><span data-stu-id="d9973-111">Describes the hosting interfaces introduced in the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="d9973-112">Interfaces de hospedagem CLR</span><span class="sxs-lookup"><span data-stu-id="d9973-112">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)  
 <span data-ttu-id="d9973-113">Descreve as interfaces de hospedagem introduzidas no .NET Framework versão 2,0.</span><span class="sxs-lookup"><span data-stu-id="d9973-113">Describes the hosting interfaces introduced in the .NET Framework version 2.0.</span></span>  
  
 [<span data-ttu-id="d9973-114">Interfaces de hospedagem CLR adicionadas no .NET Framework 4 e 4.5</span><span class="sxs-lookup"><span data-stu-id="d9973-114">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="d9973-115">Descreve as interfaces de hospedagem introduzidas no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d9973-115">Describes the hosting interfaces introduced in the .NET Framework 4.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d9973-116">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="d9973-116">Related Sections</span></span>  
 [<span data-ttu-id="d9973-117">Hospedando coclasses</span><span class="sxs-lookup"><span data-stu-id="d9973-117">Hosting Coclasses</span></span>](hosting-coclasses.md)  
  
 [<span data-ttu-id="d9973-118">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="d9973-118">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)  
  
 [<span data-ttu-id="d9973-119">Hospedando enumerações</span><span class="sxs-lookup"><span data-stu-id="d9973-119">Hosting Enumerations</span></span>](hosting-enumerations.md)  
  
 [<span data-ttu-id="d9973-120">Estruturas de hospedagem</span><span class="sxs-lookup"><span data-stu-id="d9973-120">Hosting Structures</span></span>](hosting-structures.md)  
  
 [<span data-ttu-id="d9973-121">Hosting</span><span class="sxs-lookup"><span data-stu-id="d9973-121">Hosting</span></span>](index.md)  
  
 <span data-ttu-id="d9973-122">[Hosts de runtime](/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d9973-122">[Runtime Hosts](/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span></span>
