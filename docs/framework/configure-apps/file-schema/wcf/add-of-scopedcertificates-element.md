---
title: <add> de <scopedCertificates> elemento
ms.date: 03/30/2017
ms.assetid: e21c1ef8-d6d6-4bca-ac5a-6fbf4bd77412
ms.openlocfilehash: 06a624d0146745581dfe907d044d1f7d3b857902
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119672"
---
# <a name="add-of-scopedcertificates-element"></a><span data-ttu-id="a459b-102">\<Adicionar > de \<scopedCertificates > elemento</span><span class="sxs-lookup"><span data-stu-id="a459b-102">\<add> of \<scopedCertificates> Element</span></span>
<span data-ttu-id="a459b-103">Adiciona um certificado X.509 à coleção de certificados de escopo.</span><span class="sxs-lookup"><span data-stu-id="a459b-103">Adds an X.509 certificate to the collection of scoped certificates.</span></span>  
  
 <span data-ttu-id="a459b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a459b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a459b-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="a459b-105">\<behaviors></span></span>  
<span data-ttu-id="a459b-106">seção endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="a459b-106">endpointBehaviors section</span></span>  
<span data-ttu-id="a459b-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="a459b-107">\<behavior></span></span>  
<span data-ttu-id="a459b-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="a459b-108">\<clientCredentials></span></span>  
<span data-ttu-id="a459b-109">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="a459b-109">\<serviceCertificate></span></span>  
<span data-ttu-id="a459b-110">\<scopedCertificates></span><span class="sxs-lookup"><span data-stu-id="a459b-110">\<scopedCertificates></span></span>  
<span data-ttu-id="a459b-111">\<Adicionar > elemento para \<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="a459b-111">\<add> element for \<scopedCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a459b-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a459b-112">Syntax</span></span>  
  
```xml  
<add findValue="String"
     storeLocation="CurrentUser/LocalMachine"
     storeName=" CurrentUser/LocalMachine"
     targetUri="string"
     x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a459b-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a459b-113">Attributes and Elements</span></span>  
 <span data-ttu-id="a459b-114">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="a459b-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a459b-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="a459b-115">Attributes</span></span>  
  
|<span data-ttu-id="a459b-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="a459b-116">Attribute</span></span>|<span data-ttu-id="a459b-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="a459b-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a459b-118">targetUri</span><span class="sxs-lookup"><span data-stu-id="a459b-118">targetUri</span></span>|<span data-ttu-id="a459b-119">Cadeia.</span><span class="sxs-lookup"><span data-stu-id="a459b-119">String.</span></span> <span data-ttu-id="a459b-120">Especifica o URI do serviço associado ao certificado.</span><span class="sxs-lookup"><span data-stu-id="a459b-120">Specifies the URI of the service associated with the certificate.</span></span>|  
|<span data-ttu-id="a459b-121">findValue</span><span class="sxs-lookup"><span data-stu-id="a459b-121">findValue</span></span>|<span data-ttu-id="a459b-122">Cadeia.</span><span class="sxs-lookup"><span data-stu-id="a459b-122">String.</span></span> <span data-ttu-id="a459b-123">O valor a ser procurado.</span><span class="sxs-lookup"><span data-stu-id="a459b-123">The value to search for.</span></span>|  
|<span data-ttu-id="a459b-124">x509FindType</span><span class="sxs-lookup"><span data-stu-id="a459b-124">x509FindType</span></span>|<span data-ttu-id="a459b-125">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="a459b-125">Enumeration.</span></span> <span data-ttu-id="a459b-126">Um dos campos do certificado para pesquisar.</span><span class="sxs-lookup"><span data-stu-id="a459b-126">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="a459b-127">storeLocation</span><span class="sxs-lookup"><span data-stu-id="a459b-127">storeLocation</span></span>|<span data-ttu-id="a459b-128">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="a459b-128">Enumeration.</span></span> <span data-ttu-id="a459b-129">Um dos dois locais de repositório para pesquisar.</span><span class="sxs-lookup"><span data-stu-id="a459b-129">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="a459b-130">storeName</span><span class="sxs-lookup"><span data-stu-id="a459b-130">storeName</span></span>|<span data-ttu-id="a459b-131">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="a459b-131">Enumeration.</span></span> <span data-ttu-id="a459b-132">Um dos armazenamentos de sistema para pesquisar.</span><span class="sxs-lookup"><span data-stu-id="a459b-132">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="a459b-133">findValue atributo</span><span class="sxs-lookup"><span data-stu-id="a459b-133">findValue Attribute</span></span>  
  
|<span data-ttu-id="a459b-134">Valor</span><span class="sxs-lookup"><span data-stu-id="a459b-134">Value</span></span>|<span data-ttu-id="a459b-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="a459b-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a459b-136">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="a459b-136">String</span></span>|<span data-ttu-id="a459b-137">O valor depende do campo (especificado pelo atributo X509FindType) que está sendo pesquisado.</span><span class="sxs-lookup"><span data-stu-id="a459b-137">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="a459b-138">Por exemplo, se você está procurando uma impressão digital, o valor deve ser uma cadeia de caracteres de números hexadecimais.</span><span class="sxs-lookup"><span data-stu-id="a459b-138">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="a459b-139">Atributo x509FindType</span><span class="sxs-lookup"><span data-stu-id="a459b-139">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="a459b-140">Valor</span><span class="sxs-lookup"><span data-stu-id="a459b-140">Value</span></span>|<span data-ttu-id="a459b-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="a459b-141">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a459b-142">Enumeração</span><span class="sxs-lookup"><span data-stu-id="a459b-142">Enumeration</span></span>|<span data-ttu-id="a459b-143">Os valores são: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName , FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="a459b-143">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="a459b-144">storeLocation atributo</span><span class="sxs-lookup"><span data-stu-id="a459b-144">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="a459b-145">Valor</span><span class="sxs-lookup"><span data-stu-id="a459b-145">Value</span></span>|<span data-ttu-id="a459b-146">Descrição</span><span class="sxs-lookup"><span data-stu-id="a459b-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a459b-147">Enumeração</span><span class="sxs-lookup"><span data-stu-id="a459b-147">Enumeration</span></span>|<span data-ttu-id="a459b-148">CurrentUser ou LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="a459b-148">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="a459b-149">storeName atributo</span><span class="sxs-lookup"><span data-stu-id="a459b-149">storeName Attribute</span></span>  
  
|<span data-ttu-id="a459b-150">Valor</span><span class="sxs-lookup"><span data-stu-id="a459b-150">Value</span></span>|<span data-ttu-id="a459b-151">Descrição</span><span class="sxs-lookup"><span data-stu-id="a459b-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a459b-152">Enumeração</span><span class="sxs-lookup"><span data-stu-id="a459b-152">Enumeration</span></span>|<span data-ttu-id="a459b-153">Os valores são: Catálogo de endereços, AuthRoot, CertificateAuthority, não permitido, My, raiz, TrustedPeople e TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="a459b-153">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a459b-154">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a459b-154">Child Elements</span></span>  
 <span data-ttu-id="a459b-155">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="a459b-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a459b-156">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a459b-156">Parent Elements</span></span>  
  
|<span data-ttu-id="a459b-157">Elemento</span><span class="sxs-lookup"><span data-stu-id="a459b-157">Element</span></span>|<span data-ttu-id="a459b-158">Descrição</span><span class="sxs-lookup"><span data-stu-id="a459b-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a459b-159">\<scopedCertificates></span><span class="sxs-lookup"><span data-stu-id="a459b-159">\<scopedCertificates></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)|<span data-ttu-id="a459b-160">Representa uma coleção de certificados X.509 fornecidos por serviços específicos (escopo) para autenticação.</span><span class="sxs-lookup"><span data-stu-id="a459b-160">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a459b-161">Comentários</span><span class="sxs-lookup"><span data-stu-id="a459b-161">Remarks</span></span>  
 <span data-ttu-id="a459b-162">Esse elemento permite que o cliente configurar um certificado de serviço para usar com base na URL do serviço comunica-se com.</span><span class="sxs-lookup"><span data-stu-id="a459b-162">This element enables the client to configure a service certificate to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="a459b-163">Isso é especialmente útil em cenários de token emitidos em que um cliente pode estar se comunicando a vários serviços (o serviço end como serviços de token de segurança intermediário).</span><span class="sxs-lookup"><span data-stu-id="a459b-163">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="a459b-164">Para associações que usam a segurança de mensagem baseada em certificado, esse certificado é usado para criptografar mensagens para o serviço e deve ser usado pelo serviço para assinar respostas ao cliente.</span><span class="sxs-lookup"><span data-stu-id="a459b-164">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="a459b-165">Se uma associação requer um certificado para o serviço e nenhum certificado específico para o serviço de que URL for encontrado no ScopedCertificates, o certificado padrão é usado.</span><span class="sxs-lookup"><span data-stu-id="a459b-165">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="a459b-166">Para obter mais informações, consulte a seção "Certificados no escopo" de [como: Criar um cliente federado](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span><span class="sxs-lookup"><span data-stu-id="a459b-166">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a459b-167">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a459b-167">Example</span></span>  
 <span data-ttu-id="a459b-168">O exemplo a seguir adiciona um certificado X.509 a coleção.</span><span class="sxs-lookup"><span data-stu-id="a459b-168">The following example adds an X.509 certificate the collection.</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <serviceCertificate>
          <scopedCertificates>
            <add targetUri="http://www.contoso.com"
                 findValue="www.Contoso.com"
                 storeLocation="LocalMachine"
                 storeName="Root"
                 x509FindType="FindByIssuerName" />
          </scopedCertificates>
        </serviceCertificate>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="a459b-169">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a459b-169">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="a459b-170">Como: Criar um cliente federado</span><span class="sxs-lookup"><span data-stu-id="a459b-170">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="a459b-171">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="a459b-171">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="a459b-172">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="a459b-172">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="a459b-173">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="a459b-173">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
