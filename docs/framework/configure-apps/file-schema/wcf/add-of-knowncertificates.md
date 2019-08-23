---
title: <add> de <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 128aaabe-3f1a-4c3b-b59f-898d0f02910f
ms.openlocfilehash: 939718e8dacca2698b6f71a3bdc1262a5dc3ee20
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926675"
---
# <a name="add-of-knowncertificates"></a><span data-ttu-id="9884d-102">\<Adicionar > de \<knownCertificates ></span><span class="sxs-lookup"><span data-stu-id="9884d-102">\<add> of \<knownCertificates></span></span>
<span data-ttu-id="9884d-103">Adiciona um certificado X. 509 à coleção de certificados conhecidos.</span><span class="sxs-lookup"><span data-stu-id="9884d-103">Adds an X.509 certificate to the collection of known certificates.</span></span>  
  
 <span data-ttu-id="9884d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9884d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9884d-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="9884d-105">\<behaviors></span></span>  
<span data-ttu-id="9884d-106">\<> de portais</span><span class="sxs-lookup"><span data-stu-id="9884d-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="9884d-107">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="9884d-107">\<behavior></span></span>  
<span data-ttu-id="9884d-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="9884d-108">\<serviceCredentials></span></span>  
<span data-ttu-id="9884d-109">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="9884d-109">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="9884d-110">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="9884d-110">\<knownCertificates></span></span>  
<span data-ttu-id="9884d-111">\<add></span><span class="sxs-lookup"><span data-stu-id="9884d-111">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9884d-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9884d-112">Syntax</span></span>  
  
```xml  
<knownCertificates>
   <add findValue="String"
      storeLocation="CurrentUser/LocalMachine"
      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
      x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9884d-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9884d-113">Attributes and Elements</span></span>  
 <span data-ttu-id="9884d-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9884d-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9884d-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="9884d-115">Attributes</span></span>  
  
|<span data-ttu-id="9884d-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="9884d-116">Attribute</span></span>|<span data-ttu-id="9884d-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="9884d-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9884d-118">findValue</span><span class="sxs-lookup"><span data-stu-id="9884d-118">findValue</span></span>|<span data-ttu-id="9884d-119">Cadeia.</span><span class="sxs-lookup"><span data-stu-id="9884d-119">String.</span></span> <span data-ttu-id="9884d-120">O valor a ser procurado.</span><span class="sxs-lookup"><span data-stu-id="9884d-120">The value to search for.</span></span>|  
|<span data-ttu-id="9884d-121">storeLocation</span><span class="sxs-lookup"><span data-stu-id="9884d-121">storeLocation</span></span>|<span data-ttu-id="9884d-122">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="9884d-122">Enumeration.</span></span> <span data-ttu-id="9884d-123">Um dos dois locais de armazenamento para pesquisar.</span><span class="sxs-lookup"><span data-stu-id="9884d-123">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="9884d-124">storeName</span><span class="sxs-lookup"><span data-stu-id="9884d-124">storeName</span></span>|<span data-ttu-id="9884d-125">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="9884d-125">Enumeration.</span></span> <span data-ttu-id="9884d-126">Uma das lojas de sistema para pesquisa.</span><span class="sxs-lookup"><span data-stu-id="9884d-126">One of the system stores to search.</span></span>|  
|<span data-ttu-id="9884d-127">x509FindType</span><span class="sxs-lookup"><span data-stu-id="9884d-127">x509FindType</span></span>|<span data-ttu-id="9884d-128">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="9884d-128">Enumeration.</span></span> <span data-ttu-id="9884d-129">Um dos campos de certificado a serem pesquisados.</span><span class="sxs-lookup"><span data-stu-id="9884d-129">One of the certificate fields to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="9884d-130">Atributo FindValue</span><span class="sxs-lookup"><span data-stu-id="9884d-130">findValue Attribute</span></span>  
  
|<span data-ttu-id="9884d-131">Valor</span><span class="sxs-lookup"><span data-stu-id="9884d-131">Value</span></span>|<span data-ttu-id="9884d-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="9884d-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9884d-133">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="9884d-133">String</span></span>|<span data-ttu-id="9884d-134">O valor depende do campo (especificado pelo atributo X509FindType) que está sendo pesquisado.</span><span class="sxs-lookup"><span data-stu-id="9884d-134">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="9884d-135">Por exemplo, se estiver procurando uma impressão digital, o valor deverá ser uma cadeia de caracteres de números hexadecimais.</span><span class="sxs-lookup"><span data-stu-id="9884d-135">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="9884d-136">Atributo x509FindType</span><span class="sxs-lookup"><span data-stu-id="9884d-136">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="9884d-137">Valor</span><span class="sxs-lookup"><span data-stu-id="9884d-137">Value</span></span>|<span data-ttu-id="9884d-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="9884d-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9884d-139">Enumeração</span><span class="sxs-lookup"><span data-stu-id="9884d-139">Enumeration</span></span>|<span data-ttu-id="9884d-140">Os valores são: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName , FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="9884d-140">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="9884d-141">Atributo storeLocation</span><span class="sxs-lookup"><span data-stu-id="9884d-141">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="9884d-142">Valor</span><span class="sxs-lookup"><span data-stu-id="9884d-142">Value</span></span>|<span data-ttu-id="9884d-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="9884d-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9884d-144">Enumeração</span><span class="sxs-lookup"><span data-stu-id="9884d-144">Enumeration</span></span>|<span data-ttu-id="9884d-145">CurrentUser ou LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="9884d-145">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="9884d-146">Atributo storeName</span><span class="sxs-lookup"><span data-stu-id="9884d-146">storeName Attribute</span></span>  
  
|<span data-ttu-id="9884d-147">Valor</span><span class="sxs-lookup"><span data-stu-id="9884d-147">Value</span></span>|<span data-ttu-id="9884d-148">Descrição</span><span class="sxs-lookup"><span data-stu-id="9884d-148">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9884d-149">Enumeração</span><span class="sxs-lookup"><span data-stu-id="9884d-149">Enumeration</span></span>|<span data-ttu-id="9884d-150">Os valores são: Catálogo, AuthRoot, CertificateAuthority, não permitido, My, root, TrustedPeople e TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="9884d-150">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9884d-151">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9884d-151">Child Elements</span></span>  
 <span data-ttu-id="9884d-152">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="9884d-152">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9884d-153">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9884d-153">Parent Elements</span></span>  
  
|<span data-ttu-id="9884d-154">Elemento</span><span class="sxs-lookup"><span data-stu-id="9884d-154">Element</span></span>|<span data-ttu-id="9884d-155">Descrição</span><span class="sxs-lookup"><span data-stu-id="9884d-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9884d-156">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="9884d-156">\<knownCertificates></span></span>](knowncertificates.md)|<span data-ttu-id="9884d-157">Representa uma coleção de certificados X. 509 que são fornecidos por um serviço de token de segurança (STS) para validação de tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="9884d-157">Represents a collection of X.509 certificates that are provided by a Security Token Service (STS) for validation of security tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9884d-158">Comentários</span><span class="sxs-lookup"><span data-stu-id="9884d-158">Remarks</span></span>  
 <span data-ttu-id="9884d-159">O cenário de token emitido tem três estágios.</span><span class="sxs-lookup"><span data-stu-id="9884d-159">The issued token scenario has three stages.</span></span> <span data-ttu-id="9884d-160">No primeiro estágio, um cliente que tenta acessar um serviço é chamado de um *serviço de token seguro*.</span><span class="sxs-lookup"><span data-stu-id="9884d-160">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="9884d-161">O serviço de token seguro autentica o cliente e subsequentemente emite um token do cliente, normalmente um token SAML (Security Assertion Markup Language).</span><span class="sxs-lookup"><span data-stu-id="9884d-161">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="9884d-162">O cliente retorna ao serviço com o token.</span><span class="sxs-lookup"><span data-stu-id="9884d-162">The client then returns to the service with the token.</span></span> <span data-ttu-id="9884d-163">O serviço examina o token de dados que permite que o serviço autentique o token e, portanto, o cliente.</span><span class="sxs-lookup"><span data-stu-id="9884d-163">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="9884d-164">Para autenticar o token, o certificado que o serviço de token seguro usa deve ser conhecido pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="9884d-164">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="9884d-165">O elemento de [ \<> issuedTokenAuthentication](issuedtokenauthentication-of-servicecredentials.md) é o repositório para qualquer certificado de serviço de token seguro.</span><span class="sxs-lookup"><span data-stu-id="9884d-165">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="9884d-166">Para adicionar certificados, use o [ \<> knownCertificates](knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="9884d-166">To add certificates, use the [\<knownCertificates>](knowncertificates.md).</span></span> <span data-ttu-id="9884d-167">Insira um [ \<elemento adicionar > \<elemento knownCertificates >](add-of-knowncertificates.md) para cada certificado, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="9884d-167">Insert an [\<add> element \<knownCertificates> Element](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="9884d-168">Por padrão, os certificados devem ser obtidos de um serviço de token seguro.</span><span class="sxs-lookup"><span data-stu-id="9884d-168">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="9884d-169">Esses certificados "conhecidos" garantem que somente clientes legítimos possam acessar um serviço.</span><span class="sxs-lookup"><span data-stu-id="9884d-169">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="9884d-170">Para revisar as condições necessárias para um cliente ser autenticado por um serviço federado, bem como mais informações sobre como usar esse elemento de [configuração, consulte Como: Configure as credenciais em um](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)serviço de Federação.</span><span class="sxs-lookup"><span data-stu-id="9884d-170">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="9884d-171">Para obter mais informações sobre cenários federados, consulte [Federação e tokens emitidos](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="9884d-171">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9884d-172">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9884d-172">Example</span></span>  
 <span data-ttu-id="9884d-173">O exemplo a seguir adiciona o certificado ao repositório para qualquer certificado STS.</span><span class="sxs-lookup"><span data-stu-id="9884d-173">The following example adds certificate to the repository for any STS certificates.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9884d-174">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9884d-174">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [<span data-ttu-id="9884d-175">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="9884d-175">\<knownCertificates></span></span>](knowncertificates.md)
- [<span data-ttu-id="9884d-176">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="9884d-176">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="9884d-177">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="9884d-177">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="9884d-178">Como: Configurar credenciais em um Serviço de Federação</span><span class="sxs-lookup"><span data-stu-id="9884d-178">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="9884d-179">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="9884d-179">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
