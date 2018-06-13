---
title: DeliveryRequirementsAttribute
ms.date: 03/30/2017
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
ms.openlocfilehash: d294ba4f14472012b9e311ee53742633b5173f54
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485747"
---
# <a name="deliveryrequirementsattribute"></a><span data-ttu-id="c3ad9-102">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="c3ad9-102">DeliveryRequirementsAttribute</span></span>
<span data-ttu-id="c3ad9-103">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="c3ad9-103">DeliveryRequirementsAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3ad9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c3ad9-104">Syntax</span></span>  
  
```  
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c3ad9-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="c3ad9-105">Methods</span></span>  
 <span data-ttu-id="c3ad9-106">A classe DeliveryRequirementsAttribute não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="c3ad9-106">The DeliveryRequirementsAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c3ad9-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="c3ad9-107">Properties</span></span>  
 <span data-ttu-id="c3ad9-108">A classe DeliveryRequirementsAttribute tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="c3ad9-108">The DeliveryRequirementsAttribute class has the following properties:</span></span>  
  
### <a name="queueddeliveryrequirements"></a><span data-ttu-id="c3ad9-109">QueuedDeliveryRequirements</span><span class="sxs-lookup"><span data-stu-id="c3ad9-109">QueuedDeliveryRequirements</span></span>  
 <span data-ttu-id="c3ad9-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c3ad9-110">Data type: string</span></span>  
  
 <span data-ttu-id="c3ad9-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="c3ad9-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c3ad9-112">Especifica se a associação para um serviço oferece suporte a contratos.</span><span class="sxs-lookup"><span data-stu-id="c3ad9-112">Specifies whether the binding for a service supports contracts.</span></span>  
  
### <a name="requireordereddelivery"></a><span data-ttu-id="c3ad9-113">RequireOrderedDelivery</span><span class="sxs-lookup"><span data-stu-id="c3ad9-113">RequireOrderedDelivery</span></span>  
 <span data-ttu-id="c3ad9-114">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="c3ad9-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="c3ad9-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="c3ad9-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c3ad9-116">Especifica se a associação oferece suporte a mensagens ordenadas.</span><span class="sxs-lookup"><span data-stu-id="c3ad9-116">Specifies whether the binding supports ordered messages.</span></span>  
  
### <a name="targetcontract"></a><span data-ttu-id="c3ad9-117">TargetContract</span><span class="sxs-lookup"><span data-stu-id="c3ad9-117">TargetContract</span></span>  
 <span data-ttu-id="c3ad9-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c3ad9-118">Data type: string</span></span>  
  
 <span data-ttu-id="c3ad9-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="c3ad9-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c3ad9-120">O contrato ao qual se aplica.</span><span class="sxs-lookup"><span data-stu-id="c3ad9-120">The contract to which it applies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3ad9-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c3ad9-121">Requirements</span></span>  
  
|<span data-ttu-id="c3ad9-122">MOF</span><span class="sxs-lookup"><span data-stu-id="c3ad9-122">MOF</span></span>|<span data-ttu-id="c3ad9-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="c3ad9-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c3ad9-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="c3ad9-124">Namespace</span></span>|<span data-ttu-id="c3ad9-125">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c3ad9-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c3ad9-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3ad9-126">See Also</span></span>  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>
