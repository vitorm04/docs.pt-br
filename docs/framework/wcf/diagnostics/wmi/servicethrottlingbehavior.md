---
title: ServiceThrottlingBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 59f85a148d6707876a4df512d5cfbd07ca0e54b7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="servicethrottlingbehavior"></a><span data-ttu-id="8587c-102">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="8587c-102">ServiceThrottlingBehavior</span></span>
<span data-ttu-id="8587c-103">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="8587c-103">ServiceThrottlingBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8587c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8587c-104">Syntax</span></span>  
  
```  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="8587c-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="8587c-105">Methods</span></span>  
 <span data-ttu-id="8587c-106">A classe ServiceThrottlingBehavior não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="8587c-106">The ServiceThrottlingBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="8587c-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="8587c-107">Properties</span></span>  
 <span data-ttu-id="8587c-108">A classe ServiceThrottlingBehavior tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="8587c-108">The ServiceThrottlingBehavior class has the following properties:</span></span>  
  
### <a name="maxconcurrentcalls"></a><span data-ttu-id="8587c-109">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="8587c-109">MaxConcurrentCalls</span></span>  
 <span data-ttu-id="8587c-110">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="8587c-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="8587c-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="8587c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8587c-112">O número máximo de mensagens processando ativamente entre todos os objetos do distribuidor em um ServiceHost.</span><span class="sxs-lookup"><span data-stu-id="8587c-112">The maximum number of messages actively processing across all dispatcher objects in a ServiceHost.</span></span>  
  
### <a name="maxconcurrentinstances"></a><span data-ttu-id="8587c-113">MaxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="8587c-113">MaxConcurrentInstances</span></span>  
 <span data-ttu-id="8587c-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="8587c-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="8587c-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="8587c-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8587c-116">O número máximo de objetos de serviço que podem ser executados ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="8587c-116">The maximum number of service objects that can execute at one time.</span></span>  
  
### <a name="maxconcurrentsessions"></a><span data-ttu-id="8587c-117">MaxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="8587c-117">MaxConcurrentSessions</span></span>  
 <span data-ttu-id="8587c-118">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="8587c-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="8587c-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="8587c-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8587c-120">O número máximo de sessões que um host pode aceitar de cada vez.</span><span class="sxs-lookup"><span data-stu-id="8587c-120">The maximum number of sessions a host can accept at one time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8587c-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8587c-121">Requirements</span></span>  
  
|<span data-ttu-id="8587c-122">MOF</span><span class="sxs-lookup"><span data-stu-id="8587c-122">MOF</span></span>|<span data-ttu-id="8587c-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="8587c-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="8587c-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="8587c-124">Namespace</span></span>|<span data-ttu-id="8587c-125">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8587c-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8587c-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8587c-126">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
