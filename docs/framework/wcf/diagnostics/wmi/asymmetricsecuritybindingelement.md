---
title: AsymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 09bfaa3ab4f2aceb3e80644953a87686fca9830c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="asymmetricsecuritybindingelement"></a><span data-ttu-id="77f07-102">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="77f07-102">AsymmetricSecurityBindingElement</span></span>
<span data-ttu-id="77f07-103">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="77f07-103">AsymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77f07-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="77f07-104">Syntax</span></span>  
  
```  
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="77f07-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="77f07-105">Methods</span></span>  
 <span data-ttu-id="77f07-106">A classe AsymmetricSecurityBindingElement não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="77f07-106">The AsymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="77f07-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="77f07-107">Properties</span></span>  
 <span data-ttu-id="77f07-108">A classe AsymmetricSecurityBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="77f07-108">The AsymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="77f07-109">messageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="77f07-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="77f07-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="77f07-110">Data type: string</span></span>  
  
 <span data-ttu-id="77f07-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="77f07-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="77f07-112">A ordem de criptografia de mensagem e assinatura para essa associação.</span><span class="sxs-lookup"><span data-stu-id="77f07-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="77f07-113">requireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="77f07-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="77f07-114">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="77f07-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="77f07-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="77f07-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="77f07-116">Se a associação requer confirmação de assinatura.</span><span class="sxs-lookup"><span data-stu-id="77f07-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77f07-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="77f07-117">Requirements</span></span>  
  
|<span data-ttu-id="77f07-118">MOF</span><span class="sxs-lookup"><span data-stu-id="77f07-118">MOF</span></span>|<span data-ttu-id="77f07-119">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="77f07-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="77f07-120">Namespace</span><span class="sxs-lookup"><span data-stu-id="77f07-120">Namespace</span></span>|<span data-ttu-id="77f07-121">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="77f07-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="77f07-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77f07-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
