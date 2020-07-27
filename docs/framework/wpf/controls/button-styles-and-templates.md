---
title: Estilos e modelos de botão
description: Saiba mais sobre estilos e modelos para o controle botão de Windows Presentation Foundation. Modifique o ControlTemplate para dar ao controle uma aparência exclusiva.
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], Button
- parts [WPF], Button
- styles [WPF], Button
- Button [WPF], styles and templates
- templates [WPF], Button
- ControlTemplate [WPF], Button
ms.assetid: e223c759-f8c4-4717-acfb-b1e40bdf5f3b
ms.openlocfilehash: 11509adeef397f26eb040e6e98d0edb333b2515f
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166268"
---
# <a name="button-styles-and-templates"></a><span data-ttu-id="b9414-104">Estilos e modelos de botão</span><span class="sxs-lookup"><span data-stu-id="b9414-104">Button Styles and Templates</span></span>
<span data-ttu-id="b9414-105">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.Button> controle.</span><span class="sxs-lookup"><span data-stu-id="b9414-105">This topic describes the styles and templates for the <xref:System.Windows.Controls.Button> control.</span></span> <span data-ttu-id="b9414-106">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="b9414-106">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="b9414-107">Para obter mais informações, consulte [criar um modelo para um controle](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="b9414-107">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="button-parts"></a><span data-ttu-id="b9414-108">Partes do botão</span><span class="sxs-lookup"><span data-stu-id="b9414-108">Button Parts</span></span>  
 <span data-ttu-id="b9414-109">O <xref:System.Windows.Controls.Button> controle não tem nenhuma parte nomeada.</span><span class="sxs-lookup"><span data-stu-id="b9414-109">The <xref:System.Windows.Controls.Button> control does not have any named parts.</span></span>  
  
## <a name="button-states"></a><span data-ttu-id="b9414-110">Estados do botão</span><span class="sxs-lookup"><span data-stu-id="b9414-110">Button States</span></span>  
 <span data-ttu-id="b9414-111">A tabela a seguir lista os Estados visuais para o <xref:System.Windows.Controls.Button> controle.</span><span class="sxs-lookup"><span data-stu-id="b9414-111">The following table lists the visual states for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
|<span data-ttu-id="b9414-112">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="b9414-112">VisualState Name</span></span>|<span data-ttu-id="b9414-113">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="b9414-113">VisualStateGroup Name</span></span>|<span data-ttu-id="b9414-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="b9414-114">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="b9414-115">Normal</span><span class="sxs-lookup"><span data-stu-id="b9414-115">Normal</span></span>|<span data-ttu-id="b9414-116">CommonStates</span><span class="sxs-lookup"><span data-stu-id="b9414-116">CommonStates</span></span>|<span data-ttu-id="b9414-117">O estado padrão.</span><span class="sxs-lookup"><span data-stu-id="b9414-117">The default state.</span></span>|  
|<span data-ttu-id="b9414-118">MouseOver</span><span class="sxs-lookup"><span data-stu-id="b9414-118">MouseOver</span></span>|<span data-ttu-id="b9414-119">CommonStates</span><span class="sxs-lookup"><span data-stu-id="b9414-119">CommonStates</span></span>|<span data-ttu-id="b9414-120">O ponteiro do mouse é posicionado sobre o controle.</span><span class="sxs-lookup"><span data-stu-id="b9414-120">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="b9414-121">Pressionado</span><span class="sxs-lookup"><span data-stu-id="b9414-121">Pressed</span></span>|<span data-ttu-id="b9414-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="b9414-122">CommonStates</span></span>|<span data-ttu-id="b9414-123">O controle é pressionado.</span><span class="sxs-lookup"><span data-stu-id="b9414-123">The control is pressed.</span></span>|  
|<span data-ttu-id="b9414-124">Desabilitado</span><span class="sxs-lookup"><span data-stu-id="b9414-124">Disabled</span></span>|<span data-ttu-id="b9414-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="b9414-125">CommonStates</span></span>|<span data-ttu-id="b9414-126">O controle está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="b9414-126">The control is disabled.</span></span>|  
|<span data-ttu-id="b9414-127">Focalizado</span><span class="sxs-lookup"><span data-stu-id="b9414-127">Focused</span></span>|<span data-ttu-id="b9414-128">FocusStates</span><span class="sxs-lookup"><span data-stu-id="b9414-128">FocusStates</span></span>|<span data-ttu-id="b9414-129">O controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="b9414-129">The control has focus.</span></span>|  
|<span data-ttu-id="b9414-130">Sem foco</span><span class="sxs-lookup"><span data-stu-id="b9414-130">Unfocused</span></span>|<span data-ttu-id="b9414-131">FocusStates</span><span class="sxs-lookup"><span data-stu-id="b9414-131">FocusStates</span></span>|<span data-ttu-id="b9414-132">O controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="b9414-132">The control does not have focus.</span></span>|  
|<span data-ttu-id="b9414-133">Válido</span><span class="sxs-lookup"><span data-stu-id="b9414-133">Valid</span></span>|<span data-ttu-id="b9414-134">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b9414-134">ValidationStates</span></span>|<span data-ttu-id="b9414-135">O controle usa a <xref:System.Windows.Controls.Validation> classe e a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Propriedade anexada é `false` .</span><span class="sxs-lookup"><span data-stu-id="b9414-135">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="b9414-136">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="b9414-136">InvalidFocused</span></span>|<span data-ttu-id="b9414-137">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b9414-137">ValidationStates</span></span>|<span data-ttu-id="b9414-138">A <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Propriedade anexada é `true` e o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="b9414-138">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="b9414-139">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="b9414-139">InvalidUnfocused</span></span>|<span data-ttu-id="b9414-140">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="b9414-140">ValidationStates</span></span>|<span data-ttu-id="b9414-141">A <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Propriedade anexada é `true` e o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="b9414-141">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="button-controltemplate-example"></a><span data-ttu-id="b9414-142">Exemplo de ControlTemplate de botão</span><span class="sxs-lookup"><span data-stu-id="b9414-142">Button ControlTemplate Example</span></span>  
 <span data-ttu-id="b9414-143">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.Button> controle.</span><span class="sxs-lookup"><span data-stu-id="b9414-143">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Button](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#button)]  
  
 <span data-ttu-id="b9414-144">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="b9414-144">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="b9414-145">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="b9414-145">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9414-146">Confira também</span><span class="sxs-lookup"><span data-stu-id="b9414-146">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="b9414-147">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="b9414-147">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="b9414-148">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="b9414-148">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="b9414-149">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="b9414-149">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="b9414-150">Criar um modelo para um controle</span><span class="sxs-lookup"><span data-stu-id="b9414-150">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
