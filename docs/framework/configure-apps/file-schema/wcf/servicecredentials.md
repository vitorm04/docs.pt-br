---
title: <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: b5d257b3082717ba94b9a4517ed5ccd4bd325c06
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936304"
---
# <a name="servicecredentials"></a><span data-ttu-id="56d48-101">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="56d48-101">\<serviceCredentials></span></span>
<span data-ttu-id="56d48-102">Especifica a credencial a ser usada na autenticação do serviço e nas configurações relacionadas à validação da credencial do cliente.</span><span class="sxs-lookup"><span data-stu-id="56d48-102">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
 <span data-ttu-id="56d48-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="56d48-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="56d48-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="56d48-104">\<behaviors></span></span>  
<span data-ttu-id="56d48-105">\<> de portais</span><span class="sxs-lookup"><span data-stu-id="56d48-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="56d48-106">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="56d48-106">\<behavior></span></span>  
<span data-ttu-id="56d48-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="56d48-107">\<serviceCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56d48-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="56d48-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="56d48-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="56d48-109">Attributes and Elements</span></span>  
 <span data-ttu-id="56d48-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="56d48-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="56d48-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="56d48-111">Attributes</span></span>  
  
|<span data-ttu-id="56d48-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="56d48-112">Attribute</span></span>|<span data-ttu-id="56d48-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="56d48-113">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="56d48-114">Uma cadeia de caracteres que especifica o tipo deste elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="56d48-114">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="56d48-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="56d48-115">Child Elements</span></span>  
  
|<span data-ttu-id="56d48-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="56d48-116">Element</span></span>|<span data-ttu-id="56d48-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="56d48-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="56d48-118">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="56d48-118">\<clientCertificate></span></span>](clientcertificate-of-servicecredentials.md)|<span data-ttu-id="56d48-119">Especifica o certificado a ser usado quando o certificado do cliente está disponível fora de banda.</span><span class="sxs-lookup"><span data-stu-id="56d48-119">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="56d48-120">Esse elemento também especifica as configurações de validação de certificado do cliente.</span><span class="sxs-lookup"><span data-stu-id="56d48-120">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="56d48-121">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="56d48-121">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="56d48-122">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="56d48-122">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="56d48-123">Especifica o token emitido atual para este serviço.</span><span class="sxs-lookup"><span data-stu-id="56d48-123">Specifies the current issued token for this service.</span></span> <span data-ttu-id="56d48-124">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="56d48-124">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[<span data-ttu-id="56d48-125">\<peer></span><span class="sxs-lookup"><span data-stu-id="56d48-125">\<peer></span></span>](peer-of-servicecredentials.md)|<span data-ttu-id="56d48-126">Especifica as credenciais atuais para um nó par.</span><span class="sxs-lookup"><span data-stu-id="56d48-126">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="56d48-127">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="56d48-127">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="56d48-128">\<secureConversationAuthentication></span><span class="sxs-lookup"><span data-stu-id="56d48-128">\<secureConversationAuthentication></span></span>](secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="56d48-129">Especifica as credenciais atuais para uma conversa segura.</span><span class="sxs-lookup"><span data-stu-id="56d48-129">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="56d48-130">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="56d48-130">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[<span data-ttu-id="56d48-131">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="56d48-131">\<serviceCertificate></span></span>](servicecertificate-of-servicecredentials.md)|<span data-ttu-id="56d48-132">Especifica um certificado usado por um serviço para se identificar.</span><span class="sxs-lookup"><span data-stu-id="56d48-132">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="56d48-133">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="56d48-133">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="56d48-134">\<userNameAuthentication></span><span class="sxs-lookup"><span data-stu-id="56d48-134">\<userNameAuthentication></span></span>](usernameauthentication.md)|<span data-ttu-id="56d48-135">Especifica as configurações para validação de senha de nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="56d48-135">Specifies the settings for username password validation.</span></span> <span data-ttu-id="56d48-136">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="56d48-136">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[<span data-ttu-id="56d48-137">\<windowsAuthentication></span><span class="sxs-lookup"><span data-stu-id="56d48-137">\<windowsAuthentication></span></span>](windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="56d48-138">Especifica as configurações para validação de credenciais do Windows.</span><span class="sxs-lookup"><span data-stu-id="56d48-138">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="56d48-139">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="56d48-139">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="56d48-140">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="56d48-140">Parent Elements</span></span>  
  
|<span data-ttu-id="56d48-141">Elemento</span><span class="sxs-lookup"><span data-stu-id="56d48-141">Element</span></span>|<span data-ttu-id="56d48-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="56d48-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="56d48-143">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="56d48-143">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="56d48-144">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="56d48-144">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="56d48-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="56d48-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [<span data-ttu-id="56d48-146">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="56d48-146">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
