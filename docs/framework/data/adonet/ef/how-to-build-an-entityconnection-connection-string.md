---
title: 'Como: criar uma cadeia de conexão EntityConnection'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5bd1a748-3df7-4d0a-a607-14f25e3175e9
ms.openlocfilehash: f0918950921e620f724fedd8be027ffe0e2d3fa6
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854665"
---
# <a name="how-to-build-an-entityconnection-connection-string"></a><span data-ttu-id="ff041-102">Como: criar uma cadeia de conexão EntityConnection</span><span class="sxs-lookup"><span data-stu-id="ff041-102">How to: Build an EntityConnection Connection String</span></span>
<span data-ttu-id="ff041-103">Este tópico fornece um exemplo de como criar um <xref:System.Data.EntityClient.EntityConnection>.</span><span class="sxs-lookup"><span data-stu-id="ff041-103">This topic provides an example of how to build an <xref:System.Data.EntityClient.EntityConnection>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="ff041-104">Para executar o código nesse exemplo</span><span class="sxs-lookup"><span data-stu-id="ff041-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="ff041-105">Adicione o [modelo de vendas AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) ao seu projeto e configure seu projeto para usar o Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="ff041-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="ff041-106">Para obter mais informações, confira [Como: Use o assistente](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))de modelo de dados de entidade.</span><span class="sxs-lookup"><span data-stu-id="ff041-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="ff041-107">Na página de código do seu aplicativo, adicione as seguintes instruções `using` (`Imports` no Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="ff041-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="ff041-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ff041-108">Example</span></span>  
 <span data-ttu-id="ff041-109">O exemplo a seguir inicializa o <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType> para o provedor subjacente e, em seguida, inicializa o objeto <xref:System.Data.EntityClient.EntityConnectionStringBuilder?displayProperty=nameWithType> e passa esse objeto para o construtor di <xref:System.Data.EntityClient.EntityConnection>.</span><span class="sxs-lookup"><span data-stu-id="ff041-109">The following example initializes the <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType> for the underlying provider, then initializes the <xref:System.Data.EntityClient.EntityConnectionStringBuilder?displayProperty=nameWithType> object and passes this object to the constructor of the <xref:System.Data.EntityClient.EntityConnection>.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#BuildingConnectionStringWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#buildingconnectionstringwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#BuildingConnectionStringWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#buildingconnectionstringwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="ff041-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ff041-110">See also</span></span>

- <span data-ttu-id="ff041-111">[Como: Usar EntityConnection com um contexto de objeto](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738461(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ff041-111">[How to: Use EntityConnection with an Object Context](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738461(v=vs.100))</span></span>
- [<span data-ttu-id="ff041-112">Provedor EntityClient para Entity Framework</span><span class="sxs-lookup"><span data-stu-id="ff041-112">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)
