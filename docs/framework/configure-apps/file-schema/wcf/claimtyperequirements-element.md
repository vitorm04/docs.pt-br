---
title: Elemento <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: a26efe73-4bad-4731-8cad-27f00d54354b
ms.openlocfilehash: b4d8479dd9a24774afbd0549caf9e261f55fa147
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926151"
---
# <a name="claimtyperequirements-element"></a><span data-ttu-id="7d3e7-102">\<elemento de > claimTypeRequirements</span><span class="sxs-lookup"><span data-stu-id="7d3e7-102">\<claimTypeRequirements> element</span></span>
<span data-ttu-id="7d3e7-103">Especifica uma coleção de tipos de declaração necessários.</span><span class="sxs-lookup"><span data-stu-id="7d3e7-103">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="7d3e7-104">Em um cenário federado, os serviços atendem aos requisitos de credenciais de entrada.</span><span class="sxs-lookup"><span data-stu-id="7d3e7-104">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="7d3e7-105">Por exemplo, as credenciais de entrada devem ter um determinado conjunto de tipos de declaração.</span><span class="sxs-lookup"><span data-stu-id="7d3e7-105">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="7d3e7-106">Cada elemento filho nessa coleção especifica os tipos de declarações obrigatórias e opcionais que devem aparecer em uma credencial federada.</span><span class="sxs-lookup"><span data-stu-id="7d3e7-106">Each child element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>  
  
 <span data-ttu-id="7d3e7-107">Um requisito de tipo de declaração consiste no URI do tipo de declaração solicitado no token emitido junto com um parâmetro booliano que indica se esse tipo de declaração é necessário no token emitido ou é opcional.</span><span class="sxs-lookup"><span data-stu-id="7d3e7-107">A claim type requirement consists of the URI of the claim type requested in the issued token along with a Boolean parameter that indicates whether that claim type is required in the issued token, or is optional.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d3e7-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7d3e7-108">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="7d3e7-109">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="7d3e7-109">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="7d3e7-110">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="7d3e7-110">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="7d3e7-111">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="7d3e7-111">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="7d3e7-112">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="7d3e7-112">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="7d3e7-113">\<add></span><span class="sxs-lookup"><span data-stu-id="7d3e7-113">\<add></span></span>](add-of-claimtyperequirements.md)
- [<span data-ttu-id="7d3e7-114">Associações</span><span class="sxs-lookup"><span data-stu-id="7d3e7-114">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7d3e7-115">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="7d3e7-115">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="7d3e7-116">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="7d3e7-116">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="7d3e7-117">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="7d3e7-117">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="7d3e7-118">Como: Criar uma associação personalizada usando o SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="7d3e7-118">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="7d3e7-119">Segurança de associação personalizada</span><span class="sxs-lookup"><span data-stu-id="7d3e7-119">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
