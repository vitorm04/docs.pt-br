---
title: 'Como: executar consultas SQL diretamente'
description: Saiba como usar ExecuteQuery para executar uma consulta e, em seguida, converter os resultados diretamente em objetos em casos em que uma consulta de LINQ to SQL é insuficiente.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e491b9bf-741a-4296-9f51-76c25ddf6a82
ms.openlocfilehash: 7ebd02581d789266396b58296bbd6ad312dd468e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200570"
---
# <a name="how-to-directly-execute-sql-queries"></a><span data-ttu-id="3f569-103">Como: executar consultas SQL diretamente</span><span class="sxs-lookup"><span data-stu-id="3f569-103">How to: Directly Execute SQL Queries</span></span>

<span data-ttu-id="3f569-104">O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] converte as consultas que você escreve em consultas SQL parametrizadas (em formato de texto) e as envia para o SQL Server para processamento.</span><span class="sxs-lookup"><span data-stu-id="3f569-104">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates the queries you write into parameterized SQL queries (in text form) and sends them to the SQL server for processing.</span></span>  
  
 <span data-ttu-id="3f569-105">O SQL não pode executar a variedade de métodos que podem estar disponíveis localmente para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3f569-105">SQL cannot execute the variety of methods that might be locally available to your application.</span></span> <span data-ttu-id="3f569-106">O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tenta converter esses métodos locais em operações e funções equivalentes que estão disponíveis no ambiente SQL.</span><span class="sxs-lookup"><span data-stu-id="3f569-106">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tries to convert these local methods to equivalent operations and functions that are available inside the SQL environment.</span></span> <span data-ttu-id="3f569-107">A maioria dos métodos e operadores em .NET Framework tipos internos têm traduções diretas para comandos SQL.</span><span class="sxs-lookup"><span data-stu-id="3f569-107">Most methods and operators on .NET Framework built-in types have direct translations to SQL commands.</span></span> <span data-ttu-id="3f569-108">Alguns podem ser gerados das funções que estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="3f569-108">Some can be produced from the functions that are available.</span></span> <span data-ttu-id="3f569-109">Aqueles que não podem ser produzidos geram exceções em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="3f569-109">Those that cannot be produced generate run-time exceptions.</span></span> <span data-ttu-id="3f569-110">Para obter mais informações, consulte [mapeamento de tipo SQL-CLR](sql-clr-type-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="3f569-110">For more information, see [SQL-CLR Type Mapping](sql-clr-type-mapping.md).</span></span>  
  
 <span data-ttu-id="3f569-111">Nos casos em que uma consulta de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] é insuficiente para uma tarefa especializada, você pode usar o método <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> para executar uma consulta SQL e, depois, converter o resultado da consulta diretamente em objetos.</span><span class="sxs-lookup"><span data-stu-id="3f569-111">In cases where a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query is insufficient for a specialized task, you can use the <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method to execute a SQL query, and then convert the result of your query directly into objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f569-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3f569-112">Example</span></span>  

 <span data-ttu-id="3f569-113">No exemplo a seguir, suponha que os dados da classe `Customer` são espalhados em duas tabelas (customer1 e customer2).</span><span class="sxs-lookup"><span data-stu-id="3f569-113">In the following example, assume that the data for the `Customer` class is spread over two tables (customer1 and customer2).</span></span> <span data-ttu-id="3f569-114">A consulta retorna uma sequência de objetos `Customer`.</span><span class="sxs-lookup"><span data-stu-id="3f569-114">The query returns a sequence of `Customer` objects.</span></span>  
  
 [!code-csharp[DLinqQuerying#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#4)]
 [!code-vb[DLinqQuerying#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#4)]  
  
 <span data-ttu-id="3f569-115">Desde que os nomes de coluna nos resultados de tabela correspondam às propriedades da coluna de sua classe de entidade, o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] cria seus objetos fora de qualquer consulta SQL.</span><span class="sxs-lookup"><span data-stu-id="3f569-115">As long as the column names in the tabular results match column properties of your entity class, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates your objects out of any SQL query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f569-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3f569-116">Example</span></span>  

 <span data-ttu-id="3f569-117">O método <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> também permite parâmetros.</span><span class="sxs-lookup"><span data-stu-id="3f569-117">The <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method also allows for parameters.</span></span> <span data-ttu-id="3f569-118">Use um código como o mostrado a seguir para executar uma consulta parametrizada.</span><span class="sxs-lookup"><span data-stu-id="3f569-118">Use code such as the following to execute a parameterized query.</span></span>  
  
 [!code-csharp[DLinqQuerying#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#5)]
 [!code-vb[DLinqQuerying#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#5)]  
  
 <span data-ttu-id="3f569-119">Os parâmetros são expressos no texto da consulta usando as mesmas chaves usadas por `Console.WriteLine()` e `String.Format()`.</span><span class="sxs-lookup"><span data-stu-id="3f569-119">The parameters are expressed in the query text by using the same curly notation used by `Console.WriteLine()` and `String.Format()`.</span></span> <span data-ttu-id="3f569-120">Na verdade, `String.Format()` é realmente chamado na cadeia de caracteres de consulta que você fornece, substituindo os parâmetros de chaves com nomes de parâmetro gerados, como @p0 , @p1 ..., @p (n).</span><span class="sxs-lookup"><span data-stu-id="3f569-120">In fact, `String.Format()` is actually called on the query string you provide, substituting the curly braced parameters with generated parameter names such as @p0, @p1 …, @p(n).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f569-121">Veja também</span><span class="sxs-lookup"><span data-stu-id="3f569-121">See also</span></span>

- [<span data-ttu-id="3f569-122">Informações gerais</span><span class="sxs-lookup"><span data-stu-id="3f569-122">Background Information</span></span>](background-information.md)
- [<span data-ttu-id="3f569-123">Consultando o banco de dados</span><span class="sxs-lookup"><span data-stu-id="3f569-123">Querying the Database</span></span>](querying-the-database.md)
