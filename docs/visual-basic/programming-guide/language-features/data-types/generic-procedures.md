---
title: Procedimentos genéricos no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- generic methods [Visual Basic], type inference
- generics [Visual Basic], type inference
- procedures [Visual Basic], generic
- generic procedures
- type inference, generics
- generic methods [Visual Basic]
- type inference
- generics [Visual Basic], procedures
- generic procedures [Visual Basic], type inference
ms.assetid: 95577b28-137f-4d5c-a149-919c828600e5
ms.openlocfilehash: 9a88a979a6b46f897e5f04f4481d4a23e245b165
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2018
ms.locfileid: "45969766"
---
# <a name="generic-procedures-in-visual-basic"></a><span data-ttu-id="59ae4-102">Procedimentos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="59ae4-102">Generic Procedures in Visual Basic</span></span>
<span data-ttu-id="59ae4-103">Um *procedimento genérico*, também chamado um *método genérico*, é um procedimento definido pelo menos um parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="59ae4-103">A *generic procedure*, also called a *generic method*, is a procedure defined with at least one type parameter.</span></span> <span data-ttu-id="59ae4-104">Isso permite que o código de chamada personalizar os tipos de dados para seus requisitos de cada vez que ele chama o procedimento.</span><span class="sxs-lookup"><span data-stu-id="59ae4-104">This allows the calling code to tailor the data types to its requirements each time it calls the procedure.</span></span>  
  
 <span data-ttu-id="59ae4-105">Um procedimento não é genérico simplesmente em virtude de que está sendo definido dentro de uma classe genérica ou uma estrutura genérica.</span><span class="sxs-lookup"><span data-stu-id="59ae4-105">A procedure is not generic simply by virtue of being defined inside a generic class or a generic structure.</span></span> <span data-ttu-id="59ae4-106">Para ser genérico, o procedimento tenha pelo menos um parâmetro de tipo, além de quaisquer parâmetros normais, pode levar.</span><span class="sxs-lookup"><span data-stu-id="59ae4-106">To be generic, the procedure must take at least one type parameter, in addition to any normal parameters it might take.</span></span> <span data-ttu-id="59ae4-107">Uma classe genérica ou estrutura pode conter procedimentos não genéricos e uma classe não genérica, estrutura, ou módulo pode conter procedimentos genéricos.</span><span class="sxs-lookup"><span data-stu-id="59ae4-107">A generic class or structure can contain nongeneric procedures, and a nongeneric class, structure, or module can contain generic procedures.</span></span>  
  
 <span data-ttu-id="59ae4-108">Um procedimento genérico pode usar seus parâmetros de tipo na lista de parâmetros normais, em seu tipo de retorno se ele tiver um e em seu procedimento de código.</span><span class="sxs-lookup"><span data-stu-id="59ae4-108">A generic procedure can use its type parameters in its normal parameter list, in its return type if it has one, and in its procedure code.</span></span>  
  
## <a name="type-inference"></a><span data-ttu-id="59ae4-109">Inferência de tipos</span><span class="sxs-lookup"><span data-stu-id="59ae4-109">Type Inference</span></span>  
 <span data-ttu-id="59ae4-110">Você pode chamar um procedimento genérico sem fornecer quaisquer argumentos de tipo em todos os.</span><span class="sxs-lookup"><span data-stu-id="59ae4-110">You can call a generic procedure without supplying any type arguments at all.</span></span> <span data-ttu-id="59ae4-111">Se você chamá-lo dessa forma, o compilador tentará determinar os tipos de dados apropriado para passar para os argumentos de tipo do procedimento.</span><span class="sxs-lookup"><span data-stu-id="59ae4-111">If you call it this way, the compiler attempts to determine the appropriate data types to pass to the procedure's type arguments.</span></span> <span data-ttu-id="59ae4-112">Isso é chamado *inferência de tipo*.</span><span class="sxs-lookup"><span data-stu-id="59ae4-112">This is called *type inference*.</span></span> <span data-ttu-id="59ae4-113">O código a seguir mostra uma chamada na qual o compilador infere que ele deve passar o tipo `String` para o parâmetro de tipo `t`.</span><span class="sxs-lookup"><span data-stu-id="59ae4-113">The following code shows a call in which the compiler infers that it should pass type `String` to the type parameter `t`.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#15](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_1.vb)]  
  
 <span data-ttu-id="59ae4-114">Se o compilador não é possível inferir os argumentos de tipo do contexto de sua chamada, ele relatará um erro.</span><span class="sxs-lookup"><span data-stu-id="59ae4-114">If the compiler cannot infer the type arguments from the context of your call, it reports an error.</span></span> <span data-ttu-id="59ae4-115">Uma possível causa desse erro é uma incompatibilidade de classificação de matriz.</span><span class="sxs-lookup"><span data-stu-id="59ae4-115">One possible cause of such an error is an array rank mismatch.</span></span> <span data-ttu-id="59ae4-116">Por exemplo, suponha que você definir um parâmetro normal como uma matriz de um parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="59ae4-116">For example, suppose you define a normal parameter as an array of a type parameter.</span></span> <span data-ttu-id="59ae4-117">Se você chamar o procedimento genérico fornecendo uma matriz de uma classificação diferente (número de dimensões), a incompatibilidade faz com que a inferência de tipo falhar.</span><span class="sxs-lookup"><span data-stu-id="59ae4-117">If you call the generic procedure supplying an array of a different rank (number of dimensions), the mismatch causes type inference to fail.</span></span> <span data-ttu-id="59ae4-118">O código a seguir mostra uma chamada em que uma matriz bidimensional é passada para um procedimento que espera uma matriz unidimensional.</span><span class="sxs-lookup"><span data-stu-id="59ae4-118">The following code shows a call in which a two-dimensional array is passed to a procedure that expects a one-dimensional array.</span></span>  
  
```vb  
Public Sub demoSub(Of t)(ByVal arg() As t)
End Sub

Public Sub callDemoSub()
    Dim twoDimensions(,) As Integer
    demoSub(twoDimensions)
End Sub
```
  
 <span data-ttu-id="59ae4-119">Você pode invocar a inferência de tipo omitindo todos os argumentos de tipo.</span><span class="sxs-lookup"><span data-stu-id="59ae4-119">You can invoke type inference only by omitting all the type arguments.</span></span> <span data-ttu-id="59ae4-120">Se você fornecer um argumento de tipo, você deve fornecer todos eles.</span><span class="sxs-lookup"><span data-stu-id="59ae4-120">If you supply one type argument, you must supply them all.</span></span>  
  
 <span data-ttu-id="59ae4-121">Inferência de tipo tem suporte apenas para procedimentos genéricos.</span><span class="sxs-lookup"><span data-stu-id="59ae4-121">Type inference is supported only for generic procedures.</span></span> <span data-ttu-id="59ae4-122">Você não pode invocar a inferência de tipo em classes genéricas, estruturas, interfaces ou delegados.</span><span class="sxs-lookup"><span data-stu-id="59ae4-122">You cannot invoke type inference on generic classes, structures, interfaces, or delegates.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59ae4-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="59ae4-123">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="59ae4-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="59ae4-124">Description</span></span>  
 <span data-ttu-id="59ae4-125">O exemplo a seguir define um genérico `Function` procedimento para localizar um elemento específico em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="59ae4-125">The following example defines a generic `Function` procedure to find a particular element in an array.</span></span> <span data-ttu-id="59ae4-126">Ele define um parâmetro de tipo e usa-o para construir os dois parâmetros na lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="59ae4-126">It defines one type parameter and uses it to construct the two parameters in the parameter list.</span></span>  
  
### <a name="code"></a><span data-ttu-id="59ae4-127">Código</span><span class="sxs-lookup"><span data-stu-id="59ae4-127">Code</span></span>  
 [!code-vb[VbVbalrDataTypes#14](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_2.vb)]  
  
### <a name="comments"></a><span data-ttu-id="59ae4-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="59ae4-128">Comments</span></span>  
 <span data-ttu-id="59ae4-129">O exemplo anterior requer a capacidade de comparar `searchValue` com cada elemento de `searchArray`.</span><span class="sxs-lookup"><span data-stu-id="59ae4-129">The preceding example requires the ability to compare `searchValue` against each element of `searchArray`.</span></span> <span data-ttu-id="59ae4-130">Para garantir essa capacidade, ela restringe o parâmetro de tipo `T` para implementar o <xref:System.IComparable%601> interface.</span><span class="sxs-lookup"><span data-stu-id="59ae4-130">To guarantee this ability, it constrains the type parameter `T` to implement the <xref:System.IComparable%601> interface.</span></span> <span data-ttu-id="59ae4-131">O código usa o <xref:System.IComparable%601.CompareTo%2A> método em vez do `=` operador, porque não há nenhuma garantia de que um argumento de tipo fornecido para `T` dá suporte a `=` operador.</span><span class="sxs-lookup"><span data-stu-id="59ae4-131">The code uses the <xref:System.IComparable%601.CompareTo%2A> method instead of the `=` operator, because there is no guarantee that a type argument supplied for `T` supports the `=` operator.</span></span>  
  
 <span data-ttu-id="59ae4-132">Você pode testar o `findElement` procedimento com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="59ae4-132">You can test the `findElement` procedure with the following code.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#13](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_3.vb)]  
  
 <span data-ttu-id="59ae4-133">As chamadas anteriores para `MsgBox` exibir "0", "1" e "-1", respectivamente.</span><span class="sxs-lookup"><span data-stu-id="59ae4-133">The preceding calls to `MsgBox` display "0", "1", and "-1" respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59ae4-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="59ae4-134">See Also</span></span>  
 [<span data-ttu-id="59ae4-135">Tipos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="59ae4-135">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="59ae4-136">Como definir uma classe capaz de fornecer uma funcionalidade idêntica em tipos de dados diferentes</span><span class="sxs-lookup"><span data-stu-id="59ae4-136">How to: Define a Class That Can Provide Identical Functionality on Different Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)  
 [<span data-ttu-id="59ae4-137">Como usar uma classe genérica</span><span class="sxs-lookup"><span data-stu-id="59ae4-137">How to: Use a Generic Class</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [<span data-ttu-id="59ae4-138">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="59ae4-138">Procedures</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="59ae4-139">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="59ae4-139">Procedure Parameters and Arguments</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="59ae4-140">Lista de Tipos</span><span class="sxs-lookup"><span data-stu-id="59ae4-140">Type List</span></span>](../../../../visual-basic/language-reference/statements/type-list.md)  
 [<span data-ttu-id="59ae4-141">Lista de Parâmetros</span><span class="sxs-lookup"><span data-stu-id="59ae4-141">Parameter List</span></span>](../../../../visual-basic/language-reference/statements/parameter-list.md)
