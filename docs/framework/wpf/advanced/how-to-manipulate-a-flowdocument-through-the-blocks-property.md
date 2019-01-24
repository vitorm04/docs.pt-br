---
title: 'Como: Manipular um FlowDocument por meio da propriedade Blocks'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 'documents [WPF], manipulating FlowDocuments through Blocks property [WPF], , '
- ', '
ms.assetid: cbb7291e-3f1b-433e-9e16-f4d93ced14e8
ms.openlocfilehash: e4367e8907bbe9e9ce9ff7252d30e34c04f8ebd8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54567939"
---
# <a name="how-to-manipulate-a-flowdocument-through-the-blocks-property"></a><span data-ttu-id="0ec59-102">Como: Manipular um FlowDocument por meio da propriedade Blocks</span><span class="sxs-lookup"><span data-stu-id="0ec59-102">How to: Manipulate a FlowDocument through the Blocks Property</span></span>
<span data-ttu-id="0ec59-103">Estes exemplos demonstram algumas das operações mais comuns que podem ser executadas em uma <xref:System.Windows.Documents.FlowDocument> por meio de <xref:System.Windows.Documents.FlowDocument.Blocks%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="0ec59-103">These examples demonstrate some of the more common operations that can be performed on a <xref:System.Windows.Documents.FlowDocument> through the <xref:System.Windows.Documents.FlowDocument.Blocks%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ec59-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ec59-104">Example</span></span>  
 <span data-ttu-id="0ec59-105">O exemplo a seguir cria um novo <xref:System.Windows.Documents.FlowDocument> e, em seguida, acrescenta um novo <xref:System.Windows.Documents.Paragraph> elemento para o <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="0ec59-105">The following example creates a new <xref:System.Windows.Documents.FlowDocument> and then appends a new <xref:System.Windows.Documents.Paragraph> element to the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksAdd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblocksadd)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksAdd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblocksadd)]  
  
## <a name="example"></a><span data-ttu-id="0ec59-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ec59-106">Example</span></span>  
 <span data-ttu-id="0ec59-107">O exemplo a seguir cria um novo <xref:System.Windows.Documents.Paragraph> elemento e o insere no início do <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="0ec59-107">The following example creates a new <xref:System.Windows.Documents.Paragraph> element and inserts it at the beginning of the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksInsert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblocksinsert)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksInsert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblocksinsert)]  
  
## <a name="example"></a><span data-ttu-id="0ec59-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ec59-108">Example</span></span>  
 <span data-ttu-id="0ec59-109">O exemplo a seguir obtém o número de nível superior <xref:System.Windows.Documents.Block> elementos contidos no <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="0ec59-109">The following example gets the number of top-level <xref:System.Windows.Documents.Block> elements contained in the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksCount](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblockscount)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksCount](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblockscount)]  
  
## <a name="example"></a><span data-ttu-id="0ec59-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ec59-110">Example</span></span>  
 <span data-ttu-id="0ec59-111">O exemplo a seguir exclui a última <xref:System.Windows.Documents.Block> elemento no <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="0ec59-111">The following example deletes the last <xref:System.Windows.Documents.Block> element in the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksRemoveLast](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblocksremovelast)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksRemoveLast](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblocksremovelast)]  
  
## <a name="example"></a><span data-ttu-id="0ec59-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0ec59-112">Example</span></span>  
 <span data-ttu-id="0ec59-113">O exemplo a seguir limpa todo o conteúdo (<xref:System.Windows.Documents.Block> elementos) da <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="0ec59-113">The following example clears all of the contents (<xref:System.Windows.Documents.Block> elements) from the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[FlowDocumentSnippets#_FlowDocumentBlocksClear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_flowdocumentblocksclear)]
 [!code-vb[FlowDocumentSnippets#_FlowDocumentBlocksClear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_flowdocumentblocksclear)]  
  
## <a name="see-also"></a><span data-ttu-id="0ec59-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ec59-114">See also</span></span>
- [<span data-ttu-id="0ec59-115">Manipular grupos de linhas de uma tabela por meio da propriedade RowGroups</span><span class="sxs-lookup"><span data-stu-id="0ec59-115">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
- [<span data-ttu-id="0ec59-116">Manipular colunas de uma tabela por meio da propriedade Columns</span><span class="sxs-lookup"><span data-stu-id="0ec59-116">Manipulate a Table's Columns through the Columns Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-columns-through-the-columns-property.md)
- [<span data-ttu-id="0ec59-117">Manipular grupos de linhas de uma tabela por meio da propriedade RowGroups</span><span class="sxs-lookup"><span data-stu-id="0ec59-117">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
