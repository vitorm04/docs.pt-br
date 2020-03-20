---
title: <certificateValidator>
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: 3f3d79d3567c1714a79423b7767ce3f454b9d52d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152782"
---
# <a name="certificatevalidator"></a><span data-ttu-id="24a68-101">\<> do validador de certificados</span><span class="sxs-lookup"><span data-stu-id="24a68-101">\<certificateValidator></span></span>
<span data-ttu-id="24a68-102">Especifica um tipo personalizado para validação de certificado.</span><span class="sxs-lookup"><span data-stu-id="24a68-102">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="24a68-103">Esse tipo só é `certificateValidationMode` usado se o atributo do [ \<elemento validar>certificado](certificatevalidation.md) estiver definido como "Personalizado".</span><span class="sxs-lookup"><span data-stu-id="24a68-103">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>  
  
<span data-ttu-id="24a68-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="24a68-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="24a68-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="24a68-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="24a68-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de configuração de identidade**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="24a68-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="24a68-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de validação de certificados**](certificatevalidation.md)</span><span class="sxs-lookup"><span data-stu-id="24a68-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<certificateValidation>**](certificatevalidation.md)</span></span>\
<span data-ttu-id="24a68-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>do validador de certificados**</span><span class="sxs-lookup"><span data-stu-id="24a68-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidator>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24a68-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="24a68-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="24a68-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="24a68-110">Attributes and Elements</span></span>  
 <span data-ttu-id="24a68-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="24a68-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="24a68-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="24a68-112">Attributes</span></span>  
  
|<span data-ttu-id="24a68-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="24a68-113">Attribute</span></span>|<span data-ttu-id="24a68-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="24a68-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="24a68-115">type</span><span class="sxs-lookup"><span data-stu-id="24a68-115">type</span></span>|<span data-ttu-id="24a68-116">Especifica um tipo personalizado que <xref:System.IdentityModel.Selectors.X509CertificateValidator> deriva da classe.</span><span class="sxs-lookup"><span data-stu-id="24a68-116">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="24a68-117">Defina `certificateValidationMode` o atributo do [ \<certificadoValidação>](certificatevalidation.md) elemento como "Personalizado" para usar esse tipo.</span><span class="sxs-lookup"><span data-stu-id="24a68-117">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="24a68-118">Para obter mais informações `type` sobre como especificar o atributo, consulte [Referências de tipo personalizadas](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="24a68-118">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="24a68-119">Opcional.</span><span class="sxs-lookup"><span data-stu-id="24a68-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="24a68-120">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="24a68-120">Child Elements</span></span>  
 <span data-ttu-id="24a68-121">Nenhum</span><span class="sxs-lookup"><span data-stu-id="24a68-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="24a68-122">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="24a68-122">Parent Elements</span></span>  
  
|<span data-ttu-id="24a68-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="24a68-123">Element</span></span>|<span data-ttu-id="24a68-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="24a68-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="24a68-125">\<>de validação de certificados</span><span class="sxs-lookup"><span data-stu-id="24a68-125">\<certificateValidation></span></span>](certificatevalidation.md)|<span data-ttu-id="24a68-126">Controla as configurações que os manipuladores de tokens usam para validar certificados.</span><span class="sxs-lookup"><span data-stu-id="24a68-126">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="24a68-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="24a68-127">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />
</certificateValidation>
```
