---
title: Navegar DataTables
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 202026a1-ec79-435e-b507-12a77f5011b2
ms.openlocfilehash: 91db42acb0e09b8fc99b0ee710a60800d40938ce
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59112847"
---
# <a name="navigating-datatables"></a><span data-ttu-id="00257-102">Navegar DataTables</span><span class="sxs-lookup"><span data-stu-id="00257-102">Navigating DataTables</span></span>
<span data-ttu-id="00257-103">O <xref:System.Data.DataTableReader> obtém o conteúdo de um ou mais objetos <xref:System.Data.DataTable> na forma de um ou mais conjuntos de resultados somente leitura de somente avanço.</span><span class="sxs-lookup"><span data-stu-id="00257-103">The <xref:System.Data.DataTableReader> obtains the contents of one or more <xref:System.Data.DataTable> objects in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="00257-104">Um <xref:System.Data.DataTableReader> pode conter vários conjuntos de resultados, se ela for criada usando o <xref:System.Data.DataSet.CreateDataReader%2A> método.</span><span class="sxs-lookup"><span data-stu-id="00257-104">A <xref:System.Data.DataTableReader> may contain multiple result sets if it is created by using the <xref:System.Data.DataSet.CreateDataReader%2A> method.</span></span> <span data-ttu-id="00257-105">Quando há mais de um conjunto de resultados, o <xref:System.Data.DataTableReader.NextResult%2A> método avança o cursor para o próximo conjunto de resultados.</span><span class="sxs-lookup"><span data-stu-id="00257-105">When there is more than one result set, the <xref:System.Data.DataTableReader.NextResult%2A> method advances the cursor to the next result set.</span></span> <span data-ttu-id="00257-106">Esse é um processo de somente avanço.</span><span class="sxs-lookup"><span data-stu-id="00257-106">This is a forward-only process.</span></span> <span data-ttu-id="00257-107">Não é possível retornar a um conjunto de resultados anteriores.</span><span class="sxs-lookup"><span data-stu-id="00257-107">It is not possible to return to a previous result set.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00257-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="00257-108">Example</span></span>  
 <span data-ttu-id="00257-109">No exemplo a seguir, o `TestConstructor` método cria dois <xref:System.Data.DataTable> instâncias.</span><span class="sxs-lookup"><span data-stu-id="00257-109">In the following example, the `TestConstructor` method creates two <xref:System.Data.DataTable> instances.</span></span> <span data-ttu-id="00257-110">Para demonstrar esse construtor para o <xref:System.Data.DataTableReader> classe, o exemplo cria um novo **DataTableReader** com base em uma matriz que contém os dois **DataTables**e executa uma operação simple, Imprimir o conteúdo de algumas colunas primeiro à janela do console.</span><span class="sxs-lookup"><span data-stu-id="00257-110">In order to demonstrate this constructor for the <xref:System.Data.DataTableReader> class, the sample creates a new **DataTableReader** based on an array that contains the two **DataTables**, and performs a simple operation, printing the contents from the first few columns to the console window.</span></span>  
  
 [!code-csharp[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="00257-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="00257-111">See also</span></span>

- [<span data-ttu-id="00257-112">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="00257-112">DataTableReaders</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)
- [<span data-ttu-id="00257-113">Central de desenvolvedores de provedores gerenciados ADO.NET e DataSet</span><span class="sxs-lookup"><span data-stu-id="00257-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
