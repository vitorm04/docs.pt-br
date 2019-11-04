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
ms.openlocfilehash: 7c4680a3ea9352e94d628e786fc8e4fd71018d00
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458257"
---
# <a name="textbox-styles-and-templates"></a><span data-ttu-id="aad9a-102">Estilos e modelos TextBox</span><span class="sxs-lookup"><span data-stu-id="aad9a-102">TextBox Styles and Templates</span></span>
<span data-ttu-id="aad9a-103">Este tópico descreve os estilos e modelos para o controle de <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="aad9a-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.TextBox> control.</span></span> <span data-ttu-id="aad9a-104">Você pode modificar o <xref:System.Windows.Controls.ControlTemplate> padrão para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="aad9a-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="aad9a-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="aad9a-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="textbox-parts"></a><span data-ttu-id="aad9a-106">Partes da caixa de texto</span><span class="sxs-lookup"><span data-stu-id="aad9a-106">TextBox Parts</span></span>  
 <span data-ttu-id="aad9a-107">A tabela a seguir lista as partes nomeadas para o controle de <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="aad9a-107">The following table lists the named parts for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="aad9a-108">Parte</span><span class="sxs-lookup"><span data-stu-id="aad9a-108">Part</span></span>|<span data-ttu-id="aad9a-109">Digite</span><span class="sxs-lookup"><span data-stu-id="aad9a-109">Type</span></span>|<span data-ttu-id="aad9a-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="aad9a-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="aad9a-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="aad9a-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="aad9a-112">Um elemento visual que pode conter um <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="aad9a-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="aad9a-113">O texto do <xref:System.Windows.Controls.TextBox> é exibido neste elemento.</span><span class="sxs-lookup"><span data-stu-id="aad9a-113">The text of the <xref:System.Windows.Controls.TextBox> is displayed in this element.</span></span>|  
  
## <a name="textbox-states"></a><span data-ttu-id="aad9a-114">Estados da caixa de texto</span><span class="sxs-lookup"><span data-stu-id="aad9a-114">TextBox States</span></span>  
 <span data-ttu-id="aad9a-115">A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="aad9a-115">The following table lists the visual states for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
|<span data-ttu-id="aad9a-116">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="aad9a-116">VisualState Name</span></span>|<span data-ttu-id="aad9a-117">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="aad9a-117">VisualStateGroup Name</span></span>|<span data-ttu-id="aad9a-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="aad9a-118">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="aad9a-119">Normal</span><span class="sxs-lookup"><span data-stu-id="aad9a-119">Normal</span></span>|<span data-ttu-id="aad9a-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="aad9a-120">CommonStates</span></span>|<span data-ttu-id="aad9a-121">O estado padrão.</span><span class="sxs-lookup"><span data-stu-id="aad9a-121">The default state.</span></span>|  
|<span data-ttu-id="aad9a-122">MouseOver</span><span class="sxs-lookup"><span data-stu-id="aad9a-122">MouseOver</span></span>|<span data-ttu-id="aad9a-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="aad9a-123">CommonStates</span></span>|<span data-ttu-id="aad9a-124">O ponteiro do mouse é posicionado sobre o controle.</span><span class="sxs-lookup"><span data-stu-id="aad9a-124">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="aad9a-125">Disabled</span><span class="sxs-lookup"><span data-stu-id="aad9a-125">Disabled</span></span>|<span data-ttu-id="aad9a-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="aad9a-126">CommonStates</span></span>|<span data-ttu-id="aad9a-127">O controle está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="aad9a-127">The control is disabled.</span></span>|  
|<span data-ttu-id="aad9a-128">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="aad9a-128">ReadOnly</span></span>|<span data-ttu-id="aad9a-129">CommonStates</span><span class="sxs-lookup"><span data-stu-id="aad9a-129">CommonStates</span></span>|<span data-ttu-id="aad9a-130">O usuário não pode alterar o texto na <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="aad9a-130">The user cannot change the text in the <xref:System.Windows.Controls.TextBox>.</span></span>|  
|<span data-ttu-id="aad9a-131">Focalizado</span><span class="sxs-lookup"><span data-stu-id="aad9a-131">Focused</span></span>|<span data-ttu-id="aad9a-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="aad9a-132">FocusStates</span></span>|<span data-ttu-id="aad9a-133">O controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="aad9a-133">The control has focus.</span></span>|  
|<span data-ttu-id="aad9a-134">Sem foco</span><span class="sxs-lookup"><span data-stu-id="aad9a-134">Unfocused</span></span>|<span data-ttu-id="aad9a-135">FocusStates</span><span class="sxs-lookup"><span data-stu-id="aad9a-135">FocusStates</span></span>|<span data-ttu-id="aad9a-136">O controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="aad9a-136">The control does not have focus.</span></span>|  
|<span data-ttu-id="aad9a-137">Válido</span><span class="sxs-lookup"><span data-stu-id="aad9a-137">Valid</span></span>|<span data-ttu-id="aad9a-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="aad9a-138">ValidationStates</span></span>|<span data-ttu-id="aad9a-139">O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.</span><span class="sxs-lookup"><span data-stu-id="aad9a-139">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="aad9a-140">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="aad9a-140">InvalidFocused</span></span>|<span data-ttu-id="aad9a-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="aad9a-141">ValidationStates</span></span>|<span data-ttu-id="aad9a-142">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.</span><span class="sxs-lookup"><span data-stu-id="aad9a-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="aad9a-143">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="aad9a-143">InvalidUnfocused</span></span>|<span data-ttu-id="aad9a-144">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="aad9a-144">ValidationStates</span></span>|<span data-ttu-id="aad9a-145">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="aad9a-145">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="textbox-controltemplate-example"></a><span data-ttu-id="aad9a-146">Exemplo de ControlTemplate de TextBox</span><span class="sxs-lookup"><span data-stu-id="aad9a-146">TextBox ControlTemplate Example</span></span>  
 <span data-ttu-id="aad9a-147">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o controle de <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="aad9a-147">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#TextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#textbox)]  
  
 <span data-ttu-id="aad9a-148">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="aad9a-148">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="aad9a-149">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="aad9a-149">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aad9a-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aad9a-150">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="aad9a-151">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="aad9a-151">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="aad9a-152">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="aad9a-152">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="aad9a-153">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="aad9a-153">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="aad9a-154">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="aad9a-154">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
