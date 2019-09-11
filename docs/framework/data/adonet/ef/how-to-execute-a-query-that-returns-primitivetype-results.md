---
title: 'Como: executar uma consulta que retorna resultados de PrimitiveType'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7139d585-4034-4dfa-916f-2120a8b72792
ms.openlocfilehash: a00448f1c521d468db4cdaa957f92772194c8b43
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854871"
---
# <a name="how-to-execute-a-query-that-returns-primitivetype-results"></a><span data-ttu-id="d2401-102">Como: executar uma consulta que retorna resultados de PrimitiveType</span><span class="sxs-lookup"><span data-stu-id="d2401-102">How to: Execute a Query that Returns PrimitiveType Results</span></span>
<span data-ttu-id="d2401-103">Este tópico mostra como executar um comando em um modelo conceitual usando <xref:System.Data.EntityClient.EntityCommand>, e como recuperar <xref:System.Data.Metadata.Edm.PrimitiveType> resultados usando <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="d2401-103">This topic shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand>, and how to retrieve the <xref:System.Data.Metadata.Edm.PrimitiveType> results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="d2401-104">Para executar o código nesse exemplo</span><span class="sxs-lookup"><span data-stu-id="d2401-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="d2401-105">Adicione o [modelo de vendas AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) ao seu projeto e configure seu projeto para usar o Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="d2401-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="d2401-106">Para obter mais informações, confira [Como: Use o assistente](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))de modelo de dados de entidade.</span><span class="sxs-lookup"><span data-stu-id="d2401-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="d2401-107">Na página de código do seu aplicativo, adicione as seguintes instruções `using` (`Imports` no Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="d2401-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="d2401-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d2401-108">Example</span></span>  
 <span data-ttu-id="d2401-109">Este exemplo executa uma consulta que retorna um resultado de <xref:System.Data.Metadata.Edm.PrimitiveType> .</span><span class="sxs-lookup"><span data-stu-id="d2401-109">This example executes a query that returns a <xref:System.Data.Metadata.Edm.PrimitiveType> result.</span></span> <span data-ttu-id="d2401-110">Se você passar a seguinte consulta como um argumento a função de `ExecutePrimitiveTypeQuery` , a função exibe o custo de tabela médio de qualquer `Products`:</span><span class="sxs-lookup"><span data-stu-id="d2401-110">If you pass the following query as an argument to the `ExecutePrimitiveTypeQuery` function, the function displays the average list price of all `Products`:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EDM_AVG](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#edm_avg)]  
  
 <span data-ttu-id="d2401-111">Se você passar uma consulta parametrizada, como o exemplo a seguir, objetos de <xref:System.Data.EntityClient.EntityParameter> à propriedade de <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> em <xref:System.Data.EntityClient.EntityCommand> objeto.</span><span class="sxs-lookup"><span data-stu-id="d2401-111">If you pass a parameterized query, like the following, <xref:System.Data.EntityClient.EntityParameter> objects to the <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> property on the <xref:System.Data.EntityClient.EntityCommand> object.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
 [!code-csharp[DP EntityServices Concepts#eSQLPrimitiveTypes](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#esqlprimitivetypes)]
 [!code-vb[DP EntityServices Concepts#eSQLPrimitiveTypes](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#esqlprimitivetypes)]  
  
## <a name="see-also"></a><span data-ttu-id="d2401-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d2401-112">See also</span></span>

- [<span data-ttu-id="d2401-113">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="d2401-113">Entity SQL Reference</span></span>](./language-reference/entity-sql-reference.md)
- [<span data-ttu-id="d2401-114">Provedor EntityClient para Entity Framework</span><span class="sxs-lookup"><span data-stu-id="d2401-114">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)
