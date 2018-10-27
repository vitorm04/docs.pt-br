---
title: SymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
ms.openlocfilehash: 618899c80d1b22aaabc3c13fe1079137eaf10a93
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50182496"
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="66c63-102">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="66c63-102">SymmetricSecurityBindingElement</span></span>
<span data-ttu-id="66c63-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="66c63-103">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66c63-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="66c63-104">Syntax</span></span>  
  
```csharp
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="66c63-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="66c63-105">Methods</span></span>  
 <span data-ttu-id="66c63-106">A classe SymmetricSecurityBindingElement não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="66c63-106">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="66c63-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="66c63-107">Properties</span></span>  
 <span data-ttu-id="66c63-108">A classe SymmetricSecurityBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="66c63-108">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="66c63-109">messageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="66c63-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="66c63-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="66c63-110">Data type: string</span></span>  
  
 <span data-ttu-id="66c63-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="66c63-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="66c63-112">A ordem de criptografia de mensagens e a assinatura para esta associação.</span><span class="sxs-lookup"><span data-stu-id="66c63-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="66c63-113">requireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="66c63-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="66c63-114">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="66c63-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="66c63-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="66c63-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="66c63-116">Se a associação requer confirmação de assinatura.</span><span class="sxs-lookup"><span data-stu-id="66c63-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66c63-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="66c63-117">Requirements</span></span>  
  
|<span data-ttu-id="66c63-118">MOF</span><span class="sxs-lookup"><span data-stu-id="66c63-118">MOF</span></span>|<span data-ttu-id="66c63-119">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="66c63-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="66c63-120">Namespace</span><span class="sxs-lookup"><span data-stu-id="66c63-120">Namespace</span></span>|<span data-ttu-id="66c63-121">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="66c63-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="66c63-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="66c63-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
