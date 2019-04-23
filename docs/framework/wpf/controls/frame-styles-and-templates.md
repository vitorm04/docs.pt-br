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
ms.openlocfilehash: 6b084cfa31efebe2456871a99cd810741aa26609
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59131009"
---
# <a name="frame-styles-and-templates"></a><span data-ttu-id="af1cf-102">Estilos e modelos de quadro</span><span class="sxs-lookup"><span data-stu-id="af1cf-102">Frame Styles and Templates</span></span>
<span data-ttu-id="af1cf-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.Frame> controle.</span><span class="sxs-lookup"><span data-stu-id="af1cf-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Frame> control.</span></span> <span data-ttu-id="af1cf-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="af1cf-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="af1cf-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="af1cf-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="frame-parts"></a><span data-ttu-id="af1cf-106">Partes do quadro</span><span class="sxs-lookup"><span data-stu-id="af1cf-106">Frame Parts</span></span>  
 <span data-ttu-id="af1cf-107">A tabela a seguir lista as partes nomeadas para o <xref:System.Windows.Controls.Frame> controle.</span><span class="sxs-lookup"><span data-stu-id="af1cf-107">The following table lists the named parts for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="af1cf-108">Parte</span><span class="sxs-lookup"><span data-stu-id="af1cf-108">Part</span></span>|<span data-ttu-id="af1cf-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="af1cf-109">Type</span></span>|<span data-ttu-id="af1cf-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="af1cf-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="af1cf-111">PART_FrameCP</span><span class="sxs-lookup"><span data-stu-id="af1cf-111">PART_FrameCP</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="af1cf-112">A área de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="af1cf-112">The content area.</span></span>|  
  
## <a name="frame-states"></a><span data-ttu-id="af1cf-113">Estados de quadro</span><span class="sxs-lookup"><span data-stu-id="af1cf-113">Frame States</span></span>  
 <span data-ttu-id="af1cf-114">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.Frame> controle.</span><span class="sxs-lookup"><span data-stu-id="af1cf-114">The following table lists the visual states for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="af1cf-115">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="af1cf-115">VisualState Name</span></span>|<span data-ttu-id="af1cf-116">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="af1cf-116">VisualStateGroup Name</span></span>|<span data-ttu-id="af1cf-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="af1cf-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="af1cf-118">Válido</span><span class="sxs-lookup"><span data-stu-id="af1cf-118">Valid</span></span>|<span data-ttu-id="af1cf-119">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="af1cf-119">ValidationStates</span></span>|<span data-ttu-id="af1cf-120">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="af1cf-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="af1cf-121">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="af1cf-121">InvalidFocused</span></span>|<span data-ttu-id="af1cf-122">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="af1cf-122">ValidationStates</span></span>|<span data-ttu-id="af1cf-123">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="af1cf-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="af1cf-124">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="af1cf-124">InvalidUnfocused</span></span>|<span data-ttu-id="af1cf-125">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="af1cf-125">ValidationStates</span></span>|<span data-ttu-id="af1cf-126">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle não tem o foco.</span><span class="sxs-lookup"><span data-stu-id="af1cf-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="frame-controltemplate-example"></a><span data-ttu-id="af1cf-127">Exemplo de ControlTemplate de quadro</span><span class="sxs-lookup"><span data-stu-id="af1cf-127">Frame ControlTemplate Example</span></span>  
 <span data-ttu-id="af1cf-128">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.Frame> controle.</span><span class="sxs-lookup"><span data-stu-id="af1cf-128">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Frame](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/frame.xaml#frame)]  
  
 <span data-ttu-id="af1cf-129">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="af1cf-129">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="af1cf-130">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="af1cf-130">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af1cf-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="af1cf-131">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="af1cf-132">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="af1cf-132">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="af1cf-133">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="af1cf-133">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="af1cf-134">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="af1cf-134">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="af1cf-135">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="af1cf-135">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
