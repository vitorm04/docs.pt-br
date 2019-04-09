---
title: 'Como: criar uma cadeia de conexão EntityConnection'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5bd1a748-3df7-4d0a-a607-14f25e3175e9
ms.openlocfilehash: 19943f44431a50111552f0f60d46af420a7966bf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097291"
---
# <a name="how-to-build-an-entityconnection-connection-string"></a><span data-ttu-id="921c7-102">Como: criar uma cadeia de conexão EntityConnection</span><span class="sxs-lookup"><span data-stu-id="921c7-102">How to: Build an EntityConnection Connection String</span></span>
<span data-ttu-id="921c7-103">Este tópico fornece um exemplo de como criar um <xref:System.Data.EntityClient.EntityConnection>.</span><span class="sxs-lookup"><span data-stu-id="921c7-103">This topic provides an example of how to build an <xref:System.Data.EntityClient.EntityConnection>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="921c7-104">Para executar o código nesse exemplo</span><span class="sxs-lookup"><span data-stu-id="921c7-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="921c7-105">Adicione a [modelo de vendas AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) ao seu projeto e configurar seu projeto para usar o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="921c7-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="921c7-106">Para obter mais informações, confira [Como: Use o Assistente de modelo de dados de entidade](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="921c7-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2.  <span data-ttu-id="921c7-107">Na página de código do seu aplicativo, adicione as seguintes instruções `using` (`Imports` no Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="921c7-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="921c7-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="921c7-108">Example</span></span>  
 <span data-ttu-id="921c7-109">O exemplo a seguir inicializa o <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType> para o provedor subjacente e, em seguida, inicializa o objeto <xref:System.Data.EntityClient.EntityConnectionStringBuilder?displayProperty=nameWithType> e passa esse objeto para o construtor di <xref:System.Data.EntityClient.EntityConnection>.</span><span class="sxs-lookup"><span data-stu-id="921c7-109">The following example initializes the <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType> for the underlying provider, then initializes the <xref:System.Data.EntityClient.EntityConnectionStringBuilder?displayProperty=nameWithType> object and passes this object to the constructor of the <xref:System.Data.EntityClient.EntityConnection>.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#BuildingConnectionStringWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#buildingconnectionstringwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#BuildingConnectionStringWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#buildingconnectionstringwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="921c7-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="921c7-110">See also</span></span>

- [<span data-ttu-id="921c7-111">Como: Usar o EntityConnection com um contexto de objeto</span><span class="sxs-lookup"><span data-stu-id="921c7-111">How to: Use EntityConnection with an Object Context</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738461(v=vs.100))
- [<span data-ttu-id="921c7-112">Provedor EntityClient para Entity Framework</span><span class="sxs-lookup"><span data-stu-id="921c7-112">EntityClient Provider for the Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)
