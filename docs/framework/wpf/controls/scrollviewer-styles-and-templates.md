---
title: Estilos e modelos ScrollViewer
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], ScrollViewer
- states [WPF], ScrollViewer
- styles [WPF], ScrollViewer
- templates [WPF], ScrollViewer
- ControlTemplate [WPF], ScrollViewer
- ScrollViewer [WPF], styles and templates
ms.assetid: dffdd822-ae69-4946-abaf-710860cd65b2
ms.openlocfilehash: 5ad3738972ae9b33764d3b710077f6d4a0526a13
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/23/2018
---
# <a name="scrollviewer-styles-and-templates"></a><span data-ttu-id="c12cf-102">Estilos e modelos ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="c12cf-102">ScrollViewer Styles and Templates</span></span>
<span data-ttu-id="c12cf-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.ScrollViewer> controle.</span><span class="sxs-lookup"><span data-stu-id="c12cf-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span> <span data-ttu-id="c12cf-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para que o controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="c12cf-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="c12cf-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="c12cf-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="scrollviewer-parts"></a><span data-ttu-id="c12cf-106">Partes de ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="c12cf-106">ScrollViewer Parts</span></span>  
 <span data-ttu-id="c12cf-107">A tabela a seguir lista as partes nomeadas para o <xref:System.Windows.Controls.ScrollViewer> controle.</span><span class="sxs-lookup"><span data-stu-id="c12cf-107">The following table lists the named parts for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="c12cf-108">Parte</span><span class="sxs-lookup"><span data-stu-id="c12cf-108">Part</span></span>|<span data-ttu-id="c12cf-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="c12cf-109">Type</span></span>|<span data-ttu-id="c12cf-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="c12cf-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="c12cf-111">PART_ScrollContentPresenter</span><span class="sxs-lookup"><span data-stu-id="c12cf-111">PART_ScrollContentPresenter</span></span>|<xref:System.Windows.Controls.ScrollContentPresenter>|<span data-ttu-id="c12cf-112">O espaço reservado para o conteúdo a <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="c12cf-112">The placeholder for content in the <xref:System.Windows.Controls.ScrollViewer>.</span></span>|  
|<span data-ttu-id="c12cf-113">PART_HorizontalScrollBar</span><span class="sxs-lookup"><span data-stu-id="c12cf-113">PART_HorizontalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="c12cf-114">O <xref:System.Windows.Controls.Primitives.ScrollBar> usado para rolar o conteúdo horizontalmente.</span><span class="sxs-lookup"><span data-stu-id="c12cf-114">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content horizontally.</span></span>|  
|<span data-ttu-id="c12cf-115">PART_VerticalScrollBar</span><span class="sxs-lookup"><span data-stu-id="c12cf-115">PART_VerticalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="c12cf-116">O <xref:System.Windows.Controls.Primitives.ScrollBar> usado para rolar o conteúdo verticalmente.</span><span class="sxs-lookup"><span data-stu-id="c12cf-116">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content vertically.</span></span>|  
  
## <a name="scrollviewer-states"></a><span data-ttu-id="c12cf-117">Estados de ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="c12cf-117">ScrollViewer States</span></span>  
 <span data-ttu-id="c12cf-118">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.ScrollViewer> controle.</span><span class="sxs-lookup"><span data-stu-id="c12cf-118">The following table lists the visual states for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="c12cf-119">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="c12cf-119">VisualState Name</span></span>|<span data-ttu-id="c12cf-120">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="c12cf-120">VisualStateGroup Name</span></span>|<span data-ttu-id="c12cf-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="c12cf-121">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="c12cf-122">Válido</span><span class="sxs-lookup"><span data-stu-id="c12cf-122">Valid</span></span>|<span data-ttu-id="c12cf-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c12cf-123">ValidationStates</span></span>|<span data-ttu-id="c12cf-124">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="c12cf-124">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="c12cf-125">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="c12cf-125">InvalidFocused</span></span>|<span data-ttu-id="c12cf-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c12cf-126">ValidationStates</span></span>|<span data-ttu-id="c12cf-127">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="c12cf-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="c12cf-128">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="c12cf-128">InvalidUnfocused</span></span>|<span data-ttu-id="c12cf-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c12cf-129">ValidationStates</span></span>|<span data-ttu-id="c12cf-130">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="c12cf-130">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="scrollviewer-controltemplate-example"></a><span data-ttu-id="c12cf-131">Exemplo de ControlTemplate de ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="c12cf-131">ScrollViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="c12cf-132">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.ScrollViewer> controle.</span><span class="sxs-lookup"><span data-stu-id="c12cf-132">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollViewer](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollviewer.xaml#scrollviewer)]  
  
 <span data-ttu-id="c12cf-133">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="c12cf-133">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="c12cf-134">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="c12cf-134">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c12cf-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c12cf-135">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="c12cf-136">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="c12cf-136">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="c12cf-137">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="c12cf-137">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="c12cf-138">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="c12cf-138">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="c12cf-139">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="c12cf-139">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
