---
title: Atributo mc:ProcessContent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: 2689b2c8-b4dc-4b71-b9bd-f95e619122d7
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1fe43e2450c35d976db7a188f854f7864f298afc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="mcprocesscontent-attribute"></a><span data-ttu-id="8a49b-102">Atributo mc:ProcessContent</span><span class="sxs-lookup"><span data-stu-id="8a49b-102">mc:ProcessContent Attribute</span></span>
<span data-ttu-id="8a49b-103">Especifica qual [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elementos ainda devem ter conteúdo processado pelos elementos pai relevantes, mesmo se o elemento pai imediato pode ser ignorado por um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processador devido à especificação de [mc: atributo ignorável](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md) .</span><span class="sxs-lookup"><span data-stu-id="8a49b-103">Specifies which [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] elements should still have content processed by relevant parent elements, even if the immediate parent element may be ignored by a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor due to specifying [mc:Ignorable Attribute](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md).</span></span> <span data-ttu-id="8a49b-104">O atributo `mc:ProcessContent` dá suporte à compatibilidade de marcação para o mapeamento de namespace personalizado e para controle de versão de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8a49b-104">The `mc:ProcessContent` attribute supports markup compatibility both for custom namespace mapping and for [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] versioning.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="8a49b-105">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="8a49b-105">XAML Attribute Usage</span></span>  
  
```  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...  
  mc:ProcessContent="ignorablePrefix:ThisElementCanBeIgnored"  
>  
    <ignorablePrefix:ThisElementCanBeIgnored>  
        [content]  
    </ignorablePrefix:ThisElementCanBeIgnored>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="8a49b-106">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="8a49b-106">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8a49b-107">*ignorablePrefix*</span><span class="sxs-lookup"><span data-stu-id="8a49b-107">*ignorablePrefix*</span></span>|<span data-ttu-id="8a49b-108">Qualquer cadeia de caracteres de prefixo é válida, conforme a especificação de XML 1.0.</span><span class="sxs-lookup"><span data-stu-id="8a49b-108">Any valid prefix string, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="8a49b-109">*ignorableUri*</span><span class="sxs-lookup"><span data-stu-id="8a49b-109">*ignorableUri*</span></span>|<span data-ttu-id="8a49b-110">Qualquer URI válido para designar um namespace, conforme a especificação XML 1.0.</span><span class="sxs-lookup"><span data-stu-id="8a49b-110">Any valid URI for designating a namespace, per the XML 1.0 specification.</span></span>|  
|<span data-ttu-id="8a49b-111">*ThisElementCanBeIgnored*</span><span class="sxs-lookup"><span data-stu-id="8a49b-111">*ThisElementCanBeIgnored*</span></span>|<span data-ttu-id="8a49b-112">Um elemento que poderá ser ignorado por implementações do processador [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], se o tipo subjacente não puder ser resolvido.</span><span class="sxs-lookup"><span data-stu-id="8a49b-112">An element that can be ignored by [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] processor implementations, if the underlying type cannot be resolved.</span></span>|  
|<span data-ttu-id="8a49b-113">*[conteúdo]*</span><span class="sxs-lookup"><span data-stu-id="8a49b-113">*[content]*</span></span>|<span data-ttu-id="8a49b-114">*ThisElementCanBeIgnored* está marcado como ignorável.</span><span class="sxs-lookup"><span data-stu-id="8a49b-114">*ThisElementCanBeIgnored* is marked ignorable.</span></span> <span data-ttu-id="8a49b-115">Se o processador ignora esse elemento, *[conteúdo]* é processado pelo *objeto*.</span><span class="sxs-lookup"><span data-stu-id="8a49b-115">If the processor ignores that element, *[content]* is processed by *object*.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a49b-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="8a49b-116">Remarks</span></span>  
 <span data-ttu-id="8a49b-117">Por padrão, um processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ignorará o conteúdo dentro de um elemento ignorado.</span><span class="sxs-lookup"><span data-stu-id="8a49b-117">By default, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will ignore content within an ignored element.</span></span> <span data-ttu-id="8a49b-118">Você pode especificar um elemento específico por `mc:ProcessContent`e um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processador continuará a processar o conteúdo dentro do elemento ignorado.</span><span class="sxs-lookup"><span data-stu-id="8a49b-118">You can specify a specific element by `mc:ProcessContent`, and a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processor will continue to process the content within the ignored element.</span></span> <span data-ttu-id="8a49b-119">Isso normalmente seria usado se o conteúdo é aninhado em várias marcas, pelo menos um dos quais é ignorado e pelo menos um dos quais não é ignorável.</span><span class="sxs-lookup"><span data-stu-id="8a49b-119">This would typically be used if the content is nested within several tags, at least one of which is ignorable and at least one of which is not ignorable.</span></span>  
  
 <span data-ttu-id="8a49b-120">Vários prefixos podem ser especificados no atributo, usando um separador de espaço, por exemplo: `mc:ProcessContent="ignore:Element1 ignore:Element2"`.</span><span class="sxs-lookup"><span data-stu-id="8a49b-120">Multiple prefixes may be specified in the attribute, using a space separator, for example: `mc:ProcessContent="ignore:Element1 ignore:Element2"`.</span></span>  
  
 <span data-ttu-id="8a49b-121">O namespace [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] define outros elementos e atributos que não estão documentados dentro desta área do [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8a49b-121">The [!INCLUDE[TLA#tla_mcxmlnsv1](../../../../includes/tlasharptla-mcxmlnsv1-md.md)] namespace defines other elements and attributes that are not documented within this area of the [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)].</span></span> <span data-ttu-id="8a49b-122">Para obter mais informações, consulte [Especificação de compatibilidade de marcação XML](http://go.microsoft.com/fwlink/?LinkId=73824).</span><span class="sxs-lookup"><span data-stu-id="8a49b-122">For more information, see [XML Markup Compatibility Specification](http://go.microsoft.com/fwlink/?LinkId=73824).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a49b-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8a49b-123">See Also</span></span>  
 [<span data-ttu-id="8a49b-124">Atributo mc:Ignorable</span><span class="sxs-lookup"><span data-stu-id="8a49b-124">mc:Ignorable Attribute</span></span>](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)  
 [<span data-ttu-id="8a49b-125">Visão geral de XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="8a49b-125">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
