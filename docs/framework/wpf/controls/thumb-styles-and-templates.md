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
ms.openlocfilehash: b7fc595f0c592d42f118c6b5542edf93716c2fca
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790774"
---
# <a name="thumb-styles-and-templates"></a><span data-ttu-id="c32ff-102">Estilos e modelos Thumb</span><span class="sxs-lookup"><span data-stu-id="c32ff-102">Thumb Styles and Templates</span></span>

<span data-ttu-id="c32ff-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.Primitives.Thumb> controle.</span><span class="sxs-lookup"><span data-stu-id="c32ff-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span> <span data-ttu-id="c32ff-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="c32ff-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="c32ff-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="c32ff-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>

## <a name="thumb-parts"></a><span data-ttu-id="c32ff-106">Partes do elevador</span><span class="sxs-lookup"><span data-stu-id="c32ff-106">Thumb Parts</span></span>

<span data-ttu-id="c32ff-107">O <xref:System.Windows.Controls.Primitives.Thumb> controle não tem nenhuma parte nomeada.</span><span class="sxs-lookup"><span data-stu-id="c32ff-107">The <xref:System.Windows.Controls.Primitives.Thumb> control does not have any named parts.</span></span>

## <a name="thumb-states"></a><span data-ttu-id="c32ff-108">Estados de elevador</span><span class="sxs-lookup"><span data-stu-id="c32ff-108">Thumb States</span></span>

<span data-ttu-id="c32ff-109">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.Primitives.Thumb> controle.</span><span class="sxs-lookup"><span data-stu-id="c32ff-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>

|<span data-ttu-id="c32ff-110">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="c32ff-110">VisualState Name</span></span>|<span data-ttu-id="c32ff-111">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="c32ff-111">VisualStateGroup Name</span></span>|<span data-ttu-id="c32ff-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="c32ff-112">Description</span></span>|
|-|-|-|
|<span data-ttu-id="c32ff-113">Normal</span><span class="sxs-lookup"><span data-stu-id="c32ff-113">Normal</span></span>|<span data-ttu-id="c32ff-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c32ff-114">CommonStates</span></span>|<span data-ttu-id="c32ff-115">O estado padrão.</span><span class="sxs-lookup"><span data-stu-id="c32ff-115">The default state.</span></span>|
|<span data-ttu-id="c32ff-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="c32ff-116">MouseOver</span></span>|<span data-ttu-id="c32ff-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c32ff-117">CommonStates</span></span>|<span data-ttu-id="c32ff-118">O ponteiro do mouse é posicionado sobre o controle.</span><span class="sxs-lookup"><span data-stu-id="c32ff-118">The mouse pointer is positioned over the control.</span></span>|
|<span data-ttu-id="c32ff-119">Pressionado</span><span class="sxs-lookup"><span data-stu-id="c32ff-119">Pressed</span></span>|<span data-ttu-id="c32ff-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c32ff-120">CommonStates</span></span>|<span data-ttu-id="c32ff-121">O controle é pressionado.</span><span class="sxs-lookup"><span data-stu-id="c32ff-121">The control is pressed.</span></span>|
|<span data-ttu-id="c32ff-122">Disabled</span><span class="sxs-lookup"><span data-stu-id="c32ff-122">Disabled</span></span>|<span data-ttu-id="c32ff-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="c32ff-123">CommonStates</span></span>|<span data-ttu-id="c32ff-124">O controle está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="c32ff-124">The control is disabled.</span></span>|
|<span data-ttu-id="c32ff-125">Focalizado</span><span class="sxs-lookup"><span data-stu-id="c32ff-125">Focused</span></span>|<span data-ttu-id="c32ff-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="c32ff-126">FocusStates</span></span>|<span data-ttu-id="c32ff-127">O controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="c32ff-127">The control has focus.</span></span>|
|<span data-ttu-id="c32ff-128">Sem foco</span><span class="sxs-lookup"><span data-stu-id="c32ff-128">Unfocused</span></span>|<span data-ttu-id="c32ff-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="c32ff-129">FocusStates</span></span>|<span data-ttu-id="c32ff-130">O controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="c32ff-130">The control does not have focus.</span></span>|
|<span data-ttu-id="c32ff-131">Válido</span><span class="sxs-lookup"><span data-stu-id="c32ff-131">Valid</span></span>|<span data-ttu-id="c32ff-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c32ff-132">ValidationStates</span></span>|<span data-ttu-id="c32ff-133">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="c32ff-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|
|<span data-ttu-id="c32ff-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="c32ff-134">InvalidFocused</span></span>|<span data-ttu-id="c32ff-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c32ff-135">ValidationStates</span></span>|<span data-ttu-id="c32ff-136">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="c32ff-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|
|<span data-ttu-id="c32ff-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="c32ff-137">InvalidUnfocused</span></span>|<span data-ttu-id="c32ff-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="c32ff-138">ValidationStates</span></span>|<span data-ttu-id="c32ff-139">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle não tem o foco.</span><span class="sxs-lookup"><span data-stu-id="c32ff-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|

## <a name="thumb-controltemplate-example"></a><span data-ttu-id="c32ff-140">Exemplo de ControlTemplate de Thumb</span><span class="sxs-lookup"><span data-stu-id="c32ff-140">Thumb ControlTemplate Example</span></span>

<span data-ttu-id="c32ff-141">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.Primitives.Thumb> controle.</span><span class="sxs-lookup"><span data-stu-id="c32ff-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>

[!code-xaml[ControlTemplateExamples#Thumb](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#thumb)]

<span data-ttu-id="c32ff-142">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="c32ff-142">The preceding example uses one or more of the following resources.</span></span>

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

<span data-ttu-id="c32ff-143">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="c32ff-143">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>

## <a name="see-also"></a><span data-ttu-id="c32ff-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c32ff-144">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="c32ff-145">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="c32ff-145">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="c32ff-146">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="c32ff-146">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="c32ff-147">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="c32ff-147">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="c32ff-148">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="c32ff-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
