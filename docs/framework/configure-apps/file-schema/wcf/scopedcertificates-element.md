---
title: Elemento &lt;scopedCertificates&gt;
ms.date: 03/30/2017
ms.assetid: c7b6fc35-d4b2-4c18-98bd-83e09591f1d3
ms.openlocfilehash: 5b9bf4d25e23c8bdc4e3d01c2dfa61d059166117
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48838265"
---
# <a name="ltscopedcertificatesgt-element"></a><span data-ttu-id="0d740-102">Elemento &lt;scopedCertificates&gt;</span><span class="sxs-lookup"><span data-stu-id="0d740-102">&lt;scopedCertificates&gt; Element</span></span>
<span data-ttu-id="0d740-103">Representa uma coleção de certificados X.509 fornecidos por serviços específicos (escopo) para autenticação.</span><span class="sxs-lookup"><span data-stu-id="0d740-103">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="0d740-104">Essa coleção é normalmente usada para especificar os certificados de serviço para serviços de Token de segurança em um cenário federado.</span><span class="sxs-lookup"><span data-stu-id="0d740-104">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>  
  
 <span data-ttu-id="0d740-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0d740-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="0d740-106">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="0d740-106">\<behaviors></span></span>  
<span data-ttu-id="0d740-107">seção endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="0d740-107">endpointBehaviors section</span></span>  
<span data-ttu-id="0d740-108">\<comportamento de ></span><span class="sxs-lookup"><span data-stu-id="0d740-108">\<behavior></span></span>  
<span data-ttu-id="0d740-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="0d740-109">\<clientCredentials></span></span>  
<span data-ttu-id="0d740-110">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="0d740-110">\<serviceCertificate></span></span>  
<span data-ttu-id="0d740-111">\<scopedCertificates > elemento</span><span class="sxs-lookup"><span data-stu-id="0d740-111">\<scopedCertificates> Element</span></span>  
<span data-ttu-id="0d740-112">\<Adicionar > elemento para \<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="0d740-112">\<add> element for \<scopedCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d740-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0d740-113">Syntax</span></span>  
  
```xml  
<scopedCertificates>  
      <add findValue="String"  
                storeLocation="CurrentUser/LocalMachine"  
                storeName=" CurrentUser/LocalMachine"  
                targetUri="string"  
            x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />   
</scopedCertificates>   
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d740-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0d740-114">Attributes and Elements</span></span>  
 <span data-ttu-id="0d740-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0d740-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d740-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="0d740-116">Attributes</span></span>  
 <span data-ttu-id="0d740-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="0d740-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0d740-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0d740-118">Child Elements</span></span>  
  
|<span data-ttu-id="0d740-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="0d740-119">Element</span></span>|<span data-ttu-id="0d740-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d740-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0d740-121">\<add></span><span class="sxs-lookup"><span data-stu-id="0d740-121">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md)|<span data-ttu-id="0d740-122">Adiciona um certificado X.509 à coleção de certificados de escopo.</span><span class="sxs-lookup"><span data-stu-id="0d740-122">Adds an X.509 certificate to the collection of scoped certificates.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0d740-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0d740-123">Parent Elements</span></span>  
  
|<span data-ttu-id="0d740-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="0d740-124">Element</span></span>|<span data-ttu-id="0d740-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d740-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0d740-126">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="0d740-126">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|<span data-ttu-id="0d740-127">Especifica um certificado a ser usado ao autenticar um serviço para o cliente.</span><span class="sxs-lookup"><span data-stu-id="0d740-127">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d740-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="0d740-128">Remarks</span></span>  
 <span data-ttu-id="0d740-129">Essa coleção permite que o cliente configurar os certificados de serviço para usar com base na URL do serviço comunica-se com.</span><span class="sxs-lookup"><span data-stu-id="0d740-129">This collection enables the client to configure the service certificates to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="0d740-130">Isso é especialmente útil em cenários de token emitidos em que um cliente pode estar se comunicando a vários serviços (o serviço end como serviços de token de segurança intermediário).</span><span class="sxs-lookup"><span data-stu-id="0d740-130">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="0d740-131">Para associações que usam a segurança de mensagem baseada em certificado, esse certificado é usado para criptografar mensagens para o serviço e deve ser usado pelo serviço para assinar respostas ao cliente.</span><span class="sxs-lookup"><span data-stu-id="0d740-131">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="0d740-132">Se uma associação requer um certificado para o serviço e nenhum certificado específico para o serviço de que URL for encontrado no ScopedCertificates, o certificado padrão é usado.</span><span class="sxs-lookup"><span data-stu-id="0d740-132">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="0d740-133">Para obter mais informações, consulte a seção "Certificados no escopo" de [como: criar um cliente federado](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span><span class="sxs-lookup"><span data-stu-id="0d740-133">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d740-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0d740-134">Example</span></span>  
 <span data-ttu-id="0d740-135">O exemplo a seguir especifica um certificado de serviço para o cliente a ser usado ao se comunicar com pontos de extremidade cujo nome de domínio é `http://www.contoso.com` através do protocolo HTTP.</span><span class="sxs-lookup"><span data-stu-id="0d740-135">The following example specifies a service certificate for the client to use when communicating with endpoints whose domain name is `http://www.contoso.com` over the HTTP protocol.</span></span>  
  
```xml  
<serviceCertificate>  
  <scopedCertificates>  
     <add targetUri="http://www.contoso.com"   
          findValue="www.contoso.com" storeLocation="LocalMachine"  
                  storeName="Root" x509FindType="FindByIssuerName" />  
  </scopedCertificates>  
</serviceCertificate>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0d740-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0d740-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>  
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>  
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>  
 [<span data-ttu-id="0d740-137">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="0d740-137">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="0d740-138">Como criar um cliente federado</span><span class="sxs-lookup"><span data-stu-id="0d740-138">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="0d740-139">\<add></span><span class="sxs-lookup"><span data-stu-id="0d740-139">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md)  
 [<span data-ttu-id="0d740-140">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="0d740-140">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="0d740-141">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="0d740-141">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
