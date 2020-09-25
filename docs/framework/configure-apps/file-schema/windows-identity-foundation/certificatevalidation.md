---
title: <certificateValidation>
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: 583fef7eb364c39890b3f9304770b383c1ea6d2a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183501"
---
# \<certificateValidation>

<span data-ttu-id="de85e-101">Controla as configurações que os manipuladores de token usam para validar certificados.</span><span class="sxs-lookup"><span data-stu-id="de85e-101">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="de85e-102">Essas configurações serão substituídas se um manipulador específico estiver configurado com seu próprio validador.</span><span class="sxs-lookup"><span data-stu-id="de85e-102">These settings are overridden if a specific handler is configured with its own validator.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidation>**  
  
## <a name="syntax"></a><span data-ttu-id="de85e-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="de85e-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de85e-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="de85e-104">Attributes and Elements</span></span>  

 <span data-ttu-id="de85e-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="de85e-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de85e-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="de85e-106">Attributes</span></span>  
  
|<span data-ttu-id="de85e-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="de85e-107">Attribute</span></span>|<span data-ttu-id="de85e-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="de85e-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="de85e-109">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="de85e-109">certificateValidationMode</span></span>|<span data-ttu-id="de85e-110">Um <xref:System.ServiceModel.Security.X509CertificateValidationMode> valor que especifica o modo de validação a ser usado para o certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="de85e-110">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="de85e-111">O valor padrão é "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="de85e-111">The default value is "PeerOrChainTrust".</span></span> <span data-ttu-id="de85e-112">Para especificar um validador personalizado, defina esse atributo como "Custom" e especifique o validador usando o [\<certificateValidator>](certificatevalidator.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="de85e-112">To specify a custom validator, set this attribute to "Custom" and specify the validator using the [\<certificateValidator>](certificatevalidator.md) element.</span></span> <span data-ttu-id="de85e-113">Opcional.</span><span class="sxs-lookup"><span data-stu-id="de85e-113">Optional.</span></span>|  
|<span data-ttu-id="de85e-114">rerevocationmode</span><span class="sxs-lookup"><span data-stu-id="de85e-114">revocationMode</span></span>|<span data-ttu-id="de85e-115">Um <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> valor que especifica o modo de revogação a ser usado para o certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="de85e-115">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="de85e-116">O valor padrão é "online".</span><span class="sxs-lookup"><span data-stu-id="de85e-116">The default value is "Online".</span></span> <span data-ttu-id="de85e-117">Opcional.</span><span class="sxs-lookup"><span data-stu-id="de85e-117">Optional.</span></span>|  
|<span data-ttu-id="de85e-118">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="de85e-118">trustedStoreLocation</span></span>|<span data-ttu-id="de85e-119">Um <xref:System.Security.Cryptography.X509Certificates.StoreLocation> valor que especifica o repositório de certificados X. 509.</span><span class="sxs-lookup"><span data-stu-id="de85e-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="de85e-120">O valor padrão é "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="de85e-120">The default value is "LocalMachine".</span></span> <span data-ttu-id="de85e-121">Opcional.</span><span class="sxs-lookup"><span data-stu-id="de85e-121">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="de85e-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="de85e-122">Child Elements</span></span>  
  
|<span data-ttu-id="de85e-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="de85e-123">Element</span></span>|<span data-ttu-id="de85e-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="de85e-124">Description</span></span>|  
|-------------|-----------------|  
|[\<certificateValidator>](certificatevalidator.md)|<span data-ttu-id="de85e-125">Especifica um tipo personalizado para validação de certificado.</span><span class="sxs-lookup"><span data-stu-id="de85e-125">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="de85e-126">Esse tipo será usado somente se o `certificateValidationMode` atributo do [\<certificateValidation>](certificatevalidation.md) elemento estiver definido como "personalizado".</span><span class="sxs-lookup"><span data-stu-id="de85e-126">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="de85e-127">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="de85e-127">Parent Elements</span></span>  
  
|<span data-ttu-id="de85e-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="de85e-128">Element</span></span>|<span data-ttu-id="de85e-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="de85e-129">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="de85e-130">Especifica as configurações de identidade de nível de serviço.</span><span class="sxs-lookup"><span data-stu-id="de85e-130">Specifies service-level identity settings.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="de85e-131">Fornece a configuração para uma coleção de manipuladores de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="de85e-131">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de85e-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="de85e-132">Remarks</span></span>  

 <span data-ttu-id="de85e-133">Um `<certificateValidation>` elemento pode ser especificado no nível de serviço sob o `<identityConfiguration>` elemento ou no nível de coleção do manipulador de token de segurança sob o `<securityTokenHandlerConfiguration>` elemento.</span><span class="sxs-lookup"><span data-stu-id="de85e-133">A `<certificateValidation>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="de85e-134">As configurações em uma coleção de manipulador de tokens substituem aquelas especificadas no serviço.</span><span class="sxs-lookup"><span data-stu-id="de85e-134">Settings on a token handler collection override those specified on the service.</span></span> <span data-ttu-id="de85e-135">Alguns manipuladores de token permitem que você especifique as configurações de validação de certificado na configuração.</span><span class="sxs-lookup"><span data-stu-id="de85e-135">Some token handlers allow you to specify certificate validation settings in configuration.</span></span> <span data-ttu-id="de85e-136">As configurações em manipuladores de token individuais substituem aquelas especificadas no nível de serviço e na coleção do manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="de85e-136">Settings on individual token handlers override those specified both at the service level and on the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de85e-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="de85e-137">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
