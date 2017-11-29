---
title: Estilos e modelos ToolBar
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [WPF], ToolBar
- styles [WPF], ToolBar
- ControlTemplate [WPF], ToolBar
- parts [WPF], ToolBar
- ToolBar [WPF], styles and templates
- templates [WPF], ToolBar
ms.assetid: bd875f46-4690-46f5-81e0-f11a9822484f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3e153ff0fd89259dafedf6f8abb669090a944e91
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="toolbar-styles-and-templates"></a><span data-ttu-id="8d163-102">Estilos e modelos ToolBar</span><span class="sxs-lookup"><span data-stu-id="8d163-102">ToolBar Styles and Templates</span></span>
<span data-ttu-id="8d163-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.ToolBar> controle.</span><span class="sxs-lookup"><span data-stu-id="8d163-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolBar> control.</span></span> <span data-ttu-id="8d163-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para que o controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="8d163-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="8d163-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="8d163-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="toolbar-parts"></a><span data-ttu-id="8d163-106">Partes da barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="8d163-106">ToolBar Parts</span></span>  
 <span data-ttu-id="8d163-107">A tabela a seguir lista as partes nomeadas para o <xref:System.Windows.Controls.ToolBar> controle.</span><span class="sxs-lookup"><span data-stu-id="8d163-107">The following table lists the named parts for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
|<span data-ttu-id="8d163-108">Parte</span><span class="sxs-lookup"><span data-stu-id="8d163-108">Part</span></span>|<span data-ttu-id="8d163-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="8d163-109">Type</span></span>|<span data-ttu-id="8d163-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="8d163-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="8d163-111">PART_ToolBarPanel</span><span class="sxs-lookup"><span data-stu-id="8d163-111">PART_ToolBarPanel</span></span>|<xref:System.Windows.Controls.Primitives.ToolBarPanel>|<span data-ttu-id="8d163-112">O objeto que contém os controles no <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="8d163-112">The object that contains the controls on the <xref:System.Windows.Controls.ToolBar>.</span></span>|  
|<span data-ttu-id="8d163-113">PART_ToolBarOverflowPanel</span><span class="sxs-lookup"><span data-stu-id="8d163-113">PART_ToolBarOverflowPanel</span></span>|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|<span data-ttu-id="8d163-114">O objeto que contém os controles que estão na área de estouro de <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="8d163-114">The object that contains the controls that are in the overflow area of the <xref:System.Windows.Controls.ToolBar>.</span></span>|  
  
 <span data-ttu-id="8d163-115">Quando você cria um <xref:System.Windows.Controls.ControlTemplate> para um <xref:System.Windows.Controls.ToolBar>, o modelo pode conter um <xref:System.Windows.Controls.ItemsPresenter> dentro de um <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="8d163-115">When you create a <xref:System.Windows.Controls.ControlTemplate> for a <xref:System.Windows.Controls.ToolBar>, your template might contain an <xref:System.Windows.Controls.ItemsPresenter> within a <xref:System.Windows.Controls.ScrollViewer>.</span></span> <span data-ttu-id="8d163-116">(O <xref:System.Windows.Controls.ItemsPresenter> exibe cada item de <xref:System.Windows.Controls.ToolBar>; o <xref:System.Windows.Controls.ScrollViewer> habilita a rolagem dentro do controle).</span><span class="sxs-lookup"><span data-stu-id="8d163-116">(The <xref:System.Windows.Controls.ItemsPresenter> displays each item in the <xref:System.Windows.Controls.ToolBar>; the <xref:System.Windows.Controls.ScrollViewer> enables scrolling within the control).</span></span>  <span data-ttu-id="8d163-117">Se o <xref:System.Windows.Controls.ItemsPresenter> não é filho direto do <xref:System.Windows.Controls.ScrollViewer>, você deve fornecer o <xref:System.Windows.Controls.ItemsPresenter> o nome `ItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="8d163-117">If the <xref:System.Windows.Controls.ItemsPresenter> is not the direct child of the <xref:System.Windows.Controls.ScrollViewer>, you must give the <xref:System.Windows.Controls.ItemsPresenter> the name, `ItemsPresenter`.</span></span>  
  
## <a name="toolbar-states"></a><span data-ttu-id="8d163-118">Estados da barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="8d163-118">ToolBar States</span></span>  
 <span data-ttu-id="8d163-119">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.ToolBar> controle.</span><span class="sxs-lookup"><span data-stu-id="8d163-119">The following table lists the visual states for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
|<span data-ttu-id="8d163-120">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="8d163-120">VisualState Name</span></span>|<span data-ttu-id="8d163-121">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="8d163-121">VisualStateGroup Name</span></span>|<span data-ttu-id="8d163-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="8d163-122">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="8d163-123">Válido</span><span class="sxs-lookup"><span data-stu-id="8d163-123">Valid</span></span>|<span data-ttu-id="8d163-124">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="8d163-124">ValidationStates</span></span>|<span data-ttu-id="8d163-125">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="8d163-125">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="8d163-126">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="8d163-126">InvalidFocused</span></span>|<span data-ttu-id="8d163-127">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="8d163-127">ValidationStates</span></span>|<span data-ttu-id="8d163-128">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="8d163-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="8d163-129">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="8d163-129">InvalidUnfocused</span></span>|<span data-ttu-id="8d163-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="8d163-130">ValidationStates</span></span>|<span data-ttu-id="8d163-131">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="8d163-131">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="toolbar-controltemplate-example"></a><span data-ttu-id="8d163-132">Exemplo de ControlTemplate de barra de ferramentas</span><span class="sxs-lookup"><span data-stu-id="8d163-132">ToolBar ControlTemplate Example</span></span>  
 <span data-ttu-id="8d163-133">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.ToolBar> controle.</span><span class="sxs-lookup"><span data-stu-id="8d163-133">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/toolbar.xaml#toolbar)]  
  
 <span data-ttu-id="8d163-134">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="8d163-134">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="8d163-135">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="8d163-135">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d163-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d163-136">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="8d163-137">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="8d163-137">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="8d163-138">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="8d163-138">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="8d163-139">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="8d163-139">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="8d163-140">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="8d163-140">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
