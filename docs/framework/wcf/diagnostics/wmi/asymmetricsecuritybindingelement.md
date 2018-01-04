---
title: AsymmetricSecurityBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 82e5365a440d103727f354e682d0ebecb5f46a46
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="asymmetricsecuritybindingelement"></a><span data-ttu-id="28eb3-102">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="28eb3-102">AsymmetricSecurityBindingElement</span></span>
<span data-ttu-id="28eb3-103">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="28eb3-103">AsymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28eb3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="28eb3-104">Syntax</span></span>  
  
```  
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="28eb3-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="28eb3-105">Methods</span></span>  
 <span data-ttu-id="28eb3-106">A classe AsymmetricSecurityBindingElement não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="28eb3-106">The AsymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="28eb3-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="28eb3-107">Properties</span></span>  
 <span data-ttu-id="28eb3-108">A classe AsymmetricSecurityBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="28eb3-108">The AsymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="28eb3-109">messageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="28eb3-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="28eb3-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="28eb3-110">Data type: string</span></span>  
  
 <span data-ttu-id="28eb3-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="28eb3-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="28eb3-112">A ordem de criptografia de mensagem e assinatura para essa associação.</span><span class="sxs-lookup"><span data-stu-id="28eb3-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="28eb3-113">requireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="28eb3-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="28eb3-114">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="28eb3-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="28eb3-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="28eb3-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="28eb3-116">Se a associação requer confirmação de assinatura.</span><span class="sxs-lookup"><span data-stu-id="28eb3-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28eb3-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="28eb3-117">Requirements</span></span>  
  
|<span data-ttu-id="28eb3-118">MOF</span><span class="sxs-lookup"><span data-stu-id="28eb3-118">MOF</span></span>|<span data-ttu-id="28eb3-119">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="28eb3-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="28eb3-120">Namespace</span><span class="sxs-lookup"><span data-stu-id="28eb3-120">Namespace</span></span>|<span data-ttu-id="28eb3-121">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="28eb3-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="28eb3-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="28eb3-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
