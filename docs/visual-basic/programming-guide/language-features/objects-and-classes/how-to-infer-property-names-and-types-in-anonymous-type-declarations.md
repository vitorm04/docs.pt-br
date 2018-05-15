---
title: Como inferir nomes e tipos de propriedade em declarações de tipo anônimo (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- inferring property names [Visual Basic]
- anonymous types [Visual Basic], inferring property names and types
- inferring property types [Visual Basic]
ms.assetid: 7c748b22-913f-4d9d-b747-6b7bf296a0bc
ms.openlocfilehash: 80127c05d56162397cfa421122ddd9698750b376
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-infer-property-names-and-types-in-anonymous-type-declarations-visual-basic"></a><span data-ttu-id="31b1b-102">Como inferir nomes e tipos de propriedade em declarações de tipo anônimo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31b1b-102">How to: Infer Property Names and Types in Anonymous Type Declarations (Visual Basic)</span></span>
<span data-ttu-id="31b1b-103">Tipos anônimos não fornecem nenhum mecanismo para especificar diretamente os tipos de dados de propriedades.</span><span class="sxs-lookup"><span data-stu-id="31b1b-103">Anonymous types provide no mechanism for directly specifying the data types of properties.</span></span> <span data-ttu-id="31b1b-104">Tipos de todas as propriedades são inferidos.</span><span class="sxs-lookup"><span data-stu-id="31b1b-104">Types of all properties are inferred.</span></span> <span data-ttu-id="31b1b-105">No exemplo a seguir, os tipos de `Name` e `Price` são inferidos diretamente dos valores que são usados para inicializá-los.</span><span class="sxs-lookup"><span data-stu-id="31b1b-105">In the following example, the types of `Name` and `Price` are inferred directly from the values that are used to initialize them.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#1](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_1.vb)]  
  
 <span data-ttu-id="31b1b-106">Tipos anônimos também podem inferir nomes de propriedade e tipos de outras fontes.</span><span class="sxs-lookup"><span data-stu-id="31b1b-106">Anonymous types can also infer property names and types from other sources.</span></span> <span data-ttu-id="31b1b-107">As seções a seguir fornecem uma lista das circunstâncias onde a inferência é possível e exemplos de situações em que não é.</span><span class="sxs-lookup"><span data-stu-id="31b1b-107">The sections that follow provide a list of the circumstances where inference is possible, and examples of situations where it is not.</span></span>  
  
## <a name="successful-inference"></a><span data-ttu-id="31b1b-108">Inferência bem-sucedida</span><span class="sxs-lookup"><span data-stu-id="31b1b-108">Successful Inference</span></span>  
  
#### <a name="anonymous-types-can-infer-property-names-and-types-from-the-following-sources"></a><span data-ttu-id="31b1b-109">Tipos anônimos podem inferir nomes de propriedade e tipos das seguintes fontes:</span><span class="sxs-lookup"><span data-stu-id="31b1b-109">Anonymous types can infer property names and types from the following sources:</span></span>  
  
-   <span data-ttu-id="31b1b-110">De nomes de variável.</span><span class="sxs-lookup"><span data-stu-id="31b1b-110">From variable names.</span></span> <span data-ttu-id="31b1b-111">Tipo anônimo `anonProduct` terá duas propriedades, `productName` e `productPrice`.</span><span class="sxs-lookup"><span data-stu-id="31b1b-111">Anonymous type `anonProduct` will have two properties, `productName` and `productPrice`.</span></span> <span data-ttu-id="31b1b-112">Os tipos de dados será das variáveis do originais, `String` e `Double`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="31b1b-112">Their data types will be those of the original variables, `String` and `Double`, respectively.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#11](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_2.vb)]  
  
-   <span data-ttu-id="31b1b-113">De propriedade ou campo nomes de outros objetos.</span><span class="sxs-lookup"><span data-stu-id="31b1b-113">From property or field names of other objects.</span></span> <span data-ttu-id="31b1b-114">Por exemplo, considere um `car` objeto de um `CarClass` tipo que inclui `Name` e `ID` propriedades.</span><span class="sxs-lookup"><span data-stu-id="31b1b-114">For example, consider a `car` object of a `CarClass` type that includes `Name` and `ID` properties.</span></span> <span data-ttu-id="31b1b-115">Para criar uma nova instância de tipo anônimo, `car1`, com `Name` e `ID` propriedades que são inicializadas com os valores do `car` do objeto, você pode escrever o seguinte:</span><span class="sxs-lookup"><span data-stu-id="31b1b-115">To create a new anonymous type instance, `car1`, with `Name` and `ID` properties that are initialized with the values from the `car` object, you can write the following:</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#34](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_3.vb)]  
  
     <span data-ttu-id="31b1b-116">A declaração anterior é equivalente a mais a linha de código que define o tipo anônimo `car2`.</span><span class="sxs-lookup"><span data-stu-id="31b1b-116">The previous declaration is equivalent to the longer line of code that defines anonymous type `car2`.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#35](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_4.vb)]  
  
-   <span data-ttu-id="31b1b-117">XML dos nomes de membros.</span><span class="sxs-lookup"><span data-stu-id="31b1b-117">From XML member names.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#12](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_5.vb)]  
  
     <span data-ttu-id="31b1b-118">O tipo resultante para `anon` teria uma propriedade, `Book`, do tipo <xref:System.Collections.IEnumerable>(de XElement).</span><span class="sxs-lookup"><span data-stu-id="31b1b-118">The resulting type for `anon` would have one property, `Book`, of type <xref:System.Collections.IEnumerable>(Of XElement).</span></span>  
  
-   <span data-ttu-id="31b1b-119">De uma função que não tem parâmetros, como `SomeFunction` no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="31b1b-119">From a function that has no parameters, such as `SomeFunction` in the following example.</span></span>  
  
     `Dim sc As New SomeClass`  
  
     `Dim anon1 = New With {Key sc.SomeFunction()}`  
  
     <span data-ttu-id="31b1b-120">A variável `anon2` no código a seguir é um tipo anônimo que tem uma propriedade, um caractere chamado `First`.</span><span class="sxs-lookup"><span data-stu-id="31b1b-120">The variable `anon2` in the following code is an anonymous type that has one property, a character named `First`.</span></span> <span data-ttu-id="31b1b-121">Esse código irá exibir uma letra "E", a letra que é retornada pela função <xref:System.Linq.Enumerable.First%2A>.</span><span class="sxs-lookup"><span data-stu-id="31b1b-121">This code will display a letter "E," the letter that is returned by function <xref:System.Linq.Enumerable.First%2A>.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#13](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_6.vb)]  
  
## <a name="inference-failures"></a><span data-ttu-id="31b1b-122">Falhas de inferência</span><span class="sxs-lookup"><span data-stu-id="31b1b-122">Inference Failures</span></span>  
  
#### <a name="name-inference-will-fail-in-many-circumstances-including-the-following"></a><span data-ttu-id="31b1b-123">Nome inferência falhará em muitas circunstâncias, incluindo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="31b1b-123">Name inference will fail in many circumstances, including the following:</span></span>  
  
-   <span data-ttu-id="31b1b-124">A inferência deriva de invocação de um método, um construtor ou uma propriedade com parâmetros que requer argumentos.</span><span class="sxs-lookup"><span data-stu-id="31b1b-124">The inference derives from the invocation of a method, a constructor, or a parameterized property that requires arguments.</span></span> <span data-ttu-id="31b1b-125">A declaração anterior de `anon1` falhará se `someFunction` tem um ou mais argumentos.</span><span class="sxs-lookup"><span data-stu-id="31b1b-125">The previous declaration of `anon1` fails if `someFunction` has one or more arguments.</span></span>  
  
     `' Not valid.`  
  
     `' Dim anon3 = New With {Key sc.someFunction(someArg)}`  
  
     <span data-ttu-id="31b1b-126">Atribuição para um novo nome de propriedade resolve o problema.</span><span class="sxs-lookup"><span data-stu-id="31b1b-126">Assignment to a new property name solves the problem.</span></span>  
  
     `' Valid.`  
  
     `Dim anon4 = New With {Key .FunResult = sc.someFunction(someArg)}`  
  
-   <span data-ttu-id="31b1b-127">A inferência deriva de uma expressão complexa.</span><span class="sxs-lookup"><span data-stu-id="31b1b-127">The inference derives from a complex expression.</span></span>  
  
    ```  
    Dim aString As String = "Act "  
    ' Not valid.  
    ' Dim label = New With {Key aString & "IV"}  
    ```  
  
     <span data-ttu-id="31b1b-128">O erro pode ser resolvido atribuindo o resultado da expressão para um nome de propriedade.</span><span class="sxs-lookup"><span data-stu-id="31b1b-128">The error can be resolved by assigning the result of the expression to a property name.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#14](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_7.vb)]  
  
-   <span data-ttu-id="31b1b-129">Inferência de várias propriedades produz dois ou mais propriedades que têm o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="31b1b-129">Inference for multiple properties produces two or more properties that have the same name.</span></span> <span data-ttu-id="31b1b-130">Referência de volta a declarações nos exemplos anteriores, você não pode listar os dois `product.Name` e `car1.Name` como propriedades do mesmo tipo anônimo.</span><span class="sxs-lookup"><span data-stu-id="31b1b-130">Referring back to declarations in earlier examples, you cannot list both `product.Name` and `car1.Name` as properties of the same anonymous type.</span></span> <span data-ttu-id="31b1b-131">Isso ocorre porque o identificador inferido para cada um deles seria `Name`.</span><span class="sxs-lookup"><span data-stu-id="31b1b-131">This is because the inferred identifier for each of these would be `Name`.</span></span>  
  
     `' Not valid.`  
  
     `' Dim anon5 = New With {Key product.Name, Key car1.Name}`  
  
     <span data-ttu-id="31b1b-132">O problema pode ser resolvido atribuindo valores a nomes de propriedade distintos.</span><span class="sxs-lookup"><span data-stu-id="31b1b-132">The problem can be solved by assigning the values to distinct property names.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#36](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_8.vb)]  
  
     <span data-ttu-id="31b1b-133">Observe que as alterações caso (alterações entre letras maiusculas e minúsculas) não faça dois nomes distintos.</span><span class="sxs-lookup"><span data-stu-id="31b1b-133">Note that changes in case (changes between uppercase and lowercase letters) do not make two names distinct.</span></span>  
  
     `Dim price = 0`  
  
     `' Not valid, because Price and price are the same name.`  
  
     `' Dim anon7 = New With {Key product.Price, Key price}`  
  
-   <span data-ttu-id="31b1b-134">O tipo inicial e o valor de uma propriedade depende de outra propriedade que ainda não foi estabelecida.</span><span class="sxs-lookup"><span data-stu-id="31b1b-134">The initial type and value of one property depends on another property that is not yet established.</span></span> <span data-ttu-id="31b1b-135">Por exemplo, `.IDName = .LastName` não é válido em uma declaração de tipo anônimo, a menos que `.LastName` já foi inicializado.</span><span class="sxs-lookup"><span data-stu-id="31b1b-135">For example, `.IDName = .LastName` is not valid in an anonymous type declaration unless `.LastName` is already initialized.</span></span>  
  
     `' Not valid.`  
  
     `' Dim anon8 = New With {Key .IDName = .LastName, Key .LastName = "Jones"}`  
  
     <span data-ttu-id="31b1b-136">Neste exemplo, você pode corrigir o problema, invertendo a ordem na qual as propriedades são declaradas.</span><span class="sxs-lookup"><span data-stu-id="31b1b-136">In this example, you can fix the problem by reversing the order in which the properties are declared.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#15](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_9.vb)]  
  
-   <span data-ttu-id="31b1b-137">Um nome de propriedade do tipo anônimo é igual ao nome de um membro de <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="31b1b-137">A property name of the anonymous type is the same as the name of a member of <xref:System.Object>.</span></span> <span data-ttu-id="31b1b-138">Por exemplo, a declaração a seguir falha porque `Equals` é um método de <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="31b1b-138">For example, the following declaration fails because `Equals` is a method of <xref:System.Object>.</span></span>  
  
     `' Not valid.`  
  
     `' Dim relationsLabels1 = New With {Key .Equals = "equals", Key .Greater = _`  
  
     `'                       "greater than", Key .Less = "less than"}`  
  
     <span data-ttu-id="31b1b-139">Você pode corrigir o problema alterando o nome da propriedade:</span><span class="sxs-lookup"><span data-stu-id="31b1b-139">You can fix the problem by changing the property name:</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#16](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_10.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="31b1b-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="31b1b-140">See Also</span></span>  
 [<span data-ttu-id="31b1b-141">Inicializadores de objeto: tipos nomeados e anônimos</span><span class="sxs-lookup"><span data-stu-id="31b1b-141">Object Initializers: Named and Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [<span data-ttu-id="31b1b-142">Inferência de Tipo de Variável Local</span><span class="sxs-lookup"><span data-stu-id="31b1b-142">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="31b1b-143">Tipos Anônimos</span><span class="sxs-lookup"><span data-stu-id="31b1b-143">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [<span data-ttu-id="31b1b-144">Chave</span><span class="sxs-lookup"><span data-stu-id="31b1b-144">Key</span></span>](../../../../visual-basic/language-reference/modifiers/key.md)
