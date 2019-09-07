---
title: <add> de <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 128aaabe-3f1a-4c3b-b59f-898d0f02910f
ms.openlocfilehash: 29b067e6ec20992084f9ab3bab087222bdd56da2
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400616"
---
# <a name="add-of-knowncertificates"></a><span data-ttu-id="c4fcf-102">\<Adicionar > de \<knownCertificates ></span><span class="sxs-lookup"><span data-stu-id="c4fcf-102">\<add> of \<knownCertificates></span></span>
<span data-ttu-id="c4fcf-103">Adiciona um certificado X. 509 à coleção de certificados conhecidos.</span><span class="sxs-lookup"><span data-stu-id="c4fcf-103">Adds an X.509 certificate to the collection of known certificates.</span></span>  
  
<span data-ttu-id="c4fcf-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c4fcf-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c4fcf-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c4fcf-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c4fcf-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c4fcf-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="c4fcf-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de portais**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c4fcf-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="c4fcf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c4fcf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="c4fcf-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="c4fcf-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="c4fcf-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> issuedTokenAuthentication**](issuedtokenauthentication-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="c4fcf-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)</span></span>\
<span data-ttu-id="c4fcf-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> knownCertificates**](knowncertificates.md)</span><span class="sxs-lookup"><span data-stu-id="c4fcf-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<knownCertificates>**](knowncertificates.md)</span></span>\
<span data-ttu-id="c4fcf-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Adicionar >**</span><span class="sxs-lookup"><span data-stu-id="c4fcf-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4fcf-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c4fcf-113">Syntax</span></span>  
  
```xml  
<knownCertificates>
   <add findValue="String"
      storeLocation="CurrentUser/LocalMachine"
      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
      x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c4fcf-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c4fcf-114">Attributes and Elements</span></span>  
 <span data-ttu-id="c4fcf-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c4fcf-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c4fcf-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="c4fcf-116">Attributes</span></span>  
  
|<span data-ttu-id="c4fcf-117">Atributo</span><span class="sxs-lookup"><span data-stu-id="c4fcf-117">Attribute</span></span>|<span data-ttu-id="c4fcf-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="c4fcf-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c4fcf-119">findValue</span><span class="sxs-lookup"><span data-stu-id="c4fcf-119">findValue</span></span>|<span data-ttu-id="c4fcf-120">Cadeia.</span><span class="sxs-lookup"><span data-stu-id="c4fcf-120">String.</span></span> <span data-ttu-id="c4fcf-121">O valor a ser procurado.</span><span class="sxs-lookup"><span data-stu-id="c4fcf-121">The value to search for.</span></span>|  
|<span data-ttu-id="c4fcf-122">storeLocation</span><span class="sxs-lookup"><span data-stu-id="c4fcf-122">storeLocation</span></span>|<span data-ttu-id="c4fcf-123">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="c4fcf-123">Enumeration.</span></span> <span data-ttu-id="c4fcf-124">Um dos dois locais de armazenamento para pesquisar.</span><span class="sxs-lookup"><span data-stu-id="c4fcf-124">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="c4fcf-125">storeName</span><span class="sxs-lookup"><span data-stu-id="c4fcf-125">storeName</span></span>|<span data-ttu-id="c4fcf-126">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="c4fcf-126">Enumeration.</span></span> <span data-ttu-id="c4fcf-127">Uma das lojas de sistema para pesquisa.</span><span class="sxs-lookup"><span data-stu-id="c4fcf-127">One of the system stores to search.</span></span>|  
|<span data-ttu-id="c4fcf-128">x509FindType</span><span class="sxs-lookup"><span data-stu-id="c4fcf-128">x509FindType</span></span>|<span data-ttu-id="c4fcf-129">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="c4fcf-129">Enumeration.</span></span> <span data-ttu-id="c4fcf-130">Um dos campos de certificado a serem pesquisados.</span><span class="sxs-lookup"><span data-stu-id="c4fcf-130">One of the certificate fields to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="c4fcf-131">Atributo FindValue</span><span class="sxs-lookup"><span data-stu-id="c4fcf-131">findValue Attribute</span></span>  
  
|<span data-ttu-id="c4fcf-132">Valor</span><span class="sxs-lookup"><span data-stu-id="c4fcf-132">Value</span></span>|<span data-ttu-id="c4fcf-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="c4fcf-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c4fcf-134">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c4fcf-134">String</span></span>|<span data-ttu-id="c4fcf-135">O valor depende do campo (especificado pelo atributo X509FindType) que está sendo pesquisado.</span><span class="sxs-lookup"><span data-stu-id="c4fcf-135">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="c4fcf-136">Por exemplo, se estiver procurando uma impressão digital, o valor deverá ser uma cadeia de caracteres de números hexadecimais.</span><span class="sxs-lookup"><span data-stu-id="c4fcf-136">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="c4fcf-137">Atributo x509FindType</span><span class="sxs-lookup"><span data-stu-id="c4fcf-137">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="c4fcf-138">Valor</span><span class="sxs-lookup"><span data-stu-id="c4fcf-138">Value</span></span>|<span data-ttu-id="c4fcf-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="c4fcf-139">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c4fcf-140">Enumeração</span><span class="sxs-lookup"><span data-stu-id="c4fcf-140">Enumeration</span></span>|<span data-ttu-id="c4fcf-141">Os valores são: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName , FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="c4fcf-141">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="c4fcf-142">Atributo storeLocation</span><span class="sxs-lookup"><span data-stu-id="c4fcf-142">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="c4fcf-143">Valor</span><span class="sxs-lookup"><span data-stu-id="c4fcf-143">Value</span></span>|<span data-ttu-id="c4fcf-144">Descrição</span><span class="sxs-lookup"><span data-stu-id="c4fcf-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c4fcf-145">Enumeração</span><span class="sxs-lookup"><span data-stu-id="c4fcf-145">Enumeration</span></span>|<span data-ttu-id="c4fcf-146">CurrentUser ou LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="c4fcf-146">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="c4fcf-147">Atributo storeName</span><span class="sxs-lookup"><span data-stu-id="c4fcf-147">storeName Attribute</span></span>  
  
|<span data-ttu-id="c4fcf-148">Valor</span><span class="sxs-lookup"><span data-stu-id="c4fcf-148">Value</span></span>|<span data-ttu-id="c4fcf-149">Descrição</span><span class="sxs-lookup"><span data-stu-id="c4fcf-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c4fcf-150">Enumeração</span><span class="sxs-lookup"><span data-stu-id="c4fcf-150">Enumeration</span></span>|<span data-ttu-id="c4fcf-151">Os valores são: Catálogo, AuthRoot, CertificateAuthority, não permitido, My, root, TrustedPeople e TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="c4fcf-151">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c4fcf-152">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c4fcf-152">Child Elements</span></span>  
 <span data-ttu-id="c4fcf-153">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="c4fcf-153">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c4fcf-154">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c4fcf-154">Parent Elements</span></span>  
  
|<span data-ttu-id="c4fcf-155">Elemento</span><span class="sxs-lookup"><span data-stu-id="c4fcf-155">Element</span></span>|<span data-ttu-id="c4fcf-156">Descrição</span><span class="sxs-lookup"><span data-stu-id="c4fcf-156">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c4fcf-157">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="c4fcf-157">\<knownCertificates></span></span>](knowncertificates.md)|<span data-ttu-id="c4fcf-158">Representa uma coleção de certificados X. 509 que são fornecidos por um serviço de token de segurança (STS) para validação de tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="c4fcf-158">Represents a collection of X.509 certificates that are provided by a Security Token Service (STS) for validation of security tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4fcf-159">Comentários</span><span class="sxs-lookup"><span data-stu-id="c4fcf-159">Remarks</span></span>  
 <span data-ttu-id="c4fcf-160">O cenário de token emitido tem três estágios.</span><span class="sxs-lookup"><span data-stu-id="c4fcf-160">The issued token scenario has three stages.</span></span> <span data-ttu-id="c4fcf-161">No primeiro estágio, um cliente que tenta acessar um serviço é chamado de um *serviço de token seguro*.</span><span class="sxs-lookup"><span data-stu-id="c4fcf-161">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="c4fcf-162">O serviço de token seguro autentica o cliente e subsequentemente emite um token do cliente, normalmente um token SAML (Security Assertion Markup Language).</span><span class="sxs-lookup"><span data-stu-id="c4fcf-162">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="c4fcf-163">O cliente retorna ao serviço com o token.</span><span class="sxs-lookup"><span data-stu-id="c4fcf-163">The client then returns to the service with the token.</span></span> <span data-ttu-id="c4fcf-164">O serviço examina o token de dados que permite que o serviço autentique o token e, portanto, o cliente.</span><span class="sxs-lookup"><span data-stu-id="c4fcf-164">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="c4fcf-165">Para autenticar o token, o certificado que o serviço de token seguro usa deve ser conhecido pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="c4fcf-165">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="c4fcf-166">O elemento de [ \<> issuedTokenAuthentication](issuedtokenauthentication-of-servicecredentials.md) é o repositório para qualquer certificado de serviço de token seguro.</span><span class="sxs-lookup"><span data-stu-id="c4fcf-166">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="c4fcf-167">Para adicionar certificados, use o [ \<> knownCertificates](knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="c4fcf-167">To add certificates, use the [\<knownCertificates>](knowncertificates.md).</span></span> <span data-ttu-id="c4fcf-168">Insira um [ \<elemento adicionar > \<elemento knownCertificates >](add-of-knowncertificates.md) para cada certificado, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="c4fcf-168">Insert an [\<add> element \<knownCertificates> Element](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="c4fcf-169">Por padrão, os certificados devem ser obtidos de um serviço de token seguro.</span><span class="sxs-lookup"><span data-stu-id="c4fcf-169">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="c4fcf-170">Esses certificados "conhecidos" garantem que somente clientes legítimos possam acessar um serviço.</span><span class="sxs-lookup"><span data-stu-id="c4fcf-170">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="c4fcf-171">Para revisar as condições necessárias para um cliente ser autenticado por um serviço federado, bem como mais informações sobre como usar esse elemento de [configuração, consulte Como: Configure as credenciais em um](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)serviço de Federação.</span><span class="sxs-lookup"><span data-stu-id="c4fcf-171">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="c4fcf-172">Para obter mais informações sobre cenários federados, consulte [Federação e tokens emitidos](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="c4fcf-172">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4fcf-173">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c4fcf-173">Example</span></span>  
 <span data-ttu-id="c4fcf-174">O exemplo a seguir adiciona o certificado ao repositório para qualquer certificado STS.</span><span class="sxs-lookup"><span data-stu-id="c4fcf-174">The following example adds certificate to the repository for any STS certificates.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c4fcf-175">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c4fcf-175">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [<span data-ttu-id="c4fcf-176">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="c4fcf-176">\<knownCertificates></span></span>](knowncertificates.md)
- [<span data-ttu-id="c4fcf-177">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="c4fcf-177">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="c4fcf-178">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="c4fcf-178">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="c4fcf-179">Como: Configurar credenciais em um Serviço de Federação</span><span class="sxs-lookup"><span data-stu-id="c4fcf-179">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="c4fcf-180">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="c4fcf-180">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
