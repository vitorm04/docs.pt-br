---
title: <secureConversationAuthentication> de <serviceCredential>
ms.date: 03/30/2017
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
ms.openlocfilehash: 336969c654f332ae3d838d8fd6d1c4243838539c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399938"
---
# <a name="secureconversationauthentication-of-servicecredential"></a><span data-ttu-id="8b7fc-102">\<secureConversationAuthentication> de \<serviceCredential></span><span class="sxs-lookup"><span data-stu-id="8b7fc-102">\<secureConversationAuthentication> of \<serviceCredential></span></span>
<span data-ttu-id="8b7fc-103">Especifica as configurações para um serviço de conversa segura.</span><span class="sxs-lookup"><span data-stu-id="8b7fc-103">Specifies the settings for a secure conversation service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<secureConversationAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="8b7fc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8b7fc-104">Syntax</span></span>  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8b7fc-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8b7fc-105">Attributes and Elements</span></span>  
 <span data-ttu-id="8b7fc-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8b7fc-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8b7fc-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="8b7fc-107">Attributes</span></span>  
  
|<span data-ttu-id="8b7fc-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="8b7fc-108">Attribute</span></span>|<span data-ttu-id="8b7fc-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="8b7fc-109">Description</span></span>|  
|---------------|-----------------|  
|`securityStateEncoderType`|<span data-ttu-id="8b7fc-110">Uma cadeia de caracteres que especifica o tipo de <xref:System.ServiceModel.Security.SecurityStateEncoder> a ser usado.</span><span class="sxs-lookup"><span data-stu-id="8b7fc-110">A string that specifies the type of <xref:System.ServiceModel.Security.SecurityStateEncoder> to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8b7fc-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8b7fc-111">Child Elements</span></span>  
 <span data-ttu-id="8b7fc-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="8b7fc-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8b7fc-113">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8b7fc-113">Parent Elements</span></span>  
  
|<span data-ttu-id="8b7fc-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="8b7fc-114">Element</span></span>|<span data-ttu-id="8b7fc-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="8b7fc-115">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="8b7fc-116">Especifica a credencial a ser usada na autenticação do serviço e as configurações relacionadas à validação da credencial do cliente.</span><span class="sxs-lookup"><span data-stu-id="8b7fc-116">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b7fc-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="8b7fc-117">Remarks</span></span>  
 <span data-ttu-id="8b7fc-118">Use este elemento de configuração para especificar uma lista de tipos de declaração conhecidos para a serialização de cookies do SCT (token de contexto de segurança), bem como um codificador para codificar e proteger informações de cookies.</span><span class="sxs-lookup"><span data-stu-id="8b7fc-118">Use this configuration element to specify a list of known claim types for the Security Context Token (SCT) cookies serialization, as well as an encoder to encode and secure cookies information.</span></span> <span data-ttu-id="8b7fc-119">Para obter mais informações sobre o SCT, consulte <xref:System.ServiceModel.Security.SecureConversationServiceCredential> .</span><span class="sxs-lookup"><span data-stu-id="8b7fc-119">For more information on SCT, see <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b7fc-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="8b7fc-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Security.SecureConversationServiceCredential>
