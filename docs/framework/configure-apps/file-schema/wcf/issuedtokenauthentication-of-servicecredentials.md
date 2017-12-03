---
title: '&lt;issuedTokenAuthentication&gt; de &lt;serviceCredentials&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c2e288f-f603-4d13-839a-0fd6d1981bec
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 75c3caa128018877b95824b4bad34aee331c4dab
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltissuedtokenauthenticationgt-of-ltservicecredentialsgt"></a><span data-ttu-id="ef5c1-102">&lt;issuedTokenAuthentication&gt; de &lt;serviceCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="ef5c1-102">&lt;issuedTokenAuthentication&gt; of &lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="ef5c1-103">Especifica um token personalizado emitido como uma credencial de serviço.</span><span class="sxs-lookup"><span data-stu-id="ef5c1-103">Specifies a custom token issued as a service credential.</span></span>  
  
 <span data-ttu-id="ef5c1-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="ef5c1-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ef5c1-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="ef5c1-105">\<behaviors></span></span>  
<span data-ttu-id="ef5c1-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="ef5c1-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="ef5c1-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="ef5c1-107">\<behavior></span></span>  
<span data-ttu-id="ef5c1-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="ef5c1-108">\<serviceCredentials></span></span>  
<span data-ttu-id="ef5c1-109">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="ef5c1-109">\<issuedTokenAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef5c1-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ef5c1-110">Syntax</span></span>  
  
```xml  
<issuedTokenAuthentication   
   allowUntrustedRsaIssuers="Boolean"  
   audienceUriMode="Always/BearerKeyOnly/Never"  
      customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
   revocationMode="NoCheck/Online/Offline"  
   samlSerializer="String"  
    trustedStoreLocation="CurrentUser/LocalMachine">  
      <allowedAudienceUris>  
      <add allowedAudienceUri="String"/>  
      </allowedAudienceUris>  
      <knownCertificates>   
         <add findValue="String"  
                 storeLocation="CurrentUser/LocalMachine"  
                storeName=" CurrentUser/LocalMachine"  
                x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>  
      </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ef5c1-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ef5c1-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ef5c1-112">As seções a seguir descrevem os elementos pai de atributos e elementos filho</span><span class="sxs-lookup"><span data-stu-id="ef5c1-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ef5c1-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="ef5c1-113">Attributes</span></span>  
  
|<span data-ttu-id="ef5c1-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="ef5c1-114">Attribute</span></span>|<span data-ttu-id="ef5c1-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="ef5c1-115">Description</span></span>|  
|---------------|-----------------|  
|`allowedAudienceUris`|<span data-ttu-id="ef5c1-116">Obtém o conjunto de URIs de destino para o qual o <xref:System.IdentityModel.Tokens.SamlSecurityToken> token de segurança pode ser direcionado para ser considerado válido por um <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instância.</span><span class="sxs-lookup"><span data-stu-id="ef5c1-116">Gets the set of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span> <span data-ttu-id="ef5c1-117">Para obter mais informações sobre como usar esse atributo, consulte <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.</span><span class="sxs-lookup"><span data-stu-id="ef5c1-117">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.</span></span>|  
|`allowUntrustedRsaIssuers`|<span data-ttu-id="ef5c1-118">Um valor booleano que especifica se emissores de certificados RSA não confiáveis são permitidos.</span><span class="sxs-lookup"><span data-stu-id="ef5c1-118">A Boolean value that specifies if untrusted RSA certificate issuers are allowed.</span></span><br /><br /> <span data-ttu-id="ef5c1-119">Os certificados são assinados por autoridades de certificação (CAs) para verificar a autenticidade.</span><span class="sxs-lookup"><span data-stu-id="ef5c1-119">Certificates are signed by certification authorities (CAs) to verify authenticity.</span></span> <span data-ttu-id="ef5c1-120">Um emissor confiável é uma autoridade de certificação não for especificada para ser confiável para assinar certificados.</span><span class="sxs-lookup"><span data-stu-id="ef5c1-120">An untrusted issuer is a CA that is not specified to be trusted to sign certificates.</span></span>|  
|`audienceUriMode`|<span data-ttu-id="ef5c1-121">Obtém um valor que especifica se o <xref:System.IdentityModel.Tokens.SamlSecurityToken> do token de segurança <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> devem ser validadas.</span><span class="sxs-lookup"><span data-stu-id="ef5c1-121">Gets a value that specifies whether the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token's <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> should be validated.</span></span> <span data-ttu-id="ef5c1-122">Esse valor é do tipo <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span><span class="sxs-lookup"><span data-stu-id="ef5c1-122">This value is of type <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span></span> <span data-ttu-id="ef5c1-123">Para obter mais informações sobre como usar esse atributo, consulte <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="ef5c1-123">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="ef5c1-124">Define o modo de validação de certificado.</span><span class="sxs-lookup"><span data-stu-id="ef5c1-124">Sets the certificate validation mode.</span></span> <span data-ttu-id="ef5c1-125">Um dos valores válidos de <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="ef5c1-125">One of the valid values of <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="ef5c1-126">Se definido como `Custom`, em seguida, um `customCertificateValidator` também deve ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="ef5c1-126">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="ef5c1-127">O padrão é `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="ef5c1-127">The default is `ChainTrust`.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="ef5c1-128">Cadeia de caracteres opcional.</span><span class="sxs-lookup"><span data-stu-id="ef5c1-128">Optional string.</span></span> <span data-ttu-id="ef5c1-129">Um tipo e assembly usados para validar um tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="ef5c1-129">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="ef5c1-130">Esse atributo deve ser definido quando `certificateValidationMode` é definido como `Custom`.</span><span class="sxs-lookup"><span data-stu-id="ef5c1-130">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`revocationMode`|<span data-ttu-id="ef5c1-131">Define o modo de revogação que especifica se uma verificação de revogação ocorre, e se ela é executada online ou offline.</span><span class="sxs-lookup"><span data-stu-id="ef5c1-131">Sets the revocation mode that specifies whether a revocation check occurs, and if it is performed online or offline.</span></span> <span data-ttu-id="ef5c1-132">Esse atributo é do tipo <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="ef5c1-132">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span>|  
|`samlSerializer`|<span data-ttu-id="ef5c1-133">Um atributo de cadeia de caracteres opcional que especifica o tipo de classe SamlSerializer que é usado para a credencial de serviço.</span><span class="sxs-lookup"><span data-stu-id="ef5c1-133">An optional string attribute that specifies the type of SamlSerializer that is used for the service credential.</span></span> <span data-ttu-id="ef5c1-134">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="ef5c1-134">The default is an empty string.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="ef5c1-135">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="ef5c1-135">Optional enumeration.</span></span> <span data-ttu-id="ef5c1-136">Um dos locais de armazenamento de sistema de dois: `LocalMachine` ou `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="ef5c1-136">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ef5c1-137">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ef5c1-137">Child Elements</span></span>  
  
|<span data-ttu-id="ef5c1-138">Elemento</span><span class="sxs-lookup"><span data-stu-id="ef5c1-138">Element</span></span>|<span data-ttu-id="ef5c1-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="ef5c1-139">Description</span></span>|  
|-------------|-----------------|  
|`knownCertificates`|<span data-ttu-id="ef5c1-140">Especifica uma coleção de <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> elementos que especifica os emissores confiáveis para a credencial de serviço.</span><span class="sxs-lookup"><span data-stu-id="ef5c1-140">Specifies a collection of <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> elements that specifies trusted issuers for the service credential.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ef5c1-141">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ef5c1-141">Parent Elements</span></span>  
  
|<span data-ttu-id="ef5c1-142">Elemento</span><span class="sxs-lookup"><span data-stu-id="ef5c1-142">Element</span></span>|<span data-ttu-id="ef5c1-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="ef5c1-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ef5c1-144">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="ef5c1-144">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="ef5c1-145">Especifica a credencial a ser usado na autenticação do serviço e as configurações de relacionadas à validação de credenciais do cliente.</span><span class="sxs-lookup"><span data-stu-id="ef5c1-145">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef5c1-146">Comentários</span><span class="sxs-lookup"><span data-stu-id="ef5c1-146">Remarks</span></span>  
 <span data-ttu-id="ef5c1-147">O cenário de token emitido tem três etapas.</span><span class="sxs-lookup"><span data-stu-id="ef5c1-147">The issued token scenario has three stages.</span></span> <span data-ttu-id="ef5c1-148">O primeiro estágio, um cliente tentar acessar um serviço é chamado um *do serviço de token seguro*.</span><span class="sxs-lookup"><span data-stu-id="ef5c1-148">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="ef5c1-149">O serviço de token seguro, em seguida, autentica o cliente e subsequentemente emite para o cliente um token, normalmente um token de segurança asserções SAML (Markup Language).</span><span class="sxs-lookup"><span data-stu-id="ef5c1-149">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="ef5c1-150">O cliente, em seguida, retorne para o serviço com o token.</span><span class="sxs-lookup"><span data-stu-id="ef5c1-150">The client then returns to the service with the token.</span></span> <span data-ttu-id="ef5c1-151">O serviço examina o token de dados que permite que o serviço autenticar o token e, portanto, o cliente.</span><span class="sxs-lookup"><span data-stu-id="ef5c1-151">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="ef5c1-152">Para autenticar o token, o certificado usa o serviço de token seguro deve ser conhecida para o serviço.</span><span class="sxs-lookup"><span data-stu-id="ef5c1-152">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="ef5c1-153">Esse elemento é o repositório para todos esses certificados de serviço de token seguro.</span><span class="sxs-lookup"><span data-stu-id="ef5c1-153">This element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="ef5c1-154">Para adicionar certificados, use o [ \<knownCertificates >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="ef5c1-154">To add certificates, use the [\<knownCertificates>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span></span> <span data-ttu-id="ef5c1-155">Inserir uma [ \<Adicionar >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) para cada certificado, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ef5c1-155">Insert an [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
```xml  
<issuedTokenAuthorization>  
   <knownCertificates>  
      <add findValue="www.contoso.com"   
           storeLocation="LocalMachine" storeName="My"   
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 <span data-ttu-id="ef5c1-156">Por padrão, os certificados devem ser obtidos de um serviço de token seguro.</span><span class="sxs-lookup"><span data-stu-id="ef5c1-156">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="ef5c1-157">Esses "conhecidos" certificados Certifique-se de que apenas legítimas clientes podem acessar um serviço.</span><span class="sxs-lookup"><span data-stu-id="ef5c1-157">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="ef5c1-158">Para obter mais informações sobre como usar este elemento de configuração, consulte [como: configurar credenciais em um serviço de Federação](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="ef5c1-158">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef5c1-159">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ef5c1-159">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.IssuedTokenAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A>  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>  
 [<span data-ttu-id="ef5c1-160">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="ef5c1-160">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="ef5c1-161">Como: configurar as credenciais em um serviço de Federação</span><span class="sxs-lookup"><span data-stu-id="ef5c1-161">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
