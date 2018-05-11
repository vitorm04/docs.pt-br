---
title: Criando um DataReader
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
ms.openlocfilehash: c5073a553926fdfdd78b0b6837cdc07b58ac7faf
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="creating-a-datareader"></a><span data-ttu-id="eabe2-102">Criando um DataReader</span><span class="sxs-lookup"><span data-stu-id="eabe2-102">Creating a DataReader</span></span>
<span data-ttu-id="eabe2-103">O <xref:System.Data.DataTable> e <xref:System.Data.DataSet> classes têm uma <xref:System.Data.DataTable.CreateDataReader%2A> método que retorna o conteúdo do <xref:System.Data.DataTable> ou o conteúdo do <xref:System.Data.DataSet> do objeto <xref:System.Data.DataSet.Tables%2A> coleção como um ou mais conjuntos de resultados somente leitura, somente encaminhamento.</span><span class="sxs-lookup"><span data-stu-id="eabe2-103">The <xref:System.Data.DataTable> and <xref:System.Data.DataSet> classes have a <xref:System.Data.DataTable.CreateDataReader%2A> method that returns the contents of the <xref:System.Data.DataTable> or the contents of the <xref:System.Data.DataSet> object's <xref:System.Data.DataSet.Tables%2A> collection as one or more read-only, forward-only result sets.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eabe2-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="eabe2-104">Example</span></span>  
 <span data-ttu-id="eabe2-105">O aplicativo de console a seguir cria um <xref:System.Data.DataTable> instância.</span><span class="sxs-lookup"><span data-stu-id="eabe2-105">The following console application creates a <xref:System.Data.DataTable> instance.</span></span> <span data-ttu-id="eabe2-106">O exemplo, em seguida, passa o preenchido <xref:System.Data.DataTable> para um procedimento que chama o <xref:System.Data.DataTable.CreateDataReader%2A> método, que itera através dos resultados contidos a <xref:System.Data.DataTableReader>.</span><span class="sxs-lookup"><span data-stu-id="eabe2-106">The example then passes the filled <xref:System.Data.DataTable> to a procedure that calls the <xref:System.Data.DataTable.CreateDataReader%2A> method, which iterates through the results contained within the <xref:System.Data.DataTableReader>.</span></span>  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 <span data-ttu-id="eabe2-107">O exemplo exibe a seguinte saída na janela do console:</span><span class="sxs-lookup"><span data-stu-id="eabe2-107">The example displays the following output in the console window:</span></span>  
  
```  
1 Mary  
2 Andy  
3 Peter  
4 Russ  
```  
  
## <a name="see-also"></a><span data-ttu-id="eabe2-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eabe2-108">See Also</span></span>  
 <xref:System.Data.DataTable.CreateDataReader%2A>  
 <xref:System.Data.DataSet.CreateDataReader%2A>  
 [<span data-ttu-id="eabe2-109">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="eabe2-109">DataTableReaders</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 <span data-ttu-id="eabe2-110">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="eabe2-110">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
