---
title: Estilos e modelos de botão
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], Button
- parts [WPF], Button
- styles [WPF], Button
- Button [WPF], styles and templates
- templates [WPF], Button
- ControlTemplate [WPF], Button
ms.assetid: e223c759-f8c4-4717-acfb-b1e40bdf5f3b
ms.openlocfilehash: ef9f85848ebdda9dc4ae15d0f54847eacd46e24d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283576"
---
# <a name="button-styles-and-templates"></a><span data-ttu-id="f094c-102">Estilos e modelos de botão</span><span class="sxs-lookup"><span data-stu-id="f094c-102">Button Styles and Templates</span></span>
<span data-ttu-id="f094c-103">Este tópico descreve os estilos e modelos para o controle de <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="f094c-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Button> control.</span></span> <span data-ttu-id="f094c-104">Você pode modificar o <xref:System.Windows.Controls.ControlTemplate> padrão para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="f094c-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="f094c-105">Para obter mais informações, consulte [criar um modelo para um controle](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="f094c-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="button-parts"></a><span data-ttu-id="f094c-106">Partes do botão</span><span class="sxs-lookup"><span data-stu-id="f094c-106">Button Parts</span></span>  
 <span data-ttu-id="f094c-107">O controle de <xref:System.Windows.Controls.Button> não tem nenhuma parte nomeada.</span><span class="sxs-lookup"><span data-stu-id="f094c-107">The <xref:System.Windows.Controls.Button> control does not have any named parts.</span></span>  
  
## <a name="button-states"></a><span data-ttu-id="f094c-108">Estados do botão</span><span class="sxs-lookup"><span data-stu-id="f094c-108">Button States</span></span>  
 <span data-ttu-id="f094c-109">A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="f094c-109">The following table lists the visual states for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
|<span data-ttu-id="f094c-110">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="f094c-110">VisualState Name</span></span>|<span data-ttu-id="f094c-111">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="f094c-111">VisualStateGroup Name</span></span>|<span data-ttu-id="f094c-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="f094c-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="f094c-113">Normal</span><span class="sxs-lookup"><span data-stu-id="f094c-113">Normal</span></span>|<span data-ttu-id="f094c-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f094c-114">CommonStates</span></span>|<span data-ttu-id="f094c-115">O estado padrão.</span><span class="sxs-lookup"><span data-stu-id="f094c-115">The default state.</span></span>|  
|<span data-ttu-id="f094c-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="f094c-116">MouseOver</span></span>|<span data-ttu-id="f094c-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f094c-117">CommonStates</span></span>|<span data-ttu-id="f094c-118">O ponteiro do mouse é posicionado sobre o controle.</span><span class="sxs-lookup"><span data-stu-id="f094c-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="f094c-119">Pressionado</span><span class="sxs-lookup"><span data-stu-id="f094c-119">Pressed</span></span>|<span data-ttu-id="f094c-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f094c-120">CommonStates</span></span>|<span data-ttu-id="f094c-121">O controle é pressionado.</span><span class="sxs-lookup"><span data-stu-id="f094c-121">The control is pressed.</span></span>|  
|<span data-ttu-id="f094c-122">Disabled</span><span class="sxs-lookup"><span data-stu-id="f094c-122">Disabled</span></span>|<span data-ttu-id="f094c-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f094c-123">CommonStates</span></span>|<span data-ttu-id="f094c-124">O controle está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="f094c-124">The control is disabled.</span></span>|  
|<span data-ttu-id="f094c-125">Focalizado</span><span class="sxs-lookup"><span data-stu-id="f094c-125">Focused</span></span>|<span data-ttu-id="f094c-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="f094c-126">FocusStates</span></span>|<span data-ttu-id="f094c-127">O controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="f094c-127">The control has focus.</span></span>|  
|<span data-ttu-id="f094c-128">Sem foco</span><span class="sxs-lookup"><span data-stu-id="f094c-128">Unfocused</span></span>|<span data-ttu-id="f094c-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="f094c-129">FocusStates</span></span>|<span data-ttu-id="f094c-130">O controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="f094c-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="f094c-131">Válido</span><span class="sxs-lookup"><span data-stu-id="f094c-131">Valid</span></span>|<span data-ttu-id="f094c-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f094c-132">ValidationStates</span></span>|<span data-ttu-id="f094c-133">O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.</span><span class="sxs-lookup"><span data-stu-id="f094c-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="f094c-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="f094c-134">InvalidFocused</span></span>|<span data-ttu-id="f094c-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f094c-135">ValidationStates</span></span>|<span data-ttu-id="f094c-136">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` e o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="f094c-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="f094c-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="f094c-137">InvalidUnfocused</span></span>|<span data-ttu-id="f094c-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f094c-138">ValidationStates</span></span>|<span data-ttu-id="f094c-139">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` e o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="f094c-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="button-controltemplate-example"></a><span data-ttu-id="f094c-140">Exemplo de ControlTemplate de botão</span><span class="sxs-lookup"><span data-stu-id="f094c-140">Button ControlTemplate Example</span></span>  
 <span data-ttu-id="f094c-141">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o controle de <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="f094c-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Button](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#button)]  
  
 <span data-ttu-id="f094c-142">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="f094c-142">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="f094c-143">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="f094c-143">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f094c-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f094c-144">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="f094c-145">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="f094c-145">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="f094c-146">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="f094c-146">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="f094c-147">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="f094c-147">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="f094c-148">Criar um modelo para um controle</span><span class="sxs-lookup"><span data-stu-id="f094c-148">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
