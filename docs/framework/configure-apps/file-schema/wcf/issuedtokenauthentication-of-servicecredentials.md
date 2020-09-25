---
title: <issuedTokenAuthentication> de <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 5c2e288f-f603-4d13-839a-0fd6d1981bec
ms.openlocfilehash: 88657b6982108596c8d9030161390f76fcff6609
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202468"
---
# <a name="issuedtokenauthentication-of-servicecredentials"></a><span data-ttu-id="6e34a-102">\<issuedTokenAuthentication> de \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="6e34a-102">\<issuedTokenAuthentication> of \<serviceCredentials></span></span>

<span data-ttu-id="6e34a-103">Especifica um token personalizado emitido como uma credencial de serviço.</span><span class="sxs-lookup"><span data-stu-id="6e34a-103">Specifies a custom token issued as a service credential.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuedTokenAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="6e34a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6e34a-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6e34a-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6e34a-105">Attributes and Elements</span></span>  

 <span data-ttu-id="6e34a-106">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="6e34a-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6e34a-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="6e34a-107">Attributes</span></span>  
  
|<span data-ttu-id="6e34a-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="6e34a-108">Attribute</span></span>|<span data-ttu-id="6e34a-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e34a-109">Description</span></span>|  
|---------------|-----------------|  
|`allowedAudienceUris`|<span data-ttu-id="6e34a-110">Obtém o conjunto de URIs de destino para o qual o <xref:System.IdentityModel.Tokens.SamlSecurityToken> token de segurança pode ser direcionado para ser considerado válido por uma <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instância.</span><span class="sxs-lookup"><span data-stu-id="6e34a-110">Gets the set of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span> <span data-ttu-id="6e34a-111">Para obter mais informações sobre como usar esse atributo, consulte <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A> .</span><span class="sxs-lookup"><span data-stu-id="6e34a-111">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.</span></span>|  
|`allowUntrustedRsaIssuers`|<span data-ttu-id="6e34a-112">Um valor booliano que especifica se os emissores de certificado RSA não confiáveis são permitidos.</span><span class="sxs-lookup"><span data-stu-id="6e34a-112">A Boolean value that specifies if untrusted RSA certificate issuers are allowed.</span></span><br /><br /> <span data-ttu-id="6e34a-113">Os certificados são assinados por autoridades de certificação (CAs) para verificar a autenticidade.</span><span class="sxs-lookup"><span data-stu-id="6e34a-113">Certificates are signed by certification authorities (CAs) to verify authenticity.</span></span> <span data-ttu-id="6e34a-114">Um emissor não confiável é uma AC que não é especificada para ser confiável para assinar certificados.</span><span class="sxs-lookup"><span data-stu-id="6e34a-114">An untrusted issuer is a CA that is not specified to be trusted to sign certificates.</span></span>|  
|`audienceUriMode`|<span data-ttu-id="6e34a-115">Obtém um valor que especifica se o <xref:System.IdentityModel.Tokens.SamlSecurityToken> token de segurança <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> deve ser validado.</span><span class="sxs-lookup"><span data-stu-id="6e34a-115">Gets a value that specifies whether the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token's <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> should be validated.</span></span> <span data-ttu-id="6e34a-116">Esse valor é do tipo <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span><span class="sxs-lookup"><span data-stu-id="6e34a-116">This value is of type <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span></span> <span data-ttu-id="6e34a-117">Para obter mais informações sobre como usar esse atributo, consulte <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A> .</span><span class="sxs-lookup"><span data-stu-id="6e34a-117">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="6e34a-118">Define o modo de validação de certificado.</span><span class="sxs-lookup"><span data-stu-id="6e34a-118">Sets the certificate validation mode.</span></span> <span data-ttu-id="6e34a-119">Um dos valores válidos de <xref:System.ServiceModel.Security.X509CertificateValidationMode> .</span><span class="sxs-lookup"><span data-stu-id="6e34a-119">One of the valid values of <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="6e34a-120">Se definido como `Custom` , um `customCertificateValidator` também deverá ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="6e34a-120">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="6e34a-121">O padrão é `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="6e34a-121">The default is `ChainTrust`.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="6e34a-122">Cadeia de caracteres opcional.</span><span class="sxs-lookup"><span data-stu-id="6e34a-122">Optional string.</span></span> <span data-ttu-id="6e34a-123">Um tipo e um assembly usados para validar um tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="6e34a-123">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="6e34a-124">Esse atributo deve ser definido quando `certificateValidationMode` é definido como `Custom` .</span><span class="sxs-lookup"><span data-stu-id="6e34a-124">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`revocationMode`|<span data-ttu-id="6e34a-125">Define o modo de revogação que especifica se uma verificação de revogação ocorre e se é executada online ou offline.</span><span class="sxs-lookup"><span data-stu-id="6e34a-125">Sets the revocation mode that specifies whether a revocation check occurs, and if it is performed online or offline.</span></span> <span data-ttu-id="6e34a-126">Esse atributo é do tipo <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> .</span><span class="sxs-lookup"><span data-stu-id="6e34a-126">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span>|  
|`samlSerializer`|<span data-ttu-id="6e34a-127">Um atributo de cadeia de caracteres opcional que especifica o tipo de SamlSerializer que é usado para a credencial de serviço.</span><span class="sxs-lookup"><span data-stu-id="6e34a-127">An optional string attribute that specifies the type of SamlSerializer that is used for the service credential.</span></span> <span data-ttu-id="6e34a-128">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="6e34a-128">The default is an empty string.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="6e34a-129">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="6e34a-129">Optional enumeration.</span></span> <span data-ttu-id="6e34a-130">Um dos dois locais de armazenamento do sistema: `LocalMachine` ou `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="6e34a-130">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6e34a-131">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6e34a-131">Child Elements</span></span>  
  
|<span data-ttu-id="6e34a-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="6e34a-132">Element</span></span>|<span data-ttu-id="6e34a-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e34a-133">Description</span></span>|  
|-------------|-----------------|  
|`knownCertificates`|<span data-ttu-id="6e34a-134">Especifica uma coleção de <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> elementos que especifica emissores confiáveis para a credencial de serviço.</span><span class="sxs-lookup"><span data-stu-id="6e34a-134">Specifies a collection of <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> elements that specifies trusted issuers for the service credential.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6e34a-135">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6e34a-135">Parent Elements</span></span>  
  
|<span data-ttu-id="6e34a-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="6e34a-136">Element</span></span>|<span data-ttu-id="6e34a-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e34a-137">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="6e34a-138">Especifica a credencial a ser usada na autenticação do serviço e as configurações relacionadas à validação da credencial do cliente.</span><span class="sxs-lookup"><span data-stu-id="6e34a-138">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e34a-139">Comentários</span><span class="sxs-lookup"><span data-stu-id="6e34a-139">Remarks</span></span>  

 <span data-ttu-id="6e34a-140">O cenário de token emitido tem três estágios.</span><span class="sxs-lookup"><span data-stu-id="6e34a-140">The issued token scenario has three stages.</span></span> <span data-ttu-id="6e34a-141">No primeiro estágio, um cliente que tenta acessar um serviço é chamado de um *serviço de token seguro*.</span><span class="sxs-lookup"><span data-stu-id="6e34a-141">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="6e34a-142">O serviço de token seguro autentica o cliente e subsequentemente emite um token do cliente, normalmente um token SAML (Security Assertion Markup Language).</span><span class="sxs-lookup"><span data-stu-id="6e34a-142">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="6e34a-143">O cliente retorna ao serviço com o token.</span><span class="sxs-lookup"><span data-stu-id="6e34a-143">The client then returns to the service with the token.</span></span> <span data-ttu-id="6e34a-144">O serviço examina o token de dados que permite que o serviço autentique o token e, portanto, o cliente.</span><span class="sxs-lookup"><span data-stu-id="6e34a-144">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="6e34a-145">Para autenticar o token, o certificado que o serviço de token seguro usa deve ser conhecido pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="6e34a-145">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="6e34a-146">Esse elemento é o repositório para qualquer um desses certificados de serviço de token seguro.</span><span class="sxs-lookup"><span data-stu-id="6e34a-146">This element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="6e34a-147">Para adicionar certificados, use o [\<knownCertificates>](knowncertificates.md) .</span><span class="sxs-lookup"><span data-stu-id="6e34a-147">To add certificates, use the [\<knownCertificates>](knowncertificates.md).</span></span> <span data-ttu-id="6e34a-148">Insira um [\<add>](add-of-knowncertificates.md) para cada certificado, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="6e34a-148">Insert an [\<add>](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="6e34a-149">Por padrão, os certificados devem ser obtidos de um serviço de token seguro.</span><span class="sxs-lookup"><span data-stu-id="6e34a-149">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="6e34a-150">Esses certificados "conhecidos" garantem que somente clientes legítimos possam acessar um serviço.</span><span class="sxs-lookup"><span data-stu-id="6e34a-150">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="6e34a-151">Para obter mais informações sobre como usar esse elemento de configuração, consulte [How to: Configure Credentials on a serviço de Federação](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="6e34a-151">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e34a-152">Veja também</span><span class="sxs-lookup"><span data-stu-id="6e34a-152">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>
- [<span data-ttu-id="6e34a-153">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="6e34a-153">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="6e34a-154">Como: configurar credenciais em um serviço de federação</span><span class="sxs-lookup"><span data-stu-id="6e34a-154">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
