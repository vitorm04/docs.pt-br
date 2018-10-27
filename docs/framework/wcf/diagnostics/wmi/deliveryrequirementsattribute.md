---
title: DeliveryRequirementsAttribute
ms.date: 03/30/2017
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
ms.openlocfilehash: 7bfc03299fffc8070a7d8a4b3885706ea861bdf6
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/26/2018
ms.locfileid: "50042890"
---
# <a name="deliveryrequirementsattribute"></a><span data-ttu-id="1c182-102">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="1c182-102">DeliveryRequirementsAttribute</span></span>
<span data-ttu-id="1c182-103">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="1c182-103">DeliveryRequirementsAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c182-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1c182-104">Syntax</span></span>  
  
```csharp
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="1c182-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="1c182-105">Methods</span></span>  
 <span data-ttu-id="1c182-106">A classe DeliveryRequirementsAttribute não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="1c182-106">The DeliveryRequirementsAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="1c182-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="1c182-107">Properties</span></span>  
 <span data-ttu-id="1c182-108">A classe DeliveryRequirementsAttribute tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="1c182-108">The DeliveryRequirementsAttribute class has the following properties:</span></span>  
  
### <a name="queueddeliveryrequirements"></a><span data-ttu-id="1c182-109">QueuedDeliveryRequirements</span><span class="sxs-lookup"><span data-stu-id="1c182-109">QueuedDeliveryRequirements</span></span>  
 <span data-ttu-id="1c182-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="1c182-110">Data type: string</span></span>  
  
 <span data-ttu-id="1c182-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="1c182-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1c182-112">Especifica se a associação para um serviço dá suporte a contratos.</span><span class="sxs-lookup"><span data-stu-id="1c182-112">Specifies whether the binding for a service supports contracts.</span></span>  
  
### <a name="requireordereddelivery"></a><span data-ttu-id="1c182-113">RequireOrderedDelivery</span><span class="sxs-lookup"><span data-stu-id="1c182-113">RequireOrderedDelivery</span></span>  
 <span data-ttu-id="1c182-114">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="1c182-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="1c182-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="1c182-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1c182-116">Especifica se a associação dá suporte a mensagens ordenadas.</span><span class="sxs-lookup"><span data-stu-id="1c182-116">Specifies whether the binding supports ordered messages.</span></span>  
  
### <a name="targetcontract"></a><span data-ttu-id="1c182-117">TargetContract</span><span class="sxs-lookup"><span data-stu-id="1c182-117">TargetContract</span></span>  
 <span data-ttu-id="1c182-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="1c182-118">Data type: string</span></span>  
  
 <span data-ttu-id="1c182-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="1c182-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1c182-120">O contrato ao qual se aplica.</span><span class="sxs-lookup"><span data-stu-id="1c182-120">The contract to which it applies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c182-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1c182-121">Requirements</span></span>  
  
|<span data-ttu-id="1c182-122">MOF</span><span class="sxs-lookup"><span data-stu-id="1c182-122">MOF</span></span>|<span data-ttu-id="1c182-123">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="1c182-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="1c182-124">Namespace</span><span class="sxs-lookup"><span data-stu-id="1c182-124">Namespace</span></span>|<span data-ttu-id="1c182-125">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1c182-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1c182-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1c182-126">See Also</span></span>  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>
