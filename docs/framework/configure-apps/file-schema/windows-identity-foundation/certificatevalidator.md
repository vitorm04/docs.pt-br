---
title: '&lt;certificateValidator&gt;'
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: 65b8aa6fa4422579ce0d1c5e33d3418ea051612a
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48849692"
---
# <a name="ltcertificatevalidatorgt"></a><span data-ttu-id="faadc-102">&lt;certificateValidator&gt;</span><span class="sxs-lookup"><span data-stu-id="faadc-102">&lt;certificateValidator&gt;</span></span>
<span data-ttu-id="faadc-103">Especifica um tipo personalizado para validação de certificado.</span><span class="sxs-lookup"><span data-stu-id="faadc-103">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="faadc-104">Esse tipo é usado somente se o `certificateValidationMode` atributo o [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) elemento for definido como "Custom".</span><span class="sxs-lookup"><span data-stu-id="faadc-104">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element is set to "Custom".</span></span>  
  
 <span data-ttu-id="faadc-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="faadc-105">\<system.identityModel></span></span>  
<span data-ttu-id="faadc-106">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="faadc-106">\<identityConfiguration></span></span>  
<span data-ttu-id="faadc-107">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="faadc-107">\<certificateValidation></span></span>  
<span data-ttu-id="faadc-108">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="faadc-108">\<certificateValidator></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="faadc-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="faadc-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <certificateValidation>  
      <certificateValidator type=xs:string>  
      </certificateValidator>  
    </certificateValidation>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="faadc-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="faadc-110">Attributes and Elements</span></span>  
 <span data-ttu-id="faadc-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="faadc-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="faadc-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="faadc-112">Attributes</span></span>  
  
|<span data-ttu-id="faadc-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="faadc-113">Attribute</span></span>|<span data-ttu-id="faadc-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="faadc-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="faadc-115">tipo</span><span class="sxs-lookup"><span data-stu-id="faadc-115">type</span></span>|<span data-ttu-id="faadc-116">Especifica um tipo personalizado que deriva de <xref:System.IdentityModel.Selectors.X509CertificateValidator> classe.</span><span class="sxs-lookup"><span data-stu-id="faadc-116">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="faadc-117">Defina a `certificateValidationMode` atributo do [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) elemento como "Custom" para usar esse tipo.</span><span class="sxs-lookup"><span data-stu-id="faadc-117">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="faadc-118">Para obter mais informações sobre como especificar o `type` atributo, consulte [referências de tipo personalizado](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="faadc-118">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="faadc-119">Opcional.</span><span class="sxs-lookup"><span data-stu-id="faadc-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="faadc-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="faadc-120">Child Elements</span></span>  
 <span data-ttu-id="faadc-121">Nenhum</span><span class="sxs-lookup"><span data-stu-id="faadc-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="faadc-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="faadc-122">Parent Elements</span></span>  
  
|<span data-ttu-id="faadc-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="faadc-123">Element</span></span>|<span data-ttu-id="faadc-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="faadc-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="faadc-125">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="faadc-125">\<certificateValidation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|<span data-ttu-id="faadc-126">Controla as configurações que manipuladores de token usam para validar certificados.</span><span class="sxs-lookup"><span data-stu-id="faadc-126">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="faadc-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="faadc-127">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />    
</certificateValidation>        
```
