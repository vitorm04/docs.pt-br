---
title: 'Como: consultar informações'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
ms.openlocfilehash: aedf89f1e570b34d31050fabb91842cefe351488
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033729"
---
# <a name="how-to-query-for-information"></a><span data-ttu-id="b2635-102">Como: consultar informações</span><span class="sxs-lookup"><span data-stu-id="b2635-102">How to: Query for Information</span></span>
<span data-ttu-id="b2635-103">As consultas em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] usam a mesma sintaxe que consultas em [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b2635-103">Queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] use the same syntax as queries in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span> <span data-ttu-id="b2635-104">A única diferença é que os objetos referenciados em [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] consultas são mapeadas para elementos em um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="b2635-104">The only difference is that the objects referenced in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries are mapped to elements in a database.</span></span> <span data-ttu-id="b2635-105">Para obter mais informações, consulte [Introdução a Consultas de LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="b2635-105">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="b2635-106">converte as consultas que você escreve em consultas SQL equivalentes e as envia para o servidor para processamento.</span><span class="sxs-lookup"><span data-stu-id="b2635-106">translates the queries you write into equivalent SQL queries and sends them to the server for processing.</span></span>  
  
 <span data-ttu-id="b2635-107">Alguns recursos de consultas [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] podem precisar de atenção especial em aplicativos [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b2635-107">Some features of [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] queries might need special attention in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications.</span></span> <span data-ttu-id="b2635-108">Para obter mais informações, consulte [conceitos de consulta](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md).</span><span class="sxs-lookup"><span data-stu-id="b2635-108">For more information, see [Query Concepts](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2635-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b2635-109">Example</span></span>  
 <span data-ttu-id="b2635-110">A consulta a seguir solicita uma lista de clientes de Londres.</span><span class="sxs-lookup"><span data-stu-id="b2635-110">The following query asks for a list of customers from London.</span></span> <span data-ttu-id="b2635-111">Neste exemplo, `Customers` é uma tabela no banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="b2635-111">In this example, `Customers` is a table in the Northwind sample database.</span></span>  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b2635-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b2635-112">See also</span></span>

- [<span data-ttu-id="b2635-113">Criando o modelo de objeto</span><span class="sxs-lookup"><span data-stu-id="b2635-113">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
- <span data-ttu-id="b2635-114">[Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md) (Baixando bancos de dados de amostra)</span><span class="sxs-lookup"><span data-stu-id="b2635-114">[Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)</span></span>
- [<span data-ttu-id="b2635-115">Consultando o banco de dados</span><span class="sxs-lookup"><span data-stu-id="b2635-115">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
