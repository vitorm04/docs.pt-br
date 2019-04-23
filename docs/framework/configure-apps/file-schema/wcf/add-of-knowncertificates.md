---
title: <add> de <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 128aaabe-3f1a-4c3b-b59f-898d0f02910f
ms.openlocfilehash: 3eb5bf74f909e6036154b7f5f7c6181b09fefbff
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59077713"
---
# <a name="add-of-knowncertificates"></a><span data-ttu-id="1eeb3-102">\<Adicionar > de \<knownCertificates ></span><span class="sxs-lookup"><span data-stu-id="1eeb3-102">\<add> of \<knownCertificates></span></span>
<span data-ttu-id="1eeb3-103">Adiciona um certificado X.509 à coleção de certificados conhecidos.</span><span class="sxs-lookup"><span data-stu-id="1eeb3-103">Adds an X.509 certificate to the collection of known certificates.</span></span>  
  
 <span data-ttu-id="1eeb3-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1eeb3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1eeb3-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="1eeb3-105">\<behaviors></span></span>  
<span data-ttu-id="1eeb3-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="1eeb3-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="1eeb3-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="1eeb3-107">\<behavior></span></span>  
<span data-ttu-id="1eeb3-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="1eeb3-108">\<serviceCredentials></span></span>  
<span data-ttu-id="1eeb3-109">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="1eeb3-109">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="1eeb3-110">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="1eeb3-110">\<knownCertificates></span></span>  
<span data-ttu-id="1eeb3-111">\<add></span><span class="sxs-lookup"><span data-stu-id="1eeb3-111">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1eeb3-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1eeb3-112">Syntax</span></span>  
  
```xml  
<knownCertificates>
   <add findValue="String"
      storeLocation="CurrentUser/LocalMachine"
      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
      x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1eeb3-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1eeb3-113">Attributes and Elements</span></span>  
 <span data-ttu-id="1eeb3-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1eeb3-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1eeb3-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="1eeb3-115">Attributes</span></span>  
  
|<span data-ttu-id="1eeb3-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="1eeb3-116">Attribute</span></span>|<span data-ttu-id="1eeb3-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="1eeb3-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1eeb3-118">findValue</span><span class="sxs-lookup"><span data-stu-id="1eeb3-118">findValue</span></span>|<span data-ttu-id="1eeb3-119">Cadeia.</span><span class="sxs-lookup"><span data-stu-id="1eeb3-119">String.</span></span> <span data-ttu-id="1eeb3-120">O valor a ser procurado.</span><span class="sxs-lookup"><span data-stu-id="1eeb3-120">The value to search for.</span></span>|  
|<span data-ttu-id="1eeb3-121">storeLocation</span><span class="sxs-lookup"><span data-stu-id="1eeb3-121">storeLocation</span></span>|<span data-ttu-id="1eeb3-122">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="1eeb3-122">Enumeration.</span></span> <span data-ttu-id="1eeb3-123">Um dos dois locais de repositório para pesquisar.</span><span class="sxs-lookup"><span data-stu-id="1eeb3-123">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="1eeb3-124">storeName</span><span class="sxs-lookup"><span data-stu-id="1eeb3-124">storeName</span></span>|<span data-ttu-id="1eeb3-125">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="1eeb3-125">Enumeration.</span></span> <span data-ttu-id="1eeb3-126">Um dos armazenamentos de sistema para pesquisar.</span><span class="sxs-lookup"><span data-stu-id="1eeb3-126">One of the system stores to search.</span></span>|  
|<span data-ttu-id="1eeb3-127">x509FindType</span><span class="sxs-lookup"><span data-stu-id="1eeb3-127">x509FindType</span></span>|<span data-ttu-id="1eeb3-128">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="1eeb3-128">Enumeration.</span></span> <span data-ttu-id="1eeb3-129">Um dos campos do certificado para pesquisar.</span><span class="sxs-lookup"><span data-stu-id="1eeb3-129">One of the certificate fields to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="1eeb3-130">findValue atributo</span><span class="sxs-lookup"><span data-stu-id="1eeb3-130">findValue Attribute</span></span>  
  
|<span data-ttu-id="1eeb3-131">Valor</span><span class="sxs-lookup"><span data-stu-id="1eeb3-131">Value</span></span>|<span data-ttu-id="1eeb3-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="1eeb3-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1eeb3-133">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="1eeb3-133">String</span></span>|<span data-ttu-id="1eeb3-134">O valor depende do campo (especificado pelo atributo X509FindType) que está sendo pesquisado.</span><span class="sxs-lookup"><span data-stu-id="1eeb3-134">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="1eeb3-135">Por exemplo, se você está procurando uma impressão digital, o valor deve ser uma cadeia de caracteres de números hexadecimais.</span><span class="sxs-lookup"><span data-stu-id="1eeb3-135">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="1eeb3-136">Atributo x509FindType</span><span class="sxs-lookup"><span data-stu-id="1eeb3-136">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="1eeb3-137">Valor</span><span class="sxs-lookup"><span data-stu-id="1eeb3-137">Value</span></span>|<span data-ttu-id="1eeb3-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="1eeb3-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1eeb3-139">Enumeração</span><span class="sxs-lookup"><span data-stu-id="1eeb3-139">Enumeration</span></span>|<span data-ttu-id="1eeb3-140">Os valores são: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName , FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="1eeb3-140">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="1eeb3-141">storeLocation atributo</span><span class="sxs-lookup"><span data-stu-id="1eeb3-141">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="1eeb3-142">Valor</span><span class="sxs-lookup"><span data-stu-id="1eeb3-142">Value</span></span>|<span data-ttu-id="1eeb3-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="1eeb3-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1eeb3-144">Enumeração</span><span class="sxs-lookup"><span data-stu-id="1eeb3-144">Enumeration</span></span>|<span data-ttu-id="1eeb3-145">CurrentUser ou LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="1eeb3-145">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="1eeb3-146">storeName atributo</span><span class="sxs-lookup"><span data-stu-id="1eeb3-146">storeName Attribute</span></span>  
  
|<span data-ttu-id="1eeb3-147">Valor</span><span class="sxs-lookup"><span data-stu-id="1eeb3-147">Value</span></span>|<span data-ttu-id="1eeb3-148">Descrição</span><span class="sxs-lookup"><span data-stu-id="1eeb3-148">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1eeb3-149">Enumeração</span><span class="sxs-lookup"><span data-stu-id="1eeb3-149">Enumeration</span></span>|<span data-ttu-id="1eeb3-150">Os valores são: Catálogo de endereços, AuthRoot, CertificateAuthority, não permitido, My, raiz, TrustedPeople e TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="1eeb3-150">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1eeb3-151">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1eeb3-151">Child Elements</span></span>  
 <span data-ttu-id="1eeb3-152">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="1eeb3-152">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1eeb3-153">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1eeb3-153">Parent Elements</span></span>  
  
|<span data-ttu-id="1eeb3-154">Elemento</span><span class="sxs-lookup"><span data-stu-id="1eeb3-154">Element</span></span>|<span data-ttu-id="1eeb3-155">Descrição</span><span class="sxs-lookup"><span data-stu-id="1eeb3-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1eeb3-156">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="1eeb3-156">\<knownCertificates></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md)|<span data-ttu-id="1eeb3-157">Representa uma coleção de certificados X.509 que são fornecidos por um Security Token Service (STS) para validação de tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="1eeb3-157">Represents a collection of X.509 certificates that are provided by a Security Token Service (STS) for validation of security tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1eeb3-158">Comentários</span><span class="sxs-lookup"><span data-stu-id="1eeb3-158">Remarks</span></span>  
 <span data-ttu-id="1eeb3-159">O cenário de token emitido tem três etapas.</span><span class="sxs-lookup"><span data-stu-id="1eeb3-159">The issued token scenario has three stages.</span></span> <span data-ttu-id="1eeb3-160">O primeiro estágio, um cliente tentar acessar um serviço é chamado um *serviço de token seguro*.</span><span class="sxs-lookup"><span data-stu-id="1eeb3-160">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="1eeb3-161">O serviço de token seguro, em seguida, autentica o cliente e emite subsequentemente um token, normalmente um token de segurança asserções SAML (Markup Language) para o cliente.</span><span class="sxs-lookup"><span data-stu-id="1eeb3-161">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="1eeb3-162">O cliente, em seguida, retorne para o serviço com o token.</span><span class="sxs-lookup"><span data-stu-id="1eeb3-162">The client then returns to the service with the token.</span></span> <span data-ttu-id="1eeb3-163">O serviço examina o token para os dados que permite que o serviço autenticar o token e, portanto, o cliente.</span><span class="sxs-lookup"><span data-stu-id="1eeb3-163">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="1eeb3-164">Para autenticar o token, o certificado usa o serviço de token seguro deve ser conhecida para o serviço.</span><span class="sxs-lookup"><span data-stu-id="1eeb3-164">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="1eeb3-165">O [ \<issuedTokenAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) elemento é o repositório para todos esses certificados de serviço de token seguro.</span><span class="sxs-lookup"><span data-stu-id="1eeb3-165">The [\<issuedTokenAuthentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="1eeb3-166">Para adicionar certificados, use o [ \<knownCertificates >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="1eeb3-166">To add certificates, use the [\<knownCertificates>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span></span> <span data-ttu-id="1eeb3-167">Inserir uma [ \<Adicionar > elemento \<knownCertificates > elemento](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) para cada certificado, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="1eeb3-167">Insert an [\<add> element \<knownCertificates> Element](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="1eeb3-168">Por padrão, os certificados devem ser obtidos de um serviço de token seguro.</span><span class="sxs-lookup"><span data-stu-id="1eeb3-168">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="1eeb3-169">Esses "conhecidos" certificados Certifique-se de que apenas legítimas os clientes podem acessar um serviço.</span><span class="sxs-lookup"><span data-stu-id="1eeb3-169">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="1eeb3-170">Para examinar as condições necessárias para um cliente seja autenticado por um serviço federado, bem como para obter mais informações sobre como usar este elemento de configuração, consulte [como: Configurar credenciais em um serviço de Federação](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="1eeb3-170">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="1eeb3-171">Para obter mais informações sobre cenários federados, consulte [federação e Tokens emitidos](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="1eeb3-171">For more information about federated scenarios, see [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1eeb3-172">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1eeb3-172">Example</span></span>  
 <span data-ttu-id="1eeb3-173">O exemplo a seguir adiciona o certificado no repositório para qualquer certificado STS.</span><span class="sxs-lookup"><span data-stu-id="1eeb3-173">The following example adds certificate to the repository for any STS certificates.</span></span>  
  
```xml  
<serviceBehaviors>
  <behavior name="myServiceBehavior">
    <serviceCredentials>
      <issuedTokenAuthentication>
        <knownCertificates>
          <add findValue="www.contoso.com"
               storeLocation="LocalMachine"
               storeName="CertificateAuthority"
               x509FindType="FindByIssuerName" />
        </knownCertificates>
      </issuedTokenAuthentication>
    </serviceCredentials>
  </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="1eeb3-174">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1eeb3-174">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [<span data-ttu-id="1eeb3-175">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="1eeb3-175">\<knownCertificates></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md)
- [<span data-ttu-id="1eeb3-176">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="1eeb3-176">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="1eeb3-177">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="1eeb3-177">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="1eeb3-178">Como: Configurar credenciais em um serviço de Federação</span><span class="sxs-lookup"><span data-stu-id="1eeb3-178">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="1eeb3-179">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="1eeb3-179">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
