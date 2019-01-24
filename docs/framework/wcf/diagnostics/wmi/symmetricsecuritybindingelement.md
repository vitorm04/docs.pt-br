---
title: SymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
ms.openlocfilehash: 7b979a6872da15c4130e580a3f7327802f42db18
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54701385"
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="213b7-102">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="213b7-102">SymmetricSecurityBindingElement</span></span>
<span data-ttu-id="213b7-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="213b7-103">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="213b7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="213b7-104">Syntax</span></span>  
  
```csharp
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="213b7-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="213b7-105">Methods</span></span>  
 <span data-ttu-id="213b7-106">A classe SymmetricSecurityBindingElement não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="213b7-106">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="213b7-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="213b7-107">Properties</span></span>  
 <span data-ttu-id="213b7-108">A classe SymmetricSecurityBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="213b7-108">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="213b7-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="213b7-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="213b7-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="213b7-110">Data type: string</span></span>  
  
 <span data-ttu-id="213b7-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="213b7-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="213b7-112">A ordem de criptografia de mensagens e a assinatura para esta associação.</span><span class="sxs-lookup"><span data-stu-id="213b7-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="213b7-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="213b7-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="213b7-114">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="213b7-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="213b7-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="213b7-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="213b7-116">Se a associação requer confirmação de assinatura.</span><span class="sxs-lookup"><span data-stu-id="213b7-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="213b7-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="213b7-117">Requirements</span></span>  
  
|<span data-ttu-id="213b7-118">MOF</span><span class="sxs-lookup"><span data-stu-id="213b7-118">MOF</span></span>|<span data-ttu-id="213b7-119">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="213b7-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="213b7-120">Namespace</span><span class="sxs-lookup"><span data-stu-id="213b7-120">Namespace</span></span>|<span data-ttu-id="213b7-121">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="213b7-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="213b7-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="213b7-122">See also</span></span>
- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
