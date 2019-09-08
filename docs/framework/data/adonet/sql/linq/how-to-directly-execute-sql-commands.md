---
title: 'Como: executar comandos SQL diretamente'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 04671bb0-40c0-4465-86e5-77986f454661
ms.openlocfilehash: 3f28351a29915bebd698e00113bb05647d8412b4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781989"
---
# <a name="how-to-directly-execute-sql-commands"></a><span data-ttu-id="619fd-102">Como: executar comandos SQL diretamente</span><span class="sxs-lookup"><span data-stu-id="619fd-102">How to: Directly Execute SQL Commands</span></span>
<span data-ttu-id="619fd-103">Presumindo uma conexão de <xref:System.Data.Linq.DataContext>, você pode usar o <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> para executar comandos SQL que não retornam objetos.</span><span class="sxs-lookup"><span data-stu-id="619fd-103">Assuming a <xref:System.Data.Linq.DataContext> connection, you can use <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> to execute SQL commands that do not return objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="619fd-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="619fd-104">Example</span></span>  
 <span data-ttu-id="619fd-105">O exemplo a seguir faz o SQL Server aumentar o UnitPrice em 1,00.</span><span class="sxs-lookup"><span data-stu-id="619fd-105">The following example causes SQL Server to increase UnitPrice by 1.00.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#3)]
 [!code-vb[DLinqCommunicatingWithDatabase#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="619fd-106">Consulte também</span><span class="sxs-lookup"><span data-stu-id="619fd-106">See also</span></span>

- [<span data-ttu-id="619fd-107">Como: Executar consultas SQL diretamente</span><span class="sxs-lookup"><span data-stu-id="619fd-107">How to: Directly Execute SQL Queries</span></span>](how-to-directly-execute-sql-queries.md)
- [<span data-ttu-id="619fd-108">Comunicação com o banco de dados</span><span class="sxs-lookup"><span data-stu-id="619fd-108">Communicating with the Database</span></span>](communicating-with-the-database.md)
