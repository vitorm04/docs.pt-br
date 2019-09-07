---
title: <secureConversationAuthentication> de <serviceCredential>
ms.date: 03/30/2017
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
ms.openlocfilehash: 336969c654f332ae3d838d8fd6d1c4243838539c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399938"
---
# <a name="secureconversationauthentication-of-servicecredential"></a><span data-ttu-id="c2355-102">\<secureConversationAuthentication > de \<> do incredential</span><span class="sxs-lookup"><span data-stu-id="c2355-102">\<secureConversationAuthentication> of \<serviceCredential></span></span>
<span data-ttu-id="c2355-103">Especifica as configurações para um serviço de conversa segura.</span><span class="sxs-lookup"><span data-stu-id="c2355-103">Specifies the settings for a secure conversation service.</span></span>  
  
<span data-ttu-id="c2355-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c2355-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c2355-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c2355-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c2355-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c2355-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="c2355-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de portais**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c2355-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="c2355-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c2355-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="c2355-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="c2355-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="c2355-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> secureConversationAuthentication**</span><span class="sxs-lookup"><span data-stu-id="c2355-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<secureConversationAuthentication>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2355-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c2355-111">Syntax</span></span>  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c2355-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c2355-112">Attributes and Elements</span></span>  
 <span data-ttu-id="c2355-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c2355-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c2355-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="c2355-114">Attributes</span></span>  
  
|<span data-ttu-id="c2355-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="c2355-115">Attribute</span></span>|<span data-ttu-id="c2355-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="c2355-116">Description</span></span>|  
|---------------|-----------------|  
|`securityStateEncoderType`|<span data-ttu-id="c2355-117">Uma cadeia de caracteres que especifica o <xref:System.ServiceModel.Security.SecurityStateEncoder> tipo de a ser usado.</span><span class="sxs-lookup"><span data-stu-id="c2355-117">A string that specifies the type of <xref:System.ServiceModel.Security.SecurityStateEncoder> to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c2355-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c2355-118">Child Elements</span></span>  
 <span data-ttu-id="c2355-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="c2355-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c2355-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c2355-120">Parent Elements</span></span>  
  
|<span data-ttu-id="c2355-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="c2355-121">Element</span></span>|<span data-ttu-id="c2355-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="c2355-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c2355-123">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="c2355-123">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="c2355-124">Especifica a credencial a ser usada na autenticação do serviço e as configurações relacionadas à validação da credencial do cliente.</span><span class="sxs-lookup"><span data-stu-id="c2355-124">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2355-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="c2355-125">Remarks</span></span>  
 <span data-ttu-id="c2355-126">Use este elemento de configuração para especificar uma lista de tipos de declaração conhecidos para a serialização de cookies do SCT (token de contexto de segurança), bem como um codificador para codificar e proteger informações de cookies.</span><span class="sxs-lookup"><span data-stu-id="c2355-126">Use this configuration element to specify a list of known claim types for the Security Context Token (SCT) cookies serialization, as well as an encoder to encode and secure cookies information.</span></span> <span data-ttu-id="c2355-127">Para obter mais informações sobre o SCT <xref:System.ServiceModel.Security.SecureConversationServiceCredential>, consulte.</span><span class="sxs-lookup"><span data-stu-id="c2355-127">For more information on SCT, see <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2355-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c2355-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Security.SecureConversationServiceCredential>
