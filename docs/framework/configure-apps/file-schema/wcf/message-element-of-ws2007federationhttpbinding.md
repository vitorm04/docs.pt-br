---
title: elemento de &lt;mensagem&gt; de &lt;ws2007FederationHttpBinding&gt;
ms.date: 03/30/2017
ms.assetid: 52cd941d-e230-4c82-8b29-333a7d20eca8
ms.openlocfilehash: 6954a7b9646b35ee03aab311deae026a711be9cd
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2018
ms.locfileid: "48847536"
---
# <a name="ltmessagegt-element-of-ltws2007federationhttpbindinggt"></a><span data-ttu-id="ed054-102">elemento de &lt;mensagem&gt; de &lt;ws2007FederationHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="ed054-102">&lt;message&gt; element of &lt;ws2007FederationHttpBinding&gt;</span></span>
<span data-ttu-id="ed054-103">Define as configurações para a segurança de nível de mensagem para o [ \<ws2007FederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="ed054-103">Defines settings for the message-level security for the [\<ws2007FederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) element.</span></span>  
  
 <span data-ttu-id="ed054-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ed054-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ed054-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="ed054-105">\<bindings></span></span>  
<span data-ttu-id="ed054-106">\<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="ed054-106">\<ws2007FederationHttpBinding></span></span>  
<span data-ttu-id="ed054-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="ed054-107">\<binding></span></span>  
<span data-ttu-id="ed054-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="ed054-108">\<security></span></span>  
<span data-ttu-id="ed054-109">\<message></span><span class="sxs-lookup"><span data-stu-id="ed054-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed054-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ed054-110">Syntax</span></span>  
  
```xml  
<ws2007FederationBinding>  
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
</ws2007FederationBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ed054-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ed054-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ed054-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ed054-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ed054-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="ed054-113">Attributes</span></span>  
  
|<span data-ttu-id="ed054-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="ed054-114">Attribute</span></span>|<span data-ttu-id="ed054-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="ed054-115">Description</span></span>|  
|---------------|-----------------|  
|`algorithmSuite`|<span data-ttu-id="ed054-116">Opcional.</span><span class="sxs-lookup"><span data-stu-id="ed054-116">Optional.</span></span> <span data-ttu-id="ed054-117">Define a criptografia de mensagens, a assinatura e algoritmos de encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="ed054-117">Sets the message encryption, signature, and key-wrap algorithms.</span></span> <span data-ttu-id="ed054-118">Os algoritmos e os tamanhos de chave são determinados pelo <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> classe.</span><span class="sxs-lookup"><span data-stu-id="ed054-118">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="ed054-119">Esses algoritmos são mapeados para aqueles especificados na especificação da linguagem de política de segurança (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="ed054-119">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="ed054-120">Consulte a tabela a seguir para os valores possíveis.</span><span class="sxs-lookup"><span data-stu-id="ed054-120">See the following table for possible values.</span></span> <span data-ttu-id="ed054-121">O valor padrão é Basic256.</span><span class="sxs-lookup"><span data-stu-id="ed054-121">The default value is Basic256.</span></span>|  
|`issuedKeyType`|<span data-ttu-id="ed054-122">Especifica o tipo de chave a ser emitida.</span><span class="sxs-lookup"><span data-stu-id="ed054-122">Specifies the type of key to be issued.</span></span> <span data-ttu-id="ed054-123">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ed054-123">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ed054-124">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="ed054-124">-   SymmetricKey</span></span><br /><span data-ttu-id="ed054-125">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="ed054-125">-   PublicKey</span></span><br /><span data-ttu-id="ed054-126">-BearerKey</span><span class="sxs-lookup"><span data-stu-id="ed054-126">-   BearerKey</span></span><br /><br /> <span data-ttu-id="ed054-127">O padrão é SymmetricKey.</span><span class="sxs-lookup"><span data-stu-id="ed054-127">The default is SymmetricKey.</span></span> <span data-ttu-id="ed054-128">Esse atributo é do tipo <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="ed054-128">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|`issuedTokenType`|<span data-ttu-id="ed054-129">Um URI que especifica o tipo de token a ser emitido.</span><span class="sxs-lookup"><span data-stu-id="ed054-129">A URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="ed054-130">O padrão é `null`.</span><span class="sxs-lookup"><span data-stu-id="ed054-130">The default is `null`.</span></span>|  
|`negotiateServiceCredential`|<span data-ttu-id="ed054-131">Um valor que especifica se a credencial de serviço deve ser trocada como parte da negociação ou está disponível fora da banda.</span><span class="sxs-lookup"><span data-stu-id="ed054-131">A value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="ed054-132">O padrão é `true`, o que significa que a credencial de serviço é negociada.</span><span class="sxs-lookup"><span data-stu-id="ed054-132">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="ed054-133">algorithmSuite atributo</span><span class="sxs-lookup"><span data-stu-id="ed054-133">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="ed054-134">Valor</span><span class="sxs-lookup"><span data-stu-id="ed054-134">Value</span></span>|<span data-ttu-id="ed054-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="ed054-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ed054-136">Basic128</span><span class="sxs-lookup"><span data-stu-id="ed054-136">Basic128</span></span>|<span data-ttu-id="ed054-137">Use criptografia Aes128, Sha1 de resumo da mensagem e Rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="ed054-137">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ed054-138">Basic192</span><span class="sxs-lookup"><span data-stu-id="ed054-138">Basic192</span></span>|<span data-ttu-id="ed054-139">Use a criptografia Aes192, Sha1 para o message digest, Rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="ed054-139">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ed054-140">Basic256</span><span class="sxs-lookup"><span data-stu-id="ed054-140">Basic256</span></span>|<span data-ttu-id="ed054-141">Use a criptografia Aes256, Sha1 para o message digest, Rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="ed054-141">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ed054-142">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="ed054-142">Basic256Rsa15</span></span>|<span data-ttu-id="ed054-143">Use Aes256 para criptografia de mensagem, Sha1 de resumo da mensagem e Rsa15 para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="ed054-143">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ed054-144">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="ed054-144">Basic192Rsa15</span></span>|<span data-ttu-id="ed054-145">Use Aes192 para criptografia de mensagem, Sha1 de resumo da mensagem e Rsa15 para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="ed054-145">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ed054-146">TripleDes</span><span class="sxs-lookup"><span data-stu-id="ed054-146">TripleDes</span></span>|<span data-ttu-id="ed054-147">Use a criptografia TripleDes, Sha1 para o message digest, Rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="ed054-147">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ed054-148">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="ed054-148">Basic128Rsa15</span></span>|<span data-ttu-id="ed054-149">Use Aes128 para criptografia de mensagem, Sha1 de resumo da mensagem e Rsa15 para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="ed054-149">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ed054-150">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="ed054-150">TripleDesRsa15</span></span>|<span data-ttu-id="ed054-151">Use a criptografia TripleDes, Sha1 de resumo da mensagem e Rsa15 para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="ed054-151">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ed054-152">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="ed054-152">Basic128Sha256</span></span>|<span data-ttu-id="ed054-153">Use Aes256 para criptografia de mensagem, o Sha256 para o resumo da mensagem e Rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="ed054-153">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ed054-154">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="ed054-154">Basic192Sha256</span></span>|<span data-ttu-id="ed054-155">Use Aes192 para criptografia de mensagem, o Sha256 para o resumo da mensagem e Rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="ed054-155">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ed054-156">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="ed054-156">Basic256Sha256</span></span>|<span data-ttu-id="ed054-157">Use Aes256 para criptografia de mensagem, o Sha256 para o resumo da mensagem e Rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="ed054-157">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ed054-158">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="ed054-158">TripleDesSha256</span></span>|<span data-ttu-id="ed054-159">Use triplo DES para criptografia de mensagem, o Sha256 para o resumo da mensagem e Rsa-oaep-mgf1p para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="ed054-159">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="ed054-160">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="ed054-160">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="ed054-161">Use Aes128 para criptografia de mensagem, o Sha256 para o resumo da mensagem e Rsa15 para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="ed054-161">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ed054-162">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="ed054-162">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="ed054-163">Use Aes192 para criptografia de mensagem, o Sha256 para o resumo da mensagem e Rsa15 para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="ed054-163">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ed054-164">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="ed054-164">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="ed054-165">Use Aes256 para criptografia de mensagem, o Sha256 para o resumo da mensagem e Rsa15 para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="ed054-165">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="ed054-166">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="ed054-166">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="ed054-167">Use o triplo DES para criptografia de mensagem, o Sha256 para o resumo da mensagem e Rsa15 para encapsulamento de chave.</span><span class="sxs-lookup"><span data-stu-id="ed054-167">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ed054-168">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ed054-168">Child Elements</span></span>  
  
|<span data-ttu-id="ed054-169">Elemento</span><span class="sxs-lookup"><span data-stu-id="ed054-169">Element</span></span>|<span data-ttu-id="ed054-170">Descrição</span><span class="sxs-lookup"><span data-stu-id="ed054-170">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ed054-171">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="ed054-171">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="ed054-172">Especifica uma coleção de tipos de declaração para essa associação.</span><span class="sxs-lookup"><span data-stu-id="ed054-172">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="ed054-173">Cada elemento é do tipo <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="ed054-173">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|[<span data-ttu-id="ed054-174">\<issuer></span><span class="sxs-lookup"><span data-stu-id="ed054-174">\<issuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md)|<span data-ttu-id="ed054-175">Especifica um ponto de extremidade que emite um token de segurança.</span><span class="sxs-lookup"><span data-stu-id="ed054-175">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="ed054-176">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="ed054-176">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|[<span data-ttu-id="ed054-177">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="ed054-177">\<issuerMetadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md)|<span data-ttu-id="ed054-178">Especifica o endereço do ponto de extremidade do emissor.</span><span class="sxs-lookup"><span data-stu-id="ed054-178">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="ed054-179">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="ed054-179">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="ed054-180">Uma coleção de parâmetros de solicitação de token.</span><span class="sxs-lookup"><span data-stu-id="ed054-180">A collection of token request parameters.</span></span> <span data-ttu-id="ed054-181">Cada parâmetro é um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="ed054-181">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ed054-182">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ed054-182">Parent Elements</span></span>  
  
|<span data-ttu-id="ed054-183">Elemento</span><span class="sxs-lookup"><span data-stu-id="ed054-183">Element</span></span>|<span data-ttu-id="ed054-184">Descrição</span><span class="sxs-lookup"><span data-stu-id="ed054-184">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ed054-185">\<security></span><span class="sxs-lookup"><span data-stu-id="ed054-185">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)|<span data-ttu-id="ed054-186">Define as configurações de segurança para uma associação.</span><span class="sxs-lookup"><span data-stu-id="ed054-186">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ed054-187">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ed054-187">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>  
 <span data-ttu-id="ed054-188">`System.ServiceModel.Configuration.FederatedMessageSecurityElement` [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)</span><span class="sxs-lookup"><span data-stu-id="ed054-188">`System.ServiceModel.Configuration.FederatedMessageSecurityElement` [Securing Services and Clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)</span></span>  
 [<span data-ttu-id="ed054-189">Associações</span><span class="sxs-lookup"><span data-stu-id="ed054-189">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="ed054-190">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="ed054-190">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="ed054-191">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="ed054-191">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="ed054-192">\<associação ></span><span class="sxs-lookup"><span data-stu-id="ed054-192">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
