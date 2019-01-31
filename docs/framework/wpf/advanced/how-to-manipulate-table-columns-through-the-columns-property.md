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
ms.openlocfilehash: e3327b59cb8c387cb554206d1b17c2cd7002ef80
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55258091"
---
# <a name="how-to-manipulate-a-tables-columns-through-the-columns-property"></a><span data-ttu-id="791f4-102">Como: Manipular colunas de uma tabela por meio da propriedade Columns</span><span class="sxs-lookup"><span data-stu-id="791f4-102">How to: Manipulate a Table's Columns through the Columns Property</span></span>
<span data-ttu-id="791f4-103">Este exemplo demonstra algumas das operações mais comuns que podem ser executadas em colunas de uma tabela por meio de <xref:System.Windows.Documents.Table.Columns%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="791f4-103">This example demonstrates some of the more common operations that can be performed on a table's columns through the <xref:System.Windows.Documents.Table.Columns%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="791f4-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="791f4-104">Example</span></span>  
 <span data-ttu-id="791f4-105">O exemplo a seguir cria uma nova tabela e, em seguida, usa o <xref:System.Windows.Documents.TableColumnCollection.Add%2A> método para adicionar colunas à tabela de <xref:System.Windows.Documents.Table.Columns%2A> coleção.</span><span class="sxs-lookup"><span data-stu-id="791f4-105">The following example creates a new table and then uses the <xref:System.Windows.Documents.TableColumnCollection.Add%2A> method to add columns to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Add](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_add)]
 [!code-vb[TableSnippets2#_Table_Columns_Add](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_add)]  
  
## <a name="example"></a><span data-ttu-id="791f4-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="791f4-106">Example</span></span>  
 <span data-ttu-id="791f4-107">O exemplo a seguir insere um novo <xref:System.Windows.Documents.TableColumn>.</span><span class="sxs-lookup"><span data-stu-id="791f4-107">The following example inserts a new <xref:System.Windows.Documents.TableColumn>.</span></span>  <span data-ttu-id="791f4-108">A nova coluna é inserida na posição de índice 0, tornando-a a nova primeira coluna na tabela.</span><span class="sxs-lookup"><span data-stu-id="791f4-108">The new column is inserted at index position 0, making it the new first column in the table.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="791f4-109">O <xref:System.Windows.Documents.TableColumnCollection> coleção usa a indexação padrão de base zero.</span><span class="sxs-lookup"><span data-stu-id="791f4-109">The <xref:System.Windows.Documents.TableColumnCollection> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Insert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_insert)]
 [!code-vb[TableSnippets2#_Table_Columns_Insert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_insert)]  
  
## <a name="example"></a><span data-ttu-id="791f4-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="791f4-110">Example</span></span>  
 <span data-ttu-id="791f4-111">O exemplo a seguir acessa algumas propriedades arbitrárias em colunas no <xref:System.Windows.Documents.TableColumnCollection> coleção, fazendo referência a colunas específicas por índice.</span><span class="sxs-lookup"><span data-stu-id="791f4-111">The following example accesses some arbitrary properties on columns in the <xref:System.Windows.Documents.TableColumnCollection> collection, referring to particular columns by index.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Manip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_manip)]
 [!code-vb[TableSnippets2#_Table_Columns_Manip](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_manip)]  
  
## <a name="example"></a><span data-ttu-id="791f4-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="791f4-112">Example</span></span>  
 <span data-ttu-id="791f4-113">O exemplo a seguir obtém o número de colunas atualmente hospedadas pela tabela.</span><span class="sxs-lookup"><span data-stu-id="791f4-113">The following example gets the number of columns currently hosted by the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Count](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_count)]
 [!code-vb[TableSnippets2#_Table_Columns_Count](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_count)]  
  
## <a name="example"></a><span data-ttu-id="791f4-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="791f4-114">Example</span></span>  
 <span data-ttu-id="791f4-115">O exemplo a seguir remove uma determinada coluna por referência.</span><span class="sxs-lookup"><span data-stu-id="791f4-115">The following example removes a particular column by reference.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelRef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delref)]
 [!code-vb[TableSnippets2#_Table_Columns_DelRef](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delref)]  
  
## <a name="example"></a><span data-ttu-id="791f4-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="791f4-116">Example</span></span>  
 <span data-ttu-id="791f4-117">O exemplo a seguir remove uma determinada coluna por índice.</span><span class="sxs-lookup"><span data-stu-id="791f4-117">The following example removes a particular column by index.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelIndex](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delindex)]
 [!code-vb[TableSnippets2#_Table_Columns_DelIndex](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delindex)]  
  
## <a name="example"></a><span data-ttu-id="791f4-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="791f4-118">Example</span></span>  
 <span data-ttu-id="791f4-119">O exemplo a seguir remove todas as colunas da coleção de colunas da tabela.</span><span class="sxs-lookup"><span data-stu-id="791f4-119">The following example removes all columns from the table's columns collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Clear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_clear)]
 [!code-vb[TableSnippets2#_Table_Columns_Clear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_clear)]  
  
## <a name="see-also"></a><span data-ttu-id="791f4-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="791f4-120">See also</span></span>
- [<span data-ttu-id="791f4-121">Visão geral da tabela</span><span class="sxs-lookup"><span data-stu-id="791f4-121">Table Overview</span></span>](../../../../docs/framework/wpf/advanced/table-overview.md)
- [<span data-ttu-id="791f4-122">Definir uma tabela com XAML</span><span class="sxs-lookup"><span data-stu-id="791f4-122">Define a Table with XAML</span></span>](../../../../docs/framework/wpf/advanced/how-to-define-a-table-with-xaml.md)
- [<span data-ttu-id="791f4-123">Criar uma tabela de forma programática</span><span class="sxs-lookup"><span data-stu-id="791f4-123">Build a Table Programmatically</span></span>](../../../../docs/framework/wpf/advanced/how-to-build-a-table-programmatically.md)
- [<span data-ttu-id="791f4-124">Manipular grupos de linhas de uma tabela por meio da propriedade RowGroups</span><span class="sxs-lookup"><span data-stu-id="791f4-124">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
- [<span data-ttu-id="791f4-125">Manipular um FlowDocument por meio da propriedade Blocks</span><span class="sxs-lookup"><span data-stu-id="791f4-125">Manipulate a FlowDocument through the Blocks Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [<span data-ttu-id="791f4-126">Manipular grupos de linhas de uma tabela por meio da propriedade RowGroups</span><span class="sxs-lookup"><span data-stu-id="791f4-126">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
