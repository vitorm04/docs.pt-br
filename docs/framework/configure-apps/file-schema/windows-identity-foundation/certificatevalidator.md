---
title: <certificateValidator>
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: 30f81dd5948a7d366c1116cffd347c85a396f5ae
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252120"
---
# <a name="certificatevalidator"></a><span data-ttu-id="22ef4-101">\<certificateValidator></span><span class="sxs-lookup"><span data-stu-id="22ef4-101">\<certificateValidator></span></span>
<span data-ttu-id="22ef4-102">Especifica um tipo personalizado para validação de certificado.</span><span class="sxs-lookup"><span data-stu-id="22ef4-102">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="22ef4-103">Esse tipo será usado somente se o `certificateValidationMode` atributo [ \<](certificatevalidation.md) do elemento de > CertificateValidation for definido como "Custom".</span><span class="sxs-lookup"><span data-stu-id="22ef4-103">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>  
  
<span data-ttu-id="22ef4-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="22ef4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="22ef4-105">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="22ef4-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="22ef4-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> identityConfiguration**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="22ef4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="22ef4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> certificateValidation**](certificatevalidation.md)</span><span class="sxs-lookup"><span data-stu-id="22ef4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<certificateValidation>**](certificatevalidation.md)</span></span>\
<span data-ttu-id="22ef4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> certificateValidator**</span><span class="sxs-lookup"><span data-stu-id="22ef4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidator>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22ef4-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="22ef4-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="22ef4-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="22ef4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="22ef4-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="22ef4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="22ef4-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="22ef4-112">Attributes</span></span>  
  
|<span data-ttu-id="22ef4-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="22ef4-113">Attribute</span></span>|<span data-ttu-id="22ef4-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="22ef4-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="22ef4-115">tipo</span><span class="sxs-lookup"><span data-stu-id="22ef4-115">type</span></span>|<span data-ttu-id="22ef4-116">Especifica um tipo personalizado que deriva da <xref:System.IdentityModel.Selectors.X509CertificateValidator> classe.</span><span class="sxs-lookup"><span data-stu-id="22ef4-116">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="22ef4-117">Defina o `certificateValidationMode` atributo [ \<](certificatevalidation.md) do elemento de > CertificateValidation como "Custom" para usar esse tipo.</span><span class="sxs-lookup"><span data-stu-id="22ef4-117">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="22ef4-118">Para obter mais informações sobre como especificar o `type` atributo, consulte [referências de tipo personalizado](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="22ef4-118">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="22ef4-119">Opcional.</span><span class="sxs-lookup"><span data-stu-id="22ef4-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="22ef4-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="22ef4-120">Child Elements</span></span>  
 <span data-ttu-id="22ef4-121">Nenhum</span><span class="sxs-lookup"><span data-stu-id="22ef4-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="22ef4-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="22ef4-122">Parent Elements</span></span>  
  
|<span data-ttu-id="22ef4-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="22ef4-123">Element</span></span>|<span data-ttu-id="22ef4-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="22ef4-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="22ef4-125">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="22ef4-125">\<certificateValidation></span></span>](certificatevalidation.md)|<span data-ttu-id="22ef4-126">Controla as configurações que os manipuladores de token usam para validar certificados.</span><span class="sxs-lookup"><span data-stu-id="22ef4-126">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="22ef4-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="22ef4-127">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />    
</certificateValidation>        
```
