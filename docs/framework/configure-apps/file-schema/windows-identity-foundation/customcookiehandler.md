---
title: <customCookieHandler>
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: 752b1188fccb6f09cdcab6a50653abf26e8e2a53
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55288178"
---
# <a name="customcookiehandler"></a><span data-ttu-id="c6b22-101">\<customCookieHandler></span><span class="sxs-lookup"><span data-stu-id="c6b22-101">\<customCookieHandler></span></span>
<span data-ttu-id="c6b22-102">Define o tipo de manipulador de cookie personalizado.</span><span class="sxs-lookup"><span data-stu-id="c6b22-102">Sets the custom cookie handler type.</span></span> <span data-ttu-id="c6b22-103">Esse elemento pode estar presente apenas se o `mode` atributo do `<cookieHandler>` elemento é "Custom".</span><span class="sxs-lookup"><span data-stu-id="c6b22-103">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="c6b22-104">O tipo personalizado deve ser derivado de <xref:System.IdentityModel.Services.CookieHandler> classe.</span><span class="sxs-lookup"><span data-stu-id="c6b22-104">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="c6b22-105">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="c6b22-105">\<system.identityModel.services></span></span>  
<span data-ttu-id="c6b22-106">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="c6b22-106">\<federationConfiguration></span></span>  
<span data-ttu-id="c6b22-107">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="c6b22-107">\<cookieHandler></span></span>  
<span data-ttu-id="c6b22-108">\<customCookieHandler></span><span class="sxs-lookup"><span data-stu-id="c6b22-108">\<customCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6b22-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c6b22-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c6b22-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c6b22-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c6b22-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c6b22-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c6b22-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="c6b22-112">Attributes</span></span>  
  
|<span data-ttu-id="c6b22-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="c6b22-113">Attribute</span></span>|<span data-ttu-id="c6b22-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="c6b22-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c6b22-115">tipo</span><span class="sxs-lookup"><span data-stu-id="c6b22-115">type</span></span>|<span data-ttu-id="c6b22-116">Especifica um tipo personalizado que deriva de <xref:System.IdentityModel.Services.CookieHandler> classe.</span><span class="sxs-lookup"><span data-stu-id="c6b22-116">Specifies a custom type that derives from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span> <span data-ttu-id="c6b22-117">Para obter mais informações sobre como especificar o `type` atributo, consulte [referências de tipo personalizado](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="c6b22-117">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c6b22-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c6b22-118">Child Elements</span></span>  
 <span data-ttu-id="c6b22-119">Nenhum</span><span class="sxs-lookup"><span data-stu-id="c6b22-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c6b22-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c6b22-120">Parent Elements</span></span>  
  
|<span data-ttu-id="c6b22-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="c6b22-121">Element</span></span>|<span data-ttu-id="c6b22-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="c6b22-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6b22-123">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="c6b22-123">\<cookieHandler></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|<span data-ttu-id="c6b22-124">Configura a <xref:System.IdentityModel.Services.CookieHandler> que o <xref:System.IdentityModel.Services.SessionAuthenticationModule> usa para ler e gravar cookies.</span><span class="sxs-lookup"><span data-stu-id="c6b22-124">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6b22-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="c6b22-125">Remarks</span></span>  
 <span data-ttu-id="c6b22-126">Quando você especifica um manipulador de cookie personalizado definindo a `mode` atributo do `<cookieHandler>` elemento como "Custom", você deve especificar o tipo do manipulador de cookie personalizado, incluindo um `<customCookieHandler>` elemento filho que faz referência ao tipo de manipulador de cookie.</span><span class="sxs-lookup"><span data-stu-id="c6b22-126">When you specify a custom cookie handler by setting the `mode` attribute of the `<cookieHandler>` element to "Custom", you must specify the type of the custom cookie handler by including a `<customCookieHandler>` child element that references the cookie handler type.</span></span> <span data-ttu-id="c6b22-127">Esse elemento não pode ser especificado quando o `mode` atributo é definido como "Em bloco" ou "Padrão".</span><span class="sxs-lookup"><span data-stu-id="c6b22-127">This element cannot be specified when the `mode` attribute is set to "Chunked" or "Default".</span></span> <span data-ttu-id="c6b22-128">Manipuladores de cookie personalizado devem derivar do <xref:System.IdentityModel.Services.CookieHandler> classe.</span><span class="sxs-lookup"><span data-stu-id="c6b22-128">Custom cookie handlers must derive from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="c6b22-129">O `<customCookieHandler>` elemento é representado pelo <xref:System.IdentityModel.Configuration.CustomTypeElement> classe.</span><span class="sxs-lookup"><span data-stu-id="c6b22-129">The `<customCookieHandler>` element is represented by the <xref:System.IdentityModel.Configuration.CustomTypeElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6b22-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c6b22-130">Example</span></span>  
 <span data-ttu-id="c6b22-131">O exemplo a seguir configura o SAM para usar um manipulador de cookie personalizado do tipo `MyNamespace.MyCustomCookieHandler`.</span><span class="sxs-lookup"><span data-stu-id="c6b22-131">The following example configures the SAM to use a custom cookie handler of type `MyNamespace.MyCustomCookieHandler`.</span></span>  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c6b22-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c6b22-132">See also</span></span>
- <xref:System.IdentityModel.Services.CookieHandler>
