---
title: '&lt;ServiceCredentials&gt;'
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: b9e32509a5e182301455eaf0e602a03c51fbc23a
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54150767"
---
# <a name="ltservicecredentialsgt"></a><span data-ttu-id="b7337-102">&lt;ServiceCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="b7337-102">&lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="b7337-103">Especifica a credencial a ser usado na autenticação do serviço e as configurações de relacionadas à validação de credenciais do cliente.</span><span class="sxs-lookup"><span data-stu-id="b7337-103">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
 <span data-ttu-id="b7337-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b7337-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b7337-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="b7337-105">\<behaviors></span></span>  
<span data-ttu-id="b7337-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="b7337-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="b7337-107">\<comportamento de ></span><span class="sxs-lookup"><span data-stu-id="b7337-107">\<behavior></span></span>  
<span data-ttu-id="b7337-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="b7337-108">\<serviceCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7337-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7337-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b7337-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b7337-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b7337-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b7337-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b7337-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="b7337-112">Attributes</span></span>  
  
|<span data-ttu-id="b7337-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="b7337-113">Attribute</span></span>|<span data-ttu-id="b7337-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7337-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="b7337-115">Uma cadeia de caracteres que especifica o tipo desse elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="b7337-115">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b7337-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b7337-116">Child Elements</span></span>  
  
|<span data-ttu-id="b7337-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="b7337-117">Element</span></span>|<span data-ttu-id="b7337-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7337-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7337-119">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="b7337-119">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|<span data-ttu-id="b7337-120">Especifica o certificado a ser usado quando o certificado do cliente está disponível fora da banda.</span><span class="sxs-lookup"><span data-stu-id="b7337-120">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="b7337-121">Esse elemento também especifica configurações de validação de certificado do cliente.</span><span class="sxs-lookup"><span data-stu-id="b7337-121">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="b7337-122">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="b7337-122">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="b7337-123">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="b7337-123">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="b7337-124">Especifica o token emitido atual para este serviço.</span><span class="sxs-lookup"><span data-stu-id="b7337-124">Specifies the current issued token for this service.</span></span> <span data-ttu-id="b7337-125">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="b7337-125">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[<span data-ttu-id="b7337-126">\<par ></span><span class="sxs-lookup"><span data-stu-id="b7337-126">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="b7337-127">Especifica as credenciais atuais para um nó par.</span><span class="sxs-lookup"><span data-stu-id="b7337-127">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="b7337-128">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="b7337-128">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="b7337-129">\<secureConversationAuthentication ></span><span class="sxs-lookup"><span data-stu-id="b7337-129">\<secureConversationAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="b7337-130">Especifica as credenciais atuais para uma conversa segura.</span><span class="sxs-lookup"><span data-stu-id="b7337-130">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="b7337-131">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="b7337-131">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[<span data-ttu-id="b7337-132">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="b7337-132">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|<span data-ttu-id="b7337-133">Especifica um certificado usado por um serviço para se identificar.</span><span class="sxs-lookup"><span data-stu-id="b7337-133">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="b7337-134">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="b7337-134">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="b7337-135">\<userNameAuthentication ></span><span class="sxs-lookup"><span data-stu-id="b7337-135">\<userNameAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)|<span data-ttu-id="b7337-136">Especifica as configurações para validação de senha do nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="b7337-136">Specifies the settings for username password validation.</span></span> <span data-ttu-id="b7337-137">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="b7337-137">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[<span data-ttu-id="b7337-138">\<windowsAuthentication ></span><span class="sxs-lookup"><span data-stu-id="b7337-138">\<windowsAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="b7337-139">Especifica as configurações para validação de credenciais do Windows.</span><span class="sxs-lookup"><span data-stu-id="b7337-139">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="b7337-140">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="b7337-140">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b7337-141">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b7337-141">Parent Elements</span></span>  
  
|<span data-ttu-id="b7337-142">Elemento</span><span class="sxs-lookup"><span data-stu-id="b7337-142">Element</span></span>|<span data-ttu-id="b7337-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7337-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7337-144">\<comportamento de ></span><span class="sxs-lookup"><span data-stu-id="b7337-144">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="b7337-145">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="b7337-145">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b7337-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7337-146">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
 [<span data-ttu-id="b7337-147">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="b7337-147">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
