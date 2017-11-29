---
title: Elemento &lt;scopedCertificates&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c7b6fc35-d4b2-4c18-98bd-83e09591f1d3
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8ebcc5f640a585022c924994409dacbb06a08e47
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltscopedcertificatesgt-element"></a><span data-ttu-id="c64f4-102">Elemento &lt;scopedCertificates&gt;</span><span class="sxs-lookup"><span data-stu-id="c64f4-102">&lt;scopedCertificates&gt; Element</span></span>
<span data-ttu-id="c64f4-103">Representa uma coleção de certificados x. 509 fornecidos por serviços específicos (escopo) para autenticação.</span><span class="sxs-lookup"><span data-stu-id="c64f4-103">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="c64f4-104">Essa coleção é normalmente usada para especificar os certificados de serviço para serviços de Token de segurança em um cenário federado.</span><span class="sxs-lookup"><span data-stu-id="c64f4-104">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>  
  
 <span data-ttu-id="c64f4-105">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="c64f4-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="c64f4-106">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="c64f4-106">\<behaviors></span></span>  
<span data-ttu-id="c64f4-107">seção endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="c64f4-107">endpointBehaviors section</span></span>  
<span data-ttu-id="c64f4-108">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="c64f4-108">\<behavior></span></span>  
<span data-ttu-id="c64f4-109">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="c64f4-109">\<clientCredentials></span></span>  
<span data-ttu-id="c64f4-110">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="c64f4-110">\<serviceCertificate></span></span>  
<span data-ttu-id="c64f4-111">\<scopedCertificates > elemento</span><span class="sxs-lookup"><span data-stu-id="c64f4-111">\<scopedCertificates> Element</span></span>  
<span data-ttu-id="c64f4-112">\<Adicionar > elemento para \<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="c64f4-112">\<add> element for \<scopedCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c64f4-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c64f4-113">Syntax</span></span>  
  
```xml  
<scopedCertificates>  
      <add findValue="String"  
                storeLocation="CurrentUser/LocalMachine"  
                storeName=" CurrentUser/LocalMachine"  
                targetUri="string"  
            x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />   
</scopedCertificates>   
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c64f4-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c64f4-114">Attributes and Elements</span></span>  
 <span data-ttu-id="c64f4-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c64f4-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c64f4-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="c64f4-116">Attributes</span></span>  
 <span data-ttu-id="c64f4-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="c64f4-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c64f4-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c64f4-118">Child Elements</span></span>  
  
|<span data-ttu-id="c64f4-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="c64f4-119">Element</span></span>|<span data-ttu-id="c64f4-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="c64f4-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c64f4-121">\<add></span><span class="sxs-lookup"><span data-stu-id="c64f4-121">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md)|<span data-ttu-id="c64f4-122">Adiciona um certificado x. 509 à coleção de certificados de escopo.</span><span class="sxs-lookup"><span data-stu-id="c64f4-122">Adds an X.509 certificate to the collection of scoped certificates.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c64f4-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c64f4-123">Parent Elements</span></span>  
  
|<span data-ttu-id="c64f4-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="c64f4-124">Element</span></span>|<span data-ttu-id="c64f4-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="c64f4-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c64f4-126">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="c64f4-126">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|<span data-ttu-id="c64f4-127">Especifica um certificado a ser usado ao autenticar um serviço para o cliente.</span><span class="sxs-lookup"><span data-stu-id="c64f4-127">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c64f4-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="c64f4-128">Remarks</span></span>  
 <span data-ttu-id="c64f4-129">Essa coleção permite que o cliente configurar os certificados de serviço para usar com base na URL do serviço, que ele se comunica.</span><span class="sxs-lookup"><span data-stu-id="c64f4-129">This collection enables the client to configure the service certificates to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="c64f4-130">Isso é especialmente útil em cenários de token emitidos onde um cliente pode se comunicar a vários serviços (o serviço end bem como serviços de token de segurança intermediário).</span><span class="sxs-lookup"><span data-stu-id="c64f4-130">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="c64f4-131">Para associações que usam a segurança de mensagens baseada em certificado, esse certificado é usado para criptografar mensagens para o serviço e deve ser usada pelo serviço para assinar respostas ao cliente.</span><span class="sxs-lookup"><span data-stu-id="c64f4-131">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="c64f4-132">Se uma associação requer um certificado para o serviço e nenhum certificado específico para o serviço de que URL se encontra o ScopedCertificates, o certificado padrão é usado.</span><span class="sxs-lookup"><span data-stu-id="c64f4-132">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="c64f4-133">Para obter mais informações, consulte a seção "Escopo certificados" [como: criar um cliente federado](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span><span class="sxs-lookup"><span data-stu-id="c64f4-133">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c64f4-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c64f4-134">Example</span></span>  
 <span data-ttu-id="c64f4-135">O exemplo a seguir especifica um certificado de serviço para o cliente usar ao se comunicar com pontos de extremidade cujo nome de domínio é http://www.contoso.com através do protocolo HTTP.</span><span class="sxs-lookup"><span data-stu-id="c64f4-135">The following example specifies a service certificate for the client to use when communicating with endpoints whose domain name is http://www.contoso.com over the HTTP protocol.</span></span>  
  
```xml  
<serviceCertificate>  
  <scopedCertificates>  
     <add targetUri="http://www.contoso.com"   
          findValue="www.contoso.com" storeLocation="LocalMachine"  
                  storeName="Root" x509FindType="FindByIssuerName" />  
  </scopedCertificates>  
</serviceCertificate>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c64f4-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c64f4-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>  
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>  
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>  
 [<span data-ttu-id="c64f4-137">Trabalhar com certificados</span><span class="sxs-lookup"><span data-stu-id="c64f4-137">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="c64f4-138">Como: criar um cliente federado</span><span class="sxs-lookup"><span data-stu-id="c64f4-138">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="c64f4-139">\<add></span><span class="sxs-lookup"><span data-stu-id="c64f4-139">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md)  
 <span data-ttu-id="c64f4-140">[Securing Clients](../../../../../docs/framework/wcf/securing-clients.md) (Protegendo clientes)</span><span class="sxs-lookup"><span data-stu-id="c64f4-140">[Securing Clients](../../../../../docs/framework/wcf/securing-clients.md)</span></span>  
 [<span data-ttu-id="c64f4-141">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="c64f4-141">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
