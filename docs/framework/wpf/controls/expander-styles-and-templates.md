---
title: Estilos e modelos de expansor
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- styles [WPF], Expander
- ControlTemplate [WPF], Expander
- templates [WPF], Expander
- Expander [WPF], styles and templates
- states [WPF], Expander
- parts [WPF], Expander
ms.assetid: da2e5a1c-5230-4c21-98a5-59c7895facd7
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 999b081d80680069d4c6fdf908814889afa60870
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="expander-styles-and-templates"></a><span data-ttu-id="f3193-102">Estilos e modelos de expansor</span><span class="sxs-lookup"><span data-stu-id="f3193-102">Expander Styles and Templates</span></span>
<span data-ttu-id="f3193-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.Expander> controle.</span><span class="sxs-lookup"><span data-stu-id="f3193-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Expander> control.</span></span> <span data-ttu-id="f3193-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para que o controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="f3193-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="f3193-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="f3193-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="expander-parts"></a><span data-ttu-id="f3193-106">Partes de expansão</span><span class="sxs-lookup"><span data-stu-id="f3193-106">Expander Parts</span></span>  
 <span data-ttu-id="f3193-107">O <xref:System.Windows.Controls.Expander> controle não tem as partes nomeadas.</span><span class="sxs-lookup"><span data-stu-id="f3193-107">The <xref:System.Windows.Controls.Expander> control does not have any named parts.</span></span>  
  
## <a name="expander-states"></a><span data-ttu-id="f3193-108">Estados de expansão</span><span class="sxs-lookup"><span data-stu-id="f3193-108">Expander States</span></span>  
 <span data-ttu-id="f3193-109">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.Expander> controle.</span><span class="sxs-lookup"><span data-stu-id="f3193-109">The following table lists the visual states for the <xref:System.Windows.Controls.Expander> control.</span></span>  
  
|<span data-ttu-id="f3193-110">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="f3193-110">VisualState Name</span></span>|<span data-ttu-id="f3193-111">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="f3193-111">VisualStateGroup Name</span></span>|<span data-ttu-id="f3193-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="f3193-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="f3193-113">Normal</span><span class="sxs-lookup"><span data-stu-id="f3193-113">Normal</span></span>|<span data-ttu-id="f3193-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f3193-114">CommonStates</span></span>|<span data-ttu-id="f3193-115">O estado padrão.</span><span class="sxs-lookup"><span data-stu-id="f3193-115">The default state.</span></span>|  
|<span data-ttu-id="f3193-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="f3193-116">MouseOver</span></span>|<span data-ttu-id="f3193-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f3193-117">CommonStates</span></span>|<span data-ttu-id="f3193-118">O ponteiro do mouse é posicionado sobre o controle.</span><span class="sxs-lookup"><span data-stu-id="f3193-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="f3193-119">Disabled</span><span class="sxs-lookup"><span data-stu-id="f3193-119">Disabled</span></span>|<span data-ttu-id="f3193-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f3193-120">CommonStates</span></span>|<span data-ttu-id="f3193-121">O controle está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="f3193-121">The control is disabled.</span></span>|  
|<span data-ttu-id="f3193-122">Focalizado</span><span class="sxs-lookup"><span data-stu-id="f3193-122">Focused</span></span>|<span data-ttu-id="f3193-123">FocusStates</span><span class="sxs-lookup"><span data-stu-id="f3193-123">FocusStates</span></span>|<span data-ttu-id="f3193-124">O controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="f3193-124">The control has focus.</span></span>|  
|<span data-ttu-id="f3193-125">Sem foco</span><span class="sxs-lookup"><span data-stu-id="f3193-125">Unfocused</span></span>|<span data-ttu-id="f3193-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="f3193-126">FocusStates</span></span>|<span data-ttu-id="f3193-127">O controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="f3193-127">The control does not have focus.</span></span>|  
|<span data-ttu-id="f3193-128">Expandido</span><span class="sxs-lookup"><span data-stu-id="f3193-128">Expanded</span></span>|<span data-ttu-id="f3193-129">ExpansionStates</span><span class="sxs-lookup"><span data-stu-id="f3193-129">ExpansionStates</span></span>|<span data-ttu-id="f3193-130">O controle é expandido.</span><span class="sxs-lookup"><span data-stu-id="f3193-130">The control is expanded.</span></span>|  
|<span data-ttu-id="f3193-131">Recolhido</span><span class="sxs-lookup"><span data-stu-id="f3193-131">Collapsed</span></span>|<span data-ttu-id="f3193-132">ExpansionStates</span><span class="sxs-lookup"><span data-stu-id="f3193-132">ExpansionStates</span></span>|<span data-ttu-id="f3193-133">O controle não está expandido.</span><span class="sxs-lookup"><span data-stu-id="f3193-133">The control is not expanded.</span></span>|  
|<span data-ttu-id="f3193-134">ExpandDown</span><span class="sxs-lookup"><span data-stu-id="f3193-134">ExpandDown</span></span>|<span data-ttu-id="f3193-135">ExpandDirectionStates</span><span class="sxs-lookup"><span data-stu-id="f3193-135">ExpandDirectionStates</span></span>|<span data-ttu-id="f3193-136">O controle se expande para baixo.</span><span class="sxs-lookup"><span data-stu-id="f3193-136">The control expands down.</span></span>|  
|<span data-ttu-id="f3193-137">ExpandUp</span><span class="sxs-lookup"><span data-stu-id="f3193-137">ExpandUp</span></span>|<span data-ttu-id="f3193-138">ExpandDirectionStates</span><span class="sxs-lookup"><span data-stu-id="f3193-138">ExpandDirectionStates</span></span>|<span data-ttu-id="f3193-139">Expande o controle de backup.</span><span class="sxs-lookup"><span data-stu-id="f3193-139">The control expands up.</span></span>|  
|<span data-ttu-id="f3193-140">ExpandLeft</span><span class="sxs-lookup"><span data-stu-id="f3193-140">ExpandLeft</span></span>|<span data-ttu-id="f3193-141">ExpandDirectionStates</span><span class="sxs-lookup"><span data-stu-id="f3193-141">ExpandDirectionStates</span></span>|<span data-ttu-id="f3193-142">O controle se expande para a esquerda.</span><span class="sxs-lookup"><span data-stu-id="f3193-142">The control expands left.</span></span>|  
|<span data-ttu-id="f3193-143">ExpandRight</span><span class="sxs-lookup"><span data-stu-id="f3193-143">ExpandRight</span></span>|<span data-ttu-id="f3193-144">ExpandDirectionStates</span><span class="sxs-lookup"><span data-stu-id="f3193-144">ExpandDirectionStates</span></span>|<span data-ttu-id="f3193-145">O controle se expande à direita.</span><span class="sxs-lookup"><span data-stu-id="f3193-145">The control expands right.</span></span>|  
|<span data-ttu-id="f3193-146">Válido</span><span class="sxs-lookup"><span data-stu-id="f3193-146">Valid</span></span>|<span data-ttu-id="f3193-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f3193-147">ValidationStates</span></span>|<span data-ttu-id="f3193-148">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="f3193-148">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="f3193-149">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="f3193-149">InvalidFocused</span></span>|<span data-ttu-id="f3193-150">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f3193-150">ValidationStates</span></span>|<span data-ttu-id="f3193-151">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="f3193-151">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="f3193-152">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="f3193-152">InvalidUnfocused</span></span>|<span data-ttu-id="f3193-153">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f3193-153">ValidationStates</span></span>|<span data-ttu-id="f3193-154">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="f3193-154">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="expander-controltemplate-example"></a><span data-ttu-id="f3193-155">Exemplo de ControlTemplate de expansão</span><span class="sxs-lookup"><span data-stu-id="f3193-155">Expander ControlTemplate Example</span></span>  
 <span data-ttu-id="f3193-156">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.Expander> controle.</span><span class="sxs-lookup"><span data-stu-id="f3193-156">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Expander> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Expander](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/expander.xaml#expander)]  
  
 <span data-ttu-id="f3193-157">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="f3193-157">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="f3193-158">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="f3193-158">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3193-159">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3193-159">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="f3193-160">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="f3193-160">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="f3193-161">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="f3193-161">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="f3193-162">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="f3193-162">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="f3193-163">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="f3193-163">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
