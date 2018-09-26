---
title: '&lt;CertificateReference&gt;'
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: e04dc90134aadfb8af7b0800c7144963d267f513
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47206885"
---
# <a name="ltcertificatereferencegt"></a><span data-ttu-id="01e0e-102">&lt;CertificateReference&gt;</span><span class="sxs-lookup"><span data-stu-id="01e0e-102">&lt;certificateReference&gt;</span></span>
<span data-ttu-id="01e0e-103">Especifica configurações que são usadas para encontrar e validar um certificado x. 509 em um repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="01e0e-103">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
 <span data-ttu-id="01e0e-104">\<IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="01e0e-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="01e0e-105">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="01e0e-105">\<federationConfiguration></span></span>  
<span data-ttu-id="01e0e-106">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="01e0e-106">\<serviceCertificate></span></span>  
<span data-ttu-id="01e0e-107">\<certificateReference ></span><span class="sxs-lookup"><span data-stu-id="01e0e-107">\<certificateReference></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01e0e-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="01e0e-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="01e0e-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="01e0e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="01e0e-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="01e0e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="01e0e-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="01e0e-111">Attributes</span></span>  
  
|<span data-ttu-id="01e0e-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="01e0e-112">Attribute</span></span>|<span data-ttu-id="01e0e-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="01e0e-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="01e0e-114">storeName</span><span class="sxs-lookup"><span data-stu-id="01e0e-114">storeName</span></span>|<span data-ttu-id="01e0e-115">O nome do repositório de certificados X.509.</span><span class="sxs-lookup"><span data-stu-id="01e0e-115">The name of the X.509 certificate store.</span></span> <span data-ttu-id="01e0e-116">O padrão é "My".</span><span class="sxs-lookup"><span data-stu-id="01e0e-116">The default is "My".</span></span> <span data-ttu-id="01e0e-117">Opcional.</span><span class="sxs-lookup"><span data-stu-id="01e0e-117">Optional.</span></span>|  
|<span data-ttu-id="01e0e-118">storeLocation</span><span class="sxs-lookup"><span data-stu-id="01e0e-118">storeLocation</span></span>|<span data-ttu-id="01e0e-119">Um <xref:System.Security.Cryptography.X509Certificates.StoreLocation> valor que especifica o local do repositório de certificados X.509.</span><span class="sxs-lookup"><span data-stu-id="01e0e-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="01e0e-120">O valor padrão é "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="01e0e-120">The default value is "LocalMachine".</span></span> <span data-ttu-id="01e0e-121">Opcional.</span><span class="sxs-lookup"><span data-stu-id="01e0e-121">Optional.</span></span>|  
|<span data-ttu-id="01e0e-122">x509FindType</span><span class="sxs-lookup"><span data-stu-id="01e0e-122">x509FindType</span></span>|<span data-ttu-id="01e0e-123">Um <xref:System.Security.Cryptography.X509Certificates.X509FindType> valor que especifica o tipo de pesquisa a ser executado.</span><span class="sxs-lookup"><span data-stu-id="01e0e-123">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="01e0e-124">O padrão é "FindBySubjectDistinguishedName".</span><span class="sxs-lookup"><span data-stu-id="01e0e-124">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="01e0e-125">Opcional.</span><span class="sxs-lookup"><span data-stu-id="01e0e-125">Optional.</span></span>|  
|<span data-ttu-id="01e0e-126">findValue</span><span class="sxs-lookup"><span data-stu-id="01e0e-126">findValue</span></span>|<span data-ttu-id="01e0e-127">O valor a ser pesquisado no repositório de certificados X.509.</span><span class="sxs-lookup"><span data-stu-id="01e0e-127">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="01e0e-128">Opcional.</span><span class="sxs-lookup"><span data-stu-id="01e0e-128">Optional.</span></span>|  
|<span data-ttu-id="01e0e-129">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="01e0e-129">isChainIncluded</span></span>|<span data-ttu-id="01e0e-130">Especifica se a validação deve ser executada usando a cadeia de certificados.</span><span class="sxs-lookup"><span data-stu-id="01e0e-130">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="01e0e-131">O padrão é "true"; validação é executada usando a cadeia de certificados.</span><span class="sxs-lookup"><span data-stu-id="01e0e-131">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="01e0e-132">Opcional.</span><span class="sxs-lookup"><span data-stu-id="01e0e-132">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="01e0e-133">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="01e0e-133">Child Elements</span></span>  
 <span data-ttu-id="01e0e-134">Nenhum</span><span class="sxs-lookup"><span data-stu-id="01e0e-134">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="01e0e-135">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="01e0e-135">Parent Elements</span></span>  
  
|<span data-ttu-id="01e0e-136">Elemento</span><span class="sxs-lookup"><span data-stu-id="01e0e-136">Element</span></span>|<span data-ttu-id="01e0e-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="01e0e-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="01e0e-138">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="01e0e-138">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|<span data-ttu-id="01e0e-139">Configura o certificado que é usado para criptografar e descriptografar tokens.</span><span class="sxs-lookup"><span data-stu-id="01e0e-139">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01e0e-140">Comentários</span><span class="sxs-lookup"><span data-stu-id="01e0e-140">Remarks</span></span>  
 <span data-ttu-id="01e0e-141">O `<certificateReference>` elemento Especifica configurações que são usadas para encontrar e validar um certificado x. 509 em um repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="01e0e-141">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="01e0e-142">Quando ele é especificado como o elemento filho a `<serviceCertficate>` elemento, ele especifica as configurações de local e a verificação do certificado X.509 que é usado para criptografar e descriptografar tokens.</span><span class="sxs-lookup"><span data-stu-id="01e0e-142">When it is specified as the child element of the `<serviceCertficate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="01e0e-143">O `<certificateReference>` elemento é representado pelo <xref:System.ServiceModel.Configuration.CertificateReferenceElement> classe.</span><span class="sxs-lookup"><span data-stu-id="01e0e-143">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
