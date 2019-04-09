---
title: 'Como: Manipular elementos de conteúdo de fluxo por meio da propriedade Blocks'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- documents [WPF], manipulating flow content elements through Blocks property
- flow content elements [WPF], manipulating through Blocks property
- properties [WPF], Blocks [WPF], manipulating flow content elements
- Blocks property [WPF], manipulating flow content elements
ms.assetid: aeda4ece-b979-4818-a093-ef938e908751
ms.openlocfilehash: e0e1e1333a54946f3bdf474e353de0301eb42447
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150131"
---
# <a name="how-to-manipulate-flow-content-elements-through-the-blocks-property"></a><span data-ttu-id="0d4a7-102">Como: Manipular elementos de conteúdo de fluxo por meio da propriedade Blocks</span><span class="sxs-lookup"><span data-stu-id="0d4a7-102">How to: Manipulate Flow Content Elements through the Blocks Property</span></span>
<span data-ttu-id="0d4a7-103">Estes exemplos demonstram algumas das operações mais comuns que podem ser executadas em elementos de conteúdo de fluxo por meio da propriedade **Blocks**.</span><span class="sxs-lookup"><span data-stu-id="0d4a7-103">These examples demonstrate some of the more common operations that can be performed on flow content elements through the **Blocks** property.</span></span> <span data-ttu-id="0d4a7-104">Essa propriedade é usada para adicionar e remover itens de <xref:System.Windows.Documents.BlockCollection>.</span><span class="sxs-lookup"><span data-stu-id="0d4a7-104">This property is used to add and remove items from <xref:System.Windows.Documents.BlockCollection>.</span></span> <span data-ttu-id="0d4a7-105">Elementos de conteúdo de fluxo com uma propriedade **Blocks** incluem:</span><span class="sxs-lookup"><span data-stu-id="0d4a7-105">Flow content elements that feature a **Blocks** property include:</span></span>  
  
-   <xref:System.Windows.Documents.Figure>  
  
-   <xref:System.Windows.Documents.Floater>  
  
-   <xref:System.Windows.Documents.ListItem>  
  
-   <xref:System.Windows.Documents.Section>  
  
-   <xref:System.Windows.Documents.TableCell>  
  
 <span data-ttu-id="0d4a7-106">Esses exemplos, por acaso, usam <xref:System.Windows.Documents.Section> como o fluxo de elemento de conteúdo, mas essas técnicas são aplicáveis a todos os elementos que hospedam uma coleção de elementos de conteúdo de fluxo.</span><span class="sxs-lookup"><span data-stu-id="0d4a7-106">These examples happen to use <xref:System.Windows.Documents.Section> as the flow content element, but these techniques are applicable to all elements that host a flow content element collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d4a7-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0d4a7-107">Example</span></span>  
 <span data-ttu-id="0d4a7-108">O exemplo a seguir cria um novo <xref:System.Windows.Documents.Section> e, em seguida, usa o **Add** para adicionar um novo parágrafo para o **seção** conteúdo.</span><span class="sxs-lookup"><span data-stu-id="0d4a7-108">The following example creates a new <xref:System.Windows.Documents.Section> and then uses the **Add** method to add a new Paragraph to the **Section** contents.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksadd)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksadd)]  
  
## <a name="example"></a><span data-ttu-id="0d4a7-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0d4a7-109">Example</span></span>  
 <span data-ttu-id="0d4a7-110">O exemplo a seguir cria um novo <xref:System.Windows.Documents.Paragraph> elemento e o insere no início do <xref:System.Windows.Documents.Section>.</span><span class="sxs-lookup"><span data-stu-id="0d4a7-110">The following example creates a new <xref:System.Windows.Documents.Paragraph> element and inserts it at the beginning of the <xref:System.Windows.Documents.Section>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksinsert)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksinsert)]  
  
## <a name="example"></a><span data-ttu-id="0d4a7-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0d4a7-111">Example</span></span>  
 <span data-ttu-id="0d4a7-112">O exemplo a seguir obtém o número de nível superior <xref:System.Windows.Documents.Block> elementos contidos no <xref:System.Windows.Documents.Section>.</span><span class="sxs-lookup"><span data-stu-id="0d4a7-112">The following example gets the number of top-level <xref:System.Windows.Documents.Block> elements contained in the <xref:System.Windows.Documents.Section>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksCount](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblockscount)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksCount](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblockscount)]  
  
## <a name="example"></a><span data-ttu-id="0d4a7-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0d4a7-113">Example</span></span>  
 <span data-ttu-id="0d4a7-114">O exemplo a seguir exclui a última <xref:System.Windows.Documents.Block> elemento no <xref:System.Windows.Documents.Section>.</span><span class="sxs-lookup"><span data-stu-id="0d4a7-114">The following example deletes the last <xref:System.Windows.Documents.Block> element in the <xref:System.Windows.Documents.Section>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksremovelast)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksremovelast)]  
  
## <a name="example"></a><span data-ttu-id="0d4a7-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0d4a7-115">Example</span></span>  
 <span data-ttu-id="0d4a7-116">O exemplo a seguir limpa todo o conteúdo (<xref:System.Windows.Documents.Block> elementos) da <xref:System.Windows.Documents.Section>.</span><span class="sxs-lookup"><span data-stu-id="0d4a7-116">The following example clears all of the contents (<xref:System.Windows.Documents.Block> elements) from the <xref:System.Windows.Documents.Section>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksClear](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksclear)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksclear)]  
  
## <a name="see-also"></a><span data-ttu-id="0d4a7-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0d4a7-117">See also</span></span>

- <xref:System.Windows.Documents.BlockCollection>
- <xref:System.Windows.Documents.InlineCollection>
- <xref:System.Windows.Documents.ListItemCollection>
- [<span data-ttu-id="0d4a7-118">Visão geral do documento de fluxo</span><span class="sxs-lookup"><span data-stu-id="0d4a7-118">Flow Document Overview</span></span>](flow-document-overview.md)
- [<span data-ttu-id="0d4a7-119">Manipular grupos de linhas de uma tabela por meio da propriedade RowGroups</span><span class="sxs-lookup"><span data-stu-id="0d4a7-119">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
- [<span data-ttu-id="0d4a7-120">Manipular colunas de uma tabela por meio da propriedade Columns</span><span class="sxs-lookup"><span data-stu-id="0d4a7-120">Manipulate a Table's Columns through the Columns Property</span></span>](how-to-manipulate-table-columns-through-the-columns-property.md)
- [<span data-ttu-id="0d4a7-121">Manipular grupos de linhas de uma tabela por meio da propriedade RowGroups</span><span class="sxs-lookup"><span data-stu-id="0d4a7-121">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
