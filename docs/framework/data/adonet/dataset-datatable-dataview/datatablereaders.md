---
title: DataTableReaders
ms.date: 03/30/2017
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
ms.openlocfilehash: a790335a25327563e3dab6093449345b99afd048
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61607859"
---
# <a name="datatablereaders"></a><span data-ttu-id="0137c-102">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="0137c-102">DataTableReaders</span></span>
<span data-ttu-id="0137c-103">O <xref:System.Data.DataTableReader> apresenta o conteúdo de um <xref:System.Data.DataTable> ou um <xref:System.Data.DataSet> na forma de um ou mais resultados de somente leitura, somente encaminhamento define.</span><span class="sxs-lookup"><span data-stu-id="0137c-103">The <xref:System.Data.DataTableReader> presents the contents of a <xref:System.Data.DataTable> or a <xref:System.Data.DataSet> in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="0137c-104">Quando você cria um **DataTableReader** de uma **DataTable**, resultante **DataTableReader** objeto contém um conjunto de resultados com os mesmos dados que o  **DataTable** do qual ele foi criado, exceto para quaisquer linhas que foram marcadas como excluídas.</span><span class="sxs-lookup"><span data-stu-id="0137c-104">When you create a **DataTableReader** from a **DataTable**, the resulting **DataTableReader** object contains one result set with the same data as the **DataTable** from which it was created, except for any rows that have been marked as deleted.</span></span> <span data-ttu-id="0137c-105">As colunas aparecem na mesma ordem como original **DataTable**.</span><span class="sxs-lookup"><span data-stu-id="0137c-105">The columns appear in the same order as in the original **DataTable**.</span></span>  
  
 <span data-ttu-id="0137c-106">Um **DataTableReader** pode conter vários conjuntos de resultados, se ele foi criado chamando <xref:System.Data.DataSet.CreateDataReader%2A>.</span><span class="sxs-lookup"><span data-stu-id="0137c-106">A **DataTableReader** may contain multiple result sets if it was created by calling <xref:System.Data.DataSet.CreateDataReader%2A>.</span></span> <span data-ttu-id="0137c-107">Os resultados estão na mesma ordem que o **DataTables** na **DataSet** do objeto <xref:System.Data.DataSet.Tables%2A> coleção.</span><span class="sxs-lookup"><span data-stu-id="0137c-107">The results are in the same order as the **DataTables** in the **DataSet** object's <xref:System.Data.DataSet.Tables%2A> collection.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0137c-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="0137c-108">In This Section</span></span>  
 [<span data-ttu-id="0137c-109">Criando um DataReader</span><span class="sxs-lookup"><span data-stu-id="0137c-109">Creating a DataReader</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datareader.md)  
 <span data-ttu-id="0137c-110">Discute como criar uma **DataTableReader** objeto.</span><span class="sxs-lookup"><span data-stu-id="0137c-110">Discusses how to create a **DataTableReader** object.</span></span>  
  
 [<span data-ttu-id="0137c-111">Navegando DataTables</span><span class="sxs-lookup"><span data-stu-id="0137c-111">Navigating DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datatables.md)  
 <span data-ttu-id="0137c-112">Descreve o uso do **leitura** método para mover o conteúdo de um **DataTableReader**.</span><span class="sxs-lookup"><span data-stu-id="0137c-112">Describes the use of the **Read** method to move through the contents of a **DataTableReader**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0137c-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0137c-113">See also</span></span>

- <span data-ttu-id="0137c-114">[Retrieving and Modifying Data in ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="0137c-114">[Retrieving and Modifying Data in ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)</span></span>
- <span data-ttu-id="0137c-115">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="0137c-115">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
