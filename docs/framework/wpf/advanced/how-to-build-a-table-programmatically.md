---
title: 'Como: Compilar uma tabela de forma programática'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tables [WPF], creating programmatically
ms.assetid: e3ca88f3-6e94-4b61-82fc-42104c10b761
ms.openlocfilehash: 7eced80759f4c250cba5b4fb98ab33957b33de14
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715498"
---
# <a name="how-to-build-a-table-programmatically"></a><span data-ttu-id="d6fec-102">Como: Compilar uma tabela de forma programática</span><span class="sxs-lookup"><span data-stu-id="d6fec-102">How to: Build a Table Programmatically</span></span>
<span data-ttu-id="d6fec-103">Os exemplos a seguir mostram como criar programaticamente um <xref:System.Windows.Documents.Table> e preenchê-lo com conteúdo.</span><span class="sxs-lookup"><span data-stu-id="d6fec-103">The following examples show how to programmatically create a <xref:System.Windows.Documents.Table> and populate it with content.</span></span> <span data-ttu-id="d6fec-104">O conteúdo da tabela é particionado em cinco linhas (representado por <xref:System.Windows.Documents.TableRow> objetos contidos em um <xref:System.Windows.Documents.Table.RowGroups%2A> objeto) e seis colunas (representado por <xref:System.Windows.Documents.TableColumn> objetos).</span><span class="sxs-lookup"><span data-stu-id="d6fec-104">The contents of the table are apportioned into five rows (represented by <xref:System.Windows.Documents.TableRow> objects contained in a <xref:System.Windows.Documents.Table.RowGroups%2A> object) and six columns (represented by <xref:System.Windows.Documents.TableColumn> objects).</span></span> <span data-ttu-id="d6fec-105">As linhas são usadas para fins de apresentação diferentes, incluindo uma linha de título para ser usada como título da tabela inteira, uma linha de cabeçalho para descrever as colunas de dados na tabela e uma linha de rodapé com informações resumidas.</span><span class="sxs-lookup"><span data-stu-id="d6fec-105">The rows are used for different presentation purposes, including a title row intended to title the entire table, a header row to describe the columns of data in the table, and a footer row with summary information.</span></span>  <span data-ttu-id="d6fec-106">Observe que a noção das linhas de “título”, “cabeçalho” e “rodapé” não são inerentes à tabela; essas são apenas linhas com características diferentes.</span><span class="sxs-lookup"><span data-stu-id="d6fec-106">Note that the notion of "title", "header", and "footer" rows are not inherent to the table; these are simply rows with different characteristics.</span></span> <span data-ttu-id="d6fec-107">Células de tabela contêm o conteúdo real, que pode ser composto por texto, imagens ou quase qualquer outro [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] elemento.</span><span class="sxs-lookup"><span data-stu-id="d6fec-107">Table cells contain the actual content, which can be comprised of text, images, or nearly any other [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6fec-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d6fec-108">Example</span></span>  
 <span data-ttu-id="d6fec-109">Primeiro, uma <xref:System.Windows.Documents.FlowDocument> é criado para hospedar o <xref:System.Windows.Documents.Table>e uma nova <xref:System.Windows.Documents.Table> é criado e adicionado ao conteúdo do <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="d6fec-109">First, a <xref:System.Windows.Documents.FlowDocument> is created to host the <xref:System.Windows.Documents.Table>, and a new <xref:System.Windows.Documents.Table> is created and added to the contents of the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreate)]
 [!code-vb[TableSnippets#_TableCreate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreate)]  
  
## <a name="example"></a><span data-ttu-id="d6fec-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d6fec-110">Example</span></span>  
 <span data-ttu-id="d6fec-111">Em seguida, seis <xref:System.Windows.Documents.TableColumn> objetos são criados e adicionados à tabela de <xref:System.Windows.Documents.Table.Columns%2A> coleção, com alguma formatação aplicada.</span><span class="sxs-lookup"><span data-stu-id="d6fec-111">Next, six <xref:System.Windows.Documents.TableColumn> objects are created and added to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection, with some formatting applied.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d6fec-112">Observe que a tabela <xref:System.Windows.Documents.Table.Columns%2A> coleção usa a indexação padrão de base zero.</span><span class="sxs-lookup"><span data-stu-id="d6fec-112">Note that the table's <xref:System.Windows.Documents.Table.Columns%2A> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets#_TableCreateColumns](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tablecreatecolumns)]
 [!code-vb[TableSnippets#_TableCreateColumns](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tablecreatecolumns)]  
  
## <a name="example"></a><span data-ttu-id="d6fec-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d6fec-113">Example</span></span>  
 <span data-ttu-id="d6fec-114">Em seguida, uma linha de título é criada e adicionada à tabela com certa formatação aplicada.</span><span class="sxs-lookup"><span data-stu-id="d6fec-114">Next, a title row is created and added to the table with some formatting applied.</span></span>  <span data-ttu-id="d6fec-115">Por coincidência, a linha de título contém uma única célula que abrange todas as seis colunas na tabela.</span><span class="sxs-lookup"><span data-stu-id="d6fec-115">The title row happens to contain a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddtitlerow)]
 [!code-vb[TableSnippets#_TableAddTitleRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddtitlerow)]  
  
## <a name="example"></a><span data-ttu-id="d6fec-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d6fec-116">Example</span></span>  
 <span data-ttu-id="d6fec-117">Em seguida, uma linha de cabeçalho é criada e adicionada à tabela e as células na linha de cabeçalho são criadas e populadas com conteúdo.</span><span class="sxs-lookup"><span data-stu-id="d6fec-117">Next, a header row is created and added to the table, and the cells in the header row are created and populated with content.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddheaderrow)]
 [!code-vb[TableSnippets#_TableAddHeaderRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddheaderrow)]  
  
## <a name="example"></a><span data-ttu-id="d6fec-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d6fec-118">Example</span></span>  
 <span data-ttu-id="d6fec-119">Em seguida, uma linha para os dados é criada e adicionada à tabela, e as células nesta linha são criadas e populadas com conteúdo.</span><span class="sxs-lookup"><span data-stu-id="d6fec-119">Next, a row for data is created and added to the table, and the cells in this row are created and populated with content.</span></span>  <span data-ttu-id="d6fec-120">A criação dessa linha é semelhante à criação da linha de cabeçalho, com uma formatação ligeiramente diferente aplicada.</span><span class="sxs-lookup"><span data-stu-id="d6fec-120">Building this row is similar to building the header row, with slightly different formatting applied.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddDataRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableadddatarow)]
 [!code-vb[TableSnippets#_TableAddDataRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableadddatarow)]  
  
## <a name="example"></a><span data-ttu-id="d6fec-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d6fec-121">Example</span></span>  
 <span data-ttu-id="d6fec-122">Por fim, uma linha de rodapé é criada, adicionada e formatada.</span><span class="sxs-lookup"><span data-stu-id="d6fec-122">Finally, a footer row is created, added, and formatted.</span></span>  <span data-ttu-id="d6fec-123">Como a linha de título, o rodapé contém uma única célula que abrange todas as seis colunas na tabela.</span><span class="sxs-lookup"><span data-stu-id="d6fec-123">Like the title row, the footer contains a single cell that spans all six columns in the table.</span></span>  
  
 [!code-csharp[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets/CSharp/Table.cs#_tableaddfooterrow)]
 [!code-vb[TableSnippets#_TableAddFooterRow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets/VisualBasic/Table.vb#_tableaddfooterrow)]  
  
## <a name="see-also"></a><span data-ttu-id="d6fec-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d6fec-124">See also</span></span>
- [<span data-ttu-id="d6fec-125">Visão geral da tabela</span><span class="sxs-lookup"><span data-stu-id="d6fec-125">Table Overview</span></span>](../../../../docs/framework/wpf/advanced/table-overview.md)
