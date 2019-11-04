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
ms.openlocfilehash: 4aae14299b3959e7d2122991954cc62505d2a19e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460197"
---
# <a name="navigationwindow-styles-and-templates"></a><span data-ttu-id="f44af-102">Estilos e modelos NavigationWindow</span><span class="sxs-lookup"><span data-stu-id="f44af-102">NavigationWindow Styles and Templates</span></span>
<span data-ttu-id="f44af-103">Este tópico descreve os estilos e modelos para o controle de <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="f44af-103">This topic describes the styles and templates for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span> <span data-ttu-id="f44af-104">Você pode modificar o <xref:System.Windows.Controls.ControlTemplate> padrão para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="f44af-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="f44af-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="f44af-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="navigationwindow-parts"></a><span data-ttu-id="f44af-106">Partes NavigationWindow</span><span class="sxs-lookup"><span data-stu-id="f44af-106">NavigationWindow Parts</span></span>  
 <span data-ttu-id="f44af-107">A tabela a seguir lista as partes nomeadas para o controle de <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="f44af-107">The following table lists the named parts for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span>  
  
|<span data-ttu-id="f44af-108">Parte</span><span class="sxs-lookup"><span data-stu-id="f44af-108">Part</span></span>|<span data-ttu-id="f44af-109">Digite</span><span class="sxs-lookup"><span data-stu-id="f44af-109">Type</span></span>|<span data-ttu-id="f44af-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="f44af-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="f44af-111">PART_NavWinCP</span><span class="sxs-lookup"><span data-stu-id="f44af-111">PART_NavWinCP</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="f44af-112">A área do conteúdo.</span><span class="sxs-lookup"><span data-stu-id="f44af-112">The area for the content.</span></span>|  
  
## <a name="navigationwindow-states"></a><span data-ttu-id="f44af-113">Estados da NavigationWindow</span><span class="sxs-lookup"><span data-stu-id="f44af-113">NavigationWindow States</span></span>  
 <span data-ttu-id="f44af-114">A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="f44af-114">The following table lists the visual states for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span>  
  
|<span data-ttu-id="f44af-115">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="f44af-115">VisualState Name</span></span>|<span data-ttu-id="f44af-116">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="f44af-116">VisualStateGroup Name</span></span>|<span data-ttu-id="f44af-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="f44af-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="f44af-118">Válido</span><span class="sxs-lookup"><span data-stu-id="f44af-118">Valid</span></span>|<span data-ttu-id="f44af-119">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f44af-119">ValidationStates</span></span>|<span data-ttu-id="f44af-120">O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.</span><span class="sxs-lookup"><span data-stu-id="f44af-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="f44af-121">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="f44af-121">InvalidFocused</span></span>|<span data-ttu-id="f44af-122">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f44af-122">ValidationStates</span></span>|<span data-ttu-id="f44af-123">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.</span><span class="sxs-lookup"><span data-stu-id="f44af-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="f44af-124">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="f44af-124">InvalidUnfocused</span></span>|<span data-ttu-id="f44af-125">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f44af-125">ValidationStates</span></span>|<span data-ttu-id="f44af-126">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="f44af-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="navigationwindow-controltemplate-example"></a><span data-ttu-id="f44af-127">Exemplo de ControlTemplate de NavigationWindow</span><span class="sxs-lookup"><span data-stu-id="f44af-127">NavigationWindow ControlTemplate Example</span></span>  
 <span data-ttu-id="f44af-128">Embora este exemplo contenha todos os elementos que são definidos no <xref:System.Windows.Controls.ControlTemplate> de um <xref:System.Windows.Navigation.NavigationWindow> por padrão, os valores específicos devem ser considerados como exemplos.</span><span class="sxs-lookup"><span data-stu-id="f44af-128">Although this example contains all of the elements that are defined in the <xref:System.Windows.Controls.ControlTemplate> of a <xref:System.Windows.Navigation.NavigationWindow> by default, the specific values should be thought of as examples.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#NavigationWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/navigationwindow.xaml#navigationwindow)]  
  
 <span data-ttu-id="f44af-129">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="f44af-129">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ResizeGrip](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/resizegrip.xaml#resizegrip)]  
[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="f44af-130">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="f44af-130">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f44af-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f44af-131">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="f44af-132">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="f44af-132">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="f44af-133">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="f44af-133">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="f44af-134">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="f44af-134">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="f44af-135">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="f44af-135">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
