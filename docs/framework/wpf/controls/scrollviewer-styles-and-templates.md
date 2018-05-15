---
title: Estilos e modelos ScrollViewer
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], ScrollViewer
- states [WPF], ScrollViewer
- styles [WPF], ScrollViewer
- templates [WPF], ScrollViewer
- ControlTemplate [WPF], ScrollViewer
- ScrollViewer [WPF], styles and templates
ms.assetid: dffdd822-ae69-4946-abaf-710860cd65b2
ms.openlocfilehash: 2182390b47508833b8535864f2d670c194d66088
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="scrollviewer-styles-and-templates"></a><span data-ttu-id="7787a-102">Estilos e modelos ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="7787a-102">ScrollViewer Styles and Templates</span></span>
<span data-ttu-id="7787a-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.ScrollViewer> controle.</span><span class="sxs-lookup"><span data-stu-id="7787a-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span> <span data-ttu-id="7787a-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para que o controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="7787a-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="7787a-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="7787a-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="scrollviewer-parts"></a><span data-ttu-id="7787a-106">Partes de ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="7787a-106">ScrollViewer Parts</span></span>  
 <span data-ttu-id="7787a-107">A tabela a seguir lista as partes nomeadas para o <xref:System.Windows.Controls.ScrollViewer> controle.</span><span class="sxs-lookup"><span data-stu-id="7787a-107">The following table lists the named parts for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="7787a-108">Parte</span><span class="sxs-lookup"><span data-stu-id="7787a-108">Part</span></span>|<span data-ttu-id="7787a-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="7787a-109">Type</span></span>|<span data-ttu-id="7787a-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="7787a-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="7787a-111">PART_ScrollContentPresenter</span><span class="sxs-lookup"><span data-stu-id="7787a-111">PART_ScrollContentPresenter</span></span>|<xref:System.Windows.Controls.ScrollContentPresenter>|<span data-ttu-id="7787a-112">O espaço reservado para o conteúdo a <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="7787a-112">The placeholder for content in the <xref:System.Windows.Controls.ScrollViewer>.</span></span>|  
|<span data-ttu-id="7787a-113">PART_HorizontalScrollBar</span><span class="sxs-lookup"><span data-stu-id="7787a-113">PART_HorizontalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="7787a-114">O <xref:System.Windows.Controls.Primitives.ScrollBar> usado para rolar o conteúdo horizontalmente.</span><span class="sxs-lookup"><span data-stu-id="7787a-114">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content horizontally.</span></span>|  
|<span data-ttu-id="7787a-115">PART_VerticalScrollBar</span><span class="sxs-lookup"><span data-stu-id="7787a-115">PART_VerticalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="7787a-116">O <xref:System.Windows.Controls.Primitives.ScrollBar> usado para rolar o conteúdo verticalmente.</span><span class="sxs-lookup"><span data-stu-id="7787a-116">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content vertically.</span></span>|  
  
## <a name="scrollviewer-states"></a><span data-ttu-id="7787a-117">Estados de ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="7787a-117">ScrollViewer States</span></span>  
 <span data-ttu-id="7787a-118">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.ScrollViewer> controle.</span><span class="sxs-lookup"><span data-stu-id="7787a-118">The following table lists the visual states for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="7787a-119">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="7787a-119">VisualState Name</span></span>|<span data-ttu-id="7787a-120">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="7787a-120">VisualStateGroup Name</span></span>|<span data-ttu-id="7787a-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="7787a-121">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="7787a-122">Válido</span><span class="sxs-lookup"><span data-stu-id="7787a-122">Valid</span></span>|<span data-ttu-id="7787a-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7787a-123">ValidationStates</span></span>|<span data-ttu-id="7787a-124">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="7787a-124">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="7787a-125">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="7787a-125">InvalidFocused</span></span>|<span data-ttu-id="7787a-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7787a-126">ValidationStates</span></span>|<span data-ttu-id="7787a-127">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="7787a-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="7787a-128">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="7787a-128">InvalidUnfocused</span></span>|<span data-ttu-id="7787a-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="7787a-129">ValidationStates</span></span>|<span data-ttu-id="7787a-130">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="7787a-130">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="scrollviewer-controltemplate-example"></a><span data-ttu-id="7787a-131">Exemplo de ControlTemplate de ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="7787a-131">ScrollViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="7787a-132">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.ScrollViewer> controle.</span><span class="sxs-lookup"><span data-stu-id="7787a-132">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollViewer](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollviewer.xaml#scrollviewer)]  
  
 <span data-ttu-id="7787a-133">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="7787a-133">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="7787a-134">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="7787a-134">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7787a-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7787a-135">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="7787a-136">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="7787a-136">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="7787a-137">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="7787a-137">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="7787a-138">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="7787a-138">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="7787a-139">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="7787a-139">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
