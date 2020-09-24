---
title: SqlTypes e DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9172c20a-9876-4b3b-9c97-1963c02b1993
ms.openlocfilehash: 04f95cd7d3f6e52f644f23dd8a32c77d56a5ddda
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147502"
---
# <a name="sqltypes-and-the-dataset"></a><span data-ttu-id="5062a-102">SqlTypes e DataSet</span><span class="sxs-lookup"><span data-stu-id="5062a-102">SqlTypes and the DataSet</span></span>

<span data-ttu-id="5062a-103">O ADO.NET 2.0 introduziu a compatibilidade com tipo avançada para `DataSet` por meio do namespace <xref:System.Data.SqlTypes>.</span><span class="sxs-lookup"><span data-stu-id="5062a-103">ADO.NET 2.0 introduced enhanced type support for the `DataSet` through the  <xref:System.Data.SqlTypes> namespace.</span></span> <span data-ttu-id="5062a-104">Os tipos em <xref:System.Data.SqlTypes> são projetados para fornecer tipos de dados com a mesma semântica e precisão que os tipos de dados em um banco de dados SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5062a-104">The types in <xref:System.Data.SqlTypes> are designed to provide data types with the same semantics and precision as the data types in a SQL Server database.</span></span> <span data-ttu-id="5062a-105">Cada tipo de dados no <xref:System.Data.SqlTypes> tem um tipo de dados equivalente em SQL Server, com a mesma representação de dados subjacente.</span><span class="sxs-lookup"><span data-stu-id="5062a-105">Each data type in <xref:System.Data.SqlTypes> has an equivalent data type in SQL Server, with the same underlying data representation.</span></span>  
  
 <span data-ttu-id="5062a-106">Usar <xref:System.Data.SqlTypes> diretamente em um <xref:System.Data.DataSet> confere vários benefícios ao trabalhar com tipos de dados do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5062a-106">Using <xref:System.Data.SqlTypes> directly in a <xref:System.Data.DataSet> confers several benefits when working with SQL Server data types.</span></span> <span data-ttu-id="5062a-107"><xref:System.Data.SqlTypes> é compatível com a mesma semântica que os tipos de dados nativos do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5062a-107"><xref:System.Data.SqlTypes> supports the same semantics as SQL Server native data types.</span></span> <span data-ttu-id="5062a-108">A especificação de um dos <xref:System.Data.SqlTypes> na definição de um <xref:System.Data.DataColumn> elimina a perda de precisão que pode ocorrer ao converter tipos de dados decimais ou numéricos em um dos tipos de dados de CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="5062a-108">Specifying one of the <xref:System.Data.SqlTypes> in the definition of a <xref:System.Data.DataColumn> eliminates the loss of precision that can occur when converting decimal or numeric data types to one of the common language runtime (CLR) data types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5062a-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5062a-109">Example</span></span>  

 <span data-ttu-id="5062a-110">O exemplo a seguir cria um objeto <xref:System.Data.DataTable>, definindo explicitamente os tipos de dados de <xref:System.Data.DataColumn> usando <xref:System.Data.SqlTypes> em vez de tipos CLR.</span><span class="sxs-lookup"><span data-stu-id="5062a-110">The following example creates a <xref:System.Data.DataTable> object, explicitly defining the <xref:System.Data.DataColumn> data types by using <xref:System.Data.SqlTypes> instead of CLR types.</span></span> <span data-ttu-id="5062a-111">O código preenche a <xref:System.Data.DataTable> com os dados da tabela Sales.SalesOrderDetail no banco de dados AdventureWorks no SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5062a-111">The code fills the <xref:System.Data.DataTable> with data from the Sales.SalesOrderDetail table in the AdventureWorks database in SQL Server.</span></span> <span data-ttu-id="5062a-112">A saída exibida na janela do console mostra o tipo de dados de cada coluna e os valores recuperados do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5062a-112">The output displayed in the console window shows the data type of each column, and the values retrieved from SQL Server.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="5062a-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="5062a-113">See also</span></span>

- [<span data-ttu-id="5062a-114">Mapeamentos de tipos de dados do SQL Server</span><span class="sxs-lookup"><span data-stu-id="5062a-114">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="5062a-115">Configurar parâmetros e tipos de dados de parâmetro</span><span class="sxs-lookup"><span data-stu-id="5062a-115">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="5062a-116">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5062a-116">ADO.NET Overview</span></span>](../ado-net-overview.md)
