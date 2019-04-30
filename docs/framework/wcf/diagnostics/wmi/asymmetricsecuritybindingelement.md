---
title: AsymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
ms.openlocfilehash: 0f86fc1b410753b5ec100f0a7d43de9badd1401b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61964197"
---
# <a name="asymmetricsecuritybindingelement"></a><span data-ttu-id="5f867-102">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="5f867-102">AsymmetricSecurityBindingElement</span></span>
<span data-ttu-id="5f867-103">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="5f867-103">AsymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f867-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5f867-104">Syntax</span></span>  
  
```csharp
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="5f867-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="5f867-105">Methods</span></span>  
 <span data-ttu-id="5f867-106">A classe AsymmetricSecurityBindingElement não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="5f867-106">The AsymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="5f867-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="5f867-107">Properties</span></span>  
 <span data-ttu-id="5f867-108">A classe AsymmetricSecurityBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="5f867-108">The AsymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="5f867-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="5f867-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="5f867-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="5f867-110">Data type: string</span></span>  
  
 <span data-ttu-id="5f867-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="5f867-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5f867-112">A ordem de criptografia de mensagens e a assinatura para esta associação.</span><span class="sxs-lookup"><span data-stu-id="5f867-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="5f867-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="5f867-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="5f867-114">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="5f867-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="5f867-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="5f867-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5f867-116">Se a associação requer confirmação de assinatura.</span><span class="sxs-lookup"><span data-stu-id="5f867-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f867-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5f867-117">Requirements</span></span>  
  
|<span data-ttu-id="5f867-118">MOF</span><span class="sxs-lookup"><span data-stu-id="5f867-118">MOF</span></span>|<span data-ttu-id="5f867-119">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="5f867-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="5f867-120">Namespace</span><span class="sxs-lookup"><span data-stu-id="5f867-120">Namespace</span></span>|<span data-ttu-id="5f867-121">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="5f867-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5f867-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5f867-122">See also</span></span>

- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
