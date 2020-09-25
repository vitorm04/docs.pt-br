---
title: <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: 63368355027856118546bc70183b41864eddb0e6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172873"
---
# \<serviceCredentials>

<span data-ttu-id="3ff39-101">Especifica a credencial a ser usada na autenticação do serviço e nas configurações relacionadas à validação da credencial do cliente.</span><span class="sxs-lookup"><span data-stu-id="3ff39-101">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCredentials>**  
  
## <a name="syntax"></a><span data-ttu-id="3ff39-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3ff39-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ff39-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3ff39-103">Attributes and Elements</span></span>  

 <span data-ttu-id="3ff39-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3ff39-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ff39-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="3ff39-105">Attributes</span></span>  
  
|<span data-ttu-id="3ff39-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="3ff39-106">Attribute</span></span>|<span data-ttu-id="3ff39-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="3ff39-107">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="3ff39-108">Uma cadeia de caracteres que especifica o tipo deste elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="3ff39-108">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3ff39-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3ff39-109">Child Elements</span></span>  
  
|<span data-ttu-id="3ff39-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="3ff39-110">Element</span></span>|<span data-ttu-id="3ff39-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="3ff39-111">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-servicecredentials.md)|<span data-ttu-id="3ff39-112">Especifica o certificado a ser usado quando o certificado do cliente está disponível fora de banda.</span><span class="sxs-lookup"><span data-stu-id="3ff39-112">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="3ff39-113">Esse elemento também especifica as configurações de validação de certificado do cliente.</span><span class="sxs-lookup"><span data-stu-id="3ff39-113">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="3ff39-114">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="3ff39-114">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="3ff39-115">Especifica o token emitido atual para este serviço.</span><span class="sxs-lookup"><span data-stu-id="3ff39-115">Specifies the current issued token for this service.</span></span> <span data-ttu-id="3ff39-116">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="3ff39-116">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[\<peer>](peer-of-servicecredentials.md)|<span data-ttu-id="3ff39-117">Especifica as credenciais atuais para um nó par.</span><span class="sxs-lookup"><span data-stu-id="3ff39-117">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="3ff39-118">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PeerCredentialElement> .</span><span class="sxs-lookup"><span data-stu-id="3ff39-118">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[\<secureConversationAuthentication>](secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="3ff39-119">Especifica as credenciais atuais para uma conversa segura.</span><span class="sxs-lookup"><span data-stu-id="3ff39-119">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="3ff39-120">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.SecureConversationServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="3ff39-120">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[\<serviceCertificate>](servicecertificate-of-servicecredentials.md)|<span data-ttu-id="3ff39-121">Especifica um certificado usado por um serviço para se identificar.</span><span class="sxs-lookup"><span data-stu-id="3ff39-121">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="3ff39-122">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="3ff39-122">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[\<userNameAuthentication>](usernameauthentication.md)|<span data-ttu-id="3ff39-123">Especifica as configurações para validação de senha de nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="3ff39-123">Specifies the settings for username password validation.</span></span> <span data-ttu-id="3ff39-124">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.UserNameServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="3ff39-124">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[\<windowsAuthentication>](windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="3ff39-125">Especifica as configurações para validação de credenciais do Windows.</span><span class="sxs-lookup"><span data-stu-id="3ff39-125">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="3ff39-126">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.WindowsServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="3ff39-126">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3ff39-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3ff39-127">Parent Elements</span></span>  
  
|<span data-ttu-id="3ff39-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="3ff39-128">Element</span></span>|<span data-ttu-id="3ff39-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="3ff39-129">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="3ff39-130">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="3ff39-130">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3ff39-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="3ff39-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [<span data-ttu-id="3ff39-132">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="3ff39-132">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
