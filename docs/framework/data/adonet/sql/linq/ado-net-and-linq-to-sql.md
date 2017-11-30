---
title: O ADO.NET e LINQ to SQL
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
ms.assetid: 49ac6da0-f2e1-46fa-963e-1b6dcb63fef7
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 97cf55419c6e13a497264bcbaa3a546eac37f982
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="adonet-and-linq-to-sql"></a><span data-ttu-id="700f2-102">O ADO.NET e LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="700f2-102">ADO.NET and LINQ to SQL</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="700f2-103">é parte do [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] família de tecnologias.</span><span class="sxs-lookup"><span data-stu-id="700f2-103"> is part of the [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] family of technologies.</span></span> <span data-ttu-id="700f2-104">É baseada em serviços fornecidos pelo modelo de provedor de [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="700f2-104">It is based on services provided by the [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] provider model.</span></span> <span data-ttu-id="700f2-105">Portanto, você pode misturar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] código com existente [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] aplicativos e migrar atual [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] soluções para [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="700f2-105">You can therefore mix [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] code with existing [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] applications and migrate current [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] solutions to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="700f2-106">A ilustração a seguir fornece uma exibição de alto nível de relacionamento.</span><span class="sxs-lookup"><span data-stu-id="700f2-106">The following illustration provides a high-level view of the relationship.</span></span>  
  
 <span data-ttu-id="700f2-107">![LINQ to SQL e o ADO.NET](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinq-3.png "DLinq_3")</span><span class="sxs-lookup"><span data-stu-id="700f2-107">![LINQ to SQL and ADO.NET](../../../../../../docs/framework/data/adonet/sql/linq/media/dlinq-3.png "DLinq_3")</span></span>  
  
## <a name="connections"></a><span data-ttu-id="700f2-108">Conexões</span><span class="sxs-lookup"><span data-stu-id="700f2-108">Connections</span></span>  
 <span data-ttu-id="700f2-109">Você pode fornecer um existente [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] conexão quando você cria um [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="700f2-109">You can supply an existing [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] connection when you create a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="700f2-110">Todas as operações em relação a <xref:System.Data.Linq.DataContext> (incluindo consultas) use fornecido a conexão.</span><span class="sxs-lookup"><span data-stu-id="700f2-110">All operations against the <xref:System.Data.Linq.DataContext> (including queries) use this provided connection.</span></span> <span data-ttu-id="700f2-111">Se a conexão já estiver aberto, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] deixar como está quando tiver terminado com ele.</span><span class="sxs-lookup"><span data-stu-id="700f2-111">If the connection is already open, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] leaves it as is when you are finished with it.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
 <span data-ttu-id="700f2-112">Você sempre pode acessar a conexão e fechá-lo você mesmo usando a propriedade de <xref:System.Data.Linq.DataContext.Connection%2A> , como no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="700f2-112">You can always access the connection and close it yourself by using the <xref:System.Data.Linq.DataContext.Connection%2A> property, as in the following code:</span></span>  
  
 [!code-csharp[DLinqAdoNet#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#1)]
 [!code-vb[DLinqAdoNet#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#1)]  
  
## <a name="transactions"></a><span data-ttu-id="700f2-113">Transações</span><span class="sxs-lookup"><span data-stu-id="700f2-113">Transactions</span></span>  
 <span data-ttu-id="700f2-114">Você pode fornecer seu <xref:System.Data.Linq.DataContext> com sua própria transação de base de dados quando seu aplicativo é iniciado na transação e você deseja que o <xref:System.Data.Linq.DataContext> a ser empacotado.</span><span class="sxs-lookup"><span data-stu-id="700f2-114">You can supply your <xref:System.Data.Linq.DataContext> with your own database transaction when your application has already initiated the transaction and you want your <xref:System.Data.Linq.DataContext> to be involved.</span></span>  
  
 <span data-ttu-id="700f2-115">O método preferido de transações fazer com [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] é usar o objeto de <xref:System.Transactions.TransactionScope> .</span><span class="sxs-lookup"><span data-stu-id="700f2-115">The preferred method of doing transactions with the [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] is to use the <xref:System.Transactions.TransactionScope> object.</span></span> <span data-ttu-id="700f2-116">Usando essa abordagem, você pode fazer as transações distribuídas que funcionam através de bases de dados e outros gerentes de recurso de memória residente.</span><span class="sxs-lookup"><span data-stu-id="700f2-116">By using this approach, you can make distributed transactions that work across databases and other memory-resident resource managers.</span></span> <span data-ttu-id="700f2-117">Escopos de transação requerem alguns recursos para começar.</span><span class="sxs-lookup"><span data-stu-id="700f2-117">Transaction scopes require few resources to start.</span></span> <span data-ttu-id="700f2-118">Eles se autopromover a transações distribuídas somente quando há várias conexões dentro do escopo da transação.</span><span class="sxs-lookup"><span data-stu-id="700f2-118">They promote themselves to distributed transactions only when there are multiple connections within the scope of the transaction.</span></span>  
  
 [!code-csharp[DLinqAdoNet#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#2)]
 [!code-vb[DLinqAdoNet#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#2)]  
  
 <span data-ttu-id="700f2-119">Você não pode usar essa abordagem para todos os bases de dados.</span><span class="sxs-lookup"><span data-stu-id="700f2-119">You cannot use this approach for all databases.</span></span> <span data-ttu-id="700f2-120">Por exemplo, a conexão SqlClient não pode elevar transações do sistema quando trabalha em um servidor de [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="700f2-120">For example, the SqlClient connection cannot promote system transactions when it works against a [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] server.</span></span> <span data-ttu-id="700f2-121">Em vez disso, inscreve-se automaticamente para uma transação completa, distribuído consulta sempre que um escopo de transação que está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="700f2-121">Instead, it automatically enlists to a full, distributed transaction whenever it sees a transaction scope being used.</span></span>  
  
## <a name="direct-sql-commands"></a><span data-ttu-id="700f2-122">Comandos SQL diretos</span><span class="sxs-lookup"><span data-stu-id="700f2-122">Direct SQL Commands</span></span>  
 <span data-ttu-id="700f2-123">Às vezes você pode encontrar situações onde a capacidade de <xref:System.Data.Linq.DataContext> de consulte ou enviar alterações insuficientes para a tarefa específica que você deseja executar.</span><span class="sxs-lookup"><span data-stu-id="700f2-123">At times you can encounter situations where the ability of the <xref:System.Data.Linq.DataContext> to query or submit changes is insufficient for the specialized task you want to perform.</span></span> <span data-ttu-id="700f2-124">Nesteas circunstâncias você pode usar o método de <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> para emitir comandos SQL a base de dados e para converter os resultados da consulta a objetos.</span><span class="sxs-lookup"><span data-stu-id="700f2-124">In these circumstances you can use the <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method to issue SQL commands to the database and convert the query results to objects.</span></span>  
  
 <span data-ttu-id="700f2-125">Por exemplo, suponha que os dados para a classe de `Customer` são espalhado sobre duas tabelas (customer1 e customer2).</span><span class="sxs-lookup"><span data-stu-id="700f2-125">For example, assume that the data for the `Customer` class is spread over two tables (customer1 and customer2).</span></span> <span data-ttu-id="700f2-126">A seguinte consulta retorna uma sequência de objetos `Customer` :</span><span class="sxs-lookup"><span data-stu-id="700f2-126">The following query returns a sequence of `Customer` objects:</span></span>  
  
 [!code-csharp[DLinqAdoNet#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#3)]
 [!code-vb[DLinqAdoNet#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#3)]  
  
 <span data-ttu-id="700f2-127">Como os nomes de coluna nos resultados da tabela correspondem a propriedades de coluna de sua classe de entidade, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] cria os objetos fora de qualquer consulta SQL.</span><span class="sxs-lookup"><span data-stu-id="700f2-127">As long as the column names in the tabular results match column properties of your entity class, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates your objects out of any SQL query.</span></span>  
  
### <a name="parameters"></a><span data-ttu-id="700f2-128">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="700f2-128">Parameters</span></span>  
 <span data-ttu-id="700f2-129">O método de <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> aceita parâmetros.</span><span class="sxs-lookup"><span data-stu-id="700f2-129">The <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method accepts parameters.</span></span> <span data-ttu-id="700f2-130">O código a seguir executa uma consulta parametrizada:</span><span class="sxs-lookup"><span data-stu-id="700f2-130">The following code executes a parameterized query:</span></span>  
  
 [!code-csharp[DlinqAdoNet#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#4)]
 [!code-vb[DlinqAdoNet#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#4)]  
  
> [!NOTE]
>  <span data-ttu-id="700f2-131">Os parâmetros são expressos no texto da consulta usando a mesma notação encaracolado usada por `Console.WriteLine()` e por `String.Format()`.</span><span class="sxs-lookup"><span data-stu-id="700f2-131">Parameters are expressed in the query text by using the same curly notation used by `Console.WriteLine()` and `String.Format()`.</span></span> <span data-ttu-id="700f2-132">`String.Format()` leva a cadeia de caracteres de consulta que você fornece e substitui os parâmetros encaracolado- apoiados com nomes de parâmetro gerados como `@p0`, `@p1` …, `@p(n)`.</span><span class="sxs-lookup"><span data-stu-id="700f2-132">`String.Format()` takes the query string you provide and substitutes the curly-braced parameters with generated parameter names such as `@p0`, `@p1` …, `@p(n)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="700f2-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="700f2-133">See Also</span></span>  
 [<span data-ttu-id="700f2-134">Informações de plano de fundo</span><span class="sxs-lookup"><span data-stu-id="700f2-134">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [<span data-ttu-id="700f2-135">Como: reutilizar uma Conexão entre um comando ADO.NET e um DataContext</span><span class="sxs-lookup"><span data-stu-id="700f2-135">How to: Reuse a Connection Between an ADO.NET Command and a DataContext</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-reuse-a-connection-between-an-ado-net-command-and-a-datacontext.md)
