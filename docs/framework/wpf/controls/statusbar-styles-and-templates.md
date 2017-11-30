---
title: Estilos e modelos StatusBar
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ControlTemplate [WPF], StatusBar
- styles [WPF], StatusBar
- templates [WPF], StatusBar
- states [WPF], StatusBar
- parts [WPF], StatusBar
- StatusBar [WPF], styles and templates
ms.assetid: 9f5e1c25-81eb-4756-a0ac-d9e1fbe33ee2
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 570edc023467fb6e95cdcba23b75ac53397797c2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="statusbar-styles-and-templates"></a><span data-ttu-id="a18fa-102">Estilos e modelos StatusBar</span><span class="sxs-lookup"><span data-stu-id="a18fa-102">StatusBar Styles and Templates</span></span>
<span data-ttu-id="a18fa-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.Primitives.StatusBar> controle.</span><span class="sxs-lookup"><span data-stu-id="a18fa-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span> <span data-ttu-id="a18fa-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para que o controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="a18fa-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="a18fa-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="a18fa-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="statusbar-parts"></a><span data-ttu-id="a18fa-106">Partes de StatusBar</span><span class="sxs-lookup"><span data-stu-id="a18fa-106">StatusBar Parts</span></span>  
 <span data-ttu-id="a18fa-107">O <xref:System.Windows.Controls.Primitives.StatusBar> controle não tem as partes nomeadas.</span><span class="sxs-lookup"><span data-stu-id="a18fa-107">The <xref:System.Windows.Controls.Primitives.StatusBar> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="a18fa-108">Estados de StatusBar</span><span class="sxs-lookup"><span data-stu-id="a18fa-108">StatusBar States</span></span>  
 <span data-ttu-id="a18fa-109">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.Primitives.StatusBar> controle.</span><span class="sxs-lookup"><span data-stu-id="a18fa-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
|<span data-ttu-id="a18fa-110">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="a18fa-110">VisualState Name</span></span>|<span data-ttu-id="a18fa-111">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="a18fa-111">VisualStateGroup Name</span></span>|<span data-ttu-id="a18fa-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="a18fa-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="a18fa-113">Válido</span><span class="sxs-lookup"><span data-stu-id="a18fa-113">Valid</span></span>|<span data-ttu-id="a18fa-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a18fa-114">ValidationStates</span></span>|<span data-ttu-id="a18fa-115">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="a18fa-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="a18fa-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="a18fa-116">InvalidFocused</span></span>|<span data-ttu-id="a18fa-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a18fa-117">ValidationStates</span></span>|<span data-ttu-id="a18fa-118">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="a18fa-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="a18fa-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="a18fa-119">InvalidUnfocused</span></span>|<span data-ttu-id="a18fa-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a18fa-120">ValidationStates</span></span>|<span data-ttu-id="a18fa-121">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="a18fa-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbaritem-parts"></a><span data-ttu-id="a18fa-122">StatusBarItem partes</span><span class="sxs-lookup"><span data-stu-id="a18fa-122">StatusBarItem Parts</span></span>  
 <span data-ttu-id="a18fa-123">O <xref:System.Windows.Controls.Primitives.StatusBarItem> controle não tem as partes nomeadas.</span><span class="sxs-lookup"><span data-stu-id="a18fa-123">The <xref:System.Windows.Controls.Primitives.StatusBarItem> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="a18fa-124">Estados de StatusBar</span><span class="sxs-lookup"><span data-stu-id="a18fa-124">StatusBar States</span></span>  
 <span data-ttu-id="a18fa-125">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.Primitives.StatusBarItem> controle.</span><span class="sxs-lookup"><span data-stu-id="a18fa-125">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBarItem> control.</span></span>  
  
|<span data-ttu-id="a18fa-126">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="a18fa-126">VisualState Name</span></span>|<span data-ttu-id="a18fa-127">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="a18fa-127">VisualStateGroup Name</span></span>|<span data-ttu-id="a18fa-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="a18fa-128">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="a18fa-129">Válido</span><span class="sxs-lookup"><span data-stu-id="a18fa-129">Valid</span></span>|<span data-ttu-id="a18fa-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a18fa-130">ValidationStates</span></span>|<span data-ttu-id="a18fa-131">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="a18fa-131">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="a18fa-132">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="a18fa-132">InvalidFocused</span></span>|<span data-ttu-id="a18fa-133">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a18fa-133">ValidationStates</span></span>|<span data-ttu-id="a18fa-134">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="a18fa-134">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="a18fa-135">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="a18fa-135">InvalidUnfocused</span></span>|<span data-ttu-id="a18fa-136">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a18fa-136">ValidationStates</span></span>|<span data-ttu-id="a18fa-137">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="a18fa-137">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbar-controltemplate-example"></a><span data-ttu-id="a18fa-138">Exemplo de ControlTemplate StatusBar</span><span class="sxs-lookup"><span data-stu-id="a18fa-138">StatusBar ControlTemplate Example</span></span>  
 <span data-ttu-id="a18fa-139">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.Primitives.StatusBar> controle.</span><span class="sxs-lookup"><span data-stu-id="a18fa-139">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#StatusBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/statusbar.xaml#statusbar)]  
  
 <span data-ttu-id="a18fa-140">O <xref:System.Windows.Controls.ControlTemplate> usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="a18fa-140">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="a18fa-141">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="a18fa-141">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a18fa-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a18fa-142">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="a18fa-143">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="a18fa-143">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="a18fa-144">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="a18fa-144">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="a18fa-145">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="a18fa-145">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="a18fa-146">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="a18fa-146">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
