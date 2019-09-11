---
title: 'Como: executar uma consulta Entity SQL parametrizada usando EntityCommand'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e93fea43-7e03-4d7d-9fee-2517b8b88cba
ms.openlocfilehash: aa750ef088ee045c8d1045b2509d8fc4bde014ce
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854634"
---
# <a name="how-to-execute-a-parameterized-entity-sql-query-using-entitycommand"></a><span data-ttu-id="53b4d-102">Como: executar uma consulta Entity SQL parametrizada usando EntityCommand</span><span class="sxs-lookup"><span data-stu-id="53b4d-102">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>
<span data-ttu-id="53b4d-103">Este tópico mostra como executar uma [!INCLUDE[esql](../../../../../includes/esql-md.md)] consulta que tem parâmetros usando um <xref:System.Data.EntityClient.EntityCommand> objeto.</span><span class="sxs-lookup"><span data-stu-id="53b4d-103">This topic shows how to execute an [!INCLUDE[esql](../../../../../includes/esql-md.md)] query that has parameters by using an <xref:System.Data.EntityClient.EntityCommand> object.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="53b4d-104">Para executar o código nesse exemplo</span><span class="sxs-lookup"><span data-stu-id="53b4d-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="53b4d-105">Adicione o [modelo de vendas AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) ao seu projeto e configure seu projeto para usar o Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="53b4d-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="53b4d-106">Para obter mais informações, confira [Como: Use o assistente](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))de modelo de dados de entidade.</span><span class="sxs-lookup"><span data-stu-id="53b4d-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="53b4d-107">Na página de código do seu aplicativo, adicione as seguintes instruções `using` (`Imports` no Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="53b4d-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="53b4d-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="53b4d-108">Example</span></span>  
 <span data-ttu-id="53b4d-109">O exemplo a seguir mostra como construir uma cadeia de caracteres de consulta com dois parâmetros.</span><span class="sxs-lookup"><span data-stu-id="53b4d-109">The following example shows how to construct a query string with two parameters.</span></span> <span data-ttu-id="53b4d-110">Depois, ele cria um <xref:System.Data.EntityClient.EntityCommand>, adiciona dois parâmetros à coleção <xref:System.Data.EntityClient.EntityParameter> desse <xref:System.Data.EntityClient.EntityCommand> e itera pela coleção de itens `Contact`.</span><span class="sxs-lookup"><span data-stu-id="53b4d-110">It then creates an <xref:System.Data.EntityClient.EntityCommand>, adds two parameters to the <xref:System.Data.EntityClient.EntityParameter> collection of that <xref:System.Data.EntityClient.EntityCommand>, and iterates through the collection of `Contact` items.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#parameterizedquerywithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#parameterizedquerywithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="53b4d-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="53b4d-111">See also</span></span>

- <span data-ttu-id="53b4d-112">[Como: Executar uma consulta parametrizada](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="53b4d-112">[How to: Execute a Parameterized Query](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span></span>
- <span data-ttu-id="53b4d-113">[Entity SQL Language](./language-reference/entity-sql-language.md) (Linguagem SQL de entidade)</span><span class="sxs-lookup"><span data-stu-id="53b4d-113">[Entity SQL Language](./language-reference/entity-sql-language.md)</span></span>
