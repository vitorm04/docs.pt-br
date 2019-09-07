---
title: <issuedTokenAuthentication> de <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 5c2e288f-f603-4d13-839a-0fd6d1981bec
ms.openlocfilehash: 6d468a27ee05fb4dd8cf087d10e5d170783d3454
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400352"
---
# <a name="issuedtokenauthentication-of-servicecredentials"></a><span data-ttu-id="d101a-102">\<issuedTokenAuthentication > de \<ServiceCredentials ></span><span class="sxs-lookup"><span data-stu-id="d101a-102">\<issuedTokenAuthentication> of \<serviceCredentials></span></span>
<span data-ttu-id="d101a-103">Especifica um token personalizado emitido como uma credencial de serviço.</span><span class="sxs-lookup"><span data-stu-id="d101a-103">Specifies a custom token issued as a service credential.</span></span>  
  
<span data-ttu-id="d101a-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d101a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d101a-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="d101a-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d101a-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="d101a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="d101a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de portais**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="d101a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="d101a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="d101a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="d101a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="d101a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="d101a-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> issuedTokenAuthentication**</span><span class="sxs-lookup"><span data-stu-id="d101a-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedTokenAuthentication>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d101a-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d101a-111">Syntax</span></span>  
  
```xml  
<issuedTokenAuthentication allowUntrustedRsaIssuers="Boolean"
                           audienceUriMode="Always/BearerKeyOnly/Never"
                           customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                           certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                           revocationMode="NoCheck/Online/Offline"
                           samlSerializer="String"
                           trustedStoreLocation="CurrentUser/LocalMachine">
  <allowedAudienceUris>
    <add allowedAudienceUri="String" />
  </allowedAudienceUris>
  <knownCertificates>
    <add findValue="String"
         storeLocation="CurrentUser/LocalMachine"
         storeName=" CurrentUser/LocalMachine"
         x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
  </knownCertificates>
</issuedTokenAuthentication>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d101a-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d101a-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d101a-113">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="d101a-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d101a-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="d101a-114">Attributes</span></span>  
  
|<span data-ttu-id="d101a-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="d101a-115">Attribute</span></span>|<span data-ttu-id="d101a-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="d101a-116">Description</span></span>|  
|---------------|-----------------|  
|`allowedAudienceUris`|<span data-ttu-id="d101a-117">Obtém o conjunto de URIs de destino para o <xref:System.IdentityModel.Tokens.SamlSecurityToken> qual o token de segurança pode ser direcionado para ser considerado válido por <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> uma instância.</span><span class="sxs-lookup"><span data-stu-id="d101a-117">Gets the set of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span> <span data-ttu-id="d101a-118">Para obter mais informações sobre como usar esse atributo <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>, consulte.</span><span class="sxs-lookup"><span data-stu-id="d101a-118">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.</span></span>|  
|`allowUntrustedRsaIssuers`|<span data-ttu-id="d101a-119">Um valor booliano que especifica se os emissores de certificado RSA não confiáveis são permitidos.</span><span class="sxs-lookup"><span data-stu-id="d101a-119">A Boolean value that specifies if untrusted RSA certificate issuers are allowed.</span></span><br /><br /> <span data-ttu-id="d101a-120">Os certificados são assinados por autoridades de certificação (CAs) para verificar a autenticidade.</span><span class="sxs-lookup"><span data-stu-id="d101a-120">Certificates are signed by certification authorities (CAs) to verify authenticity.</span></span> <span data-ttu-id="d101a-121">Um emissor não confiável é uma AC que não é especificada para ser confiável para assinar certificados.</span><span class="sxs-lookup"><span data-stu-id="d101a-121">An untrusted issuer is a CA that is not specified to be trusted to sign certificates.</span></span>|  
|`audienceUriMode`|<span data-ttu-id="d101a-122">Obtém um valor que especifica se o <xref:System.IdentityModel.Tokens.SamlSecurityToken> <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> token de segurança deve ser validado.</span><span class="sxs-lookup"><span data-stu-id="d101a-122">Gets a value that specifies whether the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token's <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> should be validated.</span></span> <span data-ttu-id="d101a-123">Esse valor é do tipo <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span><span class="sxs-lookup"><span data-stu-id="d101a-123">This value is of type <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span></span> <span data-ttu-id="d101a-124">Para obter mais informações sobre como usar esse atributo <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>, consulte.</span><span class="sxs-lookup"><span data-stu-id="d101a-124">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="d101a-125">Define o modo de validação de certificado.</span><span class="sxs-lookup"><span data-stu-id="d101a-125">Sets the certificate validation mode.</span></span> <span data-ttu-id="d101a-126">Um dos valores válidos de <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="d101a-126">One of the valid values of <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="d101a-127">Se definido como `Custom`, um `customCertificateValidator` também deverá ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="d101a-127">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="d101a-128">O padrão é `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="d101a-128">The default is `ChainTrust`.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="d101a-129">Cadeia de caracteres opcional.</span><span class="sxs-lookup"><span data-stu-id="d101a-129">Optional string.</span></span> <span data-ttu-id="d101a-130">Um tipo e um assembly usados para validar um tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="d101a-130">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="d101a-131">Esse atributo deve ser definido quando `certificateValidationMode` é definido como `Custom`.</span><span class="sxs-lookup"><span data-stu-id="d101a-131">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`revocationMode`|<span data-ttu-id="d101a-132">Define o modo de revogação que especifica se uma verificação de revogação ocorre e se é executada online ou offline.</span><span class="sxs-lookup"><span data-stu-id="d101a-132">Sets the revocation mode that specifies whether a revocation check occurs, and if it is performed online or offline.</span></span> <span data-ttu-id="d101a-133">Esse atributo é do tipo <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="d101a-133">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span>|  
|`samlSerializer`|<span data-ttu-id="d101a-134">Um atributo de cadeia de caracteres opcional que especifica o tipo de SamlSerializer que é usado para a credencial de serviço.</span><span class="sxs-lookup"><span data-stu-id="d101a-134">An optional string attribute that specifies the type of SamlSerializer that is used for the service credential.</span></span> <span data-ttu-id="d101a-135">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="d101a-135">The default is an empty string.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="d101a-136">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="d101a-136">Optional enumeration.</span></span> <span data-ttu-id="d101a-137">Um dos dois locais de armazenamento do sistema `LocalMachine` : `CurrentUser`ou.</span><span class="sxs-lookup"><span data-stu-id="d101a-137">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d101a-138">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d101a-138">Child Elements</span></span>  
  
|<span data-ttu-id="d101a-139">Elemento</span><span class="sxs-lookup"><span data-stu-id="d101a-139">Element</span></span>|<span data-ttu-id="d101a-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="d101a-140">Description</span></span>|  
|-------------|-----------------|  
|`knownCertificates`|<span data-ttu-id="d101a-141">Especifica uma coleção de <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> elementos que especifica emissores confiáveis para a credencial de serviço.</span><span class="sxs-lookup"><span data-stu-id="d101a-141">Specifies a collection of <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> elements that specifies trusted issuers for the service credential.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d101a-142">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d101a-142">Parent Elements</span></span>  
  
|<span data-ttu-id="d101a-143">Elemento</span><span class="sxs-lookup"><span data-stu-id="d101a-143">Element</span></span>|<span data-ttu-id="d101a-144">Descrição</span><span class="sxs-lookup"><span data-stu-id="d101a-144">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d101a-145">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="d101a-145">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="d101a-146">Especifica a credencial a ser usada na autenticação do serviço e as configurações relacionadas à validação da credencial do cliente.</span><span class="sxs-lookup"><span data-stu-id="d101a-146">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d101a-147">Comentários</span><span class="sxs-lookup"><span data-stu-id="d101a-147">Remarks</span></span>  
 <span data-ttu-id="d101a-148">O cenário de token emitido tem três estágios.</span><span class="sxs-lookup"><span data-stu-id="d101a-148">The issued token scenario has three stages.</span></span> <span data-ttu-id="d101a-149">No primeiro estágio, um cliente que tenta acessar um serviço é chamado de um *serviço de token seguro*.</span><span class="sxs-lookup"><span data-stu-id="d101a-149">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="d101a-150">O serviço de token seguro autentica o cliente e subsequentemente emite um token do cliente, normalmente um token SAML (Security Assertion Markup Language).</span><span class="sxs-lookup"><span data-stu-id="d101a-150">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="d101a-151">O cliente retorna ao serviço com o token.</span><span class="sxs-lookup"><span data-stu-id="d101a-151">The client then returns to the service with the token.</span></span> <span data-ttu-id="d101a-152">O serviço examina o token de dados que permite que o serviço autentique o token e, portanto, o cliente.</span><span class="sxs-lookup"><span data-stu-id="d101a-152">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="d101a-153">Para autenticar o token, o certificado que o serviço de token seguro usa deve ser conhecido pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="d101a-153">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="d101a-154">Esse elemento é o repositório para qualquer um desses certificados de serviço de token seguro.</span><span class="sxs-lookup"><span data-stu-id="d101a-154">This element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="d101a-155">Para adicionar certificados, use o [ \<> knownCertificates](knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="d101a-155">To add certificates, use the [\<knownCertificates>](knowncertificates.md).</span></span> <span data-ttu-id="d101a-156">Insira um [ \<> Adicionar](add-of-knowncertificates.md) para cada certificado, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="d101a-156">Insert an [\<add>](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
```xml  
<issuedTokenAuthentication>
  <knownCertificates>
    <add findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="My"
         X509FindType="FindBySubjectName" />
  </knownCertificates>
</issuedTokenAuthentication>
```  
  
 <span data-ttu-id="d101a-157">Por padrão, os certificados devem ser obtidos de um serviço de token seguro.</span><span class="sxs-lookup"><span data-stu-id="d101a-157">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="d101a-158">Esses certificados "conhecidos" garantem que somente clientes legítimos possam acessar um serviço.</span><span class="sxs-lookup"><span data-stu-id="d101a-158">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="d101a-159">Para obter mais informações sobre como usar esse elemento de [configuração, consulte Como: Configure as credenciais em um](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)serviço de Federação.</span><span class="sxs-lookup"><span data-stu-id="d101a-159">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d101a-160">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d101a-160">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>
- [<span data-ttu-id="d101a-161">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="d101a-161">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="d101a-162">Como: Configurar credenciais em um Serviço de Federação</span><span class="sxs-lookup"><span data-stu-id="d101a-162">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
