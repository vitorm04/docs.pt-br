---
title: 'Como: Manipular elementos de conteúdo de fluxo por meio da propriedade Inlines'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flow content elements [WPF], manipulating through Inlines property
- documents [WPF], manipulating flow Content elements through Inlines property
- Inlines property [WPF], manipulating flow Content elements
- properties [WPF], Inlines [WPF], manipulating flow Content elements
ms.assetid: 510780d2-3da1-4360-8763-7054bda22ea3
ms.openlocfilehash: cfff958bb4c87e6bfecf2d280224cda233c31806
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186063"
---
# <a name="how-to-manipulate-flow-content-elements-through-the-inlines-property"></a><span data-ttu-id="f966d-102">Como: Manipular elementos de conteúdo de fluxo por meio da propriedade Inlines</span><span class="sxs-lookup"><span data-stu-id="f966d-102">How to: Manipulate Flow Content Elements through the Inlines Property</span></span>
<span data-ttu-id="f966d-103">Estes exemplos demonstram algumas das operações mais comuns que podem ser executadas em elementos de conteúdo de fluxo embutido (e contêineres desses elementos, tais como <xref:System.Windows.Controls.TextBlock>) por meio de **Inlines** propriedade.</span><span class="sxs-lookup"><span data-stu-id="f966d-103">These examples demonstrate some of the more common operations that can be performed on inline flow content elements (and containers of such elements, such as <xref:System.Windows.Controls.TextBlock>) through the **Inlines** property.</span></span> <span data-ttu-id="f966d-104">Essa propriedade é usada para adicionar e remover itens de <xref:System.Windows.Documents.InlineCollection>.</span><span class="sxs-lookup"><span data-stu-id="f966d-104">This property is used to add and remove items from <xref:System.Windows.Documents.InlineCollection>.</span></span> <span data-ttu-id="f966d-105">Elementos de conteúdo de fluxo com uma propriedade **Inlines** incluem:</span><span class="sxs-lookup"><span data-stu-id="f966d-105">Flow content elements that feature an **Inlines** property include:</span></span>  
  
-   <xref:System.Windows.Documents.Bold>  
  
-   <xref:System.Windows.Documents.Hyperlink>  
  
-   <xref:System.Windows.Documents.Italic>  
  
-   <xref:System.Windows.Documents.Paragraph>  
  
-   <xref:System.Windows.Documents.Span>  
  
-   <xref:System.Windows.Documents.Underline>  
  
 <span data-ttu-id="f966d-106">Esses exemplos, por acaso, use <xref:System.Windows.Documents.Span> como o fluxo de elemento de conteúdo, mas essas técnicas são aplicáveis a todos os elementos ou controles que hospedam um <xref:System.Windows.Documents.InlineCollection> coleção.</span><span class="sxs-lookup"><span data-stu-id="f966d-106">These examples happen to use <xref:System.Windows.Documents.Span> as the flow content element, but these techniques are applicable to all elements or controls that host an <xref:System.Windows.Documents.InlineCollection> collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f966d-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f966d-107">Example</span></span>  
 <span data-ttu-id="f966d-108">O exemplo a seguir cria um novo <xref:System.Windows.Documents.Span> objeto e, em seguida, usa o **Add** método para adicionar dois texto é executado como conteúdo filho do <xref:System.Windows.Documents.Span>.</span><span class="sxs-lookup"><span data-stu-id="f966d-108">The following example creates a new <xref:System.Windows.Documents.Span> object, and then uses the **Add** method to add two text runs as content children of the <xref:System.Windows.Documents.Span>.</span></span>  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
## <a name="example"></a><span data-ttu-id="f966d-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f966d-109">Example</span></span>  
 <span data-ttu-id="f966d-110">O exemplo a seguir cria um novo <xref:System.Windows.Documents.Run> elemento e o insere no início do <xref:System.Windows.Documents.Span>.</span><span class="sxs-lookup"><span data-stu-id="f966d-110">The following example creates a new <xref:System.Windows.Documents.Run> element and inserts it at the beginning of the <xref:System.Windows.Documents.Span>.</span></span>  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
## <a name="example"></a><span data-ttu-id="f966d-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f966d-111">Example</span></span>  
 <span data-ttu-id="f966d-112">O exemplo a seguir obtém o número de nível superior <xref:System.Windows.Documents.Inline> elementos contidos no <xref:System.Windows.Documents.Span>.</span><span class="sxs-lookup"><span data-stu-id="f966d-112">The following example gets the number of top-level <xref:System.Windows.Documents.Inline> elements contained in the <xref:System.Windows.Documents.Span>.</span></span>  
  
 [!code-csharp[SpanSnippets#_SpanInlinesCount](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinescount)]
 [!code-vb[SpanSnippets#_SpanInlinesCount](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinescount)]  
  
## <a name="example"></a><span data-ttu-id="f966d-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f966d-113">Example</span></span>  
 <span data-ttu-id="f966d-114">O exemplo a seguir exclui a última <xref:System.Windows.Documents.Inline> elemento no <xref:System.Windows.Documents.Span>.</span><span class="sxs-lookup"><span data-stu-id="f966d-114">The following example deletes the last <xref:System.Windows.Documents.Inline> element in the <xref:System.Windows.Documents.Span>.</span></span>  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
## <a name="example"></a><span data-ttu-id="f966d-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f966d-115">Example</span></span>  
 <span data-ttu-id="f966d-116">O exemplo a seguir limpa todo o conteúdo (<xref:System.Windows.Documents.Inline> elementos) da <xref:System.Windows.Documents.Span>.</span><span class="sxs-lookup"><span data-stu-id="f966d-116">The following example clears all of the contents (<xref:System.Windows.Documents.Inline> elements) from the <xref:System.Windows.Documents.Span>.</span></span>  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
## <a name="see-also"></a><span data-ttu-id="f966d-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f966d-117">See also</span></span>

- <xref:System.Windows.Documents.BlockCollection>
- <xref:System.Windows.Documents.InlineCollection>
- <xref:System.Windows.Documents.ListItemCollection>
- [<span data-ttu-id="f966d-118">Visão geral do documento de fluxo</span><span class="sxs-lookup"><span data-stu-id="f966d-118">Flow Document Overview</span></span>](flow-document-overview.md)
- [<span data-ttu-id="f966d-119">Manipular um FlowDocument por meio da propriedade Blocks</span><span class="sxs-lookup"><span data-stu-id="f966d-119">Manipulate a FlowDocument through the Blocks Property</span></span>](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [<span data-ttu-id="f966d-120">Manipular colunas de uma tabela por meio da propriedade Columns</span><span class="sxs-lookup"><span data-stu-id="f966d-120">Manipulate a Table's Columns through the Columns Property</span></span>](how-to-manipulate-table-columns-through-the-columns-property.md)
- [<span data-ttu-id="f966d-121">Manipular grupos de linhas de uma tabela por meio da propriedade RowGroups</span><span class="sxs-lookup"><span data-stu-id="f966d-121">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
