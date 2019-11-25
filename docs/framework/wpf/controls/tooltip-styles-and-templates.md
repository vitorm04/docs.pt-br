---
title: Estilos e modelos ToolTip
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], ToolTip
- styles [WPF], ToolTip
- states [WPF], ToolTip
- ToolTip [WPF], styles and templates
- ControlTemplate [WPF], ToolTip
- templates [WPF], ToolTip
ms.assetid: 405fe385-4de9-49ee-a448-d8f4d1f740dd
ms.openlocfilehash: c7a14034d665c124d01e8a4b43c5d42968241925
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283641"
---
# <a name="tooltip-styles-and-templates"></a><span data-ttu-id="29fd0-102">Estilos e modelos ToolTip</span><span class="sxs-lookup"><span data-stu-id="29fd0-102">ToolTip Styles and Templates</span></span>
<span data-ttu-id="29fd0-103">Este tópico descreve os estilos e modelos para o controle de <xref:System.Windows.Controls.ToolTip>.</span><span class="sxs-lookup"><span data-stu-id="29fd0-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolTip> control.</span></span> <span data-ttu-id="29fd0-104">Você pode modificar o <xref:System.Windows.Controls.ControlTemplate> padrão para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="29fd0-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="29fd0-105">Para obter mais informações, consulte [criar um modelo para um controle](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="29fd0-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="tooltip-parts"></a><span data-ttu-id="29fd0-106">Partes da dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="29fd0-106">ToolTip Parts</span></span>  
 <span data-ttu-id="29fd0-107">O controle de <xref:System.Windows.Controls.ToolTip> não tem nenhuma parte nomeada.</span><span class="sxs-lookup"><span data-stu-id="29fd0-107">The <xref:System.Windows.Controls.ToolTip> control does not have any named parts.</span></span>  
  
## <a name="tooltip-states"></a><span data-ttu-id="29fd0-108">Estados da dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="29fd0-108">ToolTip States</span></span>  
 <span data-ttu-id="29fd0-109">A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Controls.ToolTip>.</span><span class="sxs-lookup"><span data-stu-id="29fd0-109">The following table lists the visual states for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
|<span data-ttu-id="29fd0-110">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="29fd0-110">VisualState Name</span></span>|<span data-ttu-id="29fd0-111">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="29fd0-111">VisualStateGroup Name</span></span>|<span data-ttu-id="29fd0-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="29fd0-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="29fd0-113">Fechado</span><span class="sxs-lookup"><span data-stu-id="29fd0-113">Closed</span></span>|<span data-ttu-id="29fd0-114">OpenStates</span><span class="sxs-lookup"><span data-stu-id="29fd0-114">OpenStates</span></span>|<span data-ttu-id="29fd0-115">O estado padrão.</span><span class="sxs-lookup"><span data-stu-id="29fd0-115">The default state.</span></span>|  
|<span data-ttu-id="29fd0-116">Abrir</span><span class="sxs-lookup"><span data-stu-id="29fd0-116">Open</span></span>|<span data-ttu-id="29fd0-117">OpenStates</span><span class="sxs-lookup"><span data-stu-id="29fd0-117">OpenStates</span></span>|<span data-ttu-id="29fd0-118">O <xref:System.Windows.Controls.ToolTip> está visível.</span><span class="sxs-lookup"><span data-stu-id="29fd0-118">The <xref:System.Windows.Controls.ToolTip> is visible.</span></span>|  
|<span data-ttu-id="29fd0-119">Válido</span><span class="sxs-lookup"><span data-stu-id="29fd0-119">Valid</span></span>|<span data-ttu-id="29fd0-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="29fd0-120">ValidationStates</span></span>|<span data-ttu-id="29fd0-121">O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.</span><span class="sxs-lookup"><span data-stu-id="29fd0-121">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="29fd0-122">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="29fd0-122">InvalidFocused</span></span>|<span data-ttu-id="29fd0-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="29fd0-123">ValidationStates</span></span>|<span data-ttu-id="29fd0-124">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.</span><span class="sxs-lookup"><span data-stu-id="29fd0-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="29fd0-125">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="29fd0-125">InvalidUnfocused</span></span>|<span data-ttu-id="29fd0-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="29fd0-126">ValidationStates</span></span>|<span data-ttu-id="29fd0-127">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="29fd0-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="tooltip-controltemplate-example"></a><span data-ttu-id="29fd0-128">Exemplo de ControlTemplate de dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="29fd0-128">ToolTip ControlTemplate Example</span></span>  
 <span data-ttu-id="29fd0-129">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o controle de <xref:System.Windows.Controls.ToolTip>.</span><span class="sxs-lookup"><span data-stu-id="29fd0-129">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/tooltip.xaml#tooltip)]  
  
 <span data-ttu-id="29fd0-130">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="29fd0-130">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="29fd0-131">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="29fd0-131">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29fd0-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29fd0-132">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="29fd0-133">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="29fd0-133">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="29fd0-134">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="29fd0-134">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="29fd0-135">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="29fd0-135">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="29fd0-136">Criar um modelo para um controle</span><span class="sxs-lookup"><span data-stu-id="29fd0-136">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
