---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: 47d432a84d070476ddffd9b98a4ba46d8163bdc3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152808"
---
# <a name="certificatereference"></a><span data-ttu-id="1e59d-101">\<certificado> de referência</span><span class="sxs-lookup"><span data-stu-id="1e59d-101">\<certificateReference></span></span>
<span data-ttu-id="1e59d-102">Especifica as configurações usadas para encontrar e validar um certificado X.509 em uma loja de certificados.</span><span class="sxs-lookup"><span data-stu-id="1e59d-102">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
<span data-ttu-id="1e59d-103">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1e59d-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1e59d-104">&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)</span><span class="sxs-lookup"><span data-stu-id="1e59d-104">&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)</span></span>\
<span data-ttu-id="1e59d-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<federaçãoconfiguração>**](federationconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="1e59d-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)</span></span>\
<span data-ttu-id="1e59d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de>de certificados de serviço**](servicecertificate.md)</span><span class="sxs-lookup"><span data-stu-id="1e59d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate.md)</span></span>\
<span data-ttu-id="1e59d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificado>de referência**</span><span class="sxs-lookup"><span data-stu-id="1e59d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateReference>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e59d-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1e59d-108">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
      <certificateReference
        storeName="AddressBook||AuthRoot||CertificateAuthority||Disallowed||My||Root||TrustedPeople||TrustedPublisher"  
        storeLocation="CurrentUser||LocalMachine"  
        x509FindType="FindByThumbprint||FindBySubjectName||FindBySubjectDistinguishedName||FindByIssuerName||FindByIssuerDistinguishedName||FindBySerialNumber||FindByTimeValid||FindByTimeNotYetValid||FindByTimeExpired||FindByTemplateName||FindByApplicationPolicy||FindByCertificatePolicy||FindByExtension||FindByKeyUsage||FindBySubjectKeyIdentifier"  
        findValue=xs:String  
        isChainIncluded=xs:Boolean >  
      </certificateReference>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1e59d-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1e59d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1e59d-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1e59d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1e59d-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="1e59d-111">Attributes</span></span>  
  
|<span data-ttu-id="1e59d-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="1e59d-112">Attribute</span></span>|<span data-ttu-id="1e59d-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="1e59d-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1e59d-114">storeName</span><span class="sxs-lookup"><span data-stu-id="1e59d-114">storeName</span></span>|<span data-ttu-id="1e59d-115">O nome do repositório de certificados X.509.</span><span class="sxs-lookup"><span data-stu-id="1e59d-115">The name of the X.509 certificate store.</span></span> <span data-ttu-id="1e59d-116">O padrão é "Meu".</span><span class="sxs-lookup"><span data-stu-id="1e59d-116">The default is "My".</span></span> <span data-ttu-id="1e59d-117">Opcional.</span><span class="sxs-lookup"><span data-stu-id="1e59d-117">Optional.</span></span>|  
|<span data-ttu-id="1e59d-118">storeLocation</span><span class="sxs-lookup"><span data-stu-id="1e59d-118">storeLocation</span></span>|<span data-ttu-id="1e59d-119">Um <xref:System.Security.Cryptography.X509Certificates.StoreLocation> valor que especifica a localização da loja de certificados X.509.</span><span class="sxs-lookup"><span data-stu-id="1e59d-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="1e59d-120">O valor padrão é "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="1e59d-120">The default value is "LocalMachine".</span></span> <span data-ttu-id="1e59d-121">Opcional.</span><span class="sxs-lookup"><span data-stu-id="1e59d-121">Optional.</span></span>|  
|<span data-ttu-id="1e59d-122">X509findtype</span><span class="sxs-lookup"><span data-stu-id="1e59d-122">x509FindType</span></span>|<span data-ttu-id="1e59d-123">Um <xref:System.Security.Cryptography.X509Certificates.X509FindType> valor que especifica o tipo de pesquisa a ser executado.</span><span class="sxs-lookup"><span data-stu-id="1e59d-123">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="1e59d-124">O padrão é "FindBySubjectDistinguishedName".</span><span class="sxs-lookup"><span data-stu-id="1e59d-124">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="1e59d-125">Opcional.</span><span class="sxs-lookup"><span data-stu-id="1e59d-125">Optional.</span></span>|  
|<span data-ttu-id="1e59d-126">Findvalue</span><span class="sxs-lookup"><span data-stu-id="1e59d-126">findValue</span></span>|<span data-ttu-id="1e59d-127">O valor a ser pesquisado no repositório de certificados X.509.</span><span class="sxs-lookup"><span data-stu-id="1e59d-127">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="1e59d-128">Opcional.</span><span class="sxs-lookup"><span data-stu-id="1e59d-128">Optional.</span></span>|  
|<span data-ttu-id="1e59d-129">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="1e59d-129">isChainIncluded</span></span>|<span data-ttu-id="1e59d-130">Especifica se a validação deve ser realizada usando a cadeia de certificados.</span><span class="sxs-lookup"><span data-stu-id="1e59d-130">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="1e59d-131">O padrão é "verdadeiro"; a validação é realizada usando a cadeia de certificados.</span><span class="sxs-lookup"><span data-stu-id="1e59d-131">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="1e59d-132">Opcional.</span><span class="sxs-lookup"><span data-stu-id="1e59d-132">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1e59d-133">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1e59d-133">Child Elements</span></span>  
 <span data-ttu-id="1e59d-134">Nenhum</span><span class="sxs-lookup"><span data-stu-id="1e59d-134">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1e59d-135">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1e59d-135">Parent Elements</span></span>  
  
|<span data-ttu-id="1e59d-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="1e59d-136">Element</span></span>|<span data-ttu-id="1e59d-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="1e59d-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1e59d-138">\<>de>de certificados de serviço</span><span class="sxs-lookup"><span data-stu-id="1e59d-138">\<serviceCertificate></span></span>](servicecertificate.md)|<span data-ttu-id="1e59d-139">Configura o certificado usado para criptografar e descriptografar tokens.</span><span class="sxs-lookup"><span data-stu-id="1e59d-139">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e59d-140">Comentários</span><span class="sxs-lookup"><span data-stu-id="1e59d-140">Remarks</span></span>  
 <span data-ttu-id="1e59d-141">O `<certificateReference>` elemento especifica as configurações usadas para encontrar e validar um certificado X.509 em uma loja de certificados.</span><span class="sxs-lookup"><span data-stu-id="1e59d-141">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="1e59d-142">Quando ele é especificado como `<serviceCertificate>` o elemento filho do elemento, ele especifica as configurações de localização e verificação do certificado X.509 que é usado para criptografar e descriptografar tokens.</span><span class="sxs-lookup"><span data-stu-id="1e59d-142">When it is specified as the child element of the `<serviceCertificate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="1e59d-143">O `<certificateReference>` elemento é <xref:System.ServiceModel.Configuration.CertificateReferenceElement> representado pela classe.</span><span class="sxs-lookup"><span data-stu-id="1e59d-143">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
