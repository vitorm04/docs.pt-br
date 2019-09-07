---
title: Elemento <defaultCertificate>
ms.date: 03/30/2017
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
ms.openlocfilehash: cce236bf80fa00f01a3b5f4680d975f83fde0c16
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400423"
---
# <a name="defaultcertificate-element"></a><span data-ttu-id="44b7a-102">\<Elemento de > DefaultCertificate</span><span class="sxs-lookup"><span data-stu-id="44b7a-102">\<defaultCertificate> Element</span></span>
<span data-ttu-id="44b7a-103">Especifica um certificado X. 509 a ser usado quando um serviço ou STS não fornecer um por meio de um protocolo de negociação.</span><span class="sxs-lookup"><span data-stu-id="44b7a-103">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>  
  
<span data-ttu-id="44b7a-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="44b7a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="44b7a-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="44b7a-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="44b7a-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="44b7a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="44b7a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> endpointBehaviors**](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="44b7a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="44b7a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="44b7a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="44b7a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="44b7a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="44b7a-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de certificados**](servicecertificate-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="44b7a-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)</span></span>\
<span data-ttu-id="44b7a-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> DefaultCertificate**</span><span class="sxs-lookup"><span data-stu-id="44b7a-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultCertificate>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44b7a-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="44b7a-112">Syntax</span></span>  
  
```xml  
<defaultCertificate findValue="String"
                    storeLocation=" CurrentUser/LocalMachine"
                    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                    x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44b7a-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="44b7a-113">Attributes and Elements</span></span>  
 <span data-ttu-id="44b7a-114">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="44b7a-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44b7a-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="44b7a-115">Attributes</span></span>  
  
|<span data-ttu-id="44b7a-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="44b7a-116">Attribute</span></span>|<span data-ttu-id="44b7a-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="44b7a-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="44b7a-118">findValue</span><span class="sxs-lookup"><span data-stu-id="44b7a-118">findValue</span></span>|<span data-ttu-id="44b7a-119">Cadeia.</span><span class="sxs-lookup"><span data-stu-id="44b7a-119">String.</span></span> <span data-ttu-id="44b7a-120">O valor a ser procurado.</span><span class="sxs-lookup"><span data-stu-id="44b7a-120">The value to search for.</span></span>|  
|<span data-ttu-id="44b7a-121">x509FindType</span><span class="sxs-lookup"><span data-stu-id="44b7a-121">x509FindType</span></span>|<span data-ttu-id="44b7a-122">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="44b7a-122">Enumeration.</span></span> <span data-ttu-id="44b7a-123">Um dos campos de certificado a serem pesquisados.</span><span class="sxs-lookup"><span data-stu-id="44b7a-123">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="44b7a-124">storeLocation</span><span class="sxs-lookup"><span data-stu-id="44b7a-124">storeLocation</span></span>|<span data-ttu-id="44b7a-125">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="44b7a-125">Enumeration.</span></span> <span data-ttu-id="44b7a-126">Um dos dois locais de armazenamento do sistema para pesquisar.</span><span class="sxs-lookup"><span data-stu-id="44b7a-126">One of the two system store locations to search.</span></span>|  
|<span data-ttu-id="44b7a-127">storeName</span><span class="sxs-lookup"><span data-stu-id="44b7a-127">storeName</span></span>|<span data-ttu-id="44b7a-128">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="44b7a-128">Enumeration.</span></span> <span data-ttu-id="44b7a-129">Uma das lojas de sistema para pesquisa.</span><span class="sxs-lookup"><span data-stu-id="44b7a-129">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="44b7a-130">Atributo FindValue</span><span class="sxs-lookup"><span data-stu-id="44b7a-130">findValue Attribute</span></span>  
  
|<span data-ttu-id="44b7a-131">Valor</span><span class="sxs-lookup"><span data-stu-id="44b7a-131">Value</span></span>|<span data-ttu-id="44b7a-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="44b7a-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="44b7a-133">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="44b7a-133">String</span></span>|<span data-ttu-id="44b7a-134">O valor depende do campo (especificado pelo atributo X509FindType) que está sendo pesquisado.</span><span class="sxs-lookup"><span data-stu-id="44b7a-134">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="44b7a-135">Por exemplo, se estiver procurando uma impressão digital, o valor deverá ser uma cadeia de caracteres de números hexadecimais.</span><span class="sxs-lookup"><span data-stu-id="44b7a-135">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="44b7a-136">Atributo x509FindType</span><span class="sxs-lookup"><span data-stu-id="44b7a-136">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="44b7a-137">Valor</span><span class="sxs-lookup"><span data-stu-id="44b7a-137">Value</span></span>|<span data-ttu-id="44b7a-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="44b7a-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="44b7a-139">Enumeração</span><span class="sxs-lookup"><span data-stu-id="44b7a-139">Enumeration</span></span>|<span data-ttu-id="44b7a-140">Os valores são: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName , FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="44b7a-140">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="44b7a-141">Atributo storeLocation</span><span class="sxs-lookup"><span data-stu-id="44b7a-141">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="44b7a-142">Valor</span><span class="sxs-lookup"><span data-stu-id="44b7a-142">Value</span></span>|<span data-ttu-id="44b7a-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="44b7a-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="44b7a-144">Enumeração</span><span class="sxs-lookup"><span data-stu-id="44b7a-144">Enumeration</span></span>|<span data-ttu-id="44b7a-145">CurrentUser ou LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="44b7a-145">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="44b7a-146">Atributo storeName</span><span class="sxs-lookup"><span data-stu-id="44b7a-146">storeName Attribute</span></span>  
  
|<span data-ttu-id="44b7a-147">Valor</span><span class="sxs-lookup"><span data-stu-id="44b7a-147">Value</span></span>|<span data-ttu-id="44b7a-148">Descrição</span><span class="sxs-lookup"><span data-stu-id="44b7a-148">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="44b7a-149">Enumeração</span><span class="sxs-lookup"><span data-stu-id="44b7a-149">Enumeration</span></span>|<span data-ttu-id="44b7a-150">Os valores são: Catálogo, AuthRoot, CertificateAuthority, não permitido, My, root, TrustedPeople e TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="44b7a-150">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="44b7a-151">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="44b7a-151">Child Elements</span></span>  
 <span data-ttu-id="44b7a-152">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="44b7a-152">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="44b7a-153">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="44b7a-153">Parent Elements</span></span>  
  
|<span data-ttu-id="44b7a-154">Elemento</span><span class="sxs-lookup"><span data-stu-id="44b7a-154">Element</span></span>|<span data-ttu-id="44b7a-155">Descrição</span><span class="sxs-lookup"><span data-stu-id="44b7a-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="44b7a-156">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="44b7a-156">\<serviceCertificate></span></span>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="44b7a-157">Especifica um certificado a ser usado ao autenticar um serviço para o cliente.</span><span class="sxs-lookup"><span data-stu-id="44b7a-157">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44b7a-158">Comentários</span><span class="sxs-lookup"><span data-stu-id="44b7a-158">Remarks</span></span>  
 <span data-ttu-id="44b7a-159">Para associações que usam segurança de mensagem baseada em certificado, o certificado especificado por esse elemento de configuração é usado para criptografar mensagens para o serviço e deve ser usado pelo serviço para assinar respostas para o cliente.</span><span class="sxs-lookup"><span data-stu-id="44b7a-159">For bindings that use certificate-based message security, certificate specified by this configuration element is used to encrypt messages to the service and is expected to be used by the service for signing replies to the client.</span></span> <span data-ttu-id="44b7a-160">Ele armazena um único certificado a ser usado quando nenhum certificado é especificado por um serviço.</span><span class="sxs-lookup"><span data-stu-id="44b7a-160">It stores a single certificate to be used when no certificate is specified by a service.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44b7a-161">Exemplo</span><span class="sxs-lookup"><span data-stu-id="44b7a-161">Example</span></span>  
 <span data-ttu-id="44b7a-162">O exemplo a seguir especifica um certificado a ser usado para pontos de extremidade cujo URI `http://www.contoso.com` começa com e um certificado a ser usado para todos os outros pontos de extremidade que não executam a negociação de certificado.</span><span class="sxs-lookup"><span data-stu-id="44b7a-162">The following example specifies a certificate to use for endpoints whose URI begins with `http://www.contoso.com` and a certificate to use for all other endpoints that do not perform certificate negotiation.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="44b7a-163">Consulte também</span><span class="sxs-lookup"><span data-stu-id="44b7a-163">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>
- [<span data-ttu-id="44b7a-164">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="44b7a-164">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="44b7a-165">\<authentication></span><span class="sxs-lookup"><span data-stu-id="44b7a-165">\<authentication></span></span>](authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="44b7a-166">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="44b7a-166">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="44b7a-167">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="44b7a-167">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
