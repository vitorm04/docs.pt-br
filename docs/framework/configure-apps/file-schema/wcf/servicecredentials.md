---
title: <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: 90a34a4a52b4c7a2e67d733fecba132818cac4fc
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399631"
---
# <a name="servicecredentials"></a><span data-ttu-id="1882c-101">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="1882c-101">\<serviceCredentials></span></span>
<span data-ttu-id="1882c-102">Especifica a credencial a ser usada na autenticação do serviço e nas configurações relacionadas à validação da credencial do cliente.</span><span class="sxs-lookup"><span data-stu-id="1882c-102">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
<span data-ttu-id="1882c-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1882c-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1882c-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="1882c-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="1882c-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="1882c-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="1882c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de portais**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="1882c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="1882c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="1882c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="1882c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceCredentials >**</span><span class="sxs-lookup"><span data-stu-id="1882c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCredentials>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1882c-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1882c-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1882c-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1882c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1882c-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1882c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1882c-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="1882c-112">Attributes</span></span>  
  
|<span data-ttu-id="1882c-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="1882c-113">Attribute</span></span>|<span data-ttu-id="1882c-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="1882c-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="1882c-115">Uma cadeia de caracteres que especifica o tipo deste elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="1882c-115">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1882c-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1882c-116">Child Elements</span></span>  
  
|<span data-ttu-id="1882c-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="1882c-117">Element</span></span>|<span data-ttu-id="1882c-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="1882c-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1882c-119">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="1882c-119">\<clientCertificate></span></span>](clientcertificate-of-servicecredentials.md)|<span data-ttu-id="1882c-120">Especifica o certificado a ser usado quando o certificado do cliente está disponível fora de banda.</span><span class="sxs-lookup"><span data-stu-id="1882c-120">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="1882c-121">Esse elemento também especifica as configurações de validação de certificado do cliente.</span><span class="sxs-lookup"><span data-stu-id="1882c-121">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="1882c-122">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="1882c-122">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="1882c-123">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="1882c-123">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="1882c-124">Especifica o token emitido atual para este serviço.</span><span class="sxs-lookup"><span data-stu-id="1882c-124">Specifies the current issued token for this service.</span></span> <span data-ttu-id="1882c-125">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="1882c-125">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[<span data-ttu-id="1882c-126">\<peer></span><span class="sxs-lookup"><span data-stu-id="1882c-126">\<peer></span></span>](peer-of-servicecredentials.md)|<span data-ttu-id="1882c-127">Especifica as credenciais atuais para um nó par.</span><span class="sxs-lookup"><span data-stu-id="1882c-127">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="1882c-128">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="1882c-128">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="1882c-129">\<secureConversationAuthentication></span><span class="sxs-lookup"><span data-stu-id="1882c-129">\<secureConversationAuthentication></span></span>](secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="1882c-130">Especifica as credenciais atuais para uma conversa segura.</span><span class="sxs-lookup"><span data-stu-id="1882c-130">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="1882c-131">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="1882c-131">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[<span data-ttu-id="1882c-132">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="1882c-132">\<serviceCertificate></span></span>](servicecertificate-of-servicecredentials.md)|<span data-ttu-id="1882c-133">Especifica um certificado usado por um serviço para se identificar.</span><span class="sxs-lookup"><span data-stu-id="1882c-133">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="1882c-134">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="1882c-134">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="1882c-135">\<userNameAuthentication></span><span class="sxs-lookup"><span data-stu-id="1882c-135">\<userNameAuthentication></span></span>](usernameauthentication.md)|<span data-ttu-id="1882c-136">Especifica as configurações para validação de senha de nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="1882c-136">Specifies the settings for username password validation.</span></span> <span data-ttu-id="1882c-137">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="1882c-137">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[<span data-ttu-id="1882c-138">\<windowsAuthentication></span><span class="sxs-lookup"><span data-stu-id="1882c-138">\<windowsAuthentication></span></span>](windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="1882c-139">Especifica as configurações para validação de credenciais do Windows.</span><span class="sxs-lookup"><span data-stu-id="1882c-139">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="1882c-140">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="1882c-140">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1882c-141">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1882c-141">Parent Elements</span></span>  
  
|<span data-ttu-id="1882c-142">Elemento</span><span class="sxs-lookup"><span data-stu-id="1882c-142">Element</span></span>|<span data-ttu-id="1882c-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="1882c-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1882c-144">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="1882c-144">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="1882c-145">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="1882c-145">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1882c-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1882c-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [<span data-ttu-id="1882c-147">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="1882c-147">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
