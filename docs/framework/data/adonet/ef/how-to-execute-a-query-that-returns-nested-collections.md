---
title: 'Como: executar uma consulta que retorna aninhados coleções'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f7f385f3-ffcf-4f3b-af35-de8818938e5f
ms.openlocfilehash: 3bf6e08e7842fbf235b519680b81f79fba4a7228
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198399"
---
# <a name="how-to-execute-a-query-that-returns-nested-collections"></a><span data-ttu-id="49167-102">Como: executar uma consulta que retorna aninhados coleções</span><span class="sxs-lookup"><span data-stu-id="49167-102">How to: Execute a Query that Returns Nested Collections</span></span>

<span data-ttu-id="49167-103">Isso mostra como executar um comando em um modelo conceitual usando um objeto de <xref:System.Data.EntityClient.EntityCommand> , e como recuperar a coleção aninhada resultados usando <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="49167-103">This shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand> object, and how to retrieve the nested collection results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="49167-104">Para executar o código nesse exemplo</span><span class="sxs-lookup"><span data-stu-id="49167-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="49167-105">Adicione o [modelo de vendas AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) ao seu projeto e configure seu projeto para usar o Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="49167-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="49167-106">Para obter mais informações, consulte [como: usar o assistente de modelo de dados de entidade](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="49167-106">For more information, see [How to: Use the Entity Data Model Wizard](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="49167-107">Na página de código do seu aplicativo, adicione as seguintes instruções `using` (`Imports` no Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="49167-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="49167-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="49167-108">Example</span></span>  

 <span data-ttu-id="49167-109">Uma *coleção aninhada* é uma coleção que está dentro de outra coleção.</span><span class="sxs-lookup"><span data-stu-id="49167-109">A *nested collection* is a collection that is inside another collection.</span></span> <span data-ttu-id="49167-110">O código a seguir recupera uma coleção de `Contacts` e coleções aninhados de `SalesOrderHeaders` que estão associadas com cada `Contact`.</span><span class="sxs-lookup"><span data-stu-id="49167-110">The following code retrieves a collection of `Contacts` and the nested collections of `SalesOrderHeaders` that are associated with each `Contact`.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ReturnNestedCollectionWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#returnnestedcollectionwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ReturnNestedCollectionWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#returnnestedcollectionwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="49167-111">Veja também</span><span class="sxs-lookup"><span data-stu-id="49167-111">See also</span></span>

- [<span data-ttu-id="49167-112">Provedor EntityClient para Entity Framework</span><span class="sxs-lookup"><span data-stu-id="49167-112">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)
