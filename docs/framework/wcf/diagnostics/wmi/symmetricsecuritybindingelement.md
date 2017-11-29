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
ms.openlocfilehash: ab341f55947bfcfbc776143e3bbc33e125da89c8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="96c54-102">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="96c54-102">SymmetricSecurityBindingElement</span></span>
<span data-ttu-id="96c54-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="96c54-103">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96c54-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="96c54-104">Syntax</span></span>  
  
```  
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="96c54-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="96c54-105">Methods</span></span>  
 <span data-ttu-id="96c54-106">A classe SymmetricSecurityBindingElement não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="96c54-106">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="96c54-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="96c54-107">Properties</span></span>  
 <span data-ttu-id="96c54-108">A classe SymmetricSecurityBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="96c54-108">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="96c54-109">messageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="96c54-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="96c54-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="96c54-110">Data type: string</span></span>  
  
 <span data-ttu-id="96c54-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="96c54-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="96c54-112">A ordem de criptografia de mensagem e assinatura para essa associação.</span><span class="sxs-lookup"><span data-stu-id="96c54-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="96c54-113">requireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="96c54-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="96c54-114">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="96c54-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="96c54-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="96c54-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="96c54-116">Se a associação requer confirmação de assinatura.</span><span class="sxs-lookup"><span data-stu-id="96c54-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96c54-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="96c54-117">Requirements</span></span>  
  
|<span data-ttu-id="96c54-118">MOF</span><span class="sxs-lookup"><span data-stu-id="96c54-118">MOF</span></span>|<span data-ttu-id="96c54-119">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="96c54-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="96c54-120">Namespace</span><span class="sxs-lookup"><span data-stu-id="96c54-120">Namespace</span></span>|<span data-ttu-id="96c54-121">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="96c54-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="96c54-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96c54-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
