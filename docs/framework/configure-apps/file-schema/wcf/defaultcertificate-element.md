---
title: Elemento &lt;defaultCertificate&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: aae72b7ae006a57683ea0e274fbc072c7f69cfb1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltdefaultcertificategt-element"></a><span data-ttu-id="13fa1-102">Elemento &lt;defaultCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="13fa1-102">&lt;defaultCertificate&gt; Element</span></span>
<span data-ttu-id="13fa1-103">Especifica um certificado x. 509 a ser usado quando um serviço ou STS não fornece um através de um protocolo de negociação.</span><span class="sxs-lookup"><span data-stu-id="13fa1-103">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>  
  
 <span data-ttu-id="13fa1-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="13fa1-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="13fa1-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="13fa1-105">\<behaviors></span></span>  
<span data-ttu-id="13fa1-106">seção endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="13fa1-106">endpointBehaviors section</span></span>  
<span data-ttu-id="13fa1-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="13fa1-107">\<behavior></span></span>  
<span data-ttu-id="13fa1-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="13fa1-108">\<clientCredentials></span></span>  
<span data-ttu-id="13fa1-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="13fa1-109">\<serviceCertificate></span></span>  
<span data-ttu-id="13fa1-110">\<defaultCertificate ></span><span class="sxs-lookup"><span data-stu-id="13fa1-110">\<defaultCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13fa1-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="13fa1-111">Syntax</span></span>  
  
```xml  
<defaultCertificate findValue="String"   
storeLocation=" CurrentUser/LocalMachine"  
storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"   
x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13fa1-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="13fa1-112">Attributes and Elements</span></span>  
 <span data-ttu-id="13fa1-113">As seções a seguir descrevem os elementos pai de atributos e elementos filho</span><span class="sxs-lookup"><span data-stu-id="13fa1-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13fa1-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="13fa1-114">Attributes</span></span>  
  
|<span data-ttu-id="13fa1-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="13fa1-115">Attribute</span></span>|<span data-ttu-id="13fa1-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="13fa1-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="13fa1-117">findValue</span><span class="sxs-lookup"><span data-stu-id="13fa1-117">findValue</span></span>|<span data-ttu-id="13fa1-118">Cadeia.</span><span class="sxs-lookup"><span data-stu-id="13fa1-118">String.</span></span> <span data-ttu-id="13fa1-119">O valor a ser procurado.</span><span class="sxs-lookup"><span data-stu-id="13fa1-119">The value to search for.</span></span>|  
|<span data-ttu-id="13fa1-120">X509FindType</span><span class="sxs-lookup"><span data-stu-id="13fa1-120">x509FindType</span></span>|<span data-ttu-id="13fa1-121">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="13fa1-121">Enumeration.</span></span> <span data-ttu-id="13fa1-122">Um dos campos de certificado a ser pesquisado.</span><span class="sxs-lookup"><span data-stu-id="13fa1-122">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="13fa1-123">storeLocation</span><span class="sxs-lookup"><span data-stu-id="13fa1-123">storeLocation</span></span>|<span data-ttu-id="13fa1-124">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="13fa1-124">Enumeration.</span></span> <span data-ttu-id="13fa1-125">Um sistema de dois locais de repositório para pesquisar.</span><span class="sxs-lookup"><span data-stu-id="13fa1-125">One of the two system store locations to search.</span></span>|  
|<span data-ttu-id="13fa1-126">storeName</span><span class="sxs-lookup"><span data-stu-id="13fa1-126">storeName</span></span>|<span data-ttu-id="13fa1-127">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="13fa1-127">Enumeration.</span></span> <span data-ttu-id="13fa1-128">Um dos repositórios de sistema para pesquisar.</span><span class="sxs-lookup"><span data-stu-id="13fa1-128">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="13fa1-129">findValue atributo</span><span class="sxs-lookup"><span data-stu-id="13fa1-129">findValue Attribute</span></span>  
  
|<span data-ttu-id="13fa1-130">Valor</span><span class="sxs-lookup"><span data-stu-id="13fa1-130">Value</span></span>|<span data-ttu-id="13fa1-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="13fa1-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="13fa1-132">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="13fa1-132">String</span></span>|<span data-ttu-id="13fa1-133">O valor depende do campo (especificado pelo atributo X509FindType) que está sendo pesquisado.</span><span class="sxs-lookup"><span data-stu-id="13fa1-133">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="13fa1-134">Por exemplo, se você está procurando uma impressão digital, o valor deve ser uma cadeia de caracteres de números hexadecimais.</span><span class="sxs-lookup"><span data-stu-id="13fa1-134">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="13fa1-135">Atributo x509FindType</span><span class="sxs-lookup"><span data-stu-id="13fa1-135">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="13fa1-136">Valor</span><span class="sxs-lookup"><span data-stu-id="13fa1-136">Value</span></span>|<span data-ttu-id="13fa1-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="13fa1-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="13fa1-138">Enumeração</span><span class="sxs-lookup"><span data-stu-id="13fa1-138">Enumeration</span></span>|<span data-ttu-id="13fa1-139">Os valores incluem: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="13fa1-139">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="13fa1-140">storeLocation atributo</span><span class="sxs-lookup"><span data-stu-id="13fa1-140">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="13fa1-141">Valor</span><span class="sxs-lookup"><span data-stu-id="13fa1-141">Value</span></span>|<span data-ttu-id="13fa1-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="13fa1-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="13fa1-143">Enumeração</span><span class="sxs-lookup"><span data-stu-id="13fa1-143">Enumeration</span></span>|<span data-ttu-id="13fa1-144">CurrentUser ou LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="13fa1-144">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="13fa1-145">Atributo da storeName</span><span class="sxs-lookup"><span data-stu-id="13fa1-145">storeName Attribute</span></span>  
  
|<span data-ttu-id="13fa1-146">Valor</span><span class="sxs-lookup"><span data-stu-id="13fa1-146">Value</span></span>|<span data-ttu-id="13fa1-147">Descrição</span><span class="sxs-lookup"><span data-stu-id="13fa1-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="13fa1-148">Enumeração</span><span class="sxs-lookup"><span data-stu-id="13fa1-148">Enumeration</span></span>|<span data-ttu-id="13fa1-149">Os valores incluem: catálogo de endereços, AuthRoot, CertificateAuthority, não permitidas, My, raiz, TrustedPeople e TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="13fa1-149">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="13fa1-150">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="13fa1-150">Child Elements</span></span>  
 <span data-ttu-id="13fa1-151">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="13fa1-151">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="13fa1-152">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="13fa1-152">Parent Elements</span></span>  
  
|<span data-ttu-id="13fa1-153">Elemento</span><span class="sxs-lookup"><span data-stu-id="13fa1-153">Element</span></span>|<span data-ttu-id="13fa1-154">Descrição</span><span class="sxs-lookup"><span data-stu-id="13fa1-154">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="13fa1-155">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="13fa1-155">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="13fa1-156">Especifica um certificado a ser usado ao autenticar um serviço para o cliente.</span><span class="sxs-lookup"><span data-stu-id="13fa1-156">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13fa1-157">Comentários</span><span class="sxs-lookup"><span data-stu-id="13fa1-157">Remarks</span></span>  
 <span data-ttu-id="13fa1-158">Para associações que usam a segurança de mensagens baseada em certificado, o certificado especificado por este elemento de configuração é usado para criptografar mensagens para o serviço e deve ser usada pelo serviço para assinar respostas ao cliente.</span><span class="sxs-lookup"><span data-stu-id="13fa1-158">For bindings that use certificate-based message security, certificate specified by this configuration element is used to encrypt messages to the service and is expected to be used by the service for signing replies to the client.</span></span> <span data-ttu-id="13fa1-159">Ele armazena um único certificado a ser usado quando nenhum certificado é especificado por um serviço.</span><span class="sxs-lookup"><span data-stu-id="13fa1-159">It stores a single certificate to be used when no certificate is specified by a service.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13fa1-160">Exemplo</span><span class="sxs-lookup"><span data-stu-id="13fa1-160">Example</span></span>  
 <span data-ttu-id="13fa1-161">O exemplo a seguir especifica um certificado a ser usado para pontos de extremidade cujo URI começa com http://www.contoso.com e um certificado a ser usado para todos os outros pontos de extremidade que não executam a negociação do certificado.</span><span class="sxs-lookup"><span data-stu-id="13fa1-161">The following example specifies a certificate to use for endpoints whose URI begins with http://www.contoso.com and a certificate to use for all other endpoints that do not perform certificate negotiation.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="13fa1-162">Consulte também</span><span class="sxs-lookup"><span data-stu-id="13fa1-162">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>  
 [<span data-ttu-id="13fa1-163">Trabalhar com certificados</span><span class="sxs-lookup"><span data-stu-id="13fa1-163">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="13fa1-164">\<autenticação ></span><span class="sxs-lookup"><span data-stu-id="13fa1-164">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)  
 <span data-ttu-id="13fa1-165">[Securing Clients](../../../../../docs/framework/wcf/securing-clients.md) (Protegendo clientes)</span><span class="sxs-lookup"><span data-stu-id="13fa1-165">[Securing Clients](../../../../../docs/framework/wcf/securing-clients.md)</span></span>  
 [<span data-ttu-id="13fa1-166">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="13fa1-166">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
