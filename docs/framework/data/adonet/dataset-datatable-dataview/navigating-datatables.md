---
title: Navegar DataTables
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 202026a1-ec79-435e-b507-12a77f5011b2
ms.openlocfilehash: 9b7ed4ef1dbe141d8f6a1b6c6b9af2fd89e6c7af
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148302"
---
# <a name="navigating-datatables"></a><span data-ttu-id="f3702-102">Navegar DataTables</span><span class="sxs-lookup"><span data-stu-id="f3702-102">Navigating DataTables</span></span>

<span data-ttu-id="f3702-103">O <xref:System.Data.DataTableReader> obtém o conteúdo de um ou mais objetos <xref:System.Data.DataTable> na forma de um ou mais conjuntos de resultados somente leitura de somente avanço.</span><span class="sxs-lookup"><span data-stu-id="f3702-103">The <xref:System.Data.DataTableReader> obtains the contents of one or more <xref:System.Data.DataTable> objects in the form of one or more read-only, forward-only result sets.</span></span>  
  
 <span data-ttu-id="f3702-104">Um <xref:System.Data.DataTableReader> pode conter vários conjuntos de resultados se ele for criado usando o <xref:System.Data.DataSet.CreateDataReader%2A> método.</span><span class="sxs-lookup"><span data-stu-id="f3702-104">A <xref:System.Data.DataTableReader> may contain multiple result sets if it is created by using the <xref:System.Data.DataSet.CreateDataReader%2A> method.</span></span> <span data-ttu-id="f3702-105">Quando há mais de um conjunto de resultados, o <xref:System.Data.DataTableReader.NextResult%2A> método avança o cursor para o próximo conjunto de resultados.</span><span class="sxs-lookup"><span data-stu-id="f3702-105">When there is more than one result set, the <xref:System.Data.DataTableReader.NextResult%2A> method advances the cursor to the next result set.</span></span> <span data-ttu-id="f3702-106">Esse é um processo somente de encaminhamento.</span><span class="sxs-lookup"><span data-stu-id="f3702-106">This is a forward-only process.</span></span> <span data-ttu-id="f3702-107">Não é possível retornar a um conjunto de resultados anterior.</span><span class="sxs-lookup"><span data-stu-id="f3702-107">It is not possible to return to a previous result set.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3702-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f3702-108">Example</span></span>  

 <span data-ttu-id="f3702-109">No exemplo a seguir, o `TestConstructor` método cria duas <xref:System.Data.DataTable> instâncias.</span><span class="sxs-lookup"><span data-stu-id="f3702-109">In the following example, the `TestConstructor` method creates two <xref:System.Data.DataTable> instances.</span></span> <span data-ttu-id="f3702-110">Para demonstrar esse construtor para a <xref:System.Data.DataTableReader> classe, o exemplo cria um novo **DataTableReader** com base em uma matriz que contém as duas **tabelas**e executa uma operação simples, imprimindo o conteúdo das primeiras colunas na janela do console.</span><span class="sxs-lookup"><span data-stu-id="f3702-110">In order to demonstrate this constructor for the <xref:System.Data.DataTableReader> class, the sample creates a new **DataTableReader** based on an array that contains the two **DataTables**, and performs a simple operation, printing the contents from the first few columns to the console window.</span></span>  
  
 [!code-csharp[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks DataTableReader.NextResult#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTableReader.NextResult/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f3702-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="f3702-111">See also</span></span>

- [<span data-ttu-id="f3702-112">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="f3702-112">DataTableReaders</span></span>](datatablereaders.md)
- [<span data-ttu-id="f3702-113">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f3702-113">ADO.NET Overview</span></span>](../ado-net-overview.md)
