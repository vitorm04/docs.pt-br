---
title: Criando um DataReader
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
ms.openlocfilehash: d3c20fa4394b09e9ceec332d430ed638166bed8e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491657"
---
# <a name="creating-a-datareader"></a><span data-ttu-id="28317-102">Criando um DataReader</span><span class="sxs-lookup"><span data-stu-id="28317-102">Creating a DataReader</span></span>
<span data-ttu-id="28317-103">O <xref:System.Data.DataTable> e <xref:System.Data.DataSet> classes têm uma <xref:System.Data.DataTable.CreateDataReader%2A> método que retorna o conteúdo dos <xref:System.Data.DataTable> ou o conteúdo da <xref:System.Data.DataSet> do objeto <xref:System.Data.DataSet.Tables%2A> coleção como um ou mais conjuntos de resultados somente leitura, somente encaminhamento.</span><span class="sxs-lookup"><span data-stu-id="28317-103">The <xref:System.Data.DataTable> and <xref:System.Data.DataSet> classes have a <xref:System.Data.DataTable.CreateDataReader%2A> method that returns the contents of the <xref:System.Data.DataTable> or the contents of the <xref:System.Data.DataSet> object's <xref:System.Data.DataSet.Tables%2A> collection as one or more read-only, forward-only result sets.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28317-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="28317-104">Example</span></span>  
 <span data-ttu-id="28317-105">O aplicativo de console a seguir cria um <xref:System.Data.DataTable> instância.</span><span class="sxs-lookup"><span data-stu-id="28317-105">The following console application creates a <xref:System.Data.DataTable> instance.</span></span> <span data-ttu-id="28317-106">O exemplo, em seguida, passa o preenchido <xref:System.Data.DataTable> para um procedimento que chama o <xref:System.Data.DataTable.CreateDataReader%2A> método, que itera pelos resultados da contidos o <xref:System.Data.DataTableReader>.</span><span class="sxs-lookup"><span data-stu-id="28317-106">The example then passes the filled <xref:System.Data.DataTable> to a procedure that calls the <xref:System.Data.DataTable.CreateDataReader%2A> method, which iterates through the results contained within the <xref:System.Data.DataTableReader>.</span></span>  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 <span data-ttu-id="28317-107">O exemplo exibe a seguinte saída na janela do console:</span><span class="sxs-lookup"><span data-stu-id="28317-107">The example displays the following output in the console window:</span></span>  
  
```  
1 Mary  
2 Andy  
3 Peter  
4 Russ  
```  
  
## <a name="see-also"></a><span data-ttu-id="28317-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="28317-108">See also</span></span>
- <xref:System.Data.DataTable.CreateDataReader%2A>
- <xref:System.Data.DataSet.CreateDataReader%2A>
- [<span data-ttu-id="28317-109">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="28317-109">DataTableReaders</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)
- <span data-ttu-id="28317-110">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="28317-110">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
