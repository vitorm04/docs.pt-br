---
title: Estilos e modelos DocumentViewer
ms.date: 03/30/2017
helpviewer_keywords:
- templates [WPF], DocumentViewer
- DocumentViewer [WPF], styles and templates
- states [WPF], DocumentViewer
- ControlTemplate [WPF], DocumentViewer
- parts [WPF], DocumentViewer
- styles [WPF], DocumentViewer
ms.assetid: 6bd4ff8f-ea6a-4084-ac58-e7a67446ce1c
ms.openlocfilehash: ac1dc4f74a8e8f3ad2e84c6d50239ec827306c28
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283525"
---
# <a name="documentviewer-styles-and-templates"></a><span data-ttu-id="454fe-102">Estilos e modelos DocumentViewer</span><span class="sxs-lookup"><span data-stu-id="454fe-102">DocumentViewer Styles and Templates</span></span>
<span data-ttu-id="454fe-103">Este tópico descreve os estilos e modelos para o controle de <xref:System.Windows.Controls.DocumentViewer>.</span><span class="sxs-lookup"><span data-stu-id="454fe-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span> <span data-ttu-id="454fe-104">Você pode modificar o <xref:System.Windows.Controls.ControlTemplate> padrão para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="454fe-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="454fe-105">Para obter mais informações, consulte [criar um modelo para um controle](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span><span class="sxs-lookup"><span data-stu-id="454fe-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="documentviewer-parts"></a><span data-ttu-id="454fe-106">Partes do DocumentViewer</span><span class="sxs-lookup"><span data-stu-id="454fe-106">DocumentViewer Parts</span></span>  
 <span data-ttu-id="454fe-107">A tabela a seguir lista as partes nomeadas para o controle de <xref:System.Windows.Controls.DocumentViewer>.</span><span class="sxs-lookup"><span data-stu-id="454fe-107">The following table lists the named parts for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="454fe-108">Parte</span><span class="sxs-lookup"><span data-stu-id="454fe-108">Part</span></span>|<span data-ttu-id="454fe-109">Digite</span><span class="sxs-lookup"><span data-stu-id="454fe-109">Type</span></span>|<span data-ttu-id="454fe-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="454fe-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="454fe-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="454fe-111">PART_ContentHost</span></span>|<xref:System.Windows.Controls.ScrollViewer>|<span data-ttu-id="454fe-112">O conteúdo e a área de rolagem.</span><span class="sxs-lookup"><span data-stu-id="454fe-112">The content and scrolling area.</span></span>|  
|<span data-ttu-id="454fe-113">PART_FindToolBarHost</span><span class="sxs-lookup"><span data-stu-id="454fe-113">PART_FindToolBarHost</span></span>|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="454fe-114">A caixa de pesquisa, na parte inferior, por padrão.</span><span class="sxs-lookup"><span data-stu-id="454fe-114">The search box, at the bottom by default.</span></span>|  
  
## <a name="documentviewer-states"></a><span data-ttu-id="454fe-115">Estados do DocumentViewer</span><span class="sxs-lookup"><span data-stu-id="454fe-115">DocumentViewer States</span></span>  
 <span data-ttu-id="454fe-116">A tabela a seguir lista os Estados visuais para o controle de <xref:System.Windows.Controls.DocumentViewer>.</span><span class="sxs-lookup"><span data-stu-id="454fe-116">The following table lists the visual states for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="454fe-117">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="454fe-117">VisualState Name</span></span>|<span data-ttu-id="454fe-118">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="454fe-118">VisualStateGroup Name</span></span>|<span data-ttu-id="454fe-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="454fe-119">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="454fe-120">Válido</span><span class="sxs-lookup"><span data-stu-id="454fe-120">Valid</span></span>|<span data-ttu-id="454fe-121">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="454fe-121">ValidationStates</span></span>|<span data-ttu-id="454fe-122">O controle usa a classe <xref:System.Windows.Controls.Validation> e a propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `false`.</span><span class="sxs-lookup"><span data-stu-id="454fe-122">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="454fe-123">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="454fe-123">InvalidFocused</span></span>|<span data-ttu-id="454fe-124">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="454fe-124">ValidationStates</span></span>|<span data-ttu-id="454fe-125">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle em foco.</span><span class="sxs-lookup"><span data-stu-id="454fe-125">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="454fe-126">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="454fe-126">InvalidUnfocused</span></span>|<span data-ttu-id="454fe-127">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="454fe-127">ValidationStates</span></span>|<span data-ttu-id="454fe-128">A propriedade anexada <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="454fe-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="documentviewer-controltemplate-example"></a><span data-ttu-id="454fe-129">Exemplo de ControlTemplate de DocumentViewer</span><span class="sxs-lookup"><span data-stu-id="454fe-129">DocumentViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="454fe-130">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o controle de <xref:System.Windows.Controls.DocumentViewer>.</span><span class="sxs-lookup"><span data-stu-id="454fe-130">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#DocumentViewer](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/documentviewer.xaml#documentviewer)]  
  
 <span data-ttu-id="454fe-131">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="454fe-131">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="454fe-132">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="454fe-132">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="454fe-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="454fe-133">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="454fe-134">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="454fe-134">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="454fe-135">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="454fe-135">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="454fe-136">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="454fe-136">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="454fe-137">Criar um modelo para um controle</span><span class="sxs-lookup"><span data-stu-id="454fe-137">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
