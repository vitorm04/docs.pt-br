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
ms.openlocfilehash: 89f4fc21637d20ca226507463093bc6bae2241fc
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460316"
---
# <a name="frame-styles-and-templates"></a><span data-ttu-id="83890-102">Estilos e modelos de quadro</span><span class="sxs-lookup"><span data-stu-id="83890-102">Frame Styles and Templates</span></span>
<span data-ttu-id="83890-103">Este tópico descreve os estilos e modelos para o controle de <xref:System.Windows.Controls.Frame>.</span><span class="sxs-lookup"><span data-stu-id="83890-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Frame> control.</span></span> <span data-ttu-id="83890-104">Você pode modificar o <xref:System.Windows.Controls.ControlTemplate> padrão para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="83890-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="83890-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="83890-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="frame-parts"></a><span data-ttu-id="83890-106">Partes do quadro</span><span class="sxs-lookup"><span data-stu-id="83890-106">Frame Parts</span></span>  
 <span data-ttu-id="83890-107">A tabela a seguir lista as partes nomeadas para o controle de <xref:System.Windows.Controls.Frame>.</span><span class="sxs-lookup"><span data-stu-id="83890-107">The following table lists the named parts for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="83890-108">Parte</span><span class="sxs-lookup"><span data-stu-id="83890-108">Part</span></span>|<span data-ttu-id="83890-109">Digite</span><span class="sxs-lookup"><span data-stu-id="83890-109">Type</span></span>|<span data-ttu-id="83890-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="83890-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="83890-111">PART_FrameCP</span><span class="sxs-lookup"><span data-stu-id="83890-111">PART_FrameCP</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="83890-112">A área de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="83890-112">The content area.</span></span>|  
  
## <a name="frame-states"></a><span data-ttu-id="83890-113">Estados do quadro</span><span class="sxs-lookup"><span data-stu-id="83890-113">Frame States</span></span>  
 <span data-ttu-id="83890-114">A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Controls.Frame>.</span><span class="sxs-lookup"><span data-stu-id="83890-114">The following table lists the visual states for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="83890-115">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="83890-115">VisualState Name</span></span>|<span data-ttu-id="83890-116">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="83890-116">VisualStateGroup Name</span></span>|<span data-ttu-id="83890-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="83890-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="83890-118">Válido</span><span class="sxs-lookup"><span data-stu-id="83890-118">Valid</span></span>|<span data-ttu-id="83890-119">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="83890-119">ValidationStates</span></span>|<span data-ttu-id="83890-120">O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.</span><span class="sxs-lookup"><span data-stu-id="83890-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="83890-121">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="83890-121">InvalidFocused</span></span>|<span data-ttu-id="83890-122">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="83890-122">ValidationStates</span></span>|<span data-ttu-id="83890-123">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.</span><span class="sxs-lookup"><span data-stu-id="83890-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="83890-124">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="83890-124">InvalidUnfocused</span></span>|<span data-ttu-id="83890-125">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="83890-125">ValidationStates</span></span>|<span data-ttu-id="83890-126">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="83890-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="frame-controltemplate-example"></a><span data-ttu-id="83890-127">Exemplo de ControlTemplate de quadro</span><span class="sxs-lookup"><span data-stu-id="83890-127">Frame ControlTemplate Example</span></span>  
 <span data-ttu-id="83890-128">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o controle de <xref:System.Windows.Controls.Frame>.</span><span class="sxs-lookup"><span data-stu-id="83890-128">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Frame](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/frame.xaml#frame)]  
  
 <span data-ttu-id="83890-129">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="83890-129">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="83890-130">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="83890-130">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83890-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="83890-131">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="83890-132">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="83890-132">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="83890-133">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="83890-133">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="83890-134">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="83890-134">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="83890-135">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="83890-135">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
