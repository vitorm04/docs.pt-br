---
title: 'Como: reutilizar uma conexão entre um comando ADO.NET e um DataContext'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e26c7eb-c18a-43b5-a8f0-28fd8b04b0f0
ms.openlocfilehash: 47e1e45cfe693e3569c343f1058ce2d610af96dd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163144"
---
# <a name="how-to-reuse-a-connection-between-an-adonet-command-and-a-datacontext"></a><span data-ttu-id="6df79-102">Como: reutilizar uma conexão entre um comando ADO.NET e um DataContext</span><span class="sxs-lookup"><span data-stu-id="6df79-102">How to: Reuse a Connection Between an ADO.NET Command and a DataContext</span></span>
<span data-ttu-id="6df79-103">Porque [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] é uma parte do [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] família de tecnologias e se baseia em serviços fornecidos pelo [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)], você pode reutilizar uma conexão entre um [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] comando e um <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="6df79-103">Because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] is a part of the [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] family of technologies and is based on services provided by [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)], you can reuse a connection between an [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] command and a <xref:System.Data.Linq.DataContext>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6df79-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6df79-104">Example</span></span>  
 <span data-ttu-id="6df79-105">O exemplo a seguir mostra como reutilizar a mesma conexão entre um comando de [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] e <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="6df79-105">The following example shows how to reuse the same connection between an [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] command and the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="6df79-106">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6df79-106">See also</span></span>

- [<span data-ttu-id="6df79-107">Informações gerais</span><span class="sxs-lookup"><span data-stu-id="6df79-107">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [<span data-ttu-id="6df79-108">O ADO.NET e LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="6df79-108">ADO.NET and LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/ado-net-and-linq-to-sql.md)
- [<span data-ttu-id="6df79-109">Comunicação com o banco de dados</span><span class="sxs-lookup"><span data-stu-id="6df79-109">Communicating with the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
