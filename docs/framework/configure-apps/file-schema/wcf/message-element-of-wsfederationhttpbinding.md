---
title: <message>elemento de<wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
ms.openlocfilehash: 4730d7e573eefdfcd5704621d0a7ccaa15f76d3a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931586"
---
# <a name="message-element-of-wsfederationhttpbinding"></a><span data-ttu-id="61ea9-102">\<elemento de > de \<mensagem de WSFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="61ea9-102">\<message> element of \<wsFederationHttpBinding></span></span>
<span data-ttu-id="61ea9-103">Define as configurações para a segurança em nível de mensagem para o [ \<> WSFederationHttpBinding](wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="61ea9-103">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="61ea9-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="61ea9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="61ea9-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="61ea9-105">\<bindings></span></span>  
<span data-ttu-id="61ea9-106">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="61ea9-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="61ea9-107">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="61ea9-107">\<binding></span></span>  
<span data-ttu-id="61ea9-108">\<> de segurança</span><span class="sxs-lookup"><span data-stu-id="61ea9-108">\<security></span></span>  
<span data-ttu-id="61ea9-109">\<message></span><span class="sxs-lookup"><span data-stu-id="61ea9-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61ea9-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="61ea9-110">Syntax</span></span>  
  
```xml  
<wsFederationBinding>
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
</wsFederationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="61ea9-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="61ea9-111">Attributes and Elements</span></span>  
 <span data-ttu-id="61ea9-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="61ea9-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="61ea9-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="61ea9-113">Attributes</span></span>  
  
|<span data-ttu-id="61ea9-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="61ea9-114">Attribute</span></span>|<span data-ttu-id="61ea9-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="61ea9-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="61ea9-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="61ea9-116">algorithmSuite</span></span>|<span data-ttu-id="61ea9-117">Define a criptografia de mensagem e os algoritmos de encapsulamento de chaves.</span><span class="sxs-lookup"><span data-stu-id="61ea9-117">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="61ea9-118">Consulte a tabela "atributo algorithmSuite" para obter os valores válidos deste atributo.</span><span class="sxs-lookup"><span data-stu-id="61ea9-118">See the "algorithmSuite attribute" table for valid values of this attribute.</span></span> <span data-ttu-id="61ea9-119">O valor padrão é `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="61ea9-119">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="61ea9-120">Esse atributo é do tipo <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="61ea9-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span> <span data-ttu-id="61ea9-121">Esses algoritmos são mapeados para aqueles especificados na especificação do WS-SecurityPolicy (Security Policy Language).</span><span class="sxs-lookup"><span data-stu-id="61ea9-121">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>|  
|<span data-ttu-id="61ea9-122">issuedKeyType</span><span class="sxs-lookup"><span data-stu-id="61ea9-122">issuedKeyType</span></span>|<span data-ttu-id="61ea9-123">Especifica o tipo de chave a ser emitida.</span><span class="sxs-lookup"><span data-stu-id="61ea9-123">Specifies the type of key to be issued.</span></span> <span data-ttu-id="61ea9-124">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="61ea9-124">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="61ea9-125">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="61ea9-125">-   SymmetricKey</span></span><br /><span data-ttu-id="61ea9-126">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="61ea9-126">-   PublicKey</span></span><br /><br /> <span data-ttu-id="61ea9-127">O padrão é `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="61ea9-127">The default is `SymmetricKey`.</span></span> <span data-ttu-id="61ea9-128">Esse atributo é do tipo <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="61ea9-128">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|<span data-ttu-id="61ea9-129">issuedTokenType</span><span class="sxs-lookup"><span data-stu-id="61ea9-129">issuedTokenType</span></span>|<span data-ttu-id="61ea9-130">Uma cadeia de caracteres que contém um URI que especifica o tipo de token a ser emitido.</span><span class="sxs-lookup"><span data-stu-id="61ea9-130">A string that contains a URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="61ea9-131">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="61ea9-131">The default is `null`.</span></span>|  
|<span data-ttu-id="61ea9-132">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="61ea9-132">negotiateServiceCredential</span></span>|<span data-ttu-id="61ea9-133">Um valor booliano que especifica se a credencial de serviço deve ser trocada como parte da negociação ou está disponível fora da banda.</span><span class="sxs-lookup"><span data-stu-id="61ea9-133">A Boolean value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="61ea9-134">O padrão é `true`, o que significa que a credencial de serviço é negociada.</span><span class="sxs-lookup"><span data-stu-id="61ea9-134">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="61ea9-135">Atributo algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="61ea9-135">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="61ea9-136">Valor</span><span class="sxs-lookup"><span data-stu-id="61ea9-136">Value</span></span>|<span data-ttu-id="61ea9-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="61ea9-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="61ea9-138">Basic128</span><span class="sxs-lookup"><span data-stu-id="61ea9-138">Basic128</span></span>|<span data-ttu-id="61ea9-139">Use criptografia Basic128, SHA1 para síntese de mensagem e rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="61ea9-139">Use Basic128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="61ea9-140">Basic192</span><span class="sxs-lookup"><span data-stu-id="61ea9-140">Basic192</span></span>|<span data-ttu-id="61ea9-141">Use a criptografia Basic192, SHA1 para Message Digest, rsa-oaep-mgf1p para quebra automática de chave.</span><span class="sxs-lookup"><span data-stu-id="61ea9-141">Use Basic192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="61ea9-142">Basic256</span><span class="sxs-lookup"><span data-stu-id="61ea9-142">Basic256</span></span>|<span data-ttu-id="61ea9-143">Use a criptografia Basic256, SHA1 para Message Digest, rsa-oaep-mgf1p para quebra automática de chave.</span><span class="sxs-lookup"><span data-stu-id="61ea9-143">Use Basic256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="61ea9-144">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="61ea9-144">Basic256Rsa15</span></span>|<span data-ttu-id="61ea9-145">Use Basic256 para criptografia de mensagem, SHA1 para Message Digest e Rsa15 para Key Wrap.</span><span class="sxs-lookup"><span data-stu-id="61ea9-145">Use Basic256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="61ea9-146">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="61ea9-146">Basic192Rsa15</span></span>|<span data-ttu-id="61ea9-147">Use Basic192 para criptografia de mensagem, SHA1 para Message Digest e Rsa15 para Key Wrap.</span><span class="sxs-lookup"><span data-stu-id="61ea9-147">Use Basic192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="61ea9-148">TripleDes</span><span class="sxs-lookup"><span data-stu-id="61ea9-148">TripleDes</span></span>|<span data-ttu-id="61ea9-149">Use a criptografia TripleDes, SHA1 para Message Digest, rsa-oaep-mgf1p para quebra automática de chave.</span><span class="sxs-lookup"><span data-stu-id="61ea9-149">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="61ea9-150">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="61ea9-150">Basic128Rsa15</span></span>|<span data-ttu-id="61ea9-151">Use Basic128 para criptografia de mensagem, SHA1 para Message Digest e Rsa15 para Key Wrap.</span><span class="sxs-lookup"><span data-stu-id="61ea9-151">Use Basic128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="61ea9-152">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="61ea9-152">TripleDesRsa15</span></span>|<span data-ttu-id="61ea9-153">Use a criptografia TripleDes, SHA1 para síntese de mensagem e Rsa15 para o encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="61ea9-153">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="61ea9-154">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="61ea9-154">Basic128Sha256</span></span>|<span data-ttu-id="61ea9-155">Use Basic128 para criptografia de mensagem, SHA256 para síntese de mensagem e rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="61ea9-155">Use Basic128 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="61ea9-156">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="61ea9-156">Basic192Sha256</span></span>|<span data-ttu-id="61ea9-157">Use Basic192 para criptografia de mensagem, SHA256 para síntese de mensagem e rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="61ea9-157">Use Basic192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="61ea9-158">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="61ea9-158">Basic256Sha256</span></span>|<span data-ttu-id="61ea9-159">Use Basic256 para criptografia de mensagem, SHA256 para síntese de mensagem e rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="61ea9-159">Use Basic256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="61ea9-160">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="61ea9-160">TripleDesSha256</span></span>|<span data-ttu-id="61ea9-161">Use TripleDes para criptografia de mensagem, SHA256 para síntese de mensagem e rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="61ea9-161">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="61ea9-162">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="61ea9-162">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="61ea9-163">Use Basic128 para criptografia de mensagem, SHA256 para síntese de mensagem e Rsa15 para quebra de chave.</span><span class="sxs-lookup"><span data-stu-id="61ea9-163">Use Basic128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="61ea9-164">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="61ea9-164">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="61ea9-165">Use Aes192 para criptografia de mensagem, SHA256 para síntese de mensagem e Rsa15 para quebra de chave.</span><span class="sxs-lookup"><span data-stu-id="61ea9-165">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="61ea9-166">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="61ea9-166">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="61ea9-167">Use Basic256 para criptografia de mensagem, SHA256 para síntese de mensagem e Rsa15 para quebra de chave.</span><span class="sxs-lookup"><span data-stu-id="61ea9-167">Use Basic256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="61ea9-168">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="61ea9-168">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="61ea9-169">Use TripleDes para criptografia de mensagem, SHA256 para síntese de mensagem e Rsa15 para quebra de chave.</span><span class="sxs-lookup"><span data-stu-id="61ea9-169">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="61ea9-170">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="61ea9-170">Child Elements</span></span>  
  
|<span data-ttu-id="61ea9-171">Elemento</span><span class="sxs-lookup"><span data-stu-id="61ea9-171">Element</span></span>|<span data-ttu-id="61ea9-172">Descrição</span><span class="sxs-lookup"><span data-stu-id="61ea9-172">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="61ea9-173">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="61ea9-173">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="61ea9-174">Especifica uma coleção de tipos de declaração para essa associação.</span><span class="sxs-lookup"><span data-stu-id="61ea9-174">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="61ea9-175">Cada elemento é do tipo <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="61ea9-175">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|<span data-ttu-id="61ea9-176">emissor</span><span class="sxs-lookup"><span data-stu-id="61ea9-176">issuer</span></span>|<span data-ttu-id="61ea9-177">Especifica um ponto de extremidade que emite um token de segurança.</span><span class="sxs-lookup"><span data-stu-id="61ea9-177">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="61ea9-178">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="61ea9-178">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|<span data-ttu-id="61ea9-179">issuerMetadata</span><span class="sxs-lookup"><span data-stu-id="61ea9-179">issuerMetadata</span></span>|<span data-ttu-id="61ea9-180">Especifica o endereço do ponto de extremidade do emissor.</span><span class="sxs-lookup"><span data-stu-id="61ea9-180">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="61ea9-181">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="61ea9-181">\<tokenRequestParameters></span></span>](tokenrequestparameters.md)|<span data-ttu-id="61ea9-182">Uma coleção de parâmetros de solicitação de token.</span><span class="sxs-lookup"><span data-stu-id="61ea9-182">A collection of token request parameters.</span></span> <span data-ttu-id="61ea9-183">Cada parâmetro é um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="61ea9-183">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="61ea9-184">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="61ea9-184">Parent Elements</span></span>  
  
|<span data-ttu-id="61ea9-185">Elemento</span><span class="sxs-lookup"><span data-stu-id="61ea9-185">Element</span></span>|<span data-ttu-id="61ea9-186">Descrição</span><span class="sxs-lookup"><span data-stu-id="61ea9-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="61ea9-187">\<security></span><span class="sxs-lookup"><span data-stu-id="61ea9-187">\<security></span></span>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="61ea9-188">Define as configurações de segurança para uma associação.</span><span class="sxs-lookup"><span data-stu-id="61ea9-188">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="61ea9-189">Consulte também</span><span class="sxs-lookup"><span data-stu-id="61ea9-189">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="61ea9-190">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="61ea9-190">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="61ea9-191">Associações</span><span class="sxs-lookup"><span data-stu-id="61ea9-191">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="61ea9-192">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="61ea9-192">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="61ea9-193">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="61ea9-193">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="61ea9-194">\<binding></span><span class="sxs-lookup"><span data-stu-id="61ea9-194">\<binding></span></span>](../../../misc/binding.md)
