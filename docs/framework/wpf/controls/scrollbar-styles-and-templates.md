---
title: Estilos e modelos ScrollBar
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], ScrollBar
- ControlTemplate [WPF], ScrollBar
- states [WPF], ScrollBar
- ScrollBar [WPF], styles and templates
- templates [WPF], ScrollBar
- parts [WPF], ScrollBar
ms.assetid: 066ea45a-e27d-43b0-adfe-cce6934c22f5
ms.openlocfilehash: 28b5978ad58f8978510bba9b700f6767e6c4e207
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="scrollbar-styles-and-templates"></a><span data-ttu-id="f5af5-102">Estilos e modelos ScrollBar</span><span class="sxs-lookup"><span data-stu-id="f5af5-102">ScrollBar Styles and Templates</span></span>
<span data-ttu-id="f5af5-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.Primitives.ScrollBar> controle.</span><span class="sxs-lookup"><span data-stu-id="f5af5-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span> <span data-ttu-id="f5af5-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para que o controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="f5af5-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="f5af5-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="f5af5-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="scrollbar-parts"></a><span data-ttu-id="f5af5-106">Partes de barra de rolagem</span><span class="sxs-lookup"><span data-stu-id="f5af5-106">ScrollBar Parts</span></span>  
 <span data-ttu-id="f5af5-107">A tabela a seguir lista as partes nomeadas para o <xref:System.Windows.Controls.Primitives.ScrollBar> controle.</span><span class="sxs-lookup"><span data-stu-id="f5af5-107">The following table lists the named parts for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="f5af5-108">Parte</span><span class="sxs-lookup"><span data-stu-id="f5af5-108">Part</span></span>|<span data-ttu-id="f5af5-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="f5af5-109">Type</span></span>|<span data-ttu-id="f5af5-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="f5af5-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="f5af5-111">PART_Track</span><span class="sxs-lookup"><span data-stu-id="f5af5-111">PART_Track</span></span>|<xref:System.Windows.Controls.Primitives.Track>|<span data-ttu-id="f5af5-112">O contêiner para o elemento que indica a posição do <xref:System.Windows.Controls.Primitives.ScrollBar>.</span><span class="sxs-lookup"><span data-stu-id="f5af5-112">The container for the element that indicates the position of the <xref:System.Windows.Controls.Primitives.ScrollBar>.</span></span>|  
  
## <a name="scrollbar-states"></a><span data-ttu-id="f5af5-113">Estados de barra de rolagem</span><span class="sxs-lookup"><span data-stu-id="f5af5-113">ScrollBar States</span></span>  
 <span data-ttu-id="f5af5-114">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.Primitives.ScrollBar> controle.</span><span class="sxs-lookup"><span data-stu-id="f5af5-114">The following table lists the visual states for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
|<span data-ttu-id="f5af5-115">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="f5af5-115">VisualState Name</span></span>|<span data-ttu-id="f5af5-116">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="f5af5-116">VisualStateGroup Name</span></span>|<span data-ttu-id="f5af5-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="f5af5-117">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="f5af5-118">Normal</span><span class="sxs-lookup"><span data-stu-id="f5af5-118">Normal</span></span>|<span data-ttu-id="f5af5-119">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f5af5-119">CommonStates</span></span>|<span data-ttu-id="f5af5-120">O estado padrão.</span><span class="sxs-lookup"><span data-stu-id="f5af5-120">The default state.</span></span>|  
|<span data-ttu-id="f5af5-121">MouseOver</span><span class="sxs-lookup"><span data-stu-id="f5af5-121">MouseOver</span></span>|<span data-ttu-id="f5af5-122">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f5af5-122">CommonStates</span></span>|<span data-ttu-id="f5af5-123">O ponteiro do mouse é posicionado sobre o controle.</span><span class="sxs-lookup"><span data-stu-id="f5af5-123">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="f5af5-124">Disabled</span><span class="sxs-lookup"><span data-stu-id="f5af5-124">Disabled</span></span>|<span data-ttu-id="f5af5-125">CommonStates</span><span class="sxs-lookup"><span data-stu-id="f5af5-125">CommonStates</span></span>|<span data-ttu-id="f5af5-126">O controle está desabilitado.</span><span class="sxs-lookup"><span data-stu-id="f5af5-126">The control is disabled.</span></span>|  
|<span data-ttu-id="f5af5-127">Válido</span><span class="sxs-lookup"><span data-stu-id="f5af5-127">Valid</span></span>|<span data-ttu-id="f5af5-128">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f5af5-128">ValidationStates</span></span>|<span data-ttu-id="f5af5-129">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="f5af5-129">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="f5af5-130">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="f5af5-130">InvalidFocused</span></span>|<span data-ttu-id="f5af5-131">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f5af5-131">ValidationStates</span></span>|<span data-ttu-id="f5af5-132">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="f5af5-132">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="f5af5-133">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="f5af5-133">InvalidUnfocused</span></span>|<span data-ttu-id="f5af5-134">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="f5af5-134">ValidationStates</span></span>|<span data-ttu-id="f5af5-135">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="f5af5-135">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="scrollbar-controltemplate-example"></a><span data-ttu-id="f5af5-136">Exemplo de ControlTemplate ScrollBar</span><span class="sxs-lookup"><span data-stu-id="f5af5-136">ScrollBar ControlTemplate Example</span></span>  
 <span data-ttu-id="f5af5-137">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.Primitives.ScrollBar> controle.</span><span class="sxs-lookup"><span data-stu-id="f5af5-137">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Primitives.ScrollBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#scrollbar)]  
  
 <span data-ttu-id="f5af5-138">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="f5af5-138">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="f5af5-139">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="f5af5-139">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5af5-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f5af5-140">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="f5af5-141">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="f5af5-141">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="f5af5-142">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="f5af5-142">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="f5af5-143">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="f5af5-143">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="f5af5-144">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="f5af5-144">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
