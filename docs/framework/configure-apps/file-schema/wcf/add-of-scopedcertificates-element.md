---
title: '&lt;adicionar&gt; elemento &lt;scopedCertificates&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e21c1ef8-d6d6-4bca-ac5a-6fbf4bd77412
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eff535f7eb779a69c2368f3ad815f1eb124946ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltscopedcertificatesgt-element"></a><span data-ttu-id="bf9f7-102">&lt;adicionar&gt; elemento &lt;scopedCertificates&gt;</span><span class="sxs-lookup"><span data-stu-id="bf9f7-102">&lt;add&gt; of &lt;scopedCertificates&gt; Element</span></span>
<span data-ttu-id="bf9f7-103">Adiciona um certificado x. 509 à coleção de certificados de escopo.</span><span class="sxs-lookup"><span data-stu-id="bf9f7-103">Adds an X.509 certificate to the collection of scoped certificates.</span></span>  
  
 <span data-ttu-id="bf9f7-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="bf9f7-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="bf9f7-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="bf9f7-105">\<behaviors></span></span>  
<span data-ttu-id="bf9f7-106">seção endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="bf9f7-106">endpointBehaviors section</span></span>  
<span data-ttu-id="bf9f7-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="bf9f7-107">\<behavior></span></span>  
<span data-ttu-id="bf9f7-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="bf9f7-108">\<clientCredentials></span></span>  
<span data-ttu-id="bf9f7-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="bf9f7-109">\<serviceCertificate></span></span>  
<span data-ttu-id="bf9f7-110">\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="bf9f7-110">\<scopedCertificates></span></span>  
<span data-ttu-id="bf9f7-111">\<Adicionar > elemento para \<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="bf9f7-111">\<add> element for \<scopedCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf9f7-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bf9f7-112">Syntax</span></span>  
  
```xml  
<add findValue="String"  
          storeLocation="CurrentUser/LocalMachine"  
          storeName=" CurrentUser/LocalMachine"  
          targetUri="string"  
         x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"   
/>   
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf9f7-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="bf9f7-113">Attributes and Elements</span></span>  
 <span data-ttu-id="bf9f7-114">As seções a seguir descrevem os elementos pai de atributos e elementos filho</span><span class="sxs-lookup"><span data-stu-id="bf9f7-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf9f7-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="bf9f7-115">Attributes</span></span>  
  
|<span data-ttu-id="bf9f7-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="bf9f7-116">Attribute</span></span>|<span data-ttu-id="bf9f7-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="bf9f7-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bf9f7-118">targetUri</span><span class="sxs-lookup"><span data-stu-id="bf9f7-118">targetUri</span></span>|<span data-ttu-id="bf9f7-119">Cadeia.</span><span class="sxs-lookup"><span data-stu-id="bf9f7-119">String.</span></span> <span data-ttu-id="bf9f7-120">Especifica o URI do serviço associado ao certificado.</span><span class="sxs-lookup"><span data-stu-id="bf9f7-120">Specifies the URI of the service associated with the certificate.</span></span>|  
|<span data-ttu-id="bf9f7-121">findValue</span><span class="sxs-lookup"><span data-stu-id="bf9f7-121">findValue</span></span>|<span data-ttu-id="bf9f7-122">Cadeia.</span><span class="sxs-lookup"><span data-stu-id="bf9f7-122">String.</span></span> <span data-ttu-id="bf9f7-123">O valor a ser procurado.</span><span class="sxs-lookup"><span data-stu-id="bf9f7-123">The value to search for.</span></span>|  
|<span data-ttu-id="bf9f7-124">X509FindType</span><span class="sxs-lookup"><span data-stu-id="bf9f7-124">x509FindType</span></span>|<span data-ttu-id="bf9f7-125">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="bf9f7-125">Enumeration.</span></span> <span data-ttu-id="bf9f7-126">Um dos campos de certificado a ser pesquisado.</span><span class="sxs-lookup"><span data-stu-id="bf9f7-126">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="bf9f7-127">storeLocation</span><span class="sxs-lookup"><span data-stu-id="bf9f7-127">storeLocation</span></span>|<span data-ttu-id="bf9f7-128">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="bf9f7-128">Enumeration.</span></span> <span data-ttu-id="bf9f7-129">Um dos dois locais de repositório para pesquisar.</span><span class="sxs-lookup"><span data-stu-id="bf9f7-129">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="bf9f7-130">storeName</span><span class="sxs-lookup"><span data-stu-id="bf9f7-130">storeName</span></span>|<span data-ttu-id="bf9f7-131">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="bf9f7-131">Enumeration.</span></span> <span data-ttu-id="bf9f7-132">Um dos repositórios de sistema para pesquisar.</span><span class="sxs-lookup"><span data-stu-id="bf9f7-132">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="bf9f7-133">findValue atributo</span><span class="sxs-lookup"><span data-stu-id="bf9f7-133">findValue Attribute</span></span>  
  
|<span data-ttu-id="bf9f7-134">Valor</span><span class="sxs-lookup"><span data-stu-id="bf9f7-134">Value</span></span>|<span data-ttu-id="bf9f7-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="bf9f7-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bf9f7-136">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="bf9f7-136">String</span></span>|<span data-ttu-id="bf9f7-137">O valor depende do campo (especificado pelo atributo X509FindType) que está sendo pesquisado.</span><span class="sxs-lookup"><span data-stu-id="bf9f7-137">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="bf9f7-138">Por exemplo, se você está procurando uma impressão digital, o valor deve ser uma cadeia de caracteres de números hexadecimais.</span><span class="sxs-lookup"><span data-stu-id="bf9f7-138">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="bf9f7-139">Atributo x509FindType</span><span class="sxs-lookup"><span data-stu-id="bf9f7-139">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="bf9f7-140">Valor</span><span class="sxs-lookup"><span data-stu-id="bf9f7-140">Value</span></span>|<span data-ttu-id="bf9f7-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="bf9f7-141">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bf9f7-142">Enumeração</span><span class="sxs-lookup"><span data-stu-id="bf9f7-142">Enumeration</span></span>|<span data-ttu-id="bf9f7-143">Os valores incluem: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="bf9f7-143">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="bf9f7-144">storeLocation atributo</span><span class="sxs-lookup"><span data-stu-id="bf9f7-144">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="bf9f7-145">Valor</span><span class="sxs-lookup"><span data-stu-id="bf9f7-145">Value</span></span>|<span data-ttu-id="bf9f7-146">Descrição</span><span class="sxs-lookup"><span data-stu-id="bf9f7-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bf9f7-147">Enumeração</span><span class="sxs-lookup"><span data-stu-id="bf9f7-147">Enumeration</span></span>|<span data-ttu-id="bf9f7-148">CurrentUser ou LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="bf9f7-148">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="bf9f7-149">Atributo da storeName</span><span class="sxs-lookup"><span data-stu-id="bf9f7-149">storeName Attribute</span></span>  
  
|<span data-ttu-id="bf9f7-150">Valor</span><span class="sxs-lookup"><span data-stu-id="bf9f7-150">Value</span></span>|<span data-ttu-id="bf9f7-151">Descrição</span><span class="sxs-lookup"><span data-stu-id="bf9f7-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bf9f7-152">Enumeração</span><span class="sxs-lookup"><span data-stu-id="bf9f7-152">Enumeration</span></span>|<span data-ttu-id="bf9f7-153">Os valores incluem: catálogo de endereços, AuthRoot, CertificateAuthority, não permitidas, My, raiz, TrustedPeople e TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="bf9f7-153">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bf9f7-154">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="bf9f7-154">Child Elements</span></span>  
 <span data-ttu-id="bf9f7-155">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="bf9f7-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bf9f7-156">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="bf9f7-156">Parent Elements</span></span>  
  
|<span data-ttu-id="bf9f7-157">Elemento</span><span class="sxs-lookup"><span data-stu-id="bf9f7-157">Element</span></span>|<span data-ttu-id="bf9f7-158">Descrição</span><span class="sxs-lookup"><span data-stu-id="bf9f7-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bf9f7-159">\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="bf9f7-159">\<scopedCertificates></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)|<span data-ttu-id="bf9f7-160">Representa uma coleção de certificados x. 509 fornecidos por serviços específicos (escopo) para autenticação.</span><span class="sxs-lookup"><span data-stu-id="bf9f7-160">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf9f7-161">Comentários</span><span class="sxs-lookup"><span data-stu-id="bf9f7-161">Remarks</span></span>  
 <span data-ttu-id="bf9f7-162">Esse elemento permite que o cliente configurar um certificado de serviço para uso com base na URL do serviço, que ele se comunica.</span><span class="sxs-lookup"><span data-stu-id="bf9f7-162">This element enables the client to configure a service certificate to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="bf9f7-163">Isso é especialmente útil em cenários de token emitidos onde um cliente pode se comunicar a vários serviços (o serviço end bem como serviços de token de segurança intermediário).</span><span class="sxs-lookup"><span data-stu-id="bf9f7-163">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="bf9f7-164">Para associações que usam a segurança de mensagens baseada em certificado, esse certificado é usado para criptografar mensagens para o serviço e deve ser usada pelo serviço para assinar respostas ao cliente.</span><span class="sxs-lookup"><span data-stu-id="bf9f7-164">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="bf9f7-165">Se uma associação requer um certificado para o serviço e nenhum certificado específico para o serviço de que URL se encontra o ScopedCertificates, o certificado padrão é usado.</span><span class="sxs-lookup"><span data-stu-id="bf9f7-165">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="bf9f7-166">Para obter mais informações, consulte a seção "Escopo certificados" [como: criar um cliente federado](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span><span class="sxs-lookup"><span data-stu-id="bf9f7-166">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf9f7-167">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bf9f7-167">Example</span></span>  
 <span data-ttu-id="bf9f7-168">O exemplo a seguir adiciona um certificado x. 509 a coleção.</span><span class="sxs-lookup"><span data-stu-id="bf9f7-168">The following example adds an X.509 certificate the collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bf9f7-169">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bf9f7-169">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>  
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>  
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>  
 [<span data-ttu-id="bf9f7-170">Como criar um cliente federado</span><span class="sxs-lookup"><span data-stu-id="bf9f7-170">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="bf9f7-171">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="bf9f7-171">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="bf9f7-172">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="bf9f7-172">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="bf9f7-173">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="bf9f7-173">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
