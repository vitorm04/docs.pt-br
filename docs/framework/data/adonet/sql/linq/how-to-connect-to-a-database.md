---
title: Como conectar-se a um banco de dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c33d74b3-530d-421b-a121-96786dd263a5
ms.openlocfilehash: 924fe4fadd5dae9907fca61a556506db1e583669
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362071"
---
# <a name="how-to-connect-to-a-database"></a><span data-ttu-id="78622-102">Como conectar-se a um banco de dados</span><span class="sxs-lookup"><span data-stu-id="78622-102">How to: Connect to a Database</span></span>
<span data-ttu-id="78622-103">O <xref:System.Data.Linq.DataContext> é o principal conduto pelo qual você se conecta a um banco de dados, recupera objetos deles e envia alterações de volta para ele.</span><span class="sxs-lookup"><span data-stu-id="78622-103">The <xref:System.Data.Linq.DataContext> is the main conduit by which you connect to a database, retrieve objects from it, and submit changes back to it.</span></span> <span data-ttu-id="78622-104">Você usa o <xref:System.Data.Linq.DataContext> assim como você usaria uma [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] <xref:System.Data.SqlClient.SqlConnection>.</span><span class="sxs-lookup"><span data-stu-id="78622-104">You use the <xref:System.Data.Linq.DataContext> just as you would use an [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] <xref:System.Data.SqlClient.SqlConnection>.</span></span> <span data-ttu-id="78622-105">Na verdade, o <xref:System.Data.Linq.DataContext> é inicializado com uma conexão ou com uma cadeia de conexão que você fornece.</span><span class="sxs-lookup"><span data-stu-id="78622-105">In fact, the <xref:System.Data.Linq.DataContext> is initialized with a connection or connection string that you supply.</span></span> <span data-ttu-id="78622-106">Para obter mais informações, consulte [métodos DataContext (Object Relational Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer).</span><span class="sxs-lookup"><span data-stu-id="78622-106">For more information, see [DataContext Methods (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer).</span></span>  
  
 <span data-ttu-id="78622-107">O objetivo do <xref:System.Data.Linq.DataContext> é converter suas solicitações de objetos em consultas SQL a serem feitas no banco de dados e montar objetos a partir dos resultados.</span><span class="sxs-lookup"><span data-stu-id="78622-107">The purpose of the <xref:System.Data.Linq.DataContext> is to translate your requests for objects into SQL queries to be made against the database, and then to assemble objects out of the results.</span></span> <span data-ttu-id="78622-108">O <xref:System.Data.Linq.DataContext> permite o [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] implementando o mesmo padrão de operador que os operadores de consulta padrão, como `Where` e `Select`.</span><span class="sxs-lookup"><span data-stu-id="78622-108">The <xref:System.Data.Linq.DataContext> enables [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] by implementing the same operator pattern as the Standard Query Operators, such as `Where` and `Select`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="78622-109">É muito importante manter uma conexão segura.</span><span class="sxs-lookup"><span data-stu-id="78622-109">Maintaining a secure connection is of the highest importance.</span></span> <span data-ttu-id="78622-110">Para obter mais informações, consulte [segurança em LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="78622-110">For more information, see [Security in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="78622-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="78622-111">Example</span></span>  
 <span data-ttu-id="78622-112">No exemplo a seguir, o <xref:System.Data.Linq.DataContext> é usado para conexão ao banco de dados de exemplo Northwind e recuperar linhas de clientes cuja cidade é Londres.</span><span class="sxs-lookup"><span data-stu-id="78622-112">In the following example, the <xref:System.Data.Linq.DataContext> is used to connect to the Northwind sample database and to retrieve rows of customers whose city is London.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#1)]
 [!code-vb[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#1)]  
  
 <span data-ttu-id="78622-113">Cada tabela do banco de dados é representada como uma coleção de `Table` disponível por meio do método <xref:System.Data.Linq.DataContext.GetTable%2A> usando a classe de entidade para identificá-la.</span><span class="sxs-lookup"><span data-stu-id="78622-113">Each database table is represented as a `Table` collection available by way of the <xref:System.Data.Linq.DataContext.GetTable%2A> method, by using the entity class to identify it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78622-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="78622-114">Example</span></span>  
 <span data-ttu-id="78622-115">A prática recomendada é declarar um <xref:System.Data.Linq.DataContext> fortemente tipado em vez de depender da classe básica <xref:System.Data.Linq.DataContext> e do método <xref:System.Data.Linq.DataContext.GetTable%2A>.</span><span class="sxs-lookup"><span data-stu-id="78622-115">Best practice is to declare a strongly typed <xref:System.Data.Linq.DataContext> instead of relying on the basic <xref:System.Data.Linq.DataContext> class and the <xref:System.Data.Linq.DataContext.GetTable%2A> method.</span></span> <span data-ttu-id="78622-116">Um <xref:System.Data.Linq.DataContext> fortemente tipado declara todas as coleções de `Table` como membros do contexto, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="78622-116">A strongly typed <xref:System.Data.Linq.DataContext> declares all `Table` collections as members of the context, as in the following example.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#2)]
 [!code-vb[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#2)]  
  
 <span data-ttu-id="78622-117">Você pode expressar a consulta para clientes de Londres de maneira mais simples, como:</span><span class="sxs-lookup"><span data-stu-id="78622-117">You can then express the query for customers from London more simply as:</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#5)]
 [!code-vb[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="78622-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="78622-118">See Also</span></span>  
 [<span data-ttu-id="78622-119">Comunicação com o banco de dados</span><span class="sxs-lookup"><span data-stu-id="78622-119">Communicating with the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)
