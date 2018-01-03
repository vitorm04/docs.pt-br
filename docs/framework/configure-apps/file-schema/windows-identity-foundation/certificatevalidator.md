---
title: '&lt;certificateValidator&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 98112b3f13ff0b8e4be50f158ce40b048b213248
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcertificatevalidatorgt"></a><span data-ttu-id="d6307-102">&lt;certificateValidator&gt;</span><span class="sxs-lookup"><span data-stu-id="d6307-102">&lt;certificateValidator&gt;</span></span>
<span data-ttu-id="d6307-103">Especifica um tipo personalizado para validação de certificado.</span><span class="sxs-lookup"><span data-stu-id="d6307-103">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="d6307-104">Esse tipo é usado somente se o `certificateValidationMode` atributo o [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) é definido como "Custom".</span><span class="sxs-lookup"><span data-stu-id="d6307-104">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element is set to "Custom".</span></span>  
  
 <span data-ttu-id="d6307-105">\<System. IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="d6307-105">\<system.identityModel></span></span>  
<span data-ttu-id="d6307-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="d6307-106">\<identityConfiguration></span></span>  
<span data-ttu-id="d6307-107">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="d6307-107">\<certificateValidation></span></span>  
<span data-ttu-id="d6307-108">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="d6307-108">\<certificateValidator></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6307-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d6307-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d6307-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d6307-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d6307-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d6307-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d6307-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="d6307-112">Attributes</span></span>  
  
|<span data-ttu-id="d6307-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="d6307-113">Attribute</span></span>|<span data-ttu-id="d6307-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="d6307-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d6307-115">tipo</span><span class="sxs-lookup"><span data-stu-id="d6307-115">type</span></span>|<span data-ttu-id="d6307-116">Especifica um tipo personalizado que deriva de <xref:System.IdentityModel.Selectors.X509CertificateValidator> classe.</span><span class="sxs-lookup"><span data-stu-id="d6307-116">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="d6307-117">Definir o `certificateValidationMode` atributo do [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) "Custom" para usar esse tipo de elemento.</span><span class="sxs-lookup"><span data-stu-id="d6307-117">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="d6307-118">Para obter mais informações sobre como especificar o `type` de atributo, consulte [referências de tipo personalizado](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="d6307-118">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="d6307-119">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d6307-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d6307-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d6307-120">Child Elements</span></span>  
 <span data-ttu-id="d6307-121">Nenhum</span><span class="sxs-lookup"><span data-stu-id="d6307-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d6307-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d6307-122">Parent Elements</span></span>  
  
|<span data-ttu-id="d6307-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="d6307-123">Element</span></span>|<span data-ttu-id="d6307-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="d6307-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d6307-125">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="d6307-125">\<certificateValidation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|<span data-ttu-id="d6307-126">Controla as configurações que manipuladores de token usam para validar certificados.</span><span class="sxs-lookup"><span data-stu-id="d6307-126">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d6307-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d6307-127">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />    
</certificateValidation>        
```
