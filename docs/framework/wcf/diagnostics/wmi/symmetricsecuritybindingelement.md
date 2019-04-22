---
title: SymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
ms.openlocfilehash: f6effd533a205d0e8fd1421119e325f06b340dd1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59770406"
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="112b5-102">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="112b5-102">SymmetricSecurityBindingElement</span></span>
<span data-ttu-id="112b5-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="112b5-103">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="112b5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="112b5-104">Syntax</span></span>  
  
```csharp
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="112b5-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="112b5-105">Methods</span></span>  
 <span data-ttu-id="112b5-106">A classe SymmetricSecurityBindingElement não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="112b5-106">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="112b5-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="112b5-107">Properties</span></span>  
 <span data-ttu-id="112b5-108">A classe SymmetricSecurityBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="112b5-108">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="112b5-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="112b5-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="112b5-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="112b5-110">Data type: string</span></span>  
  
 <span data-ttu-id="112b5-111">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="112b5-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="112b5-112">A ordem de criptografia de mensagens e a assinatura para esta associação.</span><span class="sxs-lookup"><span data-stu-id="112b5-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="112b5-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="112b5-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="112b5-114">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="112b5-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="112b5-115">Tipo de acesso: Somente leitura</span><span class="sxs-lookup"><span data-stu-id="112b5-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="112b5-116">Se a associação requer confirmação de assinatura.</span><span class="sxs-lookup"><span data-stu-id="112b5-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="112b5-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="112b5-117">Requirements</span></span>  
  
|<span data-ttu-id="112b5-118">MOF</span><span class="sxs-lookup"><span data-stu-id="112b5-118">MOF</span></span>|<span data-ttu-id="112b5-119">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="112b5-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="112b5-120">Namespace</span><span class="sxs-lookup"><span data-stu-id="112b5-120">Namespace</span></span>|<span data-ttu-id="112b5-121">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="112b5-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="112b5-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="112b5-122">See also</span></span>

- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
