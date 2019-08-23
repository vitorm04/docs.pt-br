---
title: <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 678e21b4-6493-47c3-8359-fcf0d37e2138
ms.openlocfilehash: 1210e6282a7dd6c40198693d4948a89efe841d59
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913534"
---
# <a name="knowncertificates"></a><span data-ttu-id="3d77b-101">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="3d77b-101">\<knownCertificates></span></span>
<span data-ttu-id="3d77b-102">Representa uma coleção de certificados X. 509 que são fornecidos para autenticar credenciais de segurança emitidas de um serviço de token de segurança (STS).</span><span class="sxs-lookup"><span data-stu-id="3d77b-102">Represents a collection of X.509 certificates that are provided to authenticate security credentials issued from a Security Token Service (STS).</span></span>  
  
 <span data-ttu-id="3d77b-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3d77b-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="3d77b-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="3d77b-104">\<behaviors></span></span>  
<span data-ttu-id="3d77b-105">\<> de portais</span><span class="sxs-lookup"><span data-stu-id="3d77b-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="3d77b-106">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="3d77b-106">\<behavior></span></span>  
<span data-ttu-id="3d77b-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="3d77b-107">\<serviceCredentials></span></span>  
<span data-ttu-id="3d77b-108">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="3d77b-108">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="3d77b-109">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="3d77b-109">\<knownCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d77b-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3d77b-110">Syntax</span></span>  
  
```xml  
<knownCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3d77b-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3d77b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3d77b-112">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="3d77b-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3d77b-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="3d77b-113">Attributes</span></span>  
 <span data-ttu-id="3d77b-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="3d77b-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3d77b-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3d77b-115">Child Elements</span></span>  
  
|<span data-ttu-id="3d77b-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="3d77b-116">Element</span></span>|<span data-ttu-id="3d77b-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="3d77b-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3d77b-118">\<add></span><span class="sxs-lookup"><span data-stu-id="3d77b-118">\<add></span></span>](add-of-knowncertificates.md)|<span data-ttu-id="3d77b-119">Adiciona um certificado X. 509 à coleção.</span><span class="sxs-lookup"><span data-stu-id="3d77b-119">Adds an X.509 certificate to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3d77b-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3d77b-120">Parent Elements</span></span>  
  
|<span data-ttu-id="3d77b-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="3d77b-121">Element</span></span>|<span data-ttu-id="3d77b-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="3d77b-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3d77b-123">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="3d77b-123">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="3d77b-124">Especifica um token emitido como uma credencial de serviço.</span><span class="sxs-lookup"><span data-stu-id="3d77b-124">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d77b-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="3d77b-125">Remarks</span></span>  
 <span data-ttu-id="3d77b-126">O cenário de token emitido tem três estágios.</span><span class="sxs-lookup"><span data-stu-id="3d77b-126">The issued token scenario has three stages.</span></span> <span data-ttu-id="3d77b-127">No primeiro estágio, um cliente que tenta acessar um serviço é chamado de um *serviço de token seguro*.</span><span class="sxs-lookup"><span data-stu-id="3d77b-127">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="3d77b-128">O serviço de token seguro autentica o cliente e subsequentemente emite um token do cliente, normalmente um token SAML (Security Assertion Markup Language).</span><span class="sxs-lookup"><span data-stu-id="3d77b-128">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="3d77b-129">O cliente retorna ao serviço com o token.</span><span class="sxs-lookup"><span data-stu-id="3d77b-129">The client then returns to the service with the token.</span></span> <span data-ttu-id="3d77b-130">O serviço examina o token de dados que permite que o serviço autentique o token e, portanto, o cliente.</span><span class="sxs-lookup"><span data-stu-id="3d77b-130">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="3d77b-131">Para autenticar o token, o certificado que o serviço de token seguro usa deve ser conhecido pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="3d77b-131">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="3d77b-132">O elemento de [ \<> issuedTokenAuthentication](issuedtokenauthentication-of-servicecredentials.md) é o repositório para qualquer certificado de serviço de token seguro.</span><span class="sxs-lookup"><span data-stu-id="3d77b-132">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="3d77b-133">Para adicionar certificados, use o [ \<elemento de > knownCertificates](knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="3d77b-133">To add certificates, use the [\<knownCertificates> element](knowncertificates.md).</span></span> <span data-ttu-id="3d77b-134">Insira um [ \<> Adicionar](add-of-knowncertificates.md) para cada certificado, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="3d77b-134">Insert an [\<add>](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="3d77b-135">Por padrão, os certificados devem ser obtidos de um serviço de token seguro.</span><span class="sxs-lookup"><span data-stu-id="3d77b-135">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="3d77b-136">Esses certificados "conhecidos" garantem que somente clientes legítimos possam acessar um serviço.</span><span class="sxs-lookup"><span data-stu-id="3d77b-136">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="3d77b-137">Para revisar as condições necessárias para um cliente ser autenticado por um serviço federado, bem como mais informações sobre como usar esse elemento de [configuração, consulte Como: Configure as credenciais em um](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)serviço de Federação.</span><span class="sxs-lookup"><span data-stu-id="3d77b-137">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="3d77b-138">Para obter mais informações sobre cenários federados, consulte [Federação e tokens emitidos](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="3d77b-138">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="3d77b-139">Para obter um exemplo que mostra como preencher a coleção na configuração, consulte [ \<Adicionar >](add-of-knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="3d77b-139">For an example that shows how to populate the collection in configuration, see [\<add>](add-of-knowncertificates.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d77b-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3d77b-140">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [<span data-ttu-id="3d77b-141">\<add></span><span class="sxs-lookup"><span data-stu-id="3d77b-141">\<add></span></span>](add-of-knowncertificates.md)
- [<span data-ttu-id="3d77b-142">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="3d77b-142">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="3d77b-143">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="3d77b-143">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="3d77b-144">Como: Configurar credenciais em um Serviço de Federação</span><span class="sxs-lookup"><span data-stu-id="3d77b-144">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="3d77b-145">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="3d77b-145">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="3d77b-146">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="3d77b-146">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="3d77b-147">\<add></span><span class="sxs-lookup"><span data-stu-id="3d77b-147">\<add></span></span>](add-of-knowncertificates.md)
- [<span data-ttu-id="3d77b-148">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="3d77b-148">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
