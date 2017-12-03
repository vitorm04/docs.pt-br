---
title: '&lt;xmlElement&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 395205c2-d8c0-4a5e-90f3-7ce3c085fccd
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b36eb762de3864eb786d0b7157d316ab071dc2fa
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltxmlelementgt"></a><span data-ttu-id="a9310-102">&lt;xmlElement&gt;</span><span class="sxs-lookup"><span data-stu-id="a9310-102">&lt;xmlElement&gt;</span></span>
<span data-ttu-id="a9310-103">Especifica um elemento XML que é enviado no corpo da mensagem para o serviço de Token de segurança ao solicitar um token.</span><span class="sxs-lookup"><span data-stu-id="a9310-103">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
 <span data-ttu-id="a9310-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="a9310-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a9310-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="a9310-105">\<bindings></span></span>  
<span data-ttu-id="a9310-106">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="a9310-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="a9310-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="a9310-107">\<binding></span></span>  
<span data-ttu-id="a9310-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="a9310-108">\<security></span></span>  
<span data-ttu-id="a9310-109">\<mensagem ></span><span class="sxs-lookup"><span data-stu-id="a9310-109">\<message></span></span>  
<span data-ttu-id="a9310-110">\<tokenRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="a9310-110">\<tokenRequestParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9310-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a9310-111">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>  
      <xmlElement xmlElement="String" />  
</tokenRequestParameters>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a9310-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a9310-112">Attributes and Elements</span></span>  
 <span data-ttu-id="a9310-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a9310-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a9310-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="a9310-114">Attributes</span></span>  
  
|<span data-ttu-id="a9310-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="a9310-115">Attribute</span></span>|<span data-ttu-id="a9310-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="a9310-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a9310-117">xmlElement</span><span class="sxs-lookup"><span data-stu-id="a9310-117">xmlElement</span></span>|<span data-ttu-id="a9310-118">Uma cadeia de caracteres especificando um elemento XML que é enviado no corpo da mensagem para o serviço de Token de segurança ao solicitar um token.</span><span class="sxs-lookup"><span data-stu-id="a9310-118">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a9310-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a9310-119">Child Elements</span></span>  
 <span data-ttu-id="a9310-120">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="a9310-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a9310-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a9310-121">Parent Elements</span></span>  
  
|<span data-ttu-id="a9310-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="a9310-122">Element</span></span>|<span data-ttu-id="a9310-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="a9310-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a9310-124">\<tokenRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="a9310-124">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="a9310-125">Uma coleção de parâmetros de solicitação de token.</span><span class="sxs-lookup"><span data-stu-id="a9310-125">A collection of token request parameters.</span></span> <span data-ttu-id="a9310-126">Cada parâmetro é um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="a9310-126">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a9310-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a9310-127">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>  
 [<span data-ttu-id="a9310-128">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="a9310-128">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="a9310-129">Federação e Tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="a9310-129">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="a9310-130">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="a9310-130">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="a9310-131">Federação e Tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="a9310-131">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 <span data-ttu-id="a9310-132">[Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)</span><span class="sxs-lookup"><span data-stu-id="a9310-132">[Bindings](../../../../../docs/framework/wcf/bindings.md)</span></span>
