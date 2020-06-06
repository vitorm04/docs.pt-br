---
title: Elemento <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: a26efe73-4bad-4731-8cad-27f00d54354b
ms.openlocfilehash: b4d8479dd9a24774afbd0549caf9e261f55fa147
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "69926151"
---
# <a name="claimtyperequirements-element"></a><span data-ttu-id="64815-102">Elemento \<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="64815-102">\<claimTypeRequirements> element</span></span>
<span data-ttu-id="64815-103">Especifica uma coleção de tipos de declaração necessários.</span><span class="sxs-lookup"><span data-stu-id="64815-103">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="64815-104">Em um cenário federado, os serviços atendem aos requisitos de credenciais de entrada.</span><span class="sxs-lookup"><span data-stu-id="64815-104">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="64815-105">Por exemplo, as credenciais de entrada devem ter um determinado conjunto de tipos de declaração.</span><span class="sxs-lookup"><span data-stu-id="64815-105">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="64815-106">Cada elemento filho nessa coleção especifica os tipos de declarações obrigatórias e opcionais que devem aparecer em uma credencial federada.</span><span class="sxs-lookup"><span data-stu-id="64815-106">Each child element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>  
  
 <span data-ttu-id="64815-107">Um requisito de tipo de declaração consiste no URI do tipo de declaração solicitado no token emitido junto com um parâmetro booliano que indica se esse tipo de declaração é necessário no token emitido ou é opcional.</span><span class="sxs-lookup"><span data-stu-id="64815-107">A claim type requirement consists of the URI of the claim type requested in the issued token along with a Boolean parameter that indicates whether that claim type is required in the issued token, or is optional.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64815-108">Confira também</span><span class="sxs-lookup"><span data-stu-id="64815-108">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="64815-109">Identidade e autenticação de serviço</span><span class="sxs-lookup"><span data-stu-id="64815-109">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="64815-110">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="64815-110">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="64815-111">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="64815-111">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="64815-112">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="64815-112">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [\<add>](add-of-claimtyperequirements.md)
- [<span data-ttu-id="64815-113">Associações</span><span class="sxs-lookup"><span data-stu-id="64815-113">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="64815-114">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="64815-114">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="64815-115">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="64815-115">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="64815-116">Como criar uma associação personalizada utilizando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="64815-116">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="64815-117">Segurança de associação personalizada</span><span class="sxs-lookup"><span data-stu-id="64815-117">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
