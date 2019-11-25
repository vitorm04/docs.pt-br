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
ms.openlocfilehash: b54dcacf55a750d7c1253db20147d18de47d027e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283402"
---
# <a name="scrollviewer-styles-and-templates"></a><span data-ttu-id="aba47-102">Estilos e modelos ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="aba47-102">ScrollViewer Styles and Templates</span></span>
<span data-ttu-id="aba47-103">Este tópico descreve os estilos e modelos para o controle de <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="aba47-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span> <span data-ttu-id="aba47-104">Você pode modificar o <xref:System.Windows.Controls.ControlTemplate> padrão para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="aba47-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="aba47-105">Para obter mais informações, consulte [criar um modelo para um controle](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="aba47-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="scrollviewer-parts"></a><span data-ttu-id="aba47-106">Partes ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="aba47-106">ScrollViewer Parts</span></span>  
 <span data-ttu-id="aba47-107">A tabela a seguir lista as partes nomeadas para o controle de <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="aba47-107">The following table lists the named parts for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="aba47-108">Parte</span><span class="sxs-lookup"><span data-stu-id="aba47-108">Part</span></span>|<span data-ttu-id="aba47-109">Digite</span><span class="sxs-lookup"><span data-stu-id="aba47-109">Type</span></span>|<span data-ttu-id="aba47-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="aba47-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="aba47-111">PART_ScrollContentPresenter</span><span class="sxs-lookup"><span data-stu-id="aba47-111">PART_ScrollContentPresenter</span></span>|<xref:System.Windows.Controls.ScrollContentPresenter>|<span data-ttu-id="aba47-112">O espaço reservado para conteúdo no <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="aba47-112">The placeholder for content in the <xref:System.Windows.Controls.ScrollViewer>.</span></span>|  
|<span data-ttu-id="aba47-113">PART_HorizontalScrollBar</span><span class="sxs-lookup"><span data-stu-id="aba47-113">PART_HorizontalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="aba47-114">O <xref:System.Windows.Controls.Primitives.ScrollBar> usado para rolar o conteúdo horizontalmente.</span><span class="sxs-lookup"><span data-stu-id="aba47-114">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content horizontally.</span></span>|  
|<span data-ttu-id="aba47-115">PART_VerticalScrollBar</span><span class="sxs-lookup"><span data-stu-id="aba47-115">PART_VerticalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="aba47-116">O <xref:System.Windows.Controls.Primitives.ScrollBar> usado para rolar o conteúdo verticalmente.</span><span class="sxs-lookup"><span data-stu-id="aba47-116">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content vertically.</span></span>|  
  
## <a name="scrollviewer-states"></a><span data-ttu-id="aba47-117">Estados de ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="aba47-117">ScrollViewer States</span></span>  
 <span data-ttu-id="aba47-118">A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="aba47-118">The following table lists the visual states for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="aba47-119">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="aba47-119">VisualState Name</span></span>|<span data-ttu-id="aba47-120">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="aba47-120">VisualStateGroup Name</span></span>|<span data-ttu-id="aba47-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="aba47-121">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="aba47-122">Válido</span><span class="sxs-lookup"><span data-stu-id="aba47-122">Valid</span></span>|<span data-ttu-id="aba47-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="aba47-123">ValidationStates</span></span>|<span data-ttu-id="aba47-124">O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.</span><span class="sxs-lookup"><span data-stu-id="aba47-124">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="aba47-125">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="aba47-125">InvalidFocused</span></span>|<span data-ttu-id="aba47-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="aba47-126">ValidationStates</span></span>|<span data-ttu-id="aba47-127">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.</span><span class="sxs-lookup"><span data-stu-id="aba47-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="aba47-128">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="aba47-128">InvalidUnfocused</span></span>|<span data-ttu-id="aba47-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="aba47-129">ValidationStates</span></span>|<span data-ttu-id="aba47-130">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="aba47-130">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="scrollviewer-controltemplate-example"></a><span data-ttu-id="aba47-131">Exemplo de ControlTemplate de ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="aba47-131">ScrollViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="aba47-132">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o controle de <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="aba47-132">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollViewer](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollviewer.xaml#scrollviewer)]  
  
 <span data-ttu-id="aba47-133">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="aba47-133">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="aba47-134">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="aba47-134">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aba47-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aba47-135">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="aba47-136">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="aba47-136">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="aba47-137">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="aba47-137">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="aba47-138">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="aba47-138">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="aba47-139">Criar um modelo para um controle</span><span class="sxs-lookup"><span data-stu-id="aba47-139">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
