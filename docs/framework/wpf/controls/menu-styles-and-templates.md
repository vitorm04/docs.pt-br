---
title: Estilos e modelos de menu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- styles [WPF], Menu
- ControlTemplate [WPF], Menu
- Menu [WPF], styles and templates
- states [WPF], Menu
- templates [WPF], Menu
- parts [WPF], Menu
ms.assetid: b89da183-9b87-42c6-ac53-731a42c7b09e
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1e007ae09e57353446feb13b3693e62c985f522d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="menu-styles-and-templates"></a><span data-ttu-id="a03dc-102">Estilos e modelos de menu</span><span class="sxs-lookup"><span data-stu-id="a03dc-102">Menu Styles and Templates</span></span>
<span data-ttu-id="a03dc-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.Menu> controle.</span><span class="sxs-lookup"><span data-stu-id="a03dc-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Menu> control.</span></span> <span data-ttu-id="a03dc-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para que o controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="a03dc-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="a03dc-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="a03dc-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="menu-parts"></a><span data-ttu-id="a03dc-106">Partes de menu</span><span class="sxs-lookup"><span data-stu-id="a03dc-106">Menu Parts</span></span>  
 <span data-ttu-id="a03dc-107">O <xref:System.Windows.Controls.Menu> controle não tem as partes nomeadas.</span><span class="sxs-lookup"><span data-stu-id="a03dc-107">The <xref:System.Windows.Controls.Menu> control does not have any named parts.</span></span>  
  
 <span data-ttu-id="a03dc-108">Quando você cria um <xref:System.Windows.Controls.ControlTemplate> para um <xref:System.Windows.Controls.Menu>, o modelo pode conter um <xref:System.Windows.Controls.ItemsPresenter> dentro de um <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="a03dc-108">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.Menu>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="a03dc-109">(O <xref:System.Windows.Controls.ItemsPresenter> exibe cada item de <xref:System.Windows.Controls.Menu>; o <xref:System.Windows.Controls.ScrollViewer> habilita a rolagem dentro do controle).</span><span class="sxs-lookup"><span data-stu-id="a03dc-109">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.Menu>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="a03dc-110">Se o <xref:System.Windows.Controls.ItemsPresenter> não é filho direto do <xref:System.Windows.Controls.ScrollViewer>, você deve fornecer o <xref:System.Windows.Controls.ItemsPresenter> o nome `ItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="a03dc-110">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="menu-states"></a><span data-ttu-id="a03dc-111">Estados de menu</span><span class="sxs-lookup"><span data-stu-id="a03dc-111">Menu States</span></span>  
 <span data-ttu-id="a03dc-112">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.Menu> controle.</span><span class="sxs-lookup"><span data-stu-id="a03dc-112">The following table lists the visual states for the <xref:System.Windows.Controls.Menu> control.</span></span>  
  
|<span data-ttu-id="a03dc-113">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="a03dc-113">VisualState Name</span></span>|<span data-ttu-id="a03dc-114">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="a03dc-114">VisualStateGroup Name</span></span>|<span data-ttu-id="a03dc-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="a03dc-115">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="a03dc-116">Válido</span><span class="sxs-lookup"><span data-stu-id="a03dc-116">Valid</span></span>|<span data-ttu-id="a03dc-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a03dc-117">ValidationStates</span></span>|<span data-ttu-id="a03dc-118">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="a03dc-118">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="a03dc-119">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="a03dc-119">InvalidFocused</span></span>|<span data-ttu-id="a03dc-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a03dc-120">ValidationStates</span></span>|<span data-ttu-id="a03dc-121">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="a03dc-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="a03dc-122">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="a03dc-122">InvalidUnfocused</span></span>|<span data-ttu-id="a03dc-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a03dc-123">ValidationStates</span></span>|<span data-ttu-id="a03dc-124">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="a03dc-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="menuitem-parts"></a><span data-ttu-id="a03dc-125">Partes de MenuItem</span><span class="sxs-lookup"><span data-stu-id="a03dc-125">MenuItem Parts</span></span>  
 <span data-ttu-id="a03dc-126">A tabela a seguir lista as partes nomeadas para o <xref:System.Windows.Controls.Menu> controle.</span><span class="sxs-lookup"><span data-stu-id="a03dc-126">The following table lists the named parts for the <xref:System.Windows.Controls.Menu> control.</span></span>  
  
|<span data-ttu-id="a03dc-127">Parte</span><span class="sxs-lookup"><span data-stu-id="a03dc-127">Part</span></span>|<span data-ttu-id="a03dc-128">Tipo</span><span class="sxs-lookup"><span data-stu-id="a03dc-128">Type</span></span>|<span data-ttu-id="a03dc-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="a03dc-129">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="a03dc-130">PART_Popup</span><span class="sxs-lookup"><span data-stu-id="a03dc-130">PART_Popup</span></span>|<xref:System.Windows.Controls.Primitives.Popup>|<span data-ttu-id="a03dc-131">A área para o submenu.</span><span class="sxs-lookup"><span data-stu-id="a03dc-131">The area for the submenu.</span></span>|  
  
 <span data-ttu-id="a03dc-132">Quando você cria um <xref:System.Windows.Controls.ControlTemplate> para um <xref:System.Windows.Controls.MenuItem>, o modelo pode conter um <xref:System.Windows.Controls.ItemsPresenter> dentro de um <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="a03dc-132">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.MenuItem>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="a03dc-133">(O <xref:System.Windows.Controls.ItemsPresenter> exibe cada item de <xref:System.Windows.Controls.MenuItem>; o <xref:System.Windows.Controls.ScrollViewer> habilita a rolagem dentro do controle).</span><span class="sxs-lookup"><span data-stu-id="a03dc-133">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.MenuItem>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="a03dc-134">Se o <xref:System.Windows.Controls.ItemsPresenter> não é filho direto do <xref:System.Windows.Controls.ScrollViewer>, você deve fornecer o <xref:System.Windows.Controls.ItemsPresenter> o nome `ItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="a03dc-134">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="menuitem-states"></a><span data-ttu-id="a03dc-135">Estados de MenuItem</span><span class="sxs-lookup"><span data-stu-id="a03dc-135">MenuItem States</span></span>  
 <span data-ttu-id="a03dc-136">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.MenuItem> controle.</span><span class="sxs-lookup"><span data-stu-id="a03dc-136">The following table lists the visual states for the <xref:System.Windows.Controls.MenuItem> control.</span></span>  
  
|<span data-ttu-id="a03dc-137">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="a03dc-137">VisualState Name</span></span>|<span data-ttu-id="a03dc-138">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="a03dc-138">VisualStateGroup Name</span></span>|<span data-ttu-id="a03dc-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="a03dc-139">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="a03dc-140">Válido</span><span class="sxs-lookup"><span data-stu-id="a03dc-140">Valid</span></span>|<span data-ttu-id="a03dc-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a03dc-141">ValidationStates</span></span>|<span data-ttu-id="a03dc-142">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="a03dc-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="a03dc-143">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="a03dc-143">InvalidFocused</span></span>|<span data-ttu-id="a03dc-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a03dc-144">ValidationStates</span></span>|<span data-ttu-id="a03dc-145">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="a03dc-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="a03dc-146">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="a03dc-146">InvalidUnfocused</span></span>|<span data-ttu-id="a03dc-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a03dc-147">ValidationStates</span></span>|<span data-ttu-id="a03dc-148">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="a03dc-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="menu-and-menuitem-controltemplate-example"></a><span data-ttu-id="a03dc-149">Menu e exemplo de ControlTemplate MenuItem</span><span class="sxs-lookup"><span data-stu-id="a03dc-149">Menu and MenuItem ControlTemplate Example</span></span>  
 <span data-ttu-id="a03dc-150">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.Menu> controle.</span><span class="sxs-lookup"><span data-stu-id="a03dc-150">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Menu> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Menu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menu)]  
  
 <span data-ttu-id="a03dc-151">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.MenuItem> controle.</span><span class="sxs-lookup"><span data-stu-id="a03dc-151">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.MenuItem> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#MenuItem](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuitem)]  
  
 <span data-ttu-id="a03dc-152">O exemplo a seguir define o `MenuScrollViewer`, que é usado no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="a03dc-152">The following example defines the `MenuScrollViewer`, which is used in the previous example.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#MenuScrollViewer](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuscrollviewer)]  
  
 <span data-ttu-id="a03dc-153">O <xref:System.Windows.Controls.ControlTemplate> exemplos usam um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="a03dc-153">The <xref:System.Windows.Controls.ControlTemplate> examples use one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="a03dc-154">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="a03dc-154">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a03dc-155">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a03dc-155">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="a03dc-156">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="a03dc-156">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="a03dc-157">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="a03dc-157">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="a03dc-158">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="a03dc-158">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="a03dc-159">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="a03dc-159">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
