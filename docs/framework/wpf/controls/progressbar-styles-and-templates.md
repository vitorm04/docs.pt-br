---
title: Estilos e modelos ProgressBar
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], ProgressBar
- ProgressBar [WPF], styles and templates
- styles [WPF], ProgressBar
- ControlTemplate [WPF], ProgressBar
- templates [WPF], ProgressBar
- states [WPF], ProgressBar
ms.assetid: 935aa600-16e6-4947-a905-37a189a583dd
ms.openlocfilehash: 6551701e86dd6abcd42f143f146c7bdadfeabbcf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283449"
---
# <a name="progressbar-styles-and-templates"></a><span data-ttu-id="3715f-102">Estilos e modelos ProgressBar</span><span class="sxs-lookup"><span data-stu-id="3715f-102">ProgressBar Styles and Templates</span></span>
<span data-ttu-id="3715f-103">Este tópico descreve os estilos e modelos para o controle de <xref:System.Windows.Controls.ProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="3715f-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ProgressBar> control.</span></span> <span data-ttu-id="3715f-104">Você pode modificar o <xref:System.Windows.Controls.ControlTemplate> padrão para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="3715f-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="3715f-105">Para obter mais informações, consulte [criar um modelo para um controle](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="3715f-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="progressbar-parts"></a><span data-ttu-id="3715f-106">Partes de ProgressBar</span><span class="sxs-lookup"><span data-stu-id="3715f-106">ProgressBar Parts</span></span>  
 <span data-ttu-id="3715f-107">A tabela a seguir lista as partes nomeadas para o controle de <xref:System.Windows.Controls.ProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="3715f-107">The following table lists the named parts for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="3715f-108">Parte</span><span class="sxs-lookup"><span data-stu-id="3715f-108">Part</span></span>|<span data-ttu-id="3715f-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="3715f-109">Type</span></span>|<span data-ttu-id="3715f-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="3715f-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="3715f-111">PART_Indicator</span><span class="sxs-lookup"><span data-stu-id="3715f-111">PART_Indicator</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="3715f-112">O objeto que indica o progresso.</span><span class="sxs-lookup"><span data-stu-id="3715f-112">The object that indicates progress.</span></span>|  
|<span data-ttu-id="3715f-113">PART_Track</span><span class="sxs-lookup"><span data-stu-id="3715f-113">PART_Track</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="3715f-114">O objeto que define o caminho do indicador de progresso.</span><span class="sxs-lookup"><span data-stu-id="3715f-114">The object that defines the path of the progress indicator.</span></span>|  
|<span data-ttu-id="3715f-115">PART_GlowRect</span><span class="sxs-lookup"><span data-stu-id="3715f-115">PART_GlowRect</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="3715f-116">Um objeto que ornamenta a barra de progresso.</span><span class="sxs-lookup"><span data-stu-id="3715f-116">An object that embellishes the progress bar.</span></span>|  
  
## <a name="progressbar-states"></a><span data-ttu-id="3715f-117">Estados de ProgressBar</span><span class="sxs-lookup"><span data-stu-id="3715f-117">ProgressBar States</span></span>  
 <span data-ttu-id="3715f-118">A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Controls.ProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="3715f-118">The following table lists the visual states for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="3715f-119">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="3715f-119">VisualState Name</span></span>|<span data-ttu-id="3715f-120">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="3715f-120">VisualStateGroup Name</span></span>|<span data-ttu-id="3715f-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="3715f-121">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="3715f-122">Barra</span><span class="sxs-lookup"><span data-stu-id="3715f-122">Determinate</span></span>|<span data-ttu-id="3715f-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="3715f-123">CommonStates</span></span>|<span data-ttu-id="3715f-124"><xref:System.Windows.Controls.ProgressBar> relata o progresso com base na propriedade <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="3715f-124"><xref:System.Windows.Controls.ProgressBar> reports progress based on the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property.</span></span>|  
|<span data-ttu-id="3715f-125">Indeterminado</span><span class="sxs-lookup"><span data-stu-id="3715f-125">Indeterminate</span></span>|<span data-ttu-id="3715f-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="3715f-126">CommonStates</span></span>|<span data-ttu-id="3715f-127"><xref:System.Windows.Controls.ProgressBar> relata o progresso genérico com um padrão repetido.</span><span class="sxs-lookup"><span data-stu-id="3715f-127"><xref:System.Windows.Controls.ProgressBar> reports generic progress with a repeating pattern.</span></span>|  
|<span data-ttu-id="3715f-128">Válido</span><span class="sxs-lookup"><span data-stu-id="3715f-128">Valid</span></span>|<span data-ttu-id="3715f-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3715f-129">ValidationStates</span></span>|<span data-ttu-id="3715f-130">O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.</span><span class="sxs-lookup"><span data-stu-id="3715f-130">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="3715f-131">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="3715f-131">InvalidFocused</span></span>|<span data-ttu-id="3715f-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3715f-132">ValidationStates</span></span>|<span data-ttu-id="3715f-133">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.</span><span class="sxs-lookup"><span data-stu-id="3715f-133">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="3715f-134">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="3715f-134">InvalidUnfocused</span></span>|<span data-ttu-id="3715f-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3715f-135">ValidationStates</span></span>|<span data-ttu-id="3715f-136">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="3715f-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="progressbar-controltemplate-example"></a><span data-ttu-id="3715f-137">Exemplo de ControlTemplate de ProgressBar</span><span class="sxs-lookup"><span data-stu-id="3715f-137">ProgressBar ControlTemplate Example</span></span>  
 <span data-ttu-id="3715f-138">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o controle de <xref:System.Windows.Controls.ProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="3715f-138">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ProgressBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
 <span data-ttu-id="3715f-139">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="3715f-139">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="3715f-140">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="3715f-140">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3715f-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3715f-141">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="3715f-142">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="3715f-142">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="3715f-143">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="3715f-143">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="3715f-144">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="3715f-144">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="3715f-145">Criar um modelo para um controle</span><span class="sxs-lookup"><span data-stu-id="3715f-145">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
