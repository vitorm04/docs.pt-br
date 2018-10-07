---
title: '&lt;customCookieHandler&gt;'
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: 51ca91de5c77727f5f5506118461d19354f12c14
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48836414"
---
# <a name="ltcustomcookiehandlergt"></a><span data-ttu-id="d3653-102">&lt;customCookieHandler&gt;</span><span class="sxs-lookup"><span data-stu-id="d3653-102">&lt;customCookieHandler&gt;</span></span>
<span data-ttu-id="d3653-103">Define o tipo de manipulador de cookie personalizado.</span><span class="sxs-lookup"><span data-stu-id="d3653-103">Sets the custom cookie handler type.</span></span> <span data-ttu-id="d3653-104">Esse elemento pode estar presente apenas se o `mode` atributo do `<cookieHandler>` elemento é "Custom".</span><span class="sxs-lookup"><span data-stu-id="d3653-104">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="d3653-105">O tipo personalizado deve ser derivado de <xref:System.IdentityModel.Services.CookieHandler> classe.</span><span class="sxs-lookup"><span data-stu-id="d3653-105">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="d3653-106">\<IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="d3653-106">\<system.identityModel.services></span></span>  
<span data-ttu-id="d3653-107">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="d3653-107">\<federationConfiguration></span></span>  
<span data-ttu-id="d3653-108">\<cookieHandler ></span><span class="sxs-lookup"><span data-stu-id="d3653-108">\<cookieHandler></span></span>  
<span data-ttu-id="d3653-109">\<customCookieHandler ></span><span class="sxs-lookup"><span data-stu-id="d3653-109">\<customCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3653-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d3653-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3653-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d3653-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d3653-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d3653-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3653-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="d3653-113">Attributes</span></span>  
  
|<span data-ttu-id="d3653-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="d3653-114">Attribute</span></span>|<span data-ttu-id="d3653-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="d3653-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d3653-116">tipo</span><span class="sxs-lookup"><span data-stu-id="d3653-116">type</span></span>|<span data-ttu-id="d3653-117">Especifica um tipo personalizado que deriva de <xref:System.IdentityModel.Services.CookieHandler> classe.</span><span class="sxs-lookup"><span data-stu-id="d3653-117">Specifies a custom type that derives from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span> <span data-ttu-id="d3653-118">Para obter mais informações sobre como especificar o `type` atributo, consulte [referências de tipo personalizado](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="d3653-118">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d3653-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d3653-119">Child Elements</span></span>  
 <span data-ttu-id="d3653-120">Nenhum</span><span class="sxs-lookup"><span data-stu-id="d3653-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d3653-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d3653-121">Parent Elements</span></span>  
  
|<span data-ttu-id="d3653-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="d3653-122">Element</span></span>|<span data-ttu-id="d3653-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="d3653-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d3653-124">\<cookieHandler ></span><span class="sxs-lookup"><span data-stu-id="d3653-124">\<cookieHandler></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|<span data-ttu-id="d3653-125">Configura a <xref:System.IdentityModel.Services.CookieHandler> que o <xref:System.IdentityModel.Services.SessionAuthenticationModule> usa para ler e gravar cookies.</span><span class="sxs-lookup"><span data-stu-id="d3653-125">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3653-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="d3653-126">Remarks</span></span>  
 <span data-ttu-id="d3653-127">Quando você especifica um manipulador de cookie personalizado definindo a `mode` atributo do `<cookieHandler>` elemento como "Custom", você deve especificar o tipo do manipulador de cookie personalizado, incluindo um `<customCookieHandler>` elemento filho que faz referência ao tipo de manipulador de cookie.</span><span class="sxs-lookup"><span data-stu-id="d3653-127">When you specify a custom cookie handler by setting the `mode` attribute of the `<cookieHandler>` element to "Custom", you must specify the type of the custom cookie handler by including a `<customCookieHandler>` child element that references the cookie handler type.</span></span> <span data-ttu-id="d3653-128">Esse elemento não pode ser especificado quando o `mode` atributo é definido como "Em bloco" ou "Padrão".</span><span class="sxs-lookup"><span data-stu-id="d3653-128">This element cannot be specified when the `mode` attribute is set to "Chunked" or "Default".</span></span> <span data-ttu-id="d3653-129">Manipuladores de cookie personalizado devem derivar do <xref:System.IdentityModel.Services.CookieHandler> classe.</span><span class="sxs-lookup"><span data-stu-id="d3653-129">Custom cookie handlers must derive from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="d3653-130">O `<customCookieHandler>` elemento é representado pelo <xref:System.IdentityModel.Configuration.CustomTypeElement> classe.</span><span class="sxs-lookup"><span data-stu-id="d3653-130">The `<customCookieHandler>` element is represented by the <xref:System.IdentityModel.Configuration.CustomTypeElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3653-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d3653-131">Example</span></span>  
 <span data-ttu-id="d3653-132">O exemplo a seguir configura o SAM para usar um manipulador de cookie personalizado do tipo `MyNamespace.MyCustomCookieHandler`.</span><span class="sxs-lookup"><span data-stu-id="d3653-132">The following example configures the SAM to use a custom cookie handler of type `MyNamespace.MyCustomCookieHandler`.</span></span>  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d3653-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d3653-133">See Also</span></span>  
 <xref:System.IdentityModel.Services.CookieHandler>
