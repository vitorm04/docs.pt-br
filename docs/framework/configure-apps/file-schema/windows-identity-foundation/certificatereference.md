---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: 6c9c77f96ff6032de43d9b5a257bc0796a19b858
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269335"
---
# <a name="certificatereference"></a><span data-ttu-id="e919a-101">\<certificateReference></span><span class="sxs-lookup"><span data-stu-id="e919a-101">\<certificateReference></span></span>
<span data-ttu-id="e919a-102">Especifica configurações que são usadas para encontrar e validar um certificado x. 509 em um repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="e919a-102">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
 <span data-ttu-id="e919a-103">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="e919a-103">\<system.identityModel.services></span></span>  
<span data-ttu-id="e919a-104">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="e919a-104">\<federationConfiguration></span></span>  
<span data-ttu-id="e919a-105">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="e919a-105">\<serviceCertificate></span></span>  
<span data-ttu-id="e919a-106">\<certificateReference></span><span class="sxs-lookup"><span data-stu-id="e919a-106">\<certificateReference></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e919a-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e919a-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e919a-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e919a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e919a-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e919a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e919a-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="e919a-110">Attributes</span></span>  
  
|<span data-ttu-id="e919a-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="e919a-111">Attribute</span></span>|<span data-ttu-id="e919a-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="e919a-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e919a-113">storeName</span><span class="sxs-lookup"><span data-stu-id="e919a-113">storeName</span></span>|<span data-ttu-id="e919a-114">O nome do repositório de certificados X.509.</span><span class="sxs-lookup"><span data-stu-id="e919a-114">The name of the X.509 certificate store.</span></span> <span data-ttu-id="e919a-115">O padrão é "My".</span><span class="sxs-lookup"><span data-stu-id="e919a-115">The default is "My".</span></span> <span data-ttu-id="e919a-116">Opcional.</span><span class="sxs-lookup"><span data-stu-id="e919a-116">Optional.</span></span>|  
|<span data-ttu-id="e919a-117">storeLocation</span><span class="sxs-lookup"><span data-stu-id="e919a-117">storeLocation</span></span>|<span data-ttu-id="e919a-118">Um <xref:System.Security.Cryptography.X509Certificates.StoreLocation> valor que especifica o local do repositório de certificados X.509.</span><span class="sxs-lookup"><span data-stu-id="e919a-118">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="e919a-119">O valor padrão é "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="e919a-119">The default value is "LocalMachine".</span></span> <span data-ttu-id="e919a-120">Opcional.</span><span class="sxs-lookup"><span data-stu-id="e919a-120">Optional.</span></span>|  
|<span data-ttu-id="e919a-121">x509FindType</span><span class="sxs-lookup"><span data-stu-id="e919a-121">x509FindType</span></span>|<span data-ttu-id="e919a-122">Um <xref:System.Security.Cryptography.X509Certificates.X509FindType> valor que especifica o tipo de pesquisa a ser executado.</span><span class="sxs-lookup"><span data-stu-id="e919a-122">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="e919a-123">O padrão é "FindBySubjectDistinguishedName".</span><span class="sxs-lookup"><span data-stu-id="e919a-123">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="e919a-124">Opcional.</span><span class="sxs-lookup"><span data-stu-id="e919a-124">Optional.</span></span>|  
|<span data-ttu-id="e919a-125">findValue</span><span class="sxs-lookup"><span data-stu-id="e919a-125">findValue</span></span>|<span data-ttu-id="e919a-126">O valor a ser pesquisado no repositório de certificados X.509.</span><span class="sxs-lookup"><span data-stu-id="e919a-126">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="e919a-127">Opcional.</span><span class="sxs-lookup"><span data-stu-id="e919a-127">Optional.</span></span>|  
|<span data-ttu-id="e919a-128">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="e919a-128">isChainIncluded</span></span>|<span data-ttu-id="e919a-129">Especifica se a validação deve ser executada usando a cadeia de certificados.</span><span class="sxs-lookup"><span data-stu-id="e919a-129">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="e919a-130">O padrão é "true"; validação é executada usando a cadeia de certificados.</span><span class="sxs-lookup"><span data-stu-id="e919a-130">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="e919a-131">Opcional.</span><span class="sxs-lookup"><span data-stu-id="e919a-131">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e919a-132">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e919a-132">Child Elements</span></span>  
 <span data-ttu-id="e919a-133">Nenhum</span><span class="sxs-lookup"><span data-stu-id="e919a-133">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e919a-134">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e919a-134">Parent Elements</span></span>  
  
|<span data-ttu-id="e919a-135">Elemento</span><span class="sxs-lookup"><span data-stu-id="e919a-135">Element</span></span>|<span data-ttu-id="e919a-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="e919a-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e919a-137">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="e919a-137">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|<span data-ttu-id="e919a-138">Configura o certificado que é usado para criptografar e descriptografar tokens.</span><span class="sxs-lookup"><span data-stu-id="e919a-138">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e919a-139">Comentários</span><span class="sxs-lookup"><span data-stu-id="e919a-139">Remarks</span></span>  
 <span data-ttu-id="e919a-140">O `<certificateReference>` elemento Especifica configurações que são usadas para encontrar e validar um certificado x. 509 em um repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="e919a-140">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="e919a-141">Quando ele é especificado como o elemento filho a `<serviceCertficate>` elemento, ele especifica as configurações de local e a verificação do certificado X.509 que é usado para criptografar e descriptografar tokens.</span><span class="sxs-lookup"><span data-stu-id="e919a-141">When it is specified as the child element of the `<serviceCertficate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="e919a-142">O `<certificateReference>` elemento é representado pelo <xref:System.ServiceModel.Configuration.CertificateReferenceElement> classe.</span><span class="sxs-lookup"><span data-stu-id="e919a-142">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
