---
title: ServiceThrottlingBehavior
ms.date: 03/30/2017
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
ms.openlocfilehash: edc154fcce0058455f1376a2a45807c92f7f2457
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2018
ms.locfileid: "49373671"
---
# <a name="servicethrottlingbehavior"></a><span data-ttu-id="e693d-102">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="e693d-102">ServiceThrottlingBehavior</span></span>
<span data-ttu-id="e693d-103">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="e693d-103">ServiceThrottlingBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e693d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e693d-104">Syntax</span></span>  
  
```csharp  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e693d-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="e693d-105">Methods</span></span>  
 <span data-ttu-id="e693d-106">A classe ServiceThrottlingBehavior não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="e693d-106">The ServiceThrottlingBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e693d-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="e693d-107">Properties</span></span>  
 <span data-ttu-id="e693d-108">A classe ServiceThrottlingBehavior tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="e693d-108">The ServiceThrottlingBehavior class has the following properties:</span></span>  
  
### <a name="maxconcurrentcalls"></a><span data-ttu-id="e693d-109">MaxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="e693d-109">MaxConcurrentCalls</span></span>  
 <span data-ttu-id="e693d-110">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="e693d-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="e693d-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="e693d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e693d-112">O número máximo de mensagens processando ativamente entre todos os objetos de dispatcher em um ServiceHost.</span><span class="sxs-lookup"><span data-stu-id="e693d-112">The maximum number of messages actively processing across all dispatcher objects in a ServiceHost.</span></span>  
  
### <a name="maxconcurrentinstances"></a><span data-ttu-id="e693d-113">MaxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="e693d-113">MaxConcurrentInstances</span></span>  
 <span data-ttu-id="e693d-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="e693d-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="e693d-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="e693d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e693d-116">O número máximo de objetos de serviço que podem ser executadas ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="e693d-116">The maximum number of service objects that can execute at one time.</span></span>  
  
### <a name="maxconcurrentsessions"></a><span data-ttu-id="e693d-117">MaxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="e693d-117">MaxConcurrentSessions</span></span>  
 <span data-ttu-id="e693d-118">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="e693d-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="e693d-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="e693d-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e693d-120">O número máximo de sessões que um host pode aceitar simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="e693d-120">The maximum number of sessions a host can accept at one time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e693d-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e693d-121">Requirements</span></span>  
  
|<span data-ttu-id="e693d-122">MOF</span><span class="sxs-lookup"><span data-stu-id="e693d-122">MOF</span></span>|<span data-ttu-id="e693d-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e693d-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e693d-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="e693d-124">Namespace</span></span>|<span data-ttu-id="e693d-125">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e693d-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e693d-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e693d-126">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
