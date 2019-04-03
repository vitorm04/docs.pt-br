---
title: Operador New (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 630b0c48def77449f426b287a26f95af7cfb930e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837677"
---
# <a name="new-operator-visual-basic"></a><span data-ttu-id="d3f10-102">Operador New (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d3f10-102">New Operator (Visual Basic)</span></span>
<span data-ttu-id="d3f10-103">Apresenta uma `New` cláusula para criar uma nova instância de objeto, especifica uma restrição de construtor em um parâmetro de tipo, ou identifica um `Sub` procedimento como um construtor de classe.</span><span class="sxs-lookup"><span data-stu-id="d3f10-103">Introduces a `New` clause to create a new object instance, specifies a constructor constraint on a type parameter, or identifies a `Sub` procedure as a class constructor.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3f10-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="d3f10-104">Remarks</span></span>  
 <span data-ttu-id="d3f10-105">Em uma declaração ou instrução de atribuição, um `New` cláusula deve especificar uma classe definida do qual a instância pode ser criada.</span><span class="sxs-lookup"><span data-stu-id="d3f10-105">In a declaration or assignment statement, a `New` clause must specify a defined class from which the instance can be created.</span></span> <span data-ttu-id="d3f10-106">Isso significa que a classe deve expor um ou mais construtores que o código de chamada pode acessar.</span><span class="sxs-lookup"><span data-stu-id="d3f10-106">This means that the class must expose one or more constructors that the calling code can access.</span></span>  
  
 <span data-ttu-id="d3f10-107">Você pode usar um `New` cláusula em uma instrução de declaração ou uma instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="d3f10-107">You can use a `New` clause in a declaration statement or an assignment statement.</span></span> <span data-ttu-id="d3f10-108">Quando a instrução é executado, ele chama o construtor apropriado da classe especificada, passando quaisquer argumentos fornecidos por você.</span><span class="sxs-lookup"><span data-stu-id="d3f10-108">When the statement runs, it calls the appropriate constructor of the specified class, passing any arguments you have supplied.</span></span> <span data-ttu-id="d3f10-109">O exemplo a seguir demonstra isso com a criação de instâncias de um `Customer` classe que tem dois construtores, um que não usa nenhum parâmetro e um que utiliza um parâmetro de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="d3f10-109">The following example demonstrates this by creating instances of a `Customer` class that has two constructors, one that takes no parameters and one that takes a string parameter.</span></span>  
  
 [!code-vb[VbVbalrKeywords#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#11)]  
  
 <span data-ttu-id="d3f10-110">Uma vez que as matrizes são classes, `New` pode criar uma nova instância de matriz, conforme mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="d3f10-110">Since arrays are classes, `New` can create a new array instance, as shown in the following examples.</span></span>  
  
 [!code-vb[VbVbalrKeywords#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#12)]  
  
 <span data-ttu-id="d3f10-111">O common language runtime (CLR) lançará um <xref:System.OutOfMemoryException> erro se não houver memória suficiente para criar a nova instância.</span><span class="sxs-lookup"><span data-stu-id="d3f10-111">The common language runtime (CLR) throws an <xref:System.OutOfMemoryException> error if there is insufficient memory to create the new instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d3f10-112">O `New` palavra-chave também é usado em listas de parâmetros de tipo para especificar que o tipo fornecido deve expor um construtor sem parâmetros acessível.</span><span class="sxs-lookup"><span data-stu-id="d3f10-112">The `New` keyword is also used in type parameter lists to specify that the supplied type must expose an accessible parameterless constructor.</span></span> <span data-ttu-id="d3f10-113">Para obter mais informações sobre parâmetros de tipo e restrições, consulte [lista de tipos](../../../visual-basic/language-reference/statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="d3f10-113">For more information about type parameters and constraints, see [Type List](../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
 <span data-ttu-id="d3f10-114">Para criar um procedimento de construtor para uma classe, defina o nome de um `Sub` procedimento para o `New` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="d3f10-114">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="d3f10-115">Para obter mais informações, consulte [tempo de vida do objeto: Como os objetos são criados e destruídos](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="d3f10-115">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>  
  
 <span data-ttu-id="d3f10-116">O `New` palavra-chave pode ser usada nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="d3f10-116">The `New` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="d3f10-117">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="d3f10-117">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="d3f10-118">Of</span><span class="sxs-lookup"><span data-stu-id="d3f10-118">Of</span></span>](../../../visual-basic/language-reference/statements/of-clause.md)  
  
 [<span data-ttu-id="d3f10-119">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="d3f10-119">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="d3f10-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d3f10-120">See also</span></span>

- <xref:System.OutOfMemoryException>
- [<span data-ttu-id="d3f10-121">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="d3f10-121">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="d3f10-122">Lista de Tipos</span><span class="sxs-lookup"><span data-stu-id="d3f10-122">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="d3f10-123">Tipos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d3f10-123">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="d3f10-124">Tempo de vida do objeto: Como os objetos são criados e destruídos</span><span class="sxs-lookup"><span data-stu-id="d3f10-124">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
