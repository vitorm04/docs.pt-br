---
title: <message> elemento de <wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
ms.openlocfilehash: ea320b1d97e742d4f90ec55502f3bd429803283d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204886"
---
# <a name="message-element-of-wsfederationhttpbinding"></a><span data-ttu-id="ec98d-102">\<message> elemento de \<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="ec98d-102">\<message> element of \<wsFederationHttpBinding></span></span>

<span data-ttu-id="ec98d-103">Define as configurações para a segurança em nível de mensagem para o [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="ec98d-103">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a><span data-ttu-id="ec98d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ec98d-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ec98d-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ec98d-105">Attributes and Elements</span></span>  

 <span data-ttu-id="ec98d-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ec98d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ec98d-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="ec98d-107">Attributes</span></span>  
  
|<span data-ttu-id="ec98d-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="ec98d-108">Attribute</span></span>|<span data-ttu-id="ec98d-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="ec98d-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ec98d-110">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="ec98d-110">algorithmSuite</span></span>|<span data-ttu-id="ec98d-111">Define a criptografia de mensagem e os algoritmos de encapsulamento de chaves.</span><span class="sxs-lookup"><span data-stu-id="ec98d-111">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="ec98d-112">Consulte a tabela "atributo algorithmSuite" para obter os valores válidos deste atributo.</span><span class="sxs-lookup"><span data-stu-id="ec98d-112">See the "algorithmSuite attribute" table for valid values of this attribute.</span></span> <span data-ttu-id="ec98d-113">O valor padrão é `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="ec98d-113">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="ec98d-114">Esse atributo é do tipo <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> .</span><span class="sxs-lookup"><span data-stu-id="ec98d-114">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span> <span data-ttu-id="ec98d-115">Esses algoritmos são mapeados para aqueles especificados na especificação do WS-SecurityPolicy (Security Policy Language).</span><span class="sxs-lookup"><span data-stu-id="ec98d-115">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>|  
|<span data-ttu-id="ec98d-116">issuedKeyType</span><span class="sxs-lookup"><span data-stu-id="ec98d-116">issuedKeyType</span></span>|<span data-ttu-id="ec98d-117">Especifica o tipo de chave a ser emitida.</span><span class="sxs-lookup"><span data-stu-id="ec98d-117">Specifies the type of key to be issued.</span></span> <span data-ttu-id="ec98d-118">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="ec98d-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ec98d-119">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="ec98d-119">-   SymmetricKey</span></span><br /><span data-ttu-id="ec98d-120">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="ec98d-120">-   PublicKey</span></span><br /><br /> <span data-ttu-id="ec98d-121">O padrão é `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="ec98d-121">The default is `SymmetricKey`.</span></span> <span data-ttu-id="ec98d-122">Esse atributo é do tipo <xref:System.IdentityModel.Tokens.SecurityKeyType> .</span><span class="sxs-lookup"><span data-stu-id="ec98d-122">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|<span data-ttu-id="ec98d-123">issuedTokenType</span><span class="sxs-lookup"><span data-stu-id="ec98d-123">issuedTokenType</span></span>|<span data-ttu-id="ec98d-124">Uma cadeia de caracteres que contém um URI que especifica o tipo de token a ser emitido.</span><span class="sxs-lookup"><span data-stu-id="ec98d-124">A string that contains a URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="ec98d-125">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="ec98d-125">The default is `null`.</span></span>|  
|<span data-ttu-id="ec98d-126">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="ec98d-126">negotiateServiceCredential</span></span>|<span data-ttu-id="ec98d-127">Um valor booliano que especifica se a credencial de serviço deve ser trocada como parte da negociação ou está disponível fora da banda.</span><span class="sxs-lookup"><span data-stu-id="ec98d-127">A Boolean value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="ec98d-128">O padrão é `true` , o que significa que a credencial de serviço é negociada.</span><span class="sxs-lookup"><span data-stu-id="ec98d-128">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="ec98d-129">Atributo algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="ec98d-129">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="ec98d-130">Valor</span><span class="sxs-lookup"><span data-stu-id="ec98d-130">Value</span></span>|<span data-ttu-id="ec98d-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="ec98d-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ec98d-132">Basic128</span><span class="sxs-lookup"><span data-stu-id="ec98d-132">Basic128</span></span>|<span data-ttu-id="ec98d-133">Use criptografia Basic128, SHA1 para síntese de mensagem e rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="ec98d-133">Use Basic128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ec98d-134">Basic192</span><span class="sxs-lookup"><span data-stu-id="ec98d-134">Basic192</span></span>|<span data-ttu-id="ec98d-135">Use a criptografia Basic192, SHA1 para Message Digest, rsa-oaep-mgf1p para quebra automática de chave.</span><span class="sxs-lookup"><span data-stu-id="ec98d-135">Use Basic192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ec98d-136">Basic256</span><span class="sxs-lookup"><span data-stu-id="ec98d-136">Basic256</span></span>|<span data-ttu-id="ec98d-137">Use a criptografia Basic256, SHA1 para Message Digest, rsa-oaep-mgf1p para quebra automática de chave.</span><span class="sxs-lookup"><span data-stu-id="ec98d-137">Use Basic256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ec98d-138">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="ec98d-138">Basic256Rsa15</span></span>|<span data-ttu-id="ec98d-139">Use Basic256 para criptografia de mensagem, SHA1 para Message Digest e Rsa15 para Key Wrap.</span><span class="sxs-lookup"><span data-stu-id="ec98d-139">Use Basic256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ec98d-140">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="ec98d-140">Basic192Rsa15</span></span>|<span data-ttu-id="ec98d-141">Use Basic192 para criptografia de mensagem, SHA1 para Message Digest e Rsa15 para Key Wrap.</span><span class="sxs-lookup"><span data-stu-id="ec98d-141">Use Basic192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ec98d-142">TripleDes</span><span class="sxs-lookup"><span data-stu-id="ec98d-142">TripleDes</span></span>|<span data-ttu-id="ec98d-143">Use a criptografia TripleDes, SHA1 para Message Digest, rsa-oaep-mgf1p para quebra automática de chave.</span><span class="sxs-lookup"><span data-stu-id="ec98d-143">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ec98d-144">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="ec98d-144">Basic128Rsa15</span></span>|<span data-ttu-id="ec98d-145">Use Basic128 para criptografia de mensagem, SHA1 para Message Digest e Rsa15 para Key Wrap.</span><span class="sxs-lookup"><span data-stu-id="ec98d-145">Use Basic128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ec98d-146">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="ec98d-146">TripleDesRsa15</span></span>|<span data-ttu-id="ec98d-147">Use a criptografia TripleDes, SHA1 para síntese de mensagem e Rsa15 para o encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="ec98d-147">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ec98d-148">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="ec98d-148">Basic128Sha256</span></span>|<span data-ttu-id="ec98d-149">Use Basic128 para criptografia de mensagem, SHA256 para síntese de mensagem e rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="ec98d-149">Use Basic128 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ec98d-150">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="ec98d-150">Basic192Sha256</span></span>|<span data-ttu-id="ec98d-151">Use Basic192 para criptografia de mensagem, SHA256 para síntese de mensagem e rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="ec98d-151">Use Basic192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ec98d-152">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="ec98d-152">Basic256Sha256</span></span>|<span data-ttu-id="ec98d-153">Use Basic256 para criptografia de mensagem, SHA256 para síntese de mensagem e rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="ec98d-153">Use Basic256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ec98d-154">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="ec98d-154">TripleDesSha256</span></span>|<span data-ttu-id="ec98d-155">Use TripleDes para criptografia de mensagem, SHA256 para síntese de mensagem e rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="ec98d-155">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ec98d-156">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="ec98d-156">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="ec98d-157">Use Basic128 para criptografia de mensagem, SHA256 para síntese de mensagem e Rsa15 para quebra de chave.</span><span class="sxs-lookup"><span data-stu-id="ec98d-157">Use Basic128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ec98d-158">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="ec98d-158">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="ec98d-159">Use Aes192 para criptografia de mensagem, SHA256 para síntese de mensagem e Rsa15 para quebra de chave.</span><span class="sxs-lookup"><span data-stu-id="ec98d-159">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ec98d-160">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="ec98d-160">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="ec98d-161">Use Basic256 para criptografia de mensagem, SHA256 para síntese de mensagem e Rsa15 para quebra de chave.</span><span class="sxs-lookup"><span data-stu-id="ec98d-161">Use Basic256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ec98d-162">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="ec98d-162">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="ec98d-163">Use TripleDes para criptografia de mensagem, SHA256 para síntese de mensagem e Rsa15 para quebra de chave.</span><span class="sxs-lookup"><span data-stu-id="ec98d-163">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ec98d-164">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ec98d-164">Child Elements</span></span>  
  
|<span data-ttu-id="ec98d-165">Elemento</span><span class="sxs-lookup"><span data-stu-id="ec98d-165">Element</span></span>|<span data-ttu-id="ec98d-166">Descrição</span><span class="sxs-lookup"><span data-stu-id="ec98d-166">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|<span data-ttu-id="ec98d-167">Especifica uma coleção de tipos de declaração para essa associação.</span><span class="sxs-lookup"><span data-stu-id="ec98d-167">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="ec98d-168">Cada elemento é do tipo <xref:System.ServiceModel.Configuration.ClaimTypeElement> .</span><span class="sxs-lookup"><span data-stu-id="ec98d-168">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|<span data-ttu-id="ec98d-169">emissor</span><span class="sxs-lookup"><span data-stu-id="ec98d-169">issuer</span></span>|<span data-ttu-id="ec98d-170">Especifica um ponto de extremidade que emite um token de segurança.</span><span class="sxs-lookup"><span data-stu-id="ec98d-170">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="ec98d-171">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement> .</span><span class="sxs-lookup"><span data-stu-id="ec98d-171">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|<span data-ttu-id="ec98d-172">issuerMetadata</span><span class="sxs-lookup"><span data-stu-id="ec98d-172">issuerMetadata</span></span>|<span data-ttu-id="ec98d-173">Especifica o endereço do ponto de extremidade do emissor.</span><span class="sxs-lookup"><span data-stu-id="ec98d-173">Specifies the endpoint address of the issuer.</span></span>|  
|[\<tokenRequestParameters>](tokenrequestparameters.md)|<span data-ttu-id="ec98d-174">Uma coleção de parâmetros de solicitação de token.</span><span class="sxs-lookup"><span data-stu-id="ec98d-174">A collection of token request parameters.</span></span> <span data-ttu-id="ec98d-175">Cada parâmetro é um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="ec98d-175">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ec98d-176">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ec98d-176">Parent Elements</span></span>  
  
|<span data-ttu-id="ec98d-177">Elemento</span><span class="sxs-lookup"><span data-stu-id="ec98d-177">Element</span></span>|<span data-ttu-id="ec98d-178">Descrição</span><span class="sxs-lookup"><span data-stu-id="ec98d-178">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="ec98d-179">Define as configurações de segurança para uma associação.</span><span class="sxs-lookup"><span data-stu-id="ec98d-179">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ec98d-180">Veja também</span><span class="sxs-lookup"><span data-stu-id="ec98d-180">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="ec98d-181">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="ec98d-181">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ec98d-182">Associações</span><span class="sxs-lookup"><span data-stu-id="ec98d-182">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ec98d-183">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="ec98d-183">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ec98d-184">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="ec98d-184">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
