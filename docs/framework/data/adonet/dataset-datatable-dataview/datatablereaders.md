---
title: DataTableReaders
ms.date: 03/30/2017
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
ms.openlocfilehash: 1ff7868b59c6fdc4e6c443be1b831accc84f36a6
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203823"
---
# <a name="datatablereaders"></a><span data-ttu-id="ce8f7-102">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="ce8f7-102">DataTableReaders</span></span>
<span data-ttu-id="ce8f7-103">O <xref:System.Data.DataTableReader> apresenta o conteúdo de um <xref:System.Data.DataTable> ou <xref:System.Data.DataSet> de um no formato de um ou mais conjuntos de resultados somente de encaminhamento e somente leitura.</span><span class="sxs-lookup"><span data-stu-id="ce8f7-103">The <xref:System.Data.DataTableReader> presents the contents of a <xref:System.Data.DataTable> or a <xref:System.Data.DataSet> in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="ce8f7-104">Quando você cria um **DataTableReader** a partir de uma **DataTable**, o objeto **DataTableReader** resultante contém um conjunto de resultados com os mesmos dados que a **DataTable** da qual foi criado, exceto para todas as linhas que foram marcadas como excluí.</span><span class="sxs-lookup"><span data-stu-id="ce8f7-104">When you create a **DataTableReader** from a **DataTable**, the resulting **DataTableReader** object contains one result set with the same data as the **DataTable** from which it was created, except for any rows that have been marked as deleted.</span></span> <span data-ttu-id="ce8f7-105">As colunas aparecem na mesma ordem que na **DataTable**original.</span><span class="sxs-lookup"><span data-stu-id="ce8f7-105">The columns appear in the same order as in the original **DataTable**.</span></span>  
  
 <span data-ttu-id="ce8f7-106">Um **DataTableReader** pode conter vários conjuntos de resultados se ele foi criado chamando <xref:System.Data.DataSet.CreateDataReader%2A>.</span><span class="sxs-lookup"><span data-stu-id="ce8f7-106">A **DataTableReader** may contain multiple result sets if it was created by calling <xref:System.Data.DataSet.CreateDataReader%2A>.</span></span> <span data-ttu-id="ce8f7-107">Os resultados estão na mesma ordem que as **tabelas de tabela** na coleção do <xref:System.Data.DataSet.Tables%2A> objeto DataSet.</span><span class="sxs-lookup"><span data-stu-id="ce8f7-107">The results are in the same order as the **DataTables** in the **DataSet** object's <xref:System.Data.DataSet.Tables%2A> collection.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ce8f7-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="ce8f7-108">In This Section</span></span>  
 [<span data-ttu-id="ce8f7-109">Criando um DataReader</span><span class="sxs-lookup"><span data-stu-id="ce8f7-109">Creating a DataReader</span></span>](creating-a-datareader.md)  
 <span data-ttu-id="ce8f7-110">Discute como criar um objeto **DataTableReader** .</span><span class="sxs-lookup"><span data-stu-id="ce8f7-110">Discusses how to create a **DataTableReader** object.</span></span>  
  
 [<span data-ttu-id="ce8f7-111">Navegando DataTables</span><span class="sxs-lookup"><span data-stu-id="ce8f7-111">Navigating DataTables</span></span>](navigating-datatables.md)  
 <span data-ttu-id="ce8f7-112">Descreve o uso do método **Read** para percorrer o conteúdo de um **DataTableReader**.</span><span class="sxs-lookup"><span data-stu-id="ce8f7-112">Describes the use of the **Read** method to move through the contents of a **DataTableReader**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce8f7-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ce8f7-113">See also</span></span>

- <span data-ttu-id="ce8f7-114">[Retrieving and Modifying Data in ADO.NET](../retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="ce8f7-114">[Retrieving and Modifying Data in ADO.NET](../retrieving-and-modifying-data.md)</span></span>
- <span data-ttu-id="ce8f7-115">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="ce8f7-115">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
