---
title: DataTableReaders
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ed9094a036262bac2e101e7b4268aac2e66a0d10
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="datatablereaders"></a><span data-ttu-id="b566f-102">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="b566f-102">DataTableReaders</span></span>
<span data-ttu-id="b566f-103">O <xref:System.Data.DataTableReader> apresenta o conteúdo de um <xref:System.Data.DataTable> ou <xref:System.Data.DataSet> na forma de um ou mais resultados de somente leitura, somente encaminhamento define.</span><span class="sxs-lookup"><span data-stu-id="b566f-103">The <xref:System.Data.DataTableReader> presents the contents of a <xref:System.Data.DataTable> or a <xref:System.Data.DataSet> in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="b566f-104">Quando você cria um **DataTableReader** de um **DataTable**, resultante **DataTableReader** objeto contém um conjunto de resultados com os mesmos dados que o  **DataTable** do qual ele foi criado, exceto para todas as linhas que foram marcadas como excluídas.</span><span class="sxs-lookup"><span data-stu-id="b566f-104">When you create a **DataTableReader** from a **DataTable**, the resulting **DataTableReader** object contains one result set with the same data as the **DataTable** from which it was created, except for any rows that have been marked as deleted.</span></span> <span data-ttu-id="b566f-105">As colunas aparecem na mesma ordem que o original **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="b566f-105">The columns appear in the same order as in the original **DataTable**.</span></span>  
  
 <span data-ttu-id="b566f-106">Um **DataTableReader** pode conter vários conjuntos de resultados se ela foi criada chamando <xref:System.Data.DataSet.CreateDataReader%2A>.</span><span class="sxs-lookup"><span data-stu-id="b566f-106">A **DataTableReader** may contain multiple result sets if it was created by calling <xref:System.Data.DataSet.CreateDataReader%2A>.</span></span> <span data-ttu-id="b566f-107">Os resultados estão na mesma ordem que a **DataTables** no **DataSet** do objeto <xref:System.Data.DataSet.Tables%2A> coleção.</span><span class="sxs-lookup"><span data-stu-id="b566f-107">The results are in the same order as the **DataTables** in the **DataSet** object's <xref:System.Data.DataSet.Tables%2A> collection.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b566f-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="b566f-108">In This Section</span></span>  
 [<span data-ttu-id="b566f-109">Criando um DataReader</span><span class="sxs-lookup"><span data-stu-id="b566f-109">Creating a DataReader</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datareader.md)  
 <span data-ttu-id="b566f-110">Discute como criar um **DataTableReader** objeto.</span><span class="sxs-lookup"><span data-stu-id="b566f-110">Discusses how to create a **DataTableReader** object.</span></span>  
  
 [<span data-ttu-id="b566f-111">Navegando DataTables</span><span class="sxs-lookup"><span data-stu-id="b566f-111">Navigating DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datatables.md)  
 <span data-ttu-id="b566f-112">Descreve o uso do **leitura** método para mover o conteúdo de um **DataTableReader**.</span><span class="sxs-lookup"><span data-stu-id="b566f-112">Describes the use of the **Read** method to move through the contents of a **DataTableReader**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b566f-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b566f-113">See Also</span></span>  
 <span data-ttu-id="b566f-114">[Retrieving and Modifying Data in ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="b566f-114">[Retrieving and Modifying Data in ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)</span></span>  
 <span data-ttu-id="b566f-115">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="b566f-115">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
