---
title: '&lt;secureConversationAuthentication&gt; de &lt;serviceCredential&gt;'
ms.date: 03/30/2017
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 7b56d12793ad35e6f951638465e77b92a66a6fd0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749326"
---
# <a name="ltsecureconversationauthenticationgt-of-ltservicecredentialgt"></a><span data-ttu-id="ef4c4-102">&lt;secureConversationAuthentication&gt; de &lt;serviceCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="ef4c4-102">&lt;secureConversationAuthentication&gt; of &lt;serviceCredential&gt;</span></span>
<span data-ttu-id="ef4c4-103">Especifica as configurações para um serviço de conversa segura.</span><span class="sxs-lookup"><span data-stu-id="ef4c4-103">Specifies the settings for a secure conversation service.</span></span>  
  
 <span data-ttu-id="ef4c4-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ef4c4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ef4c4-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="ef4c4-105">\<behaviors></span></span>  
<span data-ttu-id="ef4c4-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="ef4c4-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="ef4c4-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="ef4c4-107">\<behavior></span></span>  
<span data-ttu-id="ef4c4-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="ef4c4-108">\<serviceCredentials></span></span>  
<span data-ttu-id="ef4c4-109">\<secureConversationAuthentication ></span><span class="sxs-lookup"><span data-stu-id="ef4c4-109">\<secureConversationAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef4c4-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ef4c4-110">Syntax</span></span>  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ef4c4-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ef4c4-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ef4c4-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ef4c4-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ef4c4-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="ef4c4-113">Attributes</span></span>  
  
|<span data-ttu-id="ef4c4-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="ef4c4-114">Attribute</span></span>|<span data-ttu-id="ef4c4-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="ef4c4-115">Description</span></span>|  
|---------------|-----------------|  
|`securityStateEncoderType`|<span data-ttu-id="ef4c4-116">Uma cadeia de caracteres que especifica o tipo de <xref:System.ServiceModel.Security.SecurityStateEncoder> a ser usado.</span><span class="sxs-lookup"><span data-stu-id="ef4c4-116">A string that specifies the type of <xref:System.ServiceModel.Security.SecurityStateEncoder> to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ef4c4-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ef4c4-117">Child Elements</span></span>  
 <span data-ttu-id="ef4c4-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="ef4c4-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ef4c4-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ef4c4-119">Parent Elements</span></span>  
  
|<span data-ttu-id="ef4c4-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="ef4c4-120">Element</span></span>|<span data-ttu-id="ef4c4-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="ef4c4-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ef4c4-122">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="ef4c4-122">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="ef4c4-123">Especifica a credencial a ser usado na autenticação do serviço e as configurações de relacionadas à validação de credenciais do cliente.</span><span class="sxs-lookup"><span data-stu-id="ef4c4-123">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef4c4-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="ef4c4-124">Remarks</span></span>  
 <span data-ttu-id="ef4c4-125">Use este elemento de configuração para especificar uma lista de tipos de declaração conhecidos para a serialização de cookies de segurança contexto Token SCT (), bem como um codificador para codificar e proteger as informações de cookies.</span><span class="sxs-lookup"><span data-stu-id="ef4c4-125">Use this configuration element to specify a list of known claim types for the Security Context Token (SCT) cookies serialization, as well as an encoder to encode and secure cookies information.</span></span> <span data-ttu-id="ef4c4-126">Para obter mais informações sobre SCT, consulte <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span><span class="sxs-lookup"><span data-stu-id="ef4c4-126">For more information on SCT, see <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef4c4-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ef4c4-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>  
 <xref:System.ServiceModel.Security.SecureConversationServiceCredential>
