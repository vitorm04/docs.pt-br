---
title: Estilos e modelos de elevador
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], Thumb
- styles [WPF], Thumb
- templates [WPF], Thumb
- Thumb [WPF], styles and templates
- ControlTemplate [WPF], Thumb
- parts [WPF], Thumb
ms.assetid: 86a49235-62d9-414e-923e-53126e3f930a
ms.openlocfilehash: e987932e00be09fdf5ac34bb2bfb24a890368a15
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596378"
---
# <a name="thumb-syles-and-templates"></a><span data-ttu-id="982a0-102">Estilos e modelos de elevador</span><span class="sxs-lookup"><span data-stu-id="982a0-102">Thumb Syles and Templates</span></span>
<span data-ttu-id="982a0-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.Primitives.Thumb> controle.</span><span class="sxs-lookup"><span data-stu-id="982a0-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span> <span data-ttu-id="982a0-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="982a0-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="982a0-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="982a0-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="thumb-parts"></a><span data-ttu-id="982a0-106">Partes do elevador</span><span class="sxs-lookup"><span data-stu-id="982a0-106">Thumb Parts</span></span>  
 <span data-ttu-id="982a0-107">O <xref:System.Windows.Controls.Primitives.Thumb> controle não tem nenhuma parte nomeada.</span><span class="sxs-lookup"><span data-stu-id="982a0-107">The <xref:System.Windows.Controls.Primitives.Thumb> control does not have any named parts.</span></span>  
  
## <a name="thumb-states"></a><span data-ttu-id="982a0-108">Estados de elevador</span><span class="sxs-lookup"><span data-stu-id="982a0-108">Thumb States</span></span>  
 <span data-ttu-id="982a0-109">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.Primitives.Thumb> controle.</span><span class="sxs-lookup"><span data-stu-id="982a0-109">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>  
  
|<span data-ttu-id="982a0-110">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="982a0-110">VisualState Name</span></span>|<span data-ttu-id="982a0-111">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="982a0-111">VisualStateGroup Name</span></span>|<span data-ttu-id="982a0-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="982a0-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="982a0-113">Normal</span><span class="sxs-lookup"><span data-stu-id="982a0-113">Normal</span></span>|<span data-ttu-id="982a0-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="982a0-114">CommonStates</span></span>|<span data-ttu-id="982a0-115">O estado padrão.</span><span class="sxs-lookup"><span data-stu-id="982a0-115">The default state.</span></span>|  
|<span data-ttu-id="982a0-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="982a0-116">MouseOver</span></span>|<span data-ttu-id="982a0-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="982a0-117">CommonStates</span></span>|<span data-ttu-id="982a0-118">O ponteiro do mouse é posicionado sobre o controle.</span><span class="sxs-lookup"><span data-stu-id="982a0-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="982a0-119">Pressionado</span><span class="sxs-lookup"><span data-stu-id="982a0-119">Pressed</span></span>|<span data-ttu-id="982a0-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="982a0-120">CommonStates</span></span>|<span data-ttu-id="982a0-121">O controle é pressionado.</span><span class="sxs-lookup"><span data-stu-id="982a0-121">The control is pressed.</span></span>|  
|<span data-ttu-id="982a0-122">Disabled</span><span class="sxs-lookup"><span data-stu-id="982a0-122">Disabled</span></span>|<span data-ttu-id="982a0-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="982a0-123">CommonStates</span></span>|<span data-ttu-id="982a0-124">O controle está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="982a0-124">The control is disabled.</span></span>|  
|<span data-ttu-id="982a0-125">Focalizado</span><span class="sxs-lookup"><span data-stu-id="982a0-125">Focused</span></span>|<span data-ttu-id="982a0-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="982a0-126">FocusStates</span></span>|<span data-ttu-id="982a0-127">O controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="982a0-127">The control has focus.</span></span>|  
|<span data-ttu-id="982a0-128">Sem foco</span><span class="sxs-lookup"><span data-stu-id="982a0-128">Unfocused</span></span>|<span data-ttu-id="982a0-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="982a0-129">FocusStates</span></span>|<span data-ttu-id="982a0-130">O controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="982a0-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="982a0-131">Válido</span><span class="sxs-lookup"><span data-stu-id="982a0-131">Valid</span></span>|<span data-ttu-id="982a0-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="982a0-132">ValidationStates</span></span>|<span data-ttu-id="982a0-133">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="982a0-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="982a0-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="982a0-134">InvalidFocused</span></span>|<span data-ttu-id="982a0-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="982a0-135">ValidationStates</span></span>|<span data-ttu-id="982a0-136">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="982a0-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="982a0-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="982a0-137">InvalidUnfocused</span></span>|<span data-ttu-id="982a0-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="982a0-138">ValidationStates</span></span>|<span data-ttu-id="982a0-139">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle não tem o foco.</span><span class="sxs-lookup"><span data-stu-id="982a0-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="thumb-controltemplate-example"></a><span data-ttu-id="982a0-140">Exemplo de ControlTemplate de Thumb</span><span class="sxs-lookup"><span data-stu-id="982a0-140">Thumb ControlTemplate Example</span></span>  
 <span data-ttu-id="982a0-141">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.Primitives.Thumb> controle.</span><span class="sxs-lookup"><span data-stu-id="982a0-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.Thumb> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Thumb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#thumb)]  
  
 <span data-ttu-id="982a0-142">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="982a0-142">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="982a0-143">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="982a0-143">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="982a0-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="982a0-144">See also</span></span>
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="982a0-145">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="982a0-145">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)
- [<span data-ttu-id="982a0-146">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="982a0-146">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)
- [<span data-ttu-id="982a0-147">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="982a0-147">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [<span data-ttu-id="982a0-148">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="982a0-148">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
