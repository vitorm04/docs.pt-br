---
title: '&lt;secureConversationAuthentication&gt; de &lt;serviceCredential&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 0fb9ff476812b6b889750e8eb7b80efce801f041
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltsecureconversationauthenticationgt-of-ltservicecredentialgt"></a><span data-ttu-id="fb8c6-102">&lt;secureConversationAuthentication&gt; de &lt;serviceCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="fb8c6-102">&lt;secureConversationAuthentication&gt; of &lt;serviceCredential&gt;</span></span>
<span data-ttu-id="fb8c6-103">Especifica as configurações para um serviço de conversa segura.</span><span class="sxs-lookup"><span data-stu-id="fb8c6-103">Specifies the settings for a secure conversation service.</span></span>  
  
 <span data-ttu-id="fb8c6-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="fb8c6-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="fb8c6-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="fb8c6-105">\<behaviors></span></span>  
<span data-ttu-id="fb8c6-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="fb8c6-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="fb8c6-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="fb8c6-107">\<behavior></span></span>  
<span data-ttu-id="fb8c6-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="fb8c6-108">\<serviceCredentials></span></span>  
<span data-ttu-id="fb8c6-109">\<secureConversationAuthentication ></span><span class="sxs-lookup"><span data-stu-id="fb8c6-109">\<secureConversationAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb8c6-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fb8c6-110">Syntax</span></span>  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fb8c6-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fb8c6-111">Attributes and Elements</span></span>  
 <span data-ttu-id="fb8c6-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="fb8c6-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fb8c6-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="fb8c6-113">Attributes</span></span>  
  
|<span data-ttu-id="fb8c6-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="fb8c6-114">Attribute</span></span>|<span data-ttu-id="fb8c6-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="fb8c6-115">Description</span></span>|  
|---------------|-----------------|  
|`securityStateEncoderType`|<span data-ttu-id="fb8c6-116">Uma cadeia de caracteres que especifica o tipo de <xref:System.ServiceModel.Security.SecurityStateEncoder> a ser usado.</span><span class="sxs-lookup"><span data-stu-id="fb8c6-116">A string that specifies the type of <xref:System.ServiceModel.Security.SecurityStateEncoder> to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fb8c6-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="fb8c6-117">Child Elements</span></span>  
 <span data-ttu-id="fb8c6-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="fb8c6-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fb8c6-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="fb8c6-119">Parent Elements</span></span>  
  
|<span data-ttu-id="fb8c6-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="fb8c6-120">Element</span></span>|<span data-ttu-id="fb8c6-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="fb8c6-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fb8c6-122">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="fb8c6-122">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="fb8c6-123">Especifica a credencial a ser usado na autenticação do serviço e as configurações de relacionadas à validação de credenciais do cliente.</span><span class="sxs-lookup"><span data-stu-id="fb8c6-123">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb8c6-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="fb8c6-124">Remarks</span></span>  
 <span data-ttu-id="fb8c6-125">Use este elemento de configuração para especificar uma lista de tipos de declaração conhecidos para a serialização de cookies de segurança contexto Token SCT (), bem como um codificador para codificar e proteger as informações de cookies.</span><span class="sxs-lookup"><span data-stu-id="fb8c6-125">Use this configuration element to specify a list of known claim types for the Security Context Token (SCT) cookies serialization, as well as an encoder to encode and secure cookies information.</span></span> <span data-ttu-id="fb8c6-126">Para obter mais informações sobre SCT, consulte <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span><span class="sxs-lookup"><span data-stu-id="fb8c6-126">For more information on SCT, see <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb8c6-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fb8c6-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>  
 <xref:System.ServiceModel.Security.SecureConversationServiceCredential>
