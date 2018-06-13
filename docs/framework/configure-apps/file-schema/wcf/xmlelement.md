---
title: '&lt;XmlElement&gt;'
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: 70ff9b93bcd59331c5fa5e66bb51dc4cd1e043ff
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32767642"
---
# <a name="ltxmlelementgt"></a><span data-ttu-id="6742e-102">&lt;XmlElement&gt;</span><span class="sxs-lookup"><span data-stu-id="6742e-102">&lt;xmlElement&gt;</span></span>
<span data-ttu-id="6742e-103">Especifica um elemento XML que é enviado no corpo da mensagem para o serviço de Token de segurança ao solicitar um token.</span><span class="sxs-lookup"><span data-stu-id="6742e-103">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
 <span data-ttu-id="6742e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6742e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6742e-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="6742e-105">\<bindings></span></span>  
<span data-ttu-id="6742e-106">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="6742e-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="6742e-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="6742e-107">\<binding></span></span>  
<span data-ttu-id="6742e-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="6742e-108">\<security></span></span>  
<span data-ttu-id="6742e-109">\<message></span><span class="sxs-lookup"><span data-stu-id="6742e-109">\<message></span></span>  
<span data-ttu-id="6742e-110">\<tokenRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="6742e-110">\<tokenRequestParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6742e-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6742e-111">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>  
      <xmlElement xmlElement="String" />  
</tokenRequestParameters>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6742e-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6742e-112">Attributes and Elements</span></span>  
 <span data-ttu-id="6742e-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6742e-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6742e-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="6742e-114">Attributes</span></span>  
  
|<span data-ttu-id="6742e-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="6742e-115">Attribute</span></span>|<span data-ttu-id="6742e-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="6742e-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6742e-117">xmlElement</span><span class="sxs-lookup"><span data-stu-id="6742e-117">xmlElement</span></span>|<span data-ttu-id="6742e-118">Uma cadeia de caracteres especificando um elemento XML que é enviado no corpo da mensagem para o serviço de Token de segurança ao solicitar um token.</span><span class="sxs-lookup"><span data-stu-id="6742e-118">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6742e-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6742e-119">Child Elements</span></span>  
 <span data-ttu-id="6742e-120">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="6742e-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6742e-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6742e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="6742e-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="6742e-122">Element</span></span>|<span data-ttu-id="6742e-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="6742e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6742e-124">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="6742e-124">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="6742e-125">Uma coleção de parâmetros de solicitação de token.</span><span class="sxs-lookup"><span data-stu-id="6742e-125">A collection of token request parameters.</span></span> <span data-ttu-id="6742e-126">Cada parâmetro é um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="6742e-126">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6742e-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6742e-127">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>  
 [<span data-ttu-id="6742e-128">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="6742e-128">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="6742e-129">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="6742e-129">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="6742e-130">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="6742e-130">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="6742e-131">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="6742e-131">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="6742e-132">Associações</span><span class="sxs-lookup"><span data-stu-id="6742e-132">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
