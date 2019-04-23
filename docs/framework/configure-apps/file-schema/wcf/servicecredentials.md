---
title: <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: d9f8fdf272962916cd08aede484e9bbde55b96a3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59227074"
---
# <a name="servicecredentials"></a><span data-ttu-id="a6ee4-101">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="a6ee4-101">\<serviceCredentials></span></span>
<span data-ttu-id="a6ee4-102">Especifica a credencial a ser usado na autenticação do serviço e as configurações de relacionadas à validação de credenciais do cliente.</span><span class="sxs-lookup"><span data-stu-id="a6ee4-102">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
 <span data-ttu-id="a6ee4-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a6ee4-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="a6ee4-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="a6ee4-104">\<behaviors></span></span>  
<span data-ttu-id="a6ee4-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="a6ee4-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="a6ee4-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="a6ee4-106">\<behavior></span></span>  
<span data-ttu-id="a6ee4-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="a6ee4-107">\<serviceCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6ee4-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a6ee4-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6ee4-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a6ee4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a6ee4-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a6ee4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6ee4-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="a6ee4-111">Attributes</span></span>  
  
|<span data-ttu-id="a6ee4-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="a6ee4-112">Attribute</span></span>|<span data-ttu-id="a6ee4-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="a6ee4-113">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="a6ee4-114">Uma cadeia de caracteres que especifica o tipo desse elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="a6ee4-114">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a6ee4-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a6ee4-115">Child Elements</span></span>  
  
|<span data-ttu-id="a6ee4-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="a6ee4-116">Element</span></span>|<span data-ttu-id="a6ee4-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="a6ee4-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6ee4-118">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="a6ee4-118">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|<span data-ttu-id="a6ee4-119">Especifica o certificado a ser usado quando o certificado do cliente está disponível fora da banda.</span><span class="sxs-lookup"><span data-stu-id="a6ee4-119">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="a6ee4-120">Esse elemento também especifica configurações de validação de certificado do cliente.</span><span class="sxs-lookup"><span data-stu-id="a6ee4-120">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="a6ee4-121">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="a6ee4-121">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="a6ee4-122">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="a6ee4-122">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="a6ee4-123">Especifica o token emitido atual para este serviço.</span><span class="sxs-lookup"><span data-stu-id="a6ee4-123">Specifies the current issued token for this service.</span></span> <span data-ttu-id="a6ee4-124">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="a6ee4-124">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[<span data-ttu-id="a6ee4-125">\<peer></span><span class="sxs-lookup"><span data-stu-id="a6ee4-125">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="a6ee4-126">Especifica as credenciais atuais para um nó par.</span><span class="sxs-lookup"><span data-stu-id="a6ee4-126">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="a6ee4-127">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="a6ee4-127">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="a6ee4-128">\<secureConversationAuthentication></span><span class="sxs-lookup"><span data-stu-id="a6ee4-128">\<secureConversationAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="a6ee4-129">Especifica as credenciais atuais para uma conversa segura.</span><span class="sxs-lookup"><span data-stu-id="a6ee4-129">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="a6ee4-130">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="a6ee4-130">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[<span data-ttu-id="a6ee4-131">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="a6ee4-131">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|<span data-ttu-id="a6ee4-132">Especifica um certificado usado por um serviço para se identificar.</span><span class="sxs-lookup"><span data-stu-id="a6ee4-132">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="a6ee4-133">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="a6ee4-133">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="a6ee4-134">\<userNameAuthentication></span><span class="sxs-lookup"><span data-stu-id="a6ee4-134">\<userNameAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)|<span data-ttu-id="a6ee4-135">Especifica as configurações para validação de senha do nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="a6ee4-135">Specifies the settings for username password validation.</span></span> <span data-ttu-id="a6ee4-136">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="a6ee4-136">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[<span data-ttu-id="a6ee4-137">\<windowsAuthentication></span><span class="sxs-lookup"><span data-stu-id="a6ee4-137">\<windowsAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="a6ee4-138">Especifica as configurações para validação de credenciais do Windows.</span><span class="sxs-lookup"><span data-stu-id="a6ee4-138">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="a6ee4-139">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="a6ee4-139">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a6ee4-140">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a6ee4-140">Parent Elements</span></span>  
  
|<span data-ttu-id="a6ee4-141">Elemento</span><span class="sxs-lookup"><span data-stu-id="a6ee4-141">Element</span></span>|<span data-ttu-id="a6ee4-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="a6ee4-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6ee4-143">\<behavior></span><span class="sxs-lookup"><span data-stu-id="a6ee4-143">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="a6ee4-144">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="a6ee4-144">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a6ee4-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a6ee4-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [<span data-ttu-id="a6ee4-146">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="a6ee4-146">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
