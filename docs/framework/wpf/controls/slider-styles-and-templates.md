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
ms.openlocfilehash: 8ec1f436ac0134ccdb19e63592c4181951814cb1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375669"
---
# <a name="slider-styles-and-templates"></a><span data-ttu-id="237e9-102">Estilos e modelos de controle deslizante</span><span class="sxs-lookup"><span data-stu-id="237e9-102">Slider Styles and Templates</span></span>
<span data-ttu-id="237e9-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.Slider> controle.</span><span class="sxs-lookup"><span data-stu-id="237e9-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Slider> control.</span></span> <span data-ttu-id="237e9-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="237e9-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="237e9-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="237e9-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="slider-parts"></a><span data-ttu-id="237e9-106">Partes do controle deslizante</span><span class="sxs-lookup"><span data-stu-id="237e9-106">Slider Parts</span></span>  
 <span data-ttu-id="237e9-107">A tabela a seguir lista as partes nomeadas para o <xref:System.Windows.Controls.Slider> controle.</span><span class="sxs-lookup"><span data-stu-id="237e9-107">The following table lists the named parts for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="237e9-108">Parte</span><span class="sxs-lookup"><span data-stu-id="237e9-108">Part</span></span>|<span data-ttu-id="237e9-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="237e9-109">Type</span></span>|<span data-ttu-id="237e9-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="237e9-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="237e9-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="237e9-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="237e9-112">O contêiner para o elemento que indica a posição do <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="237e9-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Slider>.</span></span>|  
|<span data-ttu-id="237e9-113">PART_SelectionRange</span><span class="sxs-lookup"><span data-stu-id="237e9-113">PART_SelectionRange</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="237e9-114">O elemento que exibe um intervalo de seleção junto a <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="237e9-114">The element that displays a selection range along the <xref:System.Windows.Controls.Slider>.</span></span>  <span data-ttu-id="237e9-115">O intervalo de seleção é visível somente se o <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> é de propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="237e9-115">The selection range is visible only if the <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> property is `true`.</span></span>|  
  
## <a name="slider-states"></a><span data-ttu-id="237e9-116">Estados do controle deslizante</span><span class="sxs-lookup"><span data-stu-id="237e9-116">Slider States</span></span>  
 <span data-ttu-id="237e9-117">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.Slider> controle.</span><span class="sxs-lookup"><span data-stu-id="237e9-117">The following table lists the visual states for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="237e9-118">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="237e9-118">VisualState Name</span></span>|<span data-ttu-id="237e9-119">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="237e9-119">VisualStateGroup Name</span></span>|<span data-ttu-id="237e9-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="237e9-120">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="237e9-121">Normal</span><span class="sxs-lookup"><span data-stu-id="237e9-121">Normal</span></span>|<span data-ttu-id="237e9-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="237e9-122">CommonStates</span></span>|<span data-ttu-id="237e9-123">O estado padrão.</span><span class="sxs-lookup"><span data-stu-id="237e9-123">The default state.</span></span>|  
|<span data-ttu-id="237e9-124">MouseOver</span><span class="sxs-lookup"><span data-stu-id="237e9-124">MouseOver</span></span>|<span data-ttu-id="237e9-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="237e9-125">CommonStates</span></span>|<span data-ttu-id="237e9-126">O ponteiro do mouse é posicionado sobre o controle.</span><span class="sxs-lookup"><span data-stu-id="237e9-126">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="237e9-127">Disabled</span><span class="sxs-lookup"><span data-stu-id="237e9-127">Disabled</span></span>|<span data-ttu-id="237e9-128">CommonStates</span><span class="sxs-lookup"><span data-stu-id="237e9-128">CommonStates</span></span>|<span data-ttu-id="237e9-129">O controle está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="237e9-129">The control is disabled.</span></span>|  
|<span data-ttu-id="237e9-130">Focalizado</span><span class="sxs-lookup"><span data-stu-id="237e9-130">Focused</span></span>|<span data-ttu-id="237e9-131">FocusStates</span><span class="sxs-lookup"><span data-stu-id="237e9-131">FocusStates</span></span>|<span data-ttu-id="237e9-132">O controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="237e9-132">The control has focus.</span></span>|  
|<span data-ttu-id="237e9-133">Sem foco</span><span class="sxs-lookup"><span data-stu-id="237e9-133">Unfocused</span></span>|<span data-ttu-id="237e9-134">FocusStates</span><span class="sxs-lookup"><span data-stu-id="237e9-134">FocusStates</span></span>|<span data-ttu-id="237e9-135">O controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="237e9-135">The control does not have focus.</span></span>|  
|<span data-ttu-id="237e9-136">Válido</span><span class="sxs-lookup"><span data-stu-id="237e9-136">Valid</span></span>|<span data-ttu-id="237e9-137">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="237e9-137">ValidationStates</span></span>|<span data-ttu-id="237e9-138">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="237e9-138">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="237e9-139">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="237e9-139">InvalidFocused</span></span>|<span data-ttu-id="237e9-140">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="237e9-140">ValidationStates</span></span>|<span data-ttu-id="237e9-141">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="237e9-141">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="237e9-142">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="237e9-142">InvalidUnfocused</span></span>|<span data-ttu-id="237e9-143">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="237e9-143">ValidationStates</span></span>|<span data-ttu-id="237e9-144">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle não tem o foco.</span><span class="sxs-lookup"><span data-stu-id="237e9-144">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="slider-controltemplate-example"></a><span data-ttu-id="237e9-145">Exemplo de ControlTemplate de controle deslizante</span><span class="sxs-lookup"><span data-stu-id="237e9-145">Slider ControlTemplate Example</span></span>  
 <span data-ttu-id="237e9-146">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.Slider> controle.</span><span class="sxs-lookup"><span data-stu-id="237e9-146">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Slider](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#slider)]  
  
 <span data-ttu-id="237e9-147">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="237e9-147">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="237e9-148">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="237e9-148">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="237e9-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="237e9-149">See also</span></span>
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="237e9-150">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="237e9-150">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="237e9-151">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="237e9-151">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="237e9-152">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="237e9-152">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="237e9-153">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="237e9-153">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
