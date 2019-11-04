---
title: Estilos e modelos PasswordBox
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], PasswordBox
- templates [WPF], PasswordBox
- ControlTemplate [WPF], PasswordBox
- states [WPF], PasswordBox
- PasswordBox [WPF], styles and templates
- parts [WPF], PasswordBox
ms.assetid: deb52107-959f-4a60-b303-d21a0a933060
ms.openlocfilehash: 227ccbda8d570868258508935a5d95f0f40663ab
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458833"
---
# <a name="passwordbox-styles-and-templates"></a><span data-ttu-id="3d0b7-102">Estilos e modelos PasswordBox</span><span class="sxs-lookup"><span data-stu-id="3d0b7-102">PasswordBox Styles and Templates</span></span>

<span data-ttu-id="3d0b7-103">Este tópico descreve os estilos e modelos para o controle de <xref:System.Windows.Controls.PasswordBox>.</span><span class="sxs-lookup"><span data-stu-id="3d0b7-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.PasswordBox> control.</span></span> <span data-ttu-id="3d0b7-104">Você pode modificar o <xref:System.Windows.Controls.ControlTemplate> padrão para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="3d0b7-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="3d0b7-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="3d0b7-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>

## <a name="passwordbox-parts"></a><span data-ttu-id="3d0b7-106">Partes PasswordBox</span><span class="sxs-lookup"><span data-stu-id="3d0b7-106">PasswordBox Parts</span></span>

<span data-ttu-id="3d0b7-107">A tabela a seguir lista as partes nomeadas para o controle de <xref:System.Windows.Controls.PasswordBox>.</span><span class="sxs-lookup"><span data-stu-id="3d0b7-107">The following table lists the named parts for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>

|<span data-ttu-id="3d0b7-108">Parte</span><span class="sxs-lookup"><span data-stu-id="3d0b7-108">Part</span></span>|<span data-ttu-id="3d0b7-109">Digite</span><span class="sxs-lookup"><span data-stu-id="3d0b7-109">Type</span></span>|<span data-ttu-id="3d0b7-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="3d0b7-110">Description</span></span>|
|-|-|-|
|<span data-ttu-id="3d0b7-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="3d0b7-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="3d0b7-112">Um elemento visual que pode conter um <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="3d0b7-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="3d0b7-113">O texto do <xref:System.Windows.Controls.PasswordBox> é exibido neste elemento.</span><span class="sxs-lookup"><span data-stu-id="3d0b7-113">The text of the <xref:System.Windows.Controls.PasswordBox> is displayed in this element.</span></span>|

## <a name="passwordbox-states"></a><span data-ttu-id="3d0b7-114">Estados PasswordBox</span><span class="sxs-lookup"><span data-stu-id="3d0b7-114">PasswordBox States</span></span>

<span data-ttu-id="3d0b7-115">A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Controls.PasswordBox>.</span><span class="sxs-lookup"><span data-stu-id="3d0b7-115">The following table lists the visual states for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>

|<span data-ttu-id="3d0b7-116">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="3d0b7-116">VisualState Name</span></span>|<span data-ttu-id="3d0b7-117">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="3d0b7-117">VisualStateGroup Name</span></span>|<span data-ttu-id="3d0b7-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="3d0b7-118">Description</span></span>|
|-|-|-|
|<span data-ttu-id="3d0b7-119">Normal</span><span class="sxs-lookup"><span data-stu-id="3d0b7-119">Normal</span></span>|<span data-ttu-id="3d0b7-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="3d0b7-120">CommonStates</span></span>|<span data-ttu-id="3d0b7-121">O estado padrão.</span><span class="sxs-lookup"><span data-stu-id="3d0b7-121">The default state.</span></span>|
|<span data-ttu-id="3d0b7-122">MouseOver</span><span class="sxs-lookup"><span data-stu-id="3d0b7-122">MouseOver</span></span>|<span data-ttu-id="3d0b7-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="3d0b7-123">CommonStates</span></span>|<span data-ttu-id="3d0b7-124">O ponteiro do mouse é posicionado sobre o controle.</span><span class="sxs-lookup"><span data-stu-id="3d0b7-124">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="3d0b7-125">Disabled</span><span class="sxs-lookup"><span data-stu-id="3d0b7-125">Disabled</span></span>|<span data-ttu-id="3d0b7-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="3d0b7-126">CommonStates</span></span>|<span data-ttu-id="3d0b7-127">O controle está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="3d0b7-127">The control is disabled.</span></span>|
|<span data-ttu-id="3d0b7-128">Focalizado</span><span class="sxs-lookup"><span data-stu-id="3d0b7-128">Focused</span></span>|<span data-ttu-id="3d0b7-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="3d0b7-129">FocusStates</span></span>|<span data-ttu-id="3d0b7-130">O controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="3d0b7-130">The control has focus.</span></span>|
|<span data-ttu-id="3d0b7-131">Sem foco</span><span class="sxs-lookup"><span data-stu-id="3d0b7-131">Unfocused</span></span>|<span data-ttu-id="3d0b7-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="3d0b7-132">FocusStates</span></span>|<span data-ttu-id="3d0b7-133">O controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="3d0b7-133">The control does not have focus.</span></span>|
|<span data-ttu-id="3d0b7-134">Válido</span><span class="sxs-lookup"><span data-stu-id="3d0b7-134">Valid</span></span>|<span data-ttu-id="3d0b7-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3d0b7-135">ValidationStates</span></span>|<span data-ttu-id="3d0b7-136">O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.</span><span class="sxs-lookup"><span data-stu-id="3d0b7-136">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="3d0b7-137">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="3d0b7-137">InvalidFocused</span></span>|<span data-ttu-id="3d0b7-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3d0b7-138">ValidationStates</span></span>|<span data-ttu-id="3d0b7-139">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.</span><span class="sxs-lookup"><span data-stu-id="3d0b7-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="3d0b7-140">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="3d0b7-140">InvalidUnfocused</span></span>|<span data-ttu-id="3d0b7-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3d0b7-141">ValidationStates</span></span>|<span data-ttu-id="3d0b7-142">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="3d0b7-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

## <a name="passwordbox-controltemplate-example"></a><span data-ttu-id="3d0b7-143">Exemplo de ControlTemplate PasswordBox</span><span class="sxs-lookup"><span data-stu-id="3d0b7-143">PasswordBox ControlTemplate Example</span></span>

<span data-ttu-id="3d0b7-144">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o controle de <xref:System.Windows.Controls.PasswordBox>.</span><span class="sxs-lookup"><span data-stu-id="3d0b7-144">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>

[!code-xaml[ControlTemplateExamples#PasswordBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#passwordbox)]

<span data-ttu-id="3d0b7-145">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="3d0b7-145">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="3d0b7-146">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="3d0b7-146">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="3d0b7-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3d0b7-147">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="3d0b7-148">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="3d0b7-148">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="3d0b7-149">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="3d0b7-149">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="3d0b7-150">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="3d0b7-150">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="3d0b7-151">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="3d0b7-151">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
