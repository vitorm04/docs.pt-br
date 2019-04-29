---
title: <certificateValidator>
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: df52212305e0865b8c03fdd49068cb7c7da4fa38
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667360"
---
# <a name="certificatevalidator"></a><span data-ttu-id="f5dc4-101">\<certificateValidator></span><span class="sxs-lookup"><span data-stu-id="f5dc4-101">\<certificateValidator></span></span>
<span data-ttu-id="f5dc4-102">Especifica um tipo personalizado para validação de certificado.</span><span class="sxs-lookup"><span data-stu-id="f5dc4-102">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="f5dc4-103">Esse tipo é usado somente se o `certificateValidationMode` atributo o [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) elemento for definido como "Custom".</span><span class="sxs-lookup"><span data-stu-id="f5dc4-103">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element is set to "Custom".</span></span>  
  
 <span data-ttu-id="f5dc4-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="f5dc4-104">\<system.identityModel></span></span>  
<span data-ttu-id="f5dc4-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="f5dc4-105">\<identityConfiguration></span></span>  
<span data-ttu-id="f5dc4-106">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="f5dc4-106">\<certificateValidation></span></span>  
<span data-ttu-id="f5dc4-107">\<certificateValidator></span><span class="sxs-lookup"><span data-stu-id="f5dc4-107">\<certificateValidator></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5dc4-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f5dc4-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f5dc4-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f5dc4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f5dc4-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f5dc4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f5dc4-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="f5dc4-111">Attributes</span></span>  
  
|<span data-ttu-id="f5dc4-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="f5dc4-112">Attribute</span></span>|<span data-ttu-id="f5dc4-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="f5dc4-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f5dc4-114">tipo</span><span class="sxs-lookup"><span data-stu-id="f5dc4-114">type</span></span>|<span data-ttu-id="f5dc4-115">Especifica um tipo personalizado que deriva de <xref:System.IdentityModel.Selectors.X509CertificateValidator> classe.</span><span class="sxs-lookup"><span data-stu-id="f5dc4-115">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="f5dc4-116">Defina a `certificateValidationMode` atributo do [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) elemento como "Custom" para usar esse tipo.</span><span class="sxs-lookup"><span data-stu-id="f5dc4-116">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="f5dc4-117">Para obter mais informações sobre como especificar o `type` atributo, consulte [referências de tipo personalizado](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="f5dc4-117">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="f5dc4-118">Opcional.</span><span class="sxs-lookup"><span data-stu-id="f5dc4-118">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f5dc4-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f5dc4-119">Child Elements</span></span>  
 <span data-ttu-id="f5dc4-120">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f5dc4-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f5dc4-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f5dc4-121">Parent Elements</span></span>  
  
|<span data-ttu-id="f5dc4-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="f5dc4-122">Element</span></span>|<span data-ttu-id="f5dc4-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="f5dc4-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f5dc4-124">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="f5dc4-124">\<certificateValidation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|<span data-ttu-id="f5dc4-125">Controla as configurações que manipuladores de token usam para validar certificados.</span><span class="sxs-lookup"><span data-stu-id="f5dc4-125">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f5dc4-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f5dc4-126">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />    
</certificateValidation>        
```
