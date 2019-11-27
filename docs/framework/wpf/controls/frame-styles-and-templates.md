---
title: Estilos e modelos de quadro
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], Frame
- templates [WPF], Frame
- ControlTemplate [WPF], Frame
- Frame [WPF], styles and templates
- states [WPF], Frame
- styles [WPF], Frame
ms.assetid: a01c32e2-c951-46a0-a82f-2614ca241f0b
ms.openlocfilehash: de853198c97c99319bea4a816c9a6eca5dc5d917
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283740"
---
# <a name="frame-styles-and-templates"></a><span data-ttu-id="2d5a4-102">Estilos e modelos de quadro</span><span class="sxs-lookup"><span data-stu-id="2d5a4-102">Frame Styles and Templates</span></span>
<span data-ttu-id="2d5a4-103">Este tópico descreve os estilos e modelos para o controle de <xref:System.Windows.Controls.Frame>.</span><span class="sxs-lookup"><span data-stu-id="2d5a4-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Frame> control.</span></span> <span data-ttu-id="2d5a4-104">Você pode modificar o <xref:System.Windows.Controls.ControlTemplate> padrão para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="2d5a4-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="2d5a4-105">Para obter mais informações, consulte [criar um modelo para um controle](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="2d5a4-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="frame-parts"></a><span data-ttu-id="2d5a4-106">Partes do quadro</span><span class="sxs-lookup"><span data-stu-id="2d5a4-106">Frame Parts</span></span>  
 <span data-ttu-id="2d5a4-107">A tabela a seguir lista as partes nomeadas para o controle de <xref:System.Windows.Controls.Frame>.</span><span class="sxs-lookup"><span data-stu-id="2d5a4-107">The following table lists the named parts for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="2d5a4-108">Parte</span><span class="sxs-lookup"><span data-stu-id="2d5a4-108">Part</span></span>|<span data-ttu-id="2d5a4-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="2d5a4-109">Type</span></span>|<span data-ttu-id="2d5a4-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="2d5a4-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="2d5a4-111">PART_FrameCP</span><span class="sxs-lookup"><span data-stu-id="2d5a4-111">PART_FrameCP</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="2d5a4-112">A área de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="2d5a4-112">The content area.</span></span>|  
  
## <a name="frame-states"></a><span data-ttu-id="2d5a4-113">Estados do quadro</span><span class="sxs-lookup"><span data-stu-id="2d5a4-113">Frame States</span></span>  
 <span data-ttu-id="2d5a4-114">A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Controls.Frame>.</span><span class="sxs-lookup"><span data-stu-id="2d5a4-114">The following table lists the visual states for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="2d5a4-115">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="2d5a4-115">VisualState Name</span></span>|<span data-ttu-id="2d5a4-116">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="2d5a4-116">VisualStateGroup Name</span></span>|<span data-ttu-id="2d5a4-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="2d5a4-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="2d5a4-118">Válido</span><span class="sxs-lookup"><span data-stu-id="2d5a4-118">Valid</span></span>|<span data-ttu-id="2d5a4-119">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2d5a4-119">ValidationStates</span></span>|<span data-ttu-id="2d5a4-120">O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.</span><span class="sxs-lookup"><span data-stu-id="2d5a4-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="2d5a4-121">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="2d5a4-121">InvalidFocused</span></span>|<span data-ttu-id="2d5a4-122">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2d5a4-122">ValidationStates</span></span>|<span data-ttu-id="2d5a4-123">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.</span><span class="sxs-lookup"><span data-stu-id="2d5a4-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="2d5a4-124">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="2d5a4-124">InvalidUnfocused</span></span>|<span data-ttu-id="2d5a4-125">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2d5a4-125">ValidationStates</span></span>|<span data-ttu-id="2d5a4-126">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="2d5a4-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="frame-controltemplate-example"></a><span data-ttu-id="2d5a4-127">Exemplo de ControlTemplate de quadro</span><span class="sxs-lookup"><span data-stu-id="2d5a4-127">Frame ControlTemplate Example</span></span>  
 <span data-ttu-id="2d5a4-128">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o controle de <xref:System.Windows.Controls.Frame>.</span><span class="sxs-lookup"><span data-stu-id="2d5a4-128">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Frame](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/frame.xaml#frame)]  
  
 <span data-ttu-id="2d5a4-129">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="2d5a4-129">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="2d5a4-130">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="2d5a4-130">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d5a4-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2d5a4-131">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="2d5a4-132">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="2d5a4-132">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="2d5a4-133">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="2d5a4-133">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="2d5a4-134">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="2d5a4-134">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="2d5a4-135">Criar um modelo para um controle</span><span class="sxs-lookup"><span data-stu-id="2d5a4-135">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
