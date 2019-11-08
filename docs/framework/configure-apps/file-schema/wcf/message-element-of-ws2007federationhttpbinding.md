---
title: <message> elemento de <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 52cd941d-e230-4c82-8b29-333a7d20eca8
ms.openlocfilehash: dde763687dbc62d6fb342a21a4c614208f28d7e8
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739002"
---
# <a name="message-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="63c45-102">\<elemento de > de mensagem de \<ws2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="63c45-102">\<message> element of \<ws2007FederationHttpBinding></span></span>
<span data-ttu-id="63c45-103">Define as configurações para a segurança em nível de mensagem para o elemento [\<ws2007FederationHttpBinding >](ws2007federationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="63c45-103">Defines settings for the message-level security for the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
<span data-ttu-id="63c45-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="63c45-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="63c45-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="63c45-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="63c45-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="63c45-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="63c45-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ws2007FederationHttpBinding >** ](ws2007federationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="63c45-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007FederationHttpBinding>**](ws2007federationhttpbinding.md)</span></span>\
<span data-ttu-id="63c45-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Binding** ></span><span class="sxs-lookup"><span data-stu-id="63c45-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="63c45-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<security >** ](security-element-of-ws2007federationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="63c45-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-element-of-ws2007federationhttpbinding.md)</span></span>\
<span data-ttu-id="63c45-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**message >**</span><span class="sxs-lookup"><span data-stu-id="63c45-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63c45-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="63c45-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="63c45-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="63c45-112">Attributes and Elements</span></span>  
 <span data-ttu-id="63c45-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="63c45-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="63c45-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="63c45-114">Attributes</span></span>  
  
|<span data-ttu-id="63c45-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="63c45-115">Attribute</span></span>|<span data-ttu-id="63c45-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="63c45-116">Description</span></span>|  
|---------------|-----------------|  
|`algorithmSuite`|<span data-ttu-id="63c45-117">Opcional.</span><span class="sxs-lookup"><span data-stu-id="63c45-117">Optional.</span></span> <span data-ttu-id="63c45-118">Define a criptografia de mensagem, a assinatura e os algoritmos de encapsulamento de chaves.</span><span class="sxs-lookup"><span data-stu-id="63c45-118">Sets the message encryption, signature, and key-wrap algorithms.</span></span> <span data-ttu-id="63c45-119">Os algoritmos e os tamanhos de chave são determinados pela classe <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="63c45-119">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="63c45-120">Esses algoritmos são mapeados para aqueles especificados na especificação do WS-SecurityPolicy (Security Policy Language).</span><span class="sxs-lookup"><span data-stu-id="63c45-120">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="63c45-121">Consulte a tabela a seguir para obter os valores possíveis.</span><span class="sxs-lookup"><span data-stu-id="63c45-121">See the following table for possible values.</span></span> <span data-ttu-id="63c45-122">O valor padrão é Basic256.</span><span class="sxs-lookup"><span data-stu-id="63c45-122">The default value is Basic256.</span></span>|  
|`issuedKeyType`|<span data-ttu-id="63c45-123">Especifica o tipo de chave a ser emitida.</span><span class="sxs-lookup"><span data-stu-id="63c45-123">Specifies the type of key to be issued.</span></span> <span data-ttu-id="63c45-124">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="63c45-124">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="63c45-125">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="63c45-125">-   SymmetricKey</span></span><br /><span data-ttu-id="63c45-126">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="63c45-126">-   PublicKey</span></span><br /><span data-ttu-id="63c45-127">- BearerKey</span><span class="sxs-lookup"><span data-stu-id="63c45-127">-   BearerKey</span></span><br /><br /> <span data-ttu-id="63c45-128">O padrão é SymmetricKey.</span><span class="sxs-lookup"><span data-stu-id="63c45-128">The default is SymmetricKey.</span></span> <span data-ttu-id="63c45-129">Este atributo é do tipo <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="63c45-129">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|`issuedTokenType`|<span data-ttu-id="63c45-130">Um URI que especifica o tipo de token a ser emitido.</span><span class="sxs-lookup"><span data-stu-id="63c45-130">A URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="63c45-131">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="63c45-131">The default is `null`.</span></span>|  
|`negotiateServiceCredential`|<span data-ttu-id="63c45-132">Um valor que especifica se a credencial de serviço deve ser trocada como parte da negociação ou está disponível fora da banda.</span><span class="sxs-lookup"><span data-stu-id="63c45-132">A value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="63c45-133">O padrão é `true`, o que significa que a credencial de serviço é negociada.</span><span class="sxs-lookup"><span data-stu-id="63c45-133">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="63c45-134">Atributo algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="63c45-134">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="63c45-135">Valor</span><span class="sxs-lookup"><span data-stu-id="63c45-135">Value</span></span>|<span data-ttu-id="63c45-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="63c45-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="63c45-137">Basic128</span><span class="sxs-lookup"><span data-stu-id="63c45-137">Basic128</span></span>|<span data-ttu-id="63c45-138">Use criptografia Aes128, SHA1 para síntese de mensagem e rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="63c45-138">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="63c45-139">Basic192</span><span class="sxs-lookup"><span data-stu-id="63c45-139">Basic192</span></span>|<span data-ttu-id="63c45-140">Use a criptografia Aes192, SHA1 para Message Digest, rsa-oaep-mgf1p para quebra automática de chave.</span><span class="sxs-lookup"><span data-stu-id="63c45-140">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="63c45-141">Basic256</span><span class="sxs-lookup"><span data-stu-id="63c45-141">Basic256</span></span>|<span data-ttu-id="63c45-142">Use a criptografia Aes256, SHA1 para Message Digest, rsa-oaep-mgf1p para quebra automática de chave.</span><span class="sxs-lookup"><span data-stu-id="63c45-142">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="63c45-143">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="63c45-143">Basic256Rsa15</span></span>|<span data-ttu-id="63c45-144">Use Aes256 para criptografia de mensagem, SHA1 para Message Digest e Rsa15 para Key Wrap.</span><span class="sxs-lookup"><span data-stu-id="63c45-144">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="63c45-145">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="63c45-145">Basic192Rsa15</span></span>|<span data-ttu-id="63c45-146">Use Aes192 para criptografia de mensagem, SHA1 para Message Digest e Rsa15 para Key Wrap.</span><span class="sxs-lookup"><span data-stu-id="63c45-146">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="63c45-147">TripleDes</span><span class="sxs-lookup"><span data-stu-id="63c45-147">TripleDes</span></span>|<span data-ttu-id="63c45-148">Use a criptografia TripleDes, SHA1 para Message Digest, rsa-oaep-mgf1p para quebra automática de chave.</span><span class="sxs-lookup"><span data-stu-id="63c45-148">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="63c45-149">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="63c45-149">Basic128Rsa15</span></span>|<span data-ttu-id="63c45-150">Use Aes128 para criptografia de mensagem, SHA1 para Message Digest e Rsa15 para Key Wrap.</span><span class="sxs-lookup"><span data-stu-id="63c45-150">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="63c45-151">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="63c45-151">TripleDesRsa15</span></span>|<span data-ttu-id="63c45-152">Use a criptografia TripleDes, SHA1 para síntese de mensagem e Rsa15 para o encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="63c45-152">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="63c45-153">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="63c45-153">Basic128Sha256</span></span>|<span data-ttu-id="63c45-154">Use Aes256 para criptografia de mensagem, SHA256 para síntese de mensagem e rsa-oaep-mgf1p para quebra automática de chave.</span><span class="sxs-lookup"><span data-stu-id="63c45-154">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="63c45-155">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="63c45-155">Basic192Sha256</span></span>|<span data-ttu-id="63c45-156">Use Aes192 para criptografia de mensagem, SHA256 para síntese de mensagem e rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="63c45-156">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="63c45-157">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="63c45-157">Basic256Sha256</span></span>|<span data-ttu-id="63c45-158">Use Aes256 para criptografia de mensagem, SHA256 para síntese de mensagem e rsa-oaep-mgf1p para quebra automática de chave.</span><span class="sxs-lookup"><span data-stu-id="63c45-158">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="63c45-159">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="63c45-159">TripleDesSha256</span></span>|<span data-ttu-id="63c45-160">Use TripleDes para criptografia de mensagem, SHA256 para síntese de mensagem e rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="63c45-160">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="63c45-161">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="63c45-161">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="63c45-162">Use Aes128 para criptografia de mensagem, SHA256 para síntese de mensagem e Rsa15 para quebra de chave.</span><span class="sxs-lookup"><span data-stu-id="63c45-162">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="63c45-163">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="63c45-163">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="63c45-164">Use Aes192 para criptografia de mensagem, SHA256 para síntese de mensagem e Rsa15 para quebra de chave.</span><span class="sxs-lookup"><span data-stu-id="63c45-164">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="63c45-165">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="63c45-165">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="63c45-166">Use Aes256 para criptografia de mensagem, SHA256 para síntese de mensagem e Rsa15 para quebra automática de chave.</span><span class="sxs-lookup"><span data-stu-id="63c45-166">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="63c45-167">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="63c45-167">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="63c45-168">Use TripleDes para criptografia de mensagem, SHA256 para síntese de mensagem e Rsa15 para quebra de chave.</span><span class="sxs-lookup"><span data-stu-id="63c45-168">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="63c45-169">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="63c45-169">Child Elements</span></span>  
  
|<span data-ttu-id="63c45-170">Elemento</span><span class="sxs-lookup"><span data-stu-id="63c45-170">Element</span></span>|<span data-ttu-id="63c45-171">Descrição</span><span class="sxs-lookup"><span data-stu-id="63c45-171">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="63c45-172">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="63c45-172">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="63c45-173">Especifica uma coleção de tipos de declaração para essa associação.</span><span class="sxs-lookup"><span data-stu-id="63c45-173">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="63c45-174">Cada elemento é do tipo <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="63c45-174">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|[<span data-ttu-id="63c45-175">> \<emissor</span><span class="sxs-lookup"><span data-stu-id="63c45-175">\<issuer></span></span>](issuer.md)|<span data-ttu-id="63c45-176">Especifica um ponto de extremidade que emite um token de segurança.</span><span class="sxs-lookup"><span data-stu-id="63c45-176">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="63c45-177">Este elemento é do tipo <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="63c45-177">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|[<span data-ttu-id="63c45-178">\<issuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="63c45-178">\<issuerMetadata></span></span>](issuermetadata.md)|<span data-ttu-id="63c45-179">Especifica o endereço do ponto de extremidade do emissor.</span><span class="sxs-lookup"><span data-stu-id="63c45-179">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="63c45-180">\<tokenRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="63c45-180">\<tokenRequestParameters></span></span>](tokenrequestparameters.md)|<span data-ttu-id="63c45-181">Uma coleção de parâmetros de solicitação de token.</span><span class="sxs-lookup"><span data-stu-id="63c45-181">A collection of token request parameters.</span></span> <span data-ttu-id="63c45-182">Cada parâmetro é um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="63c45-182">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="63c45-183">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="63c45-183">Parent Elements</span></span>  
  
|<span data-ttu-id="63c45-184">Elemento</span><span class="sxs-lookup"><span data-stu-id="63c45-184">Element</span></span>|<span data-ttu-id="63c45-185">Descrição</span><span class="sxs-lookup"><span data-stu-id="63c45-185">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="63c45-186">\<Security ></span><span class="sxs-lookup"><span data-stu-id="63c45-186">\<security></span></span>](security-element-of-ws2007federationhttpbinding.md)|<span data-ttu-id="63c45-187">Define as configurações de segurança para uma associação.</span><span class="sxs-lookup"><span data-stu-id="63c45-187">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="63c45-188">Consulte também</span><span class="sxs-lookup"><span data-stu-id="63c45-188">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="63c45-189">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="63c45-189">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="63c45-190">Associações</span><span class="sxs-lookup"><span data-stu-id="63c45-190">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="63c45-191">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="63c45-191">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="63c45-192">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="63c45-192">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="63c45-193">\<binding ></span><span class="sxs-lookup"><span data-stu-id="63c45-193">\<binding></span></span>](bindings.md)
