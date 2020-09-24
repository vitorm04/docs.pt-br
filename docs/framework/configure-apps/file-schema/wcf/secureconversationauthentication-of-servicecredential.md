---
title: <secureConversationAuthentication> de <serviceCredential>
ms.date: 03/30/2017
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
ms.openlocfilehash: be2a9298a78de1503271f41076b9f5bb63c73f74
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162226"
---
# <a name="secureconversationauthentication-of-servicecredential"></a><span data-ttu-id="570e9-102">\<secureConversationAuthentication> de \<serviceCredential></span><span class="sxs-lookup"><span data-stu-id="570e9-102">\<secureConversationAuthentication> of \<serviceCredential></span></span>

<span data-ttu-id="570e9-103">Especifica as configurações para um serviço de conversa segura.</span><span class="sxs-lookup"><span data-stu-id="570e9-103">Specifies the settings for a secure conversation service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<secureConversationAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="570e9-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="570e9-104">Syntax</span></span>  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="570e9-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="570e9-105">Attributes and Elements</span></span>  

 <span data-ttu-id="570e9-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="570e9-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="570e9-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="570e9-107">Attributes</span></span>  
  
|<span data-ttu-id="570e9-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="570e9-108">Attribute</span></span>|<span data-ttu-id="570e9-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="570e9-109">Description</span></span>|  
|---------------|-----------------|  
|`securityStateEncoderType`|<span data-ttu-id="570e9-110">Uma cadeia de caracteres que especifica o tipo de <xref:System.ServiceModel.Security.SecurityStateEncoder> a ser usado.</span><span class="sxs-lookup"><span data-stu-id="570e9-110">A string that specifies the type of <xref:System.ServiceModel.Security.SecurityStateEncoder> to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="570e9-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="570e9-111">Child Elements</span></span>  

 <span data-ttu-id="570e9-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="570e9-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="570e9-113">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="570e9-113">Parent Elements</span></span>  
  
|<span data-ttu-id="570e9-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="570e9-114">Element</span></span>|<span data-ttu-id="570e9-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="570e9-115">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="570e9-116">Especifica a credencial a ser usada na autenticação do serviço e as configurações relacionadas à validação da credencial do cliente.</span><span class="sxs-lookup"><span data-stu-id="570e9-116">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="570e9-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="570e9-117">Remarks</span></span>  

 <span data-ttu-id="570e9-118">Use este elemento de configuração para especificar uma lista de tipos de declaração conhecidos para a serialização de cookies do SCT (token de contexto de segurança), bem como um codificador para codificar e proteger informações de cookies.</span><span class="sxs-lookup"><span data-stu-id="570e9-118">Use this configuration element to specify a list of known claim types for the Security Context Token (SCT) cookies serialization, as well as an encoder to encode and secure cookies information.</span></span> <span data-ttu-id="570e9-119">Para obter mais informações sobre o SCT, consulte <xref:System.ServiceModel.Security.SecureConversationServiceCredential> .</span><span class="sxs-lookup"><span data-stu-id="570e9-119">For more information on SCT, see <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="570e9-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="570e9-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Security.SecureConversationServiceCredential>
