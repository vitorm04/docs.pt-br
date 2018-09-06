---
title: '&lt;elemento de&gt; segurança de &lt;ws2007FederationHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 87f8f3cf296aeb30cd19c7579887ef94e0992ba7
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44032139"
---
# <a name="ltsecuritygt-element-of-ltws2007federationhttpbindinggt"></a><span data-ttu-id="5e091-102">&lt;elemento de&gt; segurança de &lt;ws2007FederationHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="5e091-102">&lt;security&gt; element of &lt;ws2007FederationHttpBinding&gt;</span></span>
<span data-ttu-id="5e091-103">Define as configurações de segurança de [ \<ws2007FederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="5e091-103">Defines the security settings of the [\<ws2007FederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) element.</span></span>  
  
 <span data-ttu-id="5e091-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5e091-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5e091-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="5e091-105">\<bindings></span></span>  
<span data-ttu-id="5e091-106">\<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="5e091-106">\<ws2007FederationHttpBinding></span></span>  
<span data-ttu-id="5e091-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="5e091-107">\<binding></span></span>  
<span data-ttu-id="5e091-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="5e091-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e091-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5e091-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5e091-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5e091-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5e091-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5e091-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5e091-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="5e091-112">Attributes</span></span>  
  
|<span data-ttu-id="5e091-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="5e091-113">Attribute</span></span>|<span data-ttu-id="5e091-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e091-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="5e091-115">Opcional.</span><span class="sxs-lookup"><span data-stu-id="5e091-115">Optional.</span></span> <span data-ttu-id="5e091-116">Especifica o tipo de segurança que é aplicado.</span><span class="sxs-lookup"><span data-stu-id="5e091-116">Specifies the type of security that is applied.</span></span> <span data-ttu-id="5e091-117">O valor padrão é `Message`.</span><span class="sxs-lookup"><span data-stu-id="5e091-117">The default value is `Message`.</span></span> <span data-ttu-id="5e091-118">Esse atributo é do tipo <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="5e091-118">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="5e091-119">modo de atributo</span><span class="sxs-lookup"><span data-stu-id="5e091-119">mode Attribute</span></span>  
  
|<span data-ttu-id="5e091-120">Valor</span><span class="sxs-lookup"><span data-stu-id="5e091-120">Value</span></span>|<span data-ttu-id="5e091-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e091-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5e091-122">Nenhum</span><span class="sxs-lookup"><span data-stu-id="5e091-122">None</span></span>|<span data-ttu-id="5e091-123">A mensagem SOAP não é segura durante a transferência.</span><span class="sxs-lookup"><span data-stu-id="5e091-123">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="5e091-124">Mensagem</span><span class="sxs-lookup"><span data-stu-id="5e091-124">Message</span></span>|<span data-ttu-id="5e091-125">São fornecidos os serviços de integridade, confidencialidade, autenticação de servidor e autenticação de cliente usando a segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="5e091-125">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="5e091-126">Por padrão, o corpo é criptografado e assinado.</span><span class="sxs-lookup"><span data-stu-id="5e091-126">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="5e091-127">O serviço deve ser configurado com um certificado.</span><span class="sxs-lookup"><span data-stu-id="5e091-127">The service must be configured with a certificate.</span></span> <span data-ttu-id="5e091-128">A autenticação de cliente baseia-se no token emitido ao cliente por um serviço de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="5e091-128">Client authentication is based on the token issued to the client by a security token service.</span></span>|  
|<span data-ttu-id="5e091-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="5e091-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="5e091-130">A integridade, a confidencialidade e a autenticação de servidor são fornecidas por HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5e091-130">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="5e091-131">O serviço deve ser configurado com um certificado.</span><span class="sxs-lookup"><span data-stu-id="5e091-131">The service must be configured with a certificate.</span></span> <span data-ttu-id="5e091-132">A autenticação de cliente é fornecida por meio de segurança de mensagens SOAP e é baseada no token emitido ao cliente por um serviço de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="5e091-132">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5e091-133">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5e091-133">Child Elements</span></span>  
  
|<span data-ttu-id="5e091-134">Elemento</span><span class="sxs-lookup"><span data-stu-id="5e091-134">Element</span></span>|<span data-ttu-id="5e091-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e091-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e091-136">\<message></span><span class="sxs-lookup"><span data-stu-id="5e091-136">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-ws2007httpbinding.md)|<span data-ttu-id="5e091-137">Define as configurações para a segurança de nível de mensagem.</span><span class="sxs-lookup"><span data-stu-id="5e091-137">Defines the settings for the message-level security.</span></span> <span data-ttu-id="5e091-138">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="5e091-138">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5e091-139">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5e091-139">Parent Elements</span></span>  
  
|<span data-ttu-id="5e091-140">Elemento</span><span class="sxs-lookup"><span data-stu-id="5e091-140">Element</span></span>|<span data-ttu-id="5e091-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e091-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e091-142">\<associação ></span><span class="sxs-lookup"><span data-stu-id="5e091-142">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="5e091-143">Define todos os recursos de associação do [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="5e091-143">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5e091-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e091-144">See Also</span></span>  
 <xref:System.ServiceModel.WSFederationHttpSecurity>  
 <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>  
 [<span data-ttu-id="5e091-145">Como criar um WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="5e091-145">How to: Create a WSFederationHttpBinding</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 [<span data-ttu-id="5e091-146">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="5e091-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="5e091-147">Selecionando um tipo de credencial</span><span class="sxs-lookup"><span data-stu-id="5e091-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="5e091-148">Associações</span><span class="sxs-lookup"><span data-stu-id="5e091-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="5e091-149">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="5e091-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="5e091-150">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="5e091-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="5e091-151">\<associação ></span><span class="sxs-lookup"><span data-stu-id="5e091-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
