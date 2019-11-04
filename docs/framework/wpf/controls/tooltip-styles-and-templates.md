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
ms.openlocfilehash: 626d0b4d49d653f820d1506f0aa09f06d26352c2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458640"
---
# <a name="tooltip-styles-and-templates"></a><span data-ttu-id="3434e-102">Estilos e modelos ToolTip</span><span class="sxs-lookup"><span data-stu-id="3434e-102">ToolTip Styles and Templates</span></span>
<span data-ttu-id="3434e-103">Este tópico descreve os estilos e modelos para o controle de <xref:System.Windows.Controls.ToolTip>.</span><span class="sxs-lookup"><span data-stu-id="3434e-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ToolTip> control.</span></span> <span data-ttu-id="3434e-104">Você pode modificar o <xref:System.Windows.Controls.ControlTemplate> padrão para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="3434e-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="3434e-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="3434e-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="tooltip-parts"></a><span data-ttu-id="3434e-106">Partes da dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="3434e-106">ToolTip Parts</span></span>  
 <span data-ttu-id="3434e-107">O controle de <xref:System.Windows.Controls.ToolTip> não tem nenhuma parte nomeada.</span><span class="sxs-lookup"><span data-stu-id="3434e-107">The <xref:System.Windows.Controls.ToolTip> control does not have any named parts.</span></span>  
  
## <a name="tooltip-states"></a><span data-ttu-id="3434e-108">Estados da dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="3434e-108">ToolTip States</span></span>  
 <span data-ttu-id="3434e-109">A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Controls.ToolTip>.</span><span class="sxs-lookup"><span data-stu-id="3434e-109">The following table lists the visual states for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
|<span data-ttu-id="3434e-110">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="3434e-110">VisualState Name</span></span>|<span data-ttu-id="3434e-111">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="3434e-111">VisualStateGroup Name</span></span>|<span data-ttu-id="3434e-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="3434e-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="3434e-113">Closed</span><span class="sxs-lookup"><span data-stu-id="3434e-113">Closed</span></span>|<span data-ttu-id="3434e-114">OpenStates</span><span class="sxs-lookup"><span data-stu-id="3434e-114">OpenStates</span></span>|<span data-ttu-id="3434e-115">O estado padrão.</span><span class="sxs-lookup"><span data-stu-id="3434e-115">The default state.</span></span>|  
|<span data-ttu-id="3434e-116">Abrir</span><span class="sxs-lookup"><span data-stu-id="3434e-116">Open</span></span>|<span data-ttu-id="3434e-117">OpenStates</span><span class="sxs-lookup"><span data-stu-id="3434e-117">OpenStates</span></span>|<span data-ttu-id="3434e-118">O <xref:System.Windows.Controls.ToolTip> está visível.</span><span class="sxs-lookup"><span data-stu-id="3434e-118">The <xref:System.Windows.Controls.ToolTip> is visible.</span></span>|  
|<span data-ttu-id="3434e-119">Válido</span><span class="sxs-lookup"><span data-stu-id="3434e-119">Valid</span></span>|<span data-ttu-id="3434e-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3434e-120">ValidationStates</span></span>|<span data-ttu-id="3434e-121">O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.</span><span class="sxs-lookup"><span data-stu-id="3434e-121">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="3434e-122">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="3434e-122">InvalidFocused</span></span>|<span data-ttu-id="3434e-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3434e-123">ValidationStates</span></span>|<span data-ttu-id="3434e-124">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.</span><span class="sxs-lookup"><span data-stu-id="3434e-124">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="3434e-125">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="3434e-125">InvalidUnfocused</span></span>|<span data-ttu-id="3434e-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="3434e-126">ValidationStates</span></span>|<span data-ttu-id="3434e-127">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="3434e-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="tooltip-controltemplate-example"></a><span data-ttu-id="3434e-128">Exemplo de ControlTemplate de dica de ferramenta</span><span class="sxs-lookup"><span data-stu-id="3434e-128">ToolTip ControlTemplate Example</span></span>  
 <span data-ttu-id="3434e-129">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o controle de <xref:System.Windows.Controls.ToolTip>.</span><span class="sxs-lookup"><span data-stu-id="3434e-129">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ToolTip> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/tooltip.xaml#tooltip)]  
  
 <span data-ttu-id="3434e-130">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="3434e-130">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="3434e-131">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="3434e-131">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3434e-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3434e-132">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="3434e-133">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="3434e-133">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="3434e-134">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="3434e-134">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="3434e-135">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="3434e-135">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="3434e-136">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="3434e-136">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
