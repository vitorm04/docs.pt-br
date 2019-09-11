---
title: 'Como: executar uma consulta que retorna resultados de StructuralType'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2314f2a2-b1c3-40c4-95bb-cdf9b21a7b53
ms.openlocfilehash: 7b649abb21b8f6ebbbd8aadc279b2902b3e21e25
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854540"
---
# <a name="how-to-execute-a-query-that-returns-structuraltype-results"></a><span data-ttu-id="a7e76-102">Como: executar uma consulta que retorna resultados de StructuralType</span><span class="sxs-lookup"><span data-stu-id="a7e76-102">How to: Execute a Query that Returns StructuralType Results</span></span>
<span data-ttu-id="a7e76-103">Este tópico mostra como executar um comando em um modelo conceitual usando um objeto de <xref:System.Data.EntityClient.EntityCommand> , e como recuperar <xref:System.Data.Metadata.Edm.StructuralType> resultados usando <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="a7e76-103">This topic shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand> object, and how to retrieve the <xref:System.Data.Metadata.Edm.StructuralType> results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span> <span data-ttu-id="a7e76-104"><xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.RowType> e as classes de <xref:System.Data.Metadata.Edm.ComplexType> derivam da classe de <xref:System.Data.Metadata.Edm.StructuralType> .</span><span class="sxs-lookup"><span data-stu-id="a7e76-104">The <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.RowType> and <xref:System.Data.Metadata.Edm.ComplexType> classes derive from the <xref:System.Data.Metadata.Edm.StructuralType> class.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="a7e76-105">Para executar o código nesse exemplo</span><span class="sxs-lookup"><span data-stu-id="a7e76-105">To run the code in this example</span></span>  
  
1. <span data-ttu-id="a7e76-106">Adicione o [modelo de vendas AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) ao seu projeto e configure seu projeto para usar o Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="a7e76-106">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="a7e76-107">Para obter mais informações, confira [Como: Use o assistente](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))de modelo de dados de entidade.</span><span class="sxs-lookup"><span data-stu-id="a7e76-107">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="a7e76-108">Na página de código do seu aplicativo, adicione as seguintes instruções `using` (`Imports` no Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="a7e76-108">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="a7e76-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a7e76-109">Example</span></span>  
 <span data-ttu-id="a7e76-110">Este exemplo executa uma consulta que retorna resultados de <xref:System.Data.Metadata.Edm.EntityType> .</span><span class="sxs-lookup"><span data-stu-id="a7e76-110">This example executes a query that returns <xref:System.Data.Metadata.Edm.EntityType> results.</span></span> <span data-ttu-id="a7e76-111">Se você passar a seguinte consulta como um argumento a função de `ExecuteStructuralTypeQuery` , a função exibe detalhes sobre `Products`:</span><span class="sxs-lookup"><span data-stu-id="a7e76-111">If you pass the following query as an argument to the `ExecuteStructuralTypeQuery` function, the function displays details about the `Products`:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#SelectProduct](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#selectproduct)]  
  
 <span data-ttu-id="a7e76-112">Se você passar uma consulta parametrizada, como o exemplo a seguir, adicione os objetos de <xref:System.Data.EntityClient.EntityParameter> à propriedade de <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> no objeto de <xref:System.Data.EntityClient.EntityCommand> .</span><span class="sxs-lookup"><span data-stu-id="a7e76-112">If you pass a parameterized query, like the following, add the <xref:System.Data.EntityClient.EntityParameter> objects to the <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> property on the <xref:System.Data.EntityClient.EntityCommand> object.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER_OR_EQUALS](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater_or_equals)]  
  
 [!code-csharp[DP EntityServices Concepts#eSQLStructuralTypes](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#esqlstructuraltypes)]
 [!code-vb[DP EntityServices Concepts#eSQLStructuralTypes](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#esqlstructuraltypes)]  
  
## <a name="see-also"></a><span data-ttu-id="a7e76-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7e76-113">See also</span></span>

- [<span data-ttu-id="a7e76-114">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a7e76-114">Entity SQL Reference</span></span>](./language-reference/entity-sql-reference.md)
- [<span data-ttu-id="a7e76-115">Provedor EntityClient para Entity Framework</span><span class="sxs-lookup"><span data-stu-id="a7e76-115">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)
