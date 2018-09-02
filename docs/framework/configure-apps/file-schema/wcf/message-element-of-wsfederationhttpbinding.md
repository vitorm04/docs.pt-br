---
title: elemento de &lt;mensagem&gt; de &lt;wsFederationHttpBinding&gt;
ms.date: 03/30/2017
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
ms.openlocfilehash: 820ee7015a51ecc5510889516faef20292cfbc07
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43416588"
---
# <a name="ltmessagegt-element-of-ltwsfederationhttpbindinggt"></a><span data-ttu-id="ecf5c-102">elemento de &lt;mensagem&gt; de &lt;wsFederationHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="ecf5c-102">&lt;message&gt; element of &lt;wsFederationHttpBinding&gt;</span></span>
<span data-ttu-id="ecf5c-103">Define as configurações para a segurança de nível de mensagem para o [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="ecf5c-103">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="ecf5c-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ecf5c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ecf5c-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="ecf5c-105">\<bindings></span></span>  
<span data-ttu-id="ecf5c-106">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="ecf5c-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="ecf5c-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="ecf5c-107">\<binding></span></span>  
<span data-ttu-id="ecf5c-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="ecf5c-108">\<security></span></span>  
<span data-ttu-id="ecf5c-109">\<message></span><span class="sxs-lookup"><span data-stu-id="ecf5c-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecf5c-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ecf5c-110">Syntax</span></span>  
  
```xml  
<wsFederationBinding>  
     <binding >  
         <security>  
         <message   
            algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            issuedTokenType="string"   
            issuedKeyType="SymmetricKey/PublicKey"  
            negotiateServiceCredential="Boolean" >  
            <claimTypeRequirements>  
               <add claimType="URI"  
                    isOptional="Boolean" />  
            </claimTypeRequirements>  
                        <issuer address="Uri" >  
               <headers>  
                  <add name="String"  
                       namespace="String" />  
                          </headers>  
                              <identity>  
                              <certificate encodedValue="String"/>  
                                <certificateReference findValue="String"   
                                 isChainIncluded="Boolean"  
                            storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
                                  storeLocation="LocalMachine/CurrentUser"  
                     x509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
                                   <dns value="String"/>  
                                <rsa value="String"/>  
                                <servicePrincipalName value="String"/>  
                                <usePrincipalName value="String"/>  
                              </identity>  
                        </issuer>  
                        <issuerMetadata address=String" >  
               <headers>  
                  <add name="String"  
                       namespace="String" />  
               </headers>  
               <identity>  
                  <certificate encodedValue="String"/>  
                  <certificateReference findValue="String"   
                     isChainIncluded="Boolean"  
                     storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
                     storeLocation="LocalMachine/CurrentUser"  
                     X509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
                  <dns value="String"/>  
                  <rsa value="String"/>  
                  <servicePrincipalName value="String"/>  
                  <usePrincipalName value="String"/>  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ecf5c-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ecf5c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ecf5c-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ecf5c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ecf5c-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="ecf5c-113">Attributes</span></span>  
  
|<span data-ttu-id="ecf5c-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="ecf5c-114">Attribute</span></span>|<span data-ttu-id="ecf5c-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="ecf5c-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ecf5c-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="ecf5c-116">algorithmSuite</span></span>|<span data-ttu-id="ecf5c-117">Define a mensagem de algoritmos de criptografia e encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="ecf5c-117">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="ecf5c-118">Consulte a tabela "algorithmSuite atributo" para obter valores válidos desse atributo.</span><span class="sxs-lookup"><span data-stu-id="ecf5c-118">See the "algorithmSuite attribute" table for valid values of this attribute.</span></span> <span data-ttu-id="ecf5c-119">O valor padrão é `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="ecf5c-119">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="ecf5c-120">Esse atributo é do tipo <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="ecf5c-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span> <span data-ttu-id="ecf5c-121">Esses algoritmos são mapeados para aqueles especificados na especificação da linguagem de política de segurança (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="ecf5c-121">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>|  
|<span data-ttu-id="ecf5c-122">issuedKeyType</span><span class="sxs-lookup"><span data-stu-id="ecf5c-122">issuedKeyType</span></span>|<span data-ttu-id="ecf5c-123">Especifica o tipo de chave a ser emitida.</span><span class="sxs-lookup"><span data-stu-id="ecf5c-123">Specifies the type of key to be issued.</span></span> <span data-ttu-id="ecf5c-124">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ecf5c-124">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ecf5c-125">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="ecf5c-125">-   SymmetricKey</span></span><br /><span data-ttu-id="ecf5c-126">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="ecf5c-126">-   PublicKey</span></span><br /><br /> <span data-ttu-id="ecf5c-127">O padrão é `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="ecf5c-127">The default is `SymmetricKey`.</span></span> <span data-ttu-id="ecf5c-128">Esse atributo é do tipo <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="ecf5c-128">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|<span data-ttu-id="ecf5c-129">issuedTokenType</span><span class="sxs-lookup"><span data-stu-id="ecf5c-129">issuedTokenType</span></span>|<span data-ttu-id="ecf5c-130">Uma cadeia de caracteres que contém um URI que especifica o tipo de token a ser emitido.</span><span class="sxs-lookup"><span data-stu-id="ecf5c-130">A string that contains a URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="ecf5c-131">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="ecf5c-131">The default is `null`.</span></span>|  
|<span data-ttu-id="ecf5c-132">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="ecf5c-132">negotiateServiceCredential</span></span>|<span data-ttu-id="ecf5c-133">Um valor booliano que especifica se a credencial de serviço deve ser trocada como parte da negociação ou está disponível fora da banda.</span><span class="sxs-lookup"><span data-stu-id="ecf5c-133">A Boolean value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="ecf5c-134">O padrão é `true`, o que significa que a credencial de serviço é negociada.</span><span class="sxs-lookup"><span data-stu-id="ecf5c-134">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="ecf5c-135">algorithmSuite atributo</span><span class="sxs-lookup"><span data-stu-id="ecf5c-135">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="ecf5c-136">Valor</span><span class="sxs-lookup"><span data-stu-id="ecf5c-136">Value</span></span>|<span data-ttu-id="ecf5c-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="ecf5c-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ecf5c-138">Basic128</span><span class="sxs-lookup"><span data-stu-id="ecf5c-138">Basic128</span></span>|<span data-ttu-id="ecf5c-139">Use criptografia Basic128, Sha1 de resumo da mensagem e Rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="ecf5c-139">Use Basic128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ecf5c-140">Basic192</span><span class="sxs-lookup"><span data-stu-id="ecf5c-140">Basic192</span></span>|<span data-ttu-id="ecf5c-141">Use a criptografia Basic192, Sha1 para o message digest, Rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="ecf5c-141">Use Basic192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ecf5c-142">Basic256</span><span class="sxs-lookup"><span data-stu-id="ecf5c-142">Basic256</span></span>|<span data-ttu-id="ecf5c-143">Use a criptografia Basic256, Sha1 para o message digest, Rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="ecf5c-143">Use Basic256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ecf5c-144">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="ecf5c-144">Basic256Rsa15</span></span>|<span data-ttu-id="ecf5c-145">Use Basic256 para criptografia de mensagem, Sha1 de resumo da mensagem e Rsa15 para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="ecf5c-145">Use Basic256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ecf5c-146">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="ecf5c-146">Basic192Rsa15</span></span>|<span data-ttu-id="ecf5c-147">Use Basic192 para criptografia de mensagem, Sha1 de resumo da mensagem e Rsa15 para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="ecf5c-147">Use Basic192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ecf5c-148">TripleDes</span><span class="sxs-lookup"><span data-stu-id="ecf5c-148">TripleDes</span></span>|<span data-ttu-id="ecf5c-149">Use a criptografia TripleDes, Sha1 para o message digest, Rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="ecf5c-149">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ecf5c-150">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="ecf5c-150">Basic128Rsa15</span></span>|<span data-ttu-id="ecf5c-151">Use Basic128 para criptografia de mensagem, Sha1 de resumo da mensagem e Rsa15 para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="ecf5c-151">Use Basic128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ecf5c-152">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="ecf5c-152">TripleDesRsa15</span></span>|<span data-ttu-id="ecf5c-153">Use a criptografia TripleDes, Sha1 de resumo da mensagem e Rsa15 para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="ecf5c-153">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ecf5c-154">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="ecf5c-154">Basic128Sha256</span></span>|<span data-ttu-id="ecf5c-155">Use Basic128 para criptografia de mensagem, o Sha256 para o resumo da mensagem e Rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="ecf5c-155">Use Basic128 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ecf5c-156">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="ecf5c-156">Basic192Sha256</span></span>|<span data-ttu-id="ecf5c-157">Use Basic192 para criptografia de mensagem, o Sha256 para o resumo da mensagem e Rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="ecf5c-157">Use Basic192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ecf5c-158">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="ecf5c-158">Basic256Sha256</span></span>|<span data-ttu-id="ecf5c-159">Use Basic256 para criptografia de mensagem, o Sha256 para o resumo da mensagem e Rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="ecf5c-159">Use Basic256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ecf5c-160">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="ecf5c-160">TripleDesSha256</span></span>|<span data-ttu-id="ecf5c-161">Use triplo DES para criptografia de mensagem, o Sha256 para o resumo da mensagem e Rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="ecf5c-161">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ecf5c-162">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="ecf5c-162">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="ecf5c-163">Use Basic128 para criptografia de mensagem, o Sha256 para o resumo da mensagem e Rsa15 para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="ecf5c-163">Use Basic128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ecf5c-164">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="ecf5c-164">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="ecf5c-165">Use Aes192 para criptografia de mensagem, o Sha256 para o resumo da mensagem e Rsa15 para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="ecf5c-165">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ecf5c-166">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="ecf5c-166">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="ecf5c-167">Use Basic256 para criptografia de mensagem, o Sha256 para o resumo da mensagem e Rsa15 para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="ecf5c-167">Use Basic256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ecf5c-168">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="ecf5c-168">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="ecf5c-169">Use o triplo DES para criptografia de mensagem, o Sha256 para o resumo da mensagem e Rsa15 para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="ecf5c-169">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ecf5c-170">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ecf5c-170">Child Elements</span></span>  
  
|<span data-ttu-id="ecf5c-171">Elemento</span><span class="sxs-lookup"><span data-stu-id="ecf5c-171">Element</span></span>|<span data-ttu-id="ecf5c-172">Descrição</span><span class="sxs-lookup"><span data-stu-id="ecf5c-172">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ecf5c-173">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="ecf5c-173">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="ecf5c-174">Especifica uma coleção de tipos de declaração para essa associação.</span><span class="sxs-lookup"><span data-stu-id="ecf5c-174">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="ecf5c-175">Cada elemento é do tipo <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="ecf5c-175">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|<span data-ttu-id="ecf5c-176">emissor</span><span class="sxs-lookup"><span data-stu-id="ecf5c-176">issuer</span></span>|<span data-ttu-id="ecf5c-177">Especifica um ponto de extremidade que emite um token de segurança.</span><span class="sxs-lookup"><span data-stu-id="ecf5c-177">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="ecf5c-178">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="ecf5c-178">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|<span data-ttu-id="ecf5c-179">issuerMetadata</span><span class="sxs-lookup"><span data-stu-id="ecf5c-179">issuerMetadata</span></span>|<span data-ttu-id="ecf5c-180">Especifica o endereço do ponto de extremidade do emissor.</span><span class="sxs-lookup"><span data-stu-id="ecf5c-180">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="ecf5c-181">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="ecf5c-181">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="ecf5c-182">Uma coleção de parâmetros de solicitação de token.</span><span class="sxs-lookup"><span data-stu-id="ecf5c-182">A collection of token request parameters.</span></span> <span data-ttu-id="ecf5c-183">Cada parâmetro é um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="ecf5c-183">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ecf5c-184">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ecf5c-184">Parent Elements</span></span>  
  
|<span data-ttu-id="ecf5c-185">Elemento</span><span class="sxs-lookup"><span data-stu-id="ecf5c-185">Element</span></span>|<span data-ttu-id="ecf5c-186">Descrição</span><span class="sxs-lookup"><span data-stu-id="ecf5c-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ecf5c-187">\<security></span><span class="sxs-lookup"><span data-stu-id="ecf5c-187">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|<span data-ttu-id="ecf5c-188">Define as configurações de segurança para uma associação.</span><span class="sxs-lookup"><span data-stu-id="ecf5c-188">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ecf5c-189">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ecf5c-189">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>  
 <span data-ttu-id="ecf5c-190">`System.ServiceModel.Configuration.FederatedMessageSecurityElement` [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)</span><span class="sxs-lookup"><span data-stu-id="ecf5c-190">`System.ServiceModel.Configuration.FederatedMessageSecurityElement` [Securing Services and Clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)</span></span>  
 [<span data-ttu-id="ecf5c-191">Associações</span><span class="sxs-lookup"><span data-stu-id="ecf5c-191">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="ecf5c-192">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="ecf5c-192">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="ecf5c-193">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="ecf5c-193">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="ecf5c-194">\<associação ></span><span class="sxs-lookup"><span data-stu-id="ecf5c-194">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
