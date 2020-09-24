---
title: 'Como: consultar informações'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
ms.openlocfilehash: d45fdfa8b8976e3cdc86b905443bf7bcea578714
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166398"
---
# <a name="how-to-query-for-information"></a><span data-ttu-id="6f2a0-102">Como: consultar informações</span><span class="sxs-lookup"><span data-stu-id="6f2a0-102">How to: Query for Information</span></span>

<span data-ttu-id="6f2a0-103">As consultas em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] usam a mesma sintaxe que as consultas no LINQ.</span><span class="sxs-lookup"><span data-stu-id="6f2a0-103">Queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] use the same syntax as queries in LINQ.</span></span> <span data-ttu-id="6f2a0-104">A única diferença é que os objetos referenciados em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] consultas são mapeados para elementos em um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="6f2a0-104">The only difference is that the objects referenced in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries are mapped to elements in a database.</span></span> <span data-ttu-id="6f2a0-105">Para obter mais informações, consulte [Introdução a Consultas de LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="6f2a0-105">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="6f2a0-106">converte as consultas que você escreve em consultas SQL equivalentes e as envia para o servidor para processamento.</span><span class="sxs-lookup"><span data-stu-id="6f2a0-106">translates the queries you write into equivalent SQL queries and sends them to the server for processing.</span></span>  
  
 <span data-ttu-id="6f2a0-107">Alguns recursos das consultas do LINQ podem precisar de atenção especial em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplicativos.</span><span class="sxs-lookup"><span data-stu-id="6f2a0-107">Some features of LINQ queries might need special attention in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications.</span></span> <span data-ttu-id="6f2a0-108">Para obter mais informações, consulte [conceitos de consulta](query-concepts.md).</span><span class="sxs-lookup"><span data-stu-id="6f2a0-108">For more information, see [Query Concepts](query-concepts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f2a0-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6f2a0-109">Example</span></span>  

 <span data-ttu-id="6f2a0-110">A consulta a seguir solicita uma lista de clientes de Londres.</span><span class="sxs-lookup"><span data-stu-id="6f2a0-110">The following query asks for a list of customers from London.</span></span> <span data-ttu-id="6f2a0-111">Neste exemplo, `Customers` é uma tabela no banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="6f2a0-111">In this example, `Customers` is a table in the Northwind sample database.</span></span>  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="6f2a0-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="6f2a0-112">See also</span></span>

- [<span data-ttu-id="6f2a0-113">Criando o modelo de objeto</span><span class="sxs-lookup"><span data-stu-id="6f2a0-113">Creating the Object Model</span></span>](creating-the-object-model.md)
- [<span data-ttu-id="6f2a0-114">Baixar bancos de dados de amostra</span><span class="sxs-lookup"><span data-stu-id="6f2a0-114">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="6f2a0-115">Consultando o banco de dados</span><span class="sxs-lookup"><span data-stu-id="6f2a0-115">Querying the Database</span></span>](querying-the-database.md)
