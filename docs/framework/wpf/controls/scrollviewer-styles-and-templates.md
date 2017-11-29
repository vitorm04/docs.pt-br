---
title: Estilos e modelos ScrollViewer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parts [WPF], ScrollViewer
- states [WPF], ScrollViewer
- styles [WPF], ScrollViewer
- templates [WPF], ScrollViewer
- ControlTemplate [WPF], ScrollViewer
- ScrollViewer [WPF], styles and templates
ms.assetid: dffdd822-ae69-4946-abaf-710860cd65b2
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ac02896708744bc9b1c2d017da4e6f56ac32b53a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="scrollviewer-styles-and-templates"></a><span data-ttu-id="06aac-102">Estilos e modelos ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="06aac-102">ScrollViewer Styles and Templates</span></span>
<span data-ttu-id="06aac-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.ScrollViewer> controle.</span><span class="sxs-lookup"><span data-stu-id="06aac-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span> <span data-ttu-id="06aac-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para que o controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="06aac-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="06aac-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="06aac-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="scrollviewer-parts"></a><span data-ttu-id="06aac-106">Partes de ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="06aac-106">ScrollViewer Parts</span></span>  
 <span data-ttu-id="06aac-107">A tabela a seguir lista as partes nomeadas para o <xref:System.Windows.Controls.ScrollViewer> controle.</span><span class="sxs-lookup"><span data-stu-id="06aac-107">The following table lists the named parts for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="06aac-108">Parte</span><span class="sxs-lookup"><span data-stu-id="06aac-108">Part</span></span>|<span data-ttu-id="06aac-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="06aac-109">Type</span></span>|<span data-ttu-id="06aac-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="06aac-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="06aac-111">PART_ScrollContentPresenter</span><span class="sxs-lookup"><span data-stu-id="06aac-111">PART_ScrollContentPresenter</span></span>|<xref:System.Windows.Controls.ScrollContentPresenter>|<span data-ttu-id="06aac-112">O espaço reservado para o conteúdo a <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="06aac-112">The placeholder for content in the <xref:System.Windows.Controls.ScrollViewer>.</span></span>|  
|<span data-ttu-id="06aac-113">PART_HorizontalScrollBar</span><span class="sxs-lookup"><span data-stu-id="06aac-113">PART_HorizontalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="06aac-114">O <xref:System.Windows.Controls.Primitives.ScrollBar> usado para rolar o conteúdo horizontalmente.</span><span class="sxs-lookup"><span data-stu-id="06aac-114">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content horizontally.</span></span>|  
|<span data-ttu-id="06aac-115">PART_VerticalScrollBar</span><span class="sxs-lookup"><span data-stu-id="06aac-115">PART_VerticalScrollBar</span></span>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="06aac-116">O <xref:System.Windows.Controls.Primitives.ScrollBar> usado para rolar o conteúdo verticalmente.</span><span class="sxs-lookup"><span data-stu-id="06aac-116">The <xref:System.Windows.Controls.Primitives.ScrollBar> used to scroll the content vertically.</span></span>|  
  
## <a name="scrollviewer-states"></a><span data-ttu-id="06aac-117">Estados de ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="06aac-117">ScrollViewer States</span></span>  
 <span data-ttu-id="06aac-118">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.ScrollViewer> controle.</span><span class="sxs-lookup"><span data-stu-id="06aac-118">The following table lists the visual states for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
|<span data-ttu-id="06aac-119">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="06aac-119">VisualState Name</span></span>|<span data-ttu-id="06aac-120">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="06aac-120">VisualStateGroup Name</span></span>|<span data-ttu-id="06aac-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="06aac-121">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="06aac-122">Válido</span><span class="sxs-lookup"><span data-stu-id="06aac-122">Valid</span></span>|<span data-ttu-id="06aac-123">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="06aac-123">ValidationStates</span></span>|<span data-ttu-id="06aac-124">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="06aac-124">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="06aac-125">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="06aac-125">InvalidFocused</span></span>|<span data-ttu-id="06aac-126">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="06aac-126">ValidationStates</span></span>|<span data-ttu-id="06aac-127">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="06aac-127">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="06aac-128">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="06aac-128">InvalidUnfocused</span></span>|<span data-ttu-id="06aac-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="06aac-129">ValidationStates</span></span>|<span data-ttu-id="06aac-130">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="06aac-130">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="scrollviewer-controltemplate-example"></a><span data-ttu-id="06aac-131">Exemplo de ControlTemplate de ScrollViewer</span><span class="sxs-lookup"><span data-stu-id="06aac-131">ScrollViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="06aac-132">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.ScrollViewer> controle.</span><span class="sxs-lookup"><span data-stu-id="06aac-132">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ScrollViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ScrollViewer](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollviewer.xaml#scrollviewer)]  
  
 <span data-ttu-id="06aac-133">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="06aac-133">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="06aac-134">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="06aac-134">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06aac-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="06aac-135">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="06aac-136">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="06aac-136">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="06aac-137">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="06aac-137">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="06aac-138">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="06aac-138">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="06aac-139">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="06aac-139">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
