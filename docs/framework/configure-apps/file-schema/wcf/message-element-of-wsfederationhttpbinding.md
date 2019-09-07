---
title: <message>elemento de<wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
ms.openlocfilehash: e26e1f94fb38e0654fd0bc9f06c6096a488bccfe
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400280"
---
# <a name="message-element-of-wsfederationhttpbinding"></a><span data-ttu-id="08dd1-102">\<elemento de > de \<mensagem de WSFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="08dd1-102">\<message> element of \<wsFederationHttpBinding></span></span>
<span data-ttu-id="08dd1-103">Define as configurações para a segurança em nível de mensagem para o [ \<> WSFederationHttpBinding](wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="08dd1-103">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
<span data-ttu-id="08dd1-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="08dd1-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="08dd1-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="08dd1-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="08dd1-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="08dd1-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="08dd1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> wsFederationHttpBinding**](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="08dd1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="08dd1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**</span><span class="sxs-lookup"><span data-stu-id="08dd1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="08dd1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de segurança**](security-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="08dd1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="08dd1-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de mensagem**</span><span class="sxs-lookup"><span data-stu-id="08dd1-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08dd1-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="08dd1-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="08dd1-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="08dd1-112">Attributes and Elements</span></span>  
 <span data-ttu-id="08dd1-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="08dd1-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="08dd1-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="08dd1-114">Attributes</span></span>  
  
|<span data-ttu-id="08dd1-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="08dd1-115">Attribute</span></span>|<span data-ttu-id="08dd1-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="08dd1-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="08dd1-117">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="08dd1-117">algorithmSuite</span></span>|<span data-ttu-id="08dd1-118">Define a criptografia de mensagem e os algoritmos de encapsulamento de chaves.</span><span class="sxs-lookup"><span data-stu-id="08dd1-118">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="08dd1-119">Consulte a tabela "atributo algorithmSuite" para obter os valores válidos deste atributo.</span><span class="sxs-lookup"><span data-stu-id="08dd1-119">See the "algorithmSuite attribute" table for valid values of this attribute.</span></span> <span data-ttu-id="08dd1-120">O valor padrão é `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="08dd1-120">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="08dd1-121">Esse atributo é do tipo <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="08dd1-121">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span> <span data-ttu-id="08dd1-122">Esses algoritmos são mapeados para aqueles especificados na especificação do WS-SecurityPolicy (Security Policy Language).</span><span class="sxs-lookup"><span data-stu-id="08dd1-122">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>|  
|<span data-ttu-id="08dd1-123">issuedKeyType</span><span class="sxs-lookup"><span data-stu-id="08dd1-123">issuedKeyType</span></span>|<span data-ttu-id="08dd1-124">Especifica o tipo de chave a ser emitida.</span><span class="sxs-lookup"><span data-stu-id="08dd1-124">Specifies the type of key to be issued.</span></span> <span data-ttu-id="08dd1-125">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="08dd1-125">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="08dd1-126">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="08dd1-126">-   SymmetricKey</span></span><br /><span data-ttu-id="08dd1-127">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="08dd1-127">-   PublicKey</span></span><br /><br /> <span data-ttu-id="08dd1-128">O padrão é `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="08dd1-128">The default is `SymmetricKey`.</span></span> <span data-ttu-id="08dd1-129">Esse atributo é do tipo <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="08dd1-129">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|<span data-ttu-id="08dd1-130">issuedTokenType</span><span class="sxs-lookup"><span data-stu-id="08dd1-130">issuedTokenType</span></span>|<span data-ttu-id="08dd1-131">Uma cadeia de caracteres que contém um URI que especifica o tipo de token a ser emitido.</span><span class="sxs-lookup"><span data-stu-id="08dd1-131">A string that contains a URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="08dd1-132">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="08dd1-132">The default is `null`.</span></span>|  
|<span data-ttu-id="08dd1-133">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="08dd1-133">negotiateServiceCredential</span></span>|<span data-ttu-id="08dd1-134">Um valor booliano que especifica se a credencial de serviço deve ser trocada como parte da negociação ou está disponível fora da banda.</span><span class="sxs-lookup"><span data-stu-id="08dd1-134">A Boolean value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="08dd1-135">O padrão é `true`, o que significa que a credencial de serviço é negociada.</span><span class="sxs-lookup"><span data-stu-id="08dd1-135">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="08dd1-136">Atributo algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="08dd1-136">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="08dd1-137">Valor</span><span class="sxs-lookup"><span data-stu-id="08dd1-137">Value</span></span>|<span data-ttu-id="08dd1-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="08dd1-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="08dd1-139">Basic128</span><span class="sxs-lookup"><span data-stu-id="08dd1-139">Basic128</span></span>|<span data-ttu-id="08dd1-140">Use criptografia Basic128, SHA1 para síntese de mensagem e rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="08dd1-140">Use Basic128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="08dd1-141">Basic192</span><span class="sxs-lookup"><span data-stu-id="08dd1-141">Basic192</span></span>|<span data-ttu-id="08dd1-142">Use a criptografia Basic192, SHA1 para Message Digest, rsa-oaep-mgf1p para quebra automática de chave.</span><span class="sxs-lookup"><span data-stu-id="08dd1-142">Use Basic192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="08dd1-143">Basic256</span><span class="sxs-lookup"><span data-stu-id="08dd1-143">Basic256</span></span>|<span data-ttu-id="08dd1-144">Use a criptografia Basic256, SHA1 para Message Digest, rsa-oaep-mgf1p para quebra automática de chave.</span><span class="sxs-lookup"><span data-stu-id="08dd1-144">Use Basic256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="08dd1-145">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="08dd1-145">Basic256Rsa15</span></span>|<span data-ttu-id="08dd1-146">Use Basic256 para criptografia de mensagem, SHA1 para Message Digest e Rsa15 para Key Wrap.</span><span class="sxs-lookup"><span data-stu-id="08dd1-146">Use Basic256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="08dd1-147">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="08dd1-147">Basic192Rsa15</span></span>|<span data-ttu-id="08dd1-148">Use Basic192 para criptografia de mensagem, SHA1 para Message Digest e Rsa15 para Key Wrap.</span><span class="sxs-lookup"><span data-stu-id="08dd1-148">Use Basic192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="08dd1-149">TripleDes</span><span class="sxs-lookup"><span data-stu-id="08dd1-149">TripleDes</span></span>|<span data-ttu-id="08dd1-150">Use a criptografia TripleDes, SHA1 para Message Digest, rsa-oaep-mgf1p para quebra automática de chave.</span><span class="sxs-lookup"><span data-stu-id="08dd1-150">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="08dd1-151">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="08dd1-151">Basic128Rsa15</span></span>|<span data-ttu-id="08dd1-152">Use Basic128 para criptografia de mensagem, SHA1 para Message Digest e Rsa15 para Key Wrap.</span><span class="sxs-lookup"><span data-stu-id="08dd1-152">Use Basic128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="08dd1-153">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="08dd1-153">TripleDesRsa15</span></span>|<span data-ttu-id="08dd1-154">Use a criptografia TripleDes, SHA1 para síntese de mensagem e Rsa15 para o encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="08dd1-154">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="08dd1-155">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="08dd1-155">Basic128Sha256</span></span>|<span data-ttu-id="08dd1-156">Use Basic128 para criptografia de mensagem, SHA256 para síntese de mensagem e rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="08dd1-156">Use Basic128 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="08dd1-157">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="08dd1-157">Basic192Sha256</span></span>|<span data-ttu-id="08dd1-158">Use Basic192 para criptografia de mensagem, SHA256 para síntese de mensagem e rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="08dd1-158">Use Basic192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="08dd1-159">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="08dd1-159">Basic256Sha256</span></span>|<span data-ttu-id="08dd1-160">Use Basic256 para criptografia de mensagem, SHA256 para síntese de mensagem e rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="08dd1-160">Use Basic256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="08dd1-161">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="08dd1-161">TripleDesSha256</span></span>|<span data-ttu-id="08dd1-162">Use TripleDes para criptografia de mensagem, SHA256 para síntese de mensagem e rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="08dd1-162">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="08dd1-163">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="08dd1-163">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="08dd1-164">Use Basic128 para criptografia de mensagem, SHA256 para síntese de mensagem e Rsa15 para quebra de chave.</span><span class="sxs-lookup"><span data-stu-id="08dd1-164">Use Basic128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="08dd1-165">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="08dd1-165">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="08dd1-166">Use Aes192 para criptografia de mensagem, SHA256 para síntese de mensagem e Rsa15 para quebra de chave.</span><span class="sxs-lookup"><span data-stu-id="08dd1-166">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="08dd1-167">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="08dd1-167">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="08dd1-168">Use Basic256 para criptografia de mensagem, SHA256 para síntese de mensagem e Rsa15 para quebra de chave.</span><span class="sxs-lookup"><span data-stu-id="08dd1-168">Use Basic256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="08dd1-169">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="08dd1-169">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="08dd1-170">Use TripleDes para criptografia de mensagem, SHA256 para síntese de mensagem e Rsa15 para quebra de chave.</span><span class="sxs-lookup"><span data-stu-id="08dd1-170">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="08dd1-171">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="08dd1-171">Child Elements</span></span>  
  
|<span data-ttu-id="08dd1-172">Elemento</span><span class="sxs-lookup"><span data-stu-id="08dd1-172">Element</span></span>|<span data-ttu-id="08dd1-173">Descrição</span><span class="sxs-lookup"><span data-stu-id="08dd1-173">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="08dd1-174">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="08dd1-174">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="08dd1-175">Especifica uma coleção de tipos de declaração para essa associação.</span><span class="sxs-lookup"><span data-stu-id="08dd1-175">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="08dd1-176">Cada elemento é do tipo <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="08dd1-176">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|<span data-ttu-id="08dd1-177">emissor</span><span class="sxs-lookup"><span data-stu-id="08dd1-177">issuer</span></span>|<span data-ttu-id="08dd1-178">Especifica um ponto de extremidade que emite um token de segurança.</span><span class="sxs-lookup"><span data-stu-id="08dd1-178">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="08dd1-179">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="08dd1-179">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|<span data-ttu-id="08dd1-180">issuerMetadata</span><span class="sxs-lookup"><span data-stu-id="08dd1-180">issuerMetadata</span></span>|<span data-ttu-id="08dd1-181">Especifica o endereço do ponto de extremidade do emissor.</span><span class="sxs-lookup"><span data-stu-id="08dd1-181">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="08dd1-182">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="08dd1-182">\<tokenRequestParameters></span></span>](tokenrequestparameters.md)|<span data-ttu-id="08dd1-183">Uma coleção de parâmetros de solicitação de token.</span><span class="sxs-lookup"><span data-stu-id="08dd1-183">A collection of token request parameters.</span></span> <span data-ttu-id="08dd1-184">Cada parâmetro é um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="08dd1-184">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="08dd1-185">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="08dd1-185">Parent Elements</span></span>  
  
|<span data-ttu-id="08dd1-186">Elemento</span><span class="sxs-lookup"><span data-stu-id="08dd1-186">Element</span></span>|<span data-ttu-id="08dd1-187">Descrição</span><span class="sxs-lookup"><span data-stu-id="08dd1-187">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="08dd1-188">\<security></span><span class="sxs-lookup"><span data-stu-id="08dd1-188">\<security></span></span>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="08dd1-189">Define as configurações de segurança para uma associação.</span><span class="sxs-lookup"><span data-stu-id="08dd1-189">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="08dd1-190">Consulte também</span><span class="sxs-lookup"><span data-stu-id="08dd1-190">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="08dd1-191">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="08dd1-191">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="08dd1-192">Associações</span><span class="sxs-lookup"><span data-stu-id="08dd1-192">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="08dd1-193">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="08dd1-193">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="08dd1-194">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="08dd1-194">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="08dd1-195">\<binding></span><span class="sxs-lookup"><span data-stu-id="08dd1-195">\<binding></span></span>](../../../misc/binding.md)
