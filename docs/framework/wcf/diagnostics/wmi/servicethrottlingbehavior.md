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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 779aabf5ec9b1bca7151eaf781c6dd6f2631b58f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="servicethrottlingbehavior"></a><span data-ttu-id="d25f7-102">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="d25f7-102">ServiceThrottlingBehavior</span></span>
<span data-ttu-id="d25f7-103">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="d25f7-103">ServiceThrottlingBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d25f7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d25f7-104">Syntax</span></span>  
  
```  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d25f7-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="d25f7-105">Methods</span></span>  
 <span data-ttu-id="d25f7-106">A classe ServiceThrottlingBehavior não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="d25f7-106">The ServiceThrottlingBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d25f7-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="d25f7-107">Properties</span></span>  
 <span data-ttu-id="d25f7-108">A classe ServiceThrottlingBehavior tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="d25f7-108">The ServiceThrottlingBehavior class has the following properties:</span></span>  
  
### <a name="maxconcurrentcalls"></a><span data-ttu-id="d25f7-109">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="d25f7-109">MaxConcurrentCalls</span></span>  
 <span data-ttu-id="d25f7-110">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="d25f7-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="d25f7-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="d25f7-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d25f7-112">O número máximo de mensagens processando ativamente entre todos os objetos do distribuidor em um ServiceHost.</span><span class="sxs-lookup"><span data-stu-id="d25f7-112">The maximum number of messages actively processing across all dispatcher objects in a ServiceHost.</span></span>  
  
### <a name="maxconcurrentinstances"></a><span data-ttu-id="d25f7-113">MaxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="d25f7-113">MaxConcurrentInstances</span></span>  
 <span data-ttu-id="d25f7-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="d25f7-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="d25f7-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="d25f7-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d25f7-116">O número máximo de objetos de serviço que podem ser executados ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="d25f7-116">The maximum number of service objects that can execute at one time.</span></span>  
  
### <a name="maxconcurrentsessions"></a><span data-ttu-id="d25f7-117">MaxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="d25f7-117">MaxConcurrentSessions</span></span>  
 <span data-ttu-id="d25f7-118">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="d25f7-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="d25f7-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="d25f7-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d25f7-120">O número máximo de sessões que um host pode aceitar de cada vez.</span><span class="sxs-lookup"><span data-stu-id="d25f7-120">The maximum number of sessions a host can accept at one time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d25f7-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d25f7-121">Requirements</span></span>  
  
|<span data-ttu-id="d25f7-122">MOF</span><span class="sxs-lookup"><span data-stu-id="d25f7-122">MOF</span></span>|<span data-ttu-id="d25f7-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d25f7-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d25f7-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="d25f7-124">Namespace</span></span>|<span data-ttu-id="d25f7-125">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d25f7-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d25f7-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d25f7-126">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
