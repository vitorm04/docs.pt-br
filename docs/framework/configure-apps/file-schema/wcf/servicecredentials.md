---
title: '&lt;serviceCredentials&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 00567c32b800bb98386e15b2ba822ccc9623d72b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltservicecredentialsgt"></a><span data-ttu-id="8916c-102">&lt;serviceCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="8916c-102">&lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="8916c-103">Especifica a credencial a ser usado na autenticação do serviço e as configurações de relacionadas à validação de credenciais do cliente.</span><span class="sxs-lookup"><span data-stu-id="8916c-103">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
 <span data-ttu-id="8916c-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="8916c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8916c-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="8916c-105">\<behaviors></span></span>  
<span data-ttu-id="8916c-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="8916c-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="8916c-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="8916c-107">\<behavior></span></span>  
<span data-ttu-id="8916c-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="8916c-108">\<serviceCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8916c-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8916c-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8916c-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8916c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8916c-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8916c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8916c-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="8916c-112">Attributes</span></span>  
  
|<span data-ttu-id="8916c-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="8916c-113">Attribute</span></span>|<span data-ttu-id="8916c-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="8916c-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="8916c-115">Uma cadeia de caracteres que especifica o tipo deste elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="8916c-115">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8916c-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8916c-116">Child Elements</span></span>  
  
|<span data-ttu-id="8916c-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="8916c-117">Element</span></span>|<span data-ttu-id="8916c-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="8916c-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8916c-119">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="8916c-119">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|<span data-ttu-id="8916c-120">Especifica o certificado a ser usado quando o certificado de cliente está fora de banda disponível.</span><span class="sxs-lookup"><span data-stu-id="8916c-120">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="8916c-121">Esse elemento também especifica configurações de validação de certificado de cliente.</span><span class="sxs-lookup"><span data-stu-id="8916c-121">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="8916c-122">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="8916c-122">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="8916c-123">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="8916c-123">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="8916c-124">Especifica o token emitido atual para este serviço.</span><span class="sxs-lookup"><span data-stu-id="8916c-124">Specifies the current issued token for this service.</span></span> <span data-ttu-id="8916c-125">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="8916c-125">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[<span data-ttu-id="8916c-126">\<par ></span><span class="sxs-lookup"><span data-stu-id="8916c-126">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="8916c-127">Especifica as credenciais atuais de um nó ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="8916c-127">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="8916c-128">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="8916c-128">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="8916c-129">\<secureConversationAuthentication ></span><span class="sxs-lookup"><span data-stu-id="8916c-129">\<secureConversationAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="8916c-130">Especifica as credenciais atuais para uma conversa segura.</span><span class="sxs-lookup"><span data-stu-id="8916c-130">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="8916c-131">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="8916c-131">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[<span data-ttu-id="8916c-132">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="8916c-132">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|<span data-ttu-id="8916c-133">Especifica um certificado usado por um serviço para se identificar.</span><span class="sxs-lookup"><span data-stu-id="8916c-133">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="8916c-134">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="8916c-134">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="8916c-135">\<userNameAuthentication ></span><span class="sxs-lookup"><span data-stu-id="8916c-135">\<userNameAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)|<span data-ttu-id="8916c-136">Especifica as configurações para validação de senha do nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="8916c-136">Specifies the settings for username password validation.</span></span> <span data-ttu-id="8916c-137">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="8916c-137">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[<span data-ttu-id="8916c-138">\<windowsAuthentication ></span><span class="sxs-lookup"><span data-stu-id="8916c-138">\<windowsAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="8916c-139">Especifica as configurações para validação de credenciais do Windows.</span><span class="sxs-lookup"><span data-stu-id="8916c-139">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="8916c-140">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="8916c-140">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8916c-141">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8916c-141">Parent Elements</span></span>  
  
|<span data-ttu-id="8916c-142">Elemento</span><span class="sxs-lookup"><span data-stu-id="8916c-142">Element</span></span>|<span data-ttu-id="8916c-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="8916c-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8916c-144">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="8916c-144">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="8916c-145">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="8916c-145">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8916c-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8916c-146">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
 [<span data-ttu-id="8916c-147">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="8916c-147">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
