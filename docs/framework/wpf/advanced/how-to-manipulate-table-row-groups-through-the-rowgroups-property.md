---
title: Como manipular grupos de linhas de uma tabela por meio da propriedade RowGroups
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- row groups [WPF], manipulating through RowGroups property
- RowGroups property [WPF], manipulating row groups
- documents [WPF], manipulating row groups through RowGroups property
- properties [WPF], RowGroups [WPF], manipulating row groups
ms.assetid: ea61440f-08ae-44ed-b314-5716aaaae3ed
ms.openlocfilehash: 8cdf3b74fa5bf5a566c541ba035a1c7da7dd6949
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-manipulate-a-table39s-row-groups-through-the-rowgroups-property"></a><span data-ttu-id="f88b5-102">Como manipular grupos de linhas de uma tabela por meio da propriedade RowGroups</span><span class="sxs-lookup"><span data-stu-id="f88b5-102">How to: Manipulate a Table&#39;s Row Groups through the RowGroups Property</span></span>
<span data-ttu-id="f88b5-103">Este exemplo demonstra algumas das operações mais comuns que podem ser executadas em grupos de linhas da tabela por meio de <xref:System.Windows.Documents.Table.RowGroups%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="f88b5-103">This example demonstrates some of the more common operations that can be performed on a table's row groups through the <xref:System.Windows.Documents.Table.RowGroups%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f88b5-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f88b5-104">Example</span></span>  
 <span data-ttu-id="f88b5-105">O exemplo a seguir cria uma nova tabela e, em seguida, usa o <xref:System.Windows.Documents.TableRowGroupCollection.Add%2A> método para adicionar colunas à tabela de <xref:System.Windows.Documents.Table.RowGroups%2A> coleção.</span><span class="sxs-lookup"><span data-stu-id="f88b5-105">The following example creates a new table and then uses the <xref:System.Windows.Documents.TableRowGroupCollection.Add%2A> method to add columns to the table's <xref:System.Windows.Documents.Table.RowGroups%2A> collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Add](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_add)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Add](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_add)]  
  
## <a name="example"></a><span data-ttu-id="f88b5-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f88b5-106">Example</span></span>  
 <span data-ttu-id="f88b5-107">O exemplo a seguir insere um novo <xref:System.Windows.Documents.TableRowGroup>.</span><span class="sxs-lookup"><span data-stu-id="f88b5-107">The following example inserts a new <xref:System.Windows.Documents.TableRowGroup>.</span></span>  <span data-ttu-id="f88b5-108">A nova coluna é inserida na posição de índice 0, tornando-a o novo grupo da primeira linha na tabela.</span><span class="sxs-lookup"><span data-stu-id="f88b5-108">The new column is inserted at index position 0, making it the new first row group in the table.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f88b5-109">O <xref:System.Windows.Documents.TableRowGroupCollection> coleção usa a indexação com base em zero padrão.</span><span class="sxs-lookup"><span data-stu-id="f88b5-109">The <xref:System.Windows.Documents.TableRowGroupCollection> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Insert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_insert)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Insert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_insert)]  
  
## <a name="example"></a><span data-ttu-id="f88b5-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f88b5-110">Example</span></span>  
 <span data-ttu-id="f88b5-111">O exemplo a seguir adiciona várias linhas para um determinado <xref:System.Windows.Documents.TableRowGroup> (especificado pelo índice) na tabela.</span><span class="sxs-lookup"><span data-stu-id="f88b5-111">The following example adds several rows to a particular <xref:System.Windows.Documents.TableRowGroup> (specified by index) in the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_AddRows](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_addrows)]
 [!code-vb[TableSnippets2#_Table_RowGroups_AddRows](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_addrows)]  
  
## <a name="example"></a><span data-ttu-id="f88b5-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f88b5-112">Example</span></span>  
 <span data-ttu-id="f88b5-113">O exemplo a seguir acessa algumas propriedades arbitrárias em linhas no primeiro grupo de linhas na tabela.</span><span class="sxs-lookup"><span data-stu-id="f88b5-113">The following example accesses some arbitrary properties on rows in the first row group in the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_ManipRows](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_maniprows)]
 [!code-vb[TableSnippets2#_Table_RowGroups_ManipRows](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_maniprows)]  
  
## <a name="example"></a><span data-ttu-id="f88b5-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f88b5-114">Example</span></span>  
 <span data-ttu-id="f88b5-115">O exemplo a seguir adiciona várias células para um determinado <xref:System.Windows.Documents.TableRow> (especificado pelo índice) na tabela.</span><span class="sxs-lookup"><span data-stu-id="f88b5-115">The following example adds several cells to a particular <xref:System.Windows.Documents.TableRow> (specified by index) in the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_AddCells](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_addcells)]
 [!code-vb[TableSnippets2#_Table_RowGroups_AddCells](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_addcells)]  
  
## <a name="example"></a><span data-ttu-id="f88b5-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f88b5-116">Example</span></span>  
 <span data-ttu-id="f88b5-117">O exemplo a seguir acessa alguns métodos e propriedades arbitrários em células na primeira linha no primeiro grupo de linhas.</span><span class="sxs-lookup"><span data-stu-id="f88b5-117">The following example access some arbitrary methods and properties on cells in the first row in the first row group.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_ManipCells](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_manipcells)]
 [!code-vb[TableSnippets2#_Table_RowGroups_ManipCells](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_manipcells)]  
  
## <a name="example"></a><span data-ttu-id="f88b5-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f88b5-118">Example</span></span>  
 <span data-ttu-id="f88b5-119">O exemplo a seguir retorna o número de <xref:System.Windows.Documents.TableRowGroup> elementos hospedados pela tabela.</span><span class="sxs-lookup"><span data-stu-id="f88b5-119">The following example returns the number of <xref:System.Windows.Documents.TableRowGroup> elements hosted by the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Count](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_count)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Count](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_count)]  
  
## <a name="example"></a><span data-ttu-id="f88b5-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f88b5-120">Example</span></span>  
 <span data-ttu-id="f88b5-121">O exemplo a seguir remove um grupo de linhas específico por referência.</span><span class="sxs-lookup"><span data-stu-id="f88b5-121">The following example removes a particular row group by reference.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_DelRef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_delref)]
 [!code-vb[TableSnippets2#_Table_RowGroups_DelRef](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_delref)]  
  
## <a name="example"></a><span data-ttu-id="f88b5-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f88b5-122">Example</span></span>  
 <span data-ttu-id="f88b5-123">O exemplo a seguir remove um grupo de linhas específico por índice.</span><span class="sxs-lookup"><span data-stu-id="f88b5-123">The following example removes a particular row group by index.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_DelIndex](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_delindex)]
 [!code-vb[TableSnippets2#_Table_RowGroups_DelIndex](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_delindex)]  
  
## <a name="example"></a><span data-ttu-id="f88b5-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f88b5-124">Example</span></span>  
 <span data-ttu-id="f88b5-125">O exemplo a seguir remove todos os grupos de linhas da coleção de grupos de linhas da tabela.</span><span class="sxs-lookup"><span data-stu-id="f88b5-125">The following example removes all row groups from the table's row groups collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Clear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_clear)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Clear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_clear)]  
  
## <a name="see-also"></a><span data-ttu-id="f88b5-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f88b5-126">See Also</span></span>  
 [<span data-ttu-id="f88b5-127">Como: Manipular elementos de fluxo de conteúdo por meio da propriedade de linhas internas</span><span class="sxs-lookup"><span data-stu-id="f88b5-127">How-to: Manipulate Flow Content Elements through the Inlines Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)  
 [<span data-ttu-id="f88b5-128">Manipular um FlowDocument por meio da propriedade Blocks</span><span class="sxs-lookup"><span data-stu-id="f88b5-128">Manipulate a FlowDocument through the Blocks Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)  
 [<span data-ttu-id="f88b5-129">Manipular colunas de uma tabela por meio da propriedade Columns</span><span class="sxs-lookup"><span data-stu-id="f88b5-129">Manipulate a Table's Columns through the Columns Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-columns-through-the-columns-property.md)
