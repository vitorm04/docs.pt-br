---
title: DataTableReaders
ms.date: 03/30/2017
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
ms.openlocfilehash: 1559cde9cb786ccb2baf920347064b8b28d472c3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785347"
---
# <a name="datatablereaders"></a><span data-ttu-id="ccb33-102">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="ccb33-102">DataTableReaders</span></span>
<span data-ttu-id="ccb33-103">O <xref:System.Data.DataTableReader> apresenta o conteúdo de um <xref:System.Data.DataTable> ou <xref:System.Data.DataSet> de um no formato de um ou mais conjuntos de resultados somente de encaminhamento e somente leitura.</span><span class="sxs-lookup"><span data-stu-id="ccb33-103">The <xref:System.Data.DataTableReader> presents the contents of a <xref:System.Data.DataTable> or a <xref:System.Data.DataSet> in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="ccb33-104">Quando você cria um **DataTableReader** a partir de uma **DataTable**, o objeto **DataTableReader** resultante contém um conjunto de resultados com os mesmos dados que a **DataTable** da qual foi criado, exceto para todas as linhas que foram marcadas como excluí.</span><span class="sxs-lookup"><span data-stu-id="ccb33-104">When you create a **DataTableReader** from a **DataTable**, the resulting **DataTableReader** object contains one result set with the same data as the **DataTable** from which it was created, except for any rows that have been marked as deleted.</span></span> <span data-ttu-id="ccb33-105">As colunas aparecem na mesma ordem que na **DataTable**original.</span><span class="sxs-lookup"><span data-stu-id="ccb33-105">The columns appear in the same order as in the original **DataTable**.</span></span>  
  
 <span data-ttu-id="ccb33-106">Um **DataTableReader** pode conter vários conjuntos de resultados se ele foi criado chamando <xref:System.Data.DataSet.CreateDataReader%2A>.</span><span class="sxs-lookup"><span data-stu-id="ccb33-106">A **DataTableReader** may contain multiple result sets if it was created by calling <xref:System.Data.DataSet.CreateDataReader%2A>.</span></span> <span data-ttu-id="ccb33-107">Os resultados estão na mesma ordem que as **tabelas de tabela** na coleção do <xref:System.Data.DataSet.Tables%2A> objeto DataSet.</span><span class="sxs-lookup"><span data-stu-id="ccb33-107">The results are in the same order as the **DataTables** in the **DataSet** object's <xref:System.Data.DataSet.Tables%2A> collection.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ccb33-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="ccb33-108">In This Section</span></span>  
 [<span data-ttu-id="ccb33-109">Criando um DataReader</span><span class="sxs-lookup"><span data-stu-id="ccb33-109">Creating a DataReader</span></span>](creating-a-datareader.md)  
 <span data-ttu-id="ccb33-110">Discute como criar um objeto **DataTableReader** .</span><span class="sxs-lookup"><span data-stu-id="ccb33-110">Discusses how to create a **DataTableReader** object.</span></span>  
  
 [<span data-ttu-id="ccb33-111">Navegando DataTables</span><span class="sxs-lookup"><span data-stu-id="ccb33-111">Navigating DataTables</span></span>](navigating-datatables.md)  
 <span data-ttu-id="ccb33-112">Descreve o uso do método **Read** para percorrer o conteúdo de um **DataTableReader**.</span><span class="sxs-lookup"><span data-stu-id="ccb33-112">Describes the use of the **Read** method to move through the contents of a **DataTableReader**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccb33-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ccb33-113">See also</span></span>

- <span data-ttu-id="ccb33-114">[Retrieving and Modifying Data in ADO.NET](../retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="ccb33-114">[Retrieving and Modifying Data in ADO.NET](../retrieving-and-modifying-data.md)</span></span>
- <span data-ttu-id="ccb33-115">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="ccb33-115">[ADO.NET Overview](../ado-net-overview.md)</span></span>
