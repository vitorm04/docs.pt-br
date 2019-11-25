---
title: Estilos e modelos StatusBar
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], StatusBar
- styles [WPF], StatusBar
- templates [WPF], StatusBar
- states [WPF], StatusBar
- parts [WPF], StatusBar
- StatusBar [WPF], styles and templates
ms.assetid: 9f5e1c25-81eb-4756-a0ac-d9e1fbe33ee2
ms.openlocfilehash: 843c9003edbe94115719a63a968eda3833515a85
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283367"
---
# <a name="statusbar-styles-and-templates"></a><span data-ttu-id="6ab48-102">Estilos e modelos StatusBar</span><span class="sxs-lookup"><span data-stu-id="6ab48-102">StatusBar Styles and Templates</span></span>
<span data-ttu-id="6ab48-103">Este tópico descreve os estilos e modelos para o controle de <xref:System.Windows.Controls.Primitives.StatusBar>.</span><span class="sxs-lookup"><span data-stu-id="6ab48-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span> <span data-ttu-id="6ab48-104">Você pode modificar o <xref:System.Windows.Controls.ControlTemplate> padrão para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="6ab48-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="6ab48-105">Para obter mais informações, consulte [criar um modelo para um controle](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="6ab48-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="statusbar-parts"></a><span data-ttu-id="6ab48-106">Partes StatusBar</span><span class="sxs-lookup"><span data-stu-id="6ab48-106">StatusBar Parts</span></span>  
 <span data-ttu-id="6ab48-107">O controle de <xref:System.Windows.Controls.Primitives.StatusBar> não tem nenhuma parte nomeada.</span><span class="sxs-lookup"><span data-stu-id="6ab48-107">The <xref:System.Windows.Controls.Primitives.StatusBar> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="6ab48-108">Estados StatusBar</span><span class="sxs-lookup"><span data-stu-id="6ab48-108">StatusBar States</span></span>  
 <span data-ttu-id="6ab48-109">A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Controls.Primitives.StatusBar>.</span><span class="sxs-lookup"><span data-stu-id="6ab48-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
|<span data-ttu-id="6ab48-110">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="6ab48-110">VisualState Name</span></span>|<span data-ttu-id="6ab48-111">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="6ab48-111">VisualStateGroup Name</span></span>|<span data-ttu-id="6ab48-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="6ab48-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="6ab48-113">Válido</span><span class="sxs-lookup"><span data-stu-id="6ab48-113">Valid</span></span>|<span data-ttu-id="6ab48-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6ab48-114">ValidationStates</span></span>|<span data-ttu-id="6ab48-115">O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.</span><span class="sxs-lookup"><span data-stu-id="6ab48-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="6ab48-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="6ab48-116">InvalidFocused</span></span>|<span data-ttu-id="6ab48-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6ab48-117">ValidationStates</span></span>|<span data-ttu-id="6ab48-118">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.</span><span class="sxs-lookup"><span data-stu-id="6ab48-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="6ab48-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="6ab48-119">InvalidUnfocused</span></span>|<span data-ttu-id="6ab48-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6ab48-120">ValidationStates</span></span>|<span data-ttu-id="6ab48-121">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="6ab48-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbaritem-parts"></a><span data-ttu-id="6ab48-122">Partes StatusBarItem</span><span class="sxs-lookup"><span data-stu-id="6ab48-122">StatusBarItem Parts</span></span>  
 <span data-ttu-id="6ab48-123">O controle de <xref:System.Windows.Controls.Primitives.StatusBarItem> não tem nenhuma parte nomeada.</span><span class="sxs-lookup"><span data-stu-id="6ab48-123">The <xref:System.Windows.Controls.Primitives.StatusBarItem> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="6ab48-124">Estados StatusBar</span><span class="sxs-lookup"><span data-stu-id="6ab48-124">StatusBar States</span></span>  
 <span data-ttu-id="6ab48-125">A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Controls.Primitives.StatusBarItem>.</span><span class="sxs-lookup"><span data-stu-id="6ab48-125">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBarItem> control.</span></span>  
  
|<span data-ttu-id="6ab48-126">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="6ab48-126">VisualState Name</span></span>|<span data-ttu-id="6ab48-127">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="6ab48-127">VisualStateGroup Name</span></span>|<span data-ttu-id="6ab48-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="6ab48-128">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="6ab48-129">Válido</span><span class="sxs-lookup"><span data-stu-id="6ab48-129">Valid</span></span>|<span data-ttu-id="6ab48-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6ab48-130">ValidationStates</span></span>|<span data-ttu-id="6ab48-131">O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.</span><span class="sxs-lookup"><span data-stu-id="6ab48-131">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="6ab48-132">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="6ab48-132">InvalidFocused</span></span>|<span data-ttu-id="6ab48-133">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6ab48-133">ValidationStates</span></span>|<span data-ttu-id="6ab48-134">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.</span><span class="sxs-lookup"><span data-stu-id="6ab48-134">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="6ab48-135">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="6ab48-135">InvalidUnfocused</span></span>|<span data-ttu-id="6ab48-136">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6ab48-136">ValidationStates</span></span>|<span data-ttu-id="6ab48-137">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="6ab48-137">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbar-controltemplate-example"></a><span data-ttu-id="6ab48-138">Exemplo de ControlTemplate StatusBar</span><span class="sxs-lookup"><span data-stu-id="6ab48-138">StatusBar ControlTemplate Example</span></span>  
 <span data-ttu-id="6ab48-139">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o controle de <xref:System.Windows.Controls.Primitives.StatusBar>.</span><span class="sxs-lookup"><span data-stu-id="6ab48-139">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#StatusBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/statusbar.xaml#statusbar)]  
  
 <span data-ttu-id="6ab48-140">O <xref:System.Windows.Controls.ControlTemplate> usa um ou mais dos recursos a seguir.</span><span class="sxs-lookup"><span data-stu-id="6ab48-140">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="6ab48-141">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="6ab48-141">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ab48-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6ab48-142">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="6ab48-143">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="6ab48-143">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="6ab48-144">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="6ab48-144">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="6ab48-145">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="6ab48-145">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="6ab48-146">Criar um modelo para um controle</span><span class="sxs-lookup"><span data-stu-id="6ab48-146">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
