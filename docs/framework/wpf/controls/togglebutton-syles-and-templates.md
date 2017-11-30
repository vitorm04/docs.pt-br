---
title: Estilos e modelos ToggleButton
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [WPF], ToggleButton
- ToggleButton [WPF], styles and templates
- ControlTemplate [WPF], ToggleButton
- styles [WPF], ToggleButton
- templates [WPF], ToggleButton
- parts [WPF], ToggleButton
ms.assetid: 54f23f30-4bcb-4f09-8ce4-376a13a255a1
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ecd6696ff9d62b4aa3397ac8567edc3fb387ba96
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="togglebutton-syles-and-templates"></a><span data-ttu-id="21d1b-102">Estilos e modelos ToggleButton</span><span class="sxs-lookup"><span data-stu-id="21d1b-102">ToggleButton Syles and Templates</span></span>
<span data-ttu-id="21d1b-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.Primitives.ToggleButton> controle.</span><span class="sxs-lookup"><span data-stu-id="21d1b-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span> <span data-ttu-id="21d1b-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para que o controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="21d1b-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="21d1b-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="21d1b-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="togglebutton-parts"></a><span data-ttu-id="21d1b-106">ToggleButton partes</span><span class="sxs-lookup"><span data-stu-id="21d1b-106">ToggleButton Parts</span></span>  
 <span data-ttu-id="21d1b-107">O <xref:System.Windows.Controls.Primitives.ToggleButton> controle não tem as partes nomeadas.</span><span class="sxs-lookup"><span data-stu-id="21d1b-107">The <xref:System.Windows.Controls.Primitives.ToggleButton> control does not have any named parts.</span></span>  
  
## <a name="togglebutton-states"></a><span data-ttu-id="21d1b-108">Estados de ToggleButton</span><span class="sxs-lookup"><span data-stu-id="21d1b-108">ToggleButton States</span></span>  
 <span data-ttu-id="21d1b-109">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.Primitives.ToggleButton> controle.</span><span class="sxs-lookup"><span data-stu-id="21d1b-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>  
  
|<span data-ttu-id="21d1b-110">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="21d1b-110">VisualState Name</span></span>|<span data-ttu-id="21d1b-111">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="21d1b-111">VisualStateGroup Name</span></span>|<span data-ttu-id="21d1b-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="21d1b-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="21d1b-113">Normal</span><span class="sxs-lookup"><span data-stu-id="21d1b-113">Normal</span></span>|<span data-ttu-id="21d1b-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="21d1b-114">CommonStates</span></span>|<span data-ttu-id="21d1b-115">O estado padrão.</span><span class="sxs-lookup"><span data-stu-id="21d1b-115">The default state.</span></span>|  
|<span data-ttu-id="21d1b-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="21d1b-116">MouseOver</span></span>|<span data-ttu-id="21d1b-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="21d1b-117">CommonStates</span></span>|<span data-ttu-id="21d1b-118">O ponteiro do mouse é posicionado sobre o controle.</span><span class="sxs-lookup"><span data-stu-id="21d1b-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="21d1b-119">Pressionado</span><span class="sxs-lookup"><span data-stu-id="21d1b-119">Pressed</span></span>|<span data-ttu-id="21d1b-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="21d1b-120">CommonStates</span></span>|<span data-ttu-id="21d1b-121">O controle é pressionado.</span><span class="sxs-lookup"><span data-stu-id="21d1b-121">The control is pressed.</span></span>|  
|<span data-ttu-id="21d1b-122">Disabled</span><span class="sxs-lookup"><span data-stu-id="21d1b-122">Disabled</span></span>|<span data-ttu-id="21d1b-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="21d1b-123">CommonStates</span></span>|<span data-ttu-id="21d1b-124">O controle está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="21d1b-124">The control is disabled.</span></span>|  
|<span data-ttu-id="21d1b-125">Focalizado</span><span class="sxs-lookup"><span data-stu-id="21d1b-125">Focused</span></span>|<span data-ttu-id="21d1b-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="21d1b-126">FocusStates</span></span>|<span data-ttu-id="21d1b-127">O controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="21d1b-127">The control has focus.</span></span>|  
|<span data-ttu-id="21d1b-128">Sem foco</span><span class="sxs-lookup"><span data-stu-id="21d1b-128">Unfocused</span></span>|<span data-ttu-id="21d1b-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="21d1b-129">FocusStates</span></span>|<span data-ttu-id="21d1b-130">O controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="21d1b-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="21d1b-131">Selecionado</span><span class="sxs-lookup"><span data-stu-id="21d1b-131">Checked</span></span>|<span data-ttu-id="21d1b-132">CheckStates</span><span class="sxs-lookup"><span data-stu-id="21d1b-132">CheckStates</span></span>|<span data-ttu-id="21d1b-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> é `true`.</span><span class="sxs-lookup"><span data-stu-id="21d1b-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `true`.</span></span>|  
|<span data-ttu-id="21d1b-134">Não Selecionado</span><span class="sxs-lookup"><span data-stu-id="21d1b-134">Unchecked</span></span>|<span data-ttu-id="21d1b-135">CheckStates</span><span class="sxs-lookup"><span data-stu-id="21d1b-135">CheckStates</span></span>|<span data-ttu-id="21d1b-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> é `false`.</span><span class="sxs-lookup"><span data-stu-id="21d1b-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `false`.</span></span>|  
|<span data-ttu-id="21d1b-137">Indeterminado</span><span class="sxs-lookup"><span data-stu-id="21d1b-137">Indeterminate</span></span>|<span data-ttu-id="21d1b-138">CheckStates</span><span class="sxs-lookup"><span data-stu-id="21d1b-138">CheckStates</span></span>|<span data-ttu-id="21d1b-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A>is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span><span class="sxs-lookup"><span data-stu-id="21d1b-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span></span>|  
|<span data-ttu-id="21d1b-140">Válido</span><span class="sxs-lookup"><span data-stu-id="21d1b-140">Valid</span></span>|<span data-ttu-id="21d1b-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="21d1b-141">ValidationStates</span></span>|<span data-ttu-id="21d1b-142">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="21d1b-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="21d1b-143">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="21d1b-143">InvalidFocused</span></span>|<span data-ttu-id="21d1b-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="21d1b-144">ValidationStates</span></span>|<span data-ttu-id="21d1b-145">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="21d1b-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="21d1b-146">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="21d1b-146">InvalidUnfocused</span></span>|<span data-ttu-id="21d1b-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="21d1b-147">ValidationStates</span></span>|<span data-ttu-id="21d1b-148">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="21d1b-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="21d1b-149">Se o estado visual indeterminado não existe no modelo de controle, em seguida, o estado visual desmarcado basearão estado visual padrão.</span><span class="sxs-lookup"><span data-stu-id="21d1b-149">If the Indeterminate visual state does not exist in your control template, then the Unchecked visual state will be used as default visual state.</span></span>  
  
## <a name="togglebutton-controltemplate-example"></a><span data-ttu-id="21d1b-150">Exemplo de ControlTemplate ToggleButton</span><span class="sxs-lookup"><span data-stu-id="21d1b-150">ToggleButton ControlTemplate Example</span></span>  
 <span data-ttu-id="21d1b-151">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.Primitives.ToggleButton> controle.</span><span class="sxs-lookup"><span data-stu-id="21d1b-151">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToggleButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#togglebutton)]  
  
 <span data-ttu-id="21d1b-152">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="21d1b-152">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="21d1b-153">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="21d1b-153">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21d1b-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="21d1b-154">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="21d1b-155">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="21d1b-155">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="21d1b-156">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="21d1b-156">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="21d1b-157">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="21d1b-157">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="21d1b-158">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="21d1b-158">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
