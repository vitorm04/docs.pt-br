---
title: <security> de <wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: a8e5e854-b8dc-4921-843d-34b6a4a6a8ba
ms.openlocfilehash: ea029444cee331a235c7a2fc140b4321d7530063
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736320"
---
# <a name="security-of-wsfederationhttpbinding"></a><span data-ttu-id="a7cf1-102">\<security> de \<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="a7cf1-102">\<security> of \<wsFederationHttpBinding></span></span>
<span data-ttu-id="a7cf1-103">Define as configurações de segurança do [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="a7cf1-103">Defines the security settings of the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="a7cf1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a7cf1-104">Syntax</span></span>  
  
```xml  
<wsFederationBinding>
  <binding>
    <security mode="None/Message/TransportWithMessageCredential">
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey"
               negotiateServiceCredential="Boolean">
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7cf1-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a7cf1-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a7cf1-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a7cf1-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7cf1-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="a7cf1-107">Attributes</span></span>  
  
|<span data-ttu-id="a7cf1-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="a7cf1-108">Attribute</span></span>|<span data-ttu-id="a7cf1-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="a7cf1-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a7cf1-110">Mode</span><span class="sxs-lookup"><span data-stu-id="a7cf1-110">Mode</span></span>|<span data-ttu-id="a7cf1-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="a7cf1-111">Optional.</span></span> <span data-ttu-id="a7cf1-112">Especifica o tipo de segurança que é aplicado.</span><span class="sxs-lookup"><span data-stu-id="a7cf1-112">Specifies the type of security that is applied.</span></span> <span data-ttu-id="a7cf1-113">O valor padrão é `Message`.</span><span class="sxs-lookup"><span data-stu-id="a7cf1-113">The default value is `Message`.</span></span> <span data-ttu-id="a7cf1-114">Esse atributo é do tipo <xref:System.ServiceModel.WSFederationHttpSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="a7cf1-114">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="a7cf1-115">Atributo Mode</span><span class="sxs-lookup"><span data-stu-id="a7cf1-115">Mode Attribute</span></span>  
  
|<span data-ttu-id="a7cf1-116">Valor</span><span class="sxs-lookup"><span data-stu-id="a7cf1-116">Value</span></span>|<span data-ttu-id="a7cf1-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="a7cf1-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a7cf1-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a7cf1-118">None</span></span>|<span data-ttu-id="a7cf1-119">A mensagem SOAP não é segura durante a transferência.</span><span class="sxs-lookup"><span data-stu-id="a7cf1-119">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="a7cf1-120">Mensagem</span><span class="sxs-lookup"><span data-stu-id="a7cf1-120">Message</span></span>|<span data-ttu-id="a7cf1-121">São fornecidos os serviços de integridade, confidencialidade, autenticação de servidor e autenticação de cliente usando a segurança de mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="a7cf1-121">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="a7cf1-122">Por padrão, o corpo é criptografado e assinado.</span><span class="sxs-lookup"><span data-stu-id="a7cf1-122">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="a7cf1-123">O serviço precisa ser configurado com um certificado.</span><span class="sxs-lookup"><span data-stu-id="a7cf1-123">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="a7cf1-124">A autenticação de cliente é baseada no token emitido para o cliente por um serviço de token de segurança</span><span class="sxs-lookup"><span data-stu-id="a7cf1-124">Client authentication is based on the token issued to the client by a security token service</span></span>|  
|<span data-ttu-id="a7cf1-125">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="a7cf1-125">TransportWithMessageCredential</span></span>|<span data-ttu-id="a7cf1-126">A integridade, a confidencialidade e a autenticação de servidor são fornecidas por HTTPS.</span><span class="sxs-lookup"><span data-stu-id="a7cf1-126">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="a7cf1-127">O serviço precisa ser configurado com um certificado.</span><span class="sxs-lookup"><span data-stu-id="a7cf1-127">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="a7cf1-128">A autenticação de cliente é fornecida por meio de segurança de mensagens SOAP e é baseada no token emitido ao cliente por um serviço de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="a7cf1-128">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a7cf1-129">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a7cf1-129">Child Elements</span></span>  
  
|<span data-ttu-id="a7cf1-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="a7cf1-130">Element</span></span>|<span data-ttu-id="a7cf1-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="a7cf1-131">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="a7cf1-132">Define as configurações para a segurança em nível de mensagem.</span><span class="sxs-lookup"><span data-stu-id="a7cf1-132">Defines the settings for the message-level security.</span></span> <span data-ttu-id="a7cf1-133">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement> .</span><span class="sxs-lookup"><span data-stu-id="a7cf1-133">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a7cf1-134">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a7cf1-134">Parent Elements</span></span>  
  
|<span data-ttu-id="a7cf1-135">Elemento</span><span class="sxs-lookup"><span data-stu-id="a7cf1-135">Element</span></span>|<span data-ttu-id="a7cf1-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="a7cf1-136">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="a7cf1-137">Define todos os recursos de associação do [\<wsDualHttpBinding>](wsdualhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="a7cf1-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a7cf1-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="a7cf1-138">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="a7cf1-139">Como criar um WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="a7cf1-139">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="a7cf1-140">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="a7cf1-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="a7cf1-141">Selecionando um tipo de credencial</span><span class="sxs-lookup"><span data-stu-id="a7cf1-141">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="a7cf1-142">Associações</span><span class="sxs-lookup"><span data-stu-id="a7cf1-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a7cf1-143">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="a7cf1-143">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a7cf1-144">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="a7cf1-144">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
