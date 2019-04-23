---
title: Estilos e modelos TextBox
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], TextBox
- parts [WPF], TextBox
- states [WPF], TextBox
- styles [WPF], TextBox
- templates [WPF], TextBox
- TextBox [WPF], styles and templates
ms.assetid: aa99130c-43a1-450f-9b46-c40ae0db0cca
ms.openlocfilehash: ccc89e0e0c8977398ed162b246ff6cdede3b8351
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59177938"
---
# <a name="textbox-styles-and-templates"></a><span data-ttu-id="df836-102">Estilos e modelos TextBox</span><span class="sxs-lookup"><span data-stu-id="df836-102">TextBox Styles and Templates</span></span>
<span data-ttu-id="df836-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.TextBox> controle.</span><span class="sxs-lookup"><span data-stu-id="df836-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.TextBox> control.</span></span> <span data-ttu-id="df836-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="df836-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="df836-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="df836-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="textbox-parts"></a><span data-ttu-id="df836-106">Partes de caixa de texto</span><span class="sxs-lookup"><span data-stu-id="df836-106">TextBox Parts</span></span>  
 <span data-ttu-id="df836-107">A tabela a seguir lista as partes nomeadas para o <xref:System.Windows.Controls.TextBox> controle.</span><span class="sxs-lookup"><span data-stu-id="df836-107">The following table lists the named parts for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="df836-108">Parte</span><span class="sxs-lookup"><span data-stu-id="df836-108">Part</span></span>|<span data-ttu-id="df836-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="df836-109">Type</span></span>|<span data-ttu-id="df836-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="df836-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="df836-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="df836-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="df836-112">Um elemento visual que pode conter um <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="df836-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="df836-113">O texto do <xref:System.Windows.Controls.TextBox> é exibido neste elemento.</span><span class="sxs-lookup"><span data-stu-id="df836-113">The text of the <xref:System.Windows.Controls.TextBox> is displayed in this element.</span></span>|  
  
## <a name="textbox-states"></a><span data-ttu-id="df836-114">Estados de caixa de texto</span><span class="sxs-lookup"><span data-stu-id="df836-114">TextBox States</span></span>  
 <span data-ttu-id="df836-115">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.TextBox> controle.</span><span class="sxs-lookup"><span data-stu-id="df836-115">The following table lists the visual states for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="df836-116">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="df836-116">VisualState Name</span></span>|<span data-ttu-id="df836-117">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="df836-117">VisualStateGroup Name</span></span>|<span data-ttu-id="df836-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="df836-118">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="df836-119">Normal</span><span class="sxs-lookup"><span data-stu-id="df836-119">Normal</span></span>|<span data-ttu-id="df836-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="df836-120">CommonStates</span></span>|<span data-ttu-id="df836-121">O estado padrão.</span><span class="sxs-lookup"><span data-stu-id="df836-121">The default state.</span></span>|  
|<span data-ttu-id="df836-122">MouseOver</span><span class="sxs-lookup"><span data-stu-id="df836-122">MouseOver</span></span>|<span data-ttu-id="df836-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="df836-123">CommonStates</span></span>|<span data-ttu-id="df836-124">O ponteiro do mouse é posicionado sobre o controle.</span><span class="sxs-lookup"><span data-stu-id="df836-124">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="df836-125">Disabled</span><span class="sxs-lookup"><span data-stu-id="df836-125">Disabled</span></span>|<span data-ttu-id="df836-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="df836-126">CommonStates</span></span>|<span data-ttu-id="df836-127">O controle está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="df836-127">The control is disabled.</span></span>|  
|<span data-ttu-id="df836-128">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="df836-128">ReadOnly</span></span>|<span data-ttu-id="df836-129">CommonStates</span><span class="sxs-lookup"><span data-stu-id="df836-129">CommonStates</span></span>|<span data-ttu-id="df836-130">O usuário não pode alterar o texto a <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="df836-130">The user cannot change the text in the <xref:System.Windows.Controls.TextBox>.</span></span>|  
|<span data-ttu-id="df836-131">Focalizado</span><span class="sxs-lookup"><span data-stu-id="df836-131">Focused</span></span>|<span data-ttu-id="df836-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="df836-132">FocusStates</span></span>|<span data-ttu-id="df836-133">O controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="df836-133">The control has focus.</span></span>|  
|<span data-ttu-id="df836-134">Sem foco</span><span class="sxs-lookup"><span data-stu-id="df836-134">Unfocused</span></span>|<span data-ttu-id="df836-135">FocusStates</span><span class="sxs-lookup"><span data-stu-id="df836-135">FocusStates</span></span>|<span data-ttu-id="df836-136">O controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="df836-136">The control does not have focus.</span></span>|  
|<span data-ttu-id="df836-137">Válido</span><span class="sxs-lookup"><span data-stu-id="df836-137">Valid</span></span>|<span data-ttu-id="df836-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="df836-138">ValidationStates</span></span>|<span data-ttu-id="df836-139">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="df836-139">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="df836-140">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="df836-140">InvalidFocused</span></span>|<span data-ttu-id="df836-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="df836-141">ValidationStates</span></span>|<span data-ttu-id="df836-142">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="df836-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="df836-143">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="df836-143">InvalidUnfocused</span></span>|<span data-ttu-id="df836-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="df836-144">ValidationStates</span></span>|<span data-ttu-id="df836-145">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle não tem o foco.</span><span class="sxs-lookup"><span data-stu-id="df836-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="textbox-controltemplate-example"></a><span data-ttu-id="df836-146">Exemplo de ControlTemplate de caixa de texto</span><span class="sxs-lookup"><span data-stu-id="df836-146">TextBox ControlTemplate Example</span></span>  
 <span data-ttu-id="df836-147">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.TextBox> controle.</span><span class="sxs-lookup"><span data-stu-id="df836-147">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#TextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#textbox)]  
  
 <span data-ttu-id="df836-148">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="df836-148">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="df836-149">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="df836-149">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df836-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df836-150">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="df836-151">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="df836-151">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="df836-152">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="df836-152">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="df836-153">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="df836-153">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="df836-154">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="df836-154">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
