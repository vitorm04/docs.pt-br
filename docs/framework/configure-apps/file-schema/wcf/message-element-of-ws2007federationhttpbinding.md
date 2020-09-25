---
title: <message> elemento de <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 52cd941d-e230-4c82-8b29-333a7d20eca8
ms.openlocfilehash: d71bce5e94568bdad3c52226fa1029a1dd87bfd9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204912"
---
# <a name="message-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="22818-102">\<message> elemento de \<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="22818-102">\<message> element of \<ws2007FederationHttpBinding></span></span>

<span data-ttu-id="22818-103">Define as configurações para a segurança em nível de mensagem para o [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="22818-103">Defines settings for the message-level security for the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007FederationHttpBinding>**](ws2007federationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-element-of-ws2007federationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a><span data-ttu-id="22818-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="22818-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="22818-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="22818-105">Attributes and Elements</span></span>  

 <span data-ttu-id="22818-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="22818-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="22818-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="22818-107">Attributes</span></span>  
  
|<span data-ttu-id="22818-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="22818-108">Attribute</span></span>|<span data-ttu-id="22818-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="22818-109">Description</span></span>|  
|---------------|-----------------|  
|`algorithmSuite`|<span data-ttu-id="22818-110">Opcional.</span><span class="sxs-lookup"><span data-stu-id="22818-110">Optional.</span></span> <span data-ttu-id="22818-111">Define a criptografia de mensagem, a assinatura e os algoritmos de encapsulamento de chaves.</span><span class="sxs-lookup"><span data-stu-id="22818-111">Sets the message encryption, signature, and key-wrap algorithms.</span></span> <span data-ttu-id="22818-112">Os algoritmos e os tamanhos de chave são determinados pela <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> classe.</span><span class="sxs-lookup"><span data-stu-id="22818-112">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="22818-113">Esses algoritmos são mapeados para aqueles especificados na especificação do WS-SecurityPolicy (Security Policy Language).</span><span class="sxs-lookup"><span data-stu-id="22818-113">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="22818-114">Consulte a tabela a seguir para obter os valores possíveis.</span><span class="sxs-lookup"><span data-stu-id="22818-114">See the following table for possible values.</span></span> <span data-ttu-id="22818-115">O valor padrão é Basic256.</span><span class="sxs-lookup"><span data-stu-id="22818-115">The default value is Basic256.</span></span>|  
|`issuedKeyType`|<span data-ttu-id="22818-116">Especifica o tipo de chave a ser emitida.</span><span class="sxs-lookup"><span data-stu-id="22818-116">Specifies the type of key to be issued.</span></span> <span data-ttu-id="22818-117">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="22818-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="22818-118">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="22818-118">-   SymmetricKey</span></span><br /><span data-ttu-id="22818-119">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="22818-119">-   PublicKey</span></span><br /><span data-ttu-id="22818-120">- BearerKey</span><span class="sxs-lookup"><span data-stu-id="22818-120">-   BearerKey</span></span><br /><br /> <span data-ttu-id="22818-121">O padrão é SymmetricKey.</span><span class="sxs-lookup"><span data-stu-id="22818-121">The default is SymmetricKey.</span></span> <span data-ttu-id="22818-122">Esse atributo é do tipo <xref:System.IdentityModel.Tokens.SecurityKeyType> .</span><span class="sxs-lookup"><span data-stu-id="22818-122">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|`issuedTokenType`|<span data-ttu-id="22818-123">Um URI que especifica o tipo de token a ser emitido.</span><span class="sxs-lookup"><span data-stu-id="22818-123">A URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="22818-124">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="22818-124">The default is `null`.</span></span>|  
|`negotiateServiceCredential`|<span data-ttu-id="22818-125">Um valor que especifica se a credencial de serviço deve ser trocada como parte da negociação ou está disponível fora da banda.</span><span class="sxs-lookup"><span data-stu-id="22818-125">A value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="22818-126">O padrão é `true` , o que significa que a credencial de serviço é negociada.</span><span class="sxs-lookup"><span data-stu-id="22818-126">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="22818-127">Atributo algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="22818-127">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="22818-128">Valor</span><span class="sxs-lookup"><span data-stu-id="22818-128">Value</span></span>|<span data-ttu-id="22818-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="22818-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="22818-130">Basic128</span><span class="sxs-lookup"><span data-stu-id="22818-130">Basic128</span></span>|<span data-ttu-id="22818-131">Use criptografia Aes128, SHA1 para síntese de mensagem e rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="22818-131">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="22818-132">Basic192</span><span class="sxs-lookup"><span data-stu-id="22818-132">Basic192</span></span>|<span data-ttu-id="22818-133">Use a criptografia Aes192, SHA1 para Message Digest, rsa-oaep-mgf1p para quebra automática de chave.</span><span class="sxs-lookup"><span data-stu-id="22818-133">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="22818-134">Basic256</span><span class="sxs-lookup"><span data-stu-id="22818-134">Basic256</span></span>|<span data-ttu-id="22818-135">Use a criptografia Aes256, SHA1 para Message Digest, rsa-oaep-mgf1p para quebra automática de chave.</span><span class="sxs-lookup"><span data-stu-id="22818-135">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="22818-136">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="22818-136">Basic256Rsa15</span></span>|<span data-ttu-id="22818-137">Use Aes256 para criptografia de mensagem, SHA1 para Message Digest e Rsa15 para Key Wrap.</span><span class="sxs-lookup"><span data-stu-id="22818-137">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="22818-138">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="22818-138">Basic192Rsa15</span></span>|<span data-ttu-id="22818-139">Use Aes192 para criptografia de mensagem, SHA1 para Message Digest e Rsa15 para Key Wrap.</span><span class="sxs-lookup"><span data-stu-id="22818-139">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="22818-140">TripleDes</span><span class="sxs-lookup"><span data-stu-id="22818-140">TripleDes</span></span>|<span data-ttu-id="22818-141">Use a criptografia TripleDes, SHA1 para Message Digest, rsa-oaep-mgf1p para quebra automática de chave.</span><span class="sxs-lookup"><span data-stu-id="22818-141">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="22818-142">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="22818-142">Basic128Rsa15</span></span>|<span data-ttu-id="22818-143">Use Aes128 para criptografia de mensagem, SHA1 para Message Digest e Rsa15 para Key Wrap.</span><span class="sxs-lookup"><span data-stu-id="22818-143">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="22818-144">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="22818-144">TripleDesRsa15</span></span>|<span data-ttu-id="22818-145">Use a criptografia TripleDes, SHA1 para síntese de mensagem e Rsa15 para o encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="22818-145">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="22818-146">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="22818-146">Basic128Sha256</span></span>|<span data-ttu-id="22818-147">Use Aes256 para criptografia de mensagem, SHA256 para síntese de mensagem e rsa-oaep-mgf1p para quebra automática de chave.</span><span class="sxs-lookup"><span data-stu-id="22818-147">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="22818-148">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="22818-148">Basic192Sha256</span></span>|<span data-ttu-id="22818-149">Use Aes192 para criptografia de mensagem, SHA256 para síntese de mensagem e rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="22818-149">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="22818-150">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="22818-150">Basic256Sha256</span></span>|<span data-ttu-id="22818-151">Use Aes256 para criptografia de mensagem, SHA256 para síntese de mensagem e rsa-oaep-mgf1p para quebra automática de chave.</span><span class="sxs-lookup"><span data-stu-id="22818-151">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="22818-152">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="22818-152">TripleDesSha256</span></span>|<span data-ttu-id="22818-153">Use TripleDes para criptografia de mensagem, SHA256 para síntese de mensagem e rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="22818-153">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="22818-154">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="22818-154">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="22818-155">Use Aes128 para criptografia de mensagem, SHA256 para síntese de mensagem e Rsa15 para quebra de chave.</span><span class="sxs-lookup"><span data-stu-id="22818-155">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="22818-156">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="22818-156">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="22818-157">Use Aes192 para criptografia de mensagem, SHA256 para síntese de mensagem e Rsa15 para quebra de chave.</span><span class="sxs-lookup"><span data-stu-id="22818-157">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="22818-158">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="22818-158">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="22818-159">Use Aes256 para criptografia de mensagem, SHA256 para síntese de mensagem e Rsa15 para quebra automática de chave.</span><span class="sxs-lookup"><span data-stu-id="22818-159">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="22818-160">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="22818-160">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="22818-161">Use TripleDes para criptografia de mensagem, SHA256 para síntese de mensagem e Rsa15 para quebra de chave.</span><span class="sxs-lookup"><span data-stu-id="22818-161">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="22818-162">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="22818-162">Child Elements</span></span>  
  
|<span data-ttu-id="22818-163">Elemento</span><span class="sxs-lookup"><span data-stu-id="22818-163">Element</span></span>|<span data-ttu-id="22818-164">Descrição</span><span class="sxs-lookup"><span data-stu-id="22818-164">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|<span data-ttu-id="22818-165">Especifica uma coleção de tipos de declaração para essa associação.</span><span class="sxs-lookup"><span data-stu-id="22818-165">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="22818-166">Cada elemento é do tipo <xref:System.ServiceModel.Configuration.ClaimTypeElement> .</span><span class="sxs-lookup"><span data-stu-id="22818-166">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|[\<issuer>](issuer.md)|<span data-ttu-id="22818-167">Especifica um ponto de extremidade que emite um token de segurança.</span><span class="sxs-lookup"><span data-stu-id="22818-167">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="22818-168">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement> .</span><span class="sxs-lookup"><span data-stu-id="22818-168">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|[\<issuerMetadata>](issuermetadata.md)|<span data-ttu-id="22818-169">Especifica o endereço do ponto de extremidade do emissor.</span><span class="sxs-lookup"><span data-stu-id="22818-169">Specifies the endpoint address of the issuer.</span></span>|  
|[\<tokenRequestParameters>](tokenrequestparameters.md)|<span data-ttu-id="22818-170">Uma coleção de parâmetros de solicitação de token.</span><span class="sxs-lookup"><span data-stu-id="22818-170">A collection of token request parameters.</span></span> <span data-ttu-id="22818-171">Cada parâmetro é um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="22818-171">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="22818-172">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="22818-172">Parent Elements</span></span>  
  
|<span data-ttu-id="22818-173">Elemento</span><span class="sxs-lookup"><span data-stu-id="22818-173">Element</span></span>|<span data-ttu-id="22818-174">Descrição</span><span class="sxs-lookup"><span data-stu-id="22818-174">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-element-of-ws2007federationhttpbinding.md)|<span data-ttu-id="22818-175">Define as configurações de segurança para uma associação.</span><span class="sxs-lookup"><span data-stu-id="22818-175">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="22818-176">Veja também</span><span class="sxs-lookup"><span data-stu-id="22818-176">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="22818-177">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="22818-177">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="22818-178">Associações</span><span class="sxs-lookup"><span data-stu-id="22818-178">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="22818-179">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="22818-179">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="22818-180">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="22818-180">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
