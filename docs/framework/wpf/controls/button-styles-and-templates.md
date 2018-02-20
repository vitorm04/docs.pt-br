---
title: "Estilos e modelos de botão"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [WPF], Button
- parts [WPF], Button
- styles [WPF], Button
- Button [WPF], styles and templates
- templates [WPF], Button
- ControlTemplate [WPF], Button
ms.assetid: e223c759-f8c4-4717-acfb-b1e40bdf5f3b
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d783b3141463ca2c74ddd649848ea49e154415b6
ms.sourcegitcommit: 96cc82cac4650adfb65ba351506d8a8fbcd17b5c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2018
---
# <a name="button-styles-and-templates"></a><span data-ttu-id="a3f85-102">Estilos e modelos de botão</span><span class="sxs-lookup"><span data-stu-id="a3f85-102">Button Styles and Templates</span></span>
<span data-ttu-id="a3f85-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.Button> controle.</span><span class="sxs-lookup"><span data-stu-id="a3f85-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Button> control.</span></span> <span data-ttu-id="a3f85-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para que o controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="a3f85-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="a3f85-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="a3f85-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="button-parts"></a><span data-ttu-id="a3f85-106">Partes de botão</span><span class="sxs-lookup"><span data-stu-id="a3f85-106">Button Parts</span></span>  
 <span data-ttu-id="a3f85-107">O <xref:System.Windows.Controls.Button> controle não tem as partes nomeadas.</span><span class="sxs-lookup"><span data-stu-id="a3f85-107">The <xref:System.Windows.Controls.Button> control does not have any named parts.</span></span>  
  
## <a name="button-states"></a><span data-ttu-id="a3f85-108">Estados de botão</span><span class="sxs-lookup"><span data-stu-id="a3f85-108">Button States</span></span>  
 <span data-ttu-id="a3f85-109">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.Button> controle.</span><span class="sxs-lookup"><span data-stu-id="a3f85-109">The following table lists the visual states for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
|<span data-ttu-id="a3f85-110">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="a3f85-110">VisualState Name</span></span>|<span data-ttu-id="a3f85-111">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="a3f85-111">VisualStateGroup Name</span></span>|<span data-ttu-id="a3f85-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="a3f85-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="a3f85-113">Normal</span><span class="sxs-lookup"><span data-stu-id="a3f85-113">Normal</span></span>|<span data-ttu-id="a3f85-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="a3f85-114">CommonStates</span></span>|<span data-ttu-id="a3f85-115">O estado padrão.</span><span class="sxs-lookup"><span data-stu-id="a3f85-115">The default state.</span></span>|  
|<span data-ttu-id="a3f85-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="a3f85-116">MouseOver</span></span>|<span data-ttu-id="a3f85-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="a3f85-117">CommonStates</span></span>|<span data-ttu-id="a3f85-118">O ponteiro do mouse é posicionado sobre o controle.</span><span class="sxs-lookup"><span data-stu-id="a3f85-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="a3f85-119">Pressionado</span><span class="sxs-lookup"><span data-stu-id="a3f85-119">Pressed</span></span>|<span data-ttu-id="a3f85-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="a3f85-120">CommonStates</span></span>|<span data-ttu-id="a3f85-121">O controle é pressionado.</span><span class="sxs-lookup"><span data-stu-id="a3f85-121">The control is pressed.</span></span>|  
|<span data-ttu-id="a3f85-122">Disabled</span><span class="sxs-lookup"><span data-stu-id="a3f85-122">Disabled</span></span>|<span data-ttu-id="a3f85-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="a3f85-123">CommonStates</span></span>|<span data-ttu-id="a3f85-124">O controle está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="a3f85-124">The control is disabled.</span></span>|  
|<span data-ttu-id="a3f85-125">Focalizado</span><span class="sxs-lookup"><span data-stu-id="a3f85-125">Focused</span></span>|<span data-ttu-id="a3f85-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="a3f85-126">FocusStates</span></span>|<span data-ttu-id="a3f85-127">O controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="a3f85-127">The control has focus.</span></span>|  
|<span data-ttu-id="a3f85-128">Sem foco</span><span class="sxs-lookup"><span data-stu-id="a3f85-128">Unfocused</span></span>|<span data-ttu-id="a3f85-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="a3f85-129">FocusStates</span></span>|<span data-ttu-id="a3f85-130">O controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="a3f85-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="a3f85-131">Válido</span><span class="sxs-lookup"><span data-stu-id="a3f85-131">Valid</span></span>|<span data-ttu-id="a3f85-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a3f85-132">ValidationStates</span></span>|<span data-ttu-id="a3f85-133">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="a3f85-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="a3f85-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="a3f85-134">InvalidFocused</span></span>|<span data-ttu-id="a3f85-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a3f85-135">ValidationStates</span></span>|<span data-ttu-id="a3f85-136">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` e o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="a3f85-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="a3f85-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="a3f85-137">InvalidUnfocused</span></span>|<span data-ttu-id="a3f85-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a3f85-138">ValidationStates</span></span>|<span data-ttu-id="a3f85-139">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` e o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="a3f85-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="button-controltemplate-example"></a><span data-ttu-id="a3f85-140">Exemplo de ControlTemplate de botão</span><span class="sxs-lookup"><span data-stu-id="a3f85-140">Button ControlTemplate Example</span></span>  
 <span data-ttu-id="a3f85-141">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.Button> controle.</span><span class="sxs-lookup"><span data-stu-id="a3f85-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Button](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#button)]  
  
 <span data-ttu-id="a3f85-142">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="a3f85-142">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="a3f85-143">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="a3f85-143">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3f85-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a3f85-144">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="a3f85-145">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="a3f85-145">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="a3f85-146">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="a3f85-146">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="a3f85-147">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="a3f85-147">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="a3f85-148">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="a3f85-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
