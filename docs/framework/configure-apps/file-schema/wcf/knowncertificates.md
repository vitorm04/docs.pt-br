---
title: <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 678e21b4-6493-47c3-8359-fcf0d37e2138
ms.openlocfilehash: 5c20baecf3e9fe83385c986e3fb58f0c03eeeb47
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224189"
---
# <a name="knowncertificates"></a><span data-ttu-id="70a48-101">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="70a48-101">\<knownCertificates></span></span>
<span data-ttu-id="70a48-102">Representa uma coleção de certificados X.509 que são fornecidos para autenticar as credenciais de segurança emitidas de um Security Token Service (STS).</span><span class="sxs-lookup"><span data-stu-id="70a48-102">Represents a collection of X.509 certificates that are provided to authenticate security credentials issued from a Security Token Service (STS).</span></span>  
  
 <span data-ttu-id="70a48-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="70a48-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="70a48-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="70a48-104">\<behaviors></span></span>  
<span data-ttu-id="70a48-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="70a48-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="70a48-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="70a48-106">\<behavior></span></span>  
<span data-ttu-id="70a48-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="70a48-107">\<serviceCredentials></span></span>  
<span data-ttu-id="70a48-108">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="70a48-108">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="70a48-109">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="70a48-109">\<knownCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70a48-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="70a48-110">Syntax</span></span>  
  
```xml  
<knownCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="70a48-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="70a48-111">Attributes and Elements</span></span>  
 <span data-ttu-id="70a48-112">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="70a48-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="70a48-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="70a48-113">Attributes</span></span>  
 <span data-ttu-id="70a48-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="70a48-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="70a48-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="70a48-115">Child Elements</span></span>  
  
|<span data-ttu-id="70a48-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="70a48-116">Element</span></span>|<span data-ttu-id="70a48-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="70a48-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="70a48-118">\<add></span><span class="sxs-lookup"><span data-stu-id="70a48-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)|<span data-ttu-id="70a48-119">Adiciona um certificado X.509 à coleção.</span><span class="sxs-lookup"><span data-stu-id="70a48-119">Adds an X.509 certificate to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="70a48-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="70a48-120">Parent Elements</span></span>  
  
|<span data-ttu-id="70a48-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="70a48-121">Element</span></span>|<span data-ttu-id="70a48-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="70a48-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="70a48-123">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="70a48-123">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="70a48-124">Especifica um token emitido como uma credencial de serviço.</span><span class="sxs-lookup"><span data-stu-id="70a48-124">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70a48-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="70a48-125">Remarks</span></span>  
 <span data-ttu-id="70a48-126">O cenário de token emitido tem três etapas.</span><span class="sxs-lookup"><span data-stu-id="70a48-126">The issued token scenario has three stages.</span></span> <span data-ttu-id="70a48-127">O primeiro estágio, um cliente tentar acessar um serviço é chamado um *serviço de token seguro*.</span><span class="sxs-lookup"><span data-stu-id="70a48-127">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="70a48-128">O serviço de token seguro, em seguida, autentica o cliente e emite subsequentemente um token, normalmente um token de segurança asserções SAML (Markup Language) para o cliente.</span><span class="sxs-lookup"><span data-stu-id="70a48-128">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="70a48-129">O cliente, em seguida, retorne para o serviço com o token.</span><span class="sxs-lookup"><span data-stu-id="70a48-129">The client then returns to the service with the token.</span></span> <span data-ttu-id="70a48-130">O serviço examina o token para os dados que permite que o serviço autenticar o token e, portanto, o cliente.</span><span class="sxs-lookup"><span data-stu-id="70a48-130">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="70a48-131">Para autenticar o token, o certificado usa o serviço de token seguro deve ser conhecida para o serviço.</span><span class="sxs-lookup"><span data-stu-id="70a48-131">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="70a48-132">O [ \<issuedTokenAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) elemento é o repositório para todos esses certificados de serviço de token seguro.</span><span class="sxs-lookup"><span data-stu-id="70a48-132">The [\<issuedTokenAuthentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="70a48-133">Para adicionar certificados, use o [ \<knownCertificates > elemento](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="70a48-133">To add certificates, use the [\<knownCertificates> element](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span></span> <span data-ttu-id="70a48-134">Inserir uma [ \<Adicionar >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) para cada certificado, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="70a48-134">Insert an [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="70a48-135">Por padrão, os certificados devem ser obtidos de um serviço de token seguro.</span><span class="sxs-lookup"><span data-stu-id="70a48-135">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="70a48-136">Esses "conhecidos" certificados Certifique-se de que apenas legítimas os clientes podem acessar um serviço.</span><span class="sxs-lookup"><span data-stu-id="70a48-136">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="70a48-137">Para examinar as condições necessárias para um cliente seja autenticado por um serviço federado, bem como para obter mais informações sobre como usar este elemento de configuração, consulte [como: Configurar credenciais em um serviço de Federação](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="70a48-137">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="70a48-138">Para obter mais informações sobre cenários federados, consulte [federação e Tokens emitidos](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="70a48-138">For more information about federated scenarios, see [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="70a48-139">Para obter um exemplo que mostra como preencher a coleção na configuração, consulte [ \<Adicionar >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="70a48-139">For an example that shows how to populate the collection in configuration, see [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70a48-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="70a48-140">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [<span data-ttu-id="70a48-141">\<add></span><span class="sxs-lookup"><span data-stu-id="70a48-141">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)
- [<span data-ttu-id="70a48-142">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="70a48-142">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="70a48-143">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="70a48-143">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="70a48-144">Como: configurar credenciais em um serviço de federação</span><span class="sxs-lookup"><span data-stu-id="70a48-144">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="70a48-145">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="70a48-145">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="70a48-146">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="70a48-146">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="70a48-147">\<add></span><span class="sxs-lookup"><span data-stu-id="70a48-147">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)
- [<span data-ttu-id="70a48-148">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="70a48-148">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
