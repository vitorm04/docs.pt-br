---
title: Estilos e modelos Thumb
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], Thumb
- styles [WPF], Thumb
- templates [WPF], Thumb
- Thumb [WPF], styles and templates
- ControlTemplate [WPF], Thumb
- parts [WPF], Thumb
ms.assetid: 86a49235-62d9-414e-923e-53126e3f930a
ms.openlocfilehash: c2114a02016db96d898a394b6892b6d3042d81ff
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458241"
---
# <a name="thumb-styles-and-templates"></a><span data-ttu-id="05ca3-102">Estilos e modelos Thumb</span><span class="sxs-lookup"><span data-stu-id="05ca3-102">Thumb Styles and Templates</span></span>

<span data-ttu-id="05ca3-103">Este tópico descreve os estilos e modelos para o controle de <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="05ca3-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span> <span data-ttu-id="05ca3-104">Você pode modificar o <xref:System.Windows.Controls.ControlTemplate> padrão para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="05ca3-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="05ca3-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="05ca3-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>

## <a name="thumb-parts"></a><span data-ttu-id="05ca3-106">Peças Thumb</span><span class="sxs-lookup"><span data-stu-id="05ca3-106">Thumb Parts</span></span>

<span data-ttu-id="05ca3-107">O controle de <xref:System.Windows.Controls.Primitives.Thumb> não tem nenhuma parte nomeada.</span><span class="sxs-lookup"><span data-stu-id="05ca3-107">The <xref:System.Windows.Controls.Primitives.Thumb> control does not have any named parts.</span></span>

## <a name="thumb-states"></a><span data-ttu-id="05ca3-108">Estados de polegar</span><span class="sxs-lookup"><span data-stu-id="05ca3-108">Thumb States</span></span>

<span data-ttu-id="05ca3-109">A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="05ca3-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>

|<span data-ttu-id="05ca3-110">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="05ca3-110">VisualState Name</span></span>|<span data-ttu-id="05ca3-111">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="05ca3-111">VisualStateGroup Name</span></span>|<span data-ttu-id="05ca3-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="05ca3-112">Description</span></span>|
|-|-|-|
|<span data-ttu-id="05ca3-113">Normal</span><span class="sxs-lookup"><span data-stu-id="05ca3-113">Normal</span></span>|<span data-ttu-id="05ca3-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="05ca3-114">CommonStates</span></span>|<span data-ttu-id="05ca3-115">O estado padrão.</span><span class="sxs-lookup"><span data-stu-id="05ca3-115">The default state.</span></span>|
|<span data-ttu-id="05ca3-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="05ca3-116">MouseOver</span></span>|<span data-ttu-id="05ca3-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="05ca3-117">CommonStates</span></span>|<span data-ttu-id="05ca3-118">O ponteiro do mouse é posicionado sobre o controle.</span><span class="sxs-lookup"><span data-stu-id="05ca3-118">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="05ca3-119">Pressionado</span><span class="sxs-lookup"><span data-stu-id="05ca3-119">Pressed</span></span>|<span data-ttu-id="05ca3-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="05ca3-120">CommonStates</span></span>|<span data-ttu-id="05ca3-121">O controle é pressionado.</span><span class="sxs-lookup"><span data-stu-id="05ca3-121">The control is pressed.</span></span>|
|<span data-ttu-id="05ca3-122">Disabled</span><span class="sxs-lookup"><span data-stu-id="05ca3-122">Disabled</span></span>|<span data-ttu-id="05ca3-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="05ca3-123">CommonStates</span></span>|<span data-ttu-id="05ca3-124">O controle está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="05ca3-124">The control is disabled.</span></span>|
|<span data-ttu-id="05ca3-125">Focalizado</span><span class="sxs-lookup"><span data-stu-id="05ca3-125">Focused</span></span>|<span data-ttu-id="05ca3-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="05ca3-126">FocusStates</span></span>|<span data-ttu-id="05ca3-127">O controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="05ca3-127">The control has focus.</span></span>|
|<span data-ttu-id="05ca3-128">Sem foco</span><span class="sxs-lookup"><span data-stu-id="05ca3-128">Unfocused</span></span>|<span data-ttu-id="05ca3-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="05ca3-129">FocusStates</span></span>|<span data-ttu-id="05ca3-130">O controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="05ca3-130">The control does not have focus.</span></span>|
|<span data-ttu-id="05ca3-131">Válido</span><span class="sxs-lookup"><span data-stu-id="05ca3-131">Valid</span></span>|<span data-ttu-id="05ca3-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="05ca3-132">ValidationStates</span></span>|<span data-ttu-id="05ca3-133">O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.</span><span class="sxs-lookup"><span data-stu-id="05ca3-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="05ca3-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="05ca3-134">InvalidFocused</span></span>|<span data-ttu-id="05ca3-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="05ca3-135">ValidationStates</span></span>|<span data-ttu-id="05ca3-136">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.</span><span class="sxs-lookup"><span data-stu-id="05ca3-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="05ca3-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="05ca3-137">InvalidUnfocused</span></span>|<span data-ttu-id="05ca3-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="05ca3-138">ValidationStates</span></span>|<span data-ttu-id="05ca3-139">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="05ca3-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

## <a name="thumb-controltemplate-example"></a><span data-ttu-id="05ca3-140">Exemplo de ControlTemplate de Thumb</span><span class="sxs-lookup"><span data-stu-id="05ca3-140">Thumb ControlTemplate Example</span></span>

<span data-ttu-id="05ca3-141">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o controle de <xref:System.Windows.Controls.Primitives.Thumb>.</span><span class="sxs-lookup"><span data-stu-id="05ca3-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>

[!code-xaml[ControlTemplateExamples#Thumb](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#thumb)]

<span data-ttu-id="05ca3-142">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="05ca3-142">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="05ca3-143">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="05ca3-143">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="05ca3-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="05ca3-144">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="05ca3-145">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="05ca3-145">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="05ca3-146">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="05ca3-146">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="05ca3-147">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="05ca3-147">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="05ca3-148">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="05ca3-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
