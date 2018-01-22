---
title: Como executar uma consulta Entity SQL parametrizada usando EntityCommand
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: e93fea43-7e03-4d7d-9fee-2517b8b88cba
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d43be857e4f920a1ce36625d9be207b9025ff423
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-execute-a-parameterized-entity-sql-query-using-entitycommand"></a><span data-ttu-id="a31b7-102">Como executar uma consulta Entity SQL parametrizada usando EntityCommand</span><span class="sxs-lookup"><span data-stu-id="a31b7-102">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>
<span data-ttu-id="a31b7-103">Este tópico mostra como executar um [!INCLUDE[esql](../../../../../includes/esql-md.md)] consulta com parâmetros usando um <xref:System.Data.EntityClient.EntityCommand> objeto.</span><span class="sxs-lookup"><span data-stu-id="a31b7-103">This topic shows how to execute an [!INCLUDE[esql](../../../../../includes/esql-md.md)] query that has parameters by using an <xref:System.Data.EntityClient.EntityCommand> object.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="a31b7-104">Para executar o código nesse exemplo</span><span class="sxs-lookup"><span data-stu-id="a31b7-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="a31b7-105">Adicionar o [modelo de vendas do AdventureWorks](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) ao seu projeto e configurar seu projeto para usar o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a31b7-105">Add the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="a31b7-106">Para obter mais informações, consulte [como: usar o Assistente de modelo de dados de entidade](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span><span class="sxs-lookup"><span data-stu-id="a31b7-106">For more information, see [How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span></span>  
  
2.  <span data-ttu-id="a31b7-107">Na página de código do seu aplicativo, adicione as seguintes instruções `using` (`Imports` no Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="a31b7-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="a31b7-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a31b7-108">Example</span></span>  
 <span data-ttu-id="a31b7-109">O exemplo a seguir mostra como construir uma cadeia de caracteres de consulta com dois parâmetros.</span><span class="sxs-lookup"><span data-stu-id="a31b7-109">The following example shows how to construct a query string with two parameters.</span></span> <span data-ttu-id="a31b7-110">Depois, ele cria um <xref:System.Data.EntityClient.EntityCommand>, adiciona dois parâmetros à coleção <xref:System.Data.EntityClient.EntityParameter> desse <xref:System.Data.EntityClient.EntityCommand> e itera pela coleção de itens `Contact`.</span><span class="sxs-lookup"><span data-stu-id="a31b7-110">It then creates an <xref:System.Data.EntityClient.EntityCommand>, adds two parameters to the <xref:System.Data.EntityClient.EntityParameter> collection of that <xref:System.Data.EntityClient.EntityCommand>, and iterates through the collection of `Contact` items.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#parameterizedquerywithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#parameterizedquerywithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="a31b7-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a31b7-111">See Also</span></span>  
 [<span data-ttu-id="a31b7-112">Como: executar uma consulta parametrizada</span><span class="sxs-lookup"><span data-stu-id="a31b7-112">How to: Execute a Parameterized Query</span></span>](http://msdn.microsoft.com/library/42048f03-c65c-4d98-b50a-3e7d537a63e8)  
 <span data-ttu-id="a31b7-113">[Entity SQL Language](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) (Linguagem SQL de entidade)</span><span class="sxs-lookup"><span data-stu-id="a31b7-113">[Entity SQL Language](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)</span></span>
