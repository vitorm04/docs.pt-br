---
title: Estilos e modelos embutidos
ms.date: 03/30/2017
helpviewer_keywords:
- inline templates [WPF]
- styles [WPF], inline
- templates [WPF], inline
- inline styles [WPF]
ms.assetid: 69a1a3f9-acb5-4e2c-9c43-2e376c055ac4
ms.openlocfilehash: b566e157e2d4a9e9be21a678541bf5d5341a898c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59091428"
---
# <a name="inline-styles-and-templates"></a><span data-ttu-id="2a47a-102">Estilos e modelos embutidos</span><span class="sxs-lookup"><span data-stu-id="2a47a-102">Inline Styles and Templates</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="2a47a-103">Fornece <xref:System.Windows.Style> objetos e objetos de modelo (<xref:System.Windows.FrameworkTemplate> subclasses) como uma maneira de definir a aparência visual de um elemento em recursos, para que eles podem ser usados várias vezes.</span><span class="sxs-lookup"><span data-stu-id="2a47a-103">provides <xref:System.Windows.Style> objects and template objects (<xref:System.Windows.FrameworkTemplate> subclasses) as a way to define the visual appearance of an element in resources, so that they can be used multiple times.</span></span> <span data-ttu-id="2a47a-104">Por esse motivo, os atributos no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] que levam os tipos <xref:System.Windows.Style> e <xref:System.Windows.FrameworkTemplate> quase sempre fazem referências de recurso a estilos e modelos existentes em vez de definir novos embutidos.</span><span class="sxs-lookup"><span data-stu-id="2a47a-104">For this reason, attributes in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] that take the types <xref:System.Windows.Style> and <xref:System.Windows.FrameworkTemplate> almost always make resource references to existing styles and templates rather than define new ones inline.</span></span>  
  
## <a name="limitations-of-inline-styles-and-templates"></a><span data-ttu-id="2a47a-105">Limitações de estilos e modelos embutidos</span><span class="sxs-lookup"><span data-stu-id="2a47a-105">Limitations of Inline Styles and Templates</span></span>  
 <span data-ttu-id="2a47a-106">No [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], as propriedades de estilo e modelo podem ser definidas tecnicamente de uma de duas maneiras.</span><span class="sxs-lookup"><span data-stu-id="2a47a-106">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], style and template properties can technically be set in one of two ways.</span></span> <span data-ttu-id="2a47a-107">Você pode usar a sintaxe de atributo para fazer referência a um estilo que foi definido dentro de um recurso, por exemplo `<`*objeto*`Style="{StaticResource`*myResourceKey*`}" .../>`.</span><span class="sxs-lookup"><span data-stu-id="2a47a-107">You can use attribute syntax to reference a style that was defined within a resource, for example `<`*object*`Style="{StaticResource`*myResourceKey*`}" .../>`.</span></span> <span data-ttu-id="2a47a-108">Ou então, você pode usar a sintaxe de elemento da propriedade para definir um estilo embutido, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="2a47a-108">Or you can use property element syntax to define a style inline, for instance:</span></span>  
  
 <span data-ttu-id="2a47a-109">`<` *objeto* `>`</span><span class="sxs-lookup"><span data-stu-id="2a47a-109">`<` *object* `>`</span></span>  
  
 <span data-ttu-id="2a47a-110">`<` *objeto* `.Style>`</span><span class="sxs-lookup"><span data-stu-id="2a47a-110">`<` *object* `.Style>`</span></span>  
  
 <span data-ttu-id="2a47a-111">`<` `Style`  `.../>`</span><span class="sxs-lookup"><span data-stu-id="2a47a-111">`<` `Style`  `.../>`</span></span>  
  
 <span data-ttu-id="2a47a-112">`</` *objeto* `.Style>`</span><span class="sxs-lookup"><span data-stu-id="2a47a-112">`</` *object* `.Style>`</span></span>  
  
 <span data-ttu-id="2a47a-113">`</` *objeto* `>`</span><span class="sxs-lookup"><span data-stu-id="2a47a-113">`</` *object* `>`</span></span>  
  
 <span data-ttu-id="2a47a-114">É muito mais comum usar o atributo.</span><span class="sxs-lookup"><span data-stu-id="2a47a-114">The attribute usage is much more common.</span></span> <span data-ttu-id="2a47a-115">Um estilo que é definido embutido e não definido em recursos terá necessariamente escopos somente para o elemento que o contém, e não poderá ser reutilizado com tanta facilidade, pois não tem nenhuma chave de recurso.</span><span class="sxs-lookup"><span data-stu-id="2a47a-115">A style that is defined inline and not defined in resources is necessarily scoped to the containing element only, and cannot be re-used as easily because it has no resource key.</span></span> <span data-ttu-id="2a47a-116">Em geral, um estilo definido por recurso é mais versátil e útil, e está mais alinhado com o princípio de modelo de programação [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] geral de lógica de programa no código de design na marcação.</span><span class="sxs-lookup"><span data-stu-id="2a47a-116">In general a resource-defined style is more versatile and useful, and is more in keeping with the general [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] programming model principle of separating program logic in code from design in markup.</span></span>  
  
 <span data-ttu-id="2a47a-117">Geralmente não haverá nenhum motivo para definir um estilo ou modelo embutido, mesmo se você pretender usar esse estilo ou modelo nesse local.</span><span class="sxs-lookup"><span data-stu-id="2a47a-117">Usually there is no reason to set a style or template inline, even if you only intend to use that style or template in that location.</span></span> <span data-ttu-id="2a47a-118">A maioria dos elementos que podem assumir um estilo ou modelo também dão suporte a uma propriedade e um modelo de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="2a47a-118">Most elements that can take a style or template also support a content property and a content model.</span></span> <span data-ttu-id="2a47a-119">Se você estivesse usando uma árvore lógica criada por meio de estilos ou modelagem, seria ainda mais fácil preencher somente essa propriedade de conteúdo com os elementos filho equivalentes na marcação direta.</span><span class="sxs-lookup"><span data-stu-id="2a47a-119">If you are only using whatever logical tree you create through styling or templating once, it would be even easier to just fill that content property with the equivalent child elements in direct markup.</span></span> <span data-ttu-id="2a47a-120">Isso ignoraria totalmente os mecanismos de estilo e modelo.</span><span class="sxs-lookup"><span data-stu-id="2a47a-120">This would bypass the style and template mechanisms altogether.</span></span>  
  
 <span data-ttu-id="2a47a-121">Outras sintaxes habilitadas por extensões de marcação que retornam um objeto também são possíveis para os estilos e modelos.</span><span class="sxs-lookup"><span data-stu-id="2a47a-121">Other syntaxes enabled by markup extensions that return an object are also possible for styles and templates.</span></span> <span data-ttu-id="2a47a-122">Duas destas extensões têm possíveis cenários incluem [TemplateBinding](templatebinding-markup-extension.md) e <xref:System.Windows.Data.Binding>.</span><span class="sxs-lookup"><span data-stu-id="2a47a-122">Two such extensions that have possible scenarios include [TemplateBinding](templatebinding-markup-extension.md) and <xref:System.Windows.Data.Binding>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a47a-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a47a-123">See also</span></span>

- [<span data-ttu-id="2a47a-124">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="2a47a-124">Styling and Templating</span></span>](../controls/styling-and-templating.md)
