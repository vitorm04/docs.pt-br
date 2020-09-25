---
title: <add> do <scopedCertificates> elemento
ms.date: 03/30/2017
ms.assetid: e21c1ef8-d6d6-4bca-ac5a-6fbf4bd77412
ms.openlocfilehash: 28777ecac130295a8ba82a8e4d67cc519d088d8a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195136"
---
# <a name="add-of-scopedcertificates-element"></a><span data-ttu-id="e9b53-102">\<add> do \<scopedCertificates> elemento</span><span class="sxs-lookup"><span data-stu-id="e9b53-102">\<add> of \<scopedCertificates> Element</span></span>

<span data-ttu-id="e9b53-103">Adiciona um certificado X. 509 à coleção de certificados com escopo.</span><span class="sxs-lookup"><span data-stu-id="e9b53-103">Adds an X.509 certificate to the collection of scoped certificates.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<scopedCertificates>**](scopedcertificates-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="e9b53-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e9b53-104">Syntax</span></span>  
  
```xml  
<add findValue="String"
     storeLocation="CurrentUser/LocalMachine"
     storeName=" CurrentUser/LocalMachine"
     targetUri="string"
     x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9b53-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e9b53-105">Attributes and Elements</span></span>  

 <span data-ttu-id="e9b53-106">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="e9b53-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9b53-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="e9b53-107">Attributes</span></span>  
  
|<span data-ttu-id="e9b53-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="e9b53-108">Attribute</span></span>|<span data-ttu-id="e9b53-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="e9b53-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e9b53-110">targetUri</span><span class="sxs-lookup"><span data-stu-id="e9b53-110">targetUri</span></span>|<span data-ttu-id="e9b53-111">Cadeia.</span><span class="sxs-lookup"><span data-stu-id="e9b53-111">String.</span></span> <span data-ttu-id="e9b53-112">Especifica o URI do serviço associado ao certificado.</span><span class="sxs-lookup"><span data-stu-id="e9b53-112">Specifies the URI of the service associated with the certificate.</span></span>|  
|<span data-ttu-id="e9b53-113">findValue</span><span class="sxs-lookup"><span data-stu-id="e9b53-113">findValue</span></span>|<span data-ttu-id="e9b53-114">Cadeia.</span><span class="sxs-lookup"><span data-stu-id="e9b53-114">String.</span></span> <span data-ttu-id="e9b53-115">O valor a ser procurado.</span><span class="sxs-lookup"><span data-stu-id="e9b53-115">The value to search for.</span></span>|  
|<span data-ttu-id="e9b53-116">x509FindType</span><span class="sxs-lookup"><span data-stu-id="e9b53-116">x509FindType</span></span>|<span data-ttu-id="e9b53-117">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="e9b53-117">Enumeration.</span></span> <span data-ttu-id="e9b53-118">Um dos campos de certificado a serem pesquisados.</span><span class="sxs-lookup"><span data-stu-id="e9b53-118">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="e9b53-119">storeLocation</span><span class="sxs-lookup"><span data-stu-id="e9b53-119">storeLocation</span></span>|<span data-ttu-id="e9b53-120">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="e9b53-120">Enumeration.</span></span> <span data-ttu-id="e9b53-121">Um dos dois locais de armazenamento para pesquisar.</span><span class="sxs-lookup"><span data-stu-id="e9b53-121">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="e9b53-122">storeName</span><span class="sxs-lookup"><span data-stu-id="e9b53-122">storeName</span></span>|<span data-ttu-id="e9b53-123">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="e9b53-123">Enumeration.</span></span> <span data-ttu-id="e9b53-124">Uma das lojas de sistema para pesquisa.</span><span class="sxs-lookup"><span data-stu-id="e9b53-124">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="e9b53-125">Atributo FindValue</span><span class="sxs-lookup"><span data-stu-id="e9b53-125">findValue Attribute</span></span>  
  
|<span data-ttu-id="e9b53-126">Valor</span><span class="sxs-lookup"><span data-stu-id="e9b53-126">Value</span></span>|<span data-ttu-id="e9b53-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="e9b53-127">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e9b53-128">String</span><span class="sxs-lookup"><span data-stu-id="e9b53-128">String</span></span>|<span data-ttu-id="e9b53-129">O valor depende do campo (especificado pelo atributo X509FindType) que está sendo pesquisado.</span><span class="sxs-lookup"><span data-stu-id="e9b53-129">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="e9b53-130">Por exemplo, se estiver procurando uma impressão digital, o valor deverá ser uma cadeia de caracteres de números hexadecimais.</span><span class="sxs-lookup"><span data-stu-id="e9b53-130">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="e9b53-131">Atributo x509FindType</span><span class="sxs-lookup"><span data-stu-id="e9b53-131">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="e9b53-132">Valor</span><span class="sxs-lookup"><span data-stu-id="e9b53-132">Value</span></span>|<span data-ttu-id="e9b53-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="e9b53-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e9b53-134">Enumeração</span><span class="sxs-lookup"><span data-stu-id="e9b53-134">Enumeration</span></span>|<span data-ttu-id="e9b53-135">Os valores incluem: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="e9b53-135">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="e9b53-136">Atributo storeLocation</span><span class="sxs-lookup"><span data-stu-id="e9b53-136">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="e9b53-137">Valor</span><span class="sxs-lookup"><span data-stu-id="e9b53-137">Value</span></span>|<span data-ttu-id="e9b53-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="e9b53-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e9b53-139">Enumeração</span><span class="sxs-lookup"><span data-stu-id="e9b53-139">Enumeration</span></span>|<span data-ttu-id="e9b53-140">CurrentUser ou LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="e9b53-140">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="e9b53-141">Atributo storeName</span><span class="sxs-lookup"><span data-stu-id="e9b53-141">storeName Attribute</span></span>  
  
|<span data-ttu-id="e9b53-142">Valor</span><span class="sxs-lookup"><span data-stu-id="e9b53-142">Value</span></span>|<span data-ttu-id="e9b53-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="e9b53-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e9b53-144">Enumeração</span><span class="sxs-lookup"><span data-stu-id="e9b53-144">Enumeration</span></span>|<span data-ttu-id="e9b53-145">Os valores incluem: catálogo, AuthRoot, CertificateAuthority, não permitido, My, root, TrustedPeople e TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="e9b53-145">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e9b53-146">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e9b53-146">Child Elements</span></span>  

 <span data-ttu-id="e9b53-147">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="e9b53-147">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e9b53-148">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e9b53-148">Parent Elements</span></span>  
  
|<span data-ttu-id="e9b53-149">Elemento</span><span class="sxs-lookup"><span data-stu-id="e9b53-149">Element</span></span>|<span data-ttu-id="e9b53-150">Descrição</span><span class="sxs-lookup"><span data-stu-id="e9b53-150">Description</span></span>|  
|-------------|-----------------|  
|[\<scopedCertificates>](scopedcertificates-element.md)|<span data-ttu-id="e9b53-151">Representa uma coleção de certificados X. 509 fornecidos por serviços específicos (com escopo) para autenticação.</span><span class="sxs-lookup"><span data-stu-id="e9b53-151">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9b53-152">Comentários</span><span class="sxs-lookup"><span data-stu-id="e9b53-152">Remarks</span></span>  

 <span data-ttu-id="e9b53-153">Esse elemento permite que o cliente configure um certificado de serviço para usar com base na URL do serviço com o qual se comunica.</span><span class="sxs-lookup"><span data-stu-id="e9b53-153">This element enables the client to configure a service certificate to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="e9b53-154">Isso é especialmente útil em cenários de token emitidos em que um cliente pode se comunicar com vários serviços (o serviço final, bem como os serviços de token de segurança intermediários).</span><span class="sxs-lookup"><span data-stu-id="e9b53-154">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="e9b53-155">Para associações que usam segurança de mensagem baseada em certificado, esse certificado é usado para criptografar mensagens para o serviço e deve ser usado pelo serviço para assinar respostas para o cliente.</span><span class="sxs-lookup"><span data-stu-id="e9b53-155">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="e9b53-156">Se uma associação exigir um certificado para o serviço e nenhum certificado específico para a URL do serviço for encontrado no ScopedCertificates, o certificado padrão será usado.</span><span class="sxs-lookup"><span data-stu-id="e9b53-156">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="e9b53-157">Para obter mais informações, consulte a seção "certificados com escopo" de [como: criar um cliente federado](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span><span class="sxs-lookup"><span data-stu-id="e9b53-157">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9b53-158">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e9b53-158">Example</span></span>  

 <span data-ttu-id="e9b53-159">O exemplo a seguir adiciona um certificado X. 509 à coleção.</span><span class="sxs-lookup"><span data-stu-id="e9b53-159">The following example adds an X.509 certificate the collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e9b53-160">Veja também</span><span class="sxs-lookup"><span data-stu-id="e9b53-160">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="e9b53-161">Como: criar um cliente federado</span><span class="sxs-lookup"><span data-stu-id="e9b53-161">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="e9b53-162">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="e9b53-162">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="e9b53-163">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="e9b53-163">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="e9b53-164">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="e9b53-164">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
