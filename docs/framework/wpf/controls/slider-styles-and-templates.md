---
title: Estilos e modelos de controle deslizante
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], Slider
- states [WPF], Slider
- Slider [WPF], styles and templates
- styles [WPF], Slider
- templates [WPF], Slider
- ControlTemplate [WPF], Slider
ms.assetid: d89aa97b-075a-4752-9c41-9679df65c491
ms.openlocfilehash: 334cb4a44788980262110eadac3305283bb61a92
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458398"
---
# <a name="slider-styles-and-templates"></a><span data-ttu-id="39bd2-102">Estilos e modelos de controle deslizante</span><span class="sxs-lookup"><span data-stu-id="39bd2-102">Slider Styles and Templates</span></span>
<span data-ttu-id="39bd2-103">Este tópico descreve os estilos e modelos para o controle de <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="39bd2-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Slider> control.</span></span> <span data-ttu-id="39bd2-104">Você pode modificar o <xref:System.Windows.Controls.ControlTemplate> padrão para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="39bd2-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="39bd2-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="39bd2-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="slider-parts"></a><span data-ttu-id="39bd2-106">Partes do controle deslizante</span><span class="sxs-lookup"><span data-stu-id="39bd2-106">Slider Parts</span></span>  
 <span data-ttu-id="39bd2-107">A tabela a seguir lista as partes nomeadas para o controle de <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="39bd2-107">The following table lists the named parts for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="39bd2-108">Parte</span><span class="sxs-lookup"><span data-stu-id="39bd2-108">Part</span></span>|<span data-ttu-id="39bd2-109">Digite</span><span class="sxs-lookup"><span data-stu-id="39bd2-109">Type</span></span>|<span data-ttu-id="39bd2-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="39bd2-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="39bd2-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="39bd2-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="39bd2-112">O contêiner para o elemento que indica a posição do <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="39bd2-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Slider>.</span></span>|  
|<span data-ttu-id="39bd2-113">PART_SelectionRange</span><span class="sxs-lookup"><span data-stu-id="39bd2-113">PART_SelectionRange</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="39bd2-114">O elemento que exibe um intervalo de seleção ao longo do <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="39bd2-114">The element that displays a selection range along the <xref:System.Windows.Controls.Slider>.</span></span>  <span data-ttu-id="39bd2-115">O intervalo de seleção só será visível se a propriedade <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> for `true`.</span><span class="sxs-lookup"><span data-stu-id="39bd2-115">The selection range is visible only if the <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> property is `true`.</span></span>|  
  
## <a name="slider-states"></a><span data-ttu-id="39bd2-116">Estados do controle deslizante</span><span class="sxs-lookup"><span data-stu-id="39bd2-116">Slider States</span></span>  
 <span data-ttu-id="39bd2-117">A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="39bd2-117">The following table lists the visual states for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="39bd2-118">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="39bd2-118">VisualState Name</span></span>|<span data-ttu-id="39bd2-119">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="39bd2-119">VisualStateGroup Name</span></span>|<span data-ttu-id="39bd2-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="39bd2-120">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="39bd2-121">Normal</span><span class="sxs-lookup"><span data-stu-id="39bd2-121">Normal</span></span>|<span data-ttu-id="39bd2-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="39bd2-122">CommonStates</span></span>|<span data-ttu-id="39bd2-123">O estado padrão.</span><span class="sxs-lookup"><span data-stu-id="39bd2-123">The default state.</span></span>|  
|<span data-ttu-id="39bd2-124">MouseOver</span><span class="sxs-lookup"><span data-stu-id="39bd2-124">MouseOver</span></span>|<span data-ttu-id="39bd2-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="39bd2-125">CommonStates</span></span>|<span data-ttu-id="39bd2-126">O ponteiro do mouse é posicionado sobre o controle.</span><span class="sxs-lookup"><span data-stu-id="39bd2-126">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="39bd2-127">Disabled</span><span class="sxs-lookup"><span data-stu-id="39bd2-127">Disabled</span></span>|<span data-ttu-id="39bd2-128">CommonStates</span><span class="sxs-lookup"><span data-stu-id="39bd2-128">CommonStates</span></span>|<span data-ttu-id="39bd2-129">O controle está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="39bd2-129">The control is disabled.</span></span>|  
|<span data-ttu-id="39bd2-130">Focalizado</span><span class="sxs-lookup"><span data-stu-id="39bd2-130">Focused</span></span>|<span data-ttu-id="39bd2-131">FocusStates</span><span class="sxs-lookup"><span data-stu-id="39bd2-131">FocusStates</span></span>|<span data-ttu-id="39bd2-132">O controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="39bd2-132">The control has focus.</span></span>|  
|<span data-ttu-id="39bd2-133">Sem foco</span><span class="sxs-lookup"><span data-stu-id="39bd2-133">Unfocused</span></span>|<span data-ttu-id="39bd2-134">FocusStates</span><span class="sxs-lookup"><span data-stu-id="39bd2-134">FocusStates</span></span>|<span data-ttu-id="39bd2-135">O controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="39bd2-135">The control does not have focus.</span></span>|  
|<span data-ttu-id="39bd2-136">Válido</span><span class="sxs-lookup"><span data-stu-id="39bd2-136">Valid</span></span>|<span data-ttu-id="39bd2-137">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="39bd2-137">ValidationStates</span></span>|<span data-ttu-id="39bd2-138">O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.</span><span class="sxs-lookup"><span data-stu-id="39bd2-138">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="39bd2-139">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="39bd2-139">InvalidFocused</span></span>|<span data-ttu-id="39bd2-140">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="39bd2-140">ValidationStates</span></span>|<span data-ttu-id="39bd2-141">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.</span><span class="sxs-lookup"><span data-stu-id="39bd2-141">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="39bd2-142">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="39bd2-142">InvalidUnfocused</span></span>|<span data-ttu-id="39bd2-143">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="39bd2-143">ValidationStates</span></span>|<span data-ttu-id="39bd2-144">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="39bd2-144">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="slider-controltemplate-example"></a><span data-ttu-id="39bd2-145">Exemplo de ControlTemplate de Slider</span><span class="sxs-lookup"><span data-stu-id="39bd2-145">Slider ControlTemplate Example</span></span>  
 <span data-ttu-id="39bd2-146">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o controle de <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="39bd2-146">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Slider](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#slider)]  
  
 <span data-ttu-id="39bd2-147">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="39bd2-147">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="39bd2-148">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="39bd2-148">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39bd2-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="39bd2-149">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="39bd2-150">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="39bd2-150">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="39bd2-151">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="39bd2-151">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="39bd2-152">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="39bd2-152">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="39bd2-153">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="39bd2-153">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
