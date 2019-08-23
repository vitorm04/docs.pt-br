---
title: <certificateValidator>
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: c25f183679f41f51ffee4f482bfe7a64763647d9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941898"
---
# <a name="certificatevalidator"></a><span data-ttu-id="3860a-101">\<certificateValidator></span><span class="sxs-lookup"><span data-stu-id="3860a-101">\<certificateValidator></span></span>
<span data-ttu-id="3860a-102">Especifica um tipo personalizado para validação de certificado.</span><span class="sxs-lookup"><span data-stu-id="3860a-102">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="3860a-103">Esse tipo será usado somente se o `certificateValidationMode` atributo [ \<](certificatevalidation.md) do elemento de > CertificateValidation for definido como "Custom".</span><span class="sxs-lookup"><span data-stu-id="3860a-103">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>  
  
 <span data-ttu-id="3860a-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="3860a-104">\<system.identityModel></span></span>  
<span data-ttu-id="3860a-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="3860a-105">\<identityConfiguration></span></span>  
<span data-ttu-id="3860a-106">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="3860a-106">\<certificateValidation></span></span>  
<span data-ttu-id="3860a-107">\<certificateValidator></span><span class="sxs-lookup"><span data-stu-id="3860a-107">\<certificateValidator></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3860a-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3860a-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3860a-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3860a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3860a-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3860a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3860a-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="3860a-111">Attributes</span></span>  
  
|<span data-ttu-id="3860a-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="3860a-112">Attribute</span></span>|<span data-ttu-id="3860a-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="3860a-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3860a-114">tipo</span><span class="sxs-lookup"><span data-stu-id="3860a-114">type</span></span>|<span data-ttu-id="3860a-115">Especifica um tipo personalizado que deriva da <xref:System.IdentityModel.Selectors.X509CertificateValidator> classe.</span><span class="sxs-lookup"><span data-stu-id="3860a-115">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="3860a-116">Defina o `certificateValidationMode` atributo [ \<](certificatevalidation.md) do elemento de > CertificateValidation como "Custom" para usar esse tipo.</span><span class="sxs-lookup"><span data-stu-id="3860a-116">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="3860a-117">Para obter mais informações sobre como especificar o `type` atributo, consulte [referências de tipo personalizado](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="3860a-117">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="3860a-118">Opcional.</span><span class="sxs-lookup"><span data-stu-id="3860a-118">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3860a-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3860a-119">Child Elements</span></span>  
 <span data-ttu-id="3860a-120">Nenhum</span><span class="sxs-lookup"><span data-stu-id="3860a-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3860a-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3860a-121">Parent Elements</span></span>  
  
|<span data-ttu-id="3860a-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="3860a-122">Element</span></span>|<span data-ttu-id="3860a-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="3860a-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3860a-124">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="3860a-124">\<certificateValidation></span></span>](certificatevalidation.md)|<span data-ttu-id="3860a-125">Controla as configurações que os manipuladores de token usam para validar certificados.</span><span class="sxs-lookup"><span data-stu-id="3860a-125">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3860a-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3860a-126">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />    
</certificateValidation>        
```
