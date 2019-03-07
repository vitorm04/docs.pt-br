---
title: ToggleButton estilos e modelos
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], ToggleButton
- ToggleButton [WPF], styles and templates
- ControlTemplate [WPF], ToggleButton
- styles [WPF], ToggleButton
- templates [WPF], ToggleButton
- parts [WPF], ToggleButton
ms.assetid: 54f23f30-4bcb-4f09-8ce4-376a13a255a1
ms.openlocfilehash: 46fd7d07c3904ee752ae3f467f65af4b0c031c84
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57509505"
---
# <a name="togglebutton-styles-and-templates"></a><span data-ttu-id="aadad-102">ToggleButton estilos e modelos</span><span class="sxs-lookup"><span data-stu-id="aadad-102">ToggleButton Styles and Templates</span></span>

<span data-ttu-id="aadad-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.Primitives.ToggleButton> controle.</span><span class="sxs-lookup"><span data-stu-id="aadad-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span> <span data-ttu-id="aadad-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="aadad-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="aadad-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="aadad-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>

## <a name="togglebutton-parts"></a><span data-ttu-id="aadad-106">Partes de ToggleButton</span><span class="sxs-lookup"><span data-stu-id="aadad-106">ToggleButton Parts</span></span>

<span data-ttu-id="aadad-107">O <xref:System.Windows.Controls.Primitives.ToggleButton> controle não tem nenhuma parte nomeada.</span><span class="sxs-lookup"><span data-stu-id="aadad-107">The <xref:System.Windows.Controls.Primitives.ToggleButton> control does not have any named parts.</span></span>

## <a name="togglebutton-states"></a><span data-ttu-id="aadad-108">Estados de ToggleButton</span><span class="sxs-lookup"><span data-stu-id="aadad-108">ToggleButton States</span></span>

<span data-ttu-id="aadad-109">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.Primitives.ToggleButton> controle.</span><span class="sxs-lookup"><span data-stu-id="aadad-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>

|<span data-ttu-id="aadad-110">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="aadad-110">VisualState Name</span></span>|<span data-ttu-id="aadad-111">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="aadad-111">VisualStateGroup Name</span></span>|<span data-ttu-id="aadad-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="aadad-112">Description</span></span>|
|-|-|-|
|<span data-ttu-id="aadad-113">Normal</span><span class="sxs-lookup"><span data-stu-id="aadad-113">Normal</span></span>|<span data-ttu-id="aadad-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="aadad-114">CommonStates</span></span>|<span data-ttu-id="aadad-115">O estado padrão.</span><span class="sxs-lookup"><span data-stu-id="aadad-115">The default state.</span></span>|
|<span data-ttu-id="aadad-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="aadad-116">MouseOver</span></span>|<span data-ttu-id="aadad-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="aadad-117">CommonStates</span></span>|<span data-ttu-id="aadad-118">O ponteiro do mouse é posicionado sobre o controle.</span><span class="sxs-lookup"><span data-stu-id="aadad-118">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="aadad-119">Pressionado</span><span class="sxs-lookup"><span data-stu-id="aadad-119">Pressed</span></span>|<span data-ttu-id="aadad-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="aadad-120">CommonStates</span></span>|<span data-ttu-id="aadad-121">O controle é pressionado.</span><span class="sxs-lookup"><span data-stu-id="aadad-121">The control is pressed.</span></span>|
|<span data-ttu-id="aadad-122">Disabled</span><span class="sxs-lookup"><span data-stu-id="aadad-122">Disabled</span></span>|<span data-ttu-id="aadad-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="aadad-123">CommonStates</span></span>|<span data-ttu-id="aadad-124">O controle está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="aadad-124">The control is disabled.</span></span>|
|<span data-ttu-id="aadad-125">Focalizado</span><span class="sxs-lookup"><span data-stu-id="aadad-125">Focused</span></span>|<span data-ttu-id="aadad-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="aadad-126">FocusStates</span></span>|<span data-ttu-id="aadad-127">O controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="aadad-127">The control has focus.</span></span>|
|<span data-ttu-id="aadad-128">Sem foco</span><span class="sxs-lookup"><span data-stu-id="aadad-128">Unfocused</span></span>|<span data-ttu-id="aadad-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="aadad-129">FocusStates</span></span>|<span data-ttu-id="aadad-130">O controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="aadad-130">The control does not have focus.</span></span>|
|<span data-ttu-id="aadad-131">Selecionado</span><span class="sxs-lookup"><span data-stu-id="aadad-131">Checked</span></span>|<span data-ttu-id="aadad-132">CheckStates</span><span class="sxs-lookup"><span data-stu-id="aadad-132">CheckStates</span></span>|<span data-ttu-id="aadad-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> é `true`.</span><span class="sxs-lookup"><span data-stu-id="aadad-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `true`.</span></span>|
|<span data-ttu-id="aadad-134">Não Selecionado</span><span class="sxs-lookup"><span data-stu-id="aadad-134">Unchecked</span></span>|<span data-ttu-id="aadad-135">CheckStates</span><span class="sxs-lookup"><span data-stu-id="aadad-135">CheckStates</span></span>|<span data-ttu-id="aadad-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> é `false`.</span><span class="sxs-lookup"><span data-stu-id="aadad-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `false`.</span></span>|
|<span data-ttu-id="aadad-137">Indeterminado</span><span class="sxs-lookup"><span data-stu-id="aadad-137">Indeterminate</span></span>|<span data-ttu-id="aadad-138">CheckStates</span><span class="sxs-lookup"><span data-stu-id="aadad-138">CheckStates</span></span>|<span data-ttu-id="aadad-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> é `true` e <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> é `null`.</span><span class="sxs-lookup"><span data-stu-id="aadad-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span></span>|
|<span data-ttu-id="aadad-140">Válido</span><span class="sxs-lookup"><span data-stu-id="aadad-140">Valid</span></span>|<span data-ttu-id="aadad-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="aadad-141">ValidationStates</span></span>|<span data-ttu-id="aadad-142">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="aadad-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="aadad-143">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="aadad-143">InvalidFocused</span></span>|<span data-ttu-id="aadad-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="aadad-144">ValidationStates</span></span>|<span data-ttu-id="aadad-145">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="aadad-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="aadad-146">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="aadad-146">InvalidUnfocused</span></span>|<span data-ttu-id="aadad-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="aadad-147">ValidationStates</span></span>|<span data-ttu-id="aadad-148">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle não tem o foco.</span><span class="sxs-lookup"><span data-stu-id="aadad-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

> [!NOTE]
> <span data-ttu-id="aadad-149">Se o estado visual indeterminado não existe em seu modelo de controle, em seguida, o estado visual não selecionado será usado como estado visual padrão.</span><span class="sxs-lookup"><span data-stu-id="aadad-149">If the Indeterminate visual state does not exist in your control template, then the Unchecked visual state will be used as default visual state.</span></span>

## <a name="togglebutton-controltemplate-example"></a><span data-ttu-id="aadad-150">Exemplo de ControlTemplate de ToggleButton</span><span class="sxs-lookup"><span data-stu-id="aadad-150">ToggleButton ControlTemplate Example</span></span>

<span data-ttu-id="aadad-151">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.Primitives.ToggleButton> controle.</span><span class="sxs-lookup"><span data-stu-id="aadad-151">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>

[!code-xaml[ControlTemplateExamples#ToggleButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#togglebutton)]

<span data-ttu-id="aadad-152">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="aadad-152">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="aadad-153">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="aadad-153">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="aadad-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aadad-154">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="aadad-155">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="aadad-155">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="aadad-156">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="aadad-156">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="aadad-157">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="aadad-157">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="aadad-158">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="aadad-158">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
