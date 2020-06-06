---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: 47d432a84d070476ddffd9b98a4ba46d8163bdc3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152808"
---
# \<certificateReference>
<span data-ttu-id="b8f6f-101">Especifica as configurações que são usadas para localizar e validar um certificado X. 509 em um repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="b8f6f-101">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateReference>**  
  
## <a name="syntax"></a><span data-ttu-id="b8f6f-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b8f6f-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8f6f-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b8f6f-103">Attributes and Elements</span></span>  
 <span data-ttu-id="b8f6f-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b8f6f-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8f6f-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="b8f6f-105">Attributes</span></span>  
  
|<span data-ttu-id="b8f6f-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="b8f6f-106">Attribute</span></span>|<span data-ttu-id="b8f6f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b8f6f-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b8f6f-108">storeName</span><span class="sxs-lookup"><span data-stu-id="b8f6f-108">storeName</span></span>|<span data-ttu-id="b8f6f-109">O nome do repositório de certificados X.509.</span><span class="sxs-lookup"><span data-stu-id="b8f6f-109">The name of the X.509 certificate store.</span></span> <span data-ttu-id="b8f6f-110">O padrão é "My".</span><span class="sxs-lookup"><span data-stu-id="b8f6f-110">The default is "My".</span></span> <span data-ttu-id="b8f6f-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b8f6f-111">Optional.</span></span>|  
|<span data-ttu-id="b8f6f-112">storeLocation</span><span class="sxs-lookup"><span data-stu-id="b8f6f-112">storeLocation</span></span>|<span data-ttu-id="b8f6f-113">Um <xref:System.Security.Cryptography.X509Certificates.StoreLocation> valor que especifica o local do repositório de certificados X. 509.</span><span class="sxs-lookup"><span data-stu-id="b8f6f-113">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="b8f6f-114">O valor padrão é "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="b8f6f-114">The default value is "LocalMachine".</span></span> <span data-ttu-id="b8f6f-115">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b8f6f-115">Optional.</span></span>|  
|<span data-ttu-id="b8f6f-116">x509FindType</span><span class="sxs-lookup"><span data-stu-id="b8f6f-116">x509FindType</span></span>|<span data-ttu-id="b8f6f-117">Um <xref:System.Security.Cryptography.X509Certificates.X509FindType> valor que especifica o tipo de pesquisa que deve ser executada.</span><span class="sxs-lookup"><span data-stu-id="b8f6f-117">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="b8f6f-118">O padrão é "FindBySubjectDistinguishedName".</span><span class="sxs-lookup"><span data-stu-id="b8f6f-118">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="b8f6f-119">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b8f6f-119">Optional.</span></span>|  
|<span data-ttu-id="b8f6f-120">findValue</span><span class="sxs-lookup"><span data-stu-id="b8f6f-120">findValue</span></span>|<span data-ttu-id="b8f6f-121">O valor a ser pesquisado no repositório de certificados X.509.</span><span class="sxs-lookup"><span data-stu-id="b8f6f-121">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="b8f6f-122">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b8f6f-122">Optional.</span></span>|  
|<span data-ttu-id="b8f6f-123">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="b8f6f-123">isChainIncluded</span></span>|<span data-ttu-id="b8f6f-124">Especifica se a validação deve ser executada usando a cadeia de certificados.</span><span class="sxs-lookup"><span data-stu-id="b8f6f-124">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="b8f6f-125">O padrão é "true"; a validação é executada usando a cadeia de certificados.</span><span class="sxs-lookup"><span data-stu-id="b8f6f-125">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="b8f6f-126">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b8f6f-126">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b8f6f-127">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b8f6f-127">Child Elements</span></span>  
 <span data-ttu-id="b8f6f-128">Nenhum</span><span class="sxs-lookup"><span data-stu-id="b8f6f-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b8f6f-129">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b8f6f-129">Parent Elements</span></span>  
  
|<span data-ttu-id="b8f6f-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="b8f6f-130">Element</span></span>|<span data-ttu-id="b8f6f-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="b8f6f-131">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate.md)|<span data-ttu-id="b8f6f-132">Configura o certificado que é usado para criptografar e descriptografar tokens.</span><span class="sxs-lookup"><span data-stu-id="b8f6f-132">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8f6f-133">Comentários</span><span class="sxs-lookup"><span data-stu-id="b8f6f-133">Remarks</span></span>  
 <span data-ttu-id="b8f6f-134">O `<certificateReference>` elemento especifica as configurações que são usadas para localizar e validar um certificado X. 509 em um repositório de certificados.</span><span class="sxs-lookup"><span data-stu-id="b8f6f-134">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="b8f6f-135">Quando é especificado como o elemento filho do `<serviceCertificate>` elemento, ele especifica as configurações de localização e verificação do certificado X. 509 que é usado para criptografar e descriptografar tokens.</span><span class="sxs-lookup"><span data-stu-id="b8f6f-135">When it is specified as the child element of the `<serviceCertificate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="b8f6f-136">O `<certificateReference>` elemento é representado pela <xref:System.ServiceModel.Configuration.CertificateReferenceElement> classe.</span><span class="sxs-lookup"><span data-stu-id="b8f6f-136">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
