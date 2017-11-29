---
title: Operador New (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.new
- vb.NewConstraint
helpviewer_keywords:
- constraints, Visual Basic generic types
- generics [Visual Basic], constraints
- constraints, New keyword [Visual Basic]
- New constraint
- New keyword [Visual Basic]
ms.assetid: d7d566d7-fe0e-4336-91f7-641a542de4d0
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 74f0352379e861ad135ea23d31ea07d638f9e6c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="new-operator-visual-basic"></a><span data-ttu-id="a6878-102">Operador New (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a6878-102">New Operator (Visual Basic)</span></span>
<span data-ttu-id="a6878-103">Apresenta um `New` cláusula para criar uma nova instância de objeto, especifica uma restrição de construtor em um parâmetro de tipo ou identifica um `Sub` procedimento como um construtor de classe.</span><span class="sxs-lookup"><span data-stu-id="a6878-103">Introduces a `New` clause to create a new object instance, specifies a constructor constraint on a type parameter, or identifies a `Sub` procedure as a class constructor.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6878-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="a6878-104">Remarks</span></span>  
 <span data-ttu-id="a6878-105">Em uma declaração ou instrução de atribuição, um `New` cláusula deve especificar uma classe definida na qual a instância pode ser criada.</span><span class="sxs-lookup"><span data-stu-id="a6878-105">In a declaration or assignment statement, a `New` clause must specify a defined class from which the instance can be created.</span></span> <span data-ttu-id="a6878-106">Isso significa que a classe deve expor um ou mais construtores que pode acessar o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="a6878-106">This means that the class must expose one or more constructors that the calling code can access.</span></span>  
  
 <span data-ttu-id="a6878-107">Você pode usar um `New` cláusula em uma instrução de declaração ou uma instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="a6878-107">You can use a `New` clause in a declaration statement or an assignment statement.</span></span> <span data-ttu-id="a6878-108">Quando a instrução é executada, ele chama o construtor apropriado da classe especificada, passando quaisquer argumentos que você forneceu.</span><span class="sxs-lookup"><span data-stu-id="a6878-108">When the statement runs, it calls the appropriate constructor of the specified class, passing any arguments you have supplied.</span></span> <span data-ttu-id="a6878-109">O exemplo a seguir demonstra isso ao criar instâncias de um `Customer` classe que tem dois construtores, um que não usa nenhum parâmetro e outro que usa um parâmetro de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a6878-109">The following example demonstrates this by creating instances of a `Customer` class that has two constructors, one that takes no parameters and one that takes a string parameter.</span></span>  
  
 [!code-vb[VbVbalrKeywords#11](../../../visual-basic/language-reference/codesnippet/VisualBasic/new-operator_1.vb)]  
  
 <span data-ttu-id="a6878-110">Como matrizes são classes, `New` pode criar uma nova instância de matriz, conforme mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="a6878-110">Since arrays are classes, `New` can create a new array instance, as shown in the following examples.</span></span>  
  
 [!code-vb[VbVbalrKeywords#12](../../../visual-basic/language-reference/codesnippet/VisualBasic/new-operator_2.vb)]  
  
 <span data-ttu-id="a6878-111">O common language runtime (CLR) gera um <xref:System.OutOfMemoryException> erro se não houver memória suficiente para criar a nova instância.</span><span class="sxs-lookup"><span data-stu-id="a6878-111">The common language runtime (CLR) throws an <xref:System.OutOfMemoryException> error if there is insufficient memory to create the new instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a6878-112">O `New` palavra-chave também é usado em listas de parâmetros de tipo para especificar que o tipo fornecido deve expor um construtor acessível sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="a6878-112">The `New` keyword is also used in type parameter lists to specify that the supplied type must expose an accessible parameterless constructor.</span></span> <span data-ttu-id="a6878-113">Para obter mais informações sobre os parâmetros de tipo e restrições, consulte [lista tipo](../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="a6878-113">For more information about type parameters and constraints, see [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
 <span data-ttu-id="a6878-114">Para criar um procedimento de construtor para uma classe, defina o nome de um `Sub` procedimento para o `New` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="a6878-114">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="a6878-115">Para obter mais informações, consulte [vida útil do objeto: como os objetos são criados e Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="a6878-115">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>  
  
 <span data-ttu-id="a6878-116">O `New` palavra-chave pode ser usada nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="a6878-116">The `New` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="a6878-117">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="a6878-117">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="a6878-118">Of</span><span class="sxs-lookup"><span data-stu-id="a6878-118">Of</span></span>](../../../visual-basic/language-reference/statements/of-clause.md)  
  
 [<span data-ttu-id="a6878-119">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="a6878-119">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="a6878-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a6878-120">See Also</span></span>  
 <xref:System.OutOfMemoryException>  
 [<span data-ttu-id="a6878-121">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="a6878-121">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="a6878-122">Lista de Tipos</span><span class="sxs-lookup"><span data-stu-id="a6878-122">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)  
 [<span data-ttu-id="a6878-123">Tipos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a6878-123">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="a6878-124">Tempo de vida do objeto: como os objetos são criados e destruídos</span><span class="sxs-lookup"><span data-stu-id="a6878-124">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
