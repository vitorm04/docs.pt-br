---
title: <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: 54ac4f0aa31a4311976449d545880d825c06337d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55256466"
---
# <a name="servicecredentials"></a><span data-ttu-id="97b71-101">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="97b71-101">\<serviceCredentials></span></span>
<span data-ttu-id="97b71-102">Especifica a credencial a ser usado na autenticação do serviço e as configurações de relacionadas à validação de credenciais do cliente.</span><span class="sxs-lookup"><span data-stu-id="97b71-102">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
 <span data-ttu-id="97b71-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="97b71-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="97b71-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="97b71-104">\<behaviors></span></span>  
<span data-ttu-id="97b71-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="97b71-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="97b71-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="97b71-106">\<behavior></span></span>  
<span data-ttu-id="97b71-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="97b71-107">\<serviceCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97b71-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="97b71-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="97b71-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="97b71-109">Attributes and Elements</span></span>  
 <span data-ttu-id="97b71-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="97b71-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="97b71-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="97b71-111">Attributes</span></span>  
  
|<span data-ttu-id="97b71-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="97b71-112">Attribute</span></span>|<span data-ttu-id="97b71-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="97b71-113">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="97b71-114">Uma cadeia de caracteres que especifica o tipo desse elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="97b71-114">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="97b71-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="97b71-115">Child Elements</span></span>  
  
|<span data-ttu-id="97b71-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="97b71-116">Element</span></span>|<span data-ttu-id="97b71-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="97b71-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="97b71-118">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="97b71-118">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|<span data-ttu-id="97b71-119">Especifica o certificado a ser usado quando o certificado do cliente está disponível fora da banda.</span><span class="sxs-lookup"><span data-stu-id="97b71-119">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="97b71-120">Esse elemento também especifica configurações de validação de certificado do cliente.</span><span class="sxs-lookup"><span data-stu-id="97b71-120">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="97b71-121">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="97b71-121">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="97b71-122">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="97b71-122">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="97b71-123">Especifica o token emitido atual para este serviço.</span><span class="sxs-lookup"><span data-stu-id="97b71-123">Specifies the current issued token for this service.</span></span> <span data-ttu-id="97b71-124">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="97b71-124">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[<span data-ttu-id="97b71-125">\<peer></span><span class="sxs-lookup"><span data-stu-id="97b71-125">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="97b71-126">Especifica as credenciais atuais para um nó par.</span><span class="sxs-lookup"><span data-stu-id="97b71-126">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="97b71-127">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="97b71-127">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="97b71-128">\<secureConversationAuthentication></span><span class="sxs-lookup"><span data-stu-id="97b71-128">\<secureConversationAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="97b71-129">Especifica as credenciais atuais para uma conversa segura.</span><span class="sxs-lookup"><span data-stu-id="97b71-129">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="97b71-130">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="97b71-130">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[<span data-ttu-id="97b71-131">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="97b71-131">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|<span data-ttu-id="97b71-132">Especifica um certificado usado por um serviço para se identificar.</span><span class="sxs-lookup"><span data-stu-id="97b71-132">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="97b71-133">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="97b71-133">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="97b71-134">\<userNameAuthentication></span><span class="sxs-lookup"><span data-stu-id="97b71-134">\<userNameAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)|<span data-ttu-id="97b71-135">Especifica as configurações para validação de senha do nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="97b71-135">Specifies the settings for username password validation.</span></span> <span data-ttu-id="97b71-136">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="97b71-136">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[<span data-ttu-id="97b71-137">\<windowsAuthentication></span><span class="sxs-lookup"><span data-stu-id="97b71-137">\<windowsAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="97b71-138">Especifica as configurações para validação de credenciais do Windows.</span><span class="sxs-lookup"><span data-stu-id="97b71-138">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="97b71-139">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="97b71-139">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="97b71-140">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="97b71-140">Parent Elements</span></span>  
  
|<span data-ttu-id="97b71-141">Elemento</span><span class="sxs-lookup"><span data-stu-id="97b71-141">Element</span></span>|<span data-ttu-id="97b71-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="97b71-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="97b71-143">\<behavior></span><span class="sxs-lookup"><span data-stu-id="97b71-143">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="97b71-144">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="97b71-144">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="97b71-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="97b71-145">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [<span data-ttu-id="97b71-146">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="97b71-146">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
