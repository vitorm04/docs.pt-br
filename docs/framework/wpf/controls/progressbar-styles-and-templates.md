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
ms.openlocfilehash: 3a1bea39ba9b6d2cff9937a3fee1d1de41daf16b
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459877"
---
# <a name="progressbar-styles-and-templates"></a><span data-ttu-id="15722-102">Estilos e modelos ProgressBar</span><span class="sxs-lookup"><span data-stu-id="15722-102">ProgressBar Styles and Templates</span></span>
<span data-ttu-id="15722-103">Este tópico descreve os estilos e modelos para o controle de <xref:System.Windows.Controls.ProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="15722-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ProgressBar> control.</span></span> <span data-ttu-id="15722-104">Você pode modificar o <xref:System.Windows.Controls.ControlTemplate> padrão para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="15722-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="15722-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="15722-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="progressbar-parts"></a><span data-ttu-id="15722-106">Partes de ProgressBar</span><span class="sxs-lookup"><span data-stu-id="15722-106">ProgressBar Parts</span></span>  
 <span data-ttu-id="15722-107">A tabela a seguir lista as partes nomeadas para o controle de <xref:System.Windows.Controls.ProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="15722-107">The following table lists the named parts for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="15722-108">Parte</span><span class="sxs-lookup"><span data-stu-id="15722-108">Part</span></span>|<span data-ttu-id="15722-109">Digite</span><span class="sxs-lookup"><span data-stu-id="15722-109">Type</span></span>|<span data-ttu-id="15722-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="15722-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="15722-111">PART_Indicator</span><span class="sxs-lookup"><span data-stu-id="15722-111">PART_Indicator</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="15722-112">O objeto que indica o progresso.</span><span class="sxs-lookup"><span data-stu-id="15722-112">The object that indicates progress.</span></span>|  
|<span data-ttu-id="15722-113">PART_Track</span><span class="sxs-lookup"><span data-stu-id="15722-113">PART_Track</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="15722-114">O objeto que define o caminho do indicador de progresso.</span><span class="sxs-lookup"><span data-stu-id="15722-114">The object that defines the path of the progress indicator.</span></span>|  
|<span data-ttu-id="15722-115">PART_GlowRect</span><span class="sxs-lookup"><span data-stu-id="15722-115">PART_GlowRect</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="15722-116">Um objeto que ornamenta a barra de progresso.</span><span class="sxs-lookup"><span data-stu-id="15722-116">An object that embellishes the progress bar.</span></span>|  
  
## <a name="progressbar-states"></a><span data-ttu-id="15722-117">Estados de ProgressBar</span><span class="sxs-lookup"><span data-stu-id="15722-117">ProgressBar States</span></span>  
 <span data-ttu-id="15722-118">A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Controls.ProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="15722-118">The following table lists the visual states for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="15722-119">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="15722-119">VisualState Name</span></span>|<span data-ttu-id="15722-120">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="15722-120">VisualStateGroup Name</span></span>|<span data-ttu-id="15722-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="15722-121">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="15722-122">Barra</span><span class="sxs-lookup"><span data-stu-id="15722-122">Determinate</span></span>|<span data-ttu-id="15722-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="15722-123">CommonStates</span></span>|<span data-ttu-id="15722-124"><xref:System.Windows.Controls.ProgressBar> relata o progresso com base na propriedade <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="15722-124"><xref:System.Windows.Controls.ProgressBar> reports progress based on the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property.</span></span>|  
|<span data-ttu-id="15722-125">Indeterminado</span><span class="sxs-lookup"><span data-stu-id="15722-125">Indeterminate</span></span>|<span data-ttu-id="15722-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="15722-126">CommonStates</span></span>|<span data-ttu-id="15722-127"><xref:System.Windows.Controls.ProgressBar> relata o progresso genérico com um padrão repetido.</span><span class="sxs-lookup"><span data-stu-id="15722-127"><xref:System.Windows.Controls.ProgressBar> reports generic progress with a repeating pattern.</span></span>|  
|<span data-ttu-id="15722-128">Válido</span><span class="sxs-lookup"><span data-stu-id="15722-128">Valid</span></span>|<span data-ttu-id="15722-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="15722-129">ValidationStates</span></span>|<span data-ttu-id="15722-130">O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.</span><span class="sxs-lookup"><span data-stu-id="15722-130">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="15722-131">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="15722-131">InvalidFocused</span></span>|<span data-ttu-id="15722-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="15722-132">ValidationStates</span></span>|<span data-ttu-id="15722-133">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.</span><span class="sxs-lookup"><span data-stu-id="15722-133">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="15722-134">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="15722-134">InvalidUnfocused</span></span>|<span data-ttu-id="15722-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="15722-135">ValidationStates</span></span>|<span data-ttu-id="15722-136">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="15722-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="progressbar-controltemplate-example"></a><span data-ttu-id="15722-137">Exemplo de ControlTemplate de ProgressBar</span><span class="sxs-lookup"><span data-stu-id="15722-137">ProgressBar ControlTemplate Example</span></span>  
 <span data-ttu-id="15722-138">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o controle de <xref:System.Windows.Controls.ProgressBar>.</span><span class="sxs-lookup"><span data-stu-id="15722-138">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ProgressBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
 <span data-ttu-id="15722-139">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="15722-139">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="15722-140">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="15722-140">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15722-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="15722-141">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="15722-142">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="15722-142">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="15722-143">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="15722-143">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="15722-144">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="15722-144">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="15722-145">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="15722-145">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
