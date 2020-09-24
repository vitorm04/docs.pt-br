---
title: Elemento <defaultCertificate>
ms.date: 03/30/2017
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
ms.openlocfilehash: 2eaec4f4296f90579ca32d817f0a20da4ccc9a37
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153892"
---
# <a name="defaultcertificate-element"></a><span data-ttu-id="92ba6-102">Elemento \<defaultCertificate></span><span class="sxs-lookup"><span data-stu-id="92ba6-102">\<defaultCertificate> Element</span></span>

<span data-ttu-id="92ba6-103">Especifica um certificado X. 509 a ser usado quando um serviço ou STS não fornecer um por meio de um protocolo de negociação.</span><span class="sxs-lookup"><span data-stu-id="92ba6-103">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="92ba6-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="92ba6-104">Syntax</span></span>  
  
```xml  
<defaultCertificate findValue="String"
                    storeLocation=" CurrentUser/LocalMachine"
                    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                    x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="92ba6-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="92ba6-105">Attributes and Elements</span></span>  

 <span data-ttu-id="92ba6-106">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="92ba6-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="92ba6-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="92ba6-107">Attributes</span></span>  
  
|<span data-ttu-id="92ba6-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="92ba6-108">Attribute</span></span>|<span data-ttu-id="92ba6-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="92ba6-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="92ba6-110">findValue</span><span class="sxs-lookup"><span data-stu-id="92ba6-110">findValue</span></span>|<span data-ttu-id="92ba6-111">Cadeia.</span><span class="sxs-lookup"><span data-stu-id="92ba6-111">String.</span></span> <span data-ttu-id="92ba6-112">O valor a ser procurado.</span><span class="sxs-lookup"><span data-stu-id="92ba6-112">The value to search for.</span></span>|  
|<span data-ttu-id="92ba6-113">x509FindType</span><span class="sxs-lookup"><span data-stu-id="92ba6-113">x509FindType</span></span>|<span data-ttu-id="92ba6-114">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="92ba6-114">Enumeration.</span></span> <span data-ttu-id="92ba6-115">Um dos campos de certificado a serem pesquisados.</span><span class="sxs-lookup"><span data-stu-id="92ba6-115">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="92ba6-116">storeLocation</span><span class="sxs-lookup"><span data-stu-id="92ba6-116">storeLocation</span></span>|<span data-ttu-id="92ba6-117">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="92ba6-117">Enumeration.</span></span> <span data-ttu-id="92ba6-118">Um dos dois locais de armazenamento do sistema para pesquisar.</span><span class="sxs-lookup"><span data-stu-id="92ba6-118">One of the two system store locations to search.</span></span>|  
|<span data-ttu-id="92ba6-119">storeName</span><span class="sxs-lookup"><span data-stu-id="92ba6-119">storeName</span></span>|<span data-ttu-id="92ba6-120">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="92ba6-120">Enumeration.</span></span> <span data-ttu-id="92ba6-121">Uma das lojas de sistema para pesquisa.</span><span class="sxs-lookup"><span data-stu-id="92ba6-121">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="92ba6-122">Atributo FindValue</span><span class="sxs-lookup"><span data-stu-id="92ba6-122">findValue Attribute</span></span>  
  
|<span data-ttu-id="92ba6-123">Valor</span><span class="sxs-lookup"><span data-stu-id="92ba6-123">Value</span></span>|<span data-ttu-id="92ba6-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="92ba6-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="92ba6-125">String</span><span class="sxs-lookup"><span data-stu-id="92ba6-125">String</span></span>|<span data-ttu-id="92ba6-126">O valor depende do campo (especificado pelo atributo X509FindType) que está sendo pesquisado.</span><span class="sxs-lookup"><span data-stu-id="92ba6-126">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="92ba6-127">Por exemplo, se estiver procurando uma impressão digital, o valor deverá ser uma cadeia de caracteres de números hexadecimais.</span><span class="sxs-lookup"><span data-stu-id="92ba6-127">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="92ba6-128">Atributo x509FindType</span><span class="sxs-lookup"><span data-stu-id="92ba6-128">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="92ba6-129">Valor</span><span class="sxs-lookup"><span data-stu-id="92ba6-129">Value</span></span>|<span data-ttu-id="92ba6-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="92ba6-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="92ba6-131">Enumeração</span><span class="sxs-lookup"><span data-stu-id="92ba6-131">Enumeration</span></span>|<span data-ttu-id="92ba6-132">Os valores incluem: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="92ba6-132">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="92ba6-133">Atributo storeLocation</span><span class="sxs-lookup"><span data-stu-id="92ba6-133">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="92ba6-134">Valor</span><span class="sxs-lookup"><span data-stu-id="92ba6-134">Value</span></span>|<span data-ttu-id="92ba6-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="92ba6-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="92ba6-136">Enumeração</span><span class="sxs-lookup"><span data-stu-id="92ba6-136">Enumeration</span></span>|<span data-ttu-id="92ba6-137">CurrentUser ou LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="92ba6-137">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="92ba6-138">Atributo storeName</span><span class="sxs-lookup"><span data-stu-id="92ba6-138">storeName Attribute</span></span>  
  
|<span data-ttu-id="92ba6-139">Valor</span><span class="sxs-lookup"><span data-stu-id="92ba6-139">Value</span></span>|<span data-ttu-id="92ba6-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="92ba6-140">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="92ba6-141">Enumeração</span><span class="sxs-lookup"><span data-stu-id="92ba6-141">Enumeration</span></span>|<span data-ttu-id="92ba6-142">Os valores incluem: catálogo, AuthRoot, CertificateAuthority, não permitido, My, root, TrustedPeople e TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="92ba6-142">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="92ba6-143">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="92ba6-143">Child Elements</span></span>  

 <span data-ttu-id="92ba6-144">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="92ba6-144">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="92ba6-145">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="92ba6-145">Parent Elements</span></span>  
  
|<span data-ttu-id="92ba6-146">Elemento</span><span class="sxs-lookup"><span data-stu-id="92ba6-146">Element</span></span>|<span data-ttu-id="92ba6-147">Descrição</span><span class="sxs-lookup"><span data-stu-id="92ba6-147">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="92ba6-148">Especifica um certificado a ser usado ao autenticar um serviço para o cliente.</span><span class="sxs-lookup"><span data-stu-id="92ba6-148">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92ba6-149">Comentários</span><span class="sxs-lookup"><span data-stu-id="92ba6-149">Remarks</span></span>  

 <span data-ttu-id="92ba6-150">Para associações que usam segurança de mensagem baseada em certificado, o certificado especificado por esse elemento de configuração é usado para criptografar mensagens para o serviço e deve ser usado pelo serviço para assinar respostas para o cliente.</span><span class="sxs-lookup"><span data-stu-id="92ba6-150">For bindings that use certificate-based message security, certificate specified by this configuration element is used to encrypt messages to the service and is expected to be used by the service for signing replies to the client.</span></span> <span data-ttu-id="92ba6-151">Ele armazena um único certificado a ser usado quando nenhum certificado é especificado por um serviço.</span><span class="sxs-lookup"><span data-stu-id="92ba6-151">It stores a single certificate to be used when no certificate is specified by a service.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92ba6-152">Exemplo</span><span class="sxs-lookup"><span data-stu-id="92ba6-152">Example</span></span>  

 <span data-ttu-id="92ba6-153">O exemplo a seguir especifica um certificado a ser usado para pontos de extremidade cujo URI começa com `http://www.contoso.com` e um certificado a ser usado para todos os outros pontos de extremidade que não executam a negociação de certificado.</span><span class="sxs-lookup"><span data-stu-id="92ba6-153">The following example specifies a certificate to use for endpoints whose URI begins with `http://www.contoso.com` and a certificate to use for all other endpoints that do not perform certificate negotiation.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="92ba6-154">Confira também</span><span class="sxs-lookup"><span data-stu-id="92ba6-154">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>
- [<span data-ttu-id="92ba6-155">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="92ba6-155">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [\<authentication>](authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="92ba6-156">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="92ba6-156">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="92ba6-157">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="92ba6-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
