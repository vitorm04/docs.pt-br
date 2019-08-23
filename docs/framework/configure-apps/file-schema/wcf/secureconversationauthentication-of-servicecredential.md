---
title: <secureConversationAuthentication> de <serviceCredential>
ms.date: 03/30/2017
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
ms.openlocfilehash: 61034c2c66a6d8e27a87ec5380aa7297247eb31e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935830"
---
# <a name="secureconversationauthentication-of-servicecredential"></a><span data-ttu-id="27372-102">\<secureConversationAuthentication > de \<> do incredential</span><span class="sxs-lookup"><span data-stu-id="27372-102">\<secureConversationAuthentication> of \<serviceCredential></span></span>
<span data-ttu-id="27372-103">Especifica as configurações para um serviço de conversa segura.</span><span class="sxs-lookup"><span data-stu-id="27372-103">Specifies the settings for a secure conversation service.</span></span>  
  
 <span data-ttu-id="27372-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="27372-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="27372-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="27372-105">\<behaviors></span></span>  
<span data-ttu-id="27372-106">\<> de portais</span><span class="sxs-lookup"><span data-stu-id="27372-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="27372-107">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="27372-107">\<behavior></span></span>  
<span data-ttu-id="27372-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="27372-108">\<serviceCredentials></span></span>  
<span data-ttu-id="27372-109">\<secureConversationAuthentication></span><span class="sxs-lookup"><span data-stu-id="27372-109">\<secureConversationAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27372-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="27372-110">Syntax</span></span>  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="27372-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="27372-111">Attributes and Elements</span></span>  
 <span data-ttu-id="27372-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="27372-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="27372-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="27372-113">Attributes</span></span>  
  
|<span data-ttu-id="27372-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="27372-114">Attribute</span></span>|<span data-ttu-id="27372-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="27372-115">Description</span></span>|  
|---------------|-----------------|  
|`securityStateEncoderType`|<span data-ttu-id="27372-116">Uma cadeia de caracteres que especifica o <xref:System.ServiceModel.Security.SecurityStateEncoder> tipo de a ser usado.</span><span class="sxs-lookup"><span data-stu-id="27372-116">A string that specifies the type of <xref:System.ServiceModel.Security.SecurityStateEncoder> to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="27372-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="27372-117">Child Elements</span></span>  
 <span data-ttu-id="27372-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="27372-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="27372-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="27372-119">Parent Elements</span></span>  
  
|<span data-ttu-id="27372-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="27372-120">Element</span></span>|<span data-ttu-id="27372-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="27372-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="27372-122">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="27372-122">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="27372-123">Especifica a credencial a ser usada na autenticação do serviço e as configurações relacionadas à validação da credencial do cliente.</span><span class="sxs-lookup"><span data-stu-id="27372-123">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27372-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="27372-124">Remarks</span></span>  
 <span data-ttu-id="27372-125">Use este elemento de configuração para especificar uma lista de tipos de declaração conhecidos para a serialização de cookies do SCT (token de contexto de segurança), bem como um codificador para codificar e proteger informações de cookies.</span><span class="sxs-lookup"><span data-stu-id="27372-125">Use this configuration element to specify a list of known claim types for the Security Context Token (SCT) cookies serialization, as well as an encoder to encode and secure cookies information.</span></span> <span data-ttu-id="27372-126">Para obter mais informações sobre o SCT <xref:System.ServiceModel.Security.SecureConversationServiceCredential>, consulte.</span><span class="sxs-lookup"><span data-stu-id="27372-126">For more information on SCT, see <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27372-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="27372-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Security.SecureConversationServiceCredential>
