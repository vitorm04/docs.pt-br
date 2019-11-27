---
title: Estilos e modelos ToolBar
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], ToolBar
- styles [WPF], ToolBar
- ControlTemplate [WPF], ToolBar
- parts [WPF], ToolBar
- ToolBar [WPF], styles and templates
- templates [WPF], ToolBar
ms.assetid: bd875f46-4690-46f5-81e0-f11a9822484f
ms.openlocfilehash: a984311234386cb205d5db35f18a743ca535ff05
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283663"
---
# <a name="toolbar-styles-and-templates"></a><span data-ttu-id="24675-102">Estilos e modelos ToolBar</span><span class="sxs-lookup"><span data-stu-id="24675-102">ToolBar Styles and Templates</span></span>
<span data-ttu-id="24675-103">Este tópico descreve os estilos e modelos para o controle de <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="24675-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolBar> control.</span></span> <span data-ttu-id="24675-104">Você pode modificar o <xref:System.Windows.Controls.ControlTemplate> padrão para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="24675-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="24675-105">Para obter mais informações, consulte [criar um modelo para um controle](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="24675-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="toolbar-parts"></a><span data-ttu-id="24675-106">Partes da barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="24675-106">ToolBar Parts</span></span>  
 <span data-ttu-id="24675-107">A tabela a seguir lista as partes nomeadas para o controle de <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="24675-107">The following table lists the named parts for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
|<span data-ttu-id="24675-108">Parte</span><span class="sxs-lookup"><span data-stu-id="24675-108">Part</span></span>|<span data-ttu-id="24675-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="24675-109">Type</span></span>|<span data-ttu-id="24675-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="24675-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="24675-111">PART_ToolBarPanel</span><span class="sxs-lookup"><span data-stu-id="24675-111">PART_ToolBarPanel</span></span>|<xref:System.Windows.Controls.Primitives.ToolBarPanel>|<span data-ttu-id="24675-112">O objeto que contém os controles na <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="24675-112">The object that contains the controls on the <xref:System.Windows.Controls.ToolBar>.</span></span>|  
|<span data-ttu-id="24675-113">PART_ToolBarOverflowPanel</span><span class="sxs-lookup"><span data-stu-id="24675-113">PART_ToolBarOverflowPanel</span></span>|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|<span data-ttu-id="24675-114">O objeto que contém os controles que estão na área de estouro do <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="24675-114">The object that contains the controls that are in the overflow area of the <xref:System.Windows.Controls.ToolBar>.</span></span>|  
  
 <span data-ttu-id="24675-115">Quando você cria um <xref:System.Windows.Controls.ControlTemplate> para uma <xref:System.Windows.Controls.ToolBar>, seu modelo pode conter uma <xref:System.Windows.Controls.ItemsPresenter> em um <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="24675-115">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ToolBar>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="24675-116">(O <xref:System.Windows.Controls.ItemsPresenter> exibe cada item na <xref:System.Windows.Controls.ToolBar>; o <xref:System.Windows.Controls.ScrollViewer> habilita a rolagem dentro do controle).</span><span class="sxs-lookup"><span data-stu-id="24675-116">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ToolBar>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="24675-117">Se o <xref:System.Windows.Controls.ItemsPresenter> não for o filho direto do <xref:System.Windows.Controls.ScrollViewer>, você deverá dar ao <xref:System.Windows.Controls.ItemsPresenter> o nome `ItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="24675-117">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="toolbar-states"></a><span data-ttu-id="24675-118">Estados da barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="24675-118">ToolBar States</span></span>  
 <span data-ttu-id="24675-119">A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="24675-119">The following table lists the visual states for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
|<span data-ttu-id="24675-120">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="24675-120">VisualState Name</span></span>|<span data-ttu-id="24675-121">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="24675-121">VisualStateGroup Name</span></span>|<span data-ttu-id="24675-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="24675-122">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="24675-123">Válido</span><span class="sxs-lookup"><span data-stu-id="24675-123">Valid</span></span>|<span data-ttu-id="24675-124">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="24675-124">ValidationStates</span></span>|<span data-ttu-id="24675-125">O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.</span><span class="sxs-lookup"><span data-stu-id="24675-125">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="24675-126">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="24675-126">InvalidFocused</span></span>|<span data-ttu-id="24675-127">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="24675-127">ValidationStates</span></span>|<span data-ttu-id="24675-128">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.</span><span class="sxs-lookup"><span data-stu-id="24675-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="24675-129">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="24675-129">InvalidUnfocused</span></span>|<span data-ttu-id="24675-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="24675-130">ValidationStates</span></span>|<span data-ttu-id="24675-131">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="24675-131">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="toolbar-controltemplate-example"></a><span data-ttu-id="24675-132">Exemplo de ControlTemplate da barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="24675-132">ToolBar ControlTemplate Example</span></span>  
 <span data-ttu-id="24675-133">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o controle de <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="24675-133">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/toolbar.xaml#toolbar)]  
  
 <span data-ttu-id="24675-134">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="24675-134">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="24675-135">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="24675-135">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24675-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="24675-136">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="24675-137">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="24675-137">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="24675-138">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="24675-138">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="24675-139">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="24675-139">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="24675-140">Criar um modelo para um controle</span><span class="sxs-lookup"><span data-stu-id="24675-140">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
