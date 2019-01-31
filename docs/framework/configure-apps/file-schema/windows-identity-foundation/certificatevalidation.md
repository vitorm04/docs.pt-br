---
title: <certificateValidation>
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: 7b8823d792e3f15846a9483d670994be4b368980
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55273891"
---
# <a name="certificatevalidation"></a><span data-ttu-id="9abbf-101">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="9abbf-101">\<certificateValidation></span></span>
<span data-ttu-id="9abbf-102">Controla as configurações que manipuladores de token usam para validar certificados.</span><span class="sxs-lookup"><span data-stu-id="9abbf-102">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="9abbf-103">Essas configurações são substituídas se um manipulador específico é configurado com seu próprio validador.</span><span class="sxs-lookup"><span data-stu-id="9abbf-103">These settings are overridden if a specific handler is configured with its own validator.</span></span>  
  
 <span data-ttu-id="9abbf-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="9abbf-104">\<system.identityModel></span></span>  
<span data-ttu-id="9abbf-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="9abbf-105">\<identityConfiguration></span></span>  
<span data-ttu-id="9abbf-106">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="9abbf-106">\<certificateValidation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9abbf-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9abbf-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9abbf-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9abbf-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9abbf-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9abbf-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9abbf-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="9abbf-110">Attributes</span></span>  
  
|<span data-ttu-id="9abbf-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="9abbf-111">Attribute</span></span>|<span data-ttu-id="9abbf-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="9abbf-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9abbf-113">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="9abbf-113">certificateValidationMode</span></span>|<span data-ttu-id="9abbf-114">Um <xref:System.ServiceModel.Security.X509CertificateValidationMode> valor que especifica o modo de validação a ser usado para o certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="9abbf-114">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="9abbf-115">O valor padrão é "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="9abbf-115">The default value is "PeerOrChainTrust".</span></span> <span data-ttu-id="9abbf-116">Para especificar um validador personalizado, defina esse atributo como "Custom" e especifique o validador usando o [ \<certificateValidator >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="9abbf-116">To specify a custom validator, set this attribute to "Custom" and specify the validator using the [\<certificateValidator>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md) element.</span></span> <span data-ttu-id="9abbf-117">Opcional.</span><span class="sxs-lookup"><span data-stu-id="9abbf-117">Optional.</span></span>|  
|<span data-ttu-id="9abbf-118">revocationMode</span><span class="sxs-lookup"><span data-stu-id="9abbf-118">revocationMode</span></span>|<span data-ttu-id="9abbf-119">Um <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> valor que especifica o modo de revogação para usar o certificado x. 509.</span><span class="sxs-lookup"><span data-stu-id="9abbf-119">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="9abbf-120">O valor padrão é "Online".</span><span class="sxs-lookup"><span data-stu-id="9abbf-120">The default value is "Online".</span></span> <span data-ttu-id="9abbf-121">Opcional.</span><span class="sxs-lookup"><span data-stu-id="9abbf-121">Optional.</span></span>|  
|<span data-ttu-id="9abbf-122">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="9abbf-122">trustedStoreLocation</span></span>|<span data-ttu-id="9abbf-123">Um <xref:System.Security.Cryptography.X509Certificates.StoreLocation> valor que especifica o repositório de certificados x. 509.</span><span class="sxs-lookup"><span data-stu-id="9abbf-123">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="9abbf-124">O valor padrão é "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="9abbf-124">The default value is "LocalMachine".</span></span> <span data-ttu-id="9abbf-125">Opcional.</span><span class="sxs-lookup"><span data-stu-id="9abbf-125">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9abbf-126">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9abbf-126">Child Elements</span></span>  
  
|<span data-ttu-id="9abbf-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="9abbf-127">Element</span></span>|<span data-ttu-id="9abbf-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="9abbf-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9abbf-129">\<certificateValidator></span><span class="sxs-lookup"><span data-stu-id="9abbf-129">\<certificateValidator></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md)|<span data-ttu-id="9abbf-130">Especifica um tipo personalizado para validação de certificado.</span><span class="sxs-lookup"><span data-stu-id="9abbf-130">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="9abbf-131">Esse tipo é usado somente se o `certificateValidationMode` atributo o [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) elemento for definido como "Custom".</span><span class="sxs-lookup"><span data-stu-id="9abbf-131">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element is set to "Custom".</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9abbf-132">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9abbf-132">Parent Elements</span></span>  
  
|<span data-ttu-id="9abbf-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="9abbf-133">Element</span></span>|<span data-ttu-id="9abbf-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="9abbf-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9abbf-135">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="9abbf-135">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="9abbf-136">Especifica as configurações de identidade de nível de serviço.</span><span class="sxs-lookup"><span data-stu-id="9abbf-136">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="9abbf-137">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="9abbf-137">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="9abbf-138">Fornece manipuladores de token de configuração para uma coleção de segurança.</span><span class="sxs-lookup"><span data-stu-id="9abbf-138">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9abbf-139">Comentários</span><span class="sxs-lookup"><span data-stu-id="9abbf-139">Remarks</span></span>  
 <span data-ttu-id="9abbf-140">Um `<certificateValidation>` elemento pode ser especificado no nível de serviço sob o `<identityConfiguration>` elemento ou em nível de conjunto de manipulador de token de segurança sob o `<securityTokenHandlerConfiguration>` elemento.</span><span class="sxs-lookup"><span data-stu-id="9abbf-140">A `<certificateValidation>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="9abbf-141">As configurações em uma coleção de manipulador de token substituem aquelas especificadas no serviço.</span><span class="sxs-lookup"><span data-stu-id="9abbf-141">Settings on a token handler collection override those specified on the service.</span></span> <span data-ttu-id="9abbf-142">Alguns manipuladores de token permitem que você especifique configurações de validação de certificado na configuração.</span><span class="sxs-lookup"><span data-stu-id="9abbf-142">Some token handlers allow you to specify certificate validation settings in configuration.</span></span> <span data-ttu-id="9abbf-143">Configurações em manipuladores de token individuais substituem aqueles especificados no nível de serviço e na coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="9abbf-143">Settings on individual token handlers override those specified both at the service level and on the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9abbf-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9abbf-144">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
