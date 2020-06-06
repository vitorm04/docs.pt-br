---
title: <add> de <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 128aaabe-3f1a-4c3b-b59f-898d0f02910f
ms.openlocfilehash: 29b067e6ec20992084f9ab3bab087222bdd56da2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400616"
---
# <a name="add-of-knowncertificates"></a><span data-ttu-id="a28c9-102">\<add> de \<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="a28c9-102">\<add> of \<knownCertificates></span></span>
<span data-ttu-id="a28c9-103">Adiciona um certificado X. 509 à coleção de certificados conhecidos.</span><span class="sxs-lookup"><span data-stu-id="a28c9-103">Adds an X.509 certificate to the collection of known certificates.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<knownCertificates>**](knowncertificates.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="a28c9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a28c9-104">Syntax</span></span>  
  
```xml  
<knownCertificates>
   <add findValue="String"
      storeLocation="CurrentUser/LocalMachine"
      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
      x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a28c9-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a28c9-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a28c9-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a28c9-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a28c9-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="a28c9-107">Attributes</span></span>  
  
|<span data-ttu-id="a28c9-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="a28c9-108">Attribute</span></span>|<span data-ttu-id="a28c9-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="a28c9-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a28c9-110">findValue</span><span class="sxs-lookup"><span data-stu-id="a28c9-110">findValue</span></span>|<span data-ttu-id="a28c9-111">Cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a28c9-111">String.</span></span> <span data-ttu-id="a28c9-112">O valor a ser procurado.</span><span class="sxs-lookup"><span data-stu-id="a28c9-112">The value to search for.</span></span>|  
|<span data-ttu-id="a28c9-113">storeLocation</span><span class="sxs-lookup"><span data-stu-id="a28c9-113">storeLocation</span></span>|<span data-ttu-id="a28c9-114">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="a28c9-114">Enumeration.</span></span> <span data-ttu-id="a28c9-115">Um dos dois locais de armazenamento para pesquisar.</span><span class="sxs-lookup"><span data-stu-id="a28c9-115">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="a28c9-116">storeName</span><span class="sxs-lookup"><span data-stu-id="a28c9-116">storeName</span></span>|<span data-ttu-id="a28c9-117">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="a28c9-117">Enumeration.</span></span> <span data-ttu-id="a28c9-118">Uma das lojas de sistema para pesquisa.</span><span class="sxs-lookup"><span data-stu-id="a28c9-118">One of the system stores to search.</span></span>|  
|<span data-ttu-id="a28c9-119">x509FindType</span><span class="sxs-lookup"><span data-stu-id="a28c9-119">x509FindType</span></span>|<span data-ttu-id="a28c9-120">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="a28c9-120">Enumeration.</span></span> <span data-ttu-id="a28c9-121">Um dos campos de certificado a serem pesquisados.</span><span class="sxs-lookup"><span data-stu-id="a28c9-121">One of the certificate fields to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="a28c9-122">Atributo FindValue</span><span class="sxs-lookup"><span data-stu-id="a28c9-122">findValue Attribute</span></span>  
  
|<span data-ttu-id="a28c9-123">Valor</span><span class="sxs-lookup"><span data-stu-id="a28c9-123">Value</span></span>|<span data-ttu-id="a28c9-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="a28c9-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a28c9-125">String</span><span class="sxs-lookup"><span data-stu-id="a28c9-125">String</span></span>|<span data-ttu-id="a28c9-126">O valor depende do campo (especificado pelo atributo X509FindType) que está sendo pesquisado.</span><span class="sxs-lookup"><span data-stu-id="a28c9-126">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="a28c9-127">Por exemplo, se estiver procurando uma impressão digital, o valor deverá ser uma cadeia de caracteres de números hexadecimais.</span><span class="sxs-lookup"><span data-stu-id="a28c9-127">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="a28c9-128">Atributo x509FindType</span><span class="sxs-lookup"><span data-stu-id="a28c9-128">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="a28c9-129">Valor</span><span class="sxs-lookup"><span data-stu-id="a28c9-129">Value</span></span>|<span data-ttu-id="a28c9-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="a28c9-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a28c9-131">Enumeração</span><span class="sxs-lookup"><span data-stu-id="a28c9-131">Enumeration</span></span>|<span data-ttu-id="a28c9-132">Os valores incluem: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="a28c9-132">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="a28c9-133">Atributo storeLocation</span><span class="sxs-lookup"><span data-stu-id="a28c9-133">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="a28c9-134">Valor</span><span class="sxs-lookup"><span data-stu-id="a28c9-134">Value</span></span>|<span data-ttu-id="a28c9-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="a28c9-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a28c9-136">Enumeração</span><span class="sxs-lookup"><span data-stu-id="a28c9-136">Enumeration</span></span>|<span data-ttu-id="a28c9-137">CurrentUser ou LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="a28c9-137">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="a28c9-138">Atributo storeName</span><span class="sxs-lookup"><span data-stu-id="a28c9-138">storeName Attribute</span></span>  
  
|<span data-ttu-id="a28c9-139">Valor</span><span class="sxs-lookup"><span data-stu-id="a28c9-139">Value</span></span>|<span data-ttu-id="a28c9-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="a28c9-140">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a28c9-141">Enumeração</span><span class="sxs-lookup"><span data-stu-id="a28c9-141">Enumeration</span></span>|<span data-ttu-id="a28c9-142">Os valores incluem: catálogo, AuthRoot, CertificateAuthority, não permitido, My, root, TrustedPeople e TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="a28c9-142">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a28c9-143">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a28c9-143">Child Elements</span></span>  
 <span data-ttu-id="a28c9-144">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a28c9-144">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a28c9-145">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a28c9-145">Parent Elements</span></span>  
  
|<span data-ttu-id="a28c9-146">Elemento</span><span class="sxs-lookup"><span data-stu-id="a28c9-146">Element</span></span>|<span data-ttu-id="a28c9-147">Descrição</span><span class="sxs-lookup"><span data-stu-id="a28c9-147">Description</span></span>|  
|-------------|-----------------|  
|[\<knownCertificates>](knowncertificates.md)|<span data-ttu-id="a28c9-148">Representa uma coleção de certificados X. 509 que são fornecidos por um serviço de token de segurança (STS) para validação de tokens de segurança.</span><span class="sxs-lookup"><span data-stu-id="a28c9-148">Represents a collection of X.509 certificates that are provided by a Security Token Service (STS) for validation of security tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a28c9-149">Comentários</span><span class="sxs-lookup"><span data-stu-id="a28c9-149">Remarks</span></span>  
 <span data-ttu-id="a28c9-150">O cenário de token emitido tem três estágios.</span><span class="sxs-lookup"><span data-stu-id="a28c9-150">The issued token scenario has three stages.</span></span> <span data-ttu-id="a28c9-151">No primeiro estágio, um cliente que tenta acessar um serviço é chamado de um *serviço de token seguro*.</span><span class="sxs-lookup"><span data-stu-id="a28c9-151">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="a28c9-152">O serviço de token seguro autentica o cliente e subsequentemente emite um token do cliente, normalmente um token SAML (Security Assertion Markup Language).</span><span class="sxs-lookup"><span data-stu-id="a28c9-152">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="a28c9-153">O cliente retorna ao serviço com o token.</span><span class="sxs-lookup"><span data-stu-id="a28c9-153">The client then returns to the service with the token.</span></span> <span data-ttu-id="a28c9-154">O serviço examina o token de dados que permite que o serviço autentique o token e, portanto, o cliente.</span><span class="sxs-lookup"><span data-stu-id="a28c9-154">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="a28c9-155">Para autenticar o token, o certificado que o serviço de token seguro usa deve ser conhecido pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="a28c9-155">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="a28c9-156">O [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) elemento é o repositório para qualquer certificado de serviço de token seguro.</span><span class="sxs-lookup"><span data-stu-id="a28c9-156">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="a28c9-157">Para adicionar certificados, use o [\<knownCertificates>](knowncertificates.md) .</span><span class="sxs-lookup"><span data-stu-id="a28c9-157">To add certificates, use the [\<knownCertificates>](knowncertificates.md).</span></span> <span data-ttu-id="a28c9-158">Insira um [ \<add> \<knownCertificates> elemento de elemento](add-of-knowncertificates.md) para cada certificado, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="a28c9-158">Insert an [\<add> element \<knownCertificates> Element](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="a28c9-159">Por padrão, os certificados devem ser obtidos de um serviço de token seguro.</span><span class="sxs-lookup"><span data-stu-id="a28c9-159">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="a28c9-160">Esses certificados "conhecidos" garantem que somente clientes legítimos possam acessar um serviço.</span><span class="sxs-lookup"><span data-stu-id="a28c9-160">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="a28c9-161">Para revisar as condições necessárias para um cliente ser autenticado por um serviço federado, bem como mais informações sobre como usar esse elemento de configuração, consulte [como configurar credenciais em um serviço de Federação](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="a28c9-161">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="a28c9-162">Para obter mais informações sobre cenários federados, consulte [Federação e tokens emitidos](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="a28c9-162">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a28c9-163">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a28c9-163">Example</span></span>  
 <span data-ttu-id="a28c9-164">O exemplo a seguir adiciona o certificado ao repositório para qualquer certificado STS.</span><span class="sxs-lookup"><span data-stu-id="a28c9-164">The following example adds certificate to the repository for any STS certificates.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a28c9-165">Confira também</span><span class="sxs-lookup"><span data-stu-id="a28c9-165">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [\<knownCertificates>](knowncertificates.md)
- [<span data-ttu-id="a28c9-166">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="a28c9-166">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="a28c9-167">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="a28c9-167">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="a28c9-168">Como configurar credenciais em um serviço de federação</span><span class="sxs-lookup"><span data-stu-id="a28c9-168">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="a28c9-169">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="a28c9-169">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
