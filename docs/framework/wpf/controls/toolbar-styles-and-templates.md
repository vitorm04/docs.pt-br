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
ms.openlocfilehash: 022581c6ef154874e563513a719fc8590a13b30a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54655680"
---
# <a name="toolbar-styles-and-templates"></a><span data-ttu-id="2d045-102">Estilos e modelos ToolBar</span><span class="sxs-lookup"><span data-stu-id="2d045-102">ToolBar Styles and Templates</span></span>
<span data-ttu-id="2d045-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.ToolBar> controle.</span><span class="sxs-lookup"><span data-stu-id="2d045-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolBar> control.</span></span> <span data-ttu-id="2d045-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="2d045-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="2d045-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="2d045-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="toolbar-parts"></a><span data-ttu-id="2d045-106">Partes da barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="2d045-106">ToolBar Parts</span></span>  
 <span data-ttu-id="2d045-107">A tabela a seguir lista as partes nomeadas para o <xref:System.Windows.Controls.ToolBar> controle.</span><span class="sxs-lookup"><span data-stu-id="2d045-107">The following table lists the named parts for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
|<span data-ttu-id="2d045-108">Parte</span><span class="sxs-lookup"><span data-stu-id="2d045-108">Part</span></span>|<span data-ttu-id="2d045-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="2d045-109">Type</span></span>|<span data-ttu-id="2d045-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="2d045-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="2d045-111">PART_ToolBarPanel</span><span class="sxs-lookup"><span data-stu-id="2d045-111">PART_ToolBarPanel</span></span>|<xref:System.Windows.Controls.Primitives.ToolBarPanel>|<span data-ttu-id="2d045-112">O objeto que contém os controles no <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="2d045-112">The object that contains the controls on the <xref:System.Windows.Controls.ToolBar>.</span></span>|  
|<span data-ttu-id="2d045-113">PART_ToolBarOverflowPanel</span><span class="sxs-lookup"><span data-stu-id="2d045-113">PART_ToolBarOverflowPanel</span></span>|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|<span data-ttu-id="2d045-114">O objeto que contém os controles que estão na área de excedentes do <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="2d045-114">The object that contains the controls that are in the overflow area of the <xref:System.Windows.Controls.ToolBar>.</span></span>|  
  
 <span data-ttu-id="2d045-115">Quando você cria um <xref:System.Windows.Controls.ControlTemplate> para um <xref:System.Windows.Controls.ToolBar>, o modelo pode conter um <xref:System.Windows.Controls.ItemsPresenter> dentro de um <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="2d045-115">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ToolBar>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="2d045-116">(O <xref:System.Windows.Controls.ItemsPresenter> exibe cada item em de <xref:System.Windows.Controls.ToolBar>; o <xref:System.Windows.Controls.ScrollViewer> habilita a rolagem no controle).</span><span class="sxs-lookup"><span data-stu-id="2d045-116">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ToolBar>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="2d045-117">Se o <xref:System.Windows.Controls.ItemsPresenter> não é filho direto do <xref:System.Windows.Controls.ScrollViewer>, você deve dar a <xref:System.Windows.Controls.ItemsPresenter> o nome, `ItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="2d045-117">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="toolbar-states"></a><span data-ttu-id="2d045-118">Estados de barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="2d045-118">ToolBar States</span></span>  
 <span data-ttu-id="2d045-119">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.ToolBar> controle.</span><span class="sxs-lookup"><span data-stu-id="2d045-119">The following table lists the visual states for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
|<span data-ttu-id="2d045-120">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="2d045-120">VisualState Name</span></span>|<span data-ttu-id="2d045-121">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="2d045-121">VisualStateGroup Name</span></span>|<span data-ttu-id="2d045-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="2d045-122">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="2d045-123">Válido</span><span class="sxs-lookup"><span data-stu-id="2d045-123">Valid</span></span>|<span data-ttu-id="2d045-124">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2d045-124">ValidationStates</span></span>|<span data-ttu-id="2d045-125">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="2d045-125">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="2d045-126">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="2d045-126">InvalidFocused</span></span>|<span data-ttu-id="2d045-127">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2d045-127">ValidationStates</span></span>|<span data-ttu-id="2d045-128">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="2d045-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="2d045-129">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="2d045-129">InvalidUnfocused</span></span>|<span data-ttu-id="2d045-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2d045-130">ValidationStates</span></span>|<span data-ttu-id="2d045-131">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle não tem o foco.</span><span class="sxs-lookup"><span data-stu-id="2d045-131">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="toolbar-controltemplate-example"></a><span data-ttu-id="2d045-132">Exemplo de ControlTemplate de barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="2d045-132">ToolBar ControlTemplate Example</span></span>  
 <span data-ttu-id="2d045-133">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.ToolBar> controle.</span><span class="sxs-lookup"><span data-stu-id="2d045-133">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/toolbar.xaml#toolbar)]  
  
 <span data-ttu-id="2d045-134">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="2d045-134">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="2d045-135">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="2d045-135">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d045-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2d045-136">See also</span></span>
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="2d045-137">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="2d045-137">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)
- [<span data-ttu-id="2d045-138">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="2d045-138">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)
- [<span data-ttu-id="2d045-139">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="2d045-139">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [<span data-ttu-id="2d045-140">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="2d045-140">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
