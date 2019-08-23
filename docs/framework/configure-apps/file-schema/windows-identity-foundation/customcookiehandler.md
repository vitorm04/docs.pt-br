---
title: <customCookieHandler>
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: ebf1f7f3de1b44dba63977bf524dea9af2690fb1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942790"
---
# <a name="customcookiehandler"></a><span data-ttu-id="3e0a6-101">\<customCookieHandler></span><span class="sxs-lookup"><span data-stu-id="3e0a6-101">\<customCookieHandler></span></span>
<span data-ttu-id="3e0a6-102">Define o tipo de manipulador de cookies personalizado.</span><span class="sxs-lookup"><span data-stu-id="3e0a6-102">Sets the custom cookie handler type.</span></span> <span data-ttu-id="3e0a6-103">Esse elemento só poderá estar presente se o `mode` atributo `<cookieHandler>` do elemento for "Custom".</span><span class="sxs-lookup"><span data-stu-id="3e0a6-103">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="3e0a6-104">O tipo personalizado deve ser derivado da <xref:System.IdentityModel.Services.CookieHandler> classe.</span><span class="sxs-lookup"><span data-stu-id="3e0a6-104">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="3e0a6-105">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="3e0a6-105">\<system.identityModel.services></span></span>  
<span data-ttu-id="3e0a6-106">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="3e0a6-106">\<federationConfiguration></span></span>  
<span data-ttu-id="3e0a6-107">\<> cookieHandler</span><span class="sxs-lookup"><span data-stu-id="3e0a6-107">\<cookieHandler></span></span>  
<span data-ttu-id="3e0a6-108">\<customCookieHandler></span><span class="sxs-lookup"><span data-stu-id="3e0a6-108">\<customCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e0a6-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3e0a6-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e0a6-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3e0a6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3e0a6-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3e0a6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e0a6-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="3e0a6-112">Attributes</span></span>  
  
|<span data-ttu-id="3e0a6-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="3e0a6-113">Attribute</span></span>|<span data-ttu-id="3e0a6-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="3e0a6-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3e0a6-115">tipo</span><span class="sxs-lookup"><span data-stu-id="3e0a6-115">type</span></span>|<span data-ttu-id="3e0a6-116">Especifica um tipo personalizado que deriva da <xref:System.IdentityModel.Services.CookieHandler> classe.</span><span class="sxs-lookup"><span data-stu-id="3e0a6-116">Specifies a custom type that derives from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span> <span data-ttu-id="3e0a6-117">Para obter mais informações sobre como especificar o `type` atributo, consulte [referências de tipo personalizado](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="3e0a6-117">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3e0a6-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3e0a6-118">Child Elements</span></span>  
 <span data-ttu-id="3e0a6-119">Nenhum</span><span class="sxs-lookup"><span data-stu-id="3e0a6-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3e0a6-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3e0a6-120">Parent Elements</span></span>  
  
|<span data-ttu-id="3e0a6-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="3e0a6-121">Element</span></span>|<span data-ttu-id="3e0a6-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="3e0a6-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3e0a6-123">\<> cookieHandler</span><span class="sxs-lookup"><span data-stu-id="3e0a6-123">\<cookieHandler></span></span>](cookiehandler.md)|<span data-ttu-id="3e0a6-124">Configura o <xref:System.IdentityModel.Services.CookieHandler> que o <xref:System.IdentityModel.Services.SessionAuthenticationModule> usa para ler e gravar cookies.</span><span class="sxs-lookup"><span data-stu-id="3e0a6-124">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e0a6-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="3e0a6-125">Remarks</span></span>  
 <span data-ttu-id="3e0a6-126">Quando você especifica um manipulador de cookie personalizado definindo o `mode` atributo `<cookieHandler>` do elemento como "Custom", você deve especificar o tipo do manipulador de cookie personalizado, incluindo um `<customCookieHandler>` elemento filho que faz referência ao tipo de manipulador de cookie.</span><span class="sxs-lookup"><span data-stu-id="3e0a6-126">When you specify a custom cookie handler by setting the `mode` attribute of the `<cookieHandler>` element to "Custom", you must specify the type of the custom cookie handler by including a `<customCookieHandler>` child element that references the cookie handler type.</span></span> <span data-ttu-id="3e0a6-127">Este elemento não pode ser especificado quando `mode` o atributo está definido como "em bloco" ou "padrão".</span><span class="sxs-lookup"><span data-stu-id="3e0a6-127">This element cannot be specified when the `mode` attribute is set to "Chunked" or "Default".</span></span> <span data-ttu-id="3e0a6-128">Os <xref:System.IdentityModel.Services.CookieHandler> manipuladores de cookie personalizados devem derivar da classe.</span><span class="sxs-lookup"><span data-stu-id="3e0a6-128">Custom cookie handlers must derive from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="3e0a6-129">O `<customCookieHandler>` elemento é representado <xref:System.IdentityModel.Configuration.CustomTypeElement> pela classe.</span><span class="sxs-lookup"><span data-stu-id="3e0a6-129">The `<customCookieHandler>` element is represented by the <xref:System.IdentityModel.Configuration.CustomTypeElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e0a6-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3e0a6-130">Example</span></span>  
 <span data-ttu-id="3e0a6-131">O exemplo a seguir configura o SAM para usar um manipulador de cookie personalizado do tipo `MyNamespace.MyCustomCookieHandler`.</span><span class="sxs-lookup"><span data-stu-id="3e0a6-131">The following example configures the SAM to use a custom cookie handler of type `MyNamespace.MyCustomCookieHandler`.</span></span>  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3e0a6-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e0a6-132">See also</span></span>

- <xref:System.IdentityModel.Services.CookieHandler>
