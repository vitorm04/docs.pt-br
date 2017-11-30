---
title: Estilos e modelos de controle deslizante
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parts [WPF], Slider
- states [WPF], Slider
- Slider [WPF], styles and templates
- styles [WPF], Slider
- templates [WPF], Slider
- ControlTemplate [WPF], Slider
ms.assetid: d89aa97b-075a-4752-9c41-9679df65c491
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9dfa340cf42e5e7ed105bf14eb0f7a24ea85a1b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="slider-styles-and-templates"></a><span data-ttu-id="f755f-102">Estilos e modelos de controle deslizante</span><span class="sxs-lookup"><span data-stu-id="f755f-102">Slider Styles and Templates</span></span>
<span data-ttu-id="f755f-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.Slider> controle.</span><span class="sxs-lookup"><span data-stu-id="f755f-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Slider> control.</span></span> <span data-ttu-id="f755f-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para que o controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="f755f-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="f755f-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="f755f-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="slider-parts"></a><span data-ttu-id="f755f-106">Partes do controle deslizante</span><span class="sxs-lookup"><span data-stu-id="f755f-106">Slider Parts</span></span>  
 <span data-ttu-id="f755f-107">A tabela a seguir lista as partes nomeadas para o <xref:System.Windows.Controls.Slider> controle.</span><span class="sxs-lookup"><span data-stu-id="f755f-107">The following table lists the named parts for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="f755f-108">Parte</span><span class="sxs-lookup"><span data-stu-id="f755f-108">Part</span></span>|<span data-ttu-id="f755f-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="f755f-109">Type</span></span>|<span data-ttu-id="f755f-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="f755f-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="f755f-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="f755f-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="f755f-112">O contêiner para o elemento que indica a posição do <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="f755f-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Slider>.</span></span>|  
|<span data-ttu-id="f755f-113">PART_SelectionRange</span><span class="sxs-lookup"><span data-stu-id="f755f-113">PART_SelectionRange</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="f755f-114">O elemento que exibe um intervalo de seleção junto a <xref:System.Windows.Controls.Slider>.</span><span class="sxs-lookup"><span data-stu-id="f755f-114">The element that displays a selection range along the <xref:System.Windows.Controls.Slider>.</span></span>  <span data-ttu-id="f755f-115">O intervalo de seleção é visível somente se o <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> é de propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="f755f-115">The selection range is visible only if the <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> property is `true`.</span></span>|  
  
## <a name="slider-states"></a><span data-ttu-id="f755f-116">Estados de controle deslizante</span><span class="sxs-lookup"><span data-stu-id="f755f-116">Slider States</span></span>  
 <span data-ttu-id="f755f-117">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.Slider> controle.</span><span class="sxs-lookup"><span data-stu-id="f755f-117">The following table lists the visual states for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
|<span data-ttu-id="f755f-118">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="f755f-118">VisualState Name</span></span>|<span data-ttu-id="f755f-119">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="f755f-119">VisualStateGroup Name</span></span>|<span data-ttu-id="f755f-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="f755f-120">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="f755f-121">Normal</span><span class="sxs-lookup"><span data-stu-id="f755f-121">Normal</span></span>|<span data-ttu-id="f755f-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f755f-122">CommonStates</span></span>|<span data-ttu-id="f755f-123">O estado padrão.</span><span class="sxs-lookup"><span data-stu-id="f755f-123">The default state.</span></span>|  
|<span data-ttu-id="f755f-124">MouseOver</span><span class="sxs-lookup"><span data-stu-id="f755f-124">MouseOver</span></span>|<span data-ttu-id="f755f-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f755f-125">CommonStates</span></span>|<span data-ttu-id="f755f-126">O ponteiro do mouse é posicionado sobre o controle.</span><span class="sxs-lookup"><span data-stu-id="f755f-126">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="f755f-127">Disabled</span><span class="sxs-lookup"><span data-stu-id="f755f-127">Disabled</span></span>|<span data-ttu-id="f755f-128">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f755f-128">CommonStates</span></span>|<span data-ttu-id="f755f-129">O controle está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="f755f-129">The control is disabled.</span></span>|  
|<span data-ttu-id="f755f-130">Focalizado</span><span class="sxs-lookup"><span data-stu-id="f755f-130">Focused</span></span>|<span data-ttu-id="f755f-131">FocusStates</span><span class="sxs-lookup"><span data-stu-id="f755f-131">FocusStates</span></span>|<span data-ttu-id="f755f-132">O controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="f755f-132">The control has focus.</span></span>|  
|<span data-ttu-id="f755f-133">Sem foco</span><span class="sxs-lookup"><span data-stu-id="f755f-133">Unfocused</span></span>|<span data-ttu-id="f755f-134">FocusStates</span><span class="sxs-lookup"><span data-stu-id="f755f-134">FocusStates</span></span>|<span data-ttu-id="f755f-135">O controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="f755f-135">The control does not have focus.</span></span>|  
|<span data-ttu-id="f755f-136">Válido</span><span class="sxs-lookup"><span data-stu-id="f755f-136">Valid</span></span>|<span data-ttu-id="f755f-137">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f755f-137">ValidationStates</span></span>|<span data-ttu-id="f755f-138">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="f755f-138">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="f755f-139">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="f755f-139">InvalidFocused</span></span>|<span data-ttu-id="f755f-140">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f755f-140">ValidationStates</span></span>|<span data-ttu-id="f755f-141">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="f755f-141">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="f755f-142">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="f755f-142">InvalidUnfocused</span></span>|<span data-ttu-id="f755f-143">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f755f-143">ValidationStates</span></span>|<span data-ttu-id="f755f-144">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="f755f-144">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="slider-controltemplate-example"></a><span data-ttu-id="f755f-145">Controle deslizante ControlTemplate exemplo</span><span class="sxs-lookup"><span data-stu-id="f755f-145">Slider ControlTemplate Example</span></span>  
 <span data-ttu-id="f755f-146">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.Slider> controle.</span><span class="sxs-lookup"><span data-stu-id="f755f-146">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Slider> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Slider](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#slider)]  
  
 <span data-ttu-id="f755f-147">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="f755f-147">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="f755f-148">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="f755f-148">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f755f-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f755f-149">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="f755f-150">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="f755f-150">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="f755f-151">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="f755f-151">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="f755f-152">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="f755f-152">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="f755f-153">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="f755f-153">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
