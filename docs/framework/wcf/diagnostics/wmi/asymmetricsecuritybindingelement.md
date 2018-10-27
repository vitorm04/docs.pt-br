---
title: AsymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
ms.openlocfilehash: 076313548828f1fbce9c68b48c0fa7db9cca095f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185112"
---
# <a name="asymmetricsecuritybindingelement"></a><span data-ttu-id="75664-102">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="75664-102">AsymmetricSecurityBindingElement</span></span>
<span data-ttu-id="75664-103">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="75664-103">AsymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75664-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="75664-104">Syntax</span></span>  
  
```csharp
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="75664-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="75664-105">Methods</span></span>  
 <span data-ttu-id="75664-106">A classe AsymmetricSecurityBindingElement não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="75664-106">The AsymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="75664-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="75664-107">Properties</span></span>  
 <span data-ttu-id="75664-108">A classe AsymmetricSecurityBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="75664-108">The AsymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="75664-109">messageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="75664-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="75664-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="75664-110">Data type: string</span></span>  
  
 <span data-ttu-id="75664-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="75664-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="75664-112">A ordem de criptografia de mensagens e a assinatura para esta associação.</span><span class="sxs-lookup"><span data-stu-id="75664-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="75664-113">requireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="75664-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="75664-114">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="75664-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="75664-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="75664-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="75664-116">Se a associação requer confirmação de assinatura.</span><span class="sxs-lookup"><span data-stu-id="75664-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75664-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="75664-117">Requirements</span></span>  
  
|<span data-ttu-id="75664-118">MOF</span><span class="sxs-lookup"><span data-stu-id="75664-118">MOF</span></span>|<span data-ttu-id="75664-119">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="75664-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="75664-120">Namespace</span><span class="sxs-lookup"><span data-stu-id="75664-120">Namespace</span></span>|<span data-ttu-id="75664-121">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="75664-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="75664-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="75664-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
