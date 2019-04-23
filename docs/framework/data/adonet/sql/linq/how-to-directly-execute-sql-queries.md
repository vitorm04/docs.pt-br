---
title: 'Como: executar consultas SQL diretamente'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e491b9bf-741a-4296-9f51-76c25ddf6a82
ms.openlocfilehash: 6423959ed5036cc8ab2a88bb7273ef7aa95c8958
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59101530"
---
# <a name="how-to-directly-execute-sql-queries"></a><span data-ttu-id="acaa8-102">Como: executar consultas SQL diretamente</span><span class="sxs-lookup"><span data-stu-id="acaa8-102">How to: Directly Execute SQL Queries</span></span>
<span data-ttu-id="acaa8-103">O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] converte as consultas que você escreve em consultas SQL parametrizadas (em formato de texto) e as envia para o SQL Server para processamento.</span><span class="sxs-lookup"><span data-stu-id="acaa8-103">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates the queries you write into parameterized SQL queries (in text form) and sends them to the SQL server for processing.</span></span>  
  
 <span data-ttu-id="acaa8-104">O SQL não pode executar a variedade de métodos que podem estar disponíveis localmente para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="acaa8-104">SQL cannot execute the variety of methods that might be locally available to your application.</span></span> <span data-ttu-id="acaa8-105">O [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tenta converter esses métodos locais em operações e funções equivalentes que estão disponíveis no ambiente SQL.</span><span class="sxs-lookup"><span data-stu-id="acaa8-105">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tries to convert these local methods to equivalent operations and functions that are available inside the SQL environment.</span></span> <span data-ttu-id="acaa8-106">A maioria dos métodos e operadores em tipos internos de [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] têm conversões diretas para comandos SQL.</span><span class="sxs-lookup"><span data-stu-id="acaa8-106">Most methods and operators on [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] built-in types have direct translations to SQL commands.</span></span> <span data-ttu-id="acaa8-107">Alguns podem ser gerados das funções que estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="acaa8-107">Some can be produced from the functions that are available.</span></span> <span data-ttu-id="acaa8-108">Aqueles que não podem ser produzidos geram exceções em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="acaa8-108">Those that cannot be produced generate run-time exceptions.</span></span> <span data-ttu-id="acaa8-109">Para obter mais informações, consulte [mapeamento de tipo de SQL-CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="acaa8-109">For more information, see [SQL-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span></span>  
  
 <span data-ttu-id="acaa8-110">Nos casos em que uma consulta de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] é insuficiente para uma tarefa especializada, você pode usar o método <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> para executar uma consulta SQL e, depois, converter o resultado da consulta diretamente em objetos.</span><span class="sxs-lookup"><span data-stu-id="acaa8-110">In cases where a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query is insufficient for a specialized task, you can use the <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method to execute a SQL query, and then convert the result of your query directly into objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="acaa8-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="acaa8-111">Example</span></span>  
 <span data-ttu-id="acaa8-112">No exemplo a seguir, suponha que os dados da classe `Customer` são espalhados em duas tabelas (customer1 e customer2).</span><span class="sxs-lookup"><span data-stu-id="acaa8-112">In the following example, assume that the data for the `Customer` class is spread over two tables (customer1 and customer2).</span></span> <span data-ttu-id="acaa8-113">A consulta retorna uma sequência de objetos `Customer`.</span><span class="sxs-lookup"><span data-stu-id="acaa8-113">The query returns a sequence of `Customer` objects.</span></span>  
  
 [!code-csharp[DLinqQuerying#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#4)]
 [!code-vb[DLinqQuerying#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#4)]  
  
 <span data-ttu-id="acaa8-114">Desde que os nomes de coluna nos resultados tabulares coincidam propriedades da coluna de sua classe de entidade, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] cria seus objetos a partir de qualquer consulta SQL.</span><span class="sxs-lookup"><span data-stu-id="acaa8-114">As long as the column names in the tabular results match column properties of your entity class, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates your objects out of any SQL query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="acaa8-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="acaa8-115">Example</span></span>  
 <span data-ttu-id="acaa8-116">O método <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> também permite parâmetros.</span><span class="sxs-lookup"><span data-stu-id="acaa8-116">The <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method also allows for parameters.</span></span> <span data-ttu-id="acaa8-117">Use um código como o mostrado a seguir para executar uma consulta parametrizada.</span><span class="sxs-lookup"><span data-stu-id="acaa8-117">Use code such as the following to execute a parameterized query.</span></span>  
  
 [!code-csharp[DLinqQuerying#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#5)]
 [!code-vb[DLinqQuerying#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#5)]  
  
 <span data-ttu-id="acaa8-118">Os parâmetros são expressos no texto da consulta usando as mesmas chaves usadas por `Console.WriteLine()` e `String.Format()`.</span><span class="sxs-lookup"><span data-stu-id="acaa8-118">The parameters are expressed in the query text by using the same curly notation used by `Console.WriteLine()` and `String.Format()`.</span></span> <span data-ttu-id="acaa8-119">Na verdade, `String.Format()` é chamado na cadeia de consulta que você fornecer, substituir os parâmetros de chaves com nomes de parâmetro gerados como @p0, @p1 ..., @p(n).</span><span class="sxs-lookup"><span data-stu-id="acaa8-119">In fact, `String.Format()` is actually called on the query string you provide, substituting the curly braced parameters with generated parameter names such as @p0, @p1 …, @p(n).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acaa8-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="acaa8-120">See also</span></span>

- [<span data-ttu-id="acaa8-121">Informações gerais</span><span class="sxs-lookup"><span data-stu-id="acaa8-121">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [<span data-ttu-id="acaa8-122">Consultando o banco de dados</span><span class="sxs-lookup"><span data-stu-id="acaa8-122">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
