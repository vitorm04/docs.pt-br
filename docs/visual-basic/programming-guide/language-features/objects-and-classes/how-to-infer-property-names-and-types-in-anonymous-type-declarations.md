---
title: "Como: inferir nomes de propriedade e tipos na declaração de tipo anônimo (Visual Basic) | Documentos do Microsoft"
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
- inferring property names [Visual Basic]
- anonymous types [Visual Basic], inferring property names and types
- inferring property types [Visual Basic]
ms.assetid: 7c748b22-913f-4d9d-b747-6b7bf296a0bc
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 795a87b87de8b636d9d103f5916452c88c3e2fd5
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-infer-property-names-and-types-in-anonymous-type-declarations-visual-basic"></a><span data-ttu-id="c2526-102">Como inferir nomes e tipos de propriedade em declarações de tipo anônimo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2526-102">How to: Infer Property Names and Types in Anonymous Type Declarations (Visual Basic)</span></span>
<span data-ttu-id="c2526-103">Tipos anônimos fornecem nenhum mecanismo para especificar os tipos de dados de propriedades diretamente.</span><span class="sxs-lookup"><span data-stu-id="c2526-103">Anonymous types provide no mechanism for directly specifying the data types of properties.</span></span> <span data-ttu-id="c2526-104">Tipos de todas as propriedades são inferidos.</span><span class="sxs-lookup"><span data-stu-id="c2526-104">Types of all properties are inferred.</span></span> <span data-ttu-id="c2526-105">No exemplo a seguir, os tipos de `Name` e `Price` são inferidos diretamente dos valores que são usados para inicializá-los.</span><span class="sxs-lookup"><span data-stu-id="c2526-105">In the following example, the types of `Name` and `Price` are inferred directly from the values that are used to initialize them.</span></span>  
  
 <span data-ttu-id="c2526-106">[!code-vb[VbVbalrAnonymousTypes n º&1;](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="c2526-106">[!code-vb[VbVbalrAnonymousTypes#1](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_1.vb)]</span></span>  
  
 <span data-ttu-id="c2526-107">Tipos anônimos também podem interpretar nomes de propriedade e tipos de outras fontes.</span><span class="sxs-lookup"><span data-stu-id="c2526-107">Anonymous types can also infer property names and types from other sources.</span></span> <span data-ttu-id="c2526-108">As seções a seguir fornecem uma lista de circunstâncias onde a inferência é possível e exemplos de situações onde não é.</span><span class="sxs-lookup"><span data-stu-id="c2526-108">The sections that follow provide a list of the circumstances where inference is possible, and examples of situations where it is not.</span></span>  
  
## <a name="successful-inference"></a><span data-ttu-id="c2526-109">Inferência bem-sucedida</span><span class="sxs-lookup"><span data-stu-id="c2526-109">Successful Inference</span></span>  
  
#### <a name="anonymous-types-can-infer-property-names-and-types-from-the-following-sources"></a><span data-ttu-id="c2526-110">Tipos anônimos podem inferir nomes de propriedade e tipos das seguintes fontes:</span><span class="sxs-lookup"><span data-stu-id="c2526-110">Anonymous types can infer property names and types from the following sources:</span></span>  
  
-   <span data-ttu-id="c2526-111">Dos nomes de variável.</span><span class="sxs-lookup"><span data-stu-id="c2526-111">From variable names.</span></span> <span data-ttu-id="c2526-112">Tipo anônimo `anonProduct` terá duas propriedades, `productName` e `productPrice`.</span><span class="sxs-lookup"><span data-stu-id="c2526-112">Anonymous type `anonProduct` will have two properties, `productName` and `productPrice`.</span></span> <span data-ttu-id="c2526-113">Os tipos de dados será das variáveis originais, `String` e `Double`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="c2526-113">Their data types will be those of the original variables, `String` and `Double`, respectively.</span></span>  
  
     <span data-ttu-id="c2526-114">[!code-vb[VbVbalrAnonymousTypes n º&11;](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="c2526-114">[!code-vb[VbVbalrAnonymousTypes#11](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_2.vb)]</span></span>  
  
-   <span data-ttu-id="c2526-115">De propriedade ou campo nomes de outros objetos.</span><span class="sxs-lookup"><span data-stu-id="c2526-115">From property or field names of other objects.</span></span> <span data-ttu-id="c2526-116">Por exemplo, considere uma `car` o objeto de um `CarClass` tipo que inclui `Name` e `ID` propriedades.</span><span class="sxs-lookup"><span data-stu-id="c2526-116">For example, consider a `car` object of a `CarClass` type that includes `Name` and `ID` properties.</span></span> <span data-ttu-id="c2526-117">Para criar uma nova instância de tipo anônimo, `car1`, com `Name` e `ID` propriedades que são inicializadas com os valores da `car` do objeto, você pode escrever o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c2526-117">To create a new anonymous type instance, `car1`, with `Name` and `ID` properties that are initialized with the values from the `car` object, you can write the following:</span></span>  
  
     <span data-ttu-id="c2526-118">[!code-vb[VbVbalrAnonymousTypes&#34;](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="c2526-118">[!code-vb[VbVbalrAnonymousTypes#34](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_3.vb)]</span></span>  
  
     <span data-ttu-id="c2526-119">A declaração anterior é equivalente a mais a linha de código que define o tipo anônimo `car2`.</span><span class="sxs-lookup"><span data-stu-id="c2526-119">The previous declaration is equivalent to the longer line of code that defines anonymous type `car2`.</span></span>  
  
     <span data-ttu-id="c2526-120">[!code-vb[VbVbalrAnonymousTypes&#35;](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="c2526-120">[!code-vb[VbVbalrAnonymousTypes#35](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_4.vb)]</span></span>  
  
-   <span data-ttu-id="c2526-121">De XML membro nomes.</span><span class="sxs-lookup"><span data-stu-id="c2526-121">From XML member names.</span></span>  
  
     <span data-ttu-id="c2526-122">[!code-vb[VbVbalrAnonymousTypes&#12;](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="c2526-122">[!code-vb[VbVbalrAnonymousTypes#12](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_5.vb)]</span></span>  
  
     <span data-ttu-id="c2526-123">O tipo resultante para `anon` teria uma propriedade, `Book`, do tipo <xref:System.Collections.IEnumerable>(de XElement).</xref:System.Collections.IEnumerable></span><span class="sxs-lookup"><span data-stu-id="c2526-123">The resulting type for `anon` would have one property, `Book`, of type <xref:System.Collections.IEnumerable>(Of XElement).</span></span>  
  
-   <span data-ttu-id="c2526-124">De uma função que não tem parâmetros, como `SomeFunction` no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="c2526-124">From a function that has no parameters, such as `SomeFunction` in the following example.</span></span>  
  
     `Dim sc As New SomeClass`  
  
     `Dim anon1 = New With {Key sc.SomeFunction()}`  
  
     <span data-ttu-id="c2526-125">A variável `anon2` no código a seguir é um tipo anônimo que tem uma propriedade, um caractere chamado `First`.</span><span class="sxs-lookup"><span data-stu-id="c2526-125">The variable `anon2` in the following code is an anonymous type that has one property, a character named `First`.</span></span> <span data-ttu-id="c2526-126">Esse código irá exibir uma letra "E", a letra que é retornada pela função <xref:System.Linq.Enumerable.First%2A>.</xref:System.Linq.Enumerable.First%2A></span><span class="sxs-lookup"><span data-stu-id="c2526-126">This code will display a letter "E," the letter that is returned by function <xref:System.Linq.Enumerable.First%2A>.</span></span>  
  
     <span data-ttu-id="c2526-127">[!code-vb[VbVbalrAnonymousTypes&13;](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="c2526-127">[!code-vb[VbVbalrAnonymousTypes#13](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_6.vb)]</span></span>  
  
## <a name="inference-failures"></a><span data-ttu-id="c2526-128">A inferência de falhas</span><span class="sxs-lookup"><span data-stu-id="c2526-128">Inference Failures</span></span>  
  
#### <a name="name-inference-will-fail-in-many-circumstances-including-the-following"></a><span data-ttu-id="c2526-129">Nome inferência falhará em muitas circunstâncias, incluindo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c2526-129">Name inference will fail in many circumstances, including the following:</span></span>  
  
-   <span data-ttu-id="c2526-130">A inferência deriva de invocação de um método, um construtor ou uma propriedade parametrizada que requer argumentos.</span><span class="sxs-lookup"><span data-stu-id="c2526-130">The inference derives from the invocation of a method, a constructor, or a parameterized property that requires arguments.</span></span> <span data-ttu-id="c2526-131">A declaração anterior de `anon1` falhará se `someFunction` possui um ou mais argumentos.</span><span class="sxs-lookup"><span data-stu-id="c2526-131">The previous declaration of `anon1` fails if `someFunction` has one or more arguments.</span></span>  
  
     `' Not valid.`  
  
     `' Dim anon3 = New With {Key sc.someFunction(someArg)}`  
  
     <span data-ttu-id="c2526-132">Atribuição a um novo nome de propriedade resolve o problema.</span><span class="sxs-lookup"><span data-stu-id="c2526-132">Assignment to a new property name solves the problem.</span></span>  
  
     `' Valid.`  
  
     `Dim anon4 = New With {Key .FunResult = sc.someFunction(someArg)}`  
  
-   <span data-ttu-id="c2526-133">A inferência deriva de uma expressão complexa.</span><span class="sxs-lookup"><span data-stu-id="c2526-133">The inference derives from a complex expression.</span></span>  
  
    ```  
    Dim aString As String = "Act "  
    ' Not valid.  
    ' Dim label = New With {Key aString & "IV"}  
    ```  
  
     <span data-ttu-id="c2526-134">O erro pode ser resolvido atribuindo o resultado da expressão a um nome de propriedade.</span><span class="sxs-lookup"><span data-stu-id="c2526-134">The error can be resolved by assigning the result of the expression to a property name.</span></span>  
  
     <span data-ttu-id="c2526-135">[!code-vb[VbVbalrAnonymousTypes&#14;](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="c2526-135">[!code-vb[VbVbalrAnonymousTypes#14](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_7.vb)]</span></span>  
  
-   <span data-ttu-id="c2526-136">Inferência de várias propriedades produz dois ou mais propriedades que têm o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="c2526-136">Inference for multiple properties produces two or more properties that have the same name.</span></span> <span data-ttu-id="c2526-137">Referência de volta a declarações nos exemplos anteriores, você não pode listar os dois `product.Name` e `car1.Name` como propriedades do mesmo tipo anônimo.</span><span class="sxs-lookup"><span data-stu-id="c2526-137">Referring back to declarations in earlier examples, you cannot list both `product.Name` and `car1.Name` as properties of the same anonymous type.</span></span> <span data-ttu-id="c2526-138">Isso ocorre porque o identificador inferido para cada um deles seria `Name`.</span><span class="sxs-lookup"><span data-stu-id="c2526-138">This is because the inferred identifier for each of these would be `Name`.</span></span>  
  
     `' Not valid.`  
  
     `' Dim anon5 = New With {Key product.Name, Key car1.Name}`  
  
     <span data-ttu-id="c2526-139">O problema pode ser resolvido atribuindo valores a nomes de propriedades distintas.</span><span class="sxs-lookup"><span data-stu-id="c2526-139">The problem can be solved by assigning the values to distinct property names.</span></span>  
  
     <span data-ttu-id="c2526-140">[!code-vb[VbVbalrAnonymousTypes&#36;](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="c2526-140">[!code-vb[VbVbalrAnonymousTypes#36](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_8.vb)]</span></span>  
  
     <span data-ttu-id="c2526-141">Observe que as alterações caso (alterações entre letras maiusculas e minúsculas) não faça dois nomes distintos.</span><span class="sxs-lookup"><span data-stu-id="c2526-141">Note that changes in case (changes between uppercase and lowercase letters) do not make two names distinct.</span></span>  
  
     `Dim price = 0`  
  
     `' Not valid, because Price and price are the same name.`  
  
     `' Dim anon7 = New With {Key product.Price, Key price}`  
  
-   <span data-ttu-id="c2526-142">O tipo inicial e o valor de uma propriedade depende outra propriedade que ainda não foi estabelecida.</span><span class="sxs-lookup"><span data-stu-id="c2526-142">The initial type and value of one property depends on another property that is not yet established.</span></span> <span data-ttu-id="c2526-143">Por exemplo, `.IDName = .LastName` não é válido em uma declaração de tipo anônimo, a menos que `.LastName` já foi inicializado.</span><span class="sxs-lookup"><span data-stu-id="c2526-143">For example, `.IDName = .LastName` is not valid in an anonymous type declaration unless `.LastName` is already initialized.</span></span>  
  
     `' Not valid.`  
  
     `' Dim anon8 = New With {Key .IDName = .LastName, Key .LastName = "Jones"}`  
  
     <span data-ttu-id="c2526-144">Neste exemplo, você pode corrigir o problema, invertendo a ordem na qual as propriedades são declaradas.</span><span class="sxs-lookup"><span data-stu-id="c2526-144">In this example, you can fix the problem by reversing the order in which the properties are declared.</span></span>  
  
     <span data-ttu-id="c2526-145">[!code-vb[VbVbalrAnonymousTypes&#15;](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="c2526-145">[!code-vb[VbVbalrAnonymousTypes#15](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_9.vb)]</span></span>  
  
-   <span data-ttu-id="c2526-146">Um nome de propriedade do tipo anônimo é o mesmo que o nome de um membro do <xref:System.Object>.</xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="c2526-146">A property name of the anonymous type is the same as the name of a member of <xref:System.Object>.</span></span> <span data-ttu-id="c2526-147">Por exemplo, a seguinte declaração falha porque `Equals` é um método de <xref:System.Object>.</xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="c2526-147">For example, the following declaration fails because `Equals` is a method of <xref:System.Object>.</span></span>  
  
     `' Not valid.`  
  
     `' Dim relationsLabels1 = New With {Key .Equals = "equals", Key .Greater = _`  
  
     `'                       "greater than", Key .Less = "less than"}`  
  
     <span data-ttu-id="c2526-148">Você pode corrigir o problema alterando o nome da propriedade:</span><span class="sxs-lookup"><span data-stu-id="c2526-148">You can fix the problem by changing the property name:</span></span>  
  
     <span data-ttu-id="c2526-149">[!code-vb[VbVbalrAnonymousTypes n º&16;](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_10.vb)]</span><span class="sxs-lookup"><span data-stu-id="c2526-149">[!code-vb[VbVbalrAnonymousTypes#16](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/how-to-infer-property-names-and-types-in-anonymous-type-declarations_10.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2526-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c2526-150">See Also</span></span>  
 <span data-ttu-id="c2526-151">[Inicializadores de objeto: Tipos nomeados e anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="c2526-151">[Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) </span></span>  
<span data-ttu-id="c2526-152"> [Inferência de tipo local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span><span class="sxs-lookup"><span data-stu-id="c2526-152"> [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span></span>  
<span data-ttu-id="c2526-153"> [Tipos anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="c2526-153"> [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) </span></span>  
<span data-ttu-id="c2526-154"> [Chave](../../../../visual-basic/language-reference/modifiers/key.md)</span><span class="sxs-lookup"><span data-stu-id="c2526-154"> [Key](../../../../visual-basic/language-reference/modifiers/key.md)</span></span>
