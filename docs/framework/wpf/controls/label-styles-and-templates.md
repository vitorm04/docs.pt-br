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
ms.openlocfilehash: a56b03d2b851f518dc76dd07e5d182688da7111d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="label-styles-and-templates"></a><span data-ttu-id="234fa-102">Estilos e modelos de rótulo</span><span class="sxs-lookup"><span data-stu-id="234fa-102">Label Styles and Templates</span></span>
<span data-ttu-id="234fa-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.Label> controle.</span><span class="sxs-lookup"><span data-stu-id="234fa-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Label> control.</span></span> <span data-ttu-id="234fa-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para que o controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="234fa-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="234fa-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="234fa-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="label-parts"></a><span data-ttu-id="234fa-106">Partes de rótulo</span><span class="sxs-lookup"><span data-stu-id="234fa-106">Label Parts</span></span>  
 <span data-ttu-id="234fa-107">O <xref:System.Windows.Controls.Label> controle não tem as partes nomeadas.</span><span class="sxs-lookup"><span data-stu-id="234fa-107">The <xref:System.Windows.Controls.Label> control does not have any named parts.</span></span>  
  
## <a name="label-states"></a><span data-ttu-id="234fa-108">Estados de rótulo</span><span class="sxs-lookup"><span data-stu-id="234fa-108">Label States</span></span>  
 <span data-ttu-id="234fa-109">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.Label> controle.</span><span class="sxs-lookup"><span data-stu-id="234fa-109">The following table lists the visual states for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
|<span data-ttu-id="234fa-110">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="234fa-110">VisualState Name</span></span>|<span data-ttu-id="234fa-111">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="234fa-111">VisualStateGroup Name</span></span>|<span data-ttu-id="234fa-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="234fa-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="234fa-113">Válido</span><span class="sxs-lookup"><span data-stu-id="234fa-113">Valid</span></span>|<span data-ttu-id="234fa-114">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="234fa-114">ValidationStates</span></span>|<span data-ttu-id="234fa-115">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="234fa-115">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="234fa-116">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="234fa-116">InvalidFocused</span></span>|<span data-ttu-id="234fa-117">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="234fa-117">ValidationStates</span></span>|<span data-ttu-id="234fa-118">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="234fa-118">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="234fa-119">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="234fa-119">InvalidUnfocused</span></span>|<span data-ttu-id="234fa-120">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="234fa-120">ValidationStates</span></span>|<span data-ttu-id="234fa-121">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="234fa-121">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="label-controltemplate-example"></a><span data-ttu-id="234fa-122">Exemplo de ControlTemplate de rótulo</span><span class="sxs-lookup"><span data-stu-id="234fa-122">Label ControlTemplate Example</span></span>  
 <span data-ttu-id="234fa-123">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.Label> controle.</span><span class="sxs-lookup"><span data-stu-id="234fa-123">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Label> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Label](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/label.xaml#label)]  
  
 <span data-ttu-id="234fa-124">O <xref:System.Windows.Controls.ControlTemplate> usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="234fa-124">The <xref:System.Windows.Controls.ControlTemplate> uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="234fa-125">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="234fa-125">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="234fa-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="234fa-126">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="234fa-127">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="234fa-127">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="234fa-128">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="234fa-128">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="234fa-129">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="234fa-129">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="234fa-130">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="234fa-130">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
