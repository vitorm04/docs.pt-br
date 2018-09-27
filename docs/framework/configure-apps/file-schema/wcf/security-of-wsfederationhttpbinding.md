---
title: '&lt;segurança&gt; de &lt;wsFederationHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: a8e5e854-b8dc-4921-843d-34b6a4a6a8ba
author: BrucePerlerMS
ms.openlocfilehash: 7c7868561ea4d41b308d3bcd963e10e9b81df314
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2018
ms.locfileid: "47397131"
---
# <a name="ltsecuritygt-of-ltwsfederationhttpbindinggt"></a><span data-ttu-id="94e46-102">&lt;segurança&gt; de &lt;wsFederationHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="94e46-102">&lt;security&gt; of &lt;wsFederationHttpBinding&gt;</span></span>
<span data-ttu-id="94e46-103">Define as configurações de segurança de [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="94e46-103">Defines the security settings of the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="94e46-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="94e46-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="94e46-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="94e46-105">\<bindings></span></span>  
<span data-ttu-id="94e46-106">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="94e46-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="94e46-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="94e46-107">\<binding></span></span>  
<span data-ttu-id="94e46-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="94e46-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94e46-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="94e46-109">Syntax</span></span>  
  
```xml  
<wsFederationBinding>  
    <binding >  
       <security mode="None/Message/TransportWithMessageCredential">  
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
                                   X509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="94e46-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="94e46-110">Attributes and Elements</span></span>  
 <span data-ttu-id="94e46-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="94e46-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="94e46-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="94e46-112">Attributes</span></span>  
  
|<span data-ttu-id="94e46-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="94e46-113">Attribute</span></span>|<span data-ttu-id="94e46-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="94e46-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="94e46-115">Modo</span><span class="sxs-lookup"><span data-stu-id="94e46-115">Mode</span></span>|<span data-ttu-id="94e46-116">Opcional.</span><span class="sxs-lookup"><span data-stu-id="94e46-116">Optional.</span></span> <span data-ttu-id="94e46-117">Especifica o tipo de segurança que é aplicado.</span><span class="sxs-lookup"><span data-stu-id="94e46-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="94e46-118">O valor padrão é `Message`.</span><span class="sxs-lookup"><span data-stu-id="94e46-118">The default value is `Message`.</span></span> <span data-ttu-id="94e46-119">Esse atributo é do tipo <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="94e46-119">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="94e46-120">modo de atributo</span><span class="sxs-lookup"><span data-stu-id="94e46-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="94e46-121">Valor</span><span class="sxs-lookup"><span data-stu-id="94e46-121">Value</span></span>|<span data-ttu-id="94e46-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="94e46-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="94e46-123">Nenhum</span><span class="sxs-lookup"><span data-stu-id="94e46-123">None</span></span>|<span data-ttu-id="94e46-124">A mensagem SOAP não é segura durante a transferência.</span><span class="sxs-lookup"><span data-stu-id="94e46-124">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="94e46-125">Mensagem</span><span class="sxs-lookup"><span data-stu-id="94e46-125">Message</span></span>|<span data-ttu-id="94e46-126">São fornecidos os serviços de integridade, confidencialidade, autenticação de servidor e autenticação de cliente usando a segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="94e46-126">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="94e46-127">Por padrão, o corpo é criptografado e assinado.</span><span class="sxs-lookup"><span data-stu-id="94e46-127">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="94e46-128">O serviço precisa ser configurado com um certificado.</span><span class="sxs-lookup"><span data-stu-id="94e46-128">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="94e46-129">Autenticação de cliente baseia-se no token emitido ao cliente por um serviço de token de segurança</span><span class="sxs-lookup"><span data-stu-id="94e46-129">Client authentication is based on the token issued to the client by a security token service</span></span>|  
|<span data-ttu-id="94e46-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="94e46-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="94e46-131">A integridade, a confidencialidade e a autenticação de servidor são fornecidas por HTTPS.</span><span class="sxs-lookup"><span data-stu-id="94e46-131">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="94e46-132">O serviço precisa ser configurado com um certificado.</span><span class="sxs-lookup"><span data-stu-id="94e46-132">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="94e46-133">A autenticação de cliente é fornecida por meio de segurança de mensagens SOAP e é baseada no token emitido ao cliente por um serviço de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="94e46-133">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="94e46-134">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="94e46-134">Child Elements</span></span>  
  
|<span data-ttu-id="94e46-135">Elemento</span><span class="sxs-lookup"><span data-stu-id="94e46-135">Element</span></span>|<span data-ttu-id="94e46-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="94e46-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="94e46-137">\<message></span><span class="sxs-lookup"><span data-stu-id="94e46-137">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="94e46-138">Define as configurações para a segurança de nível de mensagem.</span><span class="sxs-lookup"><span data-stu-id="94e46-138">Defines the settings for the message-level security.</span></span> <span data-ttu-id="94e46-139">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="94e46-139">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="94e46-140">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="94e46-140">Parent Elements</span></span>  
  
|<span data-ttu-id="94e46-141">Elemento</span><span class="sxs-lookup"><span data-stu-id="94e46-141">Element</span></span>|<span data-ttu-id="94e46-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="94e46-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="94e46-143">\<associação ></span><span class="sxs-lookup"><span data-stu-id="94e46-143">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="94e46-144">Define todos os recursos de associação do [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="94e46-144">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="94e46-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="94e46-145">See Also</span></span>  
 <xref:System.ServiceModel.WSFederationHttpSecurity>  
 <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>  
 [<span data-ttu-id="94e46-146">Como criar um WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="94e46-146">How to: Create a WSFederationHttpBinding</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 [<span data-ttu-id="94e46-147">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="94e46-147">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="94e46-148">Selecionando um tipo de credencial</span><span class="sxs-lookup"><span data-stu-id="94e46-148">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="94e46-149">Associações</span><span class="sxs-lookup"><span data-stu-id="94e46-149">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="94e46-150">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="94e46-150">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="94e46-151">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="94e46-151">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="94e46-152">\<associação ></span><span class="sxs-lookup"><span data-stu-id="94e46-152">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
