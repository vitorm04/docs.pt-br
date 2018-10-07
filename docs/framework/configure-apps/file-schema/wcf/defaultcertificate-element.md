---
title: Elemento &lt;defaultCertificate&gt;
ms.date: 03/30/2017
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
ms.openlocfilehash: 9b99ee36fdb924ea12f3023984a3aa4b590937e8
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2018
ms.locfileid: "48847848"
---
# <a name="ltdefaultcertificategt-element"></a><span data-ttu-id="ccf36-102">Elemento &lt;defaultCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="ccf36-102">&lt;defaultCertificate&gt; Element</span></span>
<span data-ttu-id="ccf36-103">Especifica um certificado X.509 a ser usado quando um serviço ou STS não fornece um através de um protocolo de negociação.</span><span class="sxs-lookup"><span data-stu-id="ccf36-103">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>  
  
 <span data-ttu-id="ccf36-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ccf36-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ccf36-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="ccf36-105">\<behaviors></span></span>  
<span data-ttu-id="ccf36-106">seção endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="ccf36-106">endpointBehaviors section</span></span>  
<span data-ttu-id="ccf36-107">\<comportamento de ></span><span class="sxs-lookup"><span data-stu-id="ccf36-107">\<behavior></span></span>  
<span data-ttu-id="ccf36-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="ccf36-108">\<clientCredentials></span></span>  
<span data-ttu-id="ccf36-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="ccf36-109">\<serviceCertificate></span></span>  
<span data-ttu-id="ccf36-110">\<defaultCertificate ></span><span class="sxs-lookup"><span data-stu-id="ccf36-110">\<defaultCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccf36-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ccf36-111">Syntax</span></span>  
  
```xml  
<defaultCertificate findValue="String"   
storeLocation=" CurrentUser/LocalMachine"  
storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"   
x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ccf36-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ccf36-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ccf36-113">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="ccf36-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ccf36-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="ccf36-114">Attributes</span></span>  
  
|<span data-ttu-id="ccf36-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="ccf36-115">Attribute</span></span>|<span data-ttu-id="ccf36-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="ccf36-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ccf36-117">findValue</span><span class="sxs-lookup"><span data-stu-id="ccf36-117">findValue</span></span>|<span data-ttu-id="ccf36-118">Cadeia.</span><span class="sxs-lookup"><span data-stu-id="ccf36-118">String.</span></span> <span data-ttu-id="ccf36-119">O valor a ser procurado.</span><span class="sxs-lookup"><span data-stu-id="ccf36-119">The value to search for.</span></span>|  
|<span data-ttu-id="ccf36-120">x509FindType</span><span class="sxs-lookup"><span data-stu-id="ccf36-120">x509FindType</span></span>|<span data-ttu-id="ccf36-121">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="ccf36-121">Enumeration.</span></span> <span data-ttu-id="ccf36-122">Um dos campos do certificado para pesquisar.</span><span class="sxs-lookup"><span data-stu-id="ccf36-122">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="ccf36-123">storeLocation</span><span class="sxs-lookup"><span data-stu-id="ccf36-123">storeLocation</span></span>|<span data-ttu-id="ccf36-124">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="ccf36-124">Enumeration.</span></span> <span data-ttu-id="ccf36-125">Um dos dois sistemas locais de repositório para pesquisar.</span><span class="sxs-lookup"><span data-stu-id="ccf36-125">One of the two system store locations to search.</span></span>|  
|<span data-ttu-id="ccf36-126">storeName</span><span class="sxs-lookup"><span data-stu-id="ccf36-126">storeName</span></span>|<span data-ttu-id="ccf36-127">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="ccf36-127">Enumeration.</span></span> <span data-ttu-id="ccf36-128">Um dos armazenamentos de sistema para pesquisar.</span><span class="sxs-lookup"><span data-stu-id="ccf36-128">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="ccf36-129">findValue atributo</span><span class="sxs-lookup"><span data-stu-id="ccf36-129">findValue Attribute</span></span>  
  
|<span data-ttu-id="ccf36-130">Valor</span><span class="sxs-lookup"><span data-stu-id="ccf36-130">Value</span></span>|<span data-ttu-id="ccf36-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="ccf36-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ccf36-132">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ccf36-132">String</span></span>|<span data-ttu-id="ccf36-133">O valor depende do campo (especificado pelo atributo X509FindType) que está sendo pesquisado.</span><span class="sxs-lookup"><span data-stu-id="ccf36-133">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="ccf36-134">Por exemplo, se você está procurando uma impressão digital, o valor deve ser uma cadeia de caracteres de números hexadecimais.</span><span class="sxs-lookup"><span data-stu-id="ccf36-134">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="ccf36-135">Atributo x509FindType</span><span class="sxs-lookup"><span data-stu-id="ccf36-135">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="ccf36-136">Valor</span><span class="sxs-lookup"><span data-stu-id="ccf36-136">Value</span></span>|<span data-ttu-id="ccf36-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="ccf36-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ccf36-138">Enumeração</span><span class="sxs-lookup"><span data-stu-id="ccf36-138">Enumeration</span></span>|<span data-ttu-id="ccf36-139">Os valores incluem: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="ccf36-139">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="ccf36-140">storeLocation atributo</span><span class="sxs-lookup"><span data-stu-id="ccf36-140">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="ccf36-141">Valor</span><span class="sxs-lookup"><span data-stu-id="ccf36-141">Value</span></span>|<span data-ttu-id="ccf36-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="ccf36-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ccf36-143">Enumeração</span><span class="sxs-lookup"><span data-stu-id="ccf36-143">Enumeration</span></span>|<span data-ttu-id="ccf36-144">CurrentUser ou LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="ccf36-144">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="ccf36-145">storeName atributo</span><span class="sxs-lookup"><span data-stu-id="ccf36-145">storeName Attribute</span></span>  
  
|<span data-ttu-id="ccf36-146">Valor</span><span class="sxs-lookup"><span data-stu-id="ccf36-146">Value</span></span>|<span data-ttu-id="ccf36-147">Descrição</span><span class="sxs-lookup"><span data-stu-id="ccf36-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ccf36-148">Enumeração</span><span class="sxs-lookup"><span data-stu-id="ccf36-148">Enumeration</span></span>|<span data-ttu-id="ccf36-149">Os valores incluem: catálogo de endereços, AuthRoot, CertificateAuthority, não permitido, My, raiz, TrustedPeople e TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="ccf36-149">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ccf36-150">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ccf36-150">Child Elements</span></span>  
 <span data-ttu-id="ccf36-151">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="ccf36-151">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ccf36-152">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ccf36-152">Parent Elements</span></span>  
  
|<span data-ttu-id="ccf36-153">Elemento</span><span class="sxs-lookup"><span data-stu-id="ccf36-153">Element</span></span>|<span data-ttu-id="ccf36-154">Descrição</span><span class="sxs-lookup"><span data-stu-id="ccf36-154">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ccf36-155">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="ccf36-155">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="ccf36-156">Especifica um certificado a ser usado ao autenticar um serviço para o cliente.</span><span class="sxs-lookup"><span data-stu-id="ccf36-156">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ccf36-157">Comentários</span><span class="sxs-lookup"><span data-stu-id="ccf36-157">Remarks</span></span>  
 <span data-ttu-id="ccf36-158">Para associações que usam a segurança de mensagem baseada em certificado, o certificado especificado por este elemento de configuração é usado para criptografar mensagens para o serviço e deve ser usado pelo serviço para assinar respostas ao cliente.</span><span class="sxs-lookup"><span data-stu-id="ccf36-158">For bindings that use certificate-based message security, certificate specified by this configuration element is used to encrypt messages to the service and is expected to be used by the service for signing replies to the client.</span></span> <span data-ttu-id="ccf36-159">Ele armazena um único certificado a ser usado quando nenhum certificado é especificado por um serviço.</span><span class="sxs-lookup"><span data-stu-id="ccf36-159">It stores a single certificate to be used when no certificate is specified by a service.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ccf36-160">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ccf36-160">Example</span></span>  
 <span data-ttu-id="ccf36-161">O exemplo a seguir especifica um certificado a ser usado para pontos de extremidade cujo URI começa com `http://www.contoso.com` e um certificado a ser usado para todos os outros pontos de extremidade que não executam o processo de negociação do certificado.</span><span class="sxs-lookup"><span data-stu-id="ccf36-161">The following example specifies a certificate to use for endpoints whose URI begins with `http://www.contoso.com` and a certificate to use for all other endpoints that do not perform certificate negotiation.</span></span>  
  
```xml  
<serviceCertificate>  
  <defaultCertificate findValue="www.contoso.com"   
                      storeLocation="LocalMachine"  
                      storeName="TrustedPeople"   
                      x509FindType="FindByIssuerDistinguishedName" />  
  <scopedCertificates>  
     <add targetUri="http://www.contoso.com"   
          findValue="www.contoso.com" storeLocation="LocalMachine"  
                  storeName="Root" x509FindType="FindByIssuerName" />  
  </scopedCertificates>  
  <authentication revocationMode="Online"   
   trustedStoreLocation="LocalMachine" />  
</serviceCertificate>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ccf36-162">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ccf36-162">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>  
 [<span data-ttu-id="ccf36-163">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="ccf36-163">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="ccf36-164">\<authentication></span><span class="sxs-lookup"><span data-stu-id="ccf36-164">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)  
 [<span data-ttu-id="ccf36-165">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="ccf36-165">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="ccf36-166">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="ccf36-166">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
