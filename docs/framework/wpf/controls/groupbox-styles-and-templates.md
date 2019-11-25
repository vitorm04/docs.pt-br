---
title: Estilos e modelos GroupBox
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], GroupBox
- parts [WPF], GroupBox
- GroupBox [WPF], styles and templates
- states [WPF], GroupBox
- styles [WPF], GroupBox
- templates [WPF], GroupBox
ms.assetid: 33df7037-0a1b-476f-b9d0-41566a777699
ms.openlocfilehash: e5befffc86f26176da4accfc01239a08d4978713
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283759"
---
# <a name="groupbox-styles-and-templates"></a><span data-ttu-id="994b1-102">Estilos e modelos GroupBox</span><span class="sxs-lookup"><span data-stu-id="994b1-102">GroupBox Styles and Templates</span></span>
<a name="introduction"></a><span data-ttu-id="994b1-103">Este tópico descreve os estilos e modelos para o controle de <xref:System.Windows.Controls.GroupBox>.</span><span class="sxs-lookup"><span data-stu-id="994b1-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.GroupBox> control.</span></span> <span data-ttu-id="994b1-104">Você pode modificar o <xref:System.Windows.Controls.ControlTemplate> padrão para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="994b1-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="994b1-105">Para obter mais informações, consulte [criar um modelo para um controle](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="994b1-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
<a name="groupbox_parts"></a>   
## <a name="groupbox-parts"></a><span data-ttu-id="994b1-106">Partes da caixa de GroupBox</span><span class="sxs-lookup"><span data-stu-id="994b1-106">GroupBox Parts</span></span>  
 <span data-ttu-id="994b1-107">O controle de <xref:System.Windows.Controls.GroupBox> não tem nenhuma parte nomeada.</span><span class="sxs-lookup"><span data-stu-id="994b1-107">The <xref:System.Windows.Controls.GroupBox> control does not have any named parts.</span></span>  
  
<a name="groupbox_states"></a>   
## <a name="groupbox-states"></a><span data-ttu-id="994b1-108">Estados da GroupBox</span><span class="sxs-lookup"><span data-stu-id="994b1-108">GroupBox States</span></span>  
 <span data-ttu-id="994b1-109">A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Controls.GroupBox>.</span><span class="sxs-lookup"><span data-stu-id="994b1-109">The following table lists the visual states for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
|<span data-ttu-id="994b1-110">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="994b1-110">VisualState Name</span></span>|<span data-ttu-id="994b1-111">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="994b1-111">VisualStateGroup Name</span></span>|<span data-ttu-id="994b1-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="994b1-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="994b1-113">Válido</span><span class="sxs-lookup"><span data-stu-id="994b1-113">Valid</span></span>|<span data-ttu-id="994b1-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="994b1-114">ValidationStates</span></span>|<span data-ttu-id="994b1-115">O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.</span><span class="sxs-lookup"><span data-stu-id="994b1-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="994b1-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="994b1-116">InvalidFocused</span></span>|<span data-ttu-id="994b1-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="994b1-117">ValidationStates</span></span>|<span data-ttu-id="994b1-118">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.</span><span class="sxs-lookup"><span data-stu-id="994b1-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="994b1-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="994b1-119">InvalidUnfocused</span></span>|<span data-ttu-id="994b1-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="994b1-120">ValidationStates</span></span>|<span data-ttu-id="994b1-121">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="994b1-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
<a name="groupbox_controltemplate_example"></a>   
## <a name="groupbox-controltemplate-example"></a><span data-ttu-id="994b1-122">Exemplo de ControlTemplate de GroupBox</span><span class="sxs-lookup"><span data-stu-id="994b1-122">GroupBox ControlTemplate Example</span></span>  
 <span data-ttu-id="994b1-123">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o controle de <xref:System.Windows.Controls.GroupBox>.</span><span class="sxs-lookup"><span data-stu-id="994b1-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#GroupBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/groupbox.xaml#groupbox)]  
  
 <span data-ttu-id="994b1-124">O <xref:System.Windows.Controls.ControlTemplate> usa um ou mais dos recursos a seguir.</span><span class="sxs-lookup"><span data-stu-id="994b1-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="994b1-125">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="994b1-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="994b1-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="994b1-126">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="994b1-127">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="994b1-127">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="994b1-128">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="994b1-128">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="994b1-129">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="994b1-129">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="994b1-130">Criar um modelo para um controle</span><span class="sxs-lookup"><span data-stu-id="994b1-130">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
