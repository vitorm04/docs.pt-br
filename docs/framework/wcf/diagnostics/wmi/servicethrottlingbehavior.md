---
title: ServiceThrottlingBehavior
ms.date: 03/30/2017
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
ms.openlocfilehash: 9a7fbf93dbdbf1a6debcf865b4883b5784e2ff4a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487601"
---
# <a name="servicethrottlingbehavior"></a><span data-ttu-id="a5969-102">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="a5969-102">ServiceThrottlingBehavior</span></span>
<span data-ttu-id="a5969-103">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="a5969-103">ServiceThrottlingBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5969-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a5969-104">Syntax</span></span>  
  
```  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a5969-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="a5969-105">Methods</span></span>  
 <span data-ttu-id="a5969-106">A classe ServiceThrottlingBehavior não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="a5969-106">The ServiceThrottlingBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a5969-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="a5969-107">Properties</span></span>  
 <span data-ttu-id="a5969-108">A classe ServiceThrottlingBehavior tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="a5969-108">The ServiceThrottlingBehavior class has the following properties:</span></span>  
  
### <a name="maxconcurrentcalls"></a><span data-ttu-id="a5969-109">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="a5969-109">MaxConcurrentCalls</span></span>  
 <span data-ttu-id="a5969-110">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="a5969-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="a5969-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a5969-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a5969-112">O número máximo de mensagens processando ativamente entre todos os objetos do distribuidor em um ServiceHost.</span><span class="sxs-lookup"><span data-stu-id="a5969-112">The maximum number of messages actively processing across all dispatcher objects in a ServiceHost.</span></span>  
  
### <a name="maxconcurrentinstances"></a><span data-ttu-id="a5969-113">MaxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="a5969-113">MaxConcurrentInstances</span></span>  
 <span data-ttu-id="a5969-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="a5969-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="a5969-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a5969-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a5969-116">O número máximo de objetos de serviço que podem ser executados ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="a5969-116">The maximum number of service objects that can execute at one time.</span></span>  
  
### <a name="maxconcurrentsessions"></a><span data-ttu-id="a5969-117">MaxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="a5969-117">MaxConcurrentSessions</span></span>  
 <span data-ttu-id="a5969-118">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="a5969-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="a5969-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="a5969-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a5969-120">O número máximo de sessões que um host pode aceitar de cada vez.</span><span class="sxs-lookup"><span data-stu-id="a5969-120">The maximum number of sessions a host can accept at one time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5969-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a5969-121">Requirements</span></span>  
  
|<span data-ttu-id="a5969-122">MOF</span><span class="sxs-lookup"><span data-stu-id="a5969-122">MOF</span></span>|<span data-ttu-id="a5969-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="a5969-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a5969-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="a5969-124">Namespace</span></span>|<span data-ttu-id="a5969-125">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a5969-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a5969-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a5969-126">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
