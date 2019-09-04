---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: 782ca3344774b8412a18e3cf13bff5f969751ea3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252152"
---
# <a name="certificatereference"></a><span data-ttu-id="611a3-101">\<certificateReference></span><span class="sxs-lookup"><span data-stu-id="611a3-101">\<certificateReference></span></span>
<span data-ttu-id="611a3-102">Especifica as configurações que são usadas para localizar e validar um certificado X. 509 em um repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="611a3-102">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
<span data-ttu-id="611a3-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="611a3-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="611a3-104">&nbsp;&nbsp;[ **\<System. identityModel. Services >** ](system-identitymodel-services.md)</span><span class="sxs-lookup"><span data-stu-id="611a3-104">&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)</span></span>\
<span data-ttu-id="611a3-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> federationConfiguration**](federationconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="611a3-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)</span></span>\
<span data-ttu-id="611a3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de certificados**](servicecertificate.md)</span><span class="sxs-lookup"><span data-stu-id="611a3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate.md)</span></span>\
<span data-ttu-id="611a3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> certificateReference**</span><span class="sxs-lookup"><span data-stu-id="611a3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateReference>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="611a3-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="611a3-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="611a3-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="611a3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="611a3-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="611a3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="611a3-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="611a3-111">Attributes</span></span>  
  
|<span data-ttu-id="611a3-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="611a3-112">Attribute</span></span>|<span data-ttu-id="611a3-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="611a3-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="611a3-114">storeName</span><span class="sxs-lookup"><span data-stu-id="611a3-114">storeName</span></span>|<span data-ttu-id="611a3-115">O nome do repositório de certificados X.509.</span><span class="sxs-lookup"><span data-stu-id="611a3-115">The name of the X.509 certificate store.</span></span> <span data-ttu-id="611a3-116">O padrão é "My".</span><span class="sxs-lookup"><span data-stu-id="611a3-116">The default is "My".</span></span> <span data-ttu-id="611a3-117">Opcional.</span><span class="sxs-lookup"><span data-stu-id="611a3-117">Optional.</span></span>|  
|<span data-ttu-id="611a3-118">storeLocation</span><span class="sxs-lookup"><span data-stu-id="611a3-118">storeLocation</span></span>|<span data-ttu-id="611a3-119">Um <xref:System.Security.Cryptography.X509Certificates.StoreLocation> valor que especifica o local do repositório de certificados X. 509.</span><span class="sxs-lookup"><span data-stu-id="611a3-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="611a3-120">O valor padrão é "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="611a3-120">The default value is "LocalMachine".</span></span> <span data-ttu-id="611a3-121">Opcional.</span><span class="sxs-lookup"><span data-stu-id="611a3-121">Optional.</span></span>|  
|<span data-ttu-id="611a3-122">x509FindType</span><span class="sxs-lookup"><span data-stu-id="611a3-122">x509FindType</span></span>|<span data-ttu-id="611a3-123">Um <xref:System.Security.Cryptography.X509Certificates.X509FindType> valor que especifica o tipo de pesquisa que deve ser executada.</span><span class="sxs-lookup"><span data-stu-id="611a3-123">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="611a3-124">O padrão é "FindBySubjectDistinguishedName".</span><span class="sxs-lookup"><span data-stu-id="611a3-124">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="611a3-125">Opcional.</span><span class="sxs-lookup"><span data-stu-id="611a3-125">Optional.</span></span>|  
|<span data-ttu-id="611a3-126">findValue</span><span class="sxs-lookup"><span data-stu-id="611a3-126">findValue</span></span>|<span data-ttu-id="611a3-127">O valor a ser pesquisado no repositório de certificados X.509.</span><span class="sxs-lookup"><span data-stu-id="611a3-127">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="611a3-128">Opcional.</span><span class="sxs-lookup"><span data-stu-id="611a3-128">Optional.</span></span>|  
|<span data-ttu-id="611a3-129">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="611a3-129">isChainIncluded</span></span>|<span data-ttu-id="611a3-130">Especifica se a validação deve ser executada usando a cadeia de certificados.</span><span class="sxs-lookup"><span data-stu-id="611a3-130">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="611a3-131">O padrão é "true"; a validação é executada usando a cadeia de certificados.</span><span class="sxs-lookup"><span data-stu-id="611a3-131">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="611a3-132">Opcional.</span><span class="sxs-lookup"><span data-stu-id="611a3-132">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="611a3-133">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="611a3-133">Child Elements</span></span>  
 <span data-ttu-id="611a3-134">Nenhum</span><span class="sxs-lookup"><span data-stu-id="611a3-134">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="611a3-135">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="611a3-135">Parent Elements</span></span>  
  
|<span data-ttu-id="611a3-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="611a3-136">Element</span></span>|<span data-ttu-id="611a3-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="611a3-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="611a3-138">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="611a3-138">\<serviceCertificate></span></span>](servicecertificate.md)|<span data-ttu-id="611a3-139">Configura o certificado que é usado para criptografar e descriptografar tokens.</span><span class="sxs-lookup"><span data-stu-id="611a3-139">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="611a3-140">Comentários</span><span class="sxs-lookup"><span data-stu-id="611a3-140">Remarks</span></span>  
 <span data-ttu-id="611a3-141">O `<certificateReference>` elemento especifica as configurações que são usadas para localizar e validar um certificado X. 509 em um repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="611a3-141">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="611a3-142">Quando é especificado como o elemento filho do `<serviceCertificate>` elemento, ele especifica as configurações de localização e verificação do certificado X. 509 que é usado para criptografar e descriptografar tokens.</span><span class="sxs-lookup"><span data-stu-id="611a3-142">When it is specified as the child element of the `<serviceCertificate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="611a3-143">O `<certificateReference>` elemento é representado <xref:System.ServiceModel.Configuration.CertificateReferenceElement> pela classe.</span><span class="sxs-lookup"><span data-stu-id="611a3-143">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
