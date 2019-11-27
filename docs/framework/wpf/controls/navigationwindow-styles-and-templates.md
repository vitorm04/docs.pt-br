---
title: Estilos e modelos NavigationWindow
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], NavigationWindow
- NavigationWindow [WPF], styles and templates
- ControlTemplate [WPF], NavigationWindow
- parts [WPF], NavigationWindow
- styles [WPF], NavigationWindow
- templates [WPF], NavigationWindow
ms.assetid: 3656055e-3222-43c8-b868-fd0c90cc31a3
ms.openlocfilehash: 5cc504956ce036505ac9261ea1438c7881fa2790
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283488"
---
# <a name="navigationwindow-styles-and-templates"></a><span data-ttu-id="63c59-102">Estilos e modelos NavigationWindow</span><span class="sxs-lookup"><span data-stu-id="63c59-102">NavigationWindow Styles and Templates</span></span>
<span data-ttu-id="63c59-103">Este tópico descreve os estilos e modelos para o controle de <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="63c59-103">This topic describes the styles and templates for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span> <span data-ttu-id="63c59-104">Você pode modificar o <xref:System.Windows.Controls.ControlTemplate> padrão para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="63c59-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="63c59-105">Para obter mais informações, consulte [criar um modelo para um controle](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="63c59-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="navigationwindow-parts"></a><span data-ttu-id="63c59-106">Partes NavigationWindow</span><span class="sxs-lookup"><span data-stu-id="63c59-106">NavigationWindow Parts</span></span>  
 <span data-ttu-id="63c59-107">A tabela a seguir lista as partes nomeadas para o controle de <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="63c59-107">The following table lists the named parts for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span>  
  
|<span data-ttu-id="63c59-108">Parte</span><span class="sxs-lookup"><span data-stu-id="63c59-108">Part</span></span>|<span data-ttu-id="63c59-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="63c59-109">Type</span></span>|<span data-ttu-id="63c59-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="63c59-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="63c59-111">PART_NavWinCP</span><span class="sxs-lookup"><span data-stu-id="63c59-111">PART_NavWinCP</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="63c59-112">A área do conteúdo.</span><span class="sxs-lookup"><span data-stu-id="63c59-112">The area for the content.</span></span>|  
  
## <a name="navigationwindow-states"></a><span data-ttu-id="63c59-113">Estados da NavigationWindow</span><span class="sxs-lookup"><span data-stu-id="63c59-113">NavigationWindow States</span></span>  
 <span data-ttu-id="63c59-114">A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="63c59-114">The following table lists the visual states for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span>  
  
|<span data-ttu-id="63c59-115">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="63c59-115">VisualState Name</span></span>|<span data-ttu-id="63c59-116">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="63c59-116">VisualStateGroup Name</span></span>|<span data-ttu-id="63c59-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="63c59-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="63c59-118">Válido</span><span class="sxs-lookup"><span data-stu-id="63c59-118">Valid</span></span>|<span data-ttu-id="63c59-119">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="63c59-119">ValidationStates</span></span>|<span data-ttu-id="63c59-120">O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.</span><span class="sxs-lookup"><span data-stu-id="63c59-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="63c59-121">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="63c59-121">InvalidFocused</span></span>|<span data-ttu-id="63c59-122">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="63c59-122">ValidationStates</span></span>|<span data-ttu-id="63c59-123">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.</span><span class="sxs-lookup"><span data-stu-id="63c59-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="63c59-124">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="63c59-124">InvalidUnfocused</span></span>|<span data-ttu-id="63c59-125">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="63c59-125">ValidationStates</span></span>|<span data-ttu-id="63c59-126">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="63c59-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="navigationwindow-controltemplate-example"></a><span data-ttu-id="63c59-127">Exemplo de ControlTemplate de NavigationWindow</span><span class="sxs-lookup"><span data-stu-id="63c59-127">NavigationWindow ControlTemplate Example</span></span>  
 <span data-ttu-id="63c59-128">Embora este exemplo contenha todos os elementos que são definidos no <xref:System.Windows.Controls.ControlTemplate> de um <xref:System.Windows.Navigation.NavigationWindow> por padrão, os valores específicos devem ser considerados como exemplos.</span><span class="sxs-lookup"><span data-stu-id="63c59-128">Although this example contains all of the elements that are defined in the <xref:System.Windows.Controls.ControlTemplate> of a <xref:System.Windows.Navigation.NavigationWindow> by default, the specific values should be thought of as examples.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#NavigationWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/navigationwindow.xaml#navigationwindow)]  
  
 <span data-ttu-id="63c59-129">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="63c59-129">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ResizeGrip](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/resizegrip.xaml#resizegrip)]  
[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="63c59-130">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="63c59-130">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63c59-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="63c59-131">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="63c59-132">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="63c59-132">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="63c59-133">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="63c59-133">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="63c59-134">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="63c59-134">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="63c59-135">Criar um modelo para um controle</span><span class="sxs-lookup"><span data-stu-id="63c59-135">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
