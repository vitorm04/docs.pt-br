---
title: SymmetricSecurityBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 7960ae9972490f2363b0f6f9942e947677c7d299
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="b7a5d-102">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="b7a5d-102">SymmetricSecurityBindingElement</span></span>
<span data-ttu-id="b7a5d-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="b7a5d-103">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7a5d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7a5d-104">Syntax</span></span>  
  
```  
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b7a5d-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="b7a5d-105">Methods</span></span>  
 <span data-ttu-id="b7a5d-106">A classe SymmetricSecurityBindingElement não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="b7a5d-106">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b7a5d-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="b7a5d-107">Properties</span></span>  
 <span data-ttu-id="b7a5d-108">A classe SymmetricSecurityBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="b7a5d-108">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="b7a5d-109">messageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="b7a5d-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="b7a5d-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="b7a5d-110">Data type: string</span></span>  
  
 <span data-ttu-id="b7a5d-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b7a5d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b7a5d-112">A ordem de criptografia de mensagem e assinatura para essa associação.</span><span class="sxs-lookup"><span data-stu-id="b7a5d-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="b7a5d-113">requireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="b7a5d-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="b7a5d-114">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="b7a5d-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="b7a5d-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="b7a5d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b7a5d-116">Se a associação requer confirmação de assinatura.</span><span class="sxs-lookup"><span data-stu-id="b7a5d-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7a5d-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b7a5d-117">Requirements</span></span>  
  
|<span data-ttu-id="b7a5d-118">MOF</span><span class="sxs-lookup"><span data-stu-id="b7a5d-118">MOF</span></span>|<span data-ttu-id="b7a5d-119">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b7a5d-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b7a5d-120">Namespace</span><span class="sxs-lookup"><span data-stu-id="b7a5d-120">Namespace</span></span>|<span data-ttu-id="b7a5d-121">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b7a5d-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b7a5d-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7a5d-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
