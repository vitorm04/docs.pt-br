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
ms.openlocfilehash: 464e2ff88b6e311470f6afe107d770922d9a395d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689228"
---
# <a name="passwordbox-syles-and-templates"></a><span data-ttu-id="5ed60-102">Estilos e modelos PasswordBox</span><span class="sxs-lookup"><span data-stu-id="5ed60-102">PasswordBox Syles and Templates</span></span>
<span data-ttu-id="5ed60-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.PasswordBox> controle.</span><span class="sxs-lookup"><span data-stu-id="5ed60-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.PasswordBox> control.</span></span> <span data-ttu-id="5ed60-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="5ed60-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="5ed60-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="5ed60-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="passwordbox-parts"></a><span data-ttu-id="5ed60-106">Partes de PasswordBox</span><span class="sxs-lookup"><span data-stu-id="5ed60-106">PasswordBox Parts</span></span>  
 <span data-ttu-id="5ed60-107">A tabela a seguir lista as partes nomeadas para o <xref:System.Windows.Controls.PasswordBox> controle.</span><span class="sxs-lookup"><span data-stu-id="5ed60-107">The following table lists the named parts for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>  
  
|<span data-ttu-id="5ed60-108">Parte</span><span class="sxs-lookup"><span data-stu-id="5ed60-108">Part</span></span>|<span data-ttu-id="5ed60-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="5ed60-109">Type</span></span>|<span data-ttu-id="5ed60-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ed60-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="5ed60-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="5ed60-111">PART_ContentHost</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="5ed60-112">Um elemento visual que pode conter um <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="5ed60-112">A visual element that can contain a <xref:System.Windows.FrameworkElement>.</span></span> <span data-ttu-id="5ed60-113">O texto do <xref:System.Windows.Controls.PasswordBox> é exibido neste elemento.</span><span class="sxs-lookup"><span data-stu-id="5ed60-113">The text of the <xref:System.Windows.Controls.PasswordBox> is displayed in this element.</span></span>|  
  
## <a name="passwordbox-states"></a><span data-ttu-id="5ed60-114">Estados de PasswordBox</span><span class="sxs-lookup"><span data-stu-id="5ed60-114">PasswordBox States</span></span>  
 <span data-ttu-id="5ed60-115">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.PasswordBox> controle.</span><span class="sxs-lookup"><span data-stu-id="5ed60-115">The following table lists the visual states for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>  
  
|<span data-ttu-id="5ed60-116">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="5ed60-116">VisualState Name</span></span>|<span data-ttu-id="5ed60-117">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="5ed60-117">VisualStateGroup Name</span></span>|<span data-ttu-id="5ed60-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ed60-118">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="5ed60-119">Normal</span><span class="sxs-lookup"><span data-stu-id="5ed60-119">Normal</span></span>|<span data-ttu-id="5ed60-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="5ed60-120">CommonStates</span></span>|<span data-ttu-id="5ed60-121">O estado padrão.</span><span class="sxs-lookup"><span data-stu-id="5ed60-121">The default state.</span></span>|  
|<span data-ttu-id="5ed60-122">MouseOver</span><span class="sxs-lookup"><span data-stu-id="5ed60-122">MouseOver</span></span>|<span data-ttu-id="5ed60-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="5ed60-123">CommonStates</span></span>|<span data-ttu-id="5ed60-124">O ponteiro do mouse é posicionado sobre o controle.</span><span class="sxs-lookup"><span data-stu-id="5ed60-124">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="5ed60-125">Disabled</span><span class="sxs-lookup"><span data-stu-id="5ed60-125">Disabled</span></span>|<span data-ttu-id="5ed60-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="5ed60-126">CommonStates</span></span>|<span data-ttu-id="5ed60-127">O controle está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="5ed60-127">The control is disabled.</span></span>|  
|<span data-ttu-id="5ed60-128">Focalizado</span><span class="sxs-lookup"><span data-stu-id="5ed60-128">Focused</span></span>|<span data-ttu-id="5ed60-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="5ed60-129">FocusStates</span></span>|<span data-ttu-id="5ed60-130">O controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="5ed60-130">The control has focus.</span></span>|  
|<span data-ttu-id="5ed60-131">Sem foco</span><span class="sxs-lookup"><span data-stu-id="5ed60-131">Unfocused</span></span>|<span data-ttu-id="5ed60-132">FocusStates</span><span class="sxs-lookup"><span data-stu-id="5ed60-132">FocusStates</span></span>|<span data-ttu-id="5ed60-133">O controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="5ed60-133">The control does not have focus.</span></span>|  
|<span data-ttu-id="5ed60-134">Válido</span><span class="sxs-lookup"><span data-stu-id="5ed60-134">Valid</span></span>|<span data-ttu-id="5ed60-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5ed60-135">ValidationStates</span></span>|<span data-ttu-id="5ed60-136">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="5ed60-136">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="5ed60-137">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="5ed60-137">InvalidFocused</span></span>|<span data-ttu-id="5ed60-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5ed60-138">ValidationStates</span></span>|<span data-ttu-id="5ed60-139">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="5ed60-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="5ed60-140">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="5ed60-140">InvalidUnfocused</span></span>|<span data-ttu-id="5ed60-141">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="5ed60-141">ValidationStates</span></span>|<span data-ttu-id="5ed60-142">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle não tem o foco.</span><span class="sxs-lookup"><span data-stu-id="5ed60-142">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="passwordbox-controltemplate-example"></a><span data-ttu-id="5ed60-143">Exemplo de ControlTemplate de PasswordBox</span><span class="sxs-lookup"><span data-stu-id="5ed60-143">PasswordBox ControlTemplate Example</span></span>  
 <span data-ttu-id="5ed60-144">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.PasswordBox> controle.</span><span class="sxs-lookup"><span data-stu-id="5ed60-144">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.PasswordBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#PasswordBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/textbox.xaml#passwordbox)]  
  
 <span data-ttu-id="5ed60-145">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="5ed60-145">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="5ed60-146">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="5ed60-146">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ed60-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5ed60-147">See also</span></span>
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="5ed60-148">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="5ed60-148">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)
- [<span data-ttu-id="5ed60-149">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="5ed60-149">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)
- [<span data-ttu-id="5ed60-150">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="5ed60-150">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [<span data-ttu-id="5ed60-151">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="5ed60-151">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
