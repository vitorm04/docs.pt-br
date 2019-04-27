---
title: 'Como: executar comandos SQL diretamente'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 04671bb0-40c0-4465-86e5-77986f454661
ms.openlocfilehash: eeac6272f176ac8e780b72b0076d032ad9e8f108
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61903221"
---
# <a name="how-to-directly-execute-sql-commands"></a><span data-ttu-id="d5303-102">Como: executar comandos SQL diretamente</span><span class="sxs-lookup"><span data-stu-id="d5303-102">How to: Directly Execute SQL Commands</span></span>
<span data-ttu-id="d5303-103">Presumindo uma conexão de <xref:System.Data.Linq.DataContext>, você pode usar o <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> para executar comandos SQL que não retornam objetos.</span><span class="sxs-lookup"><span data-stu-id="d5303-103">Assuming a <xref:System.Data.Linq.DataContext> connection, you can use <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> to execute SQL commands that do not return objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5303-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d5303-104">Example</span></span>  
 <span data-ttu-id="d5303-105">O exemplo a seguir faz o SQL Server aumentar o UnitPrice em 1,00.</span><span class="sxs-lookup"><span data-stu-id="d5303-105">The following example causes SQL Server to increase UnitPrice by 1.00.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#3)]
 [!code-vb[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="d5303-106">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d5303-106">See also</span></span>

- [<span data-ttu-id="d5303-107">Como: Executar consultas SQL diretamente</span><span class="sxs-lookup"><span data-stu-id="d5303-107">How to: Directly Execute SQL Queries</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-directly-execute-sql-queries.md)
- [<span data-ttu-id="d5303-108">Comunicação com o banco de dados</span><span class="sxs-lookup"><span data-stu-id="d5303-108">Communicating with the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
