---
title: Elemento <defaultCertificate>
ms.date: 03/30/2017
ms.assetid: f1ddf364-9a00-45d3-b989-ff381c154ce6
ms.openlocfilehash: cce236bf80fa00f01a3b5f4680d975f83fde0c16
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400423"
---
# <a name="defaultcertificate-element"></a><span data-ttu-id="c5660-102">Elemento \<defaultCertificate></span><span class="sxs-lookup"><span data-stu-id="c5660-102">\<defaultCertificate> Element</span></span>
<span data-ttu-id="c5660-103">Especifica um certificado X. 509 a ser usado quando um serviço ou STS não fornecer um por meio de um protocolo de negociação.</span><span class="sxs-lookup"><span data-stu-id="c5660-103">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="c5660-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c5660-104">Syntax</span></span>  
  
```xml  
<defaultCertificate findValue="String"
                    storeLocation=" CurrentUser/LocalMachine"
                    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                    x509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialiNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5660-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c5660-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c5660-106">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="c5660-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5660-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="c5660-107">Attributes</span></span>  
  
|<span data-ttu-id="c5660-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="c5660-108">Attribute</span></span>|<span data-ttu-id="c5660-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5660-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c5660-110">findValue</span><span class="sxs-lookup"><span data-stu-id="c5660-110">findValue</span></span>|<span data-ttu-id="c5660-111">Cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c5660-111">String.</span></span> <span data-ttu-id="c5660-112">O valor a ser procurado.</span><span class="sxs-lookup"><span data-stu-id="c5660-112">The value to search for.</span></span>|  
|<span data-ttu-id="c5660-113">x509FindType</span><span class="sxs-lookup"><span data-stu-id="c5660-113">x509FindType</span></span>|<span data-ttu-id="c5660-114">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="c5660-114">Enumeration.</span></span> <span data-ttu-id="c5660-115">Um dos campos de certificado a serem pesquisados.</span><span class="sxs-lookup"><span data-stu-id="c5660-115">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="c5660-116">storeLocation</span><span class="sxs-lookup"><span data-stu-id="c5660-116">storeLocation</span></span>|<span data-ttu-id="c5660-117">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="c5660-117">Enumeration.</span></span> <span data-ttu-id="c5660-118">Um dos dois locais de armazenamento do sistema para pesquisar.</span><span class="sxs-lookup"><span data-stu-id="c5660-118">One of the two system store locations to search.</span></span>|  
|<span data-ttu-id="c5660-119">storeName</span><span class="sxs-lookup"><span data-stu-id="c5660-119">storeName</span></span>|<span data-ttu-id="c5660-120">Enumeração.</span><span class="sxs-lookup"><span data-stu-id="c5660-120">Enumeration.</span></span> <span data-ttu-id="c5660-121">Uma das lojas de sistema para pesquisa.</span><span class="sxs-lookup"><span data-stu-id="c5660-121">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="c5660-122">Atributo FindValue</span><span class="sxs-lookup"><span data-stu-id="c5660-122">findValue Attribute</span></span>  
  
|<span data-ttu-id="c5660-123">Valor</span><span class="sxs-lookup"><span data-stu-id="c5660-123">Value</span></span>|<span data-ttu-id="c5660-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5660-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c5660-125">String</span><span class="sxs-lookup"><span data-stu-id="c5660-125">String</span></span>|<span data-ttu-id="c5660-126">O valor depende do campo (especificado pelo atributo X509FindType) que está sendo pesquisado.</span><span class="sxs-lookup"><span data-stu-id="c5660-126">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="c5660-127">Por exemplo, se estiver procurando uma impressão digital, o valor deverá ser uma cadeia de caracteres de números hexadecimais.</span><span class="sxs-lookup"><span data-stu-id="c5660-127">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="c5660-128">Atributo x509FindType</span><span class="sxs-lookup"><span data-stu-id="c5660-128">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="c5660-129">Valor</span><span class="sxs-lookup"><span data-stu-id="c5660-129">Value</span></span>|<span data-ttu-id="c5660-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5660-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c5660-131">Enumeração</span><span class="sxs-lookup"><span data-stu-id="c5660-131">Enumeration</span></span>|<span data-ttu-id="c5660-132">Os valores incluem: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span><span class="sxs-lookup"><span data-stu-id="c5660-132">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="c5660-133">Atributo storeLocation</span><span class="sxs-lookup"><span data-stu-id="c5660-133">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="c5660-134">Valor</span><span class="sxs-lookup"><span data-stu-id="c5660-134">Value</span></span>|<span data-ttu-id="c5660-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5660-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c5660-136">Enumeração</span><span class="sxs-lookup"><span data-stu-id="c5660-136">Enumeration</span></span>|<span data-ttu-id="c5660-137">CurrentUser ou LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="c5660-137">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="c5660-138">Atributo storeName</span><span class="sxs-lookup"><span data-stu-id="c5660-138">storeName Attribute</span></span>  
  
|<span data-ttu-id="c5660-139">Valor</span><span class="sxs-lookup"><span data-stu-id="c5660-139">Value</span></span>|<span data-ttu-id="c5660-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5660-140">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c5660-141">Enumeração</span><span class="sxs-lookup"><span data-stu-id="c5660-141">Enumeration</span></span>|<span data-ttu-id="c5660-142">Os valores incluem: catálogo, AuthRoot, CertificateAuthority, não permitido, My, root, TrustedPeople e TrustedPublisher.</span><span class="sxs-lookup"><span data-stu-id="c5660-142">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c5660-143">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c5660-143">Child Elements</span></span>  
 <span data-ttu-id="c5660-144">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c5660-144">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c5660-145">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c5660-145">Parent Elements</span></span>  
  
|<span data-ttu-id="c5660-146">Elemento</span><span class="sxs-lookup"><span data-stu-id="c5660-146">Element</span></span>|<span data-ttu-id="c5660-147">Descrição</span><span class="sxs-lookup"><span data-stu-id="c5660-147">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="c5660-148">Especifica um certificado a ser usado ao autenticar um serviço para o cliente.</span><span class="sxs-lookup"><span data-stu-id="c5660-148">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5660-149">Comentários</span><span class="sxs-lookup"><span data-stu-id="c5660-149">Remarks</span></span>  
 <span data-ttu-id="c5660-150">Para associações que usam segurança de mensagem baseada em certificado, o certificado especificado por esse elemento de configuração é usado para criptografar mensagens para o serviço e deve ser usado pelo serviço para assinar respostas para o cliente.</span><span class="sxs-lookup"><span data-stu-id="c5660-150">For bindings that use certificate-based message security, certificate specified by this configuration element is used to encrypt messages to the service and is expected to be used by the service for signing replies to the client.</span></span> <span data-ttu-id="c5660-151">Ele armazena um único certificado a ser usado quando nenhum certificado é especificado por um serviço.</span><span class="sxs-lookup"><span data-stu-id="c5660-151">It stores a single certificate to be used when no certificate is specified by a service.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5660-152">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c5660-152">Example</span></span>  
 <span data-ttu-id="c5660-153">O exemplo a seguir especifica um certificado a ser usado para pontos de extremidade cujo URI começa com `http://www.contoso.com` e um certificado a ser usado para todos os outros pontos de extremidade que não executam a negociação de certificado.</span><span class="sxs-lookup"><span data-stu-id="c5660-153">The following example specifies a certificate to use for endpoints whose URI begins with `http://www.contoso.com` and a certificate to use for all other endpoints that do not perform certificate negotiation.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c5660-154">Confira também</span><span class="sxs-lookup"><span data-stu-id="c5660-154">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509DefaultServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.DefaultCertificate%2A>
- [<span data-ttu-id="c5660-155">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="c5660-155">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [\<authentication>](authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="c5660-156">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="c5660-156">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="c5660-157">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="c5660-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
