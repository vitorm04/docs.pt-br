---
title: Criar um DataReader
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
ms.openlocfilehash: cb39ead1fe15e3bfcf67370e4675dcae3bbf9801
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203903"
---
# <a name="creating-a-datareader"></a><span data-ttu-id="463b0-102">Criar um DataReader</span><span class="sxs-lookup"><span data-stu-id="463b0-102">Creating a DataReader</span></span>
<span data-ttu-id="463b0-103">As <xref:System.Data.DataTable> classes <xref:System.Data.DataSet> e têm um <xref:System.Data.DataTable.CreateDataReader%2A> método que retorna o <xref:System.Data.DataSet> conteúdo do <xref:System.Data.DataTable> ou o conteúdo da coleção do <xref:System.Data.DataSet.Tables%2A> objeto como um ou mais conjuntos de resultados somente de encaminhamento e somente leitura.</span><span class="sxs-lookup"><span data-stu-id="463b0-103">The <xref:System.Data.DataTable> and <xref:System.Data.DataSet> classes have a <xref:System.Data.DataTable.CreateDataReader%2A> method that returns the contents of the <xref:System.Data.DataTable> or the contents of the <xref:System.Data.DataSet> object's <xref:System.Data.DataSet.Tables%2A> collection as one or more read-only, forward-only result sets.</span></span>  
  
## <a name="example"></a><span data-ttu-id="463b0-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="463b0-104">Example</span></span>  
 <span data-ttu-id="463b0-105">O aplicativo de console a seguir <xref:System.Data.DataTable> cria uma instância do.</span><span class="sxs-lookup"><span data-stu-id="463b0-105">The following console application creates a <xref:System.Data.DataTable> instance.</span></span> <span data-ttu-id="463b0-106">Em seguida, o exemplo passa <xref:System.Data.DataTable> o preenchido para um procedimento que <xref:System.Data.DataTable.CreateDataReader%2A> chama o método, que itera pelos resultados contidos <xref:System.Data.DataTableReader>no.</span><span class="sxs-lookup"><span data-stu-id="463b0-106">The example then passes the filled <xref:System.Data.DataTable> to a procedure that calls the <xref:System.Data.DataTable.CreateDataReader%2A> method, which iterates through the results contained within the <xref:System.Data.DataTableReader>.</span></span>  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 <span data-ttu-id="463b0-107">O exemplo exibe a seguinte saída na janela do console:</span><span class="sxs-lookup"><span data-stu-id="463b0-107">The example displays the following output in the console window:</span></span>  
  
```  
1 Mary  
2 Andy  
3 Peter  
4 Russ  
```  
  
## <a name="see-also"></a><span data-ttu-id="463b0-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="463b0-108">See also</span></span>

- <xref:System.Data.DataTable.CreateDataReader%2A>
- <xref:System.Data.DataSet.CreateDataReader%2A>
- [<span data-ttu-id="463b0-109">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="463b0-109">DataTableReaders</span></span>](datatablereaders.md)
- <span data-ttu-id="463b0-110">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="463b0-110">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
