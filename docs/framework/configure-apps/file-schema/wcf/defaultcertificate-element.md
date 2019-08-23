---
title: Elemento <defaultCertificate>
ms.date: 03/30/2017
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
ms.openlocfilehash: 93410e815a156f91db1962f05fb1aa6baca7f955
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919239"
---
# <a name="defaultcertificate-element"></a><span data-ttu-id="2a649-102">\<Elemento de > DefaultCertificate</span><span class="sxs-lookup"><span data-stu-id="2a649-102">\<defaultCertificate> Element</span></span>
<span data-ttu-id="2a649-103">Especifica um certificado X. 509 a ser usado quando um serviço ou STS não fornecer um por meio de um protocolo de negociação.</span><span class="sxs-lookup"><span data-stu-id="2a649-103">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>  
  
 <span data-ttu-id="2a649-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2a649-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2a649-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="2a649-105">\<behaviors></span></span>  
<span data-ttu-id="2a649-106">seção endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="2a649-106">endpointBehaviors section</span></span>  
<span data-ttu-id="2a649-107">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="2a649-107">\<behavior></span></span>  
<span data-ttu-id="2a649-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="2a649-108">\<clientCredentials></span></span>  
<span data-ttu-id="2a649-109">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="2a649-109">\<serviceCertificate></span></span>  
<span data-ttu-id="2a649-110">\<defaultCertificate></span><span class="sxs-lookup"><span data-stu-id="2a649-110">\<defaultCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a649-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2a649-111">Syntax</span></span>  
  
```xml  
<defaultCertificate findValue="String"
                    storeLocation=" CurrentUser/LocalMachine"
                    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                    x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a649-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2a649-112">Attributes and Elements</span></span>  
 <span data-ttu-id="2a649-113">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="2a649-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a649-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="2a649-114">Attributes</span></span>  
  
|<span data-ttu-id="2a649-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="2a649-115">Attribute</span></span>|<span data-ttu-id="2a649-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="2a649-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2a649-117">findValue</span><span class="sxs-lookup"><span data-stu-id="2a649-117">findValue</span></span>|<span data-ttu-id="2a649-118">Cadeia.</span><span class="sxs-lookup"><span data-stu-id="2a649-118">String.</span></span> <span data-ttu-id="2a649-119">O valor a ser procurado.</span><span class="sxs-lookup"><span data-stu-id="2a649-119">The value to search for.</span></span>|  
|<span data-ttu-id="2a649-120">x509FindType</span><span class="sxs-lookup"><span data-stu-id="2a649-120">x509FindType</span></span>|<span data-ttu-id="2a649-121">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="2a649-121">Enumeration.</span></span> <span data-ttu-id="2a649-122">Um dos campos de certificado a serem pesquisados.</span><span class="sxs-lookup"><span data-stu-id="2a649-122">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="2a649-123">storeLocation</span><span class="sxs-lookup"><span data-stu-id="2a649-123">storeLocation</span></span>|<span data-ttu-id="2a649-124">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="2a649-124">Enumeration.</span></span> <span data-ttu-id="2a649-125">Um dos dois locais de armazenamento do sistema para pesquisar.</span><span class="sxs-lookup"><span data-stu-id="2a649-125">One of the two system store locations to search.</span></span>|  
|<span data-ttu-id="2a649-126">storeName</span><span class="sxs-lookup"><span data-stu-id="2a649-126">storeName</span></span>|<span data-ttu-id="2a649-127">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="2a649-127">Enumeration.</span></span> <span data-ttu-id="2a649-128">Uma das lojas de sistema para pesquisa.</span><span class="sxs-lookup"><span data-stu-id="2a649-128">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="2a649-129">Atributo FindValue</span><span class="sxs-lookup"><span data-stu-id="2a649-129">findValue Attribute</span></span>  
  
|<span data-ttu-id="2a649-130">Valor</span><span class="sxs-lookup"><span data-stu-id="2a649-130">Value</span></span>|<span data-ttu-id="2a649-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="2a649-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2a649-132">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="2a649-132">String</span></span>|<span data-ttu-id="2a649-133">O valor depende do campo (especificado pelo atributo X509FindType) que está sendo pesquisado.</span><span class="sxs-lookup"><span data-stu-id="2a649-133">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="2a649-134">Por exemplo, se estiver procurando uma impressão digital, o valor deverá ser uma cadeia de caracteres de números hexadecimais.</span><span class="sxs-lookup"><span data-stu-id="2a649-134">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="2a649-135">Atributo x509FindType</span><span class="sxs-lookup"><span data-stu-id="2a649-135">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="2a649-136">Valor</span><span class="sxs-lookup"><span data-stu-id="2a649-136">Value</span></span>|<span data-ttu-id="2a649-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="2a649-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2a649-138">Enumeração</span><span class="sxs-lookup"><span data-stu-id="2a649-138">Enumeration</span></span>|<span data-ttu-id="2a649-139">Os valores são: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName , FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="2a649-139">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="2a649-140">Atributo storeLocation</span><span class="sxs-lookup"><span data-stu-id="2a649-140">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="2a649-141">Valor</span><span class="sxs-lookup"><span data-stu-id="2a649-141">Value</span></span>|<span data-ttu-id="2a649-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="2a649-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2a649-143">Enumeração</span><span class="sxs-lookup"><span data-stu-id="2a649-143">Enumeration</span></span>|<span data-ttu-id="2a649-144">CurrentUser ou LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="2a649-144">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="2a649-145">Atributo storeName</span><span class="sxs-lookup"><span data-stu-id="2a649-145">storeName Attribute</span></span>  
  
|<span data-ttu-id="2a649-146">Valor</span><span class="sxs-lookup"><span data-stu-id="2a649-146">Value</span></span>|<span data-ttu-id="2a649-147">Descrição</span><span class="sxs-lookup"><span data-stu-id="2a649-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2a649-148">Enumeração</span><span class="sxs-lookup"><span data-stu-id="2a649-148">Enumeration</span></span>|<span data-ttu-id="2a649-149">Os valores são: Catálogo, AuthRoot, CertificateAuthority, não permitido, My, root, TrustedPeople e TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="2a649-149">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2a649-150">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2a649-150">Child Elements</span></span>  
 <span data-ttu-id="2a649-151">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="2a649-151">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2a649-152">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2a649-152">Parent Elements</span></span>  
  
|<span data-ttu-id="2a649-153">Elemento</span><span class="sxs-lookup"><span data-stu-id="2a649-153">Element</span></span>|<span data-ttu-id="2a649-154">Descrição</span><span class="sxs-lookup"><span data-stu-id="2a649-154">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a649-155">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="2a649-155">\<serviceCertificate></span></span>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="2a649-156">Especifica um certificado a ser usado ao autenticar um serviço para o cliente.</span><span class="sxs-lookup"><span data-stu-id="2a649-156">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a649-157">Comentários</span><span class="sxs-lookup"><span data-stu-id="2a649-157">Remarks</span></span>  
 <span data-ttu-id="2a649-158">Para associações que usam segurança de mensagem baseada em certificado, o certificado especificado por esse elemento de configuração é usado para criptografar mensagens para o serviço e deve ser usado pelo serviço para assinar respostas para o cliente.</span><span class="sxs-lookup"><span data-stu-id="2a649-158">For bindings that use certificate-based message security, certificate specified by this configuration element is used to encrypt messages to the service and is expected to be used by the service for signing replies to the client.</span></span> <span data-ttu-id="2a649-159">Ele armazena um único certificado a ser usado quando nenhum certificado é especificado por um serviço.</span><span class="sxs-lookup"><span data-stu-id="2a649-159">It stores a single certificate to be used when no certificate is specified by a service.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a649-160">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2a649-160">Example</span></span>  
 <span data-ttu-id="2a649-161">O exemplo a seguir especifica um certificado a ser usado para pontos de extremidade cujo URI `http://www.contoso.com` começa com e um certificado a ser usado para todos os outros pontos de extremidade que não executam a negociação de certificado.</span><span class="sxs-lookup"><span data-stu-id="2a649-161">The following example specifies a certificate to use for endpoints whose URI begins with `http://www.contoso.com` and a certificate to use for all other endpoints that do not perform certificate negotiation.</span></span>  
  
```xml  
<serviceCertificate>
  <defaultCertificate findValue="www.contoso.com"
                      storeLocation="LocalMachine"
                      storeName="TrustedPeople"
                      x509FindType="FindByIssuerDistinguishedName" />
  <scopedCertificates>
    <add targetUri="http://www.contoso.com"
         findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="Root"
         x509FindType="FindByIssuerName" />
  </scopedCertificates>
  <authentication revocationMode="Online"
                  trustedStoreLocation="LocalMachine" />
</serviceCertificate>
```  
  
## <a name="see-also"></a><span data-ttu-id="2a649-162">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a649-162">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>
- [<span data-ttu-id="2a649-163">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="2a649-163">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="2a649-164">\<authentication></span><span class="sxs-lookup"><span data-stu-id="2a649-164">\<authentication></span></span>](authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="2a649-165">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="2a649-165">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="2a649-166">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="2a649-166">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
