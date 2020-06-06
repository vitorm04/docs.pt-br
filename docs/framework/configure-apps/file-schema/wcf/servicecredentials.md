---
title: <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: 90a34a4a52b4c7a2e67d733fecba132818cac4fc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399631"
---
# \<serviceCredentials>
<span data-ttu-id="1d452-101">Especifica a credencial a ser usada na autenticação do serviço e nas configurações relacionadas à validação da credencial do cliente.</span><span class="sxs-lookup"><span data-stu-id="1d452-101">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCredentials>**  
  
## <a name="syntax"></a><span data-ttu-id="1d452-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1d452-102">Syntax</span></span>  
  
```xml  
<serviceCredentials type="String">
  <clientCertificate>
  </clientCertificate>
  <issuedTokenAuthentication>
  </issuedTokenAuthentication>
  <peer>
  </peer>
  <secureConversationAuthentication>
  </secureConversationAuthentication>
  <serviceCertificate>
  </serviceCertificate>
  <userNameAuthentication>
  </userNameAuthentication>
  <windowsAuthentication>
  </windowsAuthentication>
</serviceCredentials>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d452-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1d452-103">Attributes and Elements</span></span>  
 <span data-ttu-id="1d452-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1d452-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d452-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="1d452-105">Attributes</span></span>  
  
|<span data-ttu-id="1d452-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="1d452-106">Attribute</span></span>|<span data-ttu-id="1d452-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="1d452-107">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="1d452-108">Uma cadeia de caracteres que especifica o tipo deste elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="1d452-108">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1d452-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1d452-109">Child Elements</span></span>  
  
|<span data-ttu-id="1d452-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="1d452-110">Element</span></span>|<span data-ttu-id="1d452-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="1d452-111">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-servicecredentials.md)|<span data-ttu-id="1d452-112">Especifica o certificado a ser usado quando o certificado do cliente está disponível fora de banda.</span><span class="sxs-lookup"><span data-stu-id="1d452-112">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="1d452-113">Esse elemento também especifica as configurações de validação de certificado do cliente.</span><span class="sxs-lookup"><span data-stu-id="1d452-113">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="1d452-114">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="1d452-114">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="1d452-115">Especifica o token emitido atual para este serviço.</span><span class="sxs-lookup"><span data-stu-id="1d452-115">Specifies the current issued token for this service.</span></span> <span data-ttu-id="1d452-116">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="1d452-116">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[\<peer>](peer-of-servicecredentials.md)|<span data-ttu-id="1d452-117">Especifica as credenciais atuais para um nó par.</span><span class="sxs-lookup"><span data-stu-id="1d452-117">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="1d452-118">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PeerCredentialElement> .</span><span class="sxs-lookup"><span data-stu-id="1d452-118">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[\<secureConversationAuthentication>](secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="1d452-119">Especifica as credenciais atuais para uma conversa segura.</span><span class="sxs-lookup"><span data-stu-id="1d452-119">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="1d452-120">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.SecureConversationServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="1d452-120">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[\<serviceCertificate>](servicecertificate-of-servicecredentials.md)|<span data-ttu-id="1d452-121">Especifica um certificado usado por um serviço para se identificar.</span><span class="sxs-lookup"><span data-stu-id="1d452-121">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="1d452-122">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="1d452-122">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[\<userNameAuthentication>](usernameauthentication.md)|<span data-ttu-id="1d452-123">Especifica as configurações para validação de senha de nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="1d452-123">Specifies the settings for username password validation.</span></span> <span data-ttu-id="1d452-124">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.UserNameServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="1d452-124">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[\<windowsAuthentication>](windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="1d452-125">Especifica as configurações para validação de credenciais do Windows.</span><span class="sxs-lookup"><span data-stu-id="1d452-125">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="1d452-126">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.WindowsServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="1d452-126">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1d452-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1d452-127">Parent Elements</span></span>  
  
|<span data-ttu-id="1d452-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="1d452-128">Element</span></span>|<span data-ttu-id="1d452-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="1d452-129">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="1d452-130">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="1d452-130">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1d452-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="1d452-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [<span data-ttu-id="1d452-132">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="1d452-132">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
