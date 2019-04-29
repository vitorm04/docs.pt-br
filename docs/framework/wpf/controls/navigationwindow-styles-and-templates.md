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
ms.openlocfilehash: 32d8aac99d40693e66c7b52a6c7d2c116d2f3baf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61770650"
---
# <a name="navigationwindow-styles-and-templates"></a><span data-ttu-id="6a582-102">Estilos e modelos NavigationWindow</span><span class="sxs-lookup"><span data-stu-id="6a582-102">NavigationWindow Styles and Templates</span></span>
<span data-ttu-id="6a582-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Navigation.NavigationWindow> controle.</span><span class="sxs-lookup"><span data-stu-id="6a582-103">This topic describes the styles and templates for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span> <span data-ttu-id="6a582-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="6a582-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="6a582-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="6a582-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="navigationwindow-parts"></a><span data-ttu-id="6a582-106">Partes do NavigationWindow</span><span class="sxs-lookup"><span data-stu-id="6a582-106">NavigationWindow Parts</span></span>  
 <span data-ttu-id="6a582-107">A tabela a seguir lista as partes nomeadas para o <xref:System.Windows.Navigation.NavigationWindow> controle.</span><span class="sxs-lookup"><span data-stu-id="6a582-107">The following table lists the named parts for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span>  
  
|<span data-ttu-id="6a582-108">Parte</span><span class="sxs-lookup"><span data-stu-id="6a582-108">Part</span></span>|<span data-ttu-id="6a582-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="6a582-109">Type</span></span>|<span data-ttu-id="6a582-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="6a582-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="6a582-111">PART_NavWinCP</span><span class="sxs-lookup"><span data-stu-id="6a582-111">PART_NavWinCP</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="6a582-112">A área de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="6a582-112">The area for the content.</span></span>|  
  
## <a name="navigationwindow-states"></a><span data-ttu-id="6a582-113">Estados de NavigationWindow</span><span class="sxs-lookup"><span data-stu-id="6a582-113">NavigationWindow States</span></span>  
 <span data-ttu-id="6a582-114">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Navigation.NavigationWindow> controle.</span><span class="sxs-lookup"><span data-stu-id="6a582-114">The following table lists the visual states for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span>  
  
|<span data-ttu-id="6a582-115">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="6a582-115">VisualState Name</span></span>|<span data-ttu-id="6a582-116">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="6a582-116">VisualStateGroup Name</span></span>|<span data-ttu-id="6a582-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="6a582-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="6a582-118">Válido</span><span class="sxs-lookup"><span data-stu-id="6a582-118">Valid</span></span>|<span data-ttu-id="6a582-119">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6a582-119">ValidationStates</span></span>|<span data-ttu-id="6a582-120">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="6a582-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="6a582-121">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="6a582-121">InvalidFocused</span></span>|<span data-ttu-id="6a582-122">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6a582-122">ValidationStates</span></span>|<span data-ttu-id="6a582-123">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="6a582-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="6a582-124">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="6a582-124">InvalidUnfocused</span></span>|<span data-ttu-id="6a582-125">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6a582-125">ValidationStates</span></span>|<span data-ttu-id="6a582-126">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle não tem o foco.</span><span class="sxs-lookup"><span data-stu-id="6a582-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="navigationwindow-controltemplate-example"></a><span data-ttu-id="6a582-127">Exemplo de ControlTemplate NavigationWindow</span><span class="sxs-lookup"><span data-stu-id="6a582-127">NavigationWindow ControlTemplate Example</span></span>  
 <span data-ttu-id="6a582-128">Embora este exemplo contém todos os elementos que são definidos na <xref:System.Windows.Controls.ControlTemplate> de um <xref:System.Windows.Navigation.NavigationWindow> por padrão, os valores específicos devem ser pensados como exemplos.</span><span class="sxs-lookup"><span data-stu-id="6a582-128">Although this example contains all of the elements that are defined in the <xref:System.Windows.Controls.ControlTemplate> of a <xref:System.Windows.Navigation.NavigationWindow> by default, the specific values should be thought of as examples.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#NavigationWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/navigationwindow.xaml#navigationwindow)]  
  
 <span data-ttu-id="6a582-129">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="6a582-129">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ResizeGrip](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/resizegrip.xaml#resizegrip)]  
[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="6a582-130">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="6a582-130">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a582-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6a582-131">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="6a582-132">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="6a582-132">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="6a582-133">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="6a582-133">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="6a582-134">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="6a582-134">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="6a582-135">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="6a582-135">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
