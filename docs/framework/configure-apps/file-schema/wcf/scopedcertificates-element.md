---
title: Elemento <scopedCertificates>
ms.date: 03/30/2017
ms.assetid: c7b6fc35-d4b2-4c18-98bd-83e09591f1d3
ms.openlocfilehash: ed53a42575a8d57c365f7a329a1a9c1df075d6d4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935216"
---
# <a name="scopedcertificates-element"></a><span data-ttu-id="87c17-102">\<Elemento de > scopedCertificates</span><span class="sxs-lookup"><span data-stu-id="87c17-102">\<scopedCertificates> Element</span></span>
<span data-ttu-id="87c17-103">Representa uma coleção de certificados X. 509 fornecidos por serviços específicos (com escopo) para autenticação.</span><span class="sxs-lookup"><span data-stu-id="87c17-103">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="87c17-104">Normalmente, essa coleção é usada para especificar os certificados de serviço para serviços de token de segurança em um cenário federado.</span><span class="sxs-lookup"><span data-stu-id="87c17-104">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>  
  
 <span data-ttu-id="87c17-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="87c17-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="87c17-106">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="87c17-106">\<behaviors></span></span>  
<span data-ttu-id="87c17-107">seção endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="87c17-107">endpointBehaviors section</span></span>  
<span data-ttu-id="87c17-108">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="87c17-108">\<behavior></span></span>  
<span data-ttu-id="87c17-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="87c17-109">\<clientCredentials></span></span>  
<span data-ttu-id="87c17-110">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="87c17-110">\<serviceCertificate></span></span>  
<span data-ttu-id="87c17-111">\<Elemento de > scopedCertificates</span><span class="sxs-lookup"><span data-stu-id="87c17-111">\<scopedCertificates> Element</span></span>  
<span data-ttu-id="87c17-112">\<Adicionar > elemento para \<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="87c17-112">\<add> element for \<scopedCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87c17-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="87c17-113">Syntax</span></span>  
  
```xml  
<scopedCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       targetUri="string"
       x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</scopedCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87c17-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="87c17-114">Attributes and Elements</span></span>  
 <span data-ttu-id="87c17-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="87c17-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87c17-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="87c17-116">Attributes</span></span>  
 <span data-ttu-id="87c17-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="87c17-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="87c17-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="87c17-118">Child Elements</span></span>  
  
|<span data-ttu-id="87c17-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="87c17-119">Element</span></span>|<span data-ttu-id="87c17-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="87c17-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="87c17-121">\<add></span><span class="sxs-lookup"><span data-stu-id="87c17-121">\<add></span></span>](add-of-scopedcertificates-element.md)|<span data-ttu-id="87c17-122">Adiciona um certificado X. 509 à coleção de certificados com escopo.</span><span class="sxs-lookup"><span data-stu-id="87c17-122">Adds an X.509 certificate to the collection of scoped certificates.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="87c17-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="87c17-123">Parent Elements</span></span>  
  
|<span data-ttu-id="87c17-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="87c17-124">Element</span></span>|<span data-ttu-id="87c17-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="87c17-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="87c17-126">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="87c17-126">\<serviceCertificate></span></span>](servicecertificate-of-servicecredentials.md)|<span data-ttu-id="87c17-127">Especifica um certificado a ser usado ao autenticar um serviço para o cliente.</span><span class="sxs-lookup"><span data-stu-id="87c17-127">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87c17-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="87c17-128">Remarks</span></span>  
 <span data-ttu-id="87c17-129">Essa coleção permite que o cliente configure os certificados de serviço a serem usados com base na URL do serviço com o qual se comunica.</span><span class="sxs-lookup"><span data-stu-id="87c17-129">This collection enables the client to configure the service certificates to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="87c17-130">Isso é especialmente útil em cenários de token emitidos em que um cliente pode se comunicar com vários serviços (o serviço final, bem como os serviços de token de segurança intermediários).</span><span class="sxs-lookup"><span data-stu-id="87c17-130">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="87c17-131">Para associações que usam segurança de mensagem baseada em certificado, esse certificado é usado para criptografar mensagens para o serviço e deve ser usado pelo serviço para assinar respostas para o cliente.</span><span class="sxs-lookup"><span data-stu-id="87c17-131">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="87c17-132">Se uma associação exigir um certificado para o serviço e nenhum certificado específico para a URL do serviço for encontrado no ScopedCertificates, o certificado padrão será usado.</span><span class="sxs-lookup"><span data-stu-id="87c17-132">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="87c17-133">Para obter mais informações, consulte a seção "certificados com escopo" [de como: Criar um cliente](../../../wcf/feature-details/how-to-create-a-federated-client.md)federado.</span><span class="sxs-lookup"><span data-stu-id="87c17-133">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="87c17-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="87c17-134">Example</span></span>  
 <span data-ttu-id="87c17-135">O exemplo a seguir especifica um certificado de serviço para o cliente usar ao se comunicar com pontos de extremidade cujo nome `http://www.contoso.com` de domínio está sobre o protocolo http.</span><span class="sxs-lookup"><span data-stu-id="87c17-135">The following example specifies a service certificate for the client to use when communicating with endpoints whose domain name is `http://www.contoso.com` over the HTTP protocol.</span></span>  
  
```xml  
<serviceCertificate>
  <scopedCertificates>
    <add targetUri="http://www.contoso.com"
         findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="Root"
         x509FindType="FindByIssuerName" />
  </scopedCertificates>
</serviceCertificate>
```  
  
## <a name="see-also"></a><span data-ttu-id="87c17-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="87c17-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="87c17-137">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="87c17-137">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="87c17-138">Como: Criar um cliente federado</span><span class="sxs-lookup"><span data-stu-id="87c17-138">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="87c17-139">\<add></span><span class="sxs-lookup"><span data-stu-id="87c17-139">\<add></span></span>](add-of-scopedcertificates-element.md)
- [<span data-ttu-id="87c17-140">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="87c17-140">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="87c17-141">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="87c17-141">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
