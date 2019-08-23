---
title: 'Como: Manipular colunas de uma tabela por meio da propriedade Columns'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- documents [WPF], manipulating table columns
- properties [WPF], Columns [WPF], manipulating table columns
- tables [WPF], manipulating columns
- Columns property [WPF]
ms.assetid: 3f8884f4-7e1f-456b-be06-fbd3cf469bf3
ms.openlocfilehash: 18a26c76688ebf668293cb1254404d6d2cf15208
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913598"
---
# <a name="how-to-manipulate-a-tables-columns-through-the-columns-property"></a><span data-ttu-id="12011-102">Como: Manipular colunas de uma tabela por meio da propriedade Columns</span><span class="sxs-lookup"><span data-stu-id="12011-102">How to: Manipulate a Table's Columns through the Columns Property</span></span>
<span data-ttu-id="12011-103">Este exemplo demonstra algumas das operações mais comuns que podem ser executadas nas colunas de uma tabela por meio da <xref:System.Windows.Documents.Table.Columns%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="12011-103">This example demonstrates some of the more common operations that can be performed on a table's columns through the <xref:System.Windows.Documents.Table.Columns%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12011-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="12011-104">Example</span></span>  
 <span data-ttu-id="12011-105">O exemplo a seguir cria uma nova tabela e, em <xref:System.Windows.Documents.TableColumnCollection.Add%2A> seguida, usa o método para adicionar colunas <xref:System.Windows.Documents.Table.Columns%2A> à coleção da tabela.</span><span class="sxs-lookup"><span data-stu-id="12011-105">The following example creates a new table and then uses the <xref:System.Windows.Documents.TableColumnCollection.Add%2A> method to add columns to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Add](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_add)]
 [!code-vb[TableSnippets2#_Table_Columns_Add](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_add)]  
  
## <a name="example"></a><span data-ttu-id="12011-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="12011-106">Example</span></span>  
 <span data-ttu-id="12011-107">O exemplo a seguir insere um <xref:System.Windows.Documents.TableColumn>novo.</span><span class="sxs-lookup"><span data-stu-id="12011-107">The following example inserts a new <xref:System.Windows.Documents.TableColumn>.</span></span>  <span data-ttu-id="12011-108">A nova coluna é inserida na posição de índice 0, tornando-a a nova primeira coluna na tabela.</span><span class="sxs-lookup"><span data-stu-id="12011-108">The new column is inserted at index position 0, making it the new first column in the table.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="12011-109">A <xref:System.Windows.Documents.TableColumnCollection> coleção usa a indexação padrão baseada em zero.</span><span class="sxs-lookup"><span data-stu-id="12011-109">The <xref:System.Windows.Documents.TableColumnCollection> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Insert](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_insert)]
 [!code-vb[TableSnippets2#_Table_Columns_Insert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_insert)]  
  
## <a name="example"></a><span data-ttu-id="12011-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="12011-110">Example</span></span>  
 <span data-ttu-id="12011-111">O exemplo a seguir acessa algumas propriedades arbitrárias em colunas na <xref:System.Windows.Documents.TableColumnCollection> coleção, referindo-se a colunas específicas por índice.</span><span class="sxs-lookup"><span data-stu-id="12011-111">The following example accesses some arbitrary properties on columns in the <xref:System.Windows.Documents.TableColumnCollection> collection, referring to particular columns by index.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Manip](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_manip)]
 [!code-vb[TableSnippets2#_Table_Columns_Manip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_manip)]  
  
## <a name="example"></a><span data-ttu-id="12011-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="12011-112">Example</span></span>  
 <span data-ttu-id="12011-113">O exemplo a seguir obtém o número de colunas atualmente hospedadas pela tabela.</span><span class="sxs-lookup"><span data-stu-id="12011-113">The following example gets the number of columns currently hosted by the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Count](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_count)]
 [!code-vb[TableSnippets2#_Table_Columns_Count](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_count)]  
  
## <a name="example"></a><span data-ttu-id="12011-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="12011-114">Example</span></span>  
 <span data-ttu-id="12011-115">O exemplo a seguir remove uma determinada coluna por referência.</span><span class="sxs-lookup"><span data-stu-id="12011-115">The following example removes a particular column by reference.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelRef](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delref)]
 [!code-vb[TableSnippets2#_Table_Columns_DelRef](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delref)]  
  
## <a name="example"></a><span data-ttu-id="12011-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="12011-116">Example</span></span>  
 <span data-ttu-id="12011-117">O exemplo a seguir remove uma determinada coluna por índice.</span><span class="sxs-lookup"><span data-stu-id="12011-117">The following example removes a particular column by index.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelIndex](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delindex)]
 [!code-vb[TableSnippets2#_Table_Columns_DelIndex](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delindex)]  
  
## <a name="example"></a><span data-ttu-id="12011-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="12011-118">Example</span></span>  
 <span data-ttu-id="12011-119">O exemplo a seguir remove todas as colunas da coleção de colunas da tabela.</span><span class="sxs-lookup"><span data-stu-id="12011-119">The following example removes all columns from the table's columns collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Clear](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_clear)]
 [!code-vb[TableSnippets2#_Table_Columns_Clear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_clear)]  
  
## <a name="see-also"></a><span data-ttu-id="12011-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="12011-120">See also</span></span>

- [<span data-ttu-id="12011-121">Visão geral da tabela</span><span class="sxs-lookup"><span data-stu-id="12011-121">Table Overview</span></span>](table-overview.md)
- [<span data-ttu-id="12011-122">Definir uma tabela com XAML</span><span class="sxs-lookup"><span data-stu-id="12011-122">Define a Table with XAML</span></span>](how-to-define-a-table-with-xaml.md)
- [<span data-ttu-id="12011-123">Criar uma tabela de forma programática</span><span class="sxs-lookup"><span data-stu-id="12011-123">Build a Table Programmatically</span></span>](how-to-build-a-table-programmatically.md)
- [<span data-ttu-id="12011-124">Manipular grupos de linhas de uma tabela por meio da propriedade RowGroups</span><span class="sxs-lookup"><span data-stu-id="12011-124">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
- [<span data-ttu-id="12011-125">Manipular um FlowDocument por meio da propriedade Blocks</span><span class="sxs-lookup"><span data-stu-id="12011-125">Manipulate a FlowDocument through the Blocks Property</span></span>](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [<span data-ttu-id="12011-126">Manipular grupos de linhas de uma tabela por meio da propriedade RowGroups</span><span class="sxs-lookup"><span data-stu-id="12011-126">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
