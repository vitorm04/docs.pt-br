---
title: Criar um DataReader
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49d4422a-7464-4ab8-8ec7-90185fde3ecf
ms.openlocfilehash: 696eb4dfc334390e1968dd317d441f3c987a1f77
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040116"
---
# <a name="creating-a-datareader"></a><span data-ttu-id="a6507-102">Criar um DataReader</span><span class="sxs-lookup"><span data-stu-id="a6507-102">Creating a DataReader</span></span>
<span data-ttu-id="a6507-103">As classes <xref:System.Data.DataTable> e <xref:System.Data.DataSet> têm um método <xref:System.Data.DataTable.CreateDataReader%2A> que retorna o conteúdo do <xref:System.Data.DataTable> ou o conteúdo da coleção <xref:System.Data.DataSet> do objeto <xref:System.Data.DataSet.Tables%2A> como um ou mais conjuntos de resultados somente de encaminhamento e somente leitura.</span><span class="sxs-lookup"><span data-stu-id="a6507-103">The <xref:System.Data.DataTable> and <xref:System.Data.DataSet> classes have a <xref:System.Data.DataTable.CreateDataReader%2A> method that returns the contents of the <xref:System.Data.DataTable> or the contents of the <xref:System.Data.DataSet> object's <xref:System.Data.DataSet.Tables%2A> collection as one or more read-only, forward-only result sets.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6507-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a6507-104">Example</span></span>  
 <span data-ttu-id="a6507-105">O aplicativo de console a seguir cria uma instância de <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="a6507-105">The following console application creates a <xref:System.Data.DataTable> instance.</span></span> <span data-ttu-id="a6507-106">Em seguida, o exemplo passa o <xref:System.Data.DataTable> preenchido para um procedimento que chama o método <xref:System.Data.DataTable.CreateDataReader%2A>, que itera pelos resultados contidos no <xref:System.Data.DataTableReader>.</span><span class="sxs-lookup"><span data-stu-id="a6507-106">The example then passes the filled <xref:System.Data.DataTable> to a procedure that calls the <xref:System.Data.DataTable.CreateDataReader%2A> method, which iterates through the results contained within the <xref:System.Data.DataTableReader>.</span></span>  
  
 [!code-csharp[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.CreateDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.CreateDataReader/VB/source.vb#1)]  
  
 <span data-ttu-id="a6507-107">O exemplo exibe a seguinte saída na janela do console:</span><span class="sxs-lookup"><span data-stu-id="a6507-107">The example displays the following output in the console window:</span></span>  
  
```output  
1 Mary  
2 Andy  
3 Peter  
4 Russ  
```  
  
## <a name="see-also"></a><span data-ttu-id="a6507-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a6507-108">See also</span></span>

- <xref:System.Data.DataTable.CreateDataReader%2A>
- <xref:System.Data.DataSet.CreateDataReader%2A>
- [<span data-ttu-id="a6507-109">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="a6507-109">DataTableReaders</span></span>](datatablereaders.md)
- <span data-ttu-id="a6507-110">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="a6507-110">[ADO.NET Overview](../ado-net-overview.md)</span></span>
