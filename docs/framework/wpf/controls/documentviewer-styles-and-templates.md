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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61911762"
---
# <a name="documentviewer-styles-and-templates"></a><span data-ttu-id="04efe-102">Estilos e modelos DocumentViewer</span><span class="sxs-lookup"><span data-stu-id="04efe-102">DocumentViewer Styles and Templates</span></span>
<span data-ttu-id="04efe-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.DocumentViewer> controle.</span><span class="sxs-lookup"><span data-stu-id="04efe-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span> <span data-ttu-id="04efe-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="04efe-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="04efe-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="04efe-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="documentviewer-parts"></a><span data-ttu-id="04efe-106">Partes de DocumentViewer</span><span class="sxs-lookup"><span data-stu-id="04efe-106">DocumentViewer Parts</span></span>  
 <span data-ttu-id="04efe-107">A tabela a seguir lista as partes nomeadas para o <xref:System.Windows.Controls.DocumentViewer> controle.</span><span class="sxs-lookup"><span data-stu-id="04efe-107">The following table lists the named parts for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="04efe-108">Parte</span><span class="sxs-lookup"><span data-stu-id="04efe-108">Part</span></span>|<span data-ttu-id="04efe-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="04efe-109">Type</span></span>|<span data-ttu-id="04efe-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="04efe-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="04efe-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="04efe-111">PART_ContentHost</span></span>|<xref:System.Windows.Controls.ScrollViewer>|<span data-ttu-id="04efe-112">O conteúdo e a área de rolagem.</span><span class="sxs-lookup"><span data-stu-id="04efe-112">The content and scrolling area.</span></span>|  
|<span data-ttu-id="04efe-113">PART_FindToolBarHost</span><span class="sxs-lookup"><span data-stu-id="04efe-113">PART_FindToolBarHost</span></span>|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="04efe-114">A caixa de pesquisa, na parte inferior por padrão.</span><span class="sxs-lookup"><span data-stu-id="04efe-114">The search box, at the bottom by default.</span></span>|  
  
## <a name="documentviewer-states"></a><span data-ttu-id="04efe-115">Estados de DocumentViewer</span><span class="sxs-lookup"><span data-stu-id="04efe-115">DocumentViewer States</span></span>  
 <span data-ttu-id="04efe-116">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.DocumentViewer> controle.</span><span class="sxs-lookup"><span data-stu-id="04efe-116">The following table lists the visual states for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="04efe-117">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="04efe-117">VisualState Name</span></span>|<span data-ttu-id="04efe-118">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="04efe-118">VisualStateGroup Name</span></span>|<span data-ttu-id="04efe-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="04efe-119">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="04efe-120">Válido</span><span class="sxs-lookup"><span data-stu-id="04efe-120">Valid</span></span>|<span data-ttu-id="04efe-121">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="04efe-121">ValidationStates</span></span>|<span data-ttu-id="04efe-122">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="04efe-122">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="04efe-123">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="04efe-123">InvalidFocused</span></span>|<span data-ttu-id="04efe-124">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="04efe-124">ValidationStates</span></span>|<span data-ttu-id="04efe-125">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="04efe-125">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="04efe-126">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="04efe-126">InvalidUnfocused</span></span>|<span data-ttu-id="04efe-127">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="04efe-127">ValidationStates</span></span>|<span data-ttu-id="04efe-128">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle não tem o foco.</span><span class="sxs-lookup"><span data-stu-id="04efe-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="documentviewer-controltemplate-example"></a><span data-ttu-id="04efe-129">Exemplo de ControlTemplate de DocumentViewer</span><span class="sxs-lookup"><span data-stu-id="04efe-129">DocumentViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="04efe-130">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.DocumentViewer> controle.</span><span class="sxs-lookup"><span data-stu-id="04efe-130">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#DocumentViewer](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/documentviewer.xaml#documentviewer)]  
  
 <span data-ttu-id="04efe-131">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="04efe-131">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="04efe-132">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="04efe-132">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04efe-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="04efe-133">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="04efe-134">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="04efe-134">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="04efe-135">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="04efe-135">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="04efe-136">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="04efe-136">Styling and Templating</span></span>](styling-and-templating.md)
- [<span data-ttu-id="04efe-137">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="04efe-137">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](customizing-the-appearance-of-an-existing-control.md)
