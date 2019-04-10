---
title: ServiceThrottlingBehavior
ms.date: 03/30/2017
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
ms.openlocfilehash: 572e458f08c4717207667db9940296c4a957199a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225489"
---
# <a name="servicethrottlingbehavior"></a><span data-ttu-id="40db8-102">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="40db8-102">ServiceThrottlingBehavior</span></span>
<span data-ttu-id="40db8-103">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="40db8-103">ServiceThrottlingBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40db8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="40db8-104">Syntax</span></span>  
  
```csharp  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="40db8-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="40db8-105">Methods</span></span>  
 <span data-ttu-id="40db8-106">A classe ServiceThrottlingBehavior não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="40db8-106">The ServiceThrottlingBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="40db8-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="40db8-107">Properties</span></span>  
 <span data-ttu-id="40db8-108">A classe ServiceThrottlingBehavior tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="40db8-108">The ServiceThrottlingBehavior class has the following properties:</span></span>  
  
### <a name="maxconcurrentcalls"></a><span data-ttu-id="40db8-109">MaxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="40db8-109">MaxConcurrentCalls</span></span>  
 <span data-ttu-id="40db8-110">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="40db8-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="40db8-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="40db8-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="40db8-112">O número máximo de mensagens processando ativamente entre todos os objetos de dispatcher em um ServiceHost.</span><span class="sxs-lookup"><span data-stu-id="40db8-112">The maximum number of messages actively processing across all dispatcher objects in a ServiceHost.</span></span>  
  
### <a name="maxconcurrentinstances"></a><span data-ttu-id="40db8-113">MaxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="40db8-113">MaxConcurrentInstances</span></span>  
 <span data-ttu-id="40db8-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="40db8-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="40db8-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="40db8-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="40db8-116">O número máximo de objetos de serviço que podem ser executadas ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="40db8-116">The maximum number of service objects that can execute at one time.</span></span>  
  
### <a name="maxconcurrentsessions"></a><span data-ttu-id="40db8-117">MaxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="40db8-117">MaxConcurrentSessions</span></span>  
 <span data-ttu-id="40db8-118">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="40db8-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="40db8-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="40db8-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="40db8-120">O número máximo de sessões que um host pode aceitar simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="40db8-120">The maximum number of sessions a host can accept at one time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40db8-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="40db8-121">Requirements</span></span>  
  
|<span data-ttu-id="40db8-122">MOF</span><span class="sxs-lookup"><span data-stu-id="40db8-122">MOF</span></span>|<span data-ttu-id="40db8-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="40db8-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="40db8-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="40db8-124">Namespace</span></span>|<span data-ttu-id="40db8-125">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="40db8-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="40db8-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="40db8-126">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
