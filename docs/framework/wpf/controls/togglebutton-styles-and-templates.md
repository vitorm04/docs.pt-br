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
ms.openlocfilehash: 981a487b9935a86595a9caca03b4371326924642
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458228"
---
# <a name="togglebutton-styles-and-templates"></a><span data-ttu-id="10b6a-102">Estilos e modelos ToggleButton</span><span class="sxs-lookup"><span data-stu-id="10b6a-102">ToggleButton Styles and Templates</span></span>

<span data-ttu-id="10b6a-103">Este tópico descreve os estilos e modelos para o controle de <xref:System.Windows.Controls.Primitives.ToggleButton>.</span><span class="sxs-lookup"><span data-stu-id="10b6a-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span> <span data-ttu-id="10b6a-104">Você pode modificar o <xref:System.Windows.Controls.ControlTemplate> padrão para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="10b6a-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="10b6a-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="10b6a-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>

## <a name="togglebutton-parts"></a><span data-ttu-id="10b6a-106">Partes de ToggleButton</span><span class="sxs-lookup"><span data-stu-id="10b6a-106">ToggleButton Parts</span></span>

<span data-ttu-id="10b6a-107">O controle de <xref:System.Windows.Controls.Primitives.ToggleButton> não tem nenhuma parte nomeada.</span><span class="sxs-lookup"><span data-stu-id="10b6a-107">The <xref:System.Windows.Controls.Primitives.ToggleButton> control does not have any named parts.</span></span>

## <a name="togglebutton-states"></a><span data-ttu-id="10b6a-108">Estados de ToggleButton</span><span class="sxs-lookup"><span data-stu-id="10b6a-108">ToggleButton States</span></span>

<span data-ttu-id="10b6a-109">A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Controls.Primitives.ToggleButton>.</span><span class="sxs-lookup"><span data-stu-id="10b6a-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>

|<span data-ttu-id="10b6a-110">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="10b6a-110">VisualState Name</span></span>|<span data-ttu-id="10b6a-111">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="10b6a-111">VisualStateGroup Name</span></span>|<span data-ttu-id="10b6a-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="10b6a-112">Description</span></span>|
|-|-|-|
|<span data-ttu-id="10b6a-113">Normal</span><span class="sxs-lookup"><span data-stu-id="10b6a-113">Normal</span></span>|<span data-ttu-id="10b6a-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="10b6a-114">CommonStates</span></span>|<span data-ttu-id="10b6a-115">O estado padrão.</span><span class="sxs-lookup"><span data-stu-id="10b6a-115">The default state.</span></span>|
|<span data-ttu-id="10b6a-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="10b6a-116">MouseOver</span></span>|<span data-ttu-id="10b6a-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="10b6a-117">CommonStates</span></span>|<span data-ttu-id="10b6a-118">O ponteiro do mouse é posicionado sobre o controle.</span><span class="sxs-lookup"><span data-stu-id="10b6a-118">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="10b6a-119">Pressionado</span><span class="sxs-lookup"><span data-stu-id="10b6a-119">Pressed</span></span>|<span data-ttu-id="10b6a-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="10b6a-120">CommonStates</span></span>|<span data-ttu-id="10b6a-121">O controle é pressionado.</span><span class="sxs-lookup"><span data-stu-id="10b6a-121">The control is pressed.</span></span>|
|<span data-ttu-id="10b6a-122">Disabled</span><span class="sxs-lookup"><span data-stu-id="10b6a-122">Disabled</span></span>|<span data-ttu-id="10b6a-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="10b6a-123">CommonStates</span></span>|<span data-ttu-id="10b6a-124">O controle está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="10b6a-124">The control is disabled.</span></span>|
|<span data-ttu-id="10b6a-125">Focalizado</span><span class="sxs-lookup"><span data-stu-id="10b6a-125">Focused</span></span>|<span data-ttu-id="10b6a-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="10b6a-126">FocusStates</span></span>|<span data-ttu-id="10b6a-127">O controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="10b6a-127">The control has focus.</span></span>|
|<span data-ttu-id="10b6a-128">Sem foco</span><span class="sxs-lookup"><span data-stu-id="10b6a-128">Unfocused</span></span>|<span data-ttu-id="10b6a-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="10b6a-129">FocusStates</span></span>|<span data-ttu-id="10b6a-130">O controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="10b6a-130">The control does not have focus.</span></span>|
|<span data-ttu-id="10b6a-131">Selecionado</span><span class="sxs-lookup"><span data-stu-id="10b6a-131">Checked</span></span>|<span data-ttu-id="10b6a-132">CheckStates</span><span class="sxs-lookup"><span data-stu-id="10b6a-132">CheckStates</span></span>|<span data-ttu-id="10b6a-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> é `true`.</span><span class="sxs-lookup"><span data-stu-id="10b6a-133"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `true`.</span></span>|
|<span data-ttu-id="10b6a-134">Não Selecionado</span><span class="sxs-lookup"><span data-stu-id="10b6a-134">Unchecked</span></span>|<span data-ttu-id="10b6a-135">CheckStates</span><span class="sxs-lookup"><span data-stu-id="10b6a-135">CheckStates</span></span>|<span data-ttu-id="10b6a-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> é `false`.</span><span class="sxs-lookup"><span data-stu-id="10b6a-136"><xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `false`.</span></span>|
|<span data-ttu-id="10b6a-137">Indeterminado</span><span class="sxs-lookup"><span data-stu-id="10b6a-137">Indeterminate</span></span>|<span data-ttu-id="10b6a-138">CheckStates</span><span class="sxs-lookup"><span data-stu-id="10b6a-138">CheckStates</span></span>|<span data-ttu-id="10b6a-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> é `true` e <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> é `null`.</span><span class="sxs-lookup"><span data-stu-id="10b6a-139"><xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> is `true`, and <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> is `null`.</span></span>|
|<span data-ttu-id="10b6a-140">Válido</span><span class="sxs-lookup"><span data-stu-id="10b6a-140">Valid</span></span>|<span data-ttu-id="10b6a-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="10b6a-141">ValidationStates</span></span>|<span data-ttu-id="10b6a-142">O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.</span><span class="sxs-lookup"><span data-stu-id="10b6a-142">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="10b6a-143">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="10b6a-143">InvalidFocused</span></span>|<span data-ttu-id="10b6a-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="10b6a-144">ValidationStates</span></span>|<span data-ttu-id="10b6a-145">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.</span><span class="sxs-lookup"><span data-stu-id="10b6a-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="10b6a-146">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="10b6a-146">InvalidUnfocused</span></span>|<span data-ttu-id="10b6a-147">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="10b6a-147">ValidationStates</span></span>|<span data-ttu-id="10b6a-148">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="10b6a-148">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

> [!NOTE]
> <span data-ttu-id="10b6a-149">Se o estado visual indeterminado não existir no seu modelo de controle, o estado visual desmarcado será usado como o estado visual padrão.</span><span class="sxs-lookup"><span data-stu-id="10b6a-149">If the Indeterminate visual state does not exist in your control template, then the Unchecked visual state will be used as default visual state.</span></span>

## <a name="togglebutton-controltemplate-example"></a><span data-ttu-id="10b6a-150">Exemplo de ControlTemplate de ToggleButton</span><span class="sxs-lookup"><span data-stu-id="10b6a-150">ToggleButton ControlTemplate Example</span></span>

<span data-ttu-id="10b6a-151">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o controle de <xref:System.Windows.Controls.Primitives.ToggleButton>.</span><span class="sxs-lookup"><span data-stu-id="10b6a-151">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ToggleButton> control.</span></span>

[!code-xaml[ControlTemplateExamples#ToggleButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#togglebutton)]

<span data-ttu-id="10b6a-152">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="10b6a-152">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="10b6a-153">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="10b6a-153">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="10b6a-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="10b6a-154">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="10b6a-155">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="10b6a-155">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="10b6a-156">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="10b6a-156">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="10b6a-157">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="10b6a-157">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="10b6a-158">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="10b6a-158">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
