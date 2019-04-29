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
ms.openlocfilehash: 64b5b66f7f32ea31b51b4da990ceede4078c27cf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790956"
---
# <a name="statusbar-styles-and-templates"></a><span data-ttu-id="30e84-102">Estilos e modelos StatusBar</span><span class="sxs-lookup"><span data-stu-id="30e84-102">StatusBar Styles and Templates</span></span>
<span data-ttu-id="30e84-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.Primitives.StatusBar> controle.</span><span class="sxs-lookup"><span data-stu-id="30e84-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span> <span data-ttu-id="30e84-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="30e84-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="30e84-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="30e84-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="statusbar-parts"></a><span data-ttu-id="30e84-106">Partes de StatusBar</span><span class="sxs-lookup"><span data-stu-id="30e84-106">StatusBar Parts</span></span>  
 <span data-ttu-id="30e84-107">O <xref:System.Windows.Controls.Primitives.StatusBar> controle não tem nenhuma parte nomeada.</span><span class="sxs-lookup"><span data-stu-id="30e84-107">The <xref:System.Windows.Controls.Primitives.StatusBar> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="30e84-108">Estados de StatusBar</span><span class="sxs-lookup"><span data-stu-id="30e84-108">StatusBar States</span></span>  
 <span data-ttu-id="30e84-109">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.Primitives.StatusBar> controle.</span><span class="sxs-lookup"><span data-stu-id="30e84-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
|<span data-ttu-id="30e84-110">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="30e84-110">VisualState Name</span></span>|<span data-ttu-id="30e84-111">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="30e84-111">VisualStateGroup Name</span></span>|<span data-ttu-id="30e84-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="30e84-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="30e84-113">Válido</span><span class="sxs-lookup"><span data-stu-id="30e84-113">Valid</span></span>|<span data-ttu-id="30e84-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="30e84-114">ValidationStates</span></span>|<span data-ttu-id="30e84-115">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="30e84-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="30e84-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="30e84-116">InvalidFocused</span></span>|<span data-ttu-id="30e84-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="30e84-117">ValidationStates</span></span>|<span data-ttu-id="30e84-118">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="30e84-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="30e84-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="30e84-119">InvalidUnfocused</span></span>|<span data-ttu-id="30e84-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="30e84-120">ValidationStates</span></span>|<span data-ttu-id="30e84-121">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle não tem o foco.</span><span class="sxs-lookup"><span data-stu-id="30e84-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbaritem-parts"></a><span data-ttu-id="30e84-122">StatusBarItem partes</span><span class="sxs-lookup"><span data-stu-id="30e84-122">StatusBarItem Parts</span></span>  
 <span data-ttu-id="30e84-123">O <xref:System.Windows.Controls.Primitives.StatusBarItem> controle não tem nenhuma parte nomeada.</span><span class="sxs-lookup"><span data-stu-id="30e84-123">The <xref:System.Windows.Controls.Primitives.StatusBarItem> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="30e84-124">Estados de StatusBar</span><span class="sxs-lookup"><span data-stu-id="30e84-124">StatusBar States</span></span>  
 <span data-ttu-id="30e84-125">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.Primitives.StatusBarItem> controle.</span><span class="sxs-lookup"><span data-stu-id="30e84-125">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBarItem> control.</span></span>  
  
|<span data-ttu-id="30e84-126">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="30e84-126">VisualState Name</span></span>|<span data-ttu-id="30e84-127">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="30e84-127">VisualStateGroup Name</span></span>|<span data-ttu-id="30e84-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="30e84-128">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="30e84-129">Válido</span><span class="sxs-lookup"><span data-stu-id="30e84-129">Valid</span></span>|<span data-ttu-id="30e84-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="30e84-130">ValidationStates</span></span>|<span data-ttu-id="30e84-131">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="30e84-131">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="30e84-132">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="30e84-132">InvalidFocused</span></span>|<span data-ttu-id="30e84-133">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="30e84-133">ValidationStates</span></span>|<span data-ttu-id="30e84-134">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="30e84-134">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="30e84-135">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="30e84-135">InvalidUnfocused</span></span>|<span data-ttu-id="30e84-136">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="30e84-136">ValidationStates</span></span>|<span data-ttu-id="30e84-137">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle não tem o foco.</span><span class="sxs-lookup"><span data-stu-id="30e84-137">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbar-controltemplate-example"></a><span data-ttu-id="30e84-138">Exemplo de ControlTemplate de StatusBar</span><span class="sxs-lookup"><span data-stu-id="30e84-138">StatusBar ControlTemplate Example</span></span>  
 <span data-ttu-id="30e84-139">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.Primitives.StatusBar> controle.</span><span class="sxs-lookup"><span data-stu-id="30e84-139">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#StatusBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/statusbar.xaml#statusbar)]  
  
 <span data-ttu-id="30e84-140">O <xref:System.Windows.Controls.ControlTemplate> usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="30e84-140">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="30e84-141">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="30e84-141">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30e84-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30e84-142">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="30e84-143">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="30e84-143">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="30e84-144">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="30e84-144">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="30e84-145">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="30e84-145">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="30e84-146">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="30e84-146">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
