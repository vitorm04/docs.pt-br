---
title: <customCookieHandler>
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: a8ee23ac6facaea18cd7f1820616cb9b16afa336
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189845"
---
# \<customCookieHandler>

<span data-ttu-id="b59c1-101">Define o tipo de manipulador de cookies personalizado.</span><span class="sxs-lookup"><span data-stu-id="b59c1-101">Sets the custom cookie handler type.</span></span> <span data-ttu-id="b59c1-102">Esse elemento só poderá estar presente se o `mode` atributo do `<cookieHandler>` elemento for "Custom".</span><span class="sxs-lookup"><span data-stu-id="b59c1-102">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="b59c1-103">O tipo personalizado deve ser derivado da <xref:System.IdentityModel.Services.CookieHandler> classe.</span><span class="sxs-lookup"><span data-stu-id="b59c1-103">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customCookieHandler>**  
  
## <a name="syntax"></a><span data-ttu-id="b59c1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b59c1-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b59c1-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b59c1-105">Attributes and Elements</span></span>  

 <span data-ttu-id="b59c1-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b59c1-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b59c1-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="b59c1-107">Attributes</span></span>  
  
|<span data-ttu-id="b59c1-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="b59c1-108">Attribute</span></span>|<span data-ttu-id="b59c1-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="b59c1-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b59c1-110">type</span><span class="sxs-lookup"><span data-stu-id="b59c1-110">type</span></span>|<span data-ttu-id="b59c1-111">Especifica um tipo personalizado que deriva da <xref:System.IdentityModel.Services.CookieHandler> classe.</span><span class="sxs-lookup"><span data-stu-id="b59c1-111">Specifies a custom type that derives from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span> <span data-ttu-id="b59c1-112">Para obter mais informações sobre como especificar o `type` atributo, consulte [referências de tipo personalizado](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="b59c1-112">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b59c1-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b59c1-113">Child Elements</span></span>  

 <span data-ttu-id="b59c1-114">Nenhum</span><span class="sxs-lookup"><span data-stu-id="b59c1-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b59c1-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b59c1-115">Parent Elements</span></span>  
  
|<span data-ttu-id="b59c1-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="b59c1-116">Element</span></span>|<span data-ttu-id="b59c1-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="b59c1-117">Description</span></span>|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|<span data-ttu-id="b59c1-118">Configura o <xref:System.IdentityModel.Services.CookieHandler> que o <xref:System.IdentityModel.Services.SessionAuthenticationModule> usa para ler e gravar cookies.</span><span class="sxs-lookup"><span data-stu-id="b59c1-118">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b59c1-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="b59c1-119">Remarks</span></span>  

 <span data-ttu-id="b59c1-120">Quando você especifica um manipulador de cookie personalizado definindo o `mode` atributo do `<cookieHandler>` elemento como "Custom", você deve especificar o tipo do manipulador de cookie personalizado, incluindo um `<customCookieHandler>` elemento filho que faz referência ao tipo de manipulador de cookie.</span><span class="sxs-lookup"><span data-stu-id="b59c1-120">When you specify a custom cookie handler by setting the `mode` attribute of the `<cookieHandler>` element to "Custom", you must specify the type of the custom cookie handler by including a `<customCookieHandler>` child element that references the cookie handler type.</span></span> <span data-ttu-id="b59c1-121">Este elemento não pode ser especificado quando o `mode` atributo está definido como "em bloco" ou "padrão".</span><span class="sxs-lookup"><span data-stu-id="b59c1-121">This element cannot be specified when the `mode` attribute is set to "Chunked" or "Default".</span></span> <span data-ttu-id="b59c1-122">Os manipuladores de cookie personalizados devem derivar da <xref:System.IdentityModel.Services.CookieHandler> classe.</span><span class="sxs-lookup"><span data-stu-id="b59c1-122">Custom cookie handlers must derive from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="b59c1-123">O `<customCookieHandler>` elemento é representado pela <xref:System.IdentityModel.Configuration.CustomTypeElement> classe.</span><span class="sxs-lookup"><span data-stu-id="b59c1-123">The `<customCookieHandler>` element is represented by the <xref:System.IdentityModel.Configuration.CustomTypeElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b59c1-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b59c1-124">Example</span></span>  

 <span data-ttu-id="b59c1-125">O exemplo a seguir configura o SAM para usar um manipulador de cookie personalizado do tipo `MyNamespace.MyCustomCookieHandler` .</span><span class="sxs-lookup"><span data-stu-id="b59c1-125">The following example configures the SAM to use a custom cookie handler of type `MyNamespace.MyCustomCookieHandler`.</span></span>  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b59c1-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="b59c1-126">See also</span></span>

- <xref:System.IdentityModel.Services.CookieHandler>
