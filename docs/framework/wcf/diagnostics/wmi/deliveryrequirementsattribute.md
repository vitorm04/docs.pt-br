---
title: DeliveryRequirementsAttribute
ms.date: 03/30/2017
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
ms.openlocfilehash: 7bfc03299fffc8070a7d8a4b3885706ea861bdf6
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50198504"
---
# <a name="deliveryrequirementsattribute"></a><span data-ttu-id="6f0b5-102">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="6f0b5-102">DeliveryRequirementsAttribute</span></span>
<span data-ttu-id="6f0b5-103">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="6f0b5-103">DeliveryRequirementsAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f0b5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6f0b5-104">Syntax</span></span>  
  
```csharp
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="6f0b5-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="6f0b5-105">Methods</span></span>  
 <span data-ttu-id="6f0b5-106">A classe DeliveryRequirementsAttribute não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="6f0b5-106">The DeliveryRequirementsAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="6f0b5-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="6f0b5-107">Properties</span></span>  
 <span data-ttu-id="6f0b5-108">A classe DeliveryRequirementsAttribute tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="6f0b5-108">The DeliveryRequirementsAttribute class has the following properties:</span></span>  
  
### <a name="queueddeliveryrequirements"></a><span data-ttu-id="6f0b5-109">QueuedDeliveryRequirements</span><span class="sxs-lookup"><span data-stu-id="6f0b5-109">QueuedDeliveryRequirements</span></span>  
 <span data-ttu-id="6f0b5-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="6f0b5-110">Data type: string</span></span>  
  
 <span data-ttu-id="6f0b5-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="6f0b5-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6f0b5-112">Especifica se a associação para um serviço dá suporte a contratos.</span><span class="sxs-lookup"><span data-stu-id="6f0b5-112">Specifies whether the binding for a service supports contracts.</span></span>  
  
### <a name="requireordereddelivery"></a><span data-ttu-id="6f0b5-113">RequireOrderedDelivery</span><span class="sxs-lookup"><span data-stu-id="6f0b5-113">RequireOrderedDelivery</span></span>  
 <span data-ttu-id="6f0b5-114">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="6f0b5-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="6f0b5-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="6f0b5-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6f0b5-116">Especifica se a associação dá suporte a mensagens ordenadas.</span><span class="sxs-lookup"><span data-stu-id="6f0b5-116">Specifies whether the binding supports ordered messages.</span></span>  
  
### <a name="targetcontract"></a><span data-ttu-id="6f0b5-117">TargetContract</span><span class="sxs-lookup"><span data-stu-id="6f0b5-117">TargetContract</span></span>  
 <span data-ttu-id="6f0b5-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="6f0b5-118">Data type: string</span></span>  
  
 <span data-ttu-id="6f0b5-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="6f0b5-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6f0b5-120">O contrato ao qual se aplica.</span><span class="sxs-lookup"><span data-stu-id="6f0b5-120">The contract to which it applies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f0b5-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6f0b5-121">Requirements</span></span>  
  
|<span data-ttu-id="6f0b5-122">MOF</span><span class="sxs-lookup"><span data-stu-id="6f0b5-122">MOF</span></span>|<span data-ttu-id="6f0b5-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="6f0b5-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="6f0b5-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="6f0b5-124">Namespace</span></span>|<span data-ttu-id="6f0b5-125">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="6f0b5-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6f0b5-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6f0b5-126">See Also</span></span>  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>
