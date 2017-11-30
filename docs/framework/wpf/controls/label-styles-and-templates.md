---
title: "Estilos e modelos de rótulo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- templates [WPF], Label
- parts [WPF], Label
- ControlTemplate [WPF], Label
- styles [WPF], Label
- Label [WPF], styles and templates
- states [WPF], Label
ms.assetid: c1d5359a-8e4a-4925-ab3e-e92bf6694859
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 013d21c7547531541c89435dbbdde65911ae3750
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="label-styles-and-templates"></a><span data-ttu-id="3388f-102">Estilos e modelos de rótulo</span><span class="sxs-lookup"><span data-stu-id="3388f-102">Label Styles and Templates</span></span>
<span data-ttu-id="3388f-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.Label> controle.</span><span class="sxs-lookup"><span data-stu-id="3388f-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Label> control.</span></span> <span data-ttu-id="3388f-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para que o controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="3388f-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="3388f-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="3388f-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="label-parts"></a><span data-ttu-id="3388f-106">Partes de rótulo</span><span class="sxs-lookup"><span data-stu-id="3388f-106">Label Parts</span></span>  
 <span data-ttu-id="3388f-107">O <xref:System.Windows.Controls.Label> controle não tem as partes nomeadas.</span><span class="sxs-lookup"><span data-stu-id="3388f-107">The <xref:System.Windows.Controls.Label> control does not have any named parts.</span></span>  
  
## <a name="label-states"></a><span data-ttu-id="3388f-108">Estados de rótulo</span><span class="sxs-lookup"><span data-stu-id="3388f-108">Label States</span></span>  
 <span data-ttu-id="3388f-109">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.Label> controle.</span><span class="sxs-lookup"><span data-stu-id="3388f-109">The following table lists the visual states for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
|<span data-ttu-id="3388f-110">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="3388f-110">VisualState Name</span></span>|<span data-ttu-id="3388f-111">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="3388f-111">VisualStateGroup Name</span></span>|<span data-ttu-id="3388f-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="3388f-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="3388f-113">Válido</span><span class="sxs-lookup"><span data-stu-id="3388f-113">Valid</span></span>|<span data-ttu-id="3388f-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3388f-114">ValidationStates</span></span>|<span data-ttu-id="3388f-115">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="3388f-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="3388f-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="3388f-116">InvalidFocused</span></span>|<span data-ttu-id="3388f-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3388f-117">ValidationStates</span></span>|<span data-ttu-id="3388f-118">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="3388f-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="3388f-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="3388f-119">InvalidUnfocused</span></span>|<span data-ttu-id="3388f-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3388f-120">ValidationStates</span></span>|<span data-ttu-id="3388f-121">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="3388f-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="label-controltemplate-example"></a><span data-ttu-id="3388f-122">Exemplo de ControlTemplate de rótulo</span><span class="sxs-lookup"><span data-stu-id="3388f-122">Label ControlTemplate Example</span></span>  
 <span data-ttu-id="3388f-123">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.Label> controle.</span><span class="sxs-lookup"><span data-stu-id="3388f-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Label](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/label.xaml#label)]  
  
 <span data-ttu-id="3388f-124">O <xref:System.Windows.Controls.ControlTemplate> usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="3388f-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="3388f-125">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="3388f-125">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3388f-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3388f-126">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="3388f-127">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="3388f-127">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="3388f-128">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="3388f-128">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="3388f-129">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="3388f-129">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="3388f-130">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="3388f-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
