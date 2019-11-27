---
title: Operador New
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
ms.openlocfilehash: 27b5b4516ef729045036c36fedc24b6c576a4f61
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348311"
---
# <a name="new-operator-visual-basic"></a><span data-ttu-id="21b22-102">Operador New (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21b22-102">New Operator (Visual Basic)</span></span>

<span data-ttu-id="21b22-103">Apresenta uma cláusula `New` para criar uma nova instância de objeto, especifica uma restrição de Construtor em um parâmetro de tipo ou identifica um procedimento de `Sub` como um construtor de classe.</span><span class="sxs-lookup"><span data-stu-id="21b22-103">Introduces a `New` clause to create a new object instance, specifies a constructor constraint on a type parameter, or identifies a `Sub` procedure as a class constructor.</span></span>

## <a name="remarks"></a><span data-ttu-id="21b22-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="21b22-104">Remarks</span></span>

<span data-ttu-id="21b22-105">Em uma declaração ou instrução de atribuição, uma cláusula `New` deve especificar uma classe definida da qual a instância pode ser criada.</span><span class="sxs-lookup"><span data-stu-id="21b22-105">In a declaration or assignment statement, a `New` clause must specify a defined class from which the instance can be created.</span></span> <span data-ttu-id="21b22-106">Isso significa que a classe deve expor um ou mais construtores que o código de chamada pode acessar.</span><span class="sxs-lookup"><span data-stu-id="21b22-106">This means that the class must expose one or more constructors that the calling code can access.</span></span>

<span data-ttu-id="21b22-107">Você pode usar uma cláusula `New` em uma instrução de declaração ou uma instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="21b22-107">You can use a `New` clause in a declaration statement or an assignment statement.</span></span> <span data-ttu-id="21b22-108">Quando a instrução é executada, ela chama o construtor apropriado da classe especificada, passando os argumentos que você forneceu.</span><span class="sxs-lookup"><span data-stu-id="21b22-108">When the statement runs, it calls the appropriate constructor of the specified class, passing any arguments you have supplied.</span></span> <span data-ttu-id="21b22-109">O exemplo a seguir demonstra isso criando instâncias de uma `Customer` classe que tem dois construtores, um que não usa parâmetros e um que usa um parâmetro de cadeia de caracteres:</span><span class="sxs-lookup"><span data-stu-id="21b22-109">The following example demonstrates this by creating instances of a `Customer` class that has two constructors, one that takes no parameters and one that takes a string parameter:</span></span>

[!code-vb[VbVbalrKeywords#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#11)]

<span data-ttu-id="21b22-110">Como as matrizes são classes, `New` pode criar uma nova instância de matriz, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="21b22-110">Since arrays are classes, `New` can create a new array instance, as shown in the following example:</span></span>

[!code-vb[VbVbalrKeywords#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#12)]

<span data-ttu-id="21b22-111">O Common Language Runtime (CLR) gera um erro de <xref:System.OutOfMemoryException> se não houver memória suficiente para criar a nova instância.</span><span class="sxs-lookup"><span data-stu-id="21b22-111">The common language runtime (CLR) throws an <xref:System.OutOfMemoryException> error if there is insufficient memory to create the new instance.</span></span>

> [!NOTE]
> <span data-ttu-id="21b22-112">A palavra-chave `New` também é usada em listas de parâmetros de tipo para especificar que o tipo fornecido deve expor um construtor acessível sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="21b22-112">The `New` keyword is also used in type parameter lists to specify that the supplied type must expose an accessible parameterless constructor.</span></span> <span data-ttu-id="21b22-113">Para obter mais informações sobre parâmetros de tipo e restrições, consulte [lista de tipos](../statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="21b22-113">For more information about type parameters and constraints, see [Type List](../statements/type-list.md).</span></span>

<span data-ttu-id="21b22-114">Para criar um procedimento de construtor para uma classe, defina o nome de um procedimento `Sub` para a palavra-chave `New`.</span><span class="sxs-lookup"><span data-stu-id="21b22-114">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="21b22-115">Para obter mais informações, consulte [tempo de vida do objeto: como os objetos são criados e destruídos](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="21b22-115">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>

<span data-ttu-id="21b22-116">A palavra-chave `New` pode ser usada nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="21b22-116">The `New` keyword can be used in these contexts:</span></span>

- [<span data-ttu-id="21b22-117">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="21b22-117">Dim Statement</span></span>](../statements/dim-statement.md)
- [<span data-ttu-id="21b22-118">Of</span><span class="sxs-lookup"><span data-stu-id="21b22-118">Of</span></span>](../statements/of-clause.md)
- [<span data-ttu-id="21b22-119">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="21b22-119">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="21b22-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="21b22-120">See also</span></span>

- <xref:System.OutOfMemoryException>
- [<span data-ttu-id="21b22-121">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="21b22-121">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="21b22-122">Lista de Tipos</span><span class="sxs-lookup"><span data-stu-id="21b22-122">Type List</span></span>](../statements/type-list.md)
- [<span data-ttu-id="21b22-123">Tipos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="21b22-123">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="21b22-124">Tempo de vida do objeto: como os objetos são criados e destruídos</span><span class="sxs-lookup"><span data-stu-id="21b22-124">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
