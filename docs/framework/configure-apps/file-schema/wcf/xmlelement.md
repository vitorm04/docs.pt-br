---
title: <xmlElement>
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: cc178dcc3684ab338282acc369e0ab5c789c15e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941431"
---
# <a name="xmlelement"></a><span data-ttu-id="a50fc-101">\<> xmlElement</span><span class="sxs-lookup"><span data-stu-id="a50fc-101">\<xmlElement></span></span>
<span data-ttu-id="a50fc-102">Especifica um elemento XML que é enviado no corpo da mensagem para o serviço de token de segurança ao solicitar um token.</span><span class="sxs-lookup"><span data-stu-id="a50fc-102">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
 <span data-ttu-id="a50fc-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a50fc-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="a50fc-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="a50fc-104">\<bindings></span></span>  
<span data-ttu-id="a50fc-105">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="a50fc-105">\<wsFederatedBinding></span></span>  
<span data-ttu-id="a50fc-106">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="a50fc-106">\<binding></span></span>  
<span data-ttu-id="a50fc-107">\<> de segurança</span><span class="sxs-lookup"><span data-stu-id="a50fc-107">\<security></span></span>  
<span data-ttu-id="a50fc-108">\<message></span><span class="sxs-lookup"><span data-stu-id="a50fc-108">\<message></span></span>  
<span data-ttu-id="a50fc-109">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="a50fc-109">\<tokenRequestParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a50fc-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a50fc-110">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>
  <xmlElement xmlElement="String" />
</tokenRequestParameters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a50fc-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a50fc-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a50fc-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a50fc-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a50fc-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="a50fc-113">Attributes</span></span>  
  
|<span data-ttu-id="a50fc-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="a50fc-114">Attribute</span></span>|<span data-ttu-id="a50fc-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="a50fc-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a50fc-116">xmlElement</span><span class="sxs-lookup"><span data-stu-id="a50fc-116">xmlElement</span></span>|<span data-ttu-id="a50fc-117">Uma cadeia de caracteres que especifica um elemento XML que é enviado no corpo da mensagem para o serviço de token de segurança ao solicitar um token.</span><span class="sxs-lookup"><span data-stu-id="a50fc-117">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a50fc-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a50fc-118">Child Elements</span></span>  
 <span data-ttu-id="a50fc-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="a50fc-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a50fc-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a50fc-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a50fc-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="a50fc-121">Element</span></span>|<span data-ttu-id="a50fc-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="a50fc-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a50fc-123">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="a50fc-123">\<tokenRequestParameters></span></span>](tokenrequestparameters.md)|<span data-ttu-id="a50fc-124">Uma coleção de parâmetros de solicitação de token.</span><span class="sxs-lookup"><span data-stu-id="a50fc-124">A collection of token request parameters.</span></span> <span data-ttu-id="a50fc-125">Cada parâmetro é um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="a50fc-125">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a50fc-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a50fc-126">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>
- [<span data-ttu-id="a50fc-127">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="a50fc-127">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="a50fc-128">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="a50fc-128">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="a50fc-129">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="a50fc-129">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="a50fc-130">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="a50fc-130">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="a50fc-131">Associações</span><span class="sxs-lookup"><span data-stu-id="a50fc-131">Bindings</span></span>](../../../wcf/bindings.md)
