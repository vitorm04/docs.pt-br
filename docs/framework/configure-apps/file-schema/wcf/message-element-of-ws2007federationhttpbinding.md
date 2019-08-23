---
title: <message>elemento de<ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 52cd941d-e230-4c82-8b29-333a7d20eca8
ms.openlocfilehash: 4340727026cb151f2efe813dfa005c1c5a1908be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931617"
---
# <a name="message-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="be3a3-102">\<elemento de > de \<mensagem de ws2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="be3a3-102">\<message> element of \<ws2007FederationHttpBinding></span></span>
<span data-ttu-id="be3a3-103">Define as configurações para a segurança em nível de mensagem [ \<](ws2007federationhttpbinding.md) para o elemento de > ws2007FederationHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="be3a3-103">Defines settings for the message-level security for the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
 <span data-ttu-id="be3a3-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="be3a3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="be3a3-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="be3a3-105">\<bindings></span></span>  
<span data-ttu-id="be3a3-106">\<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="be3a3-106">\<ws2007FederationHttpBinding></span></span>  
<span data-ttu-id="be3a3-107">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="be3a3-107">\<binding></span></span>  
<span data-ttu-id="be3a3-108">\<> de segurança</span><span class="sxs-lookup"><span data-stu-id="be3a3-108">\<security></span></span>  
<span data-ttu-id="be3a3-109">\<message></span><span class="sxs-lookup"><span data-stu-id="be3a3-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be3a3-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="be3a3-110">Syntax</span></span>  
  
```xml  
<ws2007FederationBinding>
  <binding>
    <security>
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey"
               negotiateServiceCredential="Boolean">
        <claimTypeRequirements>
          <add claimType="URI"
               isOptional="Boolean" />
        </claimTypeRequirements>
        <issuer address="Uri">
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  x509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuer>
        <issuerMetadata address="String">
          <headers>
            <add name="String"
                 namespace="String" />
          </headers>
          <identity>
            <certificate encodedValue="String" />
            <certificateReference findValue="String"
                                  isChainIncluded="Boolean"
                                  storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                                  storeLocation="LocalMachine/CurrentUser"
                                  X509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuerMetadata>
        <tokenRequestParameters>
          <xmlElement>
          </xmlElement>
        </tokenRequestParameters>
      </message>
    </security>
  </binding>
</ws2007FederationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="be3a3-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="be3a3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="be3a3-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="be3a3-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="be3a3-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="be3a3-113">Attributes</span></span>  
  
|<span data-ttu-id="be3a3-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="be3a3-114">Attribute</span></span>|<span data-ttu-id="be3a3-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="be3a3-115">Description</span></span>|  
|---------------|-----------------|  
|`algorithmSuite`|<span data-ttu-id="be3a3-116">Opcional.</span><span class="sxs-lookup"><span data-stu-id="be3a3-116">Optional.</span></span> <span data-ttu-id="be3a3-117">Define a criptografia de mensagem, a assinatura e os algoritmos de encapsulamento de chaves.</span><span class="sxs-lookup"><span data-stu-id="be3a3-117">Sets the message encryption, signature, and key-wrap algorithms.</span></span> <span data-ttu-id="be3a3-118">Os algoritmos e os tamanhos de chave são determinados <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> pela classe.</span><span class="sxs-lookup"><span data-stu-id="be3a3-118">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="be3a3-119">Esses algoritmos são mapeados para aqueles especificados na especificação do WS-SecurityPolicy (Security Policy Language).</span><span class="sxs-lookup"><span data-stu-id="be3a3-119">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="be3a3-120">Consulte a tabela a seguir para obter os valores possíveis.</span><span class="sxs-lookup"><span data-stu-id="be3a3-120">See the following table for possible values.</span></span> <span data-ttu-id="be3a3-121">O valor padrão é Basic256.</span><span class="sxs-lookup"><span data-stu-id="be3a3-121">The default value is Basic256.</span></span>|  
|`issuedKeyType`|<span data-ttu-id="be3a3-122">Especifica o tipo de chave a ser emitida.</span><span class="sxs-lookup"><span data-stu-id="be3a3-122">Specifies the type of key to be issued.</span></span> <span data-ttu-id="be3a3-123">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="be3a3-123">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="be3a3-124">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="be3a3-124">-   SymmetricKey</span></span><br /><span data-ttu-id="be3a3-125">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="be3a3-125">-   PublicKey</span></span><br /><span data-ttu-id="be3a3-126">- BearerKey</span><span class="sxs-lookup"><span data-stu-id="be3a3-126">-   BearerKey</span></span><br /><br /> <span data-ttu-id="be3a3-127">O padrão é SymmetricKey.</span><span class="sxs-lookup"><span data-stu-id="be3a3-127">The default is SymmetricKey.</span></span> <span data-ttu-id="be3a3-128">Esse atributo é do tipo <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="be3a3-128">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|`issuedTokenType`|<span data-ttu-id="be3a3-129">Um URI que especifica o tipo de token a ser emitido.</span><span class="sxs-lookup"><span data-stu-id="be3a3-129">A URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="be3a3-130">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="be3a3-130">The default is `null`.</span></span>|  
|`negotiateServiceCredential`|<span data-ttu-id="be3a3-131">Um valor que especifica se a credencial de serviço deve ser trocada como parte da negociação ou está disponível fora da banda.</span><span class="sxs-lookup"><span data-stu-id="be3a3-131">A value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="be3a3-132">O padrão é `true`, o que significa que a credencial de serviço é negociada.</span><span class="sxs-lookup"><span data-stu-id="be3a3-132">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="be3a3-133">Atributo algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="be3a3-133">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="be3a3-134">Valor</span><span class="sxs-lookup"><span data-stu-id="be3a3-134">Value</span></span>|<span data-ttu-id="be3a3-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="be3a3-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="be3a3-136">Basic128</span><span class="sxs-lookup"><span data-stu-id="be3a3-136">Basic128</span></span>|<span data-ttu-id="be3a3-137">Use criptografia Aes128, SHA1 para síntese de mensagem e rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="be3a3-137">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="be3a3-138">Basic192</span><span class="sxs-lookup"><span data-stu-id="be3a3-138">Basic192</span></span>|<span data-ttu-id="be3a3-139">Use a criptografia Aes192, SHA1 para Message Digest, rsa-oaep-mgf1p para quebra automática de chave.</span><span class="sxs-lookup"><span data-stu-id="be3a3-139">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="be3a3-140">Basic256</span><span class="sxs-lookup"><span data-stu-id="be3a3-140">Basic256</span></span>|<span data-ttu-id="be3a3-141">Use a criptografia Aes256, SHA1 para Message Digest, rsa-oaep-mgf1p para quebra automática de chave.</span><span class="sxs-lookup"><span data-stu-id="be3a3-141">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="be3a3-142">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="be3a3-142">Basic256Rsa15</span></span>|<span data-ttu-id="be3a3-143">Use Aes256 para criptografia de mensagem, SHA1 para Message Digest e Rsa15 para Key Wrap.</span><span class="sxs-lookup"><span data-stu-id="be3a3-143">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="be3a3-144">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="be3a3-144">Basic192Rsa15</span></span>|<span data-ttu-id="be3a3-145">Use Aes192 para criptografia de mensagem, SHA1 para Message Digest e Rsa15 para Key Wrap.</span><span class="sxs-lookup"><span data-stu-id="be3a3-145">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="be3a3-146">TripleDes</span><span class="sxs-lookup"><span data-stu-id="be3a3-146">TripleDes</span></span>|<span data-ttu-id="be3a3-147">Use a criptografia TripleDes, SHA1 para Message Digest, rsa-oaep-mgf1p para quebra automática de chave.</span><span class="sxs-lookup"><span data-stu-id="be3a3-147">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="be3a3-148">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="be3a3-148">Basic128Rsa15</span></span>|<span data-ttu-id="be3a3-149">Use Aes128 para criptografia de mensagem, SHA1 para Message Digest e Rsa15 para Key Wrap.</span><span class="sxs-lookup"><span data-stu-id="be3a3-149">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="be3a3-150">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="be3a3-150">TripleDesRsa15</span></span>|<span data-ttu-id="be3a3-151">Use a criptografia TripleDes, SHA1 para síntese de mensagem e Rsa15 para o encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="be3a3-151">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="be3a3-152">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="be3a3-152">Basic128Sha256</span></span>|<span data-ttu-id="be3a3-153">Use Aes256 para criptografia de mensagem, SHA256 para síntese de mensagem e rsa-oaep-mgf1p para quebra automática de chave.</span><span class="sxs-lookup"><span data-stu-id="be3a3-153">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="be3a3-154">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="be3a3-154">Basic192Sha256</span></span>|<span data-ttu-id="be3a3-155">Use Aes192 para criptografia de mensagem, SHA256 para síntese de mensagem e rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="be3a3-155">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="be3a3-156">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="be3a3-156">Basic256Sha256</span></span>|<span data-ttu-id="be3a3-157">Use Aes256 para criptografia de mensagem, SHA256 para síntese de mensagem e rsa-oaep-mgf1p para quebra automática de chave.</span><span class="sxs-lookup"><span data-stu-id="be3a3-157">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="be3a3-158">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="be3a3-158">TripleDesSha256</span></span>|<span data-ttu-id="be3a3-159">Use TripleDes para criptografia de mensagem, SHA256 para síntese de mensagem e rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="be3a3-159">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="be3a3-160">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="be3a3-160">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="be3a3-161">Use Aes128 para criptografia de mensagem, SHA256 para síntese de mensagem e Rsa15 para quebra de chave.</span><span class="sxs-lookup"><span data-stu-id="be3a3-161">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="be3a3-162">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="be3a3-162">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="be3a3-163">Use Aes192 para criptografia de mensagem, SHA256 para síntese de mensagem e Rsa15 para quebra de chave.</span><span class="sxs-lookup"><span data-stu-id="be3a3-163">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="be3a3-164">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="be3a3-164">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="be3a3-165">Use Aes256 para criptografia de mensagem, SHA256 para síntese de mensagem e Rsa15 para quebra automática de chave.</span><span class="sxs-lookup"><span data-stu-id="be3a3-165">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="be3a3-166">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="be3a3-166">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="be3a3-167">Use TripleDes para criptografia de mensagem, SHA256 para síntese de mensagem e Rsa15 para quebra de chave.</span><span class="sxs-lookup"><span data-stu-id="be3a3-167">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="be3a3-168">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="be3a3-168">Child Elements</span></span>  
  
|<span data-ttu-id="be3a3-169">Elemento</span><span class="sxs-lookup"><span data-stu-id="be3a3-169">Element</span></span>|<span data-ttu-id="be3a3-170">Descrição</span><span class="sxs-lookup"><span data-stu-id="be3a3-170">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="be3a3-171">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="be3a3-171">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="be3a3-172">Especifica uma coleção de tipos de declaração para essa associação.</span><span class="sxs-lookup"><span data-stu-id="be3a3-172">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="be3a3-173">Cada elemento é do tipo <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="be3a3-173">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|[<span data-ttu-id="be3a3-174">\<issuer></span><span class="sxs-lookup"><span data-stu-id="be3a3-174">\<issuer></span></span>](issuer.md)|<span data-ttu-id="be3a3-175">Especifica um ponto de extremidade que emite um token de segurança.</span><span class="sxs-lookup"><span data-stu-id="be3a3-175">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="be3a3-176">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="be3a3-176">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|[<span data-ttu-id="be3a3-177">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="be3a3-177">\<issuerMetadata></span></span>](issuermetadata.md)|<span data-ttu-id="be3a3-178">Especifica o endereço do ponto de extremidade do emissor.</span><span class="sxs-lookup"><span data-stu-id="be3a3-178">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="be3a3-179">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="be3a3-179">\<tokenRequestParameters></span></span>](tokenrequestparameters.md)|<span data-ttu-id="be3a3-180">Uma coleção de parâmetros de solicitação de token.</span><span class="sxs-lookup"><span data-stu-id="be3a3-180">A collection of token request parameters.</span></span> <span data-ttu-id="be3a3-181">Cada parâmetro é um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="be3a3-181">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="be3a3-182">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="be3a3-182">Parent Elements</span></span>  
  
|<span data-ttu-id="be3a3-183">Elemento</span><span class="sxs-lookup"><span data-stu-id="be3a3-183">Element</span></span>|<span data-ttu-id="be3a3-184">Descrição</span><span class="sxs-lookup"><span data-stu-id="be3a3-184">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="be3a3-185">\<security></span><span class="sxs-lookup"><span data-stu-id="be3a3-185">\<security></span></span>](security-element-of-ws2007federationhttpbinding.md)|<span data-ttu-id="be3a3-186">Define as configurações de segurança para uma associação.</span><span class="sxs-lookup"><span data-stu-id="be3a3-186">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="be3a3-187">Consulte também</span><span class="sxs-lookup"><span data-stu-id="be3a3-187">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="be3a3-188">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="be3a3-188">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="be3a3-189">Associações</span><span class="sxs-lookup"><span data-stu-id="be3a3-189">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="be3a3-190">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="be3a3-190">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="be3a3-191">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="be3a3-191">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="be3a3-192">\<binding></span><span class="sxs-lookup"><span data-stu-id="be3a3-192">\<binding></span></span>](../../../misc/binding.md)
