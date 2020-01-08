---
title: Como conectar-se a um banco de dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c33d74b3-530d-421b-a121-96786dd263a5
ms.openlocfilehash: 837919b1cfcdf46026ccfb37cbbec951c0ae41b8
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634671"
---
# <a name="how-to-connect-to-a-database"></a><span data-ttu-id="64086-102">Como conectar-se a um banco de dados</span><span class="sxs-lookup"><span data-stu-id="64086-102">How to: Connect to a Database</span></span>
<span data-ttu-id="64086-103">O <xref:System.Data.Linq.DataContext> é o principal conduto pelo qual você se conecta a um banco de dados, recupera objetos deles e envia alterações de volta para ele.</span><span class="sxs-lookup"><span data-stu-id="64086-103">The <xref:System.Data.Linq.DataContext> is the main conduit by which you connect to a database, retrieve objects from it, and submit changes back to it.</span></span> <span data-ttu-id="64086-104">Você usa o <xref:System.Data.Linq.DataContext> da mesma maneira que usaria um <xref:System.Data.SqlClient.SqlConnection>ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="64086-104">You use the <xref:System.Data.Linq.DataContext> just as you would use an ADO.NET <xref:System.Data.SqlClient.SqlConnection>.</span></span> <span data-ttu-id="64086-105">Na verdade, o <xref:System.Data.Linq.DataContext> é inicializado com uma conexão ou com uma cadeia de conexão que você fornece.</span><span class="sxs-lookup"><span data-stu-id="64086-105">In fact, the <xref:System.Data.Linq.DataContext> is initialized with a connection or connection string that you supply.</span></span> <span data-ttu-id="64086-106">Para obter mais informações, consulte [métodos DataContext (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer).</span><span class="sxs-lookup"><span data-stu-id="64086-106">For more information, see [DataContext Methods (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer).</span></span>  
  
 <span data-ttu-id="64086-107">O objetivo do <xref:System.Data.Linq.DataContext> é converter suas solicitações de objetos em consultas SQL a serem feitas no banco de dados e montar objetos a partir dos resultados.</span><span class="sxs-lookup"><span data-stu-id="64086-107">The purpose of the <xref:System.Data.Linq.DataContext> is to translate your requests for objects into SQL queries to be made against the database, and then to assemble objects out of the results.</span></span> <span data-ttu-id="64086-108">O <xref:System.Data.Linq.DataContext> habilita o LINQ (consulta integrada à linguagem) implementando o mesmo padrão de operador que os operadores de consulta padrão, como `Where` e `Select`.</span><span class="sxs-lookup"><span data-stu-id="64086-108">The <xref:System.Data.Linq.DataContext> enables Language-Integrated Query (LINQ) by implementing the same operator pattern as the Standard Query Operators, such as `Where` and `Select`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="64086-109">É muito importante manter uma conexão segura.</span><span class="sxs-lookup"><span data-stu-id="64086-109">Maintaining a secure connection is of the highest importance.</span></span> <span data-ttu-id="64086-110">Para obter mais informações, consulte [segurança em LINQ to SQL](security-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="64086-110">For more information, see [Security in LINQ to SQL](security-in-linq-to-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="64086-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="64086-111">Example</span></span>  
 <span data-ttu-id="64086-112">No exemplo a seguir, o <xref:System.Data.Linq.DataContext> é usado para conexão ao banco de dados de exemplo Northwind e recuperar linhas de clientes cuja cidade é Londres.</span><span class="sxs-lookup"><span data-stu-id="64086-112">In the following example, the <xref:System.Data.Linq.DataContext> is used to connect to the Northwind sample database and to retrieve rows of customers whose city is London.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#1)]
 [!code-vb[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#1)]  
  
 <span data-ttu-id="64086-113">Cada tabela do banco de dados é representada como uma coleção de `Table` disponível por meio do método <xref:System.Data.Linq.DataContext.GetTable%2A> usando a classe de entidade para identificá-la.</span><span class="sxs-lookup"><span data-stu-id="64086-113">Each database table is represented as a `Table` collection available by way of the <xref:System.Data.Linq.DataContext.GetTable%2A> method, by using the entity class to identify it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64086-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="64086-114">Example</span></span>  
 <span data-ttu-id="64086-115">A prática recomendada é declarar um <xref:System.Data.Linq.DataContext> fortemente tipado em vez de depender da classe básica <xref:System.Data.Linq.DataContext> e do método <xref:System.Data.Linq.DataContext.GetTable%2A>.</span><span class="sxs-lookup"><span data-stu-id="64086-115">Best practice is to declare a strongly typed <xref:System.Data.Linq.DataContext> instead of relying on the basic <xref:System.Data.Linq.DataContext> class and the <xref:System.Data.Linq.DataContext.GetTable%2A> method.</span></span> <span data-ttu-id="64086-116">Um <xref:System.Data.Linq.DataContext> fortemente tipado declara todas as coleções de `Table` como membros do contexto, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="64086-116">A strongly typed <xref:System.Data.Linq.DataContext> declares all `Table` collections as members of the context, as in the following example.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#2)]
 [!code-vb[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#2)]  
  
 <span data-ttu-id="64086-117">Você pode expressar a consulta para clientes de Londres de maneira mais simples, como:</span><span class="sxs-lookup"><span data-stu-id="64086-117">You can then express the query for customers from London more simply as:</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#5)]
 [!code-vb[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="64086-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="64086-118">See also</span></span>

- [<span data-ttu-id="64086-119">Comunicação com o banco de dados</span><span class="sxs-lookup"><span data-stu-id="64086-119">Communicating with the Database</span></span>](communicating-with-the-database.md)
