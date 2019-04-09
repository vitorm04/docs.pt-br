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
ms.openlocfilehash: f948cf2b4f4cd2a4cb73b0cd5fc754240c850b83
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59099411"
---
# <a name="progressbar-styles-and-templates"></a><span data-ttu-id="3aeb8-102">Estilos e modelos ProgressBar</span><span class="sxs-lookup"><span data-stu-id="3aeb8-102">ProgressBar Styles and Templates</span></span>
<span data-ttu-id="3aeb8-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.ProgressBar> controle.</span><span class="sxs-lookup"><span data-stu-id="3aeb8-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ProgressBar> control.</span></span> <span data-ttu-id="3aeb8-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="3aeb8-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="3aeb8-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="3aeb8-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="progressbar-parts"></a><span data-ttu-id="3aeb8-106">Partes da barra de progresso</span><span class="sxs-lookup"><span data-stu-id="3aeb8-106">ProgressBar Parts</span></span>  
 <span data-ttu-id="3aeb8-107">A tabela a seguir lista as partes nomeadas para o <xref:System.Windows.Controls.ProgressBar> controle.</span><span class="sxs-lookup"><span data-stu-id="3aeb8-107">The following table lists the named parts for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="3aeb8-108">Parte</span><span class="sxs-lookup"><span data-stu-id="3aeb8-108">Part</span></span>|<span data-ttu-id="3aeb8-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="3aeb8-109">Type</span></span>|<span data-ttu-id="3aeb8-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="3aeb8-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="3aeb8-111">PART_Indicator</span><span class="sxs-lookup"><span data-stu-id="3aeb8-111">PART_Indicator</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="3aeb8-112">O objeto que indica o andamento.</span><span class="sxs-lookup"><span data-stu-id="3aeb8-112">The object that indicates progress.</span></span>|  
|<span data-ttu-id="3aeb8-113">PART_Track</span><span class="sxs-lookup"><span data-stu-id="3aeb8-113">PART_Track</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="3aeb8-114">O objeto que define o caminho do indicador de progresso.</span><span class="sxs-lookup"><span data-stu-id="3aeb8-114">The object that defines the path of the progress indicator.</span></span>|  
|<span data-ttu-id="3aeb8-115">PART_GlowRect</span><span class="sxs-lookup"><span data-stu-id="3aeb8-115">PART_GlowRect</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="3aeb8-116">Um objeto que embellishes a barra de progresso.</span><span class="sxs-lookup"><span data-stu-id="3aeb8-116">An object that embellishes the progress bar.</span></span>|  
  
## <a name="progressbar-states"></a><span data-ttu-id="3aeb8-117">Estados de ProgressBar</span><span class="sxs-lookup"><span data-stu-id="3aeb8-117">ProgressBar States</span></span>  
 <span data-ttu-id="3aeb8-118">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.ProgressBar> controle.</span><span class="sxs-lookup"><span data-stu-id="3aeb8-118">The following table lists the visual states for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="3aeb8-119">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="3aeb8-119">VisualState Name</span></span>|<span data-ttu-id="3aeb8-120">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="3aeb8-120">VisualStateGroup Name</span></span>|<span data-ttu-id="3aeb8-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="3aeb8-121">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="3aeb8-122">Determinada</span><span class="sxs-lookup"><span data-stu-id="3aeb8-122">Determinate</span></span>|<span data-ttu-id="3aeb8-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="3aeb8-123">CommonStates</span></span>|<xref:System.Windows.Controls.ProgressBar> <span data-ttu-id="3aeb8-124">relata o progresso com base no <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="3aeb8-124">reports progress based on the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property.</span></span>|  
|<span data-ttu-id="3aeb8-125">Indeterminado</span><span class="sxs-lookup"><span data-stu-id="3aeb8-125">Indeterminate</span></span>|<span data-ttu-id="3aeb8-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="3aeb8-126">CommonStates</span></span>|<xref:System.Windows.Controls.ProgressBar> <span data-ttu-id="3aeb8-127">relata o andamento genérico com um padrão de repetição.</span><span class="sxs-lookup"><span data-stu-id="3aeb8-127">reports generic progress with a repeating pattern.</span></span>|  
|<span data-ttu-id="3aeb8-128">Válido</span><span class="sxs-lookup"><span data-stu-id="3aeb8-128">Valid</span></span>|<span data-ttu-id="3aeb8-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3aeb8-129">ValidationStates</span></span>|<span data-ttu-id="3aeb8-130">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="3aeb8-130">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="3aeb8-131">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="3aeb8-131">InvalidFocused</span></span>|<span data-ttu-id="3aeb8-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3aeb8-132">ValidationStates</span></span>|<span data-ttu-id="3aeb8-133">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="3aeb8-133">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="3aeb8-134">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="3aeb8-134">InvalidUnfocused</span></span>|<span data-ttu-id="3aeb8-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3aeb8-135">ValidationStates</span></span>|<span data-ttu-id="3aeb8-136">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle não tem o foco.</span><span class="sxs-lookup"><span data-stu-id="3aeb8-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="progressbar-controltemplate-example"></a><span data-ttu-id="3aeb8-137">Exemplo de ControlTemplate ProgressBar</span><span class="sxs-lookup"><span data-stu-id="3aeb8-137">ProgressBar ControlTemplate Example</span></span>  
 <span data-ttu-id="3aeb8-138">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.ProgressBar> controle.</span><span class="sxs-lookup"><span data-stu-id="3aeb8-138">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ProgressBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
 <span data-ttu-id="3aeb8-139">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="3aeb8-139">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="3aeb8-140">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="3aeb8-140">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3aeb8-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3aeb8-141">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="3aeb8-142">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="3aeb8-142">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="3aeb8-143">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="3aeb8-143">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="3aeb8-144">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="3aeb8-144">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="3aeb8-145">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="3aeb8-145">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
