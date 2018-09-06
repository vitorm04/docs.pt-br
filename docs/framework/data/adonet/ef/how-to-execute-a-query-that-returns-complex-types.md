---
title: 'Como: Executar uma consulta que retorna tipos complexos'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2209fdb-70ef-4dea-8bb8-097fe96f5563
ms.openlocfilehash: 013f1980d2ea13927871719aeea293cfce38b4d5
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43861888"
---
# <a name="how-to-execute-a-query-that-returns-complex-types"></a><span data-ttu-id="f4f3c-102">Como: Executar uma consulta que retorna tipos complexos</span><span class="sxs-lookup"><span data-stu-id="f4f3c-102">How to: Execute a Query that Returns Complex Types</span></span>
<span data-ttu-id="f4f3c-103">Este tópico mostra como executar uma consulta de [!INCLUDE[esql](../../../../../includes/esql-md.md)] que retorna os objetos do tipo de entidade que contêm uma propriedade de um tipo complexo.</span><span class="sxs-lookup"><span data-stu-id="f4f3c-103">This topic shows how to execute an [!INCLUDE[esql](../../../../../includes/esql-md.md)] query that returns entity type objects that contain a property of a complex type.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="f4f3c-104">Para executar o código nesse exemplo</span><span class="sxs-lookup"><span data-stu-id="f4f3c-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="f4f3c-105">Adicione a [modelo de vendas AdventureWorks](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) ao seu projeto e configurar seu projeto para usar o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f4f3c-105">Add the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="f4f3c-106">Para obter mais informações, consulte [como: usar o Assistente de modelo de dados de entidade](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span><span class="sxs-lookup"><span data-stu-id="f4f3c-106">For more information, see [How to: Use the Entity Data Model Wizard](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span></span>  
  
2.  <span data-ttu-id="f4f3c-107">Na página de código do seu aplicativo, adicione as seguintes instruções `using` (`Imports` no Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="f4f3c-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  <span data-ttu-id="f4f3c-108">Clique duas vezes o arquivo. edmx para exibir o modelo na [janela do navegador modelo](https://msdn.microsoft.com/library/94e836e8-a5ea-47ff-aa3e-599d8a02ebfd) do Designer de entidade.</span><span class="sxs-lookup"><span data-stu-id="f4f3c-108">Double click the .edmx file to display the model in the [Model Browser window](https://msdn.microsoft.com/library/94e836e8-a5ea-47ff-aa3e-599d8a02ebfd) of the Entity Designer.</span></span> <span data-ttu-id="f4f3c-109">Na superfície do Designer de entidade, selecione a `Email` e `Phone` propriedades da `Contact` tipo de entidade, em seguida, clique com botão direito e selecione **Refactor no novo tipo complexo**.</span><span class="sxs-lookup"><span data-stu-id="f4f3c-109">On the Entity Designer surface, select the `Email` and `Phone` properties of the `Contact` entity type, then right-click and select **Refactor into New Complex Type**.</span></span>  
  
4.  <span data-ttu-id="f4f3c-110">Um novo tipo complexo com selecionado `Email` e `Phone` propriedades é adicionado para o **Model Browser**.</span><span class="sxs-lookup"><span data-stu-id="f4f3c-110">A new complex type with the selected `Email` and `Phone` properties is added to the **Model Browser**.</span></span> <span data-ttu-id="f4f3c-111">O tipo complexo recebe um nome padrão: renomeie o tipo para `EmailPhone` no **propriedades** janela.</span><span class="sxs-lookup"><span data-stu-id="f4f3c-111">The complex type is given a default name: rename the type to `EmailPhone` in the **Properties** window.</span></span> <span data-ttu-id="f4f3c-112">Além disso, uma nova propriedade de `ComplexProperty` é adicionada ao tipo de entidade de `Contact` .</span><span class="sxs-lookup"><span data-stu-id="f4f3c-112">Also, a new `ComplexProperty` property is added to the `Contact` entity type.</span></span> <span data-ttu-id="f4f3c-113">Renomear a propriedade a `EmailPhoneComplexType.`</span><span class="sxs-lookup"><span data-stu-id="f4f3c-113">Rename the property to `EmailPhoneComplexType.`</span></span>  
  
     <span data-ttu-id="f4f3c-114">Para obter informações sobre como criar e modificar tipos complexos usando o Assistente de modelo de dados de entidade, consulte [como: refatorar as propriedades existentes em uma propriedade de tipo complexos](https://msdn.microsoft.com/library/5b2eb3b3-693d-42cb-b43a-405812d677eb) e [como: criar e modificar tipos complexos](https://msdn.microsoft.com/library/afb8e206-0ffe-4597-b6d4-6ab566897e1d).</span><span class="sxs-lookup"><span data-stu-id="f4f3c-114">For information about creating and modifying complex types by using the Entity Data Model Wizard, see [How to: Refactor Existing Properties into a Complex Type Property](https://msdn.microsoft.com/library/5b2eb3b3-693d-42cb-b43a-405812d677eb) and [How to: Create and Modify Complex Types](https://msdn.microsoft.com/library/afb8e206-0ffe-4597-b6d4-6ab566897e1d).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4f3c-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f4f3c-115">Example</span></span>  
 <span data-ttu-id="f4f3c-116">O exemplo a seguir executa uma consulta que retorna uma coleção de `Contact` objetos e exibe duas propriedades do `Contact` objetos: `ContactID` e os valores da `EmailPhoneComplexType` tipo complexo.</span><span class="sxs-lookup"><span data-stu-id="f4f3c-116">The following example executes a query that returns a collection of `Contact` objects and displays two properties of the `Contact` objects: `ContactID` and the values of the `EmailPhoneComplexType` complex type.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]
