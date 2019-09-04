---
title: <certificateValidation>
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: c2d1a5d36cb5616ef06eedc093dd70a68a164a81
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252130"
---
# <a name="certificatevalidation"></a><span data-ttu-id="81f36-101">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="81f36-101">\<certificateValidation></span></span>
<span data-ttu-id="81f36-102">Controla as configurações que os manipuladores de token usam para validar certificados.</span><span class="sxs-lookup"><span data-stu-id="81f36-102">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="81f36-103">Essas configurações serão substituídas se um manipulador específico estiver configurado com seu próprio validador.</span><span class="sxs-lookup"><span data-stu-id="81f36-103">These settings are overridden if a specific handler is configured with its own validator.</span></span>  
  
<span data-ttu-id="81f36-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="81f36-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="81f36-105">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="81f36-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="81f36-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> identityConfiguration**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="81f36-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="81f36-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> certificateValidation**</span><span class="sxs-lookup"><span data-stu-id="81f36-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidation>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81f36-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="81f36-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <certificateValidation  
      certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
      revocationMode="NoCheck||Offline||Online"  
      trustedStoreLocation="CurrentLocation||LocalMachine" >  
    </certificateValidation>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="81f36-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="81f36-109">Attributes and Elements</span></span>  
 <span data-ttu-id="81f36-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="81f36-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="81f36-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="81f36-111">Attributes</span></span>  
  
|<span data-ttu-id="81f36-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="81f36-112">Attribute</span></span>|<span data-ttu-id="81f36-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="81f36-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="81f36-114">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="81f36-114">certificateValidationMode</span></span>|<span data-ttu-id="81f36-115">Um <xref:System.ServiceModel.Security.X509CertificateValidationMode> valor que especifica o modo de validação a ser usado para o certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="81f36-115">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="81f36-116">O valor padrão é "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="81f36-116">The default value is "PeerOrChainTrust".</span></span> <span data-ttu-id="81f36-117">Para especificar um validador personalizado, defina esse atributo como "Custom" e especifique o validador usando o [ \<elemento certificateValidator >](certificatevalidator.md) .</span><span class="sxs-lookup"><span data-stu-id="81f36-117">To specify a custom validator, set this attribute to "Custom" and specify the validator using the [\<certificateValidator>](certificatevalidator.md) element.</span></span> <span data-ttu-id="81f36-118">Opcional.</span><span class="sxs-lookup"><span data-stu-id="81f36-118">Optional.</span></span>|  
|<span data-ttu-id="81f36-119">revocationMode</span><span class="sxs-lookup"><span data-stu-id="81f36-119">revocationMode</span></span>|<span data-ttu-id="81f36-120">Um <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> valor que especifica o modo de revogação a ser usado para o certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="81f36-120">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="81f36-121">O valor padrão é "online".</span><span class="sxs-lookup"><span data-stu-id="81f36-121">The default value is "Online".</span></span> <span data-ttu-id="81f36-122">Opcional.</span><span class="sxs-lookup"><span data-stu-id="81f36-122">Optional.</span></span>|  
|<span data-ttu-id="81f36-123">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="81f36-123">trustedStoreLocation</span></span>|<span data-ttu-id="81f36-124">Um <xref:System.Security.Cryptography.X509Certificates.StoreLocation> valor que especifica o repositório de certificados X. 509.</span><span class="sxs-lookup"><span data-stu-id="81f36-124">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="81f36-125">O valor padrão é "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="81f36-125">The default value is "LocalMachine".</span></span> <span data-ttu-id="81f36-126">Opcional.</span><span class="sxs-lookup"><span data-stu-id="81f36-126">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="81f36-127">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="81f36-127">Child Elements</span></span>  
  
|<span data-ttu-id="81f36-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="81f36-128">Element</span></span>|<span data-ttu-id="81f36-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="81f36-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="81f36-130">\<certificateValidator></span><span class="sxs-lookup"><span data-stu-id="81f36-130">\<certificateValidator></span></span>](certificatevalidator.md)|<span data-ttu-id="81f36-131">Especifica um tipo personalizado para validação de certificado.</span><span class="sxs-lookup"><span data-stu-id="81f36-131">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="81f36-132">Esse tipo será usado somente se o `certificateValidationMode` atributo [ \<](certificatevalidation.md) do elemento de > CertificateValidation for definido como "Custom".</span><span class="sxs-lookup"><span data-stu-id="81f36-132">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="81f36-133">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="81f36-133">Parent Elements</span></span>  
  
|<span data-ttu-id="81f36-134">Elemento</span><span class="sxs-lookup"><span data-stu-id="81f36-134">Element</span></span>|<span data-ttu-id="81f36-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="81f36-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="81f36-136">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="81f36-136">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="81f36-137">Especifica as configurações de identidade de nível de serviço.</span><span class="sxs-lookup"><span data-stu-id="81f36-137">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="81f36-138">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="81f36-138">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="81f36-139">Fornece a configuração para uma coleção de manipuladores de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="81f36-139">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81f36-140">Comentários</span><span class="sxs-lookup"><span data-stu-id="81f36-140">Remarks</span></span>  
 <span data-ttu-id="81f36-141">Um `<certificateValidation>` elemento pode ser especificado no nível de serviço sob o `<identityConfiguration>` elemento ou no nível de coleção do manipulador de token de `<securityTokenHandlerConfiguration>` segurança sob o elemento.</span><span class="sxs-lookup"><span data-stu-id="81f36-141">A `<certificateValidation>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="81f36-142">As configurações em uma coleção de manipulador de tokens substituem aquelas especificadas no serviço.</span><span class="sxs-lookup"><span data-stu-id="81f36-142">Settings on a token handler collection override those specified on the service.</span></span> <span data-ttu-id="81f36-143">Alguns manipuladores de token permitem que você especifique as configurações de validação de certificado na configuração.</span><span class="sxs-lookup"><span data-stu-id="81f36-143">Some token handlers allow you to specify certificate validation settings in configuration.</span></span> <span data-ttu-id="81f36-144">As configurações em manipuladores de token individuais substituem aquelas especificadas no nível de serviço e na coleção do manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="81f36-144">Settings on individual token handlers override those specified both at the service level and on the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81f36-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="81f36-145">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
