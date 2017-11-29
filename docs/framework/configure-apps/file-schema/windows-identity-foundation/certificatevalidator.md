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
ms.openlocfilehash: 74dd0827ee073d57c82729ec1e6a9a672aa1f404
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltcertificatevalidatorgt"></a><span data-ttu-id="7f25a-102">&lt;certificateValidator&gt;</span><span class="sxs-lookup"><span data-stu-id="7f25a-102">&lt;certificateValidator&gt;</span></span>
<span data-ttu-id="7f25a-103">Especifica um tipo personalizado para validação de certificado.</span><span class="sxs-lookup"><span data-stu-id="7f25a-103">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="7f25a-104">Esse tipo é usado somente se o `certificateValidationMode` atributo o [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) é definido como "Custom".</span><span class="sxs-lookup"><span data-stu-id="7f25a-104">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element is set to "Custom".</span></span>  
  
 <span data-ttu-id="7f25a-105">\<System. IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="7f25a-105">\<system.identityModel></span></span>  
<span data-ttu-id="7f25a-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="7f25a-106">\<identityConfiguration></span></span>  
<span data-ttu-id="7f25a-107">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="7f25a-107">\<certificateValidation></span></span>  
<span data-ttu-id="7f25a-108">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="7f25a-108">\<certificateValidator></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f25a-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7f25a-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f25a-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7f25a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7f25a-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7f25a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f25a-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="7f25a-112">Attributes</span></span>  
  
|<span data-ttu-id="7f25a-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="7f25a-113">Attribute</span></span>|<span data-ttu-id="7f25a-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="7f25a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7f25a-115">tipo</span><span class="sxs-lookup"><span data-stu-id="7f25a-115">type</span></span>|<span data-ttu-id="7f25a-116">Especifica um tipo personalizado que deriva de <xref:System.IdentityModel.Selectors.X509CertificateValidator> classe.</span><span class="sxs-lookup"><span data-stu-id="7f25a-116">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="7f25a-117">Definir o `certificateValidationMode` atributo do [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) "Custom" para usar esse tipo de elemento.</span><span class="sxs-lookup"><span data-stu-id="7f25a-117">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="7f25a-118">Para obter mais informações sobre como especificar o `type` de atributo, consulte [referências de tipo personalizado](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="7f25a-118">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="7f25a-119">Opcional.</span><span class="sxs-lookup"><span data-stu-id="7f25a-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7f25a-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7f25a-120">Child Elements</span></span>  
 <span data-ttu-id="7f25a-121">Nenhum</span><span class="sxs-lookup"><span data-stu-id="7f25a-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7f25a-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7f25a-122">Parent Elements</span></span>  
  
|<span data-ttu-id="7f25a-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="7f25a-123">Element</span></span>|<span data-ttu-id="7f25a-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="7f25a-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7f25a-125">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="7f25a-125">\<certificateValidation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|<span data-ttu-id="7f25a-126">Controla as configurações que manipuladores de token usam para validar certificados.</span><span class="sxs-lookup"><span data-stu-id="7f25a-126">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7f25a-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7f25a-127">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />    
</certificateValidation>        
```
