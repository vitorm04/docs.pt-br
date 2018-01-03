---
title: elemento de &lt;mensagem&gt; de &lt;wsFederationHttpBinding&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 09e384311f50553585c0a7a14a51df20858fb439
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltmessagegt-element-of-ltwsfederationhttpbindinggt"></a><span data-ttu-id="ba5b5-102">elemento de &lt;mensagem&gt; de &lt;wsFederationHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="ba5b5-102">&lt;message&gt; element of &lt;wsFederationHttpBinding&gt;</span></span>
<span data-ttu-id="ba5b5-103">Define as configurações para a segurança de nível de mensagem para o [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="ba5b5-103">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="ba5b5-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="ba5b5-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ba5b5-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="ba5b5-105">\<bindings></span></span>  
<span data-ttu-id="ba5b5-106">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="ba5b5-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="ba5b5-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="ba5b5-107">\<binding></span></span>  
<span data-ttu-id="ba5b5-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="ba5b5-108">\<security></span></span>  
<span data-ttu-id="ba5b5-109">\<mensagem ></span><span class="sxs-lookup"><span data-stu-id="ba5b5-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba5b5-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ba5b5-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ba5b5-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ba5b5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ba5b5-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ba5b5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ba5b5-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="ba5b5-113">Attributes</span></span>  
  
|<span data-ttu-id="ba5b5-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="ba5b5-114">Attribute</span></span>|<span data-ttu-id="ba5b5-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="ba5b5-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ba5b5-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="ba5b5-116">algorithmSuite</span></span>|<span data-ttu-id="ba5b5-117">Define a mensagem de algoritmos de criptografia e chave-wrap.</span><span class="sxs-lookup"><span data-stu-id="ba5b5-117">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="ba5b5-118">Consulte a tabela "atributo algorithmSuite" para obter valores válidos deste atributo.</span><span class="sxs-lookup"><span data-stu-id="ba5b5-118">See the "algorithmSuite attribute" table for valid values of this attribute.</span></span> <span data-ttu-id="ba5b5-119">O valor padrão é `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="ba5b5-119">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="ba5b5-120">Esse atributo é do tipo <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="ba5b5-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span> <span data-ttu-id="ba5b5-121">Esses algoritmos são mapeados para aquelas especificadas na especificação de linguagem de política de segurança (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="ba5b5-121">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>|  
|<span data-ttu-id="ba5b5-122">issuedKeyType</span><span class="sxs-lookup"><span data-stu-id="ba5b5-122">issuedKeyType</span></span>|<span data-ttu-id="ba5b5-123">Especifica o tipo de chave a ser emitida.</span><span class="sxs-lookup"><span data-stu-id="ba5b5-123">Specifies the type of key to be issued.</span></span> <span data-ttu-id="ba5b5-124">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ba5b5-124">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ba5b5-125">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="ba5b5-125">-   SymmetricKey</span></span><br /><span data-ttu-id="ba5b5-126">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="ba5b5-126">-   PublicKey</span></span><br /><br /> <span data-ttu-id="ba5b5-127">O padrão é `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="ba5b5-127">The default is `SymmetricKey`.</span></span> <span data-ttu-id="ba5b5-128">Esse atributo é do tipo <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="ba5b5-128">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|<span data-ttu-id="ba5b5-129">issuedTokenType</span><span class="sxs-lookup"><span data-stu-id="ba5b5-129">issuedTokenType</span></span>|<span data-ttu-id="ba5b5-130">Uma cadeia de caracteres que contém um URI que especifica o tipo de token a ser emitido.</span><span class="sxs-lookup"><span data-stu-id="ba5b5-130">A string that contains a URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="ba5b5-131">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="ba5b5-131">The default is `null`.</span></span>|  
|<span data-ttu-id="ba5b5-132">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="ba5b5-132">negotiateServiceCredential</span></span>|<span data-ttu-id="ba5b5-133">Um valor booleano que especifica se a credencial de serviço deve ser trocada como parte da negociação ou está disponível fora da banda.</span><span class="sxs-lookup"><span data-stu-id="ba5b5-133">A Boolean value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="ba5b5-134">O padrão é `true`, que significa que a credencial de serviço é negociada.</span><span class="sxs-lookup"><span data-stu-id="ba5b5-134">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="ba5b5-135">algorithmSuite atributo</span><span class="sxs-lookup"><span data-stu-id="ba5b5-135">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="ba5b5-136">Valor</span><span class="sxs-lookup"><span data-stu-id="ba5b5-136">Value</span></span>|<span data-ttu-id="ba5b5-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="ba5b5-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ba5b5-138">Basic128</span><span class="sxs-lookup"><span data-stu-id="ba5b5-138">Basic128</span></span>|<span data-ttu-id="ba5b5-139">Use criptografia Basic128, Sha1 para resumo da mensagem e Rsa-oaep-mgf1p para codificação de chave.</span><span class="sxs-lookup"><span data-stu-id="ba5b5-139">Use Basic128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ba5b5-140">Basic192</span><span class="sxs-lookup"><span data-stu-id="ba5b5-140">Basic192</span></span>|<span data-ttu-id="ba5b5-141">Use a criptografia Basic192, Sha1 para resumo da mensagem, Rsa-oaep mgf1p para codificação de chave.</span><span class="sxs-lookup"><span data-stu-id="ba5b5-141">Use Basic192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ba5b5-142">Basic256</span><span class="sxs-lookup"><span data-stu-id="ba5b5-142">Basic256</span></span>|<span data-ttu-id="ba5b5-143">Use a criptografia Basic256, Sha1 para resumo da mensagem, Rsa-oaep mgf1p para codificação de chave.</span><span class="sxs-lookup"><span data-stu-id="ba5b5-143">Use Basic256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ba5b5-144">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="ba5b5-144">Basic256Rsa15</span></span>|<span data-ttu-id="ba5b5-145">Use Basic256 para criptografia de mensagem, Sha1 para resumo da mensagem e Rsa15 para codificação de chave.</span><span class="sxs-lookup"><span data-stu-id="ba5b5-145">Use Basic256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ba5b5-146">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="ba5b5-146">Basic192Rsa15</span></span>|<span data-ttu-id="ba5b5-147">Use Basic192 para criptografia de mensagem, Sha1 para resumo da mensagem e Rsa15 para codificação de chave.</span><span class="sxs-lookup"><span data-stu-id="ba5b5-147">Use Basic192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ba5b5-148">TripleDes</span><span class="sxs-lookup"><span data-stu-id="ba5b5-148">TripleDes</span></span>|<span data-ttu-id="ba5b5-149">Use a criptografia TripleDes, Sha1 para resumo da mensagem, Rsa-oaep mgf1p para codificação de chave.</span><span class="sxs-lookup"><span data-stu-id="ba5b5-149">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ba5b5-150">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="ba5b5-150">Basic128Rsa15</span></span>|<span data-ttu-id="ba5b5-151">Use Basic128 para criptografia de mensagem, Sha1 para resumo da mensagem e Rsa15 para codificação de chave.</span><span class="sxs-lookup"><span data-stu-id="ba5b5-151">Use Basic128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ba5b5-152">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="ba5b5-152">TripleDesRsa15</span></span>|<span data-ttu-id="ba5b5-153">Use a criptografia TripleDes, Sha1 para resumo da mensagem e Rsa15 para codificação de chave.</span><span class="sxs-lookup"><span data-stu-id="ba5b5-153">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ba5b5-154">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="ba5b5-154">Basic128Sha256</span></span>|<span data-ttu-id="ba5b5-155">Use Basic128 para criptografia de mensagem, Sha256 para resumo da mensagem e Rsa-oaep mgf1p para codificação de chave.</span><span class="sxs-lookup"><span data-stu-id="ba5b5-155">Use Basic128 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ba5b5-156">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="ba5b5-156">Basic192Sha256</span></span>|<span data-ttu-id="ba5b5-157">Use Basic192 para criptografia de mensagem, Sha256 para resumo da mensagem e Rsa-oaep mgf1p para codificação de chave.</span><span class="sxs-lookup"><span data-stu-id="ba5b5-157">Use Basic192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ba5b5-158">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="ba5b5-158">Basic256Sha256</span></span>|<span data-ttu-id="ba5b5-159">Use Basic256 para criptografia de mensagem, Sha256 para resumo da mensagem e Rsa-oaep mgf1p para codificação de chave.</span><span class="sxs-lookup"><span data-stu-id="ba5b5-159">Use Basic256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ba5b5-160">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="ba5b5-160">TripleDesSha256</span></span>|<span data-ttu-id="ba5b5-161">Use TripleDes para criptografia de mensagem, Sha256 para resumo da mensagem e Rsa-oaep mgf1p para codificação de chave.</span><span class="sxs-lookup"><span data-stu-id="ba5b5-161">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ba5b5-162">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="ba5b5-162">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="ba5b5-163">Use Basic128 para criptografia de mensagem, Sha256 para resumo da mensagem e Rsa15 para codificação de chave.</span><span class="sxs-lookup"><span data-stu-id="ba5b5-163">Use Basic128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ba5b5-164">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="ba5b5-164">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="ba5b5-165">Use Aes192 para criptografia de mensagem, Sha256 para resumo da mensagem e Rsa15 para codificação de chave.</span><span class="sxs-lookup"><span data-stu-id="ba5b5-165">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ba5b5-166">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="ba5b5-166">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="ba5b5-167">Use Basic256 para criptografia de mensagem, Sha256 para resumo da mensagem e Rsa15 para codificação de chave.</span><span class="sxs-lookup"><span data-stu-id="ba5b5-167">Use Basic256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ba5b5-168">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="ba5b5-168">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="ba5b5-169">Use TripleDes para criptografia de mensagem, Sha256 para resumo da mensagem e Rsa15 para codificação de chave.</span><span class="sxs-lookup"><span data-stu-id="ba5b5-169">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ba5b5-170">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ba5b5-170">Child Elements</span></span>  
  
|<span data-ttu-id="ba5b5-171">Elemento</span><span class="sxs-lookup"><span data-stu-id="ba5b5-171">Element</span></span>|<span data-ttu-id="ba5b5-172">Descrição</span><span class="sxs-lookup"><span data-stu-id="ba5b5-172">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ba5b5-173">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="ba5b5-173">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="ba5b5-174">Especifica uma coleção de tipos de declaração para essa associação.</span><span class="sxs-lookup"><span data-stu-id="ba5b5-174">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="ba5b5-175">Cada elemento é do tipo <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="ba5b5-175">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|<span data-ttu-id="ba5b5-176">emissor</span><span class="sxs-lookup"><span data-stu-id="ba5b5-176">issuer</span></span>|<span data-ttu-id="ba5b5-177">Especifica um ponto de extremidade que emite um token de segurança.</span><span class="sxs-lookup"><span data-stu-id="ba5b5-177">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="ba5b5-178">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="ba5b5-178">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|<span data-ttu-id="ba5b5-179">issuerMetadata</span><span class="sxs-lookup"><span data-stu-id="ba5b5-179">issuerMetadata</span></span>|<span data-ttu-id="ba5b5-180">Especifica o endereço do ponto de extremidade do emissor.</span><span class="sxs-lookup"><span data-stu-id="ba5b5-180">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="ba5b5-181">\<tokenRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="ba5b5-181">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="ba5b5-182">Uma coleção de parâmetros de solicitação de token.</span><span class="sxs-lookup"><span data-stu-id="ba5b5-182">A collection of token request parameters.</span></span> <span data-ttu-id="ba5b5-183">Cada parâmetro é um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="ba5b5-183">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ba5b5-184">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ba5b5-184">Parent Elements</span></span>  
  
|<span data-ttu-id="ba5b5-185">Elemento</span><span class="sxs-lookup"><span data-stu-id="ba5b5-185">Element</span></span>|<span data-ttu-id="ba5b5-186">Descrição</span><span class="sxs-lookup"><span data-stu-id="ba5b5-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ba5b5-187">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="ba5b5-187">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|<span data-ttu-id="ba5b5-188">Define as configurações de segurança para uma associação.</span><span class="sxs-lookup"><span data-stu-id="ba5b5-188">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ba5b5-189">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ba5b5-189">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>  
 <span data-ttu-id="ba5b5-190">`System.ServiceModel.Configuration.FederatedMessageSecurityElement`[Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)</span><span class="sxs-lookup"><span data-stu-id="ba5b5-190">`System.ServiceModel.Configuration.FederatedMessageSecurityElement` [Securing Services and Clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)</span></span>  
 [<span data-ttu-id="ba5b5-191">Associações</span><span class="sxs-lookup"><span data-stu-id="ba5b5-191">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="ba5b5-192">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="ba5b5-192">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="ba5b5-193">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="ba5b5-193">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="ba5b5-194">\<associação ></span><span class="sxs-lookup"><span data-stu-id="ba5b5-194">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
