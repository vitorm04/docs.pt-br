---
title: DeliveryRequirementsAttribute
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 172f7df4f028c1ddc0f5565e95291e857ee6fa1d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="deliveryrequirementsattribute"></a><span data-ttu-id="e08fe-102">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="e08fe-102">DeliveryRequirementsAttribute</span></span>
<span data-ttu-id="e08fe-103">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="e08fe-103">DeliveryRequirementsAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e08fe-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e08fe-104">Syntax</span></span>  
  
```  
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e08fe-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="e08fe-105">Methods</span></span>  
 <span data-ttu-id="e08fe-106">A classe DeliveryRequirementsAttribute não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="e08fe-106">The DeliveryRequirementsAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e08fe-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="e08fe-107">Properties</span></span>  
 <span data-ttu-id="e08fe-108">A classe DeliveryRequirementsAttribute tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="e08fe-108">The DeliveryRequirementsAttribute class has the following properties:</span></span>  
  
### <a name="queueddeliveryrequirements"></a><span data-ttu-id="e08fe-109">QueuedDeliveryRequirements</span><span class="sxs-lookup"><span data-stu-id="e08fe-109">QueuedDeliveryRequirements</span></span>  
 <span data-ttu-id="e08fe-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="e08fe-110">Data type: string</span></span>  
  
 <span data-ttu-id="e08fe-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="e08fe-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e08fe-112">Especifica se a associação para um serviço oferece suporte a contratos.</span><span class="sxs-lookup"><span data-stu-id="e08fe-112">Specifies whether the binding for a service supports contracts.</span></span>  
  
### <a name="requireordereddelivery"></a><span data-ttu-id="e08fe-113">RequireOrderedDelivery</span><span class="sxs-lookup"><span data-stu-id="e08fe-113">RequireOrderedDelivery</span></span>  
 <span data-ttu-id="e08fe-114">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="e08fe-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="e08fe-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="e08fe-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e08fe-116">Especifica se a associação oferece suporte a mensagens ordenadas.</span><span class="sxs-lookup"><span data-stu-id="e08fe-116">Specifies whether the binding supports ordered messages.</span></span>  
  
### <a name="targetcontract"></a><span data-ttu-id="e08fe-117">TargetContract</span><span class="sxs-lookup"><span data-stu-id="e08fe-117">TargetContract</span></span>  
 <span data-ttu-id="e08fe-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="e08fe-118">Data type: string</span></span>  
  
 <span data-ttu-id="e08fe-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="e08fe-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e08fe-120">O contrato ao qual se aplica.</span><span class="sxs-lookup"><span data-stu-id="e08fe-120">The contract to which it applies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e08fe-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e08fe-121">Requirements</span></span>  
  
|<span data-ttu-id="e08fe-122">MOF</span><span class="sxs-lookup"><span data-stu-id="e08fe-122">MOF</span></span>|<span data-ttu-id="e08fe-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e08fe-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e08fe-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="e08fe-124">Namespace</span></span>|<span data-ttu-id="e08fe-125">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e08fe-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e08fe-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e08fe-126">See Also</span></span>  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>
