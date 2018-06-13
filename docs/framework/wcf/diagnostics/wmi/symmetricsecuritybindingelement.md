---
title: SymmetricSecurityBindingElement
ms.date: 03/30/2017
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 7fc720f4f0be25a0cec25d979942af8472efa4ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485050"
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="47e6a-102">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="47e6a-102">SymmetricSecurityBindingElement</span></span>
<span data-ttu-id="47e6a-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="47e6a-103">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47e6a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="47e6a-104">Syntax</span></span>  
  
```  
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="47e6a-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="47e6a-105">Methods</span></span>  
 <span data-ttu-id="47e6a-106">A classe SymmetricSecurityBindingElement não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="47e6a-106">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="47e6a-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="47e6a-107">Properties</span></span>  
 <span data-ttu-id="47e6a-108">A classe SymmetricSecurityBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="47e6a-108">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="47e6a-109">messageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="47e6a-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="47e6a-110">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="47e6a-110">Data type: string</span></span>  
  
 <span data-ttu-id="47e6a-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="47e6a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="47e6a-112">A ordem de criptografia de mensagem e assinatura para essa associação.</span><span class="sxs-lookup"><span data-stu-id="47e6a-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="47e6a-113">requireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="47e6a-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="47e6a-114">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="47e6a-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="47e6a-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="47e6a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="47e6a-116">Se a associação requer confirmação de assinatura.</span><span class="sxs-lookup"><span data-stu-id="47e6a-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47e6a-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="47e6a-117">Requirements</span></span>  
  
|<span data-ttu-id="47e6a-118">MOF</span><span class="sxs-lookup"><span data-stu-id="47e6a-118">MOF</span></span>|<span data-ttu-id="47e6a-119">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="47e6a-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="47e6a-120">Namespace</span><span class="sxs-lookup"><span data-stu-id="47e6a-120">Namespace</span></span>|<span data-ttu-id="47e6a-121">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="47e6a-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="47e6a-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="47e6a-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
