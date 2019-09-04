---
title: <customCookieHandler>
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: e1f32e17cf0da5e948d778e8b61aca6053eff4ef
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252012"
---
# <a name="customcookiehandler"></a><span data-ttu-id="e701d-101">\<customCookieHandler></span><span class="sxs-lookup"><span data-stu-id="e701d-101">\<customCookieHandler></span></span>
<span data-ttu-id="e701d-102">Define o tipo de manipulador de cookies personalizado.</span><span class="sxs-lookup"><span data-stu-id="e701d-102">Sets the custom cookie handler type.</span></span> <span data-ttu-id="e701d-103">Esse elemento só poderá estar presente se o `mode` atributo `<cookieHandler>` do elemento for "Custom".</span><span class="sxs-lookup"><span data-stu-id="e701d-103">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="e701d-104">O tipo personalizado deve ser derivado da <xref:System.IdentityModel.Services.CookieHandler> classe.</span><span class="sxs-lookup"><span data-stu-id="e701d-104">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
<span data-ttu-id="e701d-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e701d-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e701d-106">&nbsp;&nbsp;[ **\<System. identityModel. Services >** ](system-identitymodel-services.md)</span><span class="sxs-lookup"><span data-stu-id="e701d-106">&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)</span></span>\
<span data-ttu-id="e701d-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> federationConfiguration**](federationconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="e701d-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)</span></span>\
<span data-ttu-id="e701d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> cookieHandler**](cookiehandler.md)</span><span class="sxs-lookup"><span data-stu-id="e701d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)</span></span>\
<span data-ttu-id="e701d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> customCookieHandler**</span><span class="sxs-lookup"><span data-stu-id="e701d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customCookieHandler>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e701d-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e701d-110">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Custom">  
      <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" >  
      </customCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e701d-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e701d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e701d-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e701d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e701d-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="e701d-113">Attributes</span></span>  
  
|<span data-ttu-id="e701d-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="e701d-114">Attribute</span></span>|<span data-ttu-id="e701d-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="e701d-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e701d-116">tipo</span><span class="sxs-lookup"><span data-stu-id="e701d-116">type</span></span>|<span data-ttu-id="e701d-117">Especifica um tipo personalizado que deriva da <xref:System.IdentityModel.Services.CookieHandler> classe.</span><span class="sxs-lookup"><span data-stu-id="e701d-117">Specifies a custom type that derives from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span> <span data-ttu-id="e701d-118">Para obter mais informações sobre como especificar o `type` atributo, consulte [referências de tipo personalizado](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="e701d-118">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e701d-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e701d-119">Child Elements</span></span>  
 <span data-ttu-id="e701d-120">Nenhum</span><span class="sxs-lookup"><span data-stu-id="e701d-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e701d-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e701d-121">Parent Elements</span></span>  
  
|<span data-ttu-id="e701d-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="e701d-122">Element</span></span>|<span data-ttu-id="e701d-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="e701d-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e701d-124">\<> cookieHandler</span><span class="sxs-lookup"><span data-stu-id="e701d-124">\<cookieHandler></span></span>](cookiehandler.md)|<span data-ttu-id="e701d-125">Configura o <xref:System.IdentityModel.Services.CookieHandler> que o <xref:System.IdentityModel.Services.SessionAuthenticationModule> usa para ler e gravar cookies.</span><span class="sxs-lookup"><span data-stu-id="e701d-125">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e701d-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="e701d-126">Remarks</span></span>  
 <span data-ttu-id="e701d-127">Quando você especifica um manipulador de cookie personalizado definindo o `mode` atributo `<cookieHandler>` do elemento como "Custom", você deve especificar o tipo do manipulador de cookie personalizado, incluindo um `<customCookieHandler>` elemento filho que faz referência ao tipo de manipulador de cookie.</span><span class="sxs-lookup"><span data-stu-id="e701d-127">When you specify a custom cookie handler by setting the `mode` attribute of the `<cookieHandler>` element to "Custom", you must specify the type of the custom cookie handler by including a `<customCookieHandler>` child element that references the cookie handler type.</span></span> <span data-ttu-id="e701d-128">Este elemento não pode ser especificado quando `mode` o atributo está definido como "em bloco" ou "padrão".</span><span class="sxs-lookup"><span data-stu-id="e701d-128">This element cannot be specified when the `mode` attribute is set to "Chunked" or "Default".</span></span> <span data-ttu-id="e701d-129">Os <xref:System.IdentityModel.Services.CookieHandler> manipuladores de cookie personalizados devem derivar da classe.</span><span class="sxs-lookup"><span data-stu-id="e701d-129">Custom cookie handlers must derive from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="e701d-130">O `<customCookieHandler>` elemento é representado <xref:System.IdentityModel.Configuration.CustomTypeElement> pela classe.</span><span class="sxs-lookup"><span data-stu-id="e701d-130">The `<customCookieHandler>` element is represented by the <xref:System.IdentityModel.Configuration.CustomTypeElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e701d-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e701d-131">Example</span></span>  
 <span data-ttu-id="e701d-132">O exemplo a seguir configura o SAM para usar um manipulador de cookie personalizado do tipo `MyNamespace.MyCustomCookieHandler`.</span><span class="sxs-lookup"><span data-stu-id="e701d-132">The following example configures the SAM to use a custom cookie handler of type `MyNamespace.MyCustomCookieHandler`.</span></span>  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e701d-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e701d-133">See also</span></span>

- <xref:System.IdentityModel.Services.CookieHandler>
