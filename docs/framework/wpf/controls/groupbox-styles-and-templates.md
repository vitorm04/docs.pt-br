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
ms.openlocfilehash: 474cda0abc6a18c015836c749c78f4d33aa5abd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187474"
---
# <a name="groupbox-styles-and-templates"></a><span data-ttu-id="ee4e1-102">Estilos e modelos GroupBox</span><span class="sxs-lookup"><span data-stu-id="ee4e1-102">GroupBox Styles and Templates</span></span>
<a name="introduction"></a><span data-ttu-id="ee4e1-103">Este tópico descreve os estilos e <xref:System.Windows.Controls.GroupBox> modelos para o controle.</span><span class="sxs-lookup"><span data-stu-id="ee4e1-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.GroupBox> control.</span></span> <span data-ttu-id="ee4e1-104">Você pode modificar <xref:System.Windows.Controls.ControlTemplate> o padrão para dar ao controle uma aparência única.</span><span class="sxs-lookup"><span data-stu-id="ee4e1-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="ee4e1-105">Para obter mais informações, consulte [Criar um modelo para um controle](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="ee4e1-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
<a name="groupbox_parts"></a>
## <a name="groupbox-parts"></a><span data-ttu-id="ee4e1-106">Peças de caixa de grupo</span><span class="sxs-lookup"><span data-stu-id="ee4e1-106">GroupBox Parts</span></span>  
 <span data-ttu-id="ee4e1-107">O <xref:System.Windows.Controls.GroupBox> controle não tem nenhuma parte nomeada.</span><span class="sxs-lookup"><span data-stu-id="ee4e1-107">The <xref:System.Windows.Controls.GroupBox> control does not have any named parts.</span></span>  
  
<a name="groupbox_states"></a>
## <a name="groupbox-states"></a><span data-ttu-id="ee4e1-108">Estados groupbox</span><span class="sxs-lookup"><span data-stu-id="ee4e1-108">GroupBox States</span></span>  
 <span data-ttu-id="ee4e1-109">A tabela a seguir lista <xref:System.Windows.Controls.GroupBox> os estados visuais para o controle.</span><span class="sxs-lookup"><span data-stu-id="ee4e1-109">The following table lists the visual states for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
|<span data-ttu-id="ee4e1-110">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="ee4e1-110">VisualState Name</span></span>|<span data-ttu-id="ee4e1-111">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="ee4e1-111">VisualStateGroup Name</span></span>|<span data-ttu-id="ee4e1-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="ee4e1-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="ee4e1-113">Válido</span><span class="sxs-lookup"><span data-stu-id="ee4e1-113">Valid</span></span>|<span data-ttu-id="ee4e1-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ee4e1-114">ValidationStates</span></span>|<span data-ttu-id="ee4e1-115">O controle <xref:System.Windows.Controls.Validation> usa a <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> classe e `false`a propriedade anexada é .</span><span class="sxs-lookup"><span data-stu-id="ee4e1-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="ee4e1-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="ee4e1-116">InvalidFocused</span></span>|<span data-ttu-id="ee4e1-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ee4e1-117">ValidationStates</span></span>|<span data-ttu-id="ee4e1-118">A <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada tem `true` o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="ee4e1-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="ee4e1-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="ee4e1-119">InvalidUnfocused</span></span>|<span data-ttu-id="ee4e1-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ee4e1-120">ValidationStates</span></span>|<span data-ttu-id="ee4e1-121">A <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="ee4e1-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
<a name="groupbox_controltemplate_example"></a>
## <a name="groupbox-controltemplate-example"></a><span data-ttu-id="ee4e1-122">Exemplo de modelo de controle de caixa de grupo</span><span class="sxs-lookup"><span data-stu-id="ee4e1-122">GroupBox ControlTemplate Example</span></span>  
 <span data-ttu-id="ee4e1-123">O exemplo a seguir <xref:System.Windows.Controls.ControlTemplate> mostra <xref:System.Windows.Controls.GroupBox> como definir um para o controle.</span><span class="sxs-lookup"><span data-stu-id="ee4e1-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.GroupBox> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#GroupBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/groupbox.xaml#groupbox)]  
  
 <span data-ttu-id="ee4e1-124">O <xref:System.Windows.Controls.ControlTemplate> uso de um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="ee4e1-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="ee4e1-125">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="ee4e1-125">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee4e1-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="ee4e1-126">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="ee4e1-127">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="ee4e1-127">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="ee4e1-128">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="ee4e1-128">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="ee4e1-129">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="ee4e1-129">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="ee4e1-130">Crie um modelo para um controle</span><span class="sxs-lookup"><span data-stu-id="ee4e1-130">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
