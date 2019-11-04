---
title: Estilos e modelos de janela
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], Window
- templates [WPF], Window
- styles [WPF], Window
- ControlTemplate [WPF], Window
- Window [WPF], styles and templates
- states [WPF], Window
ms.assetid: 2dfdf025-347b-4342-bf28-95206c273f35
ms.openlocfilehash: 48fe5887ebad86efad1b1aae39ba03a26fda3bd8
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460022"
---
# <a name="window-styles-and-templates"></a><span data-ttu-id="6fc36-102">Estilos e modelos de janela</span><span class="sxs-lookup"><span data-stu-id="6fc36-102">Window Styles and Templates</span></span>
<span data-ttu-id="6fc36-103">Este tópico descreve os estilos e modelos para o controle de <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="6fc36-103">This topic describes the styles and templates for the <xref:System.Windows.Window> control.</span></span> <span data-ttu-id="6fc36-104">Você pode modificar o <xref:System.Windows.Controls.ControlTemplate> padrão para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="6fc36-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="6fc36-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="6fc36-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="window-parts"></a><span data-ttu-id="6fc36-106">Partes da janela</span><span class="sxs-lookup"><span data-stu-id="6fc36-106">Window Parts</span></span>  
 <span data-ttu-id="6fc36-107">O controle de <xref:System.Windows.Window> não tem nenhuma parte nomeada.</span><span class="sxs-lookup"><span data-stu-id="6fc36-107">The <xref:System.Windows.Window> control does not have any named parts.</span></span>  
  
## <a name="window-states"></a><span data-ttu-id="6fc36-108">Estados da janela</span><span class="sxs-lookup"><span data-stu-id="6fc36-108">Window States</span></span>  
 <span data-ttu-id="6fc36-109">A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="6fc36-109">The following table lists the visual states for the <xref:System.Windows.Window> control.</span></span>  
  
|<span data-ttu-id="6fc36-110">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="6fc36-110">VisualState Name</span></span>|<span data-ttu-id="6fc36-111">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="6fc36-111">VisualStateGroup Name</span></span>|<span data-ttu-id="6fc36-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="6fc36-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="6fc36-113">Válido</span><span class="sxs-lookup"><span data-stu-id="6fc36-113">Valid</span></span>|<span data-ttu-id="6fc36-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6fc36-114">ValidationStates</span></span>|<span data-ttu-id="6fc36-115">O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.</span><span class="sxs-lookup"><span data-stu-id="6fc36-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="6fc36-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="6fc36-116">InvalidFocused</span></span>|<span data-ttu-id="6fc36-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6fc36-117">ValidationStates</span></span>|<span data-ttu-id="6fc36-118">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.</span><span class="sxs-lookup"><span data-stu-id="6fc36-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="6fc36-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="6fc36-119">InvalidUnfocused</span></span>|<span data-ttu-id="6fc36-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="6fc36-120">ValidationStates</span></span>|<span data-ttu-id="6fc36-121">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="6fc36-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="window-controltemplate-example"></a><span data-ttu-id="6fc36-122">Exemplo de ControlTemplate de janela</span><span class="sxs-lookup"><span data-stu-id="6fc36-122">Window ControlTemplate Example</span></span>  
 <span data-ttu-id="6fc36-123">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o controle de <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="6fc36-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Window> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Window](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/window.xaml#window)]  
  
 <span data-ttu-id="6fc36-124">O <xref:System.Windows.Controls.ControlTemplate> usa um ou mais dos recursos a seguir.</span><span class="sxs-lookup"><span data-stu-id="6fc36-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ResizeGrip](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/resizegrip.xaml#resizegrip)]  
[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="6fc36-125">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="6fc36-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fc36-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6fc36-126">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="6fc36-127">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="6fc36-127">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="6fc36-128">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="6fc36-128">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="6fc36-129">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="6fc36-129">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="6fc36-130">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="6fc36-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
