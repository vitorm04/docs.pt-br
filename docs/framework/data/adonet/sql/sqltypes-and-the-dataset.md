---
title: SqlTypes e DataSet
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 9172c20a-9876-4b3b-9c97-1963c02b1993
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3235581ca3328307396796f01ff728ab798d3ad0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="sqltypes-and-the-dataset"></a><span data-ttu-id="17797-102">SqlTypes e DataSet</span><span class="sxs-lookup"><span data-stu-id="17797-102">SqlTypes and the DataSet</span></span>
<span data-ttu-id="17797-103">O ADO.NET 2.0 introduziu suporte avançado a tipos para `DataSet` por meio do namespace <xref:System.Data.SqlTypes>.</span><span class="sxs-lookup"><span data-stu-id="17797-103">ADO.NET 2.0 introduced enhanced type support for the `DataSet` through the  <xref:System.Data.SqlTypes> namespace.</span></span> <span data-ttu-id="17797-104">Os tipos em <xref:System.Data.SqlTypes> são criados para fornecer tipos de dados com a mesma semântica e precisão que os tipos de dados em um banco de dados do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="17797-104">The types in <xref:System.Data.SqlTypes> are designed to provide data types with the same semantics and precision as the data types in a SQL Server database.</span></span> <span data-ttu-id="17797-105">Cada tipo de dados em <xref:System.Data.SqlTypes> tem um tipo de dados equivalente no SQL Server, com a mesma representação de dados subjacentes.</span><span class="sxs-lookup"><span data-stu-id="17797-105">Each data type in <xref:System.Data.SqlTypes> has an equivalent data type in SQL Server, with the same underlying data representation.</span></span>  
  
 <span data-ttu-id="17797-106">Usar <xref:System.Data.SqlTypes> diretamente em um <xref:System.Data.DataSet> confere vários benefícios no trabalho com tipos de dados do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="17797-106">Using <xref:System.Data.SqlTypes> directly in a <xref:System.Data.DataSet> confers several benefits when working with SQL Server data types.</span></span> <span data-ttu-id="17797-107"><xref:System.Data.SqlTypes> oferece suporte à mesma semântica que os tipos de dados nativos do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="17797-107"><xref:System.Data.SqlTypes> supports the same semantics as SQL Server native data types.</span></span> <span data-ttu-id="17797-108">Especificar um dos <xref:System.Data.SqlTypes> na definição de <xref:System.Data.DataColumn> elimina a perda de precisão que pode ocorrer ao converter tipos de dados decimais ou numéricos em um dos tipos de dados CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="17797-108">Specifying one of the <xref:System.Data.SqlTypes> in the definition of a <xref:System.Data.DataColumn> eliminates the loss of precision that can occur when converting decimal or numeric data types to one of the common language runtime (CLR) data types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17797-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="17797-109">Example</span></span>  
 <span data-ttu-id="17797-110">O exemplo a seguir cria um objeto <xref:System.Data.DataTable>, definindo explicitamente os tipos de dados <xref:System.Data.DataColumn> usando <xref:System.Data.SqlTypes> em vez de tipos CLR.</span><span class="sxs-lookup"><span data-stu-id="17797-110">The following example creates a <xref:System.Data.DataTable> object, explicitly defining the <xref:System.Data.DataColumn> data types by using <xref:System.Data.SqlTypes> instead of CLR types.</span></span> <span data-ttu-id="17797-111">O código preenche <xref:System.Data.DataTable> com dados da tabela Sales.SalesOrderDetail no banco de dados AdventureWorks no SQL Server.</span><span class="sxs-lookup"><span data-stu-id="17797-111">The code fills the <xref:System.Data.DataTable> with data from the Sales.SalesOrderDetail table in the AdventureWorks database in SQL Server.</span></span> <span data-ttu-id="17797-112">A saída exibida na janela do console mostra o tipo de dados de cada coluna e os valores recuperados do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="17797-112">The output displayed in the console window shows the data type of each column, and the values retrieved from SQL Server.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="17797-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="17797-113">See Also</span></span>  
 [<span data-ttu-id="17797-114">Mapeamentos de tipo de dados do SQL Server</span><span class="sxs-lookup"><span data-stu-id="17797-114">SQL Server Data Type Mappings</span></span>](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [<span data-ttu-id="17797-115">Configurando parâmetros e tipos de dados de parâmetro</span><span class="sxs-lookup"><span data-stu-id="17797-115">Configuring Parameters and Parameter Data Types</span></span>](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 <span data-ttu-id="17797-116">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="17797-116">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
