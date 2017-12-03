---
title: elemento &lt;claimTypeRequirements&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a26efe73-4bad-4731-8cad-27f00d54354b
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 187fedc6f81e1cc4a022bfe3b6c68e2c12d09022
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltclaimtyperequirementsgt-element"></a><span data-ttu-id="f1f81-102">elemento &lt;claimTypeRequirements&gt;</span><span class="sxs-lookup"><span data-stu-id="f1f81-102">&lt;claimTypeRequirements&gt; element</span></span>
<span data-ttu-id="f1f81-103">Especifica uma coleção de tipos de declaração necessária.</span><span class="sxs-lookup"><span data-stu-id="f1f81-103">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="f1f81-104">Em um cenário federado, serviços de estado os requisitos de credenciais de entrada.</span><span class="sxs-lookup"><span data-stu-id="f1f81-104">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="f1f81-105">Por exemplo, as credenciais de entrada devem ter um determinado conjunto de tipos de declaração.</span><span class="sxs-lookup"><span data-stu-id="f1f81-105">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="f1f81-106">Cada elemento filho nesta coleção Especifica os tipos de declarações obrigatórias e opcionais que deve aparecer em uma credencial federada.</span><span class="sxs-lookup"><span data-stu-id="f1f81-106">Each child element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>  
  
 <span data-ttu-id="f1f81-107">Um requisito de tipo de declaração consiste o URI do tipo de declaração solicitado no token emitido junto com um parâmetro booliano que indica se essa declaração de tipo é necessária no token emitido ou é opcional.</span><span class="sxs-lookup"><span data-stu-id="f1f81-107">A claim type requirement consists of the URI of the claim type requested in the issued token along with a Boolean parameter that indicates whether that claim type is required in the issued token, or is optional.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1f81-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f1f81-108">See Also</span></span>  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>  
 <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="f1f81-109">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="f1f81-109">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="f1f81-110">Federação e Tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="f1f81-110">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="f1f81-111">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="f1f81-111">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="f1f81-112">Federação e Tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="f1f81-112">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="f1f81-113">\<add></span><span class="sxs-lookup"><span data-stu-id="f1f81-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-claimtyperequirements.md)  
 <span data-ttu-id="f1f81-114">[Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)</span><span class="sxs-lookup"><span data-stu-id="f1f81-114">[Bindings](../../../../../docs/framework/wcf/bindings.md)</span></span>  
 [<span data-ttu-id="f1f81-115">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="f1f81-115">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="f1f81-116">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="f1f81-116">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="f1f81-117">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="f1f81-117">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="f1f81-118">Como: criar uma associação personalizada utilizando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="f1f81-118">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="f1f81-119">Segurança de associação personalizada</span><span class="sxs-lookup"><span data-stu-id="f1f81-119">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
