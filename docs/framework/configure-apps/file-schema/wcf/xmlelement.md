---
title: <xmlElement>
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: a72641b438801cfd493c322297e7c384e83e687c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698454"
---
# <a name="xmlelement"></a><span data-ttu-id="6015f-101">\<xmlElement></span><span class="sxs-lookup"><span data-stu-id="6015f-101">\<xmlElement></span></span>
<span data-ttu-id="6015f-102">Especifica um elemento XML que é enviado no corpo da mensagem para o serviço de Token de segurança ao solicitar um token.</span><span class="sxs-lookup"><span data-stu-id="6015f-102">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
 <span data-ttu-id="6015f-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6015f-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="6015f-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="6015f-104">\<bindings></span></span>  
<span data-ttu-id="6015f-105">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="6015f-105">\<wsFederatedBinding></span></span>  
<span data-ttu-id="6015f-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="6015f-106">\<binding></span></span>  
<span data-ttu-id="6015f-107">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="6015f-107">\<security></span></span>  
<span data-ttu-id="6015f-108">\<message></span><span class="sxs-lookup"><span data-stu-id="6015f-108">\<message></span></span>  
<span data-ttu-id="6015f-109">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="6015f-109">\<tokenRequestParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6015f-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6015f-110">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>
  <xmlElement xmlElement="String" />
</tokenRequestParameters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6015f-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6015f-111">Attributes and Elements</span></span>  
 <span data-ttu-id="6015f-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6015f-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6015f-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="6015f-113">Attributes</span></span>  
  
|<span data-ttu-id="6015f-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="6015f-114">Attribute</span></span>|<span data-ttu-id="6015f-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="6015f-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6015f-116">xmlElement</span><span class="sxs-lookup"><span data-stu-id="6015f-116">xmlElement</span></span>|<span data-ttu-id="6015f-117">Uma cadeia de caracteres especificando um elemento XML que é enviado no corpo da mensagem para o serviço de Token de segurança ao solicitar um token.</span><span class="sxs-lookup"><span data-stu-id="6015f-117">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6015f-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6015f-118">Child Elements</span></span>  
 <span data-ttu-id="6015f-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="6015f-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6015f-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6015f-120">Parent Elements</span></span>  
  
|<span data-ttu-id="6015f-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="6015f-121">Element</span></span>|<span data-ttu-id="6015f-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="6015f-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6015f-123">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="6015f-123">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="6015f-124">Uma coleção de parâmetros de solicitação de token.</span><span class="sxs-lookup"><span data-stu-id="6015f-124">A collection of token request parameters.</span></span> <span data-ttu-id="6015f-125">Cada parâmetro é um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="6015f-125">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6015f-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6015f-126">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>
- [<span data-ttu-id="6015f-127">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="6015f-127">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="6015f-128">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="6015f-128">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="6015f-129">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="6015f-129">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="6015f-130">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="6015f-130">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="6015f-131">Associações</span><span class="sxs-lookup"><span data-stu-id="6015f-131">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
