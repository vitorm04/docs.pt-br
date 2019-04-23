---
title: <xmlElement>
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: a72641b438801cfd493c322297e7c384e83e687c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59230493"
---
# <a name="xmlelement"></a><span data-ttu-id="d23e7-101">\<xmlElement></span><span class="sxs-lookup"><span data-stu-id="d23e7-101">\<xmlElement></span></span>
<span data-ttu-id="d23e7-102">Especifica um elemento XML que é enviado no corpo da mensagem para o serviço de Token de segurança ao solicitar um token.</span><span class="sxs-lookup"><span data-stu-id="d23e7-102">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
 <span data-ttu-id="d23e7-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d23e7-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="d23e7-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="d23e7-104">\<bindings></span></span>  
<span data-ttu-id="d23e7-105">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="d23e7-105">\<wsFederatedBinding></span></span>  
<span data-ttu-id="d23e7-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="d23e7-106">\<binding></span></span>  
<span data-ttu-id="d23e7-107">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="d23e7-107">\<security></span></span>  
<span data-ttu-id="d23e7-108">\<message></span><span class="sxs-lookup"><span data-stu-id="d23e7-108">\<message></span></span>  
<span data-ttu-id="d23e7-109">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="d23e7-109">\<tokenRequestParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d23e7-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d23e7-110">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>
  <xmlElement xmlElement="String" />
</tokenRequestParameters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d23e7-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d23e7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d23e7-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d23e7-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d23e7-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="d23e7-113">Attributes</span></span>  
  
|<span data-ttu-id="d23e7-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="d23e7-114">Attribute</span></span>|<span data-ttu-id="d23e7-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="d23e7-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d23e7-116">xmlElement</span><span class="sxs-lookup"><span data-stu-id="d23e7-116">xmlElement</span></span>|<span data-ttu-id="d23e7-117">Uma cadeia de caracteres especificando um elemento XML que é enviado no corpo da mensagem para o serviço de Token de segurança ao solicitar um token.</span><span class="sxs-lookup"><span data-stu-id="d23e7-117">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d23e7-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d23e7-118">Child Elements</span></span>  
 <span data-ttu-id="d23e7-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="d23e7-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d23e7-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d23e7-120">Parent Elements</span></span>  
  
|<span data-ttu-id="d23e7-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="d23e7-121">Element</span></span>|<span data-ttu-id="d23e7-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="d23e7-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d23e7-123">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="d23e7-123">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="d23e7-124">Uma coleção de parâmetros de solicitação de token.</span><span class="sxs-lookup"><span data-stu-id="d23e7-124">A collection of token request parameters.</span></span> <span data-ttu-id="d23e7-125">Cada parâmetro é um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="d23e7-125">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d23e7-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d23e7-126">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>
- [<span data-ttu-id="d23e7-127">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="d23e7-127">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="d23e7-128">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="d23e7-128">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="d23e7-129">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="d23e7-129">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="d23e7-130">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="d23e7-130">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="d23e7-131">Associações</span><span class="sxs-lookup"><span data-stu-id="d23e7-131">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
