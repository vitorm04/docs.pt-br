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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d1efe32121bc5744c305ff8ef8eefabd8a9d19e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltxmlelementgt"></a><span data-ttu-id="8e977-102">&lt;xmlElement&gt;</span><span class="sxs-lookup"><span data-stu-id="8e977-102">&lt;xmlElement&gt;</span></span>
<span data-ttu-id="8e977-103">Especifica um elemento XML que é enviado no corpo da mensagem para o serviço de Token de segurança ao solicitar um token.</span><span class="sxs-lookup"><span data-stu-id="8e977-103">Specifies an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>  
  
 <span data-ttu-id="8e977-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="8e977-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8e977-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="8e977-105">\<bindings></span></span>  
<span data-ttu-id="8e977-106">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="8e977-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="8e977-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="8e977-107">\<binding></span></span>  
<span data-ttu-id="8e977-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="8e977-108">\<security></span></span>  
<span data-ttu-id="8e977-109">\<mensagem ></span><span class="sxs-lookup"><span data-stu-id="8e977-109">\<message></span></span>  
<span data-ttu-id="8e977-110">\<tokenRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="8e977-110">\<tokenRequestParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e977-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8e977-111">Syntax</span></span>  
  
```xml  
<tokenRequestParameters>  
      <xmlElement xmlElement="String" />  
</tokenRequestParameters>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8e977-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8e977-112">Attributes and Elements</span></span>  
 <span data-ttu-id="8e977-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8e977-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8e977-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="8e977-114">Attributes</span></span>  
  
|<span data-ttu-id="8e977-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="8e977-115">Attribute</span></span>|<span data-ttu-id="8e977-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e977-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8e977-117">xmlElement</span><span class="sxs-lookup"><span data-stu-id="8e977-117">xmlElement</span></span>|<span data-ttu-id="8e977-118">Uma cadeia de caracteres especificando um elemento XML que é enviado no corpo da mensagem para o serviço de Token de segurança ao solicitar um token.</span><span class="sxs-lookup"><span data-stu-id="8e977-118">A string specifying an XML element that is sent in the message body to the Security Token Service when requesting a token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8e977-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8e977-119">Child Elements</span></span>  
 <span data-ttu-id="8e977-120">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="8e977-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8e977-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8e977-121">Parent Elements</span></span>  
  
|<span data-ttu-id="8e977-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="8e977-122">Element</span></span>|<span data-ttu-id="8e977-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="8e977-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8e977-124">\<tokenRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="8e977-124">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="8e977-125">Uma coleção de parâmetros de solicitação de token.</span><span class="sxs-lookup"><span data-stu-id="8e977-125">A collection of token request parameters.</span></span> <span data-ttu-id="8e977-126">Cada parâmetro é um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="8e977-126">Each parameter is an XML element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8e977-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8e977-127">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.TokenRequestParameters%2A>  
 [<span data-ttu-id="8e977-128">Autenticação e identidade de serviço</span><span class="sxs-lookup"><span data-stu-id="8e977-128">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="8e977-129">Federação e Tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="8e977-129">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="8e977-130">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="8e977-130">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="8e977-131">Federação e Tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="8e977-131">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 <span data-ttu-id="8e977-132">[Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)</span><span class="sxs-lookup"><span data-stu-id="8e977-132">[Bindings](../../../../../docs/framework/wcf/bindings.md)</span></span>
