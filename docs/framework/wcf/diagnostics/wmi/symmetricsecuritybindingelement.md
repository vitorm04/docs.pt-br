---
title: SymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
author: BrucePerlerMS
ms.openlocfilehash: e633ae19cd17930fb140a93ffd0910c7ed8efea4
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2018
ms.locfileid: "49374390"
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="c7268-102">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="c7268-102">SymmetricSecurityBindingElement</span></span>
<span data-ttu-id="c7268-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="c7268-103">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7268-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c7268-104">Syntax</span></span>  
  
```csharp
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c7268-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="c7268-105">Methods</span></span>  
 <span data-ttu-id="c7268-106">A classe SymmetricSecurityBindingElement não define quaisquer métodos.</span><span class="sxs-lookup"><span data-stu-id="c7268-106">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c7268-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="c7268-107">Properties</span></span>  
 <span data-ttu-id="c7268-108">A classe SymmetricSecurityBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="c7268-108">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="c7268-109">messageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="c7268-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="c7268-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="c7268-110">Data type: string</span></span>  
  
 <span data-ttu-id="c7268-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="c7268-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c7268-112">A ordem de criptografia de mensagens e a assinatura para esta associação.</span><span class="sxs-lookup"><span data-stu-id="c7268-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="c7268-113">requireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="c7268-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="c7268-114">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="c7268-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="c7268-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="c7268-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c7268-116">Se a associação requer confirmação de assinatura.</span><span class="sxs-lookup"><span data-stu-id="c7268-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7268-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c7268-117">Requirements</span></span>  
  
|<span data-ttu-id="c7268-118">MOF</span><span class="sxs-lookup"><span data-stu-id="c7268-118">MOF</span></span>|<span data-ttu-id="c7268-119">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="c7268-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c7268-120">Namespace</span><span class="sxs-lookup"><span data-stu-id="c7268-120">Namespace</span></span>|<span data-ttu-id="c7268-121">Definido no root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c7268-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c7268-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7268-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
