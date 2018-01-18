---
title: "Como: o chamar funções definidas em consultas"
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
ms.assetid: 6c804e4d-f348-4afd-9f63-d3f0f24bc6a9
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 7a713c22b307f10ef529de5c78c002e8d67a38e8
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-call-model-defined-functions-in-queries"></a><span data-ttu-id="f7520-102">Como: o chamar funções definidas em consultas</span><span class="sxs-lookup"><span data-stu-id="f7520-102">How to: Call Model-Defined Functions in Queries</span></span>
<span data-ttu-id="f7520-103">Este tópico descreve como chamar funções que são definidas no modelo conceitual de dentro das consultas de [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="f7520-103">This topic describes how to call functions that are defined in the conceptual model from within [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries.</span></span>  
  
 <span data-ttu-id="f7520-104">O procedimento a seguir fornece um contorno de alto nível para chamar uma função do definida em uma consulta de [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="f7520-104">The procedure below provides a high-level outline for calling a model-defined function from within a [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query.</span></span> <span data-ttu-id="f7520-105">O exemplo a seguir fornece mais detalhes sobre as etapas no procedimento.</span><span class="sxs-lookup"><span data-stu-id="f7520-105">The example that follows provides more detail about the steps in the procedure.</span></span> <span data-ttu-id="f7520-106">O procedimento presume que você definiu uma função no modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="f7520-106">The procedure assumes that you have defined a function in the conceptual model.</span></span> <span data-ttu-id="f7520-107">Para obter mais informações, consulte [como: definir funções de personalizados no modelo conceitual](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f).</span><span class="sxs-lookup"><span data-stu-id="f7520-107">For more information, see [How to: Define Custom Functions in the Conceptual Model](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f).</span></span>  
  
### <a name="to-call-a-function-defined-in-the-conceptual-model"></a><span data-ttu-id="f7520-108">Para chamar uma função definida no modelo conceitual</span><span class="sxs-lookup"><span data-stu-id="f7520-108">To call a function defined in the conceptual model</span></span>  
  
1.  <span data-ttu-id="f7520-109">Adicione um método do Common Language Runtime (CLR) ao seu aplicativo que mapeia função definida no modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="f7520-109">Add a common language runtime (CLR) method to your application that maps to the function defined in the conceptual model.</span></span> <span data-ttu-id="f7520-110">Para mapear o método, você deve aplicar <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> para o método.</span><span class="sxs-lookup"><span data-stu-id="f7520-110">To map the method, you must apply an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method.</span></span> <span data-ttu-id="f7520-111">Observe que os parâmetros de <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> e de <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> de atributo é o nome do espaço do modelo conceitual e o nome da função no modelo conceitual respectivamente.</span><span class="sxs-lookup"><span data-stu-id="f7520-111">Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model respectively.</span></span> <span data-ttu-id="f7520-112">A resolução de nomes de função para LINQ diferencia maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="f7520-112">Function name resolution for LINQ is case sensitive.</span></span>  
  
2.  <span data-ttu-id="f7520-113">Chamar a função em uma consulta de [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="f7520-113">Call the function in a [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7520-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f7520-114">Example</span></span>  
 <span data-ttu-id="f7520-115">O exemplo a seguir demonstra como chamar uma função que é definida no modelo conceitual de uma consulta de [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="f7520-115">The following example demonstrates how to call a function that is defined in the conceptual model from within a [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query.</span></span> <span data-ttu-id="f7520-116">O exemplo usa o modelo de escola.</span><span class="sxs-lookup"><span data-stu-id="f7520-116">The example uses the School model.</span></span> <span data-ttu-id="f7520-117">Para obter informações sobre o modelo de escola, consulte [criando o banco de dados de exemplo School](http://msdn.microsoft.com/en-us/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0) e [gerando o EDMX escola arquivo](http://msdn.microsoft.com/en-us/c48b3907-a8be-4fe6-884c-e95af1852758).</span><span class="sxs-lookup"><span data-stu-id="f7520-117">For information about the School model, see [Creating the School Sample Database](http://msdn.microsoft.com/en-us/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0) and [Generating the School .edmx File](http://msdn.microsoft.com/en-us/c48b3907-a8be-4fe6-884c-e95af1852758).</span></span>  
  
 <span data-ttu-id="f7520-118">A função a seguir o modelo conceitual retorna o número de anos como um instrutor foi contratado.</span><span class="sxs-lookup"><span data-stu-id="f7520-118">The following conceptual model function returns the number of years since an instructor was hired.</span></span> <span data-ttu-id="f7520-119">Para obter informações sobre como adicionar a função a um modelo conceitual, consulte [como: definir funções de personalizados no modelo conceitual](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f).)</span><span class="sxs-lookup"><span data-stu-id="f7520-119">For information about adding the function to a conceptual model, see [How to: Define Custom Functions in the Conceptual Model](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f).)</span></span>  
  
 [!code-xml[DP ConceptualModelFunctions#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp conceptualmodelfunctions/xml/school.edmx#1)]
  
## <a name="example"></a><span data-ttu-id="f7520-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f7520-120">Example</span></span>  
 <span data-ttu-id="f7520-121">Em seguida, adicione o seguinte método ao seu aplicativo e usa <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> para mapear-lo à função de modelo conceitual:</span><span class="sxs-lookup"><span data-stu-id="f7520-121">Next, add the following method to your application and use an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to map it to the conceptual model function:</span></span>  
  
 [!code-csharp[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#2)]
 [!code-vb[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="f7520-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f7520-122">Example</span></span>  
 <span data-ttu-id="f7520-123">Agora você pode chamar a função do modelo conceitual de uma consulta de [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="f7520-123">Now you can call the conceptual model function from within a [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query.</span></span> <span data-ttu-id="f7520-124">O código a seguir chama o método para exibir todos os instrutores que foram contratados mais de dez anos há:</span><span class="sxs-lookup"><span data-stu-id="f7520-124">The following code calls the method to display all instructors that were hired more than ten years ago:</span></span>  
  
 [!code-csharp[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#3)]
 [!code-vb[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="f7520-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f7520-125">See Also</span></span>  
 [<span data-ttu-id="f7520-126">Visão geral do arquivo. edmx</span><span class="sxs-lookup"><span data-stu-id="f7520-126">.edmx File Overview</span></span>](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [<span data-ttu-id="f7520-127">Consultas no LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="f7520-127">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
 [<span data-ttu-id="f7520-128">Chamando funções em consultas LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="f7520-128">Calling Functions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
 [<span data-ttu-id="f7520-129">Como chamar funções definidas por modelo como métodos de objeto</span><span class="sxs-lookup"><span data-stu-id="f7520-129">How to: Call Model-Defined Functions as Object Methods</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)
