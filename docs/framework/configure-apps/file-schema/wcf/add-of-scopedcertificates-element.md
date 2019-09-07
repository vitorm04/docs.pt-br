---
title: <add>do <scopedCertificates> elemento
ms.date: 03/30/2017
ms.assetid: e21c1ef8-d6d6-4bca-ac5a-6fbf4bd77412
ms.openlocfilehash: b00a342108beca69a906fbf6212915768e98778f
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398340"
---
# <a name="add-of-scopedcertificates-element"></a><span data-ttu-id="bdc3e-102">\<Adicionar > do \<elemento scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="bdc3e-102">\<add> of \<scopedCertificates> Element</span></span>
<span data-ttu-id="bdc3e-103">Adiciona um certificado X. 509 à coleção de certificados com escopo.</span><span class="sxs-lookup"><span data-stu-id="bdc3e-103">Adds an X.509 certificate to the collection of scoped certificates.</span></span>  
  
<span data-ttu-id="bdc3e-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bdc3e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bdc3e-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="bdc3e-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="bdc3e-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="bdc3e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="bdc3e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> endpointBehaviors**](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="bdc3e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="bdc3e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="bdc3e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="bdc3e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="bdc3e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="bdc3e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de certificados**](servicecertificate-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="bdc3e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)</span></span>\
<span data-ttu-id="bdc3e-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> scopedCertificates**](scopedcertificates-element.md)</span><span class="sxs-lookup"><span data-stu-id="bdc3e-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<scopedCertificates>**](scopedcertificates-element.md)</span></span>\
<span data-ttu-id="bdc3e-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Adicionar >**</span><span class="sxs-lookup"><span data-stu-id="bdc3e-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdc3e-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bdc3e-113">Syntax</span></span>  
  
```xml  
<add findValue="String"
     storeLocation="CurrentUser/LocalMachine"
     storeName=" CurrentUser/LocalMachine"
     targetUri="string"
     x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bdc3e-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="bdc3e-114">Attributes and Elements</span></span>  
 <span data-ttu-id="bdc3e-115">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="bdc3e-115">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bdc3e-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="bdc3e-116">Attributes</span></span>  
  
|<span data-ttu-id="bdc3e-117">Atributo</span><span class="sxs-lookup"><span data-stu-id="bdc3e-117">Attribute</span></span>|<span data-ttu-id="bdc3e-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="bdc3e-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bdc3e-119">targetUri</span><span class="sxs-lookup"><span data-stu-id="bdc3e-119">targetUri</span></span>|<span data-ttu-id="bdc3e-120">Cadeia.</span><span class="sxs-lookup"><span data-stu-id="bdc3e-120">String.</span></span> <span data-ttu-id="bdc3e-121">Especifica o URI do serviço associado ao certificado.</span><span class="sxs-lookup"><span data-stu-id="bdc3e-121">Specifies the URI of the service associated with the certificate.</span></span>|  
|<span data-ttu-id="bdc3e-122">findValue</span><span class="sxs-lookup"><span data-stu-id="bdc3e-122">findValue</span></span>|<span data-ttu-id="bdc3e-123">Cadeia.</span><span class="sxs-lookup"><span data-stu-id="bdc3e-123">String.</span></span> <span data-ttu-id="bdc3e-124">O valor a ser procurado.</span><span class="sxs-lookup"><span data-stu-id="bdc3e-124">The value to search for.</span></span>|  
|<span data-ttu-id="bdc3e-125">x509FindType</span><span class="sxs-lookup"><span data-stu-id="bdc3e-125">x509FindType</span></span>|<span data-ttu-id="bdc3e-126">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="bdc3e-126">Enumeration.</span></span> <span data-ttu-id="bdc3e-127">Um dos campos de certificado a serem pesquisados.</span><span class="sxs-lookup"><span data-stu-id="bdc3e-127">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="bdc3e-128">storeLocation</span><span class="sxs-lookup"><span data-stu-id="bdc3e-128">storeLocation</span></span>|<span data-ttu-id="bdc3e-129">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="bdc3e-129">Enumeration.</span></span> <span data-ttu-id="bdc3e-130">Um dos dois locais de armazenamento para pesquisar.</span><span class="sxs-lookup"><span data-stu-id="bdc3e-130">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="bdc3e-131">storeName</span><span class="sxs-lookup"><span data-stu-id="bdc3e-131">storeName</span></span>|<span data-ttu-id="bdc3e-132">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="bdc3e-132">Enumeration.</span></span> <span data-ttu-id="bdc3e-133">Uma das lojas de sistema para pesquisa.</span><span class="sxs-lookup"><span data-stu-id="bdc3e-133">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="bdc3e-134">Atributo FindValue</span><span class="sxs-lookup"><span data-stu-id="bdc3e-134">findValue Attribute</span></span>  
  
|<span data-ttu-id="bdc3e-135">Valor</span><span class="sxs-lookup"><span data-stu-id="bdc3e-135">Value</span></span>|<span data-ttu-id="bdc3e-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="bdc3e-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bdc3e-137">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="bdc3e-137">String</span></span>|<span data-ttu-id="bdc3e-138">O valor depende do campo (especificado pelo atributo X509FindType) que está sendo pesquisado.</span><span class="sxs-lookup"><span data-stu-id="bdc3e-138">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="bdc3e-139">Por exemplo, se estiver procurando uma impressão digital, o valor deverá ser uma cadeia de caracteres de números hexadecimais.</span><span class="sxs-lookup"><span data-stu-id="bdc3e-139">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="bdc3e-140">Atributo x509FindType</span><span class="sxs-lookup"><span data-stu-id="bdc3e-140">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="bdc3e-141">Valor</span><span class="sxs-lookup"><span data-stu-id="bdc3e-141">Value</span></span>|<span data-ttu-id="bdc3e-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="bdc3e-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bdc3e-143">Enumeração</span><span class="sxs-lookup"><span data-stu-id="bdc3e-143">Enumeration</span></span>|<span data-ttu-id="bdc3e-144">Os valores são: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName , FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="bdc3e-144">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="bdc3e-145">Atributo storeLocation</span><span class="sxs-lookup"><span data-stu-id="bdc3e-145">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="bdc3e-146">Valor</span><span class="sxs-lookup"><span data-stu-id="bdc3e-146">Value</span></span>|<span data-ttu-id="bdc3e-147">Descrição</span><span class="sxs-lookup"><span data-stu-id="bdc3e-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bdc3e-148">Enumeração</span><span class="sxs-lookup"><span data-stu-id="bdc3e-148">Enumeration</span></span>|<span data-ttu-id="bdc3e-149">CurrentUser ou LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="bdc3e-149">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="bdc3e-150">Atributo storeName</span><span class="sxs-lookup"><span data-stu-id="bdc3e-150">storeName Attribute</span></span>  
  
|<span data-ttu-id="bdc3e-151">Valor</span><span class="sxs-lookup"><span data-stu-id="bdc3e-151">Value</span></span>|<span data-ttu-id="bdc3e-152">Descrição</span><span class="sxs-lookup"><span data-stu-id="bdc3e-152">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bdc3e-153">Enumeração</span><span class="sxs-lookup"><span data-stu-id="bdc3e-153">Enumeration</span></span>|<span data-ttu-id="bdc3e-154">Os valores são: Catálogo, AuthRoot, CertificateAuthority, não permitido, My, root, TrustedPeople e TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="bdc3e-154">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bdc3e-155">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="bdc3e-155">Child Elements</span></span>  
 <span data-ttu-id="bdc3e-156">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="bdc3e-156">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bdc3e-157">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="bdc3e-157">Parent Elements</span></span>  
  
|<span data-ttu-id="bdc3e-158">Elemento</span><span class="sxs-lookup"><span data-stu-id="bdc3e-158">Element</span></span>|<span data-ttu-id="bdc3e-159">Descrição</span><span class="sxs-lookup"><span data-stu-id="bdc3e-159">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bdc3e-160">\<scopedCertificates></span><span class="sxs-lookup"><span data-stu-id="bdc3e-160">\<scopedCertificates></span></span>](scopedcertificates-element.md)|<span data-ttu-id="bdc3e-161">Representa uma coleção de certificados X. 509 fornecidos por serviços específicos (com escopo) para autenticação.</span><span class="sxs-lookup"><span data-stu-id="bdc3e-161">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bdc3e-162">Comentários</span><span class="sxs-lookup"><span data-stu-id="bdc3e-162">Remarks</span></span>  
 <span data-ttu-id="bdc3e-163">Esse elemento permite que o cliente configure um certificado de serviço para usar com base na URL do serviço com o qual se comunica.</span><span class="sxs-lookup"><span data-stu-id="bdc3e-163">This element enables the client to configure a service certificate to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="bdc3e-164">Isso é especialmente útil em cenários de token emitidos em que um cliente pode se comunicar com vários serviços (o serviço final, bem como os serviços de token de segurança intermediários).</span><span class="sxs-lookup"><span data-stu-id="bdc3e-164">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="bdc3e-165">Para associações que usam segurança de mensagem baseada em certificado, esse certificado é usado para criptografar mensagens para o serviço e deve ser usado pelo serviço para assinar respostas para o cliente.</span><span class="sxs-lookup"><span data-stu-id="bdc3e-165">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="bdc3e-166">Se uma associação exigir um certificado para o serviço e nenhum certificado específico para a URL do serviço for encontrado no ScopedCertificates, o certificado padrão será usado.</span><span class="sxs-lookup"><span data-stu-id="bdc3e-166">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="bdc3e-167">Para obter mais informações, consulte a seção "certificados com escopo" [de como: Criar um cliente](../../../wcf/feature-details/how-to-create-a-federated-client.md)federado.</span><span class="sxs-lookup"><span data-stu-id="bdc3e-167">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bdc3e-168">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bdc3e-168">Example</span></span>  
 <span data-ttu-id="bdc3e-169">O exemplo a seguir adiciona um certificado X. 509 à coleção.</span><span class="sxs-lookup"><span data-stu-id="bdc3e-169">The following example adds an X.509 certificate the collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bdc3e-170">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bdc3e-170">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [<span data-ttu-id="bdc3e-171">Como: Criar um cliente federado</span><span class="sxs-lookup"><span data-stu-id="bdc3e-171">How to: Create a Federated Client</span></span>](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [<span data-ttu-id="bdc3e-172">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="bdc3e-172">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="bdc3e-173">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="bdc3e-173">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="bdc3e-174">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="bdc3e-174">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
