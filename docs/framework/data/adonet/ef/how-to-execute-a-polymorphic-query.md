---
title: 'Como: Executar uma consulta polimorfo'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2f05da1e-845b-4f14-83e4-c6353a850553
ms.openlocfilehash: 18e2bfee223fa14ec9a232fe308ad2edda6bec55
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760821"
---
# <a name="how-to-execute-a-polymorphic-query"></a><span data-ttu-id="cf679-102">Como: Executar uma consulta polimorfo</span><span class="sxs-lookup"><span data-stu-id="cf679-102">How to: Execute a Polymorphic Query</span></span>
<span data-ttu-id="cf679-103">Este tópico mostra como executar um polimórfico [!INCLUDE[esql](../../../../../includes/esql-md.md)] consultar usando o [OFTYPE](../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) operador.</span><span class="sxs-lookup"><span data-stu-id="cf679-103">This topic shows how to execute a polymorphic [!INCLUDE[esql](../../../../../includes/esql-md.md)] query using the [OFTYPE](../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) operator.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="cf679-104">Para executar o código nesse exemplo</span><span class="sxs-lookup"><span data-stu-id="cf679-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="cf679-105">Adicionar o [modelo School](http://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac) ao seu projeto e configurar seu projeto para usar o Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="cf679-105">Add the [School Model](http://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="cf679-106">Para obter mais informações, consulte [como: usar o Assistente de modelo de dados de entidade](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span><span class="sxs-lookup"><span data-stu-id="cf679-106">For more information, see [How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span></span>  
  
2.  <span data-ttu-id="cf679-107">Na página de código do seu aplicativo, adicione as seguintes instruções `using` (`Imports` no Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="cf679-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  <span data-ttu-id="cf679-108">Modificar o modelo conceitual para ter uma herança de tabela por hierrachy, seguindo as etapas em [passo a passo: mapeamento de herança - hierarquia por tabela](http://msdn.microsoft.com/library/49b685cf-9db8-4d6d-b885-8837ed238f55).</span><span class="sxs-lookup"><span data-stu-id="cf679-108">Modify the conceptual model to have a table-per-hierrachy inheritance by following the steps in [Walkthrough: Mapping Inheritance - Table-per-Hierarchy](http://msdn.microsoft.com/library/49b685cf-9db8-4d6d-b885-8837ed238f55).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf679-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cf679-109">Example</span></span>  
 <span data-ttu-id="cf679-110">O seguinte exemplo usa um operador de OFTYPE para obter e exibir uma coleção somente de `OnsiteCourses` de uma coleção de `Courses`.</span><span class="sxs-lookup"><span data-stu-id="cf679-110">The following example uses an OFTYPE operator to get and display a collection of only `OnsiteCourses` from a collection of `Courses`.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#polymorphicquery)]
 [!code-vb[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#polymorphicquery)]  
  
## <a name="see-also"></a><span data-ttu-id="cf679-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cf679-111">See Also</span></span>  
 [<span data-ttu-id="cf679-112">Provedor EntityClient para Entity Framework</span><span class="sxs-lookup"><span data-stu-id="cf679-112">EntityClient Provider for the Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
 <span data-ttu-id="cf679-113">[Entity SQL Language](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) (Linguagem SQL de entidade)</span><span class="sxs-lookup"><span data-stu-id="cf679-113">[Entity SQL Language](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)</span></span>
