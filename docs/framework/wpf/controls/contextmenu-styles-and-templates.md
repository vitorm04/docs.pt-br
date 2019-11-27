---
title: Estilos e modelos ContextMenu
ms.date: 03/30/2017
helpviewer_keywords:
- templates [WPF], ContextMenu
- parts [WPF], ContextMenu
- ContextMenu [WPF], styles and templates
- styles [WPF], ContextMenu
- ControlTemplate [WPF], ContextMenu
- states [WPF], ContextMenu
ms.assetid: 342d1f17-c406-4f94-8f55-867c5f3ea511
ms.openlocfilehash: fa192e20ea84e96c9f85ff84e16c63b7f56c8a98
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283545"
---
# <a name="contextmenu-styles-and-templates"></a><span data-ttu-id="042eb-102">Estilos e modelos ContextMenu</span><span class="sxs-lookup"><span data-stu-id="042eb-102">ContextMenu Styles and Templates</span></span>
<span data-ttu-id="042eb-103">Este tópico descreve os estilos e modelos para o controle de <xref:System.Windows.Controls.ContextMenu>.</span><span class="sxs-lookup"><span data-stu-id="042eb-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ContextMenu> control.</span></span> <span data-ttu-id="042eb-104">Você pode modificar o <xref:System.Windows.Controls.ControlTemplate> padrão para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="042eb-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="042eb-105">Para obter mais informações, consulte [criar um modelo para um controle](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="042eb-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="contextmenu-parts"></a><span data-ttu-id="042eb-106">Partes de ContextMenu</span><span class="sxs-lookup"><span data-stu-id="042eb-106">ContextMenu Parts</span></span>  
 <span data-ttu-id="042eb-107">O controle de <xref:System.Windows.Controls.ContextMenu> não tem nenhuma parte nomeada.</span><span class="sxs-lookup"><span data-stu-id="042eb-107">The <xref:System.Windows.Controls.ContextMenu> control does not have any named parts.</span></span>  
  
 <span data-ttu-id="042eb-108">Quando você cria um <xref:System.Windows.Controls.ControlTemplate> para uma <xref:System.Windows.Controls.ContextMenu>, seu modelo pode conter uma <xref:System.Windows.Controls.ItemsPresenter> em um <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="042eb-108">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ContextMenu>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="042eb-109">(O <xref:System.Windows.Controls.ItemsPresenter> exibe cada item na <xref:System.Windows.Controls.ContextMenu>; o <xref:System.Windows.Controls.ScrollViewer> habilita a rolagem dentro do controle).</span><span class="sxs-lookup"><span data-stu-id="042eb-109">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ContextMenu>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="042eb-110">Se o <xref:System.Windows.Controls.ItemsPresenter> não for o filho direto do <xref:System.Windows.Controls.ScrollViewer>, você deverá dar ao <xref:System.Windows.Controls.ItemsPresenter> o nome `ItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="042eb-110">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="contextmenu-states"></a><span data-ttu-id="042eb-111">Estados de ContextMenu</span><span class="sxs-lookup"><span data-stu-id="042eb-111">ContextMenu States</span></span>  
 <span data-ttu-id="042eb-112">A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Controls.ContextMenu>.</span><span class="sxs-lookup"><span data-stu-id="042eb-112">The following table lists the visual states for the <xref:System.Windows.Controls.ContextMenu> control.</span></span>  
  
|<span data-ttu-id="042eb-113">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="042eb-113">VisualState Name</span></span>|<span data-ttu-id="042eb-114">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="042eb-114">VisualStateGroup Name</span></span>|<span data-ttu-id="042eb-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="042eb-115">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="042eb-116">Válido</span><span class="sxs-lookup"><span data-stu-id="042eb-116">Valid</span></span>|<span data-ttu-id="042eb-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="042eb-117">ValidationStates</span></span>|<span data-ttu-id="042eb-118">O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.</span><span class="sxs-lookup"><span data-stu-id="042eb-118">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="042eb-119">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="042eb-119">InvalidFocused</span></span>|<span data-ttu-id="042eb-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="042eb-120">ValidationStates</span></span>|<span data-ttu-id="042eb-121">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.</span><span class="sxs-lookup"><span data-stu-id="042eb-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="042eb-122">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="042eb-122">InvalidUnfocused</span></span>|<span data-ttu-id="042eb-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="042eb-123">ValidationStates</span></span>|<span data-ttu-id="042eb-124">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="042eb-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="contextmenu-controltemplate-example"></a><span data-ttu-id="042eb-125">Exemplo de ControlTemplate de ContextMenu</span><span class="sxs-lookup"><span data-stu-id="042eb-125">ContextMenu ControlTemplate Example</span></span>  
 <span data-ttu-id="042eb-126">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o controle de <xref:System.Windows.Controls.ContextMenu>.</span><span class="sxs-lookup"><span data-stu-id="042eb-126">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ContextMenu> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ContextMenu](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#contextmenu)]  
  
 <span data-ttu-id="042eb-127">O <xref:System.Windows.Controls.ControlTemplate> usa os recursos a seguir.</span><span class="sxs-lookup"><span data-stu-id="042eb-127">The <xref:System.Windows.Controls.ControlTemplate> uses the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="042eb-128">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="042eb-128">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="042eb-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="042eb-129">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="042eb-130">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="042eb-130">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="042eb-131">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="042eb-131">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="042eb-132">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="042eb-132">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="042eb-133">Criar um modelo para um controle</span><span class="sxs-lookup"><span data-stu-id="042eb-133">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
