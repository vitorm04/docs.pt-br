---
title: 'Como: Executar um procedimento armazenado parametrizado usando EntityCommand'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4f5639bf-bb7f-4982-bb1d-c7caa4348888
ms.openlocfilehash: 973a1f3980c979b201b083eed3eb20a64461a3cb
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507407"
---
# <a name="how-to-execute-a-parameterized-stored-procedure-using-entitycommand"></a><span data-ttu-id="9fc33-102">Como: Executar um procedimento armazenado parametrizado usando EntityCommand</span><span class="sxs-lookup"><span data-stu-id="9fc33-102">How to: Execute a Parameterized Stored Procedure Using EntityCommand</span></span>
<span data-ttu-id="9fc33-103">Este tópico mostra como executar um procedimento armazenado parametrizado usando a classe de <xref:System.Data.EntityClient.EntityCommand> .</span><span class="sxs-lookup"><span data-stu-id="9fc33-103">This topic shows how to execute a parameterized stored procedure by using the <xref:System.Data.EntityClient.EntityCommand> class.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="9fc33-104">Para executar o código nesse exemplo</span><span class="sxs-lookup"><span data-stu-id="9fc33-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="9fc33-105">Adicione a [modelo de escola](https://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac) ao seu projeto e configurar seu projeto para usar o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9fc33-105">Add the [School Model](https://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="9fc33-106">Para obter mais informações, consulte [como: usar o Assistente de modelo de dados de entidade](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span><span class="sxs-lookup"><span data-stu-id="9fc33-106">For more information, see [How to: Use the Entity Data Model Wizard](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span></span>  
  
2.  <span data-ttu-id="9fc33-107">Na página de código do seu aplicativo, adicione as seguintes instruções `using` (`Imports` no Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="9fc33-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  <span data-ttu-id="9fc33-108">Importar o procedimento armazenado `GetStudentGrades` e especificar entidades de `CourseGrade` como um tipo de retorno.</span><span class="sxs-lookup"><span data-stu-id="9fc33-108">Import the `GetStudentGrades` stored procedure and specify `CourseGrade` entities as a return type.</span></span> <span data-ttu-id="9fc33-109">Para obter informações sobre como importar um procedimento armazenado, consulte [como: importar um procedimento armazenado](https://msdn.microsoft.com/library/24e68bf4-bd6d-428d-bc35-92d7b8e3736d).</span><span class="sxs-lookup"><span data-stu-id="9fc33-109">For information on how to import a stored procedure, see [How to: Import a Stored Procedure](https://msdn.microsoft.com/library/24e68bf4-bd6d-428d-bc35-92d7b8e3736d).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9fc33-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9fc33-110">Example</span></span>  
 <span data-ttu-id="9fc33-111">O código a seguir executa o procedimento armazenado `GetStudentGrades` onde `StudentId` é um parâmetro necessário.</span><span class="sxs-lookup"><span data-stu-id="9fc33-111">The following code executes the `GetStudentGrades` stored procedure where `StudentId` is a required parameter.</span></span> <span data-ttu-id="9fc33-112">Os resultados são lidos em seguida <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="9fc33-112">The results are then read by an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#storedprocwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#storedprocwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="9fc33-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9fc33-113">See Also</span></span>  
 [<span data-ttu-id="9fc33-114">Provedor EntityClient para Entity Framework</span><span class="sxs-lookup"><span data-stu-id="9fc33-114">EntityClient Provider for the Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)
