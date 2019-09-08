---
title: SqlTypes e DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9172c20a-9876-4b3b-9c97-1963c02b1993
ms.openlocfilehash: dea5a2017479443cb747d31e253c1c83585ddd09
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791490"
---
# <a name="sqltypes-and-the-dataset"></a><span data-ttu-id="c7eaa-102">SqlTypes e DataSet</span><span class="sxs-lookup"><span data-stu-id="c7eaa-102">SqlTypes and the DataSet</span></span>
<span data-ttu-id="c7eaa-103">O ADO.NET 2.0 introduziu suporte avançado a tipos para `DataSet` por meio do namespace <xref:System.Data.SqlTypes>.</span><span class="sxs-lookup"><span data-stu-id="c7eaa-103">ADO.NET 2.0 introduced enhanced type support for the `DataSet` through the  <xref:System.Data.SqlTypes> namespace.</span></span> <span data-ttu-id="c7eaa-104">Os tipos em <xref:System.Data.SqlTypes> são criados para fornecer tipos de dados com a mesma semântica e precisão que os tipos de dados em um banco de dados do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c7eaa-104">The types in <xref:System.Data.SqlTypes> are designed to provide data types with the same semantics and precision as the data types in a SQL Server database.</span></span> <span data-ttu-id="c7eaa-105">Cada tipo de dados em <xref:System.Data.SqlTypes> tem um tipo de dados equivalente no SQL Server, com a mesma representação de dados subjacentes.</span><span class="sxs-lookup"><span data-stu-id="c7eaa-105">Each data type in <xref:System.Data.SqlTypes> has an equivalent data type in SQL Server, with the same underlying data representation.</span></span>  
  
 <span data-ttu-id="c7eaa-106">Usar <xref:System.Data.SqlTypes> diretamente em um <xref:System.Data.DataSet> confere vários benefícios no trabalho com tipos de dados do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c7eaa-106">Using <xref:System.Data.SqlTypes> directly in a <xref:System.Data.DataSet> confers several benefits when working with SQL Server data types.</span></span> <span data-ttu-id="c7eaa-107"><xref:System.Data.SqlTypes> oferece suporte à mesma semântica que os tipos de dados nativos do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c7eaa-107"><xref:System.Data.SqlTypes> supports the same semantics as SQL Server native data types.</span></span> <span data-ttu-id="c7eaa-108">Especificar um dos <xref:System.Data.SqlTypes> na definição de <xref:System.Data.DataColumn> elimina a perda de precisão que pode ocorrer ao converter tipos de dados decimais ou numéricos em um dos tipos de dados CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="c7eaa-108">Specifying one of the <xref:System.Data.SqlTypes> in the definition of a <xref:System.Data.DataColumn> eliminates the loss of precision that can occur when converting decimal or numeric data types to one of the common language runtime (CLR) data types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7eaa-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c7eaa-109">Example</span></span>  
 <span data-ttu-id="c7eaa-110">O exemplo a seguir cria um objeto <xref:System.Data.DataTable>, definindo explicitamente os tipos de dados <xref:System.Data.DataColumn> usando <xref:System.Data.SqlTypes> em vez de tipos CLR.</span><span class="sxs-lookup"><span data-stu-id="c7eaa-110">The following example creates a <xref:System.Data.DataTable> object, explicitly defining the <xref:System.Data.DataColumn> data types by using <xref:System.Data.SqlTypes> instead of CLR types.</span></span> <span data-ttu-id="c7eaa-111">O código preenche <xref:System.Data.DataTable> com dados da tabela Sales.SalesOrderDetail no banco de dados AdventureWorks no SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c7eaa-111">The code fills the <xref:System.Data.DataTable> with data from the Sales.SalesOrderDetail table in the AdventureWorks database in SQL Server.</span></span> <span data-ttu-id="c7eaa-112">A saída exibida na janela do console mostra o tipo de dados de cada coluna e os valores recuperados do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c7eaa-112">The output displayed in the console window shows the data type of each column, and the values retrieved from SQL Server.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c7eaa-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7eaa-113">See also</span></span>

- [<span data-ttu-id="c7eaa-114">Mapeamentos de tipo de dados do SQL Server</span><span class="sxs-lookup"><span data-stu-id="c7eaa-114">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="c7eaa-115">Configurando parâmetros e tipos de dados de parâmetro</span><span class="sxs-lookup"><span data-stu-id="c7eaa-115">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- <span data-ttu-id="c7eaa-116">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="c7eaa-116">[ADO.NET Overview](../ado-net-overview.md)</span></span>
