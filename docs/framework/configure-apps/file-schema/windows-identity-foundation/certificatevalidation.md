---
title: '&lt;certificateValidation&gt;'
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: 29881be43f02d275ad135efd97dc8b25a7409beb
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47235449"
---
# <a name="ltcertificatevalidationgt"></a><span data-ttu-id="28400-102">&lt;certificateValidation&gt;</span><span class="sxs-lookup"><span data-stu-id="28400-102">&lt;certificateValidation&gt;</span></span>
<span data-ttu-id="28400-103">Controla as configurações que manipuladores de token usam para validar certificados.</span><span class="sxs-lookup"><span data-stu-id="28400-103">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="28400-104">Essas configurações são substituídas se um manipulador específico é configurado com seu próprio validador.</span><span class="sxs-lookup"><span data-stu-id="28400-104">These settings are overridden if a specific handler is configured with its own validator.</span></span>  
  
 <span data-ttu-id="28400-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="28400-105">\<system.identityModel></span></span>  
<span data-ttu-id="28400-106">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="28400-106">\<identityConfiguration></span></span>  
<span data-ttu-id="28400-107">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="28400-107">\<certificateValidation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28400-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="28400-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="28400-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="28400-109">Attributes and Elements</span></span>  
 <span data-ttu-id="28400-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="28400-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="28400-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="28400-111">Attributes</span></span>  
  
|<span data-ttu-id="28400-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="28400-112">Attribute</span></span>|<span data-ttu-id="28400-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="28400-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="28400-114">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="28400-114">certificateValidationMode</span></span>|<span data-ttu-id="28400-115">Um <xref:System.ServiceModel.Security.X509CertificateValidationMode> valor que especifica o modo de validação a ser usado para o certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="28400-115">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="28400-116">O valor padrão é "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="28400-116">The default value is "PeerOrChainTrust".</span></span> <span data-ttu-id="28400-117">Para especificar um validador personalizado, defina esse atributo como "Custom" e especifique o validador usando o [ \<certificateValidator >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="28400-117">To specify a custom validator, set this attribute to "Custom" and specify the validator using the [\<certificateValidator>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md) element.</span></span> <span data-ttu-id="28400-118">Opcional.</span><span class="sxs-lookup"><span data-stu-id="28400-118">Optional.</span></span>|  
|<span data-ttu-id="28400-119">revocationMode</span><span class="sxs-lookup"><span data-stu-id="28400-119">revocationMode</span></span>|<span data-ttu-id="28400-120">Um <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> valor que especifica o modo de revogação para usar o certificado x. 509.</span><span class="sxs-lookup"><span data-stu-id="28400-120">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="28400-121">O valor padrão é "Online".</span><span class="sxs-lookup"><span data-stu-id="28400-121">The default value is "Online".</span></span> <span data-ttu-id="28400-122">Opcional.</span><span class="sxs-lookup"><span data-stu-id="28400-122">Optional.</span></span>|  
|<span data-ttu-id="28400-123">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="28400-123">trustedStoreLocation</span></span>|<span data-ttu-id="28400-124">Um <xref:System.Security.Cryptography.X509Certificates.StoreLocation> valor que especifica o repositório de certificados x. 509.</span><span class="sxs-lookup"><span data-stu-id="28400-124">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="28400-125">O valor padrão é "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="28400-125">The default value is "LocalMachine".</span></span> <span data-ttu-id="28400-126">Opcional.</span><span class="sxs-lookup"><span data-stu-id="28400-126">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="28400-127">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="28400-127">Child Elements</span></span>  
  
|<span data-ttu-id="28400-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="28400-128">Element</span></span>|<span data-ttu-id="28400-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="28400-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="28400-130">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="28400-130">\<certificateValidator></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md)|<span data-ttu-id="28400-131">Especifica um tipo personalizado para validação de certificado.</span><span class="sxs-lookup"><span data-stu-id="28400-131">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="28400-132">Esse tipo é usado somente se o `certificateValidationMode` atributo o [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) elemento for definido como "Custom".</span><span class="sxs-lookup"><span data-stu-id="28400-132">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element is set to "Custom".</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="28400-133">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="28400-133">Parent Elements</span></span>  
  
|<span data-ttu-id="28400-134">Elemento</span><span class="sxs-lookup"><span data-stu-id="28400-134">Element</span></span>|<span data-ttu-id="28400-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="28400-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="28400-136">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="28400-136">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="28400-137">Especifica as configurações de identidade de nível de serviço.</span><span class="sxs-lookup"><span data-stu-id="28400-137">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="28400-138">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="28400-138">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="28400-139">Fornece manipuladores de token de configuração para uma coleção de segurança.</span><span class="sxs-lookup"><span data-stu-id="28400-139">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28400-140">Comentários</span><span class="sxs-lookup"><span data-stu-id="28400-140">Remarks</span></span>  
 <span data-ttu-id="28400-141">Um `<certificateValidation>` elemento pode ser especificado no nível de serviço sob o `<identityConfiguration>` elemento ou em nível de conjunto de manipulador de token de segurança sob o `<securityTokenHandlerConfiguration>` elemento.</span><span class="sxs-lookup"><span data-stu-id="28400-141">A `<certificateValidation>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="28400-142">As configurações em uma coleção de manipulador de token substituem aquelas especificadas no serviço.</span><span class="sxs-lookup"><span data-stu-id="28400-142">Settings on a token handler collection override those specified on the service.</span></span> <span data-ttu-id="28400-143">Alguns manipuladores de token permitem que você especifique configurações de validação de certificado na configuração.</span><span class="sxs-lookup"><span data-stu-id="28400-143">Some token handlers allow you to specify certificate validation settings in configuration.</span></span> <span data-ttu-id="28400-144">Configurações em manipuladores de token individuais substituem aqueles especificados no nível de serviço e na coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="28400-144">Settings on individual token handlers override those specified both at the service level and on the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28400-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="28400-145">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
