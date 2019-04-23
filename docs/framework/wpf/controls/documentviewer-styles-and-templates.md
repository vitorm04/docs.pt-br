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
ms.openlocfilehash: 4e91a640b36e4793567c9e728fd71ec8ce596743
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59158412"
---
# <a name="documentviewer-styles-and-templates"></a><span data-ttu-id="ac154-102">Estilos e modelos DocumentViewer</span><span class="sxs-lookup"><span data-stu-id="ac154-102">DocumentViewer Styles and Templates</span></span>
<span data-ttu-id="ac154-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.DocumentViewer> controle.</span><span class="sxs-lookup"><span data-stu-id="ac154-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span> <span data-ttu-id="ac154-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="ac154-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="ac154-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="ac154-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="documentviewer-parts"></a><span data-ttu-id="ac154-106">Partes de DocumentViewer</span><span class="sxs-lookup"><span data-stu-id="ac154-106">DocumentViewer Parts</span></span>  
 <span data-ttu-id="ac154-107">A tabela a seguir lista as partes nomeadas para o <xref:System.Windows.Controls.DocumentViewer> controle.</span><span class="sxs-lookup"><span data-stu-id="ac154-107">The following table lists the named parts for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="ac154-108">Parte</span><span class="sxs-lookup"><span data-stu-id="ac154-108">Part</span></span>|<span data-ttu-id="ac154-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="ac154-109">Type</span></span>|<span data-ttu-id="ac154-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="ac154-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="ac154-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="ac154-111">PART_ContentHost</span></span>|<xref:System.Windows.Controls.ScrollViewer>|<span data-ttu-id="ac154-112">O conteúdo e a área de rolagem.</span><span class="sxs-lookup"><span data-stu-id="ac154-112">The content and scrolling area.</span></span>|  
|<span data-ttu-id="ac154-113">PART_FindToolBarHost</span><span class="sxs-lookup"><span data-stu-id="ac154-113">PART_FindToolBarHost</span></span>|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="ac154-114">A caixa de pesquisa, na parte inferior por padrão.</span><span class="sxs-lookup"><span data-stu-id="ac154-114">The search box, at the bottom by default.</span></span>|  
  
## <a name="documentviewer-states"></a><span data-ttu-id="ac154-115">Estados de DocumentViewer</span><span class="sxs-lookup"><span data-stu-id="ac154-115">DocumentViewer States</span></span>  
 <span data-ttu-id="ac154-116">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.DocumentViewer> controle.</span><span class="sxs-lookup"><span data-stu-id="ac154-116">The following table lists the visual states for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="ac154-117">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="ac154-117">VisualState Name</span></span>|<span data-ttu-id="ac154-118">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="ac154-118">VisualStateGroup Name</span></span>|<span data-ttu-id="ac154-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="ac154-119">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="ac154-120">Válido</span><span class="sxs-lookup"><span data-stu-id="ac154-120">Valid</span></span>|<span data-ttu-id="ac154-121">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ac154-121">ValidationStates</span></span>|<span data-ttu-id="ac154-122">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="ac154-122">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="ac154-123">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="ac154-123">InvalidFocused</span></span>|<span data-ttu-id="ac154-124">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ac154-124">ValidationStates</span></span>|<span data-ttu-id="ac154-125">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="ac154-125">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="ac154-126">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="ac154-126">InvalidUnfocused</span></span>|<span data-ttu-id="ac154-127">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="ac154-127">ValidationStates</span></span>|<span data-ttu-id="ac154-128">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle não tem o foco.</span><span class="sxs-lookup"><span data-stu-id="ac154-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="documentviewer-controltemplate-example"></a><span data-ttu-id="ac154-129">Exemplo de ControlTemplate de DocumentViewer</span><span class="sxs-lookup"><span data-stu-id="ac154-129">DocumentViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="ac154-130">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.DocumentViewer> controle.</span><span class="sxs-lookup"><span data-stu-id="ac154-130">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#DocumentViewer](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/documentviewer.xaml#documentviewer)]  
  
 <span data-ttu-id="ac154-131">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="ac154-131">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="ac154-132">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="ac154-132">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac154-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ac154-133">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="ac154-134">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="ac154-134">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="ac154-135">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="ac154-135">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="ac154-136">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="ac154-136">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="ac154-137">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="ac154-137">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
