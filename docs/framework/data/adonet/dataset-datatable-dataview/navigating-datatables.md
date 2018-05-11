---
title: Navegando DataTables
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 202026a1-ec79-435e-b507-12a77f5011b2
ms.openlocfilehash: 3bd10694512e828354254588361cc009aac6602f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="navigating-datatables"></a><span data-ttu-id="43e51-102">Navegando DataTables</span><span class="sxs-lookup"><span data-stu-id="43e51-102">Navigating DataTables</span></span>
<span data-ttu-id="43e51-103">O <xref:System.Data.DataTableReader> obtém o conteúdo de um ou mais objetos <xref:System.Data.DataTable> na forma de um ou mais conjuntos de resultados somente leitura de somente avanço.</span><span class="sxs-lookup"><span data-stu-id="43e51-103">The <xref:System.Data.DataTableReader> obtains the contents of one or more <xref:System.Data.DataTable> objects in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="43e51-104">Um <xref:System.Data.DataTableReader> pode conter vários conjuntos de resultados se ela for criada usando o <xref:System.Data.DataSet.CreateDataReader%2A> método.</span><span class="sxs-lookup"><span data-stu-id="43e51-104">A <xref:System.Data.DataTableReader> may contain multiple result sets if it is created by using the <xref:System.Data.DataSet.CreateDataReader%2A> method.</span></span> <span data-ttu-id="43e51-105">Quando há mais de um conjunto de resultados, o <xref:System.Data.DataTableReader.NextResult%2A> método avança o cursor para o próximo conjunto de resultados.</span><span class="sxs-lookup"><span data-stu-id="43e51-105">When there is more than one result set, the <xref:System.Data.DataTableReader.NextResult%2A> method advances the cursor to the next result set.</span></span> <span data-ttu-id="43e51-106">Esse é um processo de somente avanço.</span><span class="sxs-lookup"><span data-stu-id="43e51-106">This is a forward-only process.</span></span> <span data-ttu-id="43e51-107">Não é possível retornar a um conjunto de resultados anterior.</span><span class="sxs-lookup"><span data-stu-id="43e51-107">It is not possible to return to a previous result set.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43e51-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="43e51-108">Example</span></span>  
 <span data-ttu-id="43e51-109">No exemplo a seguir, o `TestConstructor` método cria dois <xref:System.Data.DataTable> instâncias.</span><span class="sxs-lookup"><span data-stu-id="43e51-109">In the following example, the `TestConstructor` method creates two <xref:System.Data.DataTable> instances.</span></span> <span data-ttu-id="43e51-110">Para demonstrar a este construtor para o <xref:System.Data.DataTableReader> classe, o exemplo cria um novo **DataTableReader** com base em uma matriz que contém os dois **DataTables**e executa uma operação simples, Imprimir o conteúdo de algumas colunas primeiro para a janela do console.</span><span class="sxs-lookup"><span data-stu-id="43e51-110">In order to demonstrate this constructor for the <xref:System.Data.DataTableReader> class, the sample creates a new **DataTableReader** based on an array that contains the two **DataTables**, and performs a simple operation, printing the contents from the first few columns to the console window.</span></span>  
  
 [!code-csharp[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="43e51-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43e51-111">See Also</span></span>  
 [<span data-ttu-id="43e51-112">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="43e51-112">DataTableReaders</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 <span data-ttu-id="43e51-113">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="43e51-113">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
