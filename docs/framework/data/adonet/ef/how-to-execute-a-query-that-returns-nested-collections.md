---
title: 'Como: executar uma consulta que retorna aninhados coleções'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f7f385f3-ffcf-4f3b-af35-de8818938e5f
ms.openlocfilehash: b3319d3b833ab50ec426c8059bccf818b1407a60
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115291"
---
# <a name="how-to-execute-a-query-that-returns-nested-collections"></a><span data-ttu-id="c2eef-102">Como: executar uma consulta que retorna aninhados coleções</span><span class="sxs-lookup"><span data-stu-id="c2eef-102">How to: Execute a Query that Returns Nested Collections</span></span>
<span data-ttu-id="c2eef-103">Isso mostra como executar um comando em um modelo conceitual usando um objeto de <xref:System.Data.EntityClient.EntityCommand> , e como recuperar a coleção aninhada resultados usando <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="c2eef-103">This shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand> object, and how to retrieve the nested collection results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="c2eef-104">Para executar o código nesse exemplo</span><span class="sxs-lookup"><span data-stu-id="c2eef-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="c2eef-105">Adicione a [modelo de vendas AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) ao seu projeto e configurar seu projeto para usar o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c2eef-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="c2eef-106">Para obter mais informações, confira [Como: Use o Assistente de modelo de dados de entidade](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="c2eef-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2.  <span data-ttu-id="c2eef-107">Na página de código do seu aplicativo, adicione as seguintes instruções `using` (`Imports` no Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="c2eef-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="c2eef-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c2eef-108">Example</span></span>  
 <span data-ttu-id="c2eef-109">Um *aninhados coleção* é uma coleção que está dentro de outra coleção.</span><span class="sxs-lookup"><span data-stu-id="c2eef-109">A *nested collection* is a collection that is inside another collection.</span></span> <span data-ttu-id="c2eef-110">O código a seguir recupera uma coleção de `Contacts` e coleções aninhados de `SalesOrderHeaders` que estão associadas com cada `Contact`.</span><span class="sxs-lookup"><span data-stu-id="c2eef-110">The following code retrieves a collection of `Contacts` and the nested collections of `SalesOrderHeaders` that are associated with each `Contact`.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ReturnNestedCollectionWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#returnnestedcollectionwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ReturnNestedCollectionWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#returnnestedcollectionwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="c2eef-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c2eef-111">See also</span></span>

- [<span data-ttu-id="c2eef-112">Provedor EntityClient para Entity Framework</span><span class="sxs-lookup"><span data-stu-id="c2eef-112">EntityClient Provider for the Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)
