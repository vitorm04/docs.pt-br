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
ms.openlocfilehash: b1dd575d58571b845fc849ca432ad440d1ce3ec4
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458265"
---
# <a name="statusbar-styles-and-templates"></a><span data-ttu-id="6dd1b-102">Estilos e modelos StatusBar</span><span class="sxs-lookup"><span data-stu-id="6dd1b-102">StatusBar Styles and Templates</span></span>
<span data-ttu-id="6dd1b-103">Este tópico descreve os estilos e modelos para o controle de <xref:System.Windows.Controls.Primitives.StatusBar>.</span><span class="sxs-lookup"><span data-stu-id="6dd1b-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span> <span data-ttu-id="6dd1b-104">Você pode modificar o <xref:System.Windows.Controls.ControlTemplate> padrão para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="6dd1b-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="6dd1b-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="6dd1b-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="statusbar-parts"></a><span data-ttu-id="6dd1b-106">Partes StatusBar</span><span class="sxs-lookup"><span data-stu-id="6dd1b-106">StatusBar Parts</span></span>  
 <span data-ttu-id="6dd1b-107">O controle de <xref:System.Windows.Controls.Primitives.StatusBar> não tem nenhuma parte nomeada.</span><span class="sxs-lookup"><span data-stu-id="6dd1b-107">The <xref:System.Windows.Controls.Primitives.StatusBar> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="6dd1b-108">Estados StatusBar</span><span class="sxs-lookup"><span data-stu-id="6dd1b-108">StatusBar States</span></span>  
 <span data-ttu-id="6dd1b-109">A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Controls.Primitives.StatusBar>.</span><span class="sxs-lookup"><span data-stu-id="6dd1b-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
|<span data-ttu-id="6dd1b-110">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="6dd1b-110">VisualState Name</span></span>|<span data-ttu-id="6dd1b-111">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="6dd1b-111">VisualStateGroup Name</span></span>|<span data-ttu-id="6dd1b-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="6dd1b-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="6dd1b-113">Válido</span><span class="sxs-lookup"><span data-stu-id="6dd1b-113">Valid</span></span>|<span data-ttu-id="6dd1b-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6dd1b-114">ValidationStates</span></span>|<span data-ttu-id="6dd1b-115">O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.</span><span class="sxs-lookup"><span data-stu-id="6dd1b-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="6dd1b-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="6dd1b-116">InvalidFocused</span></span>|<span data-ttu-id="6dd1b-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6dd1b-117">ValidationStates</span></span>|<span data-ttu-id="6dd1b-118">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.</span><span class="sxs-lookup"><span data-stu-id="6dd1b-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="6dd1b-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="6dd1b-119">InvalidUnfocused</span></span>|<span data-ttu-id="6dd1b-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6dd1b-120">ValidationStates</span></span>|<span data-ttu-id="6dd1b-121">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="6dd1b-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbaritem-parts"></a><span data-ttu-id="6dd1b-122">Partes StatusBarItem</span><span class="sxs-lookup"><span data-stu-id="6dd1b-122">StatusBarItem Parts</span></span>  
 <span data-ttu-id="6dd1b-123">O controle de <xref:System.Windows.Controls.Primitives.StatusBarItem> não tem nenhuma parte nomeada.</span><span class="sxs-lookup"><span data-stu-id="6dd1b-123">The <xref:System.Windows.Controls.Primitives.StatusBarItem> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="6dd1b-124">Estados StatusBar</span><span class="sxs-lookup"><span data-stu-id="6dd1b-124">StatusBar States</span></span>  
 <span data-ttu-id="6dd1b-125">A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Controls.Primitives.StatusBarItem>.</span><span class="sxs-lookup"><span data-stu-id="6dd1b-125">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBarItem> control.</span></span>  
  
|<span data-ttu-id="6dd1b-126">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="6dd1b-126">VisualState Name</span></span>|<span data-ttu-id="6dd1b-127">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="6dd1b-127">VisualStateGroup Name</span></span>|<span data-ttu-id="6dd1b-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="6dd1b-128">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="6dd1b-129">Válido</span><span class="sxs-lookup"><span data-stu-id="6dd1b-129">Valid</span></span>|<span data-ttu-id="6dd1b-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6dd1b-130">ValidationStates</span></span>|<span data-ttu-id="6dd1b-131">O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.</span><span class="sxs-lookup"><span data-stu-id="6dd1b-131">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="6dd1b-132">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="6dd1b-132">InvalidFocused</span></span>|<span data-ttu-id="6dd1b-133">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6dd1b-133">ValidationStates</span></span>|<span data-ttu-id="6dd1b-134">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.</span><span class="sxs-lookup"><span data-stu-id="6dd1b-134">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="6dd1b-135">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="6dd1b-135">InvalidUnfocused</span></span>|<span data-ttu-id="6dd1b-136">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6dd1b-136">ValidationStates</span></span>|<span data-ttu-id="6dd1b-137">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="6dd1b-137">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbar-controltemplate-example"></a><span data-ttu-id="6dd1b-138">Exemplo de ControlTemplate StatusBar</span><span class="sxs-lookup"><span data-stu-id="6dd1b-138">StatusBar ControlTemplate Example</span></span>  
 <span data-ttu-id="6dd1b-139">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o controle de <xref:System.Windows.Controls.Primitives.StatusBar>.</span><span class="sxs-lookup"><span data-stu-id="6dd1b-139">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#StatusBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/statusbar.xaml#statusbar)]  
  
 <span data-ttu-id="6dd1b-140">O <xref:System.Windows.Controls.ControlTemplate> usa um ou mais dos recursos a seguir.</span><span class="sxs-lookup"><span data-stu-id="6dd1b-140">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="6dd1b-141">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="6dd1b-141">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dd1b-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6dd1b-142">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="6dd1b-143">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="6dd1b-143">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="6dd1b-144">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="6dd1b-144">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="6dd1b-145">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="6dd1b-145">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="6dd1b-146">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="6dd1b-146">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
