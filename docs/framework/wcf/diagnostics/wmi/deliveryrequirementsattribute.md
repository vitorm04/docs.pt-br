---
title: DeliveryRequirementsAttribute
ms.date: 03/30/2017
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
ms.openlocfilehash: c81e4b27969d879a70806082f48879cbf1b32ccc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979206"
---
# <a name="deliveryrequirementsattribute"></a><span data-ttu-id="ee754-102">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="ee754-102">DeliveryRequirementsAttribute</span></span>
<span data-ttu-id="ee754-103">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="ee754-103">DeliveryRequirementsAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee754-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ee754-104">Syntax</span></span>  
  
```csharp
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ee754-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="ee754-105">Methods</span></span>  
 <span data-ttu-id="ee754-106">A classe DeliveryRequirementsAttribute não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="ee754-106">The DeliveryRequirementsAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ee754-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="ee754-107">Properties</span></span>  
 <span data-ttu-id="ee754-108">A classe DeliveryRequirementsAttribute tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="ee754-108">The DeliveryRequirementsAttribute class has the following properties:</span></span>  
  
### <a name="queueddeliveryrequirements"></a><span data-ttu-id="ee754-109">QueuedDeliveryRequirements</span><span class="sxs-lookup"><span data-stu-id="ee754-109">QueuedDeliveryRequirements</span></span>  
 <span data-ttu-id="ee754-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="ee754-110">Data type: string</span></span>  
  
 <span data-ttu-id="ee754-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="ee754-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ee754-112">Especifica se a associação para um serviço dá suporte a contratos.</span><span class="sxs-lookup"><span data-stu-id="ee754-112">Specifies whether the binding for a service supports contracts.</span></span>  
  
### <a name="requireordereddelivery"></a><span data-ttu-id="ee754-113">RequireOrderedDelivery</span><span class="sxs-lookup"><span data-stu-id="ee754-113">RequireOrderedDelivery</span></span>  
 <span data-ttu-id="ee754-114">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="ee754-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="ee754-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="ee754-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ee754-116">Especifica se a associação dá suporte a mensagens ordenadas.</span><span class="sxs-lookup"><span data-stu-id="ee754-116">Specifies whether the binding supports ordered messages.</span></span>  
  
### <a name="targetcontract"></a><span data-ttu-id="ee754-117">TargetContract</span><span class="sxs-lookup"><span data-stu-id="ee754-117">TargetContract</span></span>  
 <span data-ttu-id="ee754-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="ee754-118">Data type: string</span></span>  
  
 <span data-ttu-id="ee754-119">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="ee754-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ee754-120">O contrato ao qual se aplica.</span><span class="sxs-lookup"><span data-stu-id="ee754-120">The contract to which it applies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee754-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ee754-121">Requirements</span></span>  
  
|<span data-ttu-id="ee754-122">MOF</span><span class="sxs-lookup"><span data-stu-id="ee754-122">MOF</span></span>|<span data-ttu-id="ee754-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="ee754-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ee754-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="ee754-124">Namespace</span></span>|<span data-ttu-id="ee754-125">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ee754-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ee754-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ee754-126">See also</span></span>

- <xref:System.ServiceModel.DeliveryRequirementsAttribute>
