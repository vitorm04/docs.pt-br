---
title: AsymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
ms.openlocfilehash: e968f5f2d7ffdb193b30762d32a47be3778b98dc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54621351"
---
# <a name="asymmetricsecuritybindingelement"></a><span data-ttu-id="de0e6-102">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="de0e6-102">AsymmetricSecurityBindingElement</span></span>
<span data-ttu-id="de0e6-103">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="de0e6-103">AsymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de0e6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="de0e6-104">Syntax</span></span>  
  
```csharp
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="de0e6-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="de0e6-105">Methods</span></span>  
 <span data-ttu-id="de0e6-106">A classe AsymmetricSecurityBindingElement não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="de0e6-106">The AsymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="de0e6-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="de0e6-107">Properties</span></span>  
 <span data-ttu-id="de0e6-108">A classe AsymmetricSecurityBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="de0e6-108">The AsymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="de0e6-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="de0e6-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="de0e6-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="de0e6-110">Data type: string</span></span>  
  
 <span data-ttu-id="de0e6-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="de0e6-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="de0e6-112">A ordem de criptografia de mensagens e a assinatura para esta associação.</span><span class="sxs-lookup"><span data-stu-id="de0e6-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="de0e6-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="de0e6-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="de0e6-114">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="de0e6-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="de0e6-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="de0e6-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="de0e6-116">Se a associação requer confirmação de assinatura.</span><span class="sxs-lookup"><span data-stu-id="de0e6-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de0e6-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="de0e6-117">Requirements</span></span>  
  
|<span data-ttu-id="de0e6-118">MOF</span><span class="sxs-lookup"><span data-stu-id="de0e6-118">MOF</span></span>|<span data-ttu-id="de0e6-119">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="de0e6-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="de0e6-120">Namespace</span><span class="sxs-lookup"><span data-stu-id="de0e6-120">Namespace</span></span>|<span data-ttu-id="de0e6-121">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="de0e6-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="de0e6-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="de0e6-122">See also</span></span>
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
