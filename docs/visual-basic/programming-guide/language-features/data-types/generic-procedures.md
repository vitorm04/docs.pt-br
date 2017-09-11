---
title: "Procedimentos genéricos no Visual Basic | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- generic methods, type inference
- generics [Visual Basic], type inference
- procedures, generic
- generic procedures
- type inference, generics
- generic methods
- type inference
- generics [Visual Basic], procedures
- generic procedures, type inference
ms.assetid: 95577b28-137f-4d5c-a149-919c828600e5
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: ade019295137d6c526a28b3b2c72d1bdc8faf053
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="generic-procedures-in-visual-basic"></a><span data-ttu-id="9e875-102">Procedimentos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9e875-102">Generic Procedures in Visual Basic</span></span>
<span data-ttu-id="9e875-103">A *procedimento genérico*, também chamado um *método genérico*, é um procedimento definido pelo menos um parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="9e875-103">A *generic procedure*, also called a *generic method*, is a procedure defined with at least one type parameter.</span></span> <span data-ttu-id="9e875-104">Isso permite que o código de chamada adapte os tipos de dados para seus requisitos de cada vez que ele chama o procedimento.</span><span class="sxs-lookup"><span data-stu-id="9e875-104">This allows the calling code to tailor the data types to its requirements each time it calls the procedure.</span></span>  
  
 <span data-ttu-id="9e875-105">Um procedimento não é genérico simplesmente por que está sendo definido dentro de uma classe genérica ou uma estrutura genérica.</span><span class="sxs-lookup"><span data-stu-id="9e875-105">A procedure is not generic simply by virtue of being defined inside a generic class or a generic structure.</span></span> <span data-ttu-id="9e875-106">Para ser genérico, o procedimento deve levar pelo menos um parâmetro de tipo, além de qualquer parâmetro normal que pode demorar.</span><span class="sxs-lookup"><span data-stu-id="9e875-106">To be generic, the procedure must take at least one type parameter, in addition to any normal parameters it might take.</span></span> <span data-ttu-id="9e875-107">Uma classe ou estrutura genérica pode conter procedimentos não genéricos e uma classe genérica, estrutura, ou módulo pode conter procedimentos genéricos.</span><span class="sxs-lookup"><span data-stu-id="9e875-107">A generic class or structure can contain nongeneric procedures, and a nongeneric class, structure, or module can contain generic procedures.</span></span>  
  
 <span data-ttu-id="9e875-108">Um procedimento genérico pode usar seus parâmetros de tipo em sua lista de parâmetros normais, em seu tipo de retorno se ele tiver um e em seu procedimento de código.</span><span class="sxs-lookup"><span data-stu-id="9e875-108">A generic procedure can use its type parameters in its normal parameter list, in its return type if it has one, and in its procedure code.</span></span>  
  
## <a name="type-inference"></a><span data-ttu-id="9e875-109">Inferência de tipos</span><span class="sxs-lookup"><span data-stu-id="9e875-109">Type Inference</span></span>  
 <span data-ttu-id="9e875-110">Você pode chamar um procedimento genérico sem fornecer quaisquer argumentos de tipo algum.</span><span class="sxs-lookup"><span data-stu-id="9e875-110">You can call a generic procedure without supplying any type arguments at all.</span></span> <span data-ttu-id="9e875-111">Se você chamá-lo dessa maneira, o compilador tentará determinar os tipos de dados apropriados para passar para os argumentos de tipo do procedimento.</span><span class="sxs-lookup"><span data-stu-id="9e875-111">If you call it this way, the compiler attempts to determine the appropriate data types to pass to the procedure's type arguments.</span></span> <span data-ttu-id="9e875-112">Isso é chamado de *inferência de tipo*.</span><span class="sxs-lookup"><span data-stu-id="9e875-112">This is called *type inference*.</span></span> <span data-ttu-id="9e875-113">O código a seguir mostra uma chamada na qual o compilador infere que ele deve passar tipo `String` para o parâmetro de tipo `t`.</span><span class="sxs-lookup"><span data-stu-id="9e875-113">The following code shows a call in which the compiler infers that it should pass type `String` to the type parameter `t`.</span></span>  
  
 <span data-ttu-id="9e875-114">[!code-vb[VbVbalrDataTypes&#15;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="9e875-114">[!code-vb[VbVbalrDataTypes#15](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_1.vb)]</span></span>  
  
 <span data-ttu-id="9e875-115">Se o compilador não pode inferir os argumentos de tipo do contexto de sua chamada, ele relata um erro.</span><span class="sxs-lookup"><span data-stu-id="9e875-115">If the compiler cannot infer the type arguments from the context of your call, it reports an error.</span></span> <span data-ttu-id="9e875-116">Uma possível causa desse erro é uma incompatibilidade de classificação de matriz.</span><span class="sxs-lookup"><span data-stu-id="9e875-116">One possible cause of such an error is an array rank mismatch.</span></span> <span data-ttu-id="9e875-117">Por exemplo, suponha que você define um parâmetro normal como uma matriz de um parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="9e875-117">For example, suppose you define a normal parameter as an array of a type parameter.</span></span> <span data-ttu-id="9e875-118">Se você chamar o procedimento genérico fornecendo uma matriz de uma posição diferente (número de dimensões), a incompatibilidade fará com que inferência falha.</span><span class="sxs-lookup"><span data-stu-id="9e875-118">If you call the generic procedure supplying an array of a different rank (number of dimensions), the mismatch causes type inference to fail.</span></span> <span data-ttu-id="9e875-119">O código a seguir mostra uma chamada na qual uma matriz bidimensional é passada para um procedimento que espera uma matriz unidimensional.</span><span class="sxs-lookup"><span data-stu-id="9e875-119">The following code shows a call in which a two-dimensional array is passed to a procedure that expects a one-dimensional array.</span></span>  
  
 `Public Sub demoSub(Of t)(ByVal arg() As t)`  
  
 `End Sub`  
  
 `Public Sub callDemoSub()`  
  
 `Dim twoDimensions(,) As Integer`  
  
 `demoSub(twoDimensions)`  
  
 `End Sub`  
  
 <span data-ttu-id="9e875-120">Você pode chamar inferência de tipos somente omitindo todos os argumentos de tipo.</span><span class="sxs-lookup"><span data-stu-id="9e875-120">You can invoke type inference only by omitting all the type arguments.</span></span> <span data-ttu-id="9e875-121">Se você fornecer um argumento de tipo, você deve fornecer todos eles.</span><span class="sxs-lookup"><span data-stu-id="9e875-121">If you supply one type argument, you must supply them all.</span></span>  
  
 <span data-ttu-id="9e875-122">Inferência de tipo é suportada somente para procedimentos genéricos.</span><span class="sxs-lookup"><span data-stu-id="9e875-122">Type inference is supported only for generic procedures.</span></span> <span data-ttu-id="9e875-123">Você não pode chamar inferência de tipo em classes genéricas, estruturas, interfaces ou representantes.</span><span class="sxs-lookup"><span data-stu-id="9e875-123">You cannot invoke type inference on generic classes, structures, interfaces, or delegates.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e875-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9e875-124">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="9e875-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="9e875-125">Description</span></span>  
 <span data-ttu-id="9e875-126">O exemplo a seguir define um genérico `Function` procedimento para localizar um elemento específico em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="9e875-126">The following example defines a generic `Function` procedure to find a particular element in an array.</span></span> <span data-ttu-id="9e875-127">Ele define um parâmetro do tipo e usa-o para construir os dois parâmetros na lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="9e875-127">It defines one type parameter and uses it to construct the two parameters in the parameter list.</span></span>  
  
### <a name="code"></a><span data-ttu-id="9e875-128">Código</span><span class="sxs-lookup"><span data-stu-id="9e875-128">Code</span></span>  
 <span data-ttu-id="9e875-129">[!code-vb[VbVbalrDataTypes&#14;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="9e875-129">[!code-vb[VbVbalrDataTypes#14](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_2.vb)]</span></span>  
  
### <a name="comments"></a><span data-ttu-id="9e875-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="9e875-130">Comments</span></span>  
 <span data-ttu-id="9e875-131">O exemplo anterior requer a capacidade de comparar `searchValue` com cada elemento de `searchArray`.</span><span class="sxs-lookup"><span data-stu-id="9e875-131">The preceding example requires the ability to compare `searchValue` against each element of `searchArray`.</span></span> <span data-ttu-id="9e875-132">Para garantir essa capacidade, ele restringe o parâmetro de tipo `T` para implementar o <xref:System.IComparable%601>interface.</xref:System.IComparable%601></span><span class="sxs-lookup"><span data-stu-id="9e875-132">To guarantee this ability, it constrains the type parameter `T` to implement the <xref:System.IComparable%601> interface.</span></span> <span data-ttu-id="9e875-133">O código usa o <xref:System.IComparable%601.CompareTo%2A>método em vez do `=` operador, porque não há nenhuma garantia de que um argumento de tipo fornecido para `T` oferece suporte a `=` operador.</xref:System.IComparable%601.CompareTo%2A></span><span class="sxs-lookup"><span data-stu-id="9e875-133">The code uses the <xref:System.IComparable%601.CompareTo%2A> method instead of the `=` operator, because there is no guarantee that a type argument supplied for `T` supports the `=` operator.</span></span>  
  
 <span data-ttu-id="9e875-134">Você pode testar o `findElement` procedimento com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="9e875-134">You can test the `findElement` procedure with the following code.</span></span>  
  
 <span data-ttu-id="9e875-135">[!code-vb[VbVbalrDataTypes&13;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="9e875-135">[!code-vb[VbVbalrDataTypes#13](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-procedures_3.vb)]</span></span>  
  
 <span data-ttu-id="9e875-136">As chamadas anteriores para `MsgBox` exibem "0", "1" e "-1", respectivamente.</span><span class="sxs-lookup"><span data-stu-id="9e875-136">The preceding calls to `MsgBox` display "0", "1", and "-1" respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e875-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9e875-137">See Also</span></span>  
 <span data-ttu-id="9e875-138">[Tipos genéricos no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span><span class="sxs-lookup"><span data-stu-id="9e875-138">[Generic Types in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span></span>  
<span data-ttu-id="9e875-139"> [Como: definir uma classe que pode fornecer funcionalidade idêntica em diferentes tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="9e875-139"> [How to: Define a Class That Can Provide Identical Functionality on Different Data Types](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md) </span></span>  
<span data-ttu-id="9e875-140"> [Como: usar uma classe genérica](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md) </span><span class="sxs-lookup"><span data-stu-id="9e875-140"> [How to: Use a Generic Class](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md) </span></span>  
<span data-ttu-id="9e875-141"> [Procedimentos](../../../../visual-basic/programming-guide/language-features/procedures/index.md) </span><span class="sxs-lookup"><span data-stu-id="9e875-141"> [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md) </span></span>  
<span data-ttu-id="9e875-142"> [Argumentos e parâmetros de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="9e875-142"> [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="9e875-143"> [Lista de tipos](../../../../visual-basic/language-reference/statements/type-list.md) </span><span class="sxs-lookup"><span data-stu-id="9e875-143"> [Type List](../../../../visual-basic/language-reference/statements/type-list.md) </span></span>  
<span data-ttu-id="9e875-144"> [Lista de Parâmetros](../../../../visual-basic/language-reference/statements/parameter-list.md)</span><span class="sxs-lookup"><span data-stu-id="9e875-144"> [Parameter List](../../../../visual-basic/language-reference/statements/parameter-list.md)</span></span>
