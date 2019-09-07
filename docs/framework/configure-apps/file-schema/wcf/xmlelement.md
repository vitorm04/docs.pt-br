---
title: <xmlElement>
ms.date: 03/30/2017
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
ms.openlocfilehash: 841331f233bb8c42c25c88ad8e9b4fb1a86faa76
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398999"
---
# <a name="xmlelement"></a><span data-ttu-id="68362-101">\<> xmlElement</span><span class="sxs-lookup"><span data-stu-id="68362-101">\<xmlElement></span></span>
<span data-ttu-id="68362-102">Especifica um elemento XML que é enviado no corpo da mensagem para o serviço de token de segurança ao solicitar um token.</span><span class="sxs-lookup"><span data-stu-id="68362-102">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
<span data-ttu-id="68362-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="68362-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="68362-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="68362-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="68362-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="68362-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="68362-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> wsFederationHttpBinding**](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="68362-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="68362-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**</span><span class="sxs-lookup"><span data-stu-id="68362-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="68362-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de segurança**](security-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="68362-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="68362-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de mensagem**](message-element-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="68362-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="68362-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> tokenRequestParameters**](tokenrequestparameters.md)</span><span class="sxs-lookup"><span data-stu-id="68362-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<tokenRequestParameters>**](tokenrequestparameters.md)</span></span>\
<span data-ttu-id="68362-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> xmlElement**</span><span class="sxs-lookup"><span data-stu-id="68362-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<xmlElement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68362-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="68362-112">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>
  <xmlElement xmlElement="String" />
</tokenRequestParameters>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="68362-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="68362-113">Attributes and Elements</span></span>  
 <span data-ttu-id="68362-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="68362-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="68362-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="68362-115">Attributes</span></span>  
  
|<span data-ttu-id="68362-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="68362-116">Attribute</span></span>|<span data-ttu-id="68362-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="68362-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="68362-118">xmlElement</span><span class="sxs-lookup"><span data-stu-id="68362-118">xmlElement</span></span>|<span data-ttu-id="68362-119">Uma cadeia de caracteres que especifica um elemento XML que é enviado no corpo da mensagem para o serviço de token de segurança ao solicitar um token.</span><span class="sxs-lookup"><span data-stu-id="68362-119">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="68362-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="68362-120">Child Elements</span></span>  
 <span data-ttu-id="68362-121">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="68362-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="68362-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="68362-122">Parent Elements</span></span>  
  
|<span data-ttu-id="68362-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="68362-123">Element</span></span>|<span data-ttu-id="68362-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="68362-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="68362-125">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="68362-125">\<tokenRequestParameters></span></span>](tokenrequestparameters.md)|<span data-ttu-id="68362-126">Uma coleção de parâmetros de solicitação de token.</span><span class="sxs-lookup"><span data-stu-id="68362-126">A collection of token request parameters.</span></span> <span data-ttu-id="68362-127">Cada parâmetro é um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="68362-127">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="68362-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="68362-128">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>
- [<span data-ttu-id="68362-129">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="68362-129">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="68362-130">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="68362-130">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="68362-131">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="68362-131">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="68362-132">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="68362-132">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="68362-133">Associações</span><span class="sxs-lookup"><span data-stu-id="68362-133">Bindings</span></span>](../../../wcf/bindings.md)
