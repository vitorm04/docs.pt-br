---
title: <security> elemento de <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 826219b4-3a16-45fc-832d-0cd7cbbd3b84
ms.openlocfilehash: 15740144b0aad7eb2798db4712e4769d08d893a6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186856"
---
# <a name="security-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="d29da-102">\<segurança > elemento \<ws2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="d29da-102">\<security> element of \<ws2007FederationHttpBinding></span></span>
<span data-ttu-id="d29da-103">Define as configurações de segurança de [ \<ws2007FederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="d29da-103">Defines the security settings of the [\<ws2007FederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) element.</span></span>  
  
 <span data-ttu-id="d29da-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d29da-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d29da-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="d29da-105">\<bindings></span></span>  
<span data-ttu-id="d29da-106">\<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="d29da-106">\<ws2007FederationHttpBinding></span></span>  
<span data-ttu-id="d29da-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="d29da-107">\<binding></span></span>  
<span data-ttu-id="d29da-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="d29da-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d29da-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d29da-109">Syntax</span></span>  
  
```xml  
<ws2007FederationBinding>
  <binding>
    <security mode="None/Message/TransportWithMessageCredential">
      <message negotiateServiceCredential="Boolean"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/  Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               defaultProtectionLevel="none/sign/EncryptAndSign"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey">
      </message>
    </security>
  </binding>
</ws2007FederationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d29da-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d29da-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d29da-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d29da-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d29da-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="d29da-112">Attributes</span></span>  
  
|<span data-ttu-id="d29da-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="d29da-113">Attribute</span></span>|<span data-ttu-id="d29da-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="d29da-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="d29da-115">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d29da-115">Optional.</span></span> <span data-ttu-id="d29da-116">Especifica o tipo de segurança que é aplicado.</span><span class="sxs-lookup"><span data-stu-id="d29da-116">Specifies the type of security that is applied.</span></span> <span data-ttu-id="d29da-117">O valor padrão é `Message`.</span><span class="sxs-lookup"><span data-stu-id="d29da-117">The default value is `Message`.</span></span> <span data-ttu-id="d29da-118">Esse atributo é do tipo <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="d29da-118">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="d29da-119">modo de atributo</span><span class="sxs-lookup"><span data-stu-id="d29da-119">mode Attribute</span></span>  
  
|<span data-ttu-id="d29da-120">Valor</span><span class="sxs-lookup"><span data-stu-id="d29da-120">Value</span></span>|<span data-ttu-id="d29da-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="d29da-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d29da-122">Nenhum</span><span class="sxs-lookup"><span data-stu-id="d29da-122">None</span></span>|<span data-ttu-id="d29da-123">A mensagem SOAP não é segura durante a transferência.</span><span class="sxs-lookup"><span data-stu-id="d29da-123">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="d29da-124">Mensagem</span><span class="sxs-lookup"><span data-stu-id="d29da-124">Message</span></span>|<span data-ttu-id="d29da-125">São fornecidos os serviços de integridade, confidencialidade, autenticação de servidor e autenticação de cliente usando a segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="d29da-125">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="d29da-126">Por padrão, o corpo é criptografado e assinado.</span><span class="sxs-lookup"><span data-stu-id="d29da-126">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="d29da-127">O serviço deve ser configurado com um certificado.</span><span class="sxs-lookup"><span data-stu-id="d29da-127">The service must be configured with a certificate.</span></span> <span data-ttu-id="d29da-128">A autenticação de cliente baseia-se no token emitido ao cliente por um serviço de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="d29da-128">Client authentication is based on the token issued to the client by a security token service.</span></span>|  
|<span data-ttu-id="d29da-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="d29da-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="d29da-130">A integridade, a confidencialidade e a autenticação de servidor são fornecidas por HTTPS.</span><span class="sxs-lookup"><span data-stu-id="d29da-130">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="d29da-131">O serviço deve ser configurado com um certificado.</span><span class="sxs-lookup"><span data-stu-id="d29da-131">The service must be configured with a certificate.</span></span> <span data-ttu-id="d29da-132">A autenticação de cliente é fornecida por meio de segurança de mensagens SOAP e é baseada no token emitido ao cliente por um serviço de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="d29da-132">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d29da-133">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d29da-133">Child Elements</span></span>  
  
|<span data-ttu-id="d29da-134">Elemento</span><span class="sxs-lookup"><span data-stu-id="d29da-134">Element</span></span>|<span data-ttu-id="d29da-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="d29da-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d29da-136">\<message></span><span class="sxs-lookup"><span data-stu-id="d29da-136">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-ws2007httpbinding.md)|<span data-ttu-id="d29da-137">Define as configurações para a segurança de nível de mensagem.</span><span class="sxs-lookup"><span data-stu-id="d29da-137">Defines the settings for the message-level security.</span></span> <span data-ttu-id="d29da-138">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="d29da-138">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d29da-139">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d29da-139">Parent Elements</span></span>  
  
|<span data-ttu-id="d29da-140">Elemento</span><span class="sxs-lookup"><span data-stu-id="d29da-140">Element</span></span>|<span data-ttu-id="d29da-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="d29da-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d29da-142">\<binding></span><span class="sxs-lookup"><span data-stu-id="d29da-142">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="d29da-143">Define todos os recursos de associação do [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="d29da-143">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d29da-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d29da-144">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="d29da-145">Como: Criar um WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="d29da-145">How to: Create a WSFederationHttpBinding</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="d29da-146">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="d29da-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="d29da-147">Selecionando um tipo de credencial</span><span class="sxs-lookup"><span data-stu-id="d29da-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="d29da-148">Associações</span><span class="sxs-lookup"><span data-stu-id="d29da-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="d29da-149">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="d29da-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d29da-150">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="d29da-150">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="d29da-151">\<binding></span><span class="sxs-lookup"><span data-stu-id="d29da-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
