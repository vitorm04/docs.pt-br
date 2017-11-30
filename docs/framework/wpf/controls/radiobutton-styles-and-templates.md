---
title: Estilos e modelos RadioButton
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- styles [WPF], RadioButton
- RadioButton [WPF], styles and templates
- ControlTemplate [WPF], RadioButton
- states [WPF], RadioButton
- templates [WPF], RadioButton
- parts [WPF], RadioButton
ms.assetid: 9acf93f7-dd2f-4010-8ce0-1edd81c52ae2
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 384a587fe01fb69ff5d377f2aa34d03ff110880d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="radiobutton-styles-and-templates"></a><span data-ttu-id="02933-102">Estilos e modelos RadioButton</span><span class="sxs-lookup"><span data-stu-id="02933-102">RadioButton Styles and Templates</span></span>
<span data-ttu-id="02933-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.RadioButton> controle.</span><span class="sxs-lookup"><span data-stu-id="02933-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.RadioButton> control.</span></span> <span data-ttu-id="02933-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para que o controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="02933-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="02933-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="02933-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="radiobutton-parts"></a><span data-ttu-id="02933-106">Partes de RadioButton</span><span class="sxs-lookup"><span data-stu-id="02933-106">RadioButton Parts</span></span>  
 <span data-ttu-id="02933-107">O <xref:System.Windows.Controls.RadioButton> controle não tem as partes nomeadas.</span><span class="sxs-lookup"><span data-stu-id="02933-107">The <xref:System.Windows.Controls.RadioButton> control does not have any named parts.</span></span>  
  
## <a name="radiobutton-states"></a><span data-ttu-id="02933-108">Estados de botão de opção</span><span class="sxs-lookup"><span data-stu-id="02933-108">RadioButton States</span></span>  
 <span data-ttu-id="02933-109">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.RadioButton> controle.</span><span class="sxs-lookup"><span data-stu-id="02933-109">The following table lists the visual states for the <xref:System.Windows.Controls.RadioButton> control.</span></span>  
  
|<span data-ttu-id="02933-110">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="02933-110">VisualState Name</span></span>|<span data-ttu-id="02933-111">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="02933-111">VisualStateGroup Name</span></span>|<span data-ttu-id="02933-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="02933-112">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="02933-113">Normal</span><span class="sxs-lookup"><span data-stu-id="02933-113">Normal</span></span>|<span data-ttu-id="02933-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="02933-114">CommonStates</span></span>|<span data-ttu-id="02933-115">O estado padrão.</span><span class="sxs-lookup"><span data-stu-id="02933-115">The default state.</span></span>|  
|<span data-ttu-id="02933-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="02933-116">MouseOver</span></span>|<span data-ttu-id="02933-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="02933-117">CommonStates</span></span>|<span data-ttu-id="02933-118">O ponteiro do mouse é posicionado sobre o controle.</span><span class="sxs-lookup"><span data-stu-id="02933-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="02933-119">Pressionado</span><span class="sxs-lookup"><span data-stu-id="02933-119">Pressed</span></span>|<span data-ttu-id="02933-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="02933-120">CommonStates</span></span>|<span data-ttu-id="02933-121">O controle é pressionado.</span><span class="sxs-lookup"><span data-stu-id="02933-121">The control is pressed.</span></span>|  
|<span data-ttu-id="02933-122">Disabled</span><span class="sxs-lookup"><span data-stu-id="02933-122">Disabled</span></span>|<span data-ttu-id="02933-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="02933-123">CommonStates</span></span>|<span data-ttu-id="02933-124">O controle está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="02933-124">The control is disabled.</span></span>|  
|<span data-ttu-id="02933-125">Focalizado</span><span class="sxs-lookup"><span data-stu-id="02933-125">Focused</span></span>|<span data-ttu-id="02933-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="02933-126">FocusStates</span></span>|<span data-ttu-id="02933-127">O controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="02933-127">The control has focus.</span></span>|  
|<span data-ttu-id="02933-128">Sem foco</span><span class="sxs-lookup"><span data-stu-id="02933-128">Unfocused</span></span>|<span data-ttu-id="02933-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="02933-129">FocusStates</span></span>|<span data-ttu-id="02933-130">O controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="02933-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="02933-131">Selecionado</span><span class="sxs-lookup"><span data-stu-id="02933-131">Checked</span></span>|<span data-ttu-id="02933-132">CheckStates</span><span class="sxs-lookup"><span data-stu-id="02933-132">CheckStates</span></span>|<span data-ttu-id="02933-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> é `true`.</span><span class="sxs-lookup"><span data-stu-id="02933-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `true`.</span></span>|  
|<span data-ttu-id="02933-134">Não Selecionado</span><span class="sxs-lookup"><span data-stu-id="02933-134">Unchecked</span></span>|<span data-ttu-id="02933-135">CheckStates</span><span class="sxs-lookup"><span data-stu-id="02933-135">CheckStates</span></span>|<span data-ttu-id="02933-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> é `false`.</span><span class="sxs-lookup"><span data-stu-id="02933-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `false`.</span></span>|  
|<span data-ttu-id="02933-137">Indeterminado</span><span class="sxs-lookup"><span data-stu-id="02933-137">Indeterminate</span></span>|<span data-ttu-id="02933-138">CheckStates</span><span class="sxs-lookup"><span data-stu-id="02933-138">CheckStates</span></span>|<span data-ttu-id="02933-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A>is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span><span class="sxs-lookup"><span data-stu-id="02933-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span></span>|  
|<span data-ttu-id="02933-140">Válido</span><span class="sxs-lookup"><span data-stu-id="02933-140">Valid</span></span>|<span data-ttu-id="02933-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="02933-141">ValidationStates</span></span>|<span data-ttu-id="02933-142">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="02933-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="02933-143">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="02933-143">InvalidFocused</span></span>|<span data-ttu-id="02933-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="02933-144">ValidationStates</span></span>|<span data-ttu-id="02933-145">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="02933-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="02933-146">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="02933-146">InvalidUnfocused</span></span>|<span data-ttu-id="02933-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="02933-147">ValidationStates</span></span>|<span data-ttu-id="02933-148">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="02933-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="radiobutton-controltemplate-example"></a><span data-ttu-id="02933-149">Exemplo de ControlTemplate de RadioButton</span><span class="sxs-lookup"><span data-stu-id="02933-149">RadioButton ControlTemplate Example</span></span>  
 <span data-ttu-id="02933-150">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.RadioButton> controle.</span><span class="sxs-lookup"><span data-stu-id="02933-150">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.RadioButton> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#RadioButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/radiobutton.xaml#radiobutton)]  
  
 <span data-ttu-id="02933-151">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="02933-151">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="02933-152">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="02933-152">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02933-153">Consulte também</span><span class="sxs-lookup"><span data-stu-id="02933-153">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="02933-154">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="02933-154">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="02933-155">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="02933-155">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="02933-156">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="02933-156">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="02933-157">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="02933-157">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
