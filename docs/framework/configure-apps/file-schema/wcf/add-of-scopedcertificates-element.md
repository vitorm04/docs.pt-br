---
title: <add>do <scopedCertificates> elemento
ms.date: 03/30/2017
ms.assetid: e21c1ef8-d6d6-4bca-ac5a-6fbf4bd77412
ms.openlocfilehash: 9756d37527fcf888cad930b24677ae8e6a2c8fba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920051"
---
# <a name="add-of-scopedcertificates-element"></a><span data-ttu-id="1533a-102">\<Adicionar > do \<elemento scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="1533a-102">\<add> of \<scopedCertificates> Element</span></span>
<span data-ttu-id="1533a-103">Adiciona um certificado X. 509 à coleção de certificados com escopo.</span><span class="sxs-lookup"><span data-stu-id="1533a-103">Adds an X.509 certificate to the collection of scoped certificates.</span></span>  
  
 <span data-ttu-id="1533a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1533a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1533a-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="1533a-105">\<behaviors></span></span>  
<span data-ttu-id="1533a-106">seção endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="1533a-106">endpointBehaviors section</span></span>  
<span data-ttu-id="1533a-107">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="1533a-107">\<behavior></span></span>  
<span data-ttu-id="1533a-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="1533a-108">\<clientCredentials></span></span>  
<span data-ttu-id="1533a-109">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="1533a-109">\<serviceCertificate></span></span>  
<span data-ttu-id="1533a-110">\<scopedCertificates></span><span class="sxs-lookup"><span data-stu-id="1533a-110">\<scopedCertificates></span></span>  
<span data-ttu-id="1533a-111">\<Adicionar > elemento para \<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="1533a-111">\<add> element for \<scopedCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1533a-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1533a-112">Syntax</span></span>  
  
```xml  
<add findValue="String"
     storeLocation="CurrentUser/LocalMachine"
     storeName=" CurrentUser/LocalMachine"
     targetUri="string"
     x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1533a-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1533a-113">Attributes and Elements</span></span>  
 <span data-ttu-id="1533a-114">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="1533a-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1533a-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="1533a-115">Attributes</span></span>  
  
|<span data-ttu-id="1533a-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="1533a-116">Attribute</span></span>|<span data-ttu-id="1533a-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="1533a-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1533a-118">targetUri</span><span class="sxs-lookup"><span data-stu-id="1533a-118">targetUri</span></span>|<span data-ttu-id="1533a-119">Cadeia.</span><span class="sxs-lookup"><span data-stu-id="1533a-119">String.</span></span> <span data-ttu-id="1533a-120">Especifica o URI do serviço associado ao certificado.</span><span class="sxs-lookup"><span data-stu-id="1533a-120">Specifies the URI of the service associated with the certificate.</span></span>|  
|<span data-ttu-id="1533a-121">findValue</span><span class="sxs-lookup"><span data-stu-id="1533a-121">findValue</span></span>|<span data-ttu-id="1533a-122">Cadeia.</span><span class="sxs-lookup"><span data-stu-id="1533a-122">String.</span></span> <span data-ttu-id="1533a-123">O valor a ser procurado.</span><span class="sxs-lookup"><span data-stu-id="1533a-123">The value to search for.</span></span>|  
|<span data-ttu-id="1533a-124">x509FindType</span><span class="sxs-lookup"><span data-stu-id="1533a-124">x509FindType</span></span>|<span data-ttu-id="1533a-125">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="1533a-125">Enumeration.</span></span> <span data-ttu-id="1533a-126">Um dos campos de certificado a serem pesquisados.</span><span class="sxs-lookup"><span data-stu-id="1533a-126">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="1533a-127">storeLocation</span><span class="sxs-lookup"><span data-stu-id="1533a-127">storeLocation</span></span>|<span data-ttu-id="1533a-128">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="1533a-128">Enumeration.</span></span> <span data-ttu-id="1533a-129">Um dos dois locais de armazenamento para pesquisar.</span><span class="sxs-lookup"><span data-stu-id="1533a-129">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="1533a-130">storeName</span><span class="sxs-lookup"><span data-stu-id="1533a-130">storeName</span></span>|<span data-ttu-id="1533a-131">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="1533a-131">Enumeration.</span></span> <span data-ttu-id="1533a-132">Uma das lojas de sistema para pesquisa.</span><span class="sxs-lookup"><span data-stu-id="1533a-132">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="1533a-133">Atributo FindValue</span><span class="sxs-lookup"><span data-stu-id="1533a-133">findValue Attribute</span></span>  
  
|<span data-ttu-id="1533a-134">Valor</span><span class="sxs-lookup"><span data-stu-id="1533a-134">Value</span></span>|<span data-ttu-id="1533a-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="1533a-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1533a-136">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="1533a-136">String</span></span>|<span data-ttu-id="1533a-137">O valor depende do campo (especificado pelo atributo X509FindType) que está sendo pesquisado.</span><span class="sxs-lookup"><span data-stu-id="1533a-137">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="1533a-138">Por exemplo, se estiver procurando uma impressão digital, o valor deverá ser uma cadeia de caracteres de números hexadecimais.</span><span class="sxs-lookup"><span data-stu-id="1533a-138">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="1533a-139">Atributo x509FindType</span><span class="sxs-lookup"><span data-stu-id="1533a-139">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="1533a-140">Valor</span><span class="sxs-lookup"><span data-stu-id="1533a-140">Value</span></span>|<span data-ttu-id="1533a-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="1533a-141">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1533a-142">Enumeração</span><span class="sxs-lookup"><span data-stu-id="1533a-142">Enumeration</span></span>|<span data-ttu-id="1533a-143">Os valores são: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName , FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="1533a-143">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="1533a-144">Atributo storeLocation</span><span class="sxs-lookup"><span data-stu-id="1533a-144">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="1533a-145">Valor</span><span class="sxs-lookup"><span data-stu-id="1533a-145">Value</span></span>|<span data-ttu-id="1533a-146">Descrição</span><span class="sxs-lookup"><span data-stu-id="1533a-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1533a-147">Enumeração</span><span class="sxs-lookup"><span data-stu-id="1533a-147">Enumeration</span></span>|<span data-ttu-id="1533a-148">CurrentUser ou LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="1533a-148">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="1533a-149">Atributo storeName</span><span class="sxs-lookup"><span data-stu-id="1533a-149">storeName Attribute</span></span>  
  
|<span data-ttu-id="1533a-150">Valor</span><span class="sxs-lookup"><span data-stu-id="1533a-150">Value</span></span>|<span data-ttu-id="1533a-151">Descrição</span><span class="sxs-lookup"><span data-stu-id="1533a-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1533a-152">Enumeração</span><span class="sxs-lookup"><span data-stu-id="1533a-152">Enumeration</span></span>|<span data-ttu-id="1533a-153">Os valores são: Catálogo, AuthRoot, CertificateAuthority, não permitido, My, root, TrustedPeople e TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="1533a-153">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1533a-154">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1533a-154">Child Elements</span></span>  
 <span data-ttu-id="1533a-155">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="1533a-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1533a-156">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1533a-156">Parent Elements</span></span>  
  
|<span data-ttu-id="1533a-157">Elemento</span><span class="sxs-lookup"><span data-stu-id="1533a-157">Element</span></span>|<span data-ttu-id="1533a-158">Descrição</span><span class="sxs-lookup"><span data-stu-id="1533a-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1533a-159">\<scopedCertificates></span><span class="sxs-lookup"><span data-stu-id="1533a-159">\<scopedCertificates></span></span>](scopedcertificates-element.md)|<span data-ttu-id="1533a-160">Representa uma coleção de certificados X. 509 fornecidos por serviços específicos (com escopo) para autenticação.</span><span class="sxs-lookup"><span data-stu-id="1533a-160">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1533a-161">Comentários</span><span class="sxs-lookup"><span data-stu-id="1533a-161">Remarks</span></span>  
 <span data-ttu-id="1533a-162">Esse elemento permite que o cliente configure um certificado de serviço para usar com base na URL do serviço com o qual se comunica.</span><span class="sxs-lookup"><span data-stu-id="1533a-162">This element enables the client to configure a service certificate to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="1533a-163">Isso é especialmente útil em cenários de token emitidos em que um cliente pode se comunicar com vários serviços (o serviço final, bem como os serviços de token de segurança intermediários).</span><span class="sxs-lookup"><span data-stu-id="1533a-163">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="1533a-164">Para associações que usam segurança de mensagem baseada em certificado, esse certificado é usado para criptografar mensagens para o serviço e deve ser usado pelo serviço para assinar respostas para o cliente.</span><span class="sxs-lookup"><span data-stu-id="1533a-164">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="1533a-165">Se uma associação exigir um certificado para o serviço e nenhum certificado específico para a URL do serviço for encontrado no ScopedCertificates, o certificado padrão será usado.</span><span class="sxs-lookup"><span data-stu-id="1533a-165">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="1533a-166">Para obter mais informações, consulte a seção "certificados com escopo" [de como: Criar um cliente](../../../wcf/feature-details/how-to-create-a-federated-client.md)federado.</span><span class="sxs-lookup"><span data-stu-id="1533a-166">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1533a-167">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1533a-167">Example</span></span>  
 <span data-ttu-id="1533a-168">O exemplo a seguir adiciona um certificado X. 509 à coleção.</span><span class="sxs-lookup"><span data-stu-id="1533a-168">The following example adds an X.509 certificate the collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1533a-169">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1533a-169">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="1533a-170">Como: Criar um cliente federado</span><span class="sxs-lookup"><span data-stu-id="1533a-170">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="1533a-171">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="1533a-171">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="1533a-172">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="1533a-172">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="1533a-173">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="1533a-173">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
