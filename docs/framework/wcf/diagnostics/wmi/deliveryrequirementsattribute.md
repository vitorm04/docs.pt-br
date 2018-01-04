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
ms.workload: dotnet
ms.openlocfilehash: e297bfc0499ea3ee8d3dd8395165ca22b2baa1de
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="deliveryrequirementsattribute"></a><span data-ttu-id="d476d-102">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="d476d-102">DeliveryRequirementsAttribute</span></span>
<span data-ttu-id="d476d-103">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="d476d-103">DeliveryRequirementsAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d476d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d476d-104">Syntax</span></span>  
  
```  
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d476d-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="d476d-105">Methods</span></span>  
 <span data-ttu-id="d476d-106">A classe DeliveryRequirementsAttribute não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="d476d-106">The DeliveryRequirementsAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d476d-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="d476d-107">Properties</span></span>  
 <span data-ttu-id="d476d-108">A classe DeliveryRequirementsAttribute tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="d476d-108">The DeliveryRequirementsAttribute class has the following properties:</span></span>  
  
### <a name="queueddeliveryrequirements"></a><span data-ttu-id="d476d-109">QueuedDeliveryRequirements</span><span class="sxs-lookup"><span data-stu-id="d476d-109">QueuedDeliveryRequirements</span></span>  
 <span data-ttu-id="d476d-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="d476d-110">Data type: string</span></span>  
  
 <span data-ttu-id="d476d-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="d476d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d476d-112">Especifica se a associação para um serviço oferece suporte a contratos.</span><span class="sxs-lookup"><span data-stu-id="d476d-112">Specifies whether the binding for a service supports contracts.</span></span>  
  
### <a name="requireordereddelivery"></a><span data-ttu-id="d476d-113">RequireOrderedDelivery</span><span class="sxs-lookup"><span data-stu-id="d476d-113">RequireOrderedDelivery</span></span>  
 <span data-ttu-id="d476d-114">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="d476d-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="d476d-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="d476d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d476d-116">Especifica se a associação oferece suporte a mensagens ordenadas.</span><span class="sxs-lookup"><span data-stu-id="d476d-116">Specifies whether the binding supports ordered messages.</span></span>  
  
### <a name="targetcontract"></a><span data-ttu-id="d476d-117">TargetContract</span><span class="sxs-lookup"><span data-stu-id="d476d-117">TargetContract</span></span>  
 <span data-ttu-id="d476d-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="d476d-118">Data type: string</span></span>  
  
 <span data-ttu-id="d476d-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="d476d-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d476d-120">O contrato ao qual se aplica.</span><span class="sxs-lookup"><span data-stu-id="d476d-120">The contract to which it applies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d476d-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d476d-121">Requirements</span></span>  
  
|<span data-ttu-id="d476d-122">MOF</span><span class="sxs-lookup"><span data-stu-id="d476d-122">MOF</span></span>|<span data-ttu-id="d476d-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d476d-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d476d-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="d476d-124">Namespace</span></span>|<span data-ttu-id="d476d-125">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d476d-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d476d-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d476d-126">See Also</span></span>  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>
