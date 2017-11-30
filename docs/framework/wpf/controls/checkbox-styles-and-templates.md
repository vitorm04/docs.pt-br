---
title: Estilos e modelos CheckBox
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [WPF], CheckBox
- templates [WPF], CheckBox
- parts [WPF], CheckBox
- ControlTemplate [WPF], CheckBox
- CheckBox [WPF], styles and templates
- styles [WPF], CheckBox
ms.assetid: bfdaec96-d101-4d3d-864d-c27e6b621d03
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9c901d710e96cd111104b9fef2219b157377adc3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="checkbox-styles-and-templates"></a><span data-ttu-id="cdb05-102">Estilos e modelos CheckBox</span><span class="sxs-lookup"><span data-stu-id="cdb05-102">CheckBox Styles and Templates</span></span>
<span data-ttu-id="cdb05-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.CheckBox> controle.</span><span class="sxs-lookup"><span data-stu-id="cdb05-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.CheckBox> control.</span></span> <span data-ttu-id="cdb05-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para que o controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="cdb05-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="cdb05-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="cdb05-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="checkbox-parts"></a><span data-ttu-id="cdb05-106">Partes de CheckBox</span><span class="sxs-lookup"><span data-stu-id="cdb05-106">CheckBox Parts</span></span>  
 <span data-ttu-id="cdb05-107">O <xref:System.Windows.Controls.CheckBox> controle não tem as partes nomeadas.</span><span class="sxs-lookup"><span data-stu-id="cdb05-107">The <xref:System.Windows.Controls.CheckBox> control does not have any named parts.</span></span>  
  
## <a name="checkbox-states"></a><span data-ttu-id="cdb05-108">Estados de CheckBox</span><span class="sxs-lookup"><span data-stu-id="cdb05-108">CheckBox States</span></span>  
 <span data-ttu-id="cdb05-109">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.CheckBox> controle.</span><span class="sxs-lookup"><span data-stu-id="cdb05-109">The following table lists the visual states for the <xref:System.Windows.Controls.CheckBox> control.</span></span>  
  
|<span data-ttu-id="cdb05-110">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="cdb05-110">VisualState Name</span></span>|<span data-ttu-id="cdb05-111">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="cdb05-111">VisualStateGroup Name</span></span>|<span data-ttu-id="cdb05-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="cdb05-112">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="cdb05-113">Normal</span><span class="sxs-lookup"><span data-stu-id="cdb05-113">Normal</span></span>|<span data-ttu-id="cdb05-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="cdb05-114">CommonStates</span></span>|<span data-ttu-id="cdb05-115">O estado padrão.</span><span class="sxs-lookup"><span data-stu-id="cdb05-115">The default state.</span></span>|  
|<span data-ttu-id="cdb05-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="cdb05-116">MouseOver</span></span>|<span data-ttu-id="cdb05-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="cdb05-117">CommonStates</span></span>|<span data-ttu-id="cdb05-118">O ponteiro do mouse é posicionado sobre o controle.</span><span class="sxs-lookup"><span data-stu-id="cdb05-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="cdb05-119">Pressionado</span><span class="sxs-lookup"><span data-stu-id="cdb05-119">Pressed</span></span>|<span data-ttu-id="cdb05-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="cdb05-120">CommonStates</span></span>|<span data-ttu-id="cdb05-121">O controle é pressionado.</span><span class="sxs-lookup"><span data-stu-id="cdb05-121">The control is pressed.</span></span>|  
|<span data-ttu-id="cdb05-122">Disabled</span><span class="sxs-lookup"><span data-stu-id="cdb05-122">Disabled</span></span>|<span data-ttu-id="cdb05-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="cdb05-123">CommonStates</span></span>|<span data-ttu-id="cdb05-124">O controle está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="cdb05-124">The control is disabled.</span></span>|  
|<span data-ttu-id="cdb05-125">Focalizado</span><span class="sxs-lookup"><span data-stu-id="cdb05-125">Focused</span></span>|<span data-ttu-id="cdb05-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="cdb05-126">FocusStates</span></span>|<span data-ttu-id="cdb05-127">O controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="cdb05-127">The control has focus.</span></span>|  
|<span data-ttu-id="cdb05-128">Sem foco</span><span class="sxs-lookup"><span data-stu-id="cdb05-128">Unfocused</span></span>|<span data-ttu-id="cdb05-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="cdb05-129">FocusStates</span></span>|<span data-ttu-id="cdb05-130">O controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="cdb05-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="cdb05-131">Selecionado</span><span class="sxs-lookup"><span data-stu-id="cdb05-131">Checked</span></span>|<span data-ttu-id="cdb05-132">CheckStates</span><span class="sxs-lookup"><span data-stu-id="cdb05-132">CheckStates</span></span>|<span data-ttu-id="cdb05-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> é `true`.</span><span class="sxs-lookup"><span data-stu-id="cdb05-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `true`.</span></span>|  
|<span data-ttu-id="cdb05-134">Não Selecionado</span><span class="sxs-lookup"><span data-stu-id="cdb05-134">Unchecked</span></span>|<span data-ttu-id="cdb05-135">CheckStates</span><span class="sxs-lookup"><span data-stu-id="cdb05-135">CheckStates</span></span>|<span data-ttu-id="cdb05-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> é `false`.</span><span class="sxs-lookup"><span data-stu-id="cdb05-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `false`.</span></span>|  
|<span data-ttu-id="cdb05-137">Indeterminado</span><span class="sxs-lookup"><span data-stu-id="cdb05-137">Indeterminate</span></span>|<span data-ttu-id="cdb05-138">CheckStates</span><span class="sxs-lookup"><span data-stu-id="cdb05-138">CheckStates</span></span>|<span data-ttu-id="cdb05-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A>is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span><span class="sxs-lookup"><span data-stu-id="cdb05-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span></span>|  
|<span data-ttu-id="cdb05-140">Válido</span><span class="sxs-lookup"><span data-stu-id="cdb05-140">Valid</span></span>|<span data-ttu-id="cdb05-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="cdb05-141">ValidationStates</span></span>|<span data-ttu-id="cdb05-142">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="cdb05-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="cdb05-143">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="cdb05-143">InvalidUnfocused</span></span>|<span data-ttu-id="cdb05-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="cdb05-144">ValidationStates</span></span>|<span data-ttu-id="cdb05-145">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="cdb05-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="cdb05-146">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="cdb05-146">InvalidFocused</span></span>|<span data-ttu-id="cdb05-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="cdb05-147">ValidationStates</span></span>|<span data-ttu-id="cdb05-148">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="cdb05-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="checkbox-controltemplate-example"></a><span data-ttu-id="cdb05-149">Exemplo de ControlTemplate de CheckBox</span><span class="sxs-lookup"><span data-stu-id="cdb05-149">CheckBox ControlTemplate Example</span></span>  
 <span data-ttu-id="cdb05-150">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.CheckBox> controle.</span><span class="sxs-lookup"><span data-stu-id="cdb05-150">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.CheckBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#CheckBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/checkbox.xaml#checkbox)]  
  
 <span data-ttu-id="cdb05-151">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="cdb05-151">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="cdb05-152">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="cdb05-152">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdb05-153">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cdb05-153">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="cdb05-154">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="cdb05-154">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="cdb05-155">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="cdb05-155">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="cdb05-156">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="cdb05-156">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="cdb05-157">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="cdb05-157">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
