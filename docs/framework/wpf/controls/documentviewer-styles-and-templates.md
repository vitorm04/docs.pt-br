---
title: Estilos e modelos DocumentViewer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- templates [WPF], DocumentViewer
- DocumentViewer [WPF], styles and templates
- states [WPF], DocumentViewer
- ControlTemplate [WPF], DocumentViewer
- parts [WPF], DocumentViewer
- styles [WPF], DocumentViewer
ms.assetid: 6bd4ff8f-ea6a-4084-ac58-e7a67446ce1c
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 33631b0a63b69f848cb3f09b4dcb617fb328b06c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="documentviewer-styles-and-templates"></a><span data-ttu-id="a29a0-102">Estilos e modelos DocumentViewer</span><span class="sxs-lookup"><span data-stu-id="a29a0-102">DocumentViewer Styles and Templates</span></span>
<span data-ttu-id="a29a0-103">Este tópico descreve os estilos e modelos para o <xref:System.Windows.Controls.DocumentViewer> controle.</span><span class="sxs-lookup"><span data-stu-id="a29a0-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span> <span data-ttu-id="a29a0-104">Você pode modificar o padrão <xref:System.Windows.Controls.ControlTemplate> para que o controle uma aparência exclusiva.</span><span class="sxs-lookup"><span data-stu-id="a29a0-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="a29a0-105">Para obter mais informações, consulte [Personalizando a aparência de um controle existente criando um ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="a29a0-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="documentviewer-parts"></a><span data-ttu-id="a29a0-106">Partes do Visualizador de documentos</span><span class="sxs-lookup"><span data-stu-id="a29a0-106">DocumentViewer Parts</span></span>  
 <span data-ttu-id="a29a0-107">A tabela a seguir lista as partes nomeadas para o <xref:System.Windows.Controls.DocumentViewer> controle.</span><span class="sxs-lookup"><span data-stu-id="a29a0-107">The following table lists the named parts for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="a29a0-108">Parte</span><span class="sxs-lookup"><span data-stu-id="a29a0-108">Part</span></span>|<span data-ttu-id="a29a0-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="a29a0-109">Type</span></span>|<span data-ttu-id="a29a0-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="a29a0-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="a29a0-111">PART_ContentHost</span><span class="sxs-lookup"><span data-stu-id="a29a0-111">PART_ContentHost</span></span>|<xref:System.Windows.Controls.ScrollViewer>|<span data-ttu-id="a29a0-112">O conteúdo e a área de rolagem.</span><span class="sxs-lookup"><span data-stu-id="a29a0-112">The content and scrolling area.</span></span>|  
|<span data-ttu-id="a29a0-113">PART_FindToolBarHost</span><span class="sxs-lookup"><span data-stu-id="a29a0-113">PART_FindToolBarHost</span></span>|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="a29a0-114">A caixa de pesquisa, na parte inferior por padrão.</span><span class="sxs-lookup"><span data-stu-id="a29a0-114">The search box, at the bottom by default.</span></span>|  
  
## <a name="documentviewer-states"></a><span data-ttu-id="a29a0-115">Estados de DocumentViewer</span><span class="sxs-lookup"><span data-stu-id="a29a0-115">DocumentViewer States</span></span>  
 <span data-ttu-id="a29a0-116">A tabela a seguir lista os estados visuais para o <xref:System.Windows.Controls.DocumentViewer> controle.</span><span class="sxs-lookup"><span data-stu-id="a29a0-116">The following table lists the visual states for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
|<span data-ttu-id="a29a0-117">Nome do VisualState</span><span class="sxs-lookup"><span data-stu-id="a29a0-117">VisualState Name</span></span>|<span data-ttu-id="a29a0-118">Nome do VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="a29a0-118">VisualStateGroup Name</span></span>|<span data-ttu-id="a29a0-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="a29a0-119">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="a29a0-120">Válido</span><span class="sxs-lookup"><span data-stu-id="a29a0-120">Valid</span></span>|<span data-ttu-id="a29a0-121">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a29a0-121">ValidationStates</span></span>|<span data-ttu-id="a29a0-122">O controle usa o <xref:System.Windows.Controls.Validation> classe e o <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> propriedade anexada é `false`.</span><span class="sxs-lookup"><span data-stu-id="a29a0-122">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="a29a0-123">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="a29a0-123">InvalidFocused</span></span>|<span data-ttu-id="a29a0-124">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a29a0-124">ValidationStates</span></span>|<span data-ttu-id="a29a0-125">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle tem foco.</span><span class="sxs-lookup"><span data-stu-id="a29a0-125">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="a29a0-126">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="a29a0-126">InvalidUnfocused</span></span>|<span data-ttu-id="a29a0-127">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="a29a0-127">ValidationStates</span></span>|<span data-ttu-id="a29a0-128">O <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> é de propriedade anexada `true` tem o controle não tem foco.</span><span class="sxs-lookup"><span data-stu-id="a29a0-128">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="documentviewer-controltemplate-example"></a><span data-ttu-id="a29a0-129">Exemplo de ControlTemplate de DocumentViewer</span><span class="sxs-lookup"><span data-stu-id="a29a0-129">DocumentViewer ControlTemplate Example</span></span>  
 <span data-ttu-id="a29a0-130">O exemplo a seguir mostra como definir um <xref:System.Windows.Controls.ControlTemplate> para o <xref:System.Windows.Controls.DocumentViewer> controle.</span><span class="sxs-lookup"><span data-stu-id="a29a0-130">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.DocumentViewer> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#DocumentViewer](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/documentviewer.xaml#documentviewer)]  
  
 <span data-ttu-id="a29a0-131">O exemplo anterior usa um ou mais dos seguintes recursos.</span><span class="sxs-lookup"><span data-stu-id="a29a0-131">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="a29a0-132">Para ver o exemplo completo, consulte [Styling with ControlTemplates Sample (Estilos com a amostra ControlTemplates)](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="a29a0-132">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a29a0-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a29a0-133">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="a29a0-134">Estilos e modelos de controle</span><span class="sxs-lookup"><span data-stu-id="a29a0-134">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="a29a0-135">Personalização do controle</span><span class="sxs-lookup"><span data-stu-id="a29a0-135">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="a29a0-136">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="a29a0-136">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="a29a0-137">Personalizando a aparência de um controle existente criando um ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="a29a0-137">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
