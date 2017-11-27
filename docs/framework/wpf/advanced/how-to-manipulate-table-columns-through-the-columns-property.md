---
title: Como manipular colunas de uma tabela por meio da propriedade Columns
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
- documents [WPF], manipulating table columns
- properties [WPF], Columns [WPF], manipulating table columns
- tables [WPF], manipulating columns
- Columns property [WPF]
ms.assetid: 3f8884f4-7e1f-456b-be06-fbd3cf469bf3
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d0f15339b829335798d7ee21dcc90b81cb536cf2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-manipulate-a-table39s-columns-through-the-columns-property"></a><span data-ttu-id="4d8b5-102">Como manipular colunas de uma tabela por meio da propriedade Columns</span><span class="sxs-lookup"><span data-stu-id="4d8b5-102">How to: Manipulate a Table&#39;s Columns through the Columns Property</span></span>
<span data-ttu-id="4d8b5-103">Este exemplo demonstra algumas das operações mais comuns que podem ser executadas em colunas de uma tabela por meio de <xref:System.Windows.Documents.Table.Columns%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="4d8b5-103">This example demonstrates some of the more common operations that can be performed on a table's columns through the <xref:System.Windows.Documents.Table.Columns%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d8b5-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4d8b5-104">Example</span></span>  
 <span data-ttu-id="4d8b5-105">O exemplo a seguir cria uma nova tabela e, em seguida, usa o <xref:System.Windows.Documents.TableColumnCollection.Add%2A> método para adicionar colunas à tabela de <xref:System.Windows.Documents.Table.Columns%2A> coleção.</span><span class="sxs-lookup"><span data-stu-id="4d8b5-105">The following example creates a new table and then uses the <xref:System.Windows.Documents.TableColumnCollection.Add%2A> method to add columns to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Add](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_add)]
 [!code-vb[TableSnippets2#_Table_Columns_Add](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_add)]  
  
## <a name="example"></a><span data-ttu-id="4d8b5-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4d8b5-106">Example</span></span>  
 <span data-ttu-id="4d8b5-107">O exemplo a seguir insere um novo <xref:System.Windows.Documents.TableColumn>.</span><span class="sxs-lookup"><span data-stu-id="4d8b5-107">The following example inserts a new <xref:System.Windows.Documents.TableColumn>.</span></span>  <span data-ttu-id="4d8b5-108">A nova coluna é inserida na posição de índice 0, tornando-a a nova primeira coluna na tabela.</span><span class="sxs-lookup"><span data-stu-id="4d8b5-108">The new column is inserted at index position 0, making it the new first column in the table.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4d8b5-109">O <xref:System.Windows.Documents.TableColumnCollection> coleção usa a indexação com base em zero padrão.</span><span class="sxs-lookup"><span data-stu-id="4d8b5-109">The <xref:System.Windows.Documents.TableColumnCollection> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Insert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_insert)]
 [!code-vb[TableSnippets2#_Table_Columns_Insert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_insert)]  
  
## <a name="example"></a><span data-ttu-id="4d8b5-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4d8b5-110">Example</span></span>  
 <span data-ttu-id="4d8b5-111">O exemplo a seguir acessa algumas propriedades arbitrárias em colunas da <xref:System.Windows.Documents.TableColumnCollection> coleção, que faz referência a colunas específicas por índice.</span><span class="sxs-lookup"><span data-stu-id="4d8b5-111">The following example accesses some arbitrary properties on columns in the <xref:System.Windows.Documents.TableColumnCollection> collection, referring to particular columns by index.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Manip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_manip)]
 [!code-vb[TableSnippets2#_Table_Columns_Manip](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_manip)]  
  
## <a name="example"></a><span data-ttu-id="4d8b5-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4d8b5-112">Example</span></span>  
 <span data-ttu-id="4d8b5-113">O exemplo a seguir obtém o número de colunas atualmente hospedadas pela tabela.</span><span class="sxs-lookup"><span data-stu-id="4d8b5-113">The following example gets the number of columns currently hosted by the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Count](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_count)]
 [!code-vb[TableSnippets2#_Table_Columns_Count](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_count)]  
  
## <a name="example"></a><span data-ttu-id="4d8b5-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4d8b5-114">Example</span></span>  
 <span data-ttu-id="4d8b5-115">O exemplo a seguir remove uma determinada coluna por referência.</span><span class="sxs-lookup"><span data-stu-id="4d8b5-115">The following example removes a particular column by reference.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelRef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delref)]
 [!code-vb[TableSnippets2#_Table_Columns_DelRef](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delref)]  
  
## <a name="example"></a><span data-ttu-id="4d8b5-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4d8b5-116">Example</span></span>  
 <span data-ttu-id="4d8b5-117">O exemplo a seguir remove uma determinada coluna por índice.</span><span class="sxs-lookup"><span data-stu-id="4d8b5-117">The following example removes a particular column by index.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelIndex](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delindex)]
 [!code-vb[TableSnippets2#_Table_Columns_DelIndex](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delindex)]  
  
## <a name="example"></a><span data-ttu-id="4d8b5-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4d8b5-118">Example</span></span>  
 <span data-ttu-id="4d8b5-119">O exemplo a seguir remove todas as colunas da coleção de colunas da tabela.</span><span class="sxs-lookup"><span data-stu-id="4d8b5-119">The following example removes all columns from the table's columns collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Clear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_clear)]
 [!code-vb[TableSnippets2#_Table_Columns_Clear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_clear)]  
  
## <a name="see-also"></a><span data-ttu-id="4d8b5-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4d8b5-120">See Also</span></span>  
 [<span data-ttu-id="4d8b5-121">Visão geral da tabela</span><span class="sxs-lookup"><span data-stu-id="4d8b5-121">Table Overview</span></span>](../../../../docs/framework/wpf/advanced/table-overview.md)  
 [<span data-ttu-id="4d8b5-122">Definir uma tabela com XAML</span><span class="sxs-lookup"><span data-stu-id="4d8b5-122">Define a Table with XAML</span></span>](../../../../docs/framework/wpf/advanced/how-to-define-a-table-with-xaml.md)  
 [<span data-ttu-id="4d8b5-123">Criar uma tabela de forma programática</span><span class="sxs-lookup"><span data-stu-id="4d8b5-123">Build a Table Programmatically</span></span>](../../../../docs/framework/wpf/advanced/how-to-build-a-table-programmatically.md)  
 [<span data-ttu-id="4d8b5-124">Manipular grupos de linhas de uma tabela por meio da propriedade RowGroups</span><span class="sxs-lookup"><span data-stu-id="4d8b5-124">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)  
 [<span data-ttu-id="4d8b5-125">Manipular um FlowDocument por meio da propriedade Blocks</span><span class="sxs-lookup"><span data-stu-id="4d8b5-125">Manipulate a FlowDocument through the Blocks Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-a-flowdocument-through-the-blocks-property.md)  
 [<span data-ttu-id="4d8b5-126">Manipular grupos de linhas de uma tabela por meio da propriedade RowGroups</span><span class="sxs-lookup"><span data-stu-id="4d8b5-126">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](../../../../docs/framework/wpf/advanced/how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
