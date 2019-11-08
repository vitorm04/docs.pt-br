---
title: <message> elemento de <wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
ms.openlocfilehash: 8e0903dd1313e68e2de65730e129079199ebe2f2
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738988"
---
# <a name="message-element-of-wsfederationhttpbinding"></a><span data-ttu-id="3d2cb-102">\<elemento de > de mensagem de \<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="3d2cb-102">\<message> element of \<wsFederationHttpBinding></span></span>
<span data-ttu-id="3d2cb-103">Define as configurações para a segurança em nível de mensagem para o [\<wsFederationHttpBinding >](wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="3d2cb-103">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
<span data-ttu-id="3d2cb-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3d2cb-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3d2cb-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="3d2cb-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="3d2cb-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="3d2cb-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="3d2cb-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="3d2cb-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="3d2cb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Binding** ></span><span class="sxs-lookup"><span data-stu-id="3d2cb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="3d2cb-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<security >** ](security-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="3d2cb-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="3d2cb-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**message >**</span><span class="sxs-lookup"><span data-stu-id="3d2cb-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d2cb-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3d2cb-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3d2cb-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3d2cb-112">Attributes and Elements</span></span>  
 <span data-ttu-id="3d2cb-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3d2cb-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3d2cb-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="3d2cb-114">Attributes</span></span>  
  
|<span data-ttu-id="3d2cb-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="3d2cb-115">Attribute</span></span>|<span data-ttu-id="3d2cb-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="3d2cb-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3d2cb-117">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="3d2cb-117">algorithmSuite</span></span>|<span data-ttu-id="3d2cb-118">Define a criptografia de mensagem e os algoritmos de encapsulamento de chaves.</span><span class="sxs-lookup"><span data-stu-id="3d2cb-118">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="3d2cb-119">Consulte a tabela "atributo algorithmSuite" para obter os valores válidos deste atributo.</span><span class="sxs-lookup"><span data-stu-id="3d2cb-119">See the "algorithmSuite attribute" table for valid values of this attribute.</span></span> <span data-ttu-id="3d2cb-120">O valor padrão é `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="3d2cb-120">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="3d2cb-121">Este atributo é do tipo <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="3d2cb-121">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span> <span data-ttu-id="3d2cb-122">Esses algoritmos são mapeados para aqueles especificados na especificação do WS-SecurityPolicy (Security Policy Language).</span><span class="sxs-lookup"><span data-stu-id="3d2cb-122">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>|  
|<span data-ttu-id="3d2cb-123">issuedKeyType</span><span class="sxs-lookup"><span data-stu-id="3d2cb-123">issuedKeyType</span></span>|<span data-ttu-id="3d2cb-124">Especifica o tipo de chave a ser emitida.</span><span class="sxs-lookup"><span data-stu-id="3d2cb-124">Specifies the type of key to be issued.</span></span> <span data-ttu-id="3d2cb-125">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="3d2cb-125">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3d2cb-126">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="3d2cb-126">-   SymmetricKey</span></span><br /><span data-ttu-id="3d2cb-127">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="3d2cb-127">-   PublicKey</span></span><br /><br /> <span data-ttu-id="3d2cb-128">O padrão é `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="3d2cb-128">The default is `SymmetricKey`.</span></span> <span data-ttu-id="3d2cb-129">Este atributo é do tipo <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="3d2cb-129">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|<span data-ttu-id="3d2cb-130">issuedTokenType</span><span class="sxs-lookup"><span data-stu-id="3d2cb-130">issuedTokenType</span></span>|<span data-ttu-id="3d2cb-131">Uma cadeia de caracteres que contém um URI que especifica o tipo de token a ser emitido.</span><span class="sxs-lookup"><span data-stu-id="3d2cb-131">A string that contains a URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="3d2cb-132">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="3d2cb-132">The default is `null`.</span></span>|  
|<span data-ttu-id="3d2cb-133">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="3d2cb-133">negotiateServiceCredential</span></span>|<span data-ttu-id="3d2cb-134">Um valor booliano que especifica se a credencial de serviço deve ser trocada como parte da negociação ou está disponível fora da banda.</span><span class="sxs-lookup"><span data-stu-id="3d2cb-134">A Boolean value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="3d2cb-135">O padrão é `true`, o que significa que a credencial de serviço é negociada.</span><span class="sxs-lookup"><span data-stu-id="3d2cb-135">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="3d2cb-136">Atributo algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="3d2cb-136">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="3d2cb-137">Valor</span><span class="sxs-lookup"><span data-stu-id="3d2cb-137">Value</span></span>|<span data-ttu-id="3d2cb-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="3d2cb-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3d2cb-139">Basic128</span><span class="sxs-lookup"><span data-stu-id="3d2cb-139">Basic128</span></span>|<span data-ttu-id="3d2cb-140">Use criptografia Basic128, SHA1 para síntese de mensagem e rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="3d2cb-140">Use Basic128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="3d2cb-141">Basic192</span><span class="sxs-lookup"><span data-stu-id="3d2cb-141">Basic192</span></span>|<span data-ttu-id="3d2cb-142">Use a criptografia Basic192, SHA1 para Message Digest, rsa-oaep-mgf1p para quebra automática de chave.</span><span class="sxs-lookup"><span data-stu-id="3d2cb-142">Use Basic192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="3d2cb-143">Basic256</span><span class="sxs-lookup"><span data-stu-id="3d2cb-143">Basic256</span></span>|<span data-ttu-id="3d2cb-144">Use a criptografia Basic256, SHA1 para Message Digest, rsa-oaep-mgf1p para quebra automática de chave.</span><span class="sxs-lookup"><span data-stu-id="3d2cb-144">Use Basic256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="3d2cb-145">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="3d2cb-145">Basic256Rsa15</span></span>|<span data-ttu-id="3d2cb-146">Use Basic256 para criptografia de mensagem, SHA1 para Message Digest e Rsa15 para Key Wrap.</span><span class="sxs-lookup"><span data-stu-id="3d2cb-146">Use Basic256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="3d2cb-147">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="3d2cb-147">Basic192Rsa15</span></span>|<span data-ttu-id="3d2cb-148">Use Basic192 para criptografia de mensagem, SHA1 para Message Digest e Rsa15 para Key Wrap.</span><span class="sxs-lookup"><span data-stu-id="3d2cb-148">Use Basic192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="3d2cb-149">TripleDes</span><span class="sxs-lookup"><span data-stu-id="3d2cb-149">TripleDes</span></span>|<span data-ttu-id="3d2cb-150">Use a criptografia TripleDes, SHA1 para Message Digest, rsa-oaep-mgf1p para quebra automática de chave.</span><span class="sxs-lookup"><span data-stu-id="3d2cb-150">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="3d2cb-151">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="3d2cb-151">Basic128Rsa15</span></span>|<span data-ttu-id="3d2cb-152">Use Basic128 para criptografia de mensagem, SHA1 para Message Digest e Rsa15 para Key Wrap.</span><span class="sxs-lookup"><span data-stu-id="3d2cb-152">Use Basic128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="3d2cb-153">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="3d2cb-153">TripleDesRsa15</span></span>|<span data-ttu-id="3d2cb-154">Use a criptografia TripleDes, SHA1 para síntese de mensagem e Rsa15 para o encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="3d2cb-154">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="3d2cb-155">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="3d2cb-155">Basic128Sha256</span></span>|<span data-ttu-id="3d2cb-156">Use Basic128 para criptografia de mensagem, SHA256 para síntese de mensagem e rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="3d2cb-156">Use Basic128 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="3d2cb-157">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="3d2cb-157">Basic192Sha256</span></span>|<span data-ttu-id="3d2cb-158">Use Basic192 para criptografia de mensagem, SHA256 para síntese de mensagem e rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="3d2cb-158">Use Basic192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="3d2cb-159">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="3d2cb-159">Basic256Sha256</span></span>|<span data-ttu-id="3d2cb-160">Use Basic256 para criptografia de mensagem, SHA256 para síntese de mensagem e rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="3d2cb-160">Use Basic256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="3d2cb-161">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="3d2cb-161">TripleDesSha256</span></span>|<span data-ttu-id="3d2cb-162">Use TripleDes para criptografia de mensagem, SHA256 para síntese de mensagem e rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="3d2cb-162">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="3d2cb-163">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="3d2cb-163">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="3d2cb-164">Use Basic128 para criptografia de mensagem, SHA256 para síntese de mensagem e Rsa15 para quebra de chave.</span><span class="sxs-lookup"><span data-stu-id="3d2cb-164">Use Basic128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="3d2cb-165">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="3d2cb-165">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="3d2cb-166">Use Aes192 para criptografia de mensagem, SHA256 para síntese de mensagem e Rsa15 para quebra de chave.</span><span class="sxs-lookup"><span data-stu-id="3d2cb-166">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="3d2cb-167">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="3d2cb-167">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="3d2cb-168">Use Basic256 para criptografia de mensagem, SHA256 para síntese de mensagem e Rsa15 para quebra de chave.</span><span class="sxs-lookup"><span data-stu-id="3d2cb-168">Use Basic256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="3d2cb-169">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="3d2cb-169">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="3d2cb-170">Use TripleDes para criptografia de mensagem, SHA256 para síntese de mensagem e Rsa15 para quebra de chave.</span><span class="sxs-lookup"><span data-stu-id="3d2cb-170">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3d2cb-171">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3d2cb-171">Child Elements</span></span>  
  
|<span data-ttu-id="3d2cb-172">Elemento</span><span class="sxs-lookup"><span data-stu-id="3d2cb-172">Element</span></span>|<span data-ttu-id="3d2cb-173">Descrição</span><span class="sxs-lookup"><span data-stu-id="3d2cb-173">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3d2cb-174">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="3d2cb-174">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="3d2cb-175">Especifica uma coleção de tipos de declaração para essa associação.</span><span class="sxs-lookup"><span data-stu-id="3d2cb-175">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="3d2cb-176">Cada elemento é do tipo <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="3d2cb-176">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|<span data-ttu-id="3d2cb-177">emissor</span><span class="sxs-lookup"><span data-stu-id="3d2cb-177">issuer</span></span>|<span data-ttu-id="3d2cb-178">Especifica um ponto de extremidade que emite um token de segurança.</span><span class="sxs-lookup"><span data-stu-id="3d2cb-178">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="3d2cb-179">Este elemento é do tipo <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="3d2cb-179">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|<span data-ttu-id="3d2cb-180">issuerMetadata</span><span class="sxs-lookup"><span data-stu-id="3d2cb-180">issuerMetadata</span></span>|<span data-ttu-id="3d2cb-181">Especifica o endereço do ponto de extremidade do emissor.</span><span class="sxs-lookup"><span data-stu-id="3d2cb-181">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="3d2cb-182">\<tokenRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="3d2cb-182">\<tokenRequestParameters></span></span>](tokenrequestparameters.md)|<span data-ttu-id="3d2cb-183">Uma coleção de parâmetros de solicitação de token.</span><span class="sxs-lookup"><span data-stu-id="3d2cb-183">A collection of token request parameters.</span></span> <span data-ttu-id="3d2cb-184">Cada parâmetro é um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="3d2cb-184">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3d2cb-185">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3d2cb-185">Parent Elements</span></span>  
  
|<span data-ttu-id="3d2cb-186">Elemento</span><span class="sxs-lookup"><span data-stu-id="3d2cb-186">Element</span></span>|<span data-ttu-id="3d2cb-187">Descrição</span><span class="sxs-lookup"><span data-stu-id="3d2cb-187">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3d2cb-188">\<Security ></span><span class="sxs-lookup"><span data-stu-id="3d2cb-188">\<security></span></span>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="3d2cb-189">Define as configurações de segurança para uma associação.</span><span class="sxs-lookup"><span data-stu-id="3d2cb-189">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3d2cb-190">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3d2cb-190">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="3d2cb-191">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="3d2cb-191">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="3d2cb-192">Associações</span><span class="sxs-lookup"><span data-stu-id="3d2cb-192">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3d2cb-193">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="3d2cb-193">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="3d2cb-194">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="3d2cb-194">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="3d2cb-195">\<binding ></span><span class="sxs-lookup"><span data-stu-id="3d2cb-195">\<binding></span></span>](bindings.md)
