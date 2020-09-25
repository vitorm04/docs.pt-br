---
title: Criar um DataReader
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
ms.openlocfilehash: 3af6ae3a8f4ecc3ec34c186ce55c1c77c27514a9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202325"
---
# <a name="creating-a-datareader"></a><span data-ttu-id="589e6-102">Criar um DataReader</span><span class="sxs-lookup"><span data-stu-id="589e6-102">Creating a DataReader</span></span>

<span data-ttu-id="589e6-103">As <xref:System.Data.DataTable> <xref:System.Data.DataSet> classes e têm um <xref:System.Data.DataTable.CreateDataReader%2A> método que retorna o conteúdo do <xref:System.Data.DataTable> ou o conteúdo da <xref:System.Data.DataSet> coleção do objeto <xref:System.Data.DataSet.Tables%2A> como um ou mais conjuntos de resultados somente de encaminhamento e somente leitura.</span><span class="sxs-lookup"><span data-stu-id="589e6-103">The <xref:System.Data.DataTable> and <xref:System.Data.DataSet> classes have a <xref:System.Data.DataTable.CreateDataReader%2A> method that returns the contents of the <xref:System.Data.DataTable> or the contents of the <xref:System.Data.DataSet> object's <xref:System.Data.DataSet.Tables%2A> collection as one or more read-only, forward-only result sets.</span></span>  
  
## <a name="example"></a><span data-ttu-id="589e6-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="589e6-104">Example</span></span>  

 <span data-ttu-id="589e6-105">O aplicativo de console a seguir cria uma <xref:System.Data.DataTable> instância do.</span><span class="sxs-lookup"><span data-stu-id="589e6-105">The following console application creates a <xref:System.Data.DataTable> instance.</span></span> <span data-ttu-id="589e6-106">Em seguida, o exemplo passa o preenchido <xref:System.Data.DataTable> para um procedimento que chama o <xref:System.Data.DataTable.CreateDataReader%2A> método, que itera pelos resultados contidos no <xref:System.Data.DataTableReader> .</span><span class="sxs-lookup"><span data-stu-id="589e6-106">The example then passes the filled <xref:System.Data.DataTable> to a procedure that calls the <xref:System.Data.DataTable.CreateDataReader%2A> method, which iterates through the results contained within the <xref:System.Data.DataTableReader>.</span></span>  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 <span data-ttu-id="589e6-107">O exemplo exibe a seguinte saída na janela do console:</span><span class="sxs-lookup"><span data-stu-id="589e6-107">The example displays the following output in the console window:</span></span>  
  
```output  
1 Mary  
2 Andy  
3 Peter  
4 Russ  
```  
  
## <a name="see-also"></a><span data-ttu-id="589e6-108">Veja também</span><span class="sxs-lookup"><span data-stu-id="589e6-108">See also</span></span>

- <xref:System.Data.DataTable.CreateDataReader%2A>
- <xref:System.Data.DataSet.CreateDataReader%2A>
- [<span data-ttu-id="589e6-109">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="589e6-109">DataTableReaders</span></span>](datatablereaders.md)
- [<span data-ttu-id="589e6-110">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="589e6-110">ADO.NET Overview</span></span>](../ado-net-overview.md)
