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
ms.openlocfilehash: 42bf7aa672addadbc4205c796c09914fe8f3054d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372467"
---
# <a name="statusbar-styles-and-templates"></a><span data-ttu-id="997e8-102">Estilos e modelos StatusBar</span><span class="sxs-lookup"><span data-stu-id="997e8-102">StatusBar Styles and Templates</span></span>
<span data-ttu-id="997e8-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.Primitives.StatusBar> controle.</span><span class="sxs-lookup"><span data-stu-id="997e8-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span> <span data-ttu-id="997e8-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="997e8-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="997e8-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="997e8-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="statusbar-parts"></a><span data-ttu-id="997e8-106">Partes de StatusBar</span><span class="sxs-lookup"><span data-stu-id="997e8-106">StatusBar Parts</span></span>  
 <span data-ttu-id="997e8-107">O <xref:System.Windows.Controls.Primitives.StatusBar> controle não tem nenhuma parte nomeada.</span><span class="sxs-lookup"><span data-stu-id="997e8-107">The <xref:System.Windows.Controls.Primitives.StatusBar> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="997e8-108">Estados de StatusBar</span><span class="sxs-lookup"><span data-stu-id="997e8-108">StatusBar States</span></span>  
 <span data-ttu-id="997e8-109">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.Primitives.StatusBar> controle.</span><span class="sxs-lookup"><span data-stu-id="997e8-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
|<span data-ttu-id="997e8-110">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="997e8-110">VisualState Name</span></span>|<span data-ttu-id="997e8-111">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="997e8-111">VisualStateGroup Name</span></span>|<span data-ttu-id="997e8-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="997e8-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="997e8-113">Válido</span><span class="sxs-lookup"><span data-stu-id="997e8-113">Valid</span></span>|<span data-ttu-id="997e8-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="997e8-114">ValidationStates</span></span>|<span data-ttu-id="997e8-115">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="997e8-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="997e8-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="997e8-116">InvalidFocused</span></span>|<span data-ttu-id="997e8-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="997e8-117">ValidationStates</span></span>|<span data-ttu-id="997e8-118">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="997e8-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="997e8-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="997e8-119">InvalidUnfocused</span></span>|<span data-ttu-id="997e8-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="997e8-120">ValidationStates</span></span>|<span data-ttu-id="997e8-121">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle não tem o foco.</span><span class="sxs-lookup"><span data-stu-id="997e8-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbaritem-parts"></a><span data-ttu-id="997e8-122">StatusBarItem partes</span><span class="sxs-lookup"><span data-stu-id="997e8-122">StatusBarItem Parts</span></span>  
 <span data-ttu-id="997e8-123">O <xref:System.Windows.Controls.Primitives.StatusBarItem> controle não tem nenhuma parte nomeada.</span><span class="sxs-lookup"><span data-stu-id="997e8-123">The <xref:System.Windows.Controls.Primitives.StatusBarItem> control does not have any named parts.</span></span>  
  
## <a name="statusbar-states"></a><span data-ttu-id="997e8-124">Estados de StatusBar</span><span class="sxs-lookup"><span data-stu-id="997e8-124">StatusBar States</span></span>  
 <span data-ttu-id="997e8-125">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.Primitives.StatusBarItem> controle.</span><span class="sxs-lookup"><span data-stu-id="997e8-125">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.StatusBarItem> control.</span></span>  
  
|<span data-ttu-id="997e8-126">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="997e8-126">VisualState Name</span></span>|<span data-ttu-id="997e8-127">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="997e8-127">VisualStateGroup Name</span></span>|<span data-ttu-id="997e8-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="997e8-128">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="997e8-129">Válido</span><span class="sxs-lookup"><span data-stu-id="997e8-129">Valid</span></span>|<span data-ttu-id="997e8-130">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="997e8-130">ValidationStates</span></span>|<span data-ttu-id="997e8-131">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="997e8-131">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="997e8-132">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="997e8-132">InvalidFocused</span></span>|<span data-ttu-id="997e8-133">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="997e8-133">ValidationStates</span></span>|<span data-ttu-id="997e8-134">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="997e8-134">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="997e8-135">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="997e8-135">InvalidUnfocused</span></span>|<span data-ttu-id="997e8-136">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="997e8-136">ValidationStates</span></span>|<span data-ttu-id="997e8-137">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle não tem o foco.</span><span class="sxs-lookup"><span data-stu-id="997e8-137">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="statusbar-controltemplate-example"></a><span data-ttu-id="997e8-138">Exemplo de ControlTemplate de StatusBar</span><span class="sxs-lookup"><span data-stu-id="997e8-138">StatusBar ControlTemplate Example</span></span>  
 <span data-ttu-id="997e8-139">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.Primitives.StatusBar> controle.</span><span class="sxs-lookup"><span data-stu-id="997e8-139">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.StatusBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#StatusBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/statusbar.xaml#statusbar)]  
  
 <span data-ttu-id="997e8-140">O <xref:System.Windows.Controls.ControlTemplate> usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="997e8-140">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="997e8-141">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="997e8-141">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="997e8-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="997e8-142">See also</span></span>
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="997e8-143">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="997e8-143">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="997e8-144">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="997e8-144">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="997e8-145">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="997e8-145">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="997e8-146">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="997e8-146">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
