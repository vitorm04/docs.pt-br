---
title: "&lt;elemento de&gt; segurança de &lt;ws2007FederationHttpBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
caps.latest.revision: "10"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 27fedcd8ae7501f484de0aa2f21af8c701990285
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecuritygt-element-of-ltws2007federationhttpbindinggt"></a><span data-ttu-id="765d9-102">&lt;elemento de&gt; segurança de &lt;ws2007FederationHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="765d9-102">&lt;security&gt; element of &lt;ws2007FederationHttpBinding&gt;</span></span>
<span data-ttu-id="765d9-103">Define as configurações de segurança de [ \<ws2007FederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="765d9-103">Defines the security settings of the [\<ws2007FederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) element.</span></span>  
  
 <span data-ttu-id="765d9-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="765d9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="765d9-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="765d9-105">\<bindings></span></span>  
<span data-ttu-id="765d9-106">\<WS2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="765d9-106">\<ws2007FederationHttpBinding></span></span>  
<span data-ttu-id="765d9-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="765d9-107">\<binding></span></span>  
<span data-ttu-id="765d9-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="765d9-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="765d9-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="765d9-109">Syntax</span></span>  
  
```xml  
<ws2007FederationBinding>  
    <binding >  
        <security mode="None/Message/TransportWithMessageCredential">  
           <message negotiateServiceCredential="Boolean"  
                algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/ Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
                defaultProtectionLevel="none/sign/EncryptAndSign"   
                issuedTokenType="string"   
                issuedKeyType="SymmetricKey/PublicKey"  
           </message>  
        </security>  
    </binding>  
</ws2007FederationBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="765d9-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="765d9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="765d9-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="765d9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="765d9-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="765d9-112">Attributes</span></span>  
  
|<span data-ttu-id="765d9-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="765d9-113">Attribute</span></span>|<span data-ttu-id="765d9-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="765d9-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="765d9-115">Opcional.</span><span class="sxs-lookup"><span data-stu-id="765d9-115">Optional.</span></span> <span data-ttu-id="765d9-116">Especifica o tipo de segurança que é aplicada.</span><span class="sxs-lookup"><span data-stu-id="765d9-116">Specifies the type of security that is applied.</span></span> <span data-ttu-id="765d9-117">O valor padrão é `Message`.</span><span class="sxs-lookup"><span data-stu-id="765d9-117">The default value is `Message`.</span></span> <span data-ttu-id="765d9-118">Esse atributo é do tipo <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="765d9-118">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="765d9-119">Atributo mode</span><span class="sxs-lookup"><span data-stu-id="765d9-119">mode Attribute</span></span>  
  
|<span data-ttu-id="765d9-120">Valor</span><span class="sxs-lookup"><span data-stu-id="765d9-120">Value</span></span>|<span data-ttu-id="765d9-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="765d9-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="765d9-122">Nenhum</span><span class="sxs-lookup"><span data-stu-id="765d9-122">None</span></span>|<span data-ttu-id="765d9-123">A mensagem SOAP não é segura durante a transferência.</span><span class="sxs-lookup"><span data-stu-id="765d9-123">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="765d9-124">Mensagem</span><span class="sxs-lookup"><span data-stu-id="765d9-124">Message</span></span>|<span data-ttu-id="765d9-125">Integridade, confidencialidade, autenticação de servidor e autenticação de cliente são fornecidos usando a segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="765d9-125">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="765d9-126">Por padrão, o corpo é criptografado e assinado.</span><span class="sxs-lookup"><span data-stu-id="765d9-126">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="765d9-127">O serviço deve ser configurado com um certificado.</span><span class="sxs-lookup"><span data-stu-id="765d9-127">The service must be configured with a certificate.</span></span> <span data-ttu-id="765d9-128">Autenticação de cliente baseia-se no token emitido para o cliente por um serviço de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="765d9-128">Client authentication is based on the token issued to the client by a security token service.</span></span>|  
|<span data-ttu-id="765d9-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="765d9-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="765d9-130">A integridade, a confidencialidade e a autenticação de servidor são fornecidas por HTTPS.</span><span class="sxs-lookup"><span data-stu-id="765d9-130">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="765d9-131">O serviço deve ser configurado com um certificado.</span><span class="sxs-lookup"><span data-stu-id="765d9-131">The service must be configured with a certificate.</span></span> <span data-ttu-id="765d9-132">Autenticação de cliente é fornecida por meio de segurança de mensagens SOAP e é baseada no token emitido para o cliente por um serviço de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="765d9-132">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="765d9-133">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="765d9-133">Child Elements</span></span>  
  
|<span data-ttu-id="765d9-134">Elemento</span><span class="sxs-lookup"><span data-stu-id="765d9-134">Element</span></span>|<span data-ttu-id="765d9-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="765d9-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="765d9-136">\<mensagem ></span><span class="sxs-lookup"><span data-stu-id="765d9-136">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-ws2007httpbinding.md)|<span data-ttu-id="765d9-137">Define as configurações para a segurança de nível de mensagem.</span><span class="sxs-lookup"><span data-stu-id="765d9-137">Defines the settings for the message-level security.</span></span> <span data-ttu-id="765d9-138">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="765d9-138">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="765d9-139">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="765d9-139">Parent Elements</span></span>  
  
|<span data-ttu-id="765d9-140">Elemento</span><span class="sxs-lookup"><span data-stu-id="765d9-140">Element</span></span>|<span data-ttu-id="765d9-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="765d9-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="765d9-142">\<associação ></span><span class="sxs-lookup"><span data-stu-id="765d9-142">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="765d9-143">Define todos os recursos de associação do [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="765d9-143">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="765d9-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="765d9-144">See Also</span></span>  
 <xref:System.ServiceModel.WSFederationHttpSecurity>  
 <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>  
 [<span data-ttu-id="765d9-145">Como criar um WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="765d9-145">How to: Create a WSFederationHttpBinding</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 [<span data-ttu-id="765d9-146">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="765d9-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="765d9-147">Selecionando um tipo de credencial</span><span class="sxs-lookup"><span data-stu-id="765d9-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="765d9-148">Associações</span><span class="sxs-lookup"><span data-stu-id="765d9-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="765d9-149">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="765d9-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="765d9-150">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="765d9-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="765d9-151">\<associação ></span><span class="sxs-lookup"><span data-stu-id="765d9-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
