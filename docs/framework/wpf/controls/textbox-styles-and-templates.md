---
title: Estilos e modelos TextBox
description: Saiba mais sobre estilos e modelos para o controle caixa de texto Windows Presentation Foundation. Modifique o ControlTemplate para dar ao controle uma aparência exclusiva.
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], TextBox
- parts [WPF], TextBox
- states [WPF], TextBox
- styles [WPF], TextBox
- templates [WPF], TextBox
- TextBox [WPF], styles and templates
ms.assetid: aa99130c-43a1-450f-9b46-c40ae0db0cca
ms.openlocfilehash: 0e15fd40f5590ee46da49cc6c0d5fb30e051f7e4
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164732"
---
# <a name="textbox-styles-and-templates"></a><span data-ttu-id="71047-104">Estilos e modelos TextBox</span><span class="sxs-lookup"><span data-stu-id="71047-104">TextBox Styles and Templates</span></span>
<span data-ttu-id="71047-105">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.TextBox> controle.</span><span class="sxs-lookup"><span data-stu-id="71047-105">This topic describes the styles and templates for the <xref:System.Windows.Controls.TextBox> control.</span></span> <span data-ttu-id="71047-106">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="71047-106">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="71047-107">Para obter mais informações, consulte [criar um modelo para um controle](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="71047-107">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="textbox-parts"></a><span data-ttu-id="71047-108">Partes da caixa de texto</span><span class="sxs-lookup"><span data-stu-id="71047-108">TextBox Parts</span></span>  
 <span data-ttu-id="71047-109">A tabela a seguir lista as partes nomeadas para o <xref:System.Windows.Controls.TextBox> controle.</span><span class="sxs-lookup"><span data-stu-id="71047-109">The following table lists the named parts for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="71047-110">Parte</span><span class="sxs-lookup"><span data-stu-id="71047-110">Part</span></span>|<span data-ttu-id="71047-111">Type</span><span class="sxs-lookup"><span data-stu-id="71047-111">Type</span></span>|<span data-ttu-id="71047-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="71047-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="71047-113">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="71047-113">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="71047-114">Um elemento visual que pode conter um <xref:System.Windows.FrameworkElement> .</span><span class="sxs-lookup"><span data-stu-id="71047-114">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="71047-115">O texto do <xref:System.Windows.Controls.TextBox> é exibido neste elemento.</span><span class="sxs-lookup"><span data-stu-id="71047-115">The text of the <xref:System.Windows.Controls.TextBox> is displayed in this element.</span></span>|  
  
## <a name="textbox-states"></a><span data-ttu-id="71047-116">Estados da caixa de texto</span><span class="sxs-lookup"><span data-stu-id="71047-116">TextBox States</span></span>  
 <span data-ttu-id="71047-117">A tabela a seguir lista os Estados visuais para o <xref:System.Windows.Controls.TextBox> controle.</span><span class="sxs-lookup"><span data-stu-id="71047-117">The following table lists the visual states for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="71047-118">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="71047-118">VisualState Name</span></span>|<span data-ttu-id="71047-119">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="71047-119">VisualStateGroup Name</span></span>|<span data-ttu-id="71047-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="71047-120">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="71047-121">Normal</span><span class="sxs-lookup"><span data-stu-id="71047-121">Normal</span></span>|<span data-ttu-id="71047-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="71047-122">CommonStates</span></span>|<span data-ttu-id="71047-123">O estado padrão.</span><span class="sxs-lookup"><span data-stu-id="71047-123">The default state.</span></span>|  
|<span data-ttu-id="71047-124">MouseOver</span><span class="sxs-lookup"><span data-stu-id="71047-124">MouseOver</span></span>|<span data-ttu-id="71047-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="71047-125">CommonStates</span></span>|<span data-ttu-id="71047-126">O ponteiro do mouse é posicionado sobre o controle.</span><span class="sxs-lookup"><span data-stu-id="71047-126">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="71047-127">Desabilitado</span><span class="sxs-lookup"><span data-stu-id="71047-127">Disabled</span></span>|<span data-ttu-id="71047-128">CommonStates</span><span class="sxs-lookup"><span data-stu-id="71047-128">CommonStates</span></span>|<span data-ttu-id="71047-129">O controle está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="71047-129">The control is disabled.</span></span>|  
|<span data-ttu-id="71047-130">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="71047-130">ReadOnly</span></span>|<span data-ttu-id="71047-131">CommonStates</span><span class="sxs-lookup"><span data-stu-id="71047-131">CommonStates</span></span>|<span data-ttu-id="71047-132">O usuário não pode alterar o texto no <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="71047-132">The user cannot change the text in the <xref:System.Windows.Controls.TextBox>.</span></span>|  
|<span data-ttu-id="71047-133">Focalizado</span><span class="sxs-lookup"><span data-stu-id="71047-133">Focused</span></span>|<span data-ttu-id="71047-134">FocusStates</span><span class="sxs-lookup"><span data-stu-id="71047-134">FocusStates</span></span>|<span data-ttu-id="71047-135">O controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="71047-135">The control has focus.</span></span>|  
|<span data-ttu-id="71047-136">Sem foco</span><span class="sxs-lookup"><span data-stu-id="71047-136">Unfocused</span></span>|<span data-ttu-id="71047-137">FocusStates</span><span class="sxs-lookup"><span data-stu-id="71047-137">FocusStates</span></span>|<span data-ttu-id="71047-138">O controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="71047-138">The control does not have focus.</span></span>|  
|<span data-ttu-id="71047-139">Válido</span><span class="sxs-lookup"><span data-stu-id="71047-139">Valid</span></span>|<span data-ttu-id="71047-140">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="71047-140">ValidationStates</span></span>|<span data-ttu-id="71047-141">O controle usa a <xref:System.Windows.Controls.Validation> classe e a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Propriedade anexada é `false` .</span><span class="sxs-lookup"><span data-stu-id="71047-141">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="71047-142">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="71047-142">InvalidFocused</span></span>|<span data-ttu-id="71047-143">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="71047-143">ValidationStates</span></span>|<span data-ttu-id="71047-144">A <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Propriedade anexada `true` tem o controle foco.</span><span class="sxs-lookup"><span data-stu-id="71047-144">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="71047-145">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="71047-145">InvalidUnfocused</span></span>|<span data-ttu-id="71047-146">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="71047-146">ValidationStates</span></span>|<span data-ttu-id="71047-147">A <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Propriedade anexada `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="71047-147">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="textbox-controltemplate-example"></a><span data-ttu-id="71047-148">Exemplo de ControlTemplate de TextBox</span><span class="sxs-lookup"><span data-stu-id="71047-148">TextBox ControlTemplate Example</span></span>  
 <span data-ttu-id="71047-149">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.TextBox> controle.</span><span class="sxs-lookup"><span data-stu-id="71047-149">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#TextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#textbox)]  
  
 <span data-ttu-id="71047-150">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="71047-150">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="71047-151">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="71047-151">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71047-152">Confira também</span><span class="sxs-lookup"><span data-stu-id="71047-152">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="71047-153">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="71047-153">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="71047-154">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="71047-154">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="71047-155">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="71047-155">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="71047-156">Criar um modelo para um controle</span><span class="sxs-lookup"><span data-stu-id="71047-156">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
