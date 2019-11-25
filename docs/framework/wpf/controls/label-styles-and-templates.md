---
title: Estilos e modelos de rótulo
ms.date: 03/30/2017
helpviewer_keywords:
- templates [WPF], Label
- parts [WPF], Label
- ControlTemplate [WPF], Label
- styles [WPF], Label
- Label [WPF], styles and templates
- states [WPF], Label
ms.assetid: c1d5359a-8e4a-4925-ab3e-e92bf6694859
ms.openlocfilehash: 35fcd9c15bf44d15a08c16d58847698c5ec6e574
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283501"
---
# <a name="label-styles-and-templates"></a><span data-ttu-id="62623-102">Estilos e modelos de rótulo</span><span class="sxs-lookup"><span data-stu-id="62623-102">Label Styles and Templates</span></span>
<span data-ttu-id="62623-103">Este tópico descreve os estilos e modelos para o controle de <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="62623-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Label> control.</span></span> <span data-ttu-id="62623-104">Você pode modificar o <xref:System.Windows.Controls.ControlTemplate> padrão para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="62623-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="62623-105">Para obter mais informações, consulte [criar um modelo para um controle](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="62623-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="label-parts"></a><span data-ttu-id="62623-106">Partes de rótulo</span><span class="sxs-lookup"><span data-stu-id="62623-106">Label Parts</span></span>  
 <span data-ttu-id="62623-107">O controle de <xref:System.Windows.Controls.Label> não tem nenhuma parte nomeada.</span><span class="sxs-lookup"><span data-stu-id="62623-107">The <xref:System.Windows.Controls.Label> control does not have any named parts.</span></span>  
  
## <a name="label-states"></a><span data-ttu-id="62623-108">Estados de rótulo</span><span class="sxs-lookup"><span data-stu-id="62623-108">Label States</span></span>  
 <span data-ttu-id="62623-109">A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="62623-109">The following table lists the visual states for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
|<span data-ttu-id="62623-110">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="62623-110">VisualState Name</span></span>|<span data-ttu-id="62623-111">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="62623-111">VisualStateGroup Name</span></span>|<span data-ttu-id="62623-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="62623-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="62623-113">Válido</span><span class="sxs-lookup"><span data-stu-id="62623-113">Valid</span></span>|<span data-ttu-id="62623-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="62623-114">ValidationStates</span></span>|<span data-ttu-id="62623-115">O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.</span><span class="sxs-lookup"><span data-stu-id="62623-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="62623-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="62623-116">InvalidFocused</span></span>|<span data-ttu-id="62623-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="62623-117">ValidationStates</span></span>|<span data-ttu-id="62623-118">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.</span><span class="sxs-lookup"><span data-stu-id="62623-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="62623-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="62623-119">InvalidUnfocused</span></span>|<span data-ttu-id="62623-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="62623-120">ValidationStates</span></span>|<span data-ttu-id="62623-121">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="62623-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="label-controltemplate-example"></a><span data-ttu-id="62623-122">Exemplo de ControlTemplate de rótulo</span><span class="sxs-lookup"><span data-stu-id="62623-122">Label ControlTemplate Example</span></span>  
 <span data-ttu-id="62623-123">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o controle de <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="62623-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Label](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/label.xaml#label)]  
  
 <span data-ttu-id="62623-124">O <xref:System.Windows.Controls.ControlTemplate> usa um ou mais dos recursos a seguir.</span><span class="sxs-lookup"><span data-stu-id="62623-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="62623-125">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="62623-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62623-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="62623-126">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="62623-127">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="62623-127">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="62623-128">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="62623-128">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="62623-129">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="62623-129">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="62623-130">Criar um modelo para um controle</span><span class="sxs-lookup"><span data-stu-id="62623-130">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
