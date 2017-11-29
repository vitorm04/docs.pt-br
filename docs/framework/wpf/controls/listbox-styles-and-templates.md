---
title: Estilos e modelos ListBox
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- styles [WPF], ListBox
- templates [WPF], ListBox
- states [WPF], ListBox
- ControlTemplate [WPF], ListBox
- parts [WPF], ListBox
- ListBox [WPF], styles and templates
ms.assetid: fc5764cb-c27b-495b-88d4-d969a8213ccb
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: df974b2f6f89c3b62c5039be9cde144d9ef62d14
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="listbox-styles-and-templates"></a><span data-ttu-id="459cf-102">Estilos e modelos ListBox</span><span class="sxs-lookup"><span data-stu-id="459cf-102">ListBox Styles and Templates</span></span>
<span data-ttu-id="459cf-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.ListBox> controle.</span><span class="sxs-lookup"><span data-stu-id="459cf-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ListBox> control.</span></span> <span data-ttu-id="459cf-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para que o controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="459cf-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="459cf-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="459cf-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="listbox-parts"></a><span data-ttu-id="459cf-106">Partes da caixa de listagem</span><span class="sxs-lookup"><span data-stu-id="459cf-106">ListBox Parts</span></span>  
 <span data-ttu-id="459cf-107">O <xref:System.Windows.Controls.ListBox> controle não tem as partes nomeadas.</span><span class="sxs-lookup"><span data-stu-id="459cf-107">The <xref:System.Windows.Controls.ListBox> control does not have any named parts.</span></span>  
  
 <span data-ttu-id="459cf-108">Quando você cria um <xref:System.Windows.Controls.ControlTemplate> para um <xref:System.Windows.Controls.ListBox>, o modelo pode conter um <xref:System.Windows.Controls.ItemsPresenter> dentro de um <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="459cf-108">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ListBox>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="459cf-109">(O <xref:System.Windows.Controls.ItemsPresenter> exibe cada item de <xref:System.Windows.Controls.ListBox>; o <xref:System.Windows.Controls.ScrollViewer> habilita a rolagem dentro do controle).</span><span class="sxs-lookup"><span data-stu-id="459cf-109">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ListBox>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="459cf-110">Se o <xref:System.Windows.Controls.ItemsPresenter> não é filho direto do <xref:System.Windows.Controls.ScrollViewer>, você deve fornecer o <xref:System.Windows.Controls.ItemsPresenter> o nome `ItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="459cf-110">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="listbox-states"></a><span data-ttu-id="459cf-111">Estados de caixa de listagem</span><span class="sxs-lookup"><span data-stu-id="459cf-111">ListBox States</span></span>  
 <span data-ttu-id="459cf-112">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.ListBox> controle.</span><span class="sxs-lookup"><span data-stu-id="459cf-112">The following table lists the visual states for the <xref:System.Windows.Controls.ListBox> control.</span></span>  
  
|<span data-ttu-id="459cf-113">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="459cf-113">VisualState Name</span></span>|<span data-ttu-id="459cf-114">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="459cf-114">VisualStateGroup Name</span></span>|<span data-ttu-id="459cf-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="459cf-115">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="459cf-116">Válido</span><span class="sxs-lookup"><span data-stu-id="459cf-116">Valid</span></span>|<span data-ttu-id="459cf-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="459cf-117">ValidationStates</span></span>|<span data-ttu-id="459cf-118">O controle é válido.</span><span class="sxs-lookup"><span data-stu-id="459cf-118">The control is valid.</span></span>|  
|<span data-ttu-id="459cf-119">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="459cf-119">InvalidFocused</span></span>|<span data-ttu-id="459cf-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="459cf-120">ValidationStates</span></span>|<span data-ttu-id="459cf-121">O controle não é válido e tem o foco.</span><span class="sxs-lookup"><span data-stu-id="459cf-121">The control is not valid and has focus.</span></span>|  
|<span data-ttu-id="459cf-122">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="459cf-122">InvalidUnfocused</span></span>|<span data-ttu-id="459cf-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="459cf-123">ValidationStates</span></span>|<span data-ttu-id="459cf-124">O controle não é válido e não tem o foco.</span><span class="sxs-lookup"><span data-stu-id="459cf-124">The control is not valid and does not have focus.</span></span>|  
  
## <a name="listboxitem-parts"></a><span data-ttu-id="459cf-125">Partes de ListBoxItem</span><span class="sxs-lookup"><span data-stu-id="459cf-125">ListBoxItem Parts</span></span>  
 <span data-ttu-id="459cf-126">O <xref:System.Windows.Controls.ListBoxItem> controle não tem as partes nomeadas.</span><span class="sxs-lookup"><span data-stu-id="459cf-126">The <xref:System.Windows.Controls.ListBoxItem> control does not have any named parts.</span></span>  
  
## <a name="listboxitem-states"></a><span data-ttu-id="459cf-127">Estados de ListBoxItem</span><span class="sxs-lookup"><span data-stu-id="459cf-127">ListBoxItem States</span></span>  
 <span data-ttu-id="459cf-128">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.ListBox> controle.</span><span class="sxs-lookup"><span data-stu-id="459cf-128">The following table lists the visual states for the <xref:System.Windows.Controls.ListBox> control.</span></span>  
  
|<span data-ttu-id="459cf-129">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="459cf-129">VisualState Name</span></span>|<span data-ttu-id="459cf-130">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="459cf-130">VisualStateGroup Name</span></span>|<span data-ttu-id="459cf-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="459cf-131">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="459cf-132">Normal</span><span class="sxs-lookup"><span data-stu-id="459cf-132">Normal</span></span>|<span data-ttu-id="459cf-133">CommonStates</span><span class="sxs-lookup"><span data-stu-id="459cf-133">CommonStates</span></span>|<span data-ttu-id="459cf-134">O estado padrão.</span><span class="sxs-lookup"><span data-stu-id="459cf-134">The default state.</span></span>|  
|<span data-ttu-id="459cf-135">MouseOver</span><span class="sxs-lookup"><span data-stu-id="459cf-135">MouseOver</span></span>|<span data-ttu-id="459cf-136">CommonStates</span><span class="sxs-lookup"><span data-stu-id="459cf-136">CommonStates</span></span>|<span data-ttu-id="459cf-137">O ponteiro do mouse é posicionado sobre o controle.</span><span class="sxs-lookup"><span data-stu-id="459cf-137">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="459cf-138">Disabled</span><span class="sxs-lookup"><span data-stu-id="459cf-138">Disabled</span></span>|<span data-ttu-id="459cf-139">CommonStates</span><span class="sxs-lookup"><span data-stu-id="459cf-139">CommonStates</span></span>|<span data-ttu-id="459cf-140">O item está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="459cf-140">The item is disabled.</span></span>|  
|<span data-ttu-id="459cf-141">Focalizado</span><span class="sxs-lookup"><span data-stu-id="459cf-141">Focused</span></span>|<span data-ttu-id="459cf-142">FocusStates</span><span class="sxs-lookup"><span data-stu-id="459cf-142">FocusStates</span></span>|<span data-ttu-id="459cf-143">O item tem o foco.</span><span class="sxs-lookup"><span data-stu-id="459cf-143">The item has focus.</span></span>|  
|<span data-ttu-id="459cf-144">Sem foco</span><span class="sxs-lookup"><span data-stu-id="459cf-144">Unfocused</span></span>|<span data-ttu-id="459cf-145">FocusStates</span><span class="sxs-lookup"><span data-stu-id="459cf-145">FocusStates</span></span>|<span data-ttu-id="459cf-146">O item não tem foco.</span><span class="sxs-lookup"><span data-stu-id="459cf-146">The item does not have focus.</span></span>|  
|<span data-ttu-id="459cf-147">Não selecionado</span><span class="sxs-lookup"><span data-stu-id="459cf-147">Unselected</span></span>|<span data-ttu-id="459cf-148">SelectionStates</span><span class="sxs-lookup"><span data-stu-id="459cf-148">SelectionStates</span></span>|<span data-ttu-id="459cf-149">O item não está selecionado.</span><span class="sxs-lookup"><span data-stu-id="459cf-149">The item is not selected.</span></span>|  
|<span data-ttu-id="459cf-150">Selecionado</span><span class="sxs-lookup"><span data-stu-id="459cf-150">Selected</span></span>|<span data-ttu-id="459cf-151">SelectionStates</span><span class="sxs-lookup"><span data-stu-id="459cf-151">SelectionStates</span></span>|<span data-ttu-id="459cf-152">O item é currentlyplate selecionado.</span><span class="sxs-lookup"><span data-stu-id="459cf-152">The item is currentlyplate selected.</span></span>|  
|<span data-ttu-id="459cf-153">SelectedUnfocused</span><span class="sxs-lookup"><span data-stu-id="459cf-153">SelectedUnfocused</span></span>|<span data-ttu-id="459cf-154">SelectionStates</span><span class="sxs-lookup"><span data-stu-id="459cf-154">SelectionStates</span></span>|<span data-ttu-id="459cf-155">O item está selecionado, mas não tem o foco.</span><span class="sxs-lookup"><span data-stu-id="459cf-155">The item is selected, but does not have focus.</span></span>|  
|<span data-ttu-id="459cf-156">Válido</span><span class="sxs-lookup"><span data-stu-id="459cf-156">Valid</span></span>|<span data-ttu-id="459cf-157">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="459cf-157">ValidationStates</span></span>|<span data-ttu-id="459cf-158">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="459cf-158">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="459cf-159">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="459cf-159">InvalidFocused</span></span>|<span data-ttu-id="459cf-160">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="459cf-160">ValidationStates</span></span>|<span data-ttu-id="459cf-161">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="459cf-161">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="459cf-162">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="459cf-162">InvalidUnfocused</span></span>|<span data-ttu-id="459cf-163">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="459cf-163">ValidationStates</span></span>|<span data-ttu-id="459cf-164">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="459cf-164">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="listbox-controltemplate-example"></a><span data-ttu-id="459cf-165">Exemplo de ControlTemplate ListBox</span><span class="sxs-lookup"><span data-stu-id="459cf-165">ListBox ControlTemplate Example</span></span>  
 <span data-ttu-id="459cf-166">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.ListBox> e <xref:System.Windows.Controls.ListBoxItem> controles.</span><span class="sxs-lookup"><span data-stu-id="459cf-166">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ListBox> and <xref:System.Windows.Controls.ListBoxItem> controls.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ListBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/listbox.xaml#listbox)]  
  
 <span data-ttu-id="459cf-167">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="459cf-167">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="459cf-168">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="459cf-168">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="459cf-169">Consulte também</span><span class="sxs-lookup"><span data-stu-id="459cf-169">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="459cf-170">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="459cf-170">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="459cf-171">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="459cf-171">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="459cf-172">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="459cf-172">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="459cf-173">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="459cf-173">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
