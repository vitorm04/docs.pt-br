---
title: "Consultando a coleção DataRowView em um DataView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b9070a12-1094-44d6-bb87-a23b50bcb0af
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 02b32157fe88bddfd9a777042f6da87aa48ca551
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="querying-the-datarowview-collection-in-a-dataview"></a><span data-ttu-id="09775-102">Consultando a coleção DataRowView em um DataView</span><span class="sxs-lookup"><span data-stu-id="09775-102">Querying the DataRowView Collection in a DataView</span></span>
<span data-ttu-id="09775-103">O <xref:System.Data.DataView> expõe uma coleção enumerável de objetos <xref:System.Data.DataRowView>.</span><span class="sxs-lookup"><span data-stu-id="09775-103">The <xref:System.Data.DataView> exposes an enumerable collection of <xref:System.Data.DataRowView> objects.</span></span> <span data-ttu-id="09775-104">O <xref:System.Data.DataRowView> representa uma exibição personalizada do <xref:System.Data.DataRow> e exibe uma versão específica desse <xref:System.Data.DataRow> em um controle.</span><span class="sxs-lookup"><span data-stu-id="09775-104"><xref:System.Data.DataRowView> represents a customized view of a <xref:System.Data.DataRow> and displays a specific version of that <xref:System.Data.DataRow> in a control.</span></span> <span data-ttu-id="09775-105">Somente uma versão de um <xref:System.Data.DataRow> pode ser exibida em um controle, como <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="09775-105">Only one version of a <xref:System.Data.DataRow> can be displayed through a control, such as a <xref:System.Windows.Forms.DataGridView>.</span></span> <span data-ttu-id="09775-106">Você pode acessar o <xref:System.Data.DataRow> que é exposto pelo <xref:System.Data.DataRowView> por meio da propriedade <xref:System.Data.DataRowView.Row%2A> do <xref:System.Data.DataRowView>.</span><span class="sxs-lookup"><span data-stu-id="09775-106">You can access the <xref:System.Data.DataRow> that is exposed by the <xref:System.Data.DataRowView> through the <xref:System.Data.DataRowView.Row%2A> property of the <xref:System.Data.DataRowView>.</span></span> <span data-ttu-id="09775-107">Quando você exibe valores usando um <xref:System.Data.DataRowView>, a propriedade <xref:System.Data.DataView.RowStateFilter%2A> determina qual versão da linha do <xref:System.Data.DataRow> subjacente é exposta.</span><span class="sxs-lookup"><span data-stu-id="09775-107">When you view values by using a <xref:System.Data.DataRowView>, the <xref:System.Data.DataView.RowStateFilter%2A> property determines which row version of the underlying <xref:System.Data.DataRow> is exposed.</span></span> <span data-ttu-id="09775-108">Para obter informações sobre como acessar versões de linha diferente usando um <xref:System.Data.DataRow>, consulte [estados de linha e versões de linha](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span><span class="sxs-lookup"><span data-stu-id="09775-108">For information about accessing different row versions using a <xref:System.Data.DataRow>, see [Row States and Row Versions](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span> <span data-ttu-id="09775-109">Porque a coleção de <xref:System.Data.DataRowView> objetos expostos pelo <xref:System.Data.DataView> é enumerável, você pode usar [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] para consultar sobre ele.</span><span class="sxs-lookup"><span data-stu-id="09775-109">Because the collection of <xref:System.Data.DataRowView> objects exposed by the <xref:System.Data.DataView> is enumerable, you can use [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] to query over it.</span></span>  
  
 <span data-ttu-id="09775-110">O exemplo a seguir consulta produtos na cor vermelha na tabela `Product` e cria uma tabela daquela consulta.</span><span class="sxs-lookup"><span data-stu-id="09775-110">The following example queries the `Product` table for red-colored products and creates a table from that query.</span></span> <span data-ttu-id="09775-111">Um <xref:System.Data.DataView> é criado da tabela e a propriedade <xref:System.Data.DataView.RowStateFilter%2A> é definida para filtrar em linhas excluídas e modificadas.</span><span class="sxs-lookup"><span data-stu-id="09775-111">A <xref:System.Data.DataView> is created from the table and the <xref:System.Data.DataView.RowStateFilter%2A> property is set to filter on deleted and modified rows.</span></span> <span data-ttu-id="09775-112">O <xref:System.Data.DataView> é então usado como uma origem em uma consulta LINQ, e os objetos <xref:System.Data.DataRowView> que foram modificados e excluídos são associados a um controle <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="09775-112">The <xref:System.Data.DataView> is then used as a source in a LINQ query, and the <xref:System.Data.DataRowView> objects that have been modified and deleted are bound to a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[DP DataView Samples#QueryDataView2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview2)]
 [!code-vb[DP DataView Samples#QueryDataView2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview2)]  
  
 <span data-ttu-id="09775-113">O exemplo a seguir cria uma tabela de produtos de uma exibição que está associada a um controle <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="09775-113">The following example creates a table of products from a view that is bound to a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="09775-114">Produtos na cor vermelha são consultados no <xref:System.Data.DataView> e os resultados ordenados são associados a um controle <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="09775-114">The <xref:System.Data.DataView> is queried for red-colored products and the ordered results are bound to a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[DP DataView Samples#QueryDataView1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview1)]
 [!code-vb[DP DataView Samples#QueryDataView1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview1)]  
  
## <a name="see-also"></a><span data-ttu-id="09775-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="09775-115">See Also</span></span>  
 [<span data-ttu-id="09775-116">Associação de dados e LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="09775-116">Data Binding and LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
