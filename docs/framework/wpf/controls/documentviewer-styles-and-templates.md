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
ms.openlocfilehash: 7ac68e8666a0de5cf683e3c4186d7805168dadb5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54581000"
---
# <a name="documentviewer-styles-and-templates"></a><span data-ttu-id="78ae9-102">Estilos e modelos DocumentViewer</span><span class="sxs-lookup"><span data-stu-id="78ae9-102">DocumentViewer Styles and Templates</span></span>
<span data-ttu-id="78ae9-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.DocumentViewer> controle.</span><span class="sxs-lookup"><span data-stu-id="78ae9-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span> <span data-ttu-id="78ae9-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para dar ao controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="78ae9-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="78ae9-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="78ae9-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="documentviewer-parts"></a><span data-ttu-id="78ae9-106">Partes de DocumentViewer</span><span class="sxs-lookup"><span data-stu-id="78ae9-106">DocumentViewer Parts</span></span>  
 <span data-ttu-id="78ae9-107">A tabela a seguir lista as partes nomeadas para o <xref:System.Windows.Controls.DocumentViewer> controle.</span><span class="sxs-lookup"><span data-stu-id="78ae9-107">The following table lists the named parts for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="78ae9-108">Parte</span><span class="sxs-lookup"><span data-stu-id="78ae9-108">Part</span></span>|<span data-ttu-id="78ae9-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="78ae9-109">Type</span></span>|<span data-ttu-id="78ae9-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="78ae9-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="78ae9-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="78ae9-111">PART_ContentHost</span></span>|<xref:System.Windows.Controls.ScrollViewer>|<span data-ttu-id="78ae9-112">O conteúdo e a área de rolagem.</span><span class="sxs-lookup"><span data-stu-id="78ae9-112">The content and scrolling area.</span></span>|  
|<span data-ttu-id="78ae9-113">PART_FindToolBarHost</span><span class="sxs-lookup"><span data-stu-id="78ae9-113">PART_FindToolBarHost</span></span>|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="78ae9-114">A caixa de pesquisa, na parte inferior por padrão.</span><span class="sxs-lookup"><span data-stu-id="78ae9-114">The search box, at the bottom by default.</span></span>|  
  
## <a name="documentviewer-states"></a><span data-ttu-id="78ae9-115">Estados de DocumentViewer</span><span class="sxs-lookup"><span data-stu-id="78ae9-115">DocumentViewer States</span></span>  
 <span data-ttu-id="78ae9-116">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.DocumentViewer> controle.</span><span class="sxs-lookup"><span data-stu-id="78ae9-116">The following table lists the visual states for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="78ae9-117">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="78ae9-117">VisualState Name</span></span>|<span data-ttu-id="78ae9-118">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="78ae9-118">VisualStateGroup Name</span></span>|<span data-ttu-id="78ae9-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="78ae9-119">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="78ae9-120">Válido</span><span class="sxs-lookup"><span data-stu-id="78ae9-120">Valid</span></span>|<span data-ttu-id="78ae9-121">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="78ae9-121">ValidationStates</span></span>|<span data-ttu-id="78ae9-122">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="78ae9-122">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="78ae9-123">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="78ae9-123">InvalidFocused</span></span>|<span data-ttu-id="78ae9-124">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="78ae9-124">ValidationStates</span></span>|<span data-ttu-id="78ae9-125">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="78ae9-125">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="78ae9-126">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="78ae9-126">InvalidUnfocused</span></span>|<span data-ttu-id="78ae9-127">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="78ae9-127">ValidationStates</span></span>|<span data-ttu-id="78ae9-128">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `true` tem o controle não tem o foco.</span><span class="sxs-lookup"><span data-stu-id="78ae9-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="documentviewer-controltemplate-example"></a><span data-ttu-id="78ae9-129">Exemplo de ControlTemplate de DocumentViewer</span><span class="sxs-lookup"><span data-stu-id="78ae9-129">DocumentViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="78ae9-130">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.DocumentViewer> controle.</span><span class="sxs-lookup"><span data-stu-id="78ae9-130">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#DocumentViewer](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/documentviewer.xaml#documentviewer)]  
  
 <span data-ttu-id="78ae9-131">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="78ae9-131">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="78ae9-132">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span><span class="sxs-lookup"><span data-stu-id="78ae9-132">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78ae9-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="78ae9-133">See also</span></span>
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="78ae9-134">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="78ae9-134">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)
- [<span data-ttu-id="78ae9-135">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="78ae9-135">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)
- [<span data-ttu-id="78ae9-136">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="78ae9-136">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [<span data-ttu-id="78ae9-137">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="78ae9-137">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
