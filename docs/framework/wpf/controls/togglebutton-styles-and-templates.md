---
title: Estilos e modelos ToggleButton
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], ToggleButton
- ToggleButton [WPF], styles and templates
- ControlTemplate [WPF], ToggleButton
- styles [WPF], ToggleButton
- templates [WPF], ToggleButton
- parts [WPF], ToggleButton
ms.assetid: 54f23f30-4bcb-4f09-8ce4-376a13a255a1
ms.openlocfilehash: e055dcbd557f9b90eb2fe99ad15a05b6f229fd28
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805916"
---
# <a name="togglebutton-styles-and-templates"></a><span data-ttu-id="9b2e8-102">Estilos e modelos ToggleButton</span><span class="sxs-lookup"><span data-stu-id="9b2e8-102">ToggleButton Styles and Templates</span></span>

<span data-ttu-id="9b2e8-103">Este tópico descreve os estilos e <xref:System.Windows.Controls.Primitives.ToggleButton> modelos para o controle.</span><span class="sxs-lookup"><span data-stu-id="9b2e8-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span> <span data-ttu-id="9b2e8-104">Você pode modificar <xref:System.Windows.Controls.ControlTemplate> o padrão para dar ao controle uma aparência única.</span><span class="sxs-lookup"><span data-stu-id="9b2e8-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="9b2e8-105">Para obter mais informações, consulte [Criar um modelo para um controle](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="9b2e8-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>

## <a name="togglebutton-parts"></a><span data-ttu-id="9b2e8-106">Alternar peças de botão</span><span class="sxs-lookup"><span data-stu-id="9b2e8-106">ToggleButton Parts</span></span>

<span data-ttu-id="9b2e8-107">O <xref:System.Windows.Controls.Primitives.ToggleButton> controle não tem nenhuma parte nomeada.</span><span class="sxs-lookup"><span data-stu-id="9b2e8-107">The <xref:System.Windows.Controls.Primitives.ToggleButton> control does not have any named parts.</span></span>

## <a name="togglebutton-states"></a><span data-ttu-id="9b2e8-108">Estados de ToggleButton</span><span class="sxs-lookup"><span data-stu-id="9b2e8-108">ToggleButton States</span></span>

<span data-ttu-id="9b2e8-109">A tabela a seguir lista <xref:System.Windows.Controls.Primitives.ToggleButton> os estados visuais para o controle.</span><span class="sxs-lookup"><span data-stu-id="9b2e8-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>

|<span data-ttu-id="9b2e8-110">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="9b2e8-110">VisualState Name</span></span>|<span data-ttu-id="9b2e8-111">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="9b2e8-111">VisualStateGroup Name</span></span>|<span data-ttu-id="9b2e8-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="9b2e8-112">Description</span></span>|
|-|-|-|
|<span data-ttu-id="9b2e8-113">Normal</span><span class="sxs-lookup"><span data-stu-id="9b2e8-113">Normal</span></span>|<span data-ttu-id="9b2e8-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="9b2e8-114">CommonStates</span></span>|<span data-ttu-id="9b2e8-115">O estado padrão.</span><span class="sxs-lookup"><span data-stu-id="9b2e8-115">The default state.</span></span>|
|<span data-ttu-id="9b2e8-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="9b2e8-116">MouseOver</span></span>|<span data-ttu-id="9b2e8-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="9b2e8-117">CommonStates</span></span>|<span data-ttu-id="9b2e8-118">O ponteiro do mouse é posicionado sobre o controle.</span><span class="sxs-lookup"><span data-stu-id="9b2e8-118">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="9b2e8-119">Pressionado</span><span class="sxs-lookup"><span data-stu-id="9b2e8-119">Pressed</span></span>|<span data-ttu-id="9b2e8-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="9b2e8-120">CommonStates</span></span>|<span data-ttu-id="9b2e8-121">O controle é pressionado.</span><span class="sxs-lookup"><span data-stu-id="9b2e8-121">The control is pressed.</span></span>|
|<span data-ttu-id="9b2e8-122">Desabilitado</span><span class="sxs-lookup"><span data-stu-id="9b2e8-122">Disabled</span></span>|<span data-ttu-id="9b2e8-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="9b2e8-123">CommonStates</span></span>|<span data-ttu-id="9b2e8-124">O controle está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="9b2e8-124">The control is disabled.</span></span>|
|<span data-ttu-id="9b2e8-125">Focalizado</span><span class="sxs-lookup"><span data-stu-id="9b2e8-125">Focused</span></span>|<span data-ttu-id="9b2e8-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="9b2e8-126">FocusStates</span></span>|<span data-ttu-id="9b2e8-127">O controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="9b2e8-127">The control has focus.</span></span>|
|<span data-ttu-id="9b2e8-128">Sem foco</span><span class="sxs-lookup"><span data-stu-id="9b2e8-128">Unfocused</span></span>|<span data-ttu-id="9b2e8-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="9b2e8-129">FocusStates</span></span>|<span data-ttu-id="9b2e8-130">O controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="9b2e8-130">The control does not have focus.</span></span>|
|<span data-ttu-id="9b2e8-131">Verificado</span><span class="sxs-lookup"><span data-stu-id="9b2e8-131">Checked</span></span>|<span data-ttu-id="9b2e8-132">CheckStates</span><span class="sxs-lookup"><span data-stu-id="9b2e8-132">CheckStates</span></span>|<span data-ttu-id="9b2e8-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> é `true`.</span><span class="sxs-lookup"><span data-stu-id="9b2e8-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `true`.</span></span>|
|<span data-ttu-id="9b2e8-134">Desmarcado</span><span class="sxs-lookup"><span data-stu-id="9b2e8-134">Unchecked</span></span>|<span data-ttu-id="9b2e8-135">CheckStates</span><span class="sxs-lookup"><span data-stu-id="9b2e8-135">CheckStates</span></span>|<span data-ttu-id="9b2e8-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> é `false`.</span><span class="sxs-lookup"><span data-stu-id="9b2e8-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `false`.</span></span>|
|<span data-ttu-id="9b2e8-137">Indeterminado</span><span class="sxs-lookup"><span data-stu-id="9b2e8-137">Indeterminate</span></span>|<span data-ttu-id="9b2e8-138">CheckStates</span><span class="sxs-lookup"><span data-stu-id="9b2e8-138">CheckStates</span></span>|<span data-ttu-id="9b2e8-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> é `true` e <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> é `null`.</span><span class="sxs-lookup"><span data-stu-id="9b2e8-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span></span>|
|<span data-ttu-id="9b2e8-140">Válido</span><span class="sxs-lookup"><span data-stu-id="9b2e8-140">Valid</span></span>|<span data-ttu-id="9b2e8-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="9b2e8-141">ValidationStates</span></span>|<span data-ttu-id="9b2e8-142">O controle <xref:System.Windows.Controls.Validation> usa a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> classe e `false`a propriedade anexada é .</span><span class="sxs-lookup"><span data-stu-id="9b2e8-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="9b2e8-143">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="9b2e8-143">InvalidFocused</span></span>|<span data-ttu-id="9b2e8-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="9b2e8-144">ValidationStates</span></span>|<span data-ttu-id="9b2e8-145">A <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` e o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="9b2e8-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|
|<span data-ttu-id="9b2e8-146">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="9b2e8-146">InvalidUnfocused</span></span>|<span data-ttu-id="9b2e8-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="9b2e8-147">ValidationStates</span></span>|<span data-ttu-id="9b2e8-148">A <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` e o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="9b2e8-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|

> [!NOTE]
> <span data-ttu-id="9b2e8-149">Se o estado visual indeterminado não existir no seu modelo de controle, o estado visual desmarcado será usado como estado visual padrão.</span><span class="sxs-lookup"><span data-stu-id="9b2e8-149">If the Indeterminate visual state does not exist in your control template, then the Unchecked visual state will be used as default visual state.</span></span>

## <a name="togglebutton-controltemplate-example"></a><span data-ttu-id="9b2e8-150">Exemplo de modelo de controle de botão de alternar</span><span class="sxs-lookup"><span data-stu-id="9b2e8-150">ToggleButton ControlTemplate Example</span></span>

<span data-ttu-id="9b2e8-151">O exemplo a seguir <xref:System.Windows.Controls.ControlTemplate> mostra <xref:System.Windows.Controls.Primitives.ToggleButton> como definir um para o controle.</span><span class="sxs-lookup"><span data-stu-id="9b2e8-151">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>

[!code-xaml[ControlTemplateExamples#ToggleButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#togglebutton)]

<span data-ttu-id="9b2e8-152">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="9b2e8-152">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="9b2e8-153">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="9b2e8-153">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="9b2e8-154">Confira também</span><span class="sxs-lookup"><span data-stu-id="9b2e8-154">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="9b2e8-155">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="9b2e8-155">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="9b2e8-156">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="9b2e8-156">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="9b2e8-157">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="9b2e8-157">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="9b2e8-158">Crie um modelo para um controle</span><span class="sxs-lookup"><span data-stu-id="9b2e8-158">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
