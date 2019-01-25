---
title: ServiceThrottlingBehavior
ms.date: 03/30/2017
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
ms.openlocfilehash: 98e8a720e92547ca0a893dd988b91cb7907660b5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689845"
---
# <a name="servicethrottlingbehavior"></a><span data-ttu-id="afc10-102">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="afc10-102">ServiceThrottlingBehavior</span></span>
<span data-ttu-id="afc10-103">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="afc10-103">ServiceThrottlingBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afc10-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="afc10-104">Syntax</span></span>  
  
```csharp  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="afc10-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="afc10-105">Methods</span></span>  
 <span data-ttu-id="afc10-106">A classe ServiceThrottlingBehavior não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="afc10-106">The ServiceThrottlingBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="afc10-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="afc10-107">Properties</span></span>  
 <span data-ttu-id="afc10-108">A classe ServiceThrottlingBehavior tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="afc10-108">The ServiceThrottlingBehavior class has the following properties:</span></span>  
  
### <a name="maxconcurrentcalls"></a><span data-ttu-id="afc10-109">MaxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="afc10-109">MaxConcurrentCalls</span></span>  
 <span data-ttu-id="afc10-110">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="afc10-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="afc10-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="afc10-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="afc10-112">O número máximo de mensagens processando ativamente entre todos os objetos de dispatcher em um ServiceHost.</span><span class="sxs-lookup"><span data-stu-id="afc10-112">The maximum number of messages actively processing across all dispatcher objects in a ServiceHost.</span></span>  
  
### <a name="maxconcurrentinstances"></a><span data-ttu-id="afc10-113">MaxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="afc10-113">MaxConcurrentInstances</span></span>  
 <span data-ttu-id="afc10-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="afc10-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="afc10-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="afc10-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="afc10-116">O número máximo de objetos de serviço que podem ser executadas ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="afc10-116">The maximum number of service objects that can execute at one time.</span></span>  
  
### <a name="maxconcurrentsessions"></a><span data-ttu-id="afc10-117">MaxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="afc10-117">MaxConcurrentSessions</span></span>  
 <span data-ttu-id="afc10-118">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="afc10-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="afc10-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="afc10-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="afc10-120">O número máximo de sessões que um host pode aceitar simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="afc10-120">The maximum number of sessions a host can accept at one time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afc10-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="afc10-121">Requirements</span></span>  
  
|<span data-ttu-id="afc10-122">MOF</span><span class="sxs-lookup"><span data-stu-id="afc10-122">MOF</span></span>|<span data-ttu-id="afc10-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="afc10-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="afc10-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="afc10-124">Namespace</span></span>|<span data-ttu-id="afc10-125">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="afc10-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="afc10-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="afc10-126">See also</span></span>
- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
