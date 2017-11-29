---
title: Estilos e modelos de elevador
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [WPF], Thumb
- styles [WPF], Thumb
- templates [WPF], Thumb
- Thumb [WPF], styles and templates
- ControlTemplate [WPF], Thumb
- parts [WPF], Thumb
ms.assetid: 86a49235-62d9-414e-923e-53126e3f930a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7d9f0b8559497939737b97568a679953d392d5be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="thumb-syles-and-templates"></a><span data-ttu-id="eab70-102">Estilos e modelos de elevador</span><span class="sxs-lookup"><span data-stu-id="eab70-102">Thumb Syles and Templates</span></span>
<span data-ttu-id="eab70-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.Primitives.Thumb> controle.</span><span class="sxs-lookup"><span data-stu-id="eab70-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span> <span data-ttu-id="eab70-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para que o controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="eab70-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="eab70-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="eab70-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="thumb-parts"></a><span data-ttu-id="eab70-106">Partes de miniatura</span><span class="sxs-lookup"><span data-stu-id="eab70-106">Thumb Parts</span></span>  
 <span data-ttu-id="eab70-107">O <xref:System.Windows.Controls.Primitives.Thumb> controle não tem as partes nomeadas.</span><span class="sxs-lookup"><span data-stu-id="eab70-107">The <xref:System.Windows.Controls.Primitives.Thumb> control does not have any named parts.</span></span>  
  
## <a name="thumb-states"></a><span data-ttu-id="eab70-108">Estados de miniatura</span><span class="sxs-lookup"><span data-stu-id="eab70-108">Thumb States</span></span>  
 <span data-ttu-id="eab70-109">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.Primitives.Thumb> controle.</span><span class="sxs-lookup"><span data-stu-id="eab70-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>  
  
|<span data-ttu-id="eab70-110">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="eab70-110">VisualState Name</span></span>|<span data-ttu-id="eab70-111">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="eab70-111">VisualStateGroup Name</span></span>|<span data-ttu-id="eab70-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="eab70-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="eab70-113">Normal</span><span class="sxs-lookup"><span data-stu-id="eab70-113">Normal</span></span>|<span data-ttu-id="eab70-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="eab70-114">CommonStates</span></span>|<span data-ttu-id="eab70-115">O estado padrão.</span><span class="sxs-lookup"><span data-stu-id="eab70-115">The default state.</span></span>|  
|<span data-ttu-id="eab70-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="eab70-116">MouseOver</span></span>|<span data-ttu-id="eab70-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="eab70-117">CommonStates</span></span>|<span data-ttu-id="eab70-118">O ponteiro do mouse é posicionado sobre o controle.</span><span class="sxs-lookup"><span data-stu-id="eab70-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="eab70-119">Pressionado</span><span class="sxs-lookup"><span data-stu-id="eab70-119">Pressed</span></span>|<span data-ttu-id="eab70-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="eab70-120">CommonStates</span></span>|<span data-ttu-id="eab70-121">O controle é pressionado.</span><span class="sxs-lookup"><span data-stu-id="eab70-121">The control is pressed.</span></span>|  
|<span data-ttu-id="eab70-122">Disabled</span><span class="sxs-lookup"><span data-stu-id="eab70-122">Disabled</span></span>|<span data-ttu-id="eab70-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="eab70-123">CommonStates</span></span>|<span data-ttu-id="eab70-124">O controle está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="eab70-124">The control is disabled.</span></span>|  
|<span data-ttu-id="eab70-125">Focalizado</span><span class="sxs-lookup"><span data-stu-id="eab70-125">Focused</span></span>|<span data-ttu-id="eab70-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="eab70-126">FocusStates</span></span>|<span data-ttu-id="eab70-127">O controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="eab70-127">The control has focus.</span></span>|  
|<span data-ttu-id="eab70-128">Sem foco</span><span class="sxs-lookup"><span data-stu-id="eab70-128">Unfocused</span></span>|<span data-ttu-id="eab70-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="eab70-129">FocusStates</span></span>|<span data-ttu-id="eab70-130">O controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="eab70-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="eab70-131">Válido</span><span class="sxs-lookup"><span data-stu-id="eab70-131">Valid</span></span>|<span data-ttu-id="eab70-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="eab70-132">ValidationStates</span></span>|<span data-ttu-id="eab70-133">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="eab70-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="eab70-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="eab70-134">InvalidFocused</span></span>|<span data-ttu-id="eab70-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="eab70-135">ValidationStates</span></span>|<span data-ttu-id="eab70-136">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="eab70-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="eab70-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="eab70-137">InvalidUnfocused</span></span>|<span data-ttu-id="eab70-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="eab70-138">ValidationStates</span></span>|<span data-ttu-id="eab70-139">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="eab70-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="thumb-controltemplate-example"></a><span data-ttu-id="eab70-140">Exemplo de ControlTemplate Thumb</span><span class="sxs-lookup"><span data-stu-id="eab70-140">Thumb ControlTemplate Example</span></span>  
 <span data-ttu-id="eab70-141">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.Primitives.Thumb> controle.</span><span class="sxs-lookup"><span data-stu-id="eab70-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Thumb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#thumb)]  
  
 <span data-ttu-id="eab70-142">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="eab70-142">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="eab70-143">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="eab70-143">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eab70-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eab70-144">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="eab70-145">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="eab70-145">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="eab70-146">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="eab70-146">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="eab70-147">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="eab70-147">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="eab70-148">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="eab70-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
