---
title: Várias operações de cópia em massa
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5ad12f94-7459-4a93-a421-4160d1a90715
ms.openlocfilehash: 838f56311f165c99c71cc734576bbdb53a946b7c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792071"
---
# <a name="multiple-bulk-copy-operations"></a><span data-ttu-id="ec363-102">Várias operações de cópia em massa</span><span class="sxs-lookup"><span data-stu-id="ec363-102">Multiple Bulk Copy Operations</span></span>
<span data-ttu-id="ec363-103">Você pode executar várias operações de cópia em massa usando uma única instância <xref:System.Data.SqlClient.SqlBulkCopy> de uma classe.</span><span class="sxs-lookup"><span data-stu-id="ec363-103">You can perform multiple bulk copy operations using a single instance of a <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span> <span data-ttu-id="ec363-104">Se os parâmetros de operação forem alterados entre cópias (por exemplo, o nome da tabela de destino), você deverá atualizá-los antes de qualquer chamada subsequente para qualquer um dos métodos **WriteToServer** , conforme demonstrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ec363-104">If the operation parameters change between copies (for example, the name of the destination table), you must update them prior to any subsequent calls to any of the **WriteToServer** methods, as demonstrated in the following example.</span></span> <span data-ttu-id="ec363-105">A menos que seja alterado explicitamente, todos os valores de propriedade permanecem os mesmos que estavam na operação de cópia em massa anterior para uma determinada instância.</span><span class="sxs-lookup"><span data-stu-id="ec363-105">Unless explicitly changed, all property values remain the same as they were on the previous bulk copy operation for a given instance.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ec363-106">Executar várias operações de cópia em massa usando a mesma <xref:System.Data.SqlClient.SqlBulkCopy> instância do é geralmente mais eficiente do que usar uma instância separada para cada operação.</span><span class="sxs-lookup"><span data-stu-id="ec363-106">Performing multiple bulk copy operations using the same instance of <xref:System.Data.SqlClient.SqlBulkCopy> is usually more efficient than using a separate instance for each operation.</span></span>  
  
 <span data-ttu-id="ec363-107">Se você executar várias operações de cópia em massa usando <xref:System.Data.SqlClient.SqlBulkCopy> o mesmo objeto, não haverá restrições se as informações de origem ou destino forem iguais ou diferentes em cada operação.</span><span class="sxs-lookup"><span data-stu-id="ec363-107">If you perform several bulk copy operations using the same <xref:System.Data.SqlClient.SqlBulkCopy> object, there are no restrictions on whether source or target information is equal or different in each operation.</span></span> <span data-ttu-id="ec363-108">No entanto, você deve garantir que as informações de associação de coluna sejam definidas corretamente cada vez que você gravar no servidor.</span><span class="sxs-lookup"><span data-stu-id="ec363-108">However, you must ensure that column association information is properly set each time you write to the server.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ec363-109">Este exemplo não será executado a menos que você tenha criado as tabelas de trabalho conforme descrito em [configuração de exemplo de cópia em massa](bulk-copy-example-setup.md).</span><span class="sxs-lookup"><span data-stu-id="ec363-109">This sample will not run unless you have created the work tables as described in [Bulk Copy Example Setup](bulk-copy-example-setup.md).</span></span> <span data-ttu-id="ec363-110">Esse código é fornecido para demonstrar a sintaxe somente para uso de **SqlBulkCopy** .</span><span class="sxs-lookup"><span data-stu-id="ec363-110">This code is provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="ec363-111">Se as tabelas de origem e destino estiverem localizadas na mesma instância de SQL Server, será mais fácil e rápido usar uma instrução Transact `INSERT … SELECT` -SQL para copiar os dados.</span><span class="sxs-lookup"><span data-stu-id="ec363-111">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
 [!code-csharp[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ec363-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ec363-112">See also</span></span>

- [<span data-ttu-id="ec363-113">Operações de cópia em massa no SQL Server</span><span class="sxs-lookup"><span data-stu-id="ec363-113">Bulk Copy Operations in SQL Server</span></span>](bulk-copy-operations-in-sql-server.md)
- <span data-ttu-id="ec363-114">[ADO.NET Overview](../ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="ec363-114">[ADO.NET Overview](../ado-net-overview.md)</span></span>
