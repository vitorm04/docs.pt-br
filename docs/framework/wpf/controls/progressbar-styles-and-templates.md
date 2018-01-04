---
title: Estilos e modelos ProgressBar
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parts [WPF], ProgressBar
- ProgressBar [WPF], styles and templates
- styles [WPF], ProgressBar
- ControlTemplate [WPF], ProgressBar
- templates [WPF], ProgressBar
- states [WPF], ProgressBar
ms.assetid: 935aa600-16e6-4947-a905-37a189a583dd
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6809ce2f51af8a1baf535afa8fe80f4e5b5f53e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="progressbar-styles-and-templates"></a><span data-ttu-id="5b512-102">Estilos e modelos ProgressBar</span><span class="sxs-lookup"><span data-stu-id="5b512-102">ProgressBar Styles and Templates</span></span>
<span data-ttu-id="5b512-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.ProgressBar> controle.</span><span class="sxs-lookup"><span data-stu-id="5b512-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ProgressBar> control.</span></span> <span data-ttu-id="5b512-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para que o controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="5b512-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="5b512-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="5b512-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="progressbar-parts"></a><span data-ttu-id="5b512-106">Partes de barra de progresso</span><span class="sxs-lookup"><span data-stu-id="5b512-106">ProgressBar Parts</span></span>  
 <span data-ttu-id="5b512-107">A tabela a seguir lista as partes nomeadas para o <xref:System.Windows.Controls.ProgressBar> controle.</span><span class="sxs-lookup"><span data-stu-id="5b512-107">The following table lists the named parts for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="5b512-108">Parte</span><span class="sxs-lookup"><span data-stu-id="5b512-108">Part</span></span>|<span data-ttu-id="5b512-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="5b512-109">Type</span></span>|<span data-ttu-id="5b512-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="5b512-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="5b512-111">PART_Indicator</span><span class="sxs-lookup"><span data-stu-id="5b512-111">PART_Indicator</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="5b512-112">O objeto que indica o progresso.</span><span class="sxs-lookup"><span data-stu-id="5b512-112">The object that indicates progress.</span></span>|  
|<span data-ttu-id="5b512-113">PART_Track</span><span class="sxs-lookup"><span data-stu-id="5b512-113">PART_Track</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="5b512-114">O objeto que define o caminho do indicador de progresso.</span><span class="sxs-lookup"><span data-stu-id="5b512-114">The object that defines the path of the progress indicator.</span></span>|  
|<span data-ttu-id="5b512-115">PART_GlowRect</span><span class="sxs-lookup"><span data-stu-id="5b512-115">PART_GlowRect</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="5b512-116">Um objeto que embellishes a barra de progresso.</span><span class="sxs-lookup"><span data-stu-id="5b512-116">An object that embellishes the progress bar.</span></span>|  
  
## <a name="progressbar-states"></a><span data-ttu-id="5b512-117">Estados de barra de progresso</span><span class="sxs-lookup"><span data-stu-id="5b512-117">ProgressBar States</span></span>  
 <span data-ttu-id="5b512-118">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.ProgressBar> controle.</span><span class="sxs-lookup"><span data-stu-id="5b512-118">The following table lists the visual states for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="5b512-119">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="5b512-119">VisualState Name</span></span>|<span data-ttu-id="5b512-120">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="5b512-120">VisualStateGroup Name</span></span>|<span data-ttu-id="5b512-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="5b512-121">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="5b512-122">Determinada</span><span class="sxs-lookup"><span data-stu-id="5b512-122">Determinate</span></span>|<span data-ttu-id="5b512-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="5b512-123">CommonStates</span></span>|<span data-ttu-id="5b512-124"><xref:System.Windows.Controls.ProgressBar>relata o progresso com base no <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="5b512-124"><xref:System.Windows.Controls.ProgressBar> reports progress based on the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property.</span></span>|  
|<span data-ttu-id="5b512-125">Indeterminado</span><span class="sxs-lookup"><span data-stu-id="5b512-125">Indeterminate</span></span>|<span data-ttu-id="5b512-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="5b512-126">CommonStates</span></span>|<span data-ttu-id="5b512-127"><xref:System.Windows.Controls.ProgressBar>relata o progresso genérico com um padrão de repetição.</span><span class="sxs-lookup"><span data-stu-id="5b512-127"><xref:System.Windows.Controls.ProgressBar> reports generic progress with a repeating pattern.</span></span>|  
|<span data-ttu-id="5b512-128">Válido</span><span class="sxs-lookup"><span data-stu-id="5b512-128">Valid</span></span>|<span data-ttu-id="5b512-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5b512-129">ValidationStates</span></span>|<span data-ttu-id="5b512-130">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="5b512-130">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="5b512-131">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="5b512-131">InvalidFocused</span></span>|<span data-ttu-id="5b512-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5b512-132">ValidationStates</span></span>|<span data-ttu-id="5b512-133">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="5b512-133">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="5b512-134">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="5b512-134">InvalidUnfocused</span></span>|<span data-ttu-id="5b512-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5b512-135">ValidationStates</span></span>|<span data-ttu-id="5b512-136">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="5b512-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="progressbar-controltemplate-example"></a><span data-ttu-id="5b512-137">Exemplo de ControlTemplate ProgressBar</span><span class="sxs-lookup"><span data-stu-id="5b512-137">ProgressBar ControlTemplate Example</span></span>  
 <span data-ttu-id="5b512-138">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.ProgressBar> controle.</span><span class="sxs-lookup"><span data-stu-id="5b512-138">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ProgressBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
 <span data-ttu-id="5b512-139">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="5b512-139">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="5b512-140">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="5b512-140">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b512-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5b512-141">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="5b512-142">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="5b512-142">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="5b512-143">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="5b512-143">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="5b512-144">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="5b512-144">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="5b512-145">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="5b512-145">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
