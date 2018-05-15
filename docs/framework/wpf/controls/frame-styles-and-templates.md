---
title: Estilos e modelos de quadro
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], Frame
- templates [WPF], Frame
- ControlTemplate [WPF], Frame
- Frame [WPF], styles and templates
- states [WPF], Frame
- styles [WPF], Frame
ms.assetid: a01c32e2-c951-46a0-a82f-2614ca241f0b
ms.openlocfilehash: ae7227aeca3680b5e10ae62637268eae7825f492
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="frame-styles-and-templates"></a><span data-ttu-id="888e8-102">Estilos e modelos de quadro</span><span class="sxs-lookup"><span data-stu-id="888e8-102">Frame Styles and Templates</span></span>
<span data-ttu-id="888e8-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.Frame> controle.</span><span class="sxs-lookup"><span data-stu-id="888e8-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Frame> control.</span></span> <span data-ttu-id="888e8-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para que o controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="888e8-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="888e8-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="888e8-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="frame-parts"></a><span data-ttu-id="888e8-106">Partes de quadro</span><span class="sxs-lookup"><span data-stu-id="888e8-106">Frame Parts</span></span>  
 <span data-ttu-id="888e8-107">A tabela a seguir lista as partes nomeadas para o <xref:System.Windows.Controls.Frame> controle.</span><span class="sxs-lookup"><span data-stu-id="888e8-107">The following table lists the named parts for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="888e8-108">Parte</span><span class="sxs-lookup"><span data-stu-id="888e8-108">Part</span></span>|<span data-ttu-id="888e8-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="888e8-109">Type</span></span>|<span data-ttu-id="888e8-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="888e8-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="888e8-111">PART_FrameCP</span><span class="sxs-lookup"><span data-stu-id="888e8-111">PART_FrameCP</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="888e8-112">A área de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="888e8-112">The content area.</span></span>|  
  
## <a name="frame-states"></a><span data-ttu-id="888e8-113">Estados de quadro</span><span class="sxs-lookup"><span data-stu-id="888e8-113">Frame States</span></span>  
 <span data-ttu-id="888e8-114">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.Frame> controle.</span><span class="sxs-lookup"><span data-stu-id="888e8-114">The following table lists the visual states for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="888e8-115">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="888e8-115">VisualState Name</span></span>|<span data-ttu-id="888e8-116">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="888e8-116">VisualStateGroup Name</span></span>|<span data-ttu-id="888e8-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="888e8-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="888e8-118">Válido</span><span class="sxs-lookup"><span data-stu-id="888e8-118">Valid</span></span>|<span data-ttu-id="888e8-119">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="888e8-119">ValidationStates</span></span>|<span data-ttu-id="888e8-120">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="888e8-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="888e8-121">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="888e8-121">InvalidFocused</span></span>|<span data-ttu-id="888e8-122">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="888e8-122">ValidationStates</span></span>|<span data-ttu-id="888e8-123">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="888e8-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="888e8-124">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="888e8-124">InvalidUnfocused</span></span>|<span data-ttu-id="888e8-125">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="888e8-125">ValidationStates</span></span>|<span data-ttu-id="888e8-126">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="888e8-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="frame-controltemplate-example"></a><span data-ttu-id="888e8-127">Exemplo de ControlTemplate Frame</span><span class="sxs-lookup"><span data-stu-id="888e8-127">Frame ControlTemplate Example</span></span>  
 <span data-ttu-id="888e8-128">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.Frame> controle.</span><span class="sxs-lookup"><span data-stu-id="888e8-128">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Frame](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/frame.xaml#frame)]  
  
 <span data-ttu-id="888e8-129">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="888e8-129">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="888e8-130">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="888e8-130">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="888e8-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="888e8-131">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="888e8-132">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="888e8-132">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="888e8-133">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="888e8-133">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="888e8-134">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="888e8-134">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="888e8-135">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="888e8-135">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
