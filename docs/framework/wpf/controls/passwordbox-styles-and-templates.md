---
title: Modelos e estilos PasswordBox
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], PasswordBox
- templates [WPF], PasswordBox
- ControlTemplate [WPF], PasswordBox
- states [WPF], PasswordBox
- PasswordBox [WPF], styles and templates
- parts [WPF], PasswordBox
ms.assetid: deb52107-959f-4a60-b303-d21a0a933060
ms.openlocfilehash: 7783330dd56ec5b2759e783a6935761eb3587978
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57509525"
---
# <a name="passwordbox-styles-and-templates"></a><span data-ttu-id="464e7-102">Modelos e estilos PasswordBox</span><span class="sxs-lookup"><span data-stu-id="464e7-102">PasswordBox Styles and Templates</span></span>

<span data-ttu-id="464e7-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.PasswordBox> controle.</span><span class="sxs-lookup"><span data-stu-id="464e7-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.PasswordBox> control.</span></span> <span data-ttu-id="464e7-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="464e7-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="464e7-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="464e7-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>

## <a name="passwordbox-parts"></a><span data-ttu-id="464e7-106">Partes de PasswordBox</span><span class="sxs-lookup"><span data-stu-id="464e7-106">PasswordBox Parts</span></span>

<span data-ttu-id="464e7-107">A tabela a seguir lista as partes nomeadas para o <xref:System.Windows.Controls.PasswordBox> controle.</span><span class="sxs-lookup"><span data-stu-id="464e7-107">The following table lists the named parts for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>

|<span data-ttu-id="464e7-108">Parte</span><span class="sxs-lookup"><span data-stu-id="464e7-108">Part</span></span>|<span data-ttu-id="464e7-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="464e7-109">Type</span></span>|<span data-ttu-id="464e7-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="464e7-110">Description</span></span>|
|-|-|-|
|<span data-ttu-id="464e7-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="464e7-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="464e7-112">Um elemento visual que pode conter um <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="464e7-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="464e7-113">O texto do <xref:System.Windows.Controls.PasswordBox> é exibido neste elemento.</span><span class="sxs-lookup"><span data-stu-id="464e7-113">The text of the <xref:System.Windows.Controls.PasswordBox> is displayed in this element.</span></span>|

## <a name="passwordbox-states"></a><span data-ttu-id="464e7-114">Estados de PasswordBox</span><span class="sxs-lookup"><span data-stu-id="464e7-114">PasswordBox States</span></span>

<span data-ttu-id="464e7-115">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.PasswordBox> controle.</span><span class="sxs-lookup"><span data-stu-id="464e7-115">The following table lists the visual states for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>

|<span data-ttu-id="464e7-116">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="464e7-116">VisualState Name</span></span>|<span data-ttu-id="464e7-117">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="464e7-117">VisualStateGroup Name</span></span>|<span data-ttu-id="464e7-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="464e7-118">Description</span></span>|
|-|-|-|
|<span data-ttu-id="464e7-119">Normal</span><span class="sxs-lookup"><span data-stu-id="464e7-119">Normal</span></span>|<span data-ttu-id="464e7-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="464e7-120">CommonStates</span></span>|<span data-ttu-id="464e7-121">O estado padrão.</span><span class="sxs-lookup"><span data-stu-id="464e7-121">The default state.</span></span>|
|<span data-ttu-id="464e7-122">MouseOver</span><span class="sxs-lookup"><span data-stu-id="464e7-122">MouseOver</span></span>|<span data-ttu-id="464e7-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="464e7-123">CommonStates</span></span>|<span data-ttu-id="464e7-124">O ponteiro do mouse é posicionado sobre o controle.</span><span class="sxs-lookup"><span data-stu-id="464e7-124">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="464e7-125">Disabled</span><span class="sxs-lookup"><span data-stu-id="464e7-125">Disabled</span></span>|<span data-ttu-id="464e7-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="464e7-126">CommonStates</span></span>|<span data-ttu-id="464e7-127">O controle está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="464e7-127">The control is disabled.</span></span>|
|<span data-ttu-id="464e7-128">Focalizado</span><span class="sxs-lookup"><span data-stu-id="464e7-128">Focused</span></span>|<span data-ttu-id="464e7-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="464e7-129">FocusStates</span></span>|<span data-ttu-id="464e7-130">O controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="464e7-130">The control has focus.</span></span>|
|<span data-ttu-id="464e7-131">Sem foco</span><span class="sxs-lookup"><span data-stu-id="464e7-131">Unfocused</span></span>|<span data-ttu-id="464e7-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="464e7-132">FocusStates</span></span>|<span data-ttu-id="464e7-133">O controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="464e7-133">The control does not have focus.</span></span>|
|<span data-ttu-id="464e7-134">Válido</span><span class="sxs-lookup"><span data-stu-id="464e7-134">Valid</span></span>|<span data-ttu-id="464e7-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="464e7-135">ValidationStates</span></span>|<span data-ttu-id="464e7-136">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="464e7-136">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="464e7-137">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="464e7-137">InvalidFocused</span></span>|<span data-ttu-id="464e7-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="464e7-138">ValidationStates</span></span>|<span data-ttu-id="464e7-139">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="464e7-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="464e7-140">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="464e7-140">InvalidUnfocused</span></span>|<span data-ttu-id="464e7-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="464e7-141">ValidationStates</span></span>|<span data-ttu-id="464e7-142">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle não tem o foco.</span><span class="sxs-lookup"><span data-stu-id="464e7-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

## <a name="passwordbox-controltemplate-example"></a><span data-ttu-id="464e7-143">Exemplo de ControlTemplate de PasswordBox</span><span class="sxs-lookup"><span data-stu-id="464e7-143">PasswordBox ControlTemplate Example</span></span>

<span data-ttu-id="464e7-144">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.PasswordBox> controle.</span><span class="sxs-lookup"><span data-stu-id="464e7-144">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>

[!code-xaml[ControlTemplateExamples#PasswordBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#passwordbox)]

<span data-ttu-id="464e7-145">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="464e7-145">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="464e7-146">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="464e7-146">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="464e7-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="464e7-147">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="464e7-148">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="464e7-148">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="464e7-149">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="464e7-149">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="464e7-150">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="464e7-150">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="464e7-151">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="464e7-151">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
