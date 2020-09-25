---
title: <certificateValidator>
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: 8476600769b6099bb885566de4c908c78a2dbbda
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201363"
---
# \<certificateValidator>

<span data-ttu-id="c8457-101">Especifica um tipo personalizado para validação de certificado.</span><span class="sxs-lookup"><span data-stu-id="c8457-101">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="c8457-102">Esse tipo será usado somente se o `certificateValidationMode` atributo do [\<certificateValidation>](certificatevalidation.md) elemento estiver definido como "personalizado".</span><span class="sxs-lookup"><span data-stu-id="c8457-102">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<certificateValidation>**](certificatevalidation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidator>**  
  
## <a name="syntax"></a><span data-ttu-id="c8457-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c8457-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c8457-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c8457-104">Attributes and Elements</span></span>  

 <span data-ttu-id="c8457-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c8457-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c8457-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="c8457-106">Attributes</span></span>  
  
|<span data-ttu-id="c8457-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="c8457-107">Attribute</span></span>|<span data-ttu-id="c8457-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="c8457-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c8457-109">type</span><span class="sxs-lookup"><span data-stu-id="c8457-109">type</span></span>|<span data-ttu-id="c8457-110">Especifica um tipo personalizado que deriva da <xref:System.IdentityModel.Selectors.X509CertificateValidator> classe.</span><span class="sxs-lookup"><span data-stu-id="c8457-110">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="c8457-111">Defina o `certificateValidationMode` atributo do [\<certificateValidation>](certificatevalidation.md) elemento como "Custom" para usar esse tipo.</span><span class="sxs-lookup"><span data-stu-id="c8457-111">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="c8457-112">Para obter mais informações sobre como especificar o `type` atributo, consulte [referências de tipo personalizado](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="c8457-112">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="c8457-113">Opcional.</span><span class="sxs-lookup"><span data-stu-id="c8457-113">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c8457-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c8457-114">Child Elements</span></span>  

 <span data-ttu-id="c8457-115">Nenhum</span><span class="sxs-lookup"><span data-stu-id="c8457-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c8457-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c8457-116">Parent Elements</span></span>  
  
|<span data-ttu-id="c8457-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="c8457-117">Element</span></span>|<span data-ttu-id="c8457-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="c8457-118">Description</span></span>|  
|-------------|-----------------|  
|[\<certificateValidation>](certificatevalidation.md)|<span data-ttu-id="c8457-119">Controla as configurações que os manipuladores de token usam para validar certificados.</span><span class="sxs-lookup"><span data-stu-id="c8457-119">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c8457-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c8457-120">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />
</certificateValidation>
```
