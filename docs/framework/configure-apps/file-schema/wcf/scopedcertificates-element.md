---
title: Elemento <scopedCertificates>
ms.date: 03/30/2017
ms.assetid: c7b6fc35-d4b2-4c18-98bd-83e09591f1d3
ms.openlocfilehash: 3c06159709df0afe2a475de1e186b0114af32bc2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399951"
---
# <a name="scopedcertificates-element"></a><span data-ttu-id="59423-102">Elemento \<scopedCertificates></span><span class="sxs-lookup"><span data-stu-id="59423-102">\<scopedCertificates> Element</span></span>
<span data-ttu-id="59423-103">Representa uma coleção de certificados X. 509 fornecidos por serviços específicos (com escopo) para autenticação.</span><span class="sxs-lookup"><span data-stu-id="59423-103">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="59423-104">Normalmente, essa coleção é usada para especificar os certificados de serviço para serviços de token de segurança em um cenário federado.</span><span class="sxs-lookup"><span data-stu-id="59423-104">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<scopedCertificates>**  
  
## <a name="syntax"></a><span data-ttu-id="59423-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="59423-105">Syntax</span></span>  
  
```xml  
<scopedCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       targetUri="string"
       x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</scopedCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59423-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="59423-106">Attributes and Elements</span></span>  
 <span data-ttu-id="59423-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="59423-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59423-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="59423-108">Attributes</span></span>  
 <span data-ttu-id="59423-109">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="59423-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="59423-110">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="59423-110">Child Elements</span></span>  
  
|<span data-ttu-id="59423-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="59423-111">Element</span></span>|<span data-ttu-id="59423-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="59423-112">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-scopedcertificates-element.md)|<span data-ttu-id="59423-113">Adiciona um certificado X. 509 à coleção de certificados com escopo.</span><span class="sxs-lookup"><span data-stu-id="59423-113">Adds an X.509 certificate to the collection of scoped certificates.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="59423-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="59423-114">Parent Elements</span></span>  
  
|<span data-ttu-id="59423-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="59423-115">Element</span></span>|<span data-ttu-id="59423-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="59423-116">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate-of-servicecredentials.md)|<span data-ttu-id="59423-117">Especifica um certificado a ser usado ao autenticar um serviço para o cliente.</span><span class="sxs-lookup"><span data-stu-id="59423-117">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59423-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="59423-118">Remarks</span></span>  
 <span data-ttu-id="59423-119">Essa coleção permite que o cliente configure os certificados de serviço a serem usados com base na URL do serviço com o qual se comunica.</span><span class="sxs-lookup"><span data-stu-id="59423-119">This collection enables the client to configure the service certificates to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="59423-120">Isso é especialmente útil em cenários de token emitidos em que um cliente pode se comunicar com vários serviços (o serviço final, bem como os serviços de token de segurança intermediários).</span><span class="sxs-lookup"><span data-stu-id="59423-120">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="59423-121">Para associações que usam segurança de mensagem baseada em certificado, esse certificado é usado para criptografar mensagens para o serviço e deve ser usado pelo serviço para assinar respostas para o cliente.</span><span class="sxs-lookup"><span data-stu-id="59423-121">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="59423-122">Se uma associação exigir um certificado para o serviço e nenhum certificado específico para a URL do serviço for encontrado no ScopedCertificates, o certificado padrão será usado.</span><span class="sxs-lookup"><span data-stu-id="59423-122">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="59423-123">Para obter mais informações, consulte a seção "certificados com escopo" de [como: criar um cliente federado](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span><span class="sxs-lookup"><span data-stu-id="59423-123">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="59423-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="59423-124">Example</span></span>  
 <span data-ttu-id="59423-125">O exemplo a seguir especifica um certificado de serviço para o cliente usar ao se comunicar com pontos de extremidade cujo nome `http://www.contoso.com` de domínio está sobre o protocolo http.</span><span class="sxs-lookup"><span data-stu-id="59423-125">The following example specifies a service certificate for the client to use when communicating with endpoints whose domain name is `http://www.contoso.com` over the HTTP protocol.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="59423-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="59423-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="59423-127">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="59423-127">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="59423-128">Como criar um cliente federado</span><span class="sxs-lookup"><span data-stu-id="59423-128">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [\<add>](add-of-scopedcertificates-element.md)
- [<span data-ttu-id="59423-129">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="59423-129">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="59423-130">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="59423-130">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
