---
title: Várias operações de cópia em massa
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5ad12f94-7459-4a93-a421-4160d1a90715
ms.openlocfilehash: 267103e7315e337d223ce60652bdfddedbe4ec02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358122"
---
# <a name="multiple-bulk-copy-operations"></a><span data-ttu-id="eeadc-102">Várias operações de cópia em massa</span><span class="sxs-lookup"><span data-stu-id="eeadc-102">Multiple Bulk Copy Operations</span></span>
<span data-ttu-id="eeadc-103">Você pode executar várias operações de cópia em massa usando uma única instância de um <xref:System.Data.SqlClient.SqlBulkCopy> classe.</span><span class="sxs-lookup"><span data-stu-id="eeadc-103">You can perform multiple bulk copy operations using a single instance of a <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span> <span data-ttu-id="eeadc-104">Se os parâmetros de operação alterar entre as cópias (por exemplo, o nome da tabela de destino), você deve atualizá-los antes de qualquer chamada subsequente para qualquer uma da **WriteToServer** métodos, como demonstrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="eeadc-104">If the operation parameters change between copies (for example, the name of the destination table), you must update them prior to any subsequent calls to any of the **WriteToServer** methods, as demonstrated in the following example.</span></span> <span data-ttu-id="eeadc-105">A menos que explicitamente alterado, todos os valores de propriedade permanecem como estavam na operação de cópia em massa anterior para uma determinada instância.</span><span class="sxs-lookup"><span data-stu-id="eeadc-105">Unless explicitly changed, all property values remain the same as they were on the previous bulk copy operation for a given instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eeadc-106">Executar várias operações de cópia em massa usando a mesma instância de <xref:System.Data.SqlClient.SqlBulkCopy> é geralmente mais eficiente do que usar uma instância separada para cada operação.</span><span class="sxs-lookup"><span data-stu-id="eeadc-106">Performing multiple bulk copy operations using the same instance of <xref:System.Data.SqlClient.SqlBulkCopy> is usually more efficient than using a separate instance for each operation.</span></span>  
  
 <span data-ttu-id="eeadc-107">Se você executar várias operações de cópia em massa usando a mesma <xref:System.Data.SqlClient.SqlBulkCopy> do objeto, não existem restrições em se as informações de origem ou de destino forem iguais ou diferentes em cada operação.</span><span class="sxs-lookup"><span data-stu-id="eeadc-107">If you perform several bulk copy operations using the same <xref:System.Data.SqlClient.SqlBulkCopy> object, there are no restrictions on whether source or target information is equal or different in each operation.</span></span> <span data-ttu-id="eeadc-108">No entanto, você deve garantir que as informações de associação de coluna estão definidas corretamente cada vez que você grava para o servidor.</span><span class="sxs-lookup"><span data-stu-id="eeadc-108">However, you must ensure that column association information is properly set each time you write to the server.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="eeadc-109">Este exemplo não funcionará a menos que você criou as tabelas de trabalho conforme descrito em [configuração de exemplo de cópia em massa](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md).</span><span class="sxs-lookup"><span data-stu-id="eeadc-109">This sample will not run unless you have created the work tables as described in [Bulk Copy Example Setup](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md).</span></span> <span data-ttu-id="eeadc-110">Esse código é fornecido para demonstrar a sintaxe para usar **SqlBulkCopy** somente.</span><span class="sxs-lookup"><span data-stu-id="eeadc-110">This code is provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="eeadc-111">Se as tabelas de origem e destino estão localizadas na mesma instância do SQL Server, é mais fácil e rápido para usar um Transact-SQL `INSERT … SELECT` instrução para copiar os dados.</span><span class="sxs-lookup"><span data-stu-id="eeadc-111">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
 [!code-csharp[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="eeadc-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eeadc-112">See Also</span></span>  
 [<span data-ttu-id="eeadc-113">Operações de cópia em massa no SQL Server</span><span class="sxs-lookup"><span data-stu-id="eeadc-113">Bulk Copy Operations in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)  
 <span data-ttu-id="eeadc-114">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="eeadc-114">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
