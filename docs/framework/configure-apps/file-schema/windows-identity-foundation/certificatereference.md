---
title: '&lt;certificateReference&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: fd0d4742a162000d438851cef9c00e21368b7ba1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcertificatereferencegt"></a><span data-ttu-id="59d83-102">&lt;certificateReference&gt;</span><span class="sxs-lookup"><span data-stu-id="59d83-102">&lt;certificateReference&gt;</span></span>
<span data-ttu-id="59d83-103">Especifica configurações que são usadas para encontrar e validar um certificado x. 509 em um repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="59d83-103">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
 <span data-ttu-id="59d83-104">\<System ></span><span class="sxs-lookup"><span data-stu-id="59d83-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="59d83-105">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="59d83-105">\<federationConfiguration></span></span>  
<span data-ttu-id="59d83-106">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="59d83-106">\<serviceCertificate></span></span>  
<span data-ttu-id="59d83-107">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="59d83-107">\<certificateReference></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59d83-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="59d83-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59d83-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="59d83-109">Attributes and Elements</span></span>  
 <span data-ttu-id="59d83-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="59d83-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59d83-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="59d83-111">Attributes</span></span>  
  
|<span data-ttu-id="59d83-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="59d83-112">Attribute</span></span>|<span data-ttu-id="59d83-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="59d83-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="59d83-114">storeName</span><span class="sxs-lookup"><span data-stu-id="59d83-114">storeName</span></span>|<span data-ttu-id="59d83-115">O nome do repositório de certificados X.509.</span><span class="sxs-lookup"><span data-stu-id="59d83-115">The name of the X.509 certificate store.</span></span> <span data-ttu-id="59d83-116">O padrão é "My".</span><span class="sxs-lookup"><span data-stu-id="59d83-116">The default is "My".</span></span> <span data-ttu-id="59d83-117">Opcional.</span><span class="sxs-lookup"><span data-stu-id="59d83-117">Optional.</span></span>|  
|<span data-ttu-id="59d83-118">storeLocation</span><span class="sxs-lookup"><span data-stu-id="59d83-118">storeLocation</span></span>|<span data-ttu-id="59d83-119">Um <xref:System.Security.Cryptography.X509Certificates.StoreLocation> valor que especifica o local do repositório de certificados x. 509.</span><span class="sxs-lookup"><span data-stu-id="59d83-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="59d83-120">O valor padrão é "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="59d83-120">The default value is "LocalMachine".</span></span> <span data-ttu-id="59d83-121">Opcional.</span><span class="sxs-lookup"><span data-stu-id="59d83-121">Optional.</span></span>|  
|<span data-ttu-id="59d83-122">X509FindType</span><span class="sxs-lookup"><span data-stu-id="59d83-122">x509FindType</span></span>|<span data-ttu-id="59d83-123">Um <xref:System.Security.Cryptography.X509Certificates.X509FindType> valor que especifica o tipo de pesquisa a ser executado.</span><span class="sxs-lookup"><span data-stu-id="59d83-123">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="59d83-124">O padrão é "FindBySubjectDistinguishedName".</span><span class="sxs-lookup"><span data-stu-id="59d83-124">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="59d83-125">Opcional.</span><span class="sxs-lookup"><span data-stu-id="59d83-125">Optional.</span></span>|  
|<span data-ttu-id="59d83-126">findValue</span><span class="sxs-lookup"><span data-stu-id="59d83-126">findValue</span></span>|<span data-ttu-id="59d83-127">O valor a ser pesquisado no repositório de certificados X.509.</span><span class="sxs-lookup"><span data-stu-id="59d83-127">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="59d83-128">Opcional.</span><span class="sxs-lookup"><span data-stu-id="59d83-128">Optional.</span></span>|  
|<span data-ttu-id="59d83-129">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="59d83-129">isChainIncluded</span></span>|<span data-ttu-id="59d83-130">Especifica se a validação deve ser executada usando a cadeia de certificados.</span><span class="sxs-lookup"><span data-stu-id="59d83-130">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="59d83-131">O padrão é "true"; a validação é executada usando a cadeia de certificados.</span><span class="sxs-lookup"><span data-stu-id="59d83-131">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="59d83-132">Opcional.</span><span class="sxs-lookup"><span data-stu-id="59d83-132">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="59d83-133">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="59d83-133">Child Elements</span></span>  
 <span data-ttu-id="59d83-134">Nenhum</span><span class="sxs-lookup"><span data-stu-id="59d83-134">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="59d83-135">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="59d83-135">Parent Elements</span></span>  
  
|<span data-ttu-id="59d83-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="59d83-136">Element</span></span>|<span data-ttu-id="59d83-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="59d83-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="59d83-138">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="59d83-138">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|<span data-ttu-id="59d83-139">Configura o certificado usado para criptografar e descriptografar tokens.</span><span class="sxs-lookup"><span data-stu-id="59d83-139">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59d83-140">Comentários</span><span class="sxs-lookup"><span data-stu-id="59d83-140">Remarks</span></span>  
 <span data-ttu-id="59d83-141">O `<certificateReference>` elemento Especifica configurações que são usadas para localizar e validar um certificado x. 509 em um repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="59d83-141">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="59d83-142">Quando ele é especificado como o elemento filho de `<serviceCertficate>` elemento, especifica as configurações de local e a verificação do certificado x. 509 que é usada para criptografar e descriptografar tokens.</span><span class="sxs-lookup"><span data-stu-id="59d83-142">When it is specified as the child element of the `<serviceCertficate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="59d83-143">O `<certificateReference>` elemento é representado pela <xref:System.ServiceModel.Configuration.CertificateReferenceElement> classe.</span><span class="sxs-lookup"><span data-stu-id="59d83-143">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
