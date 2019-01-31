---
title: Elemento <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: a26efe73-4bad-4731-8cad-27f00d54354b
ms.openlocfilehash: 95cc1adf7ab37475e8d3eeb01750531a7f8ab249
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55279624"
---
# <a name="claimtyperequirements-element"></a><span data-ttu-id="59fa9-102">\<claimTypeRequirements > elemento</span><span class="sxs-lookup"><span data-stu-id="59fa9-102">\<claimTypeRequirements> element</span></span>
<span data-ttu-id="59fa9-103">Especifica uma coleção de tipos de declaração exigidos.</span><span class="sxs-lookup"><span data-stu-id="59fa9-103">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="59fa9-104">Em um cenário federado, os serviços de estado os requisitos de credenciais de entrada.</span><span class="sxs-lookup"><span data-stu-id="59fa9-104">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="59fa9-105">Por exemplo, as credenciais de entrada devem ter um determinado conjunto de tipos de declaração.</span><span class="sxs-lookup"><span data-stu-id="59fa9-105">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="59fa9-106">Cada elemento filho nesta coleção Especifica os tipos de declarações obrigatórias e opcionais esperados para aparecer em uma credencial federada.</span><span class="sxs-lookup"><span data-stu-id="59fa9-106">Each child element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>  
  
 <span data-ttu-id="59fa9-107">Um requisito de tipo de declaração consiste o URI do tipo de declaração solicitado no token emitido junto com um parâmetro booliano que indica se essa declaração de tipo é necessária no token emitido, ou é opcional.</span><span class="sxs-lookup"><span data-stu-id="59fa9-107">A claim type requirement consists of the URI of the claim type requested in the issued token along with a Boolean parameter that indicates whether that claim type is required in the issued token, or is optional.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59fa9-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="59fa9-108">See also</span></span>
- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="59fa9-109">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="59fa9-109">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="59fa9-110">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="59fa9-110">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="59fa9-111">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="59fa9-111">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="59fa9-112">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="59fa9-112">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="59fa9-113">\<add></span><span class="sxs-lookup"><span data-stu-id="59fa9-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-claimtyperequirements.md)
- [<span data-ttu-id="59fa9-114">Associações</span><span class="sxs-lookup"><span data-stu-id="59fa9-114">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="59fa9-115">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="59fa9-115">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="59fa9-116">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="59fa9-116">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="59fa9-117">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="59fa9-117">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="59fa9-118">Como: Criar uma associação personalizada utilizando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="59fa9-118">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="59fa9-119">Segurança de associação personalizada</span><span class="sxs-lookup"><span data-stu-id="59fa9-119">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
