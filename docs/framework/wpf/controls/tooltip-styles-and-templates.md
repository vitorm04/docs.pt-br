---
title: Estilos e modelos ToolTip
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parts [WPF], ToolTip
- styles [WPF], ToolTip
- states [WPF], ToolTip
- ToolTip [WPF], styles and templates
- ControlTemplate [WPF], ToolTip
- templates [WPF], ToolTip
ms.assetid: 405fe385-4de9-49ee-a448-d8f4d1f740dd
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4e39372083ede5649addee4b493f2425116ec2aa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="tooltip-styles-and-templates"></a><span data-ttu-id="08a07-102">Estilos e modelos ToolTip</span><span class="sxs-lookup"><span data-stu-id="08a07-102">ToolTip Styles and Templates</span></span>
<span data-ttu-id="08a07-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.ToolTip> controle.</span><span class="sxs-lookup"><span data-stu-id="08a07-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolTip> control.</span></span> <span data-ttu-id="08a07-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para que o controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="08a07-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="08a07-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="08a07-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="tooltip-parts"></a><span data-ttu-id="08a07-106">Partes de dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="08a07-106">ToolTip Parts</span></span>  
 <span data-ttu-id="08a07-107">O <xref:System.Windows.Controls.ToolTip> controle não tem as partes nomeadas.</span><span class="sxs-lookup"><span data-stu-id="08a07-107">The <xref:System.Windows.Controls.ToolTip> control does not have any named parts.</span></span>  
  
## <a name="tooltip-states"></a><span data-ttu-id="08a07-108">Estados de dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="08a07-108">ToolTip States</span></span>  
 <span data-ttu-id="08a07-109">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.ToolTip> controle.</span><span class="sxs-lookup"><span data-stu-id="08a07-109">The following table lists the visual states for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
|<span data-ttu-id="08a07-110">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="08a07-110">VisualState Name</span></span>|<span data-ttu-id="08a07-111">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="08a07-111">VisualStateGroup Name</span></span>|<span data-ttu-id="08a07-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="08a07-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="08a07-113">Closed</span><span class="sxs-lookup"><span data-stu-id="08a07-113">Closed</span></span>|<span data-ttu-id="08a07-114">OpenStates</span><span class="sxs-lookup"><span data-stu-id="08a07-114">OpenStates</span></span>|<span data-ttu-id="08a07-115">O estado padrão.</span><span class="sxs-lookup"><span data-stu-id="08a07-115">The default state.</span></span>|  
|<span data-ttu-id="08a07-116">Abrir</span><span class="sxs-lookup"><span data-stu-id="08a07-116">Open</span></span>|<span data-ttu-id="08a07-117">OpenStates</span><span class="sxs-lookup"><span data-stu-id="08a07-117">OpenStates</span></span>|<span data-ttu-id="08a07-118">O <xref:System.Windows.Controls.ToolTip> está visível.</span><span class="sxs-lookup"><span data-stu-id="08a07-118">The <xref:System.Windows.Controls.ToolTip> is visible.</span></span>|  
|<span data-ttu-id="08a07-119">Válido</span><span class="sxs-lookup"><span data-stu-id="08a07-119">Valid</span></span>|<span data-ttu-id="08a07-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="08a07-120">ValidationStates</span></span>|<span data-ttu-id="08a07-121">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="08a07-121">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="08a07-122">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="08a07-122">InvalidFocused</span></span>|<span data-ttu-id="08a07-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="08a07-123">ValidationStates</span></span>|<span data-ttu-id="08a07-124">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="08a07-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="08a07-125">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="08a07-125">InvalidUnfocused</span></span>|<span data-ttu-id="08a07-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="08a07-126">ValidationStates</span></span>|<span data-ttu-id="08a07-127">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="08a07-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="tooltip-controltemplate-example"></a><span data-ttu-id="08a07-128">Exemplo de ControlTemplate ToolTip</span><span class="sxs-lookup"><span data-stu-id="08a07-128">ToolTip ControlTemplate Example</span></span>  
 <span data-ttu-id="08a07-129">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.ToolTip> controle.</span><span class="sxs-lookup"><span data-stu-id="08a07-129">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/tooltip.xaml#tooltip)]  
  
 <span data-ttu-id="08a07-130">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="08a07-130">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="08a07-131">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="08a07-131">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08a07-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="08a07-132">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="08a07-133">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="08a07-133">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="08a07-134">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="08a07-134">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="08a07-135">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="08a07-135">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="08a07-136">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="08a07-136">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
