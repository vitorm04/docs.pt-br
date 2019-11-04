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
ms.openlocfilehash: b782e62500edd14b40b1267c3b7f92758210a5c0
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458214"
---
# <a name="toolbar-styles-and-templates"></a><span data-ttu-id="1f344-102">Estilos e modelos ToolBar</span><span class="sxs-lookup"><span data-stu-id="1f344-102">ToolBar Styles and Templates</span></span>
<span data-ttu-id="1f344-103">Este tópico descreve os estilos e modelos para o controle de <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="1f344-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolBar> control.</span></span> <span data-ttu-id="1f344-104">Você pode modificar o <xref:System.Windows.Controls.ControlTemplate> padrão para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="1f344-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="1f344-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="1f344-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="toolbar-parts"></a><span data-ttu-id="1f344-106">Partes da barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="1f344-106">ToolBar Parts</span></span>  
 <span data-ttu-id="1f344-107">A tabela a seguir lista as partes nomeadas para o controle de <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="1f344-107">The following table lists the named parts for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
|<span data-ttu-id="1f344-108">Parte</span><span class="sxs-lookup"><span data-stu-id="1f344-108">Part</span></span>|<span data-ttu-id="1f344-109">Digite</span><span class="sxs-lookup"><span data-stu-id="1f344-109">Type</span></span>|<span data-ttu-id="1f344-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="1f344-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="1f344-111">PART_ToolBarPanel</span><span class="sxs-lookup"><span data-stu-id="1f344-111">PART_ToolBarPanel</span></span>|<xref:System.Windows.Controls.Primitives.ToolBarPanel>|<span data-ttu-id="1f344-112">O objeto que contém os controles na <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="1f344-112">The object that contains the controls on the <xref:System.Windows.Controls.ToolBar>.</span></span>|  
|<span data-ttu-id="1f344-113">PART_ToolBarOverflowPanel</span><span class="sxs-lookup"><span data-stu-id="1f344-113">PART_ToolBarOverflowPanel</span></span>|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|<span data-ttu-id="1f344-114">O objeto que contém os controles que estão na área de estouro do <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="1f344-114">The object that contains the controls that are in the overflow area of the <xref:System.Windows.Controls.ToolBar>.</span></span>|  
  
 <span data-ttu-id="1f344-115">Quando você cria um <xref:System.Windows.Controls.ControlTemplate> para uma <xref:System.Windows.Controls.ToolBar>, seu modelo pode conter uma <xref:System.Windows.Controls.ItemsPresenter> em um <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="1f344-115">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ToolBar>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="1f344-116">(O <xref:System.Windows.Controls.ItemsPresenter> exibe cada item na <xref:System.Windows.Controls.ToolBar>; o <xref:System.Windows.Controls.ScrollViewer> habilita a rolagem dentro do controle).</span><span class="sxs-lookup"><span data-stu-id="1f344-116">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ToolBar>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="1f344-117">Se o <xref:System.Windows.Controls.ItemsPresenter> não for o filho direto do <xref:System.Windows.Controls.ScrollViewer>, você deverá dar ao <xref:System.Windows.Controls.ItemsPresenter> o nome `ItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="1f344-117">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="toolbar-states"></a><span data-ttu-id="1f344-118">Estados da barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="1f344-118">ToolBar States</span></span>  
 <span data-ttu-id="1f344-119">A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="1f344-119">The following table lists the visual states for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
|<span data-ttu-id="1f344-120">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="1f344-120">VisualState Name</span></span>|<span data-ttu-id="1f344-121">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="1f344-121">VisualStateGroup Name</span></span>|<span data-ttu-id="1f344-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="1f344-122">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="1f344-123">Válido</span><span class="sxs-lookup"><span data-stu-id="1f344-123">Valid</span></span>|<span data-ttu-id="1f344-124">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="1f344-124">ValidationStates</span></span>|<span data-ttu-id="1f344-125">O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.</span><span class="sxs-lookup"><span data-stu-id="1f344-125">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="1f344-126">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="1f344-126">InvalidFocused</span></span>|<span data-ttu-id="1f344-127">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="1f344-127">ValidationStates</span></span>|<span data-ttu-id="1f344-128">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.</span><span class="sxs-lookup"><span data-stu-id="1f344-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="1f344-129">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="1f344-129">InvalidUnfocused</span></span>|<span data-ttu-id="1f344-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="1f344-130">ValidationStates</span></span>|<span data-ttu-id="1f344-131">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="1f344-131">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="toolbar-controltemplate-example"></a><span data-ttu-id="1f344-132">Exemplo de ControlTemplate da barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="1f344-132">ToolBar ControlTemplate Example</span></span>  
 <span data-ttu-id="1f344-133">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o controle de <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="1f344-133">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/toolbar.xaml#toolbar)]  
  
 <span data-ttu-id="1f344-134">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="1f344-134">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="1f344-135">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="1f344-135">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f344-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1f344-136">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="1f344-137">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="1f344-137">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="1f344-138">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="1f344-138">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="1f344-139">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="1f344-139">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="1f344-140">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="1f344-140">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
