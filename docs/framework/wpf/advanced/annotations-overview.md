---
title: "Visão geral de anotações"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- highlights [WPF]
- documents [WPF], annotations
- sticky notes [WPF]
ms.assetid: 716bf474-29bd-4c74-84a4-8e0744bdad62
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7cc7b09211bc9168bbab85105a0574dc142542ba
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="annotations-overview"></a><span data-ttu-id="4d42a-102">Visão geral de anotações</span><span class="sxs-lookup"><span data-stu-id="4d42a-102">Annotations Overview</span></span>
<span data-ttu-id="4d42a-103">Escrever anotações ou comentários em documentos em papel é uma atividade tão comum que quase não valorizamos.</span><span class="sxs-lookup"><span data-stu-id="4d42a-103">Writing notes or comments on paper documents is such a commonplace activity that we almost take it for granted.</span></span> <span data-ttu-id="4d42a-104">Essas anotações ou comentários são "anotações" que adicionamos a um documento para sinalizar informações ou realçar itens de interesse para referência posterior.</span><span class="sxs-lookup"><span data-stu-id="4d42a-104">These notes or comments are "annotations" that we add to a document to flag information or to highlight items of interest for later reference.</span></span> <span data-ttu-id="4d42a-105">Embora gravar anotações em documentos impressos seja fácil e um lugar comum, a capacidade de adicionar comentários pessoais aos documentos eletrônicos normalmente é muito limitada, quando sequer está disponível.</span><span class="sxs-lookup"><span data-stu-id="4d42a-105">Although writing notes on printed documents is easy and commonplace, the ability to add personal comments to electronic documents is typically very limited, if available at all.</span></span>  
  
 <span data-ttu-id="4d42a-106">Este tópico examina vários tipos comuns de anotações, especificamente notas autoadesivas e realces e ilustra como o [!INCLUDE[TLA#tla_caf](../../../../includes/tlasharptla-caf-md.md)] facilita esses tipos de anotações em aplicativos por meio de controles de exibição de documento [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4d42a-106">This topic reviews several common types of annotations, specifically sticky notes and highlights, and illustrates how the [!INCLUDE[TLA#tla_caf](../../../../includes/tlasharptla-caf-md.md)] facilitates these types of annotations in applications through the [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] document viewing controls.</span></span>  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<span data-ttu-id="4d42a-107">controles de visualização de documento que oferecem suporte a anotações incluem <xref:System.Windows.Controls.FlowDocumentReader> e <xref:System.Windows.Controls.FlowDocumentScrollViewer>, bem como controles derivados de <xref:System.Windows.Controls.Primitives.DocumentViewerBase> como <xref:System.Windows.Controls.DocumentViewer> e <xref:System.Windows.Controls.FlowDocumentPageViewer>.</span><span class="sxs-lookup"><span data-stu-id="4d42a-107"> document viewing controls that support annotations include <xref:System.Windows.Controls.FlowDocumentReader> and <xref:System.Windows.Controls.FlowDocumentScrollViewer>, as well as controls derived from <xref:System.Windows.Controls.Primitives.DocumentViewerBase> such as <xref:System.Windows.Controls.DocumentViewer> and <xref:System.Windows.Controls.FlowDocumentPageViewer>.</span></span>  
  
  
<a name="caf1_type_stickynotes"></a>   
## <a name="sticky-notes"></a><span data-ttu-id="4d42a-108">Notas autoadesivas</span><span class="sxs-lookup"><span data-stu-id="4d42a-108">Sticky Notes</span></span>  
 <span data-ttu-id="4d42a-109">Uma nota autoadesiva típica contém informações gravadas em um pequeno pedaço de papel colorido que é então "colado" a um documento.</span><span class="sxs-lookup"><span data-stu-id="4d42a-109">A typical sticky note contains information written on a small piece of colored paper that is then "stuck" to a document.</span></span> <span data-ttu-id="4d42a-110">Notas Autoadesivas digitais fornecem funcionalidade semelhante para documentos eletrônicos, mas com a flexibilidade adicional de incluir muitos outros tipos de conteúdo, como texto digitado, anotações manuscritas (por exemplo, [!INCLUDE[TLA#tla_tpc](../../../../includes/tlasharptla-tpc-md.md)] traços de "tinta") ou links da Web.</span><span class="sxs-lookup"><span data-stu-id="4d42a-110">Digital sticky notes provide similar functionality for electronic documents, but with the added flexibility to include many other types of content such as typed text, handwritten notes (for example, [!INCLUDE[TLA#tla_tpc](../../../../includes/tlasharptla-tpc-md.md)] "ink" strokes), or Web links.</span></span>  
  
 <span data-ttu-id="4d42a-111">A ilustração a seguir mostra alguns exemplos de realce, nota autoadesiva de texto e anotações em nota autoadesivas de tinta.</span><span class="sxs-lookup"><span data-stu-id="4d42a-111">The following illustration shows some examples of highlight, text sticky note, and ink sticky note annotations.</span></span>  
  
 <span data-ttu-id="4d42a-112">![Anotações em notas autoadesivas de tinta, texto e realce.] (../../../../docs/framework/wpf/advanced/media/caf-stickynote.jpg "CAF_StickyNote")</span><span class="sxs-lookup"><span data-stu-id="4d42a-112">![Highlight, text and ink sticky note annotations.](../../../../docs/framework/wpf/advanced/media/caf-stickynote.jpg "CAF_StickyNote")</span></span>  
  
 <span data-ttu-id="4d42a-113">O exemplo a seguir mostra o método que você pode usar para habilitar o suporte a anotação em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4d42a-113">The following example shows the method that you can use to enable annotation support in your application.</span></span>  
  
 [!code-csharp[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXml/CSharp/Window1.xaml.cs#docviewxmlstartannotations)]
 [!code-vb[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DocViewerAnnotationsXml/visualbasic/window1.xaml.vb#docviewxmlstartannotations)]  
  
<a name="caf1_type_callouts"></a>   
## <a name="highlights"></a><span data-ttu-id="4d42a-114">Destaques</span><span class="sxs-lookup"><span data-stu-id="4d42a-114">Highlights</span></span>  
 <span data-ttu-id="4d42a-115">As pessoas usam métodos criativos para chamar a atenção para itens de interesse quando marcam um documento em papel, como sublinhar, realçar, circular palavras em uma frase ou desenhar de marcas ou anotações nas margens.</span><span class="sxs-lookup"><span data-stu-id="4d42a-115">People use creative methods to draw attention to items of interest when they mark up a paper document, such as underlining, highlighting, circling words in a sentence, or drawing marks or notations in the margin.</span></span>  <span data-ttu-id="4d42a-116">Anotações de realce no [!INCLUDE[TLA#tla_caf](../../../../includes/tlasharptla-caf-md.md)] fornecem um recurso semelhante para marcação de informações exibidas em controles de exibição de documento [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4d42a-116">Highlight annotations in [!INCLUDE[TLA#tla_caf](../../../../includes/tlasharptla-caf-md.md)] provide a similar feature for marking up information displayed in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] document viewing controls.</span></span>  
  
 <span data-ttu-id="4d42a-117">A ilustração a seguir mostra um exemplo de uma anotação de realce.</span><span class="sxs-lookup"><span data-stu-id="4d42a-117">The following illustration shows an example of a highlight annotation.</span></span>  
  
 <span data-ttu-id="4d42a-118">![Realçar anotação](../../../../docs/framework/wpf/advanced/media/caf-callouts.png "CAF_Callouts")</span><span class="sxs-lookup"><span data-stu-id="4d42a-118">![Highlight Annotation](../../../../docs/framework/wpf/advanced/media/caf-callouts.png "CAF_Callouts")</span></span>  
  
 <span data-ttu-id="4d42a-119">Os usuários geralmente criam anotações selecionando primeiro um texto ou um item de interesse e, em seguida, clicando duas vezes para exibir um <xref:System.Windows.Controls.ContextMenu> das opções de anotação.</span><span class="sxs-lookup"><span data-stu-id="4d42a-119">Users typically create annotations by first selecting some text or an item of interest, and then right-clicking to display a <xref:System.Windows.Controls.ContextMenu> of annotation options.</span></span>  <span data-ttu-id="4d42a-120">A exemplo a seguir mostra o [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] você pode usar para declarar um <xref:System.Windows.Controls.ContextMenu> com comandos roteados que os usuários podem acessar para criar e gerenciar as anotações.</span><span class="sxs-lookup"><span data-stu-id="4d42a-120">The following example shows the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] you can use to declare a <xref:System.Windows.Controls.ContextMenu> with routed commands that users can access to create and manage annotations.</span></span>  
  
 [!code-xaml[DocViewerAnnotationsXps#CreateDeleteAnnotations](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXps/CSharp/Window1.xaml#createdeleteannotations)]  
  
<a name="caf1_framework_data_anchoring"></a>   
## <a name="data-anchoring"></a><span data-ttu-id="4d42a-121">Ancoragem de dados</span><span class="sxs-lookup"><span data-stu-id="4d42a-121">Data Anchoring</span></span>  
 <span data-ttu-id="4d42a-122">O [!INCLUDE[TLA2#tla_caf](../../../../includes/tla2sharptla-caf-md.md)] associa as anotações aos dados que o usuário seleciona, não apenas para uma posição no modo de exibição.</span><span class="sxs-lookup"><span data-stu-id="4d42a-122">The [!INCLUDE[TLA2#tla_caf](../../../../includes/tla2sharptla-caf-md.md)] binds annotations to the data that the user selects, not just to a position on the display view.</span></span> <span data-ttu-id="4d42a-123">Portanto, se a exibição de documento mudar, como quando o usuário rolar ou redimensionar a janela de exibição, a anotação permanecerá com a seleção de dados à qual está vinculada.</span><span class="sxs-lookup"><span data-stu-id="4d42a-123">Therefore, if the document view changes, such as when the user scrolls or resizes the display window, the annotation stays with the data selection to which it is bound.</span></span> <span data-ttu-id="4d42a-124">Por exemplo, o gráfico a seguir ilustra uma anotação que o usuário fez em uma seleção de texto.</span><span class="sxs-lookup"><span data-stu-id="4d42a-124">For example, the following graphic illustrates an annotation that the user has made on a text selection.</span></span> <span data-ttu-id="4d42a-125">Quando a exibição do documento muda (rola, é redimensionada, tem a escala ajustada ou se move de outra maneira), a anotação de realce se move com a seleção de dados original.</span><span class="sxs-lookup"><span data-stu-id="4d42a-125">When the document view changes (scrolls, resizes, scales, or otherwise moves), the highlight annotation moves with the original data selection.</span></span>  
  
 <span data-ttu-id="4d42a-126">![Ancoragem de dados de anotação](../../../../docs/framework/wpf/advanced/media/caf-dataanchoring.png "CAF_DataAnchoring")</span><span class="sxs-lookup"><span data-stu-id="4d42a-126">![Annotation Data Anchoring](../../../../docs/framework/wpf/advanced/media/caf-dataanchoring.png "CAF_DataAnchoring")</span></span>  
  
<a name="matching_annotations_with_annotated_objects"></a>   
## <a name="matching-annotations-with-annotated-objects"></a><span data-ttu-id="4d42a-127">Combinando anotações com objetos anotados</span><span class="sxs-lookup"><span data-stu-id="4d42a-127">Matching Annotations with Annotated Objects</span></span>  
 <span data-ttu-id="4d42a-128">Você pode combinar anotações com os respectivos objetos anotados.</span><span class="sxs-lookup"><span data-stu-id="4d42a-128">You can match annotations with the corresponding annotated objects.</span></span> <span data-ttu-id="4d42a-129">Por exemplo, considere um aplicativo de leitor de documento simples que tenha um painel de comentários.</span><span class="sxs-lookup"><span data-stu-id="4d42a-129">For example, consider a simple document reader application that has a comments pane.</span></span> <span data-ttu-id="4d42a-130">O painel de comentários pode ser uma caixa de listagem que exiba texto de uma lista de anotações ancoradas a um documento.</span><span class="sxs-lookup"><span data-stu-id="4d42a-130">The comments pane might be a list box that displays the text from a list of annotations that are anchored to a document.</span></span> <span data-ttu-id="4d42a-131">Se o usuário selecionar um item na caixa de listagem, o aplicativo trará para a exibição o parágrafo no documento ao qual o objeto de anotação correspondente está ancorado.</span><span class="sxs-lookup"><span data-stu-id="4d42a-131">If the user selects an item in the list box, then the application brings into view the paragraph in the document that the corresponding annotation object is anchored to.</span></span>  
  
 <span data-ttu-id="4d42a-132">O exemplo a seguir demonstra como implementar o manipulador de eventos de uma caixa de listagem assim que serve como painel de comentários.</span><span class="sxs-lookup"><span data-stu-id="4d42a-132">The following example demonstrates how to implement the event handler of such a list box that serves as the comments pane.</span></span>  
  
 [!code-csharp[FlowDocumentAnnotatedViewer#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/CSharp/Window1.xaml.cs#handler)]
 [!code-vb[FlowDocumentAnnotatedViewer#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/visualbasic/window1.xaml.vb#handler)]  
  
 <span data-ttu-id="4d42a-133">Outro cenário de exemplo envolve aplicativos que permitem a troca de anotações e notas autoadesivas entre leitores de documento por email.</span><span class="sxs-lookup"><span data-stu-id="4d42a-133">Another example scenario involves applications that enable the exchange of annotations and sticky notes between document readers through e-mail.</span></span> <span data-ttu-id="4d42a-134">Esse recurso permite que esses aplicativos levem o leitor para a página que contém a anotação que está sendo trocada.</span><span class="sxs-lookup"><span data-stu-id="4d42a-134">This feature enables these applications to navigate the reader to the page that contains the annotation that is being exchanged.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d42a-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4d42a-135">See Also</span></span>  
 <xref:System.Windows.Controls.Primitives.DocumentViewerBase>  
 <xref:System.Windows.Controls.DocumentViewer>  
 <xref:System.Windows.Controls.FlowDocumentPageViewer>  
 <xref:System.Windows.Controls.FlowDocumentScrollViewer>  
 <xref:System.Windows.Controls.FlowDocumentReader>  
 <xref:System.Windows.Annotations.IAnchorInfo>  
 [<span data-ttu-id="4d42a-136">Esquema de anotações</span><span class="sxs-lookup"><span data-stu-id="4d42a-136">Annotations Schema</span></span>](../../../../docs/framework/wpf/advanced/annotations-schema.md)  
 [<span data-ttu-id="4d42a-137">Visão geral de ContextMenu</span><span class="sxs-lookup"><span data-stu-id="4d42a-137">ContextMenu Overview</span></span>](../../../../docs/framework/wpf/controls/contextmenu-overview.md)  
 [<span data-ttu-id="4d42a-138">Visão geral de comandos</span><span class="sxs-lookup"><span data-stu-id="4d42a-138">Commanding Overview</span></span>](../../../../docs/framework/wpf/advanced/commanding-overview.md)  
 [<span data-ttu-id="4d42a-139">Visão geral do documento de fluxo</span><span class="sxs-lookup"><span data-stu-id="4d42a-139">Flow Document Overview</span></span>](../../../../docs/framework/wpf/advanced/flow-document-overview.md)  
 [<span data-ttu-id="4d42a-140">Como adicionar um comando a um MenuItem</span><span class="sxs-lookup"><span data-stu-id="4d42a-140">How to: Add a Command to a MenuItem</span></span>](http://msdn.microsoft.com/library/013d68a0-5373-4a68-bd91-5de574307370)
