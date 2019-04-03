---
title: 'Como: Inferir nomes de propriedade e tipos em declarações de tipo anônimo (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inferring property names [Visual Basic]
- anonymous types [Visual Basic], inferring property names and types
- inferring property types [Visual Basic]
ms.assetid: 7c748b22-913f-4d9d-b747-6b7bf296a0bc
ms.openlocfilehash: be3c74e8f8c69eb9f0a1d0dda4d6c90dfd7e567a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824706"
---
# <a name="how-to-infer-property-names-and-types-in-anonymous-type-declarations-visual-basic"></a><span data-ttu-id="a1f6e-102">Como: Inferir nomes de propriedade e tipos em declarações de tipo anônimo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a1f6e-102">How to: Infer Property Names and Types in Anonymous Type Declarations (Visual Basic)</span></span>
<span data-ttu-id="a1f6e-103">Tipos anônimos não fornecem um mecanismo para especificar diretamente os tipos de dados de propriedades.</span><span class="sxs-lookup"><span data-stu-id="a1f6e-103">Anonymous types provide no mechanism for directly specifying the data types of properties.</span></span> <span data-ttu-id="a1f6e-104">Tipos de todas as propriedades são inferidos.</span><span class="sxs-lookup"><span data-stu-id="a1f6e-104">Types of all properties are inferred.</span></span> <span data-ttu-id="a1f6e-105">No exemplo a seguir, os tipos de `Name` e `Price` são inferidos diretamente dos valores que são usados para inicializá-los.</span><span class="sxs-lookup"><span data-stu-id="a1f6e-105">In the following example, the types of `Name` and `Price` are inferred directly from the values that are used to initialize them.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#1)]  
  
 <span data-ttu-id="a1f6e-106">Tipos anônimos também podem interpretar os nomes de propriedade e tipos de outras fontes.</span><span class="sxs-lookup"><span data-stu-id="a1f6e-106">Anonymous types can also infer property names and types from other sources.</span></span> <span data-ttu-id="a1f6e-107">As seções a seguir fornecem uma lista de circunstâncias em que a inferência de tipos é possível e exemplos de situações em que não é.</span><span class="sxs-lookup"><span data-stu-id="a1f6e-107">The sections that follow provide a list of the circumstances where inference is possible, and examples of situations where it is not.</span></span>  
  
## <a name="successful-inference"></a><span data-ttu-id="a1f6e-108">Inferência bem-sucedida</span><span class="sxs-lookup"><span data-stu-id="a1f6e-108">Successful Inference</span></span>  
  
#### <a name="anonymous-types-can-infer-property-names-and-types-from-the-following-sources"></a><span data-ttu-id="a1f6e-109">Tipos anônimos podem inferir nomes de propriedade e tipos das seguintes fontes:</span><span class="sxs-lookup"><span data-stu-id="a1f6e-109">Anonymous types can infer property names and types from the following sources:</span></span>  
  
-   <span data-ttu-id="a1f6e-110">De nomes de variáveis.</span><span class="sxs-lookup"><span data-stu-id="a1f6e-110">From variable names.</span></span> <span data-ttu-id="a1f6e-111">Tipo anônimo `anonProduct` terá duas propriedades, `productName` e `productPrice`.</span><span class="sxs-lookup"><span data-stu-id="a1f6e-111">Anonymous type `anonProduct` will have two properties, `productName` and `productPrice`.</span></span> <span data-ttu-id="a1f6e-112">Os tipos de dados será das variáveis do originais `String` e `Double`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="a1f6e-112">Their data types will be those of the original variables, `String` and `Double`, respectively.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#11)]  
  
-   <span data-ttu-id="a1f6e-113">De nomes de campo ou propriedade de outros objetos.</span><span class="sxs-lookup"><span data-stu-id="a1f6e-113">From property or field names of other objects.</span></span> <span data-ttu-id="a1f6e-114">Por exemplo, considere uma `car` objeto de um `CarClass` tipo que inclui `Name` e `ID` propriedades.</span><span class="sxs-lookup"><span data-stu-id="a1f6e-114">For example, consider a `car` object of a `CarClass` type that includes `Name` and `ID` properties.</span></span> <span data-ttu-id="a1f6e-115">Para criar uma nova instância de tipo anônimo, `car1`, com `Name` e `ID` propriedades que são inicializadas com os valores do `car` do objeto, você pode escrever o seguinte:</span><span class="sxs-lookup"><span data-stu-id="a1f6e-115">To create a new anonymous type instance, `car1`, with `Name` and `ID` properties that are initialized with the values from the `car` object, you can write the following:</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#34)]  
  
     <span data-ttu-id="a1f6e-116">A declaração anterior é equivalente a mais a linha de código que define o tipo anônimo `car2`.</span><span class="sxs-lookup"><span data-stu-id="a1f6e-116">The previous declaration is equivalent to the longer line of code that defines anonymous type `car2`.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#35)]  
  
-   <span data-ttu-id="a1f6e-117">De nomes de membro XML.</span><span class="sxs-lookup"><span data-stu-id="a1f6e-117">From XML member names.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#12)]  
  
     <span data-ttu-id="a1f6e-118">O tipo resultante para `anon` teria uma propriedade, `Book`, do tipo <xref:System.Collections.IEnumerable>(de XElement).</span><span class="sxs-lookup"><span data-stu-id="a1f6e-118">The resulting type for `anon` would have one property, `Book`, of type <xref:System.Collections.IEnumerable>(Of XElement).</span></span>  
  
-   <span data-ttu-id="a1f6e-119">De uma função que não tem parâmetros, como `SomeFunction` no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="a1f6e-119">From a function that has no parameters, such as `SomeFunction` in the following example.</span></span>  
  
     `Dim sc As New SomeClass`  
  
     `Dim anon1 = New With {Key sc.SomeFunction()}`  
  
     <span data-ttu-id="a1f6e-120">A variável `anon2` no código a seguir é um tipo anônimo que tem uma propriedade, um caractere chamado `First`.</span><span class="sxs-lookup"><span data-stu-id="a1f6e-120">The variable `anon2` in the following code is an anonymous type that has one property, a character named `First`.</span></span> <span data-ttu-id="a1f6e-121">Esse código exibirá uma letra "E", a letra que é retornada pela função <xref:System.Linq.Enumerable.First%2A>.</span><span class="sxs-lookup"><span data-stu-id="a1f6e-121">This code will display a letter "E," the letter that is returned by function <xref:System.Linq.Enumerable.First%2A>.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#13)]  
  
## <a name="inference-failures"></a><span data-ttu-id="a1f6e-122">A inferência de falhas</span><span class="sxs-lookup"><span data-stu-id="a1f6e-122">Inference Failures</span></span>  
  
#### <a name="name-inference-will-fail-in-many-circumstances-including-the-following"></a><span data-ttu-id="a1f6e-123">A inferência de nome falhará em muitas circunstâncias, incluindo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="a1f6e-123">Name inference will fail in many circumstances, including the following:</span></span>  
  
-   <span data-ttu-id="a1f6e-124">A inferência deriva de invocação de um método, um construtor ou uma propriedade com parâmetros que requer argumentos.</span><span class="sxs-lookup"><span data-stu-id="a1f6e-124">The inference derives from the invocation of a method, a constructor, or a parameterized property that requires arguments.</span></span> <span data-ttu-id="a1f6e-125">A declaração anterior de `anon1` falhará se `someFunction` tem um ou mais argumentos.</span><span class="sxs-lookup"><span data-stu-id="a1f6e-125">The previous declaration of `anon1` fails if `someFunction` has one or more arguments.</span></span>  
  
     `' Not valid.`  
  
     `' Dim anon3 = New With {Key sc.someFunction(someArg)}`  
  
     <span data-ttu-id="a1f6e-126">Atribuição para um novo nome de propriedade resolve o problema.</span><span class="sxs-lookup"><span data-stu-id="a1f6e-126">Assignment to a new property name solves the problem.</span></span>  
  
     `' Valid.`  
  
     `Dim anon4 = New With {Key .FunResult = sc.someFunction(someArg)}`  
  
-   <span data-ttu-id="a1f6e-127">A inferência deriva de uma expressão complexa.</span><span class="sxs-lookup"><span data-stu-id="a1f6e-127">The inference derives from a complex expression.</span></span>  
  
    ```  
    Dim aString As String = "Act "  
    ' Not valid.  
    ' Dim label = New With {Key aString & "IV"}  
    ```  
  
     <span data-ttu-id="a1f6e-128">O erro pode ser resolvido ao atribuir o resultado da expressão a um nome de propriedade.</span><span class="sxs-lookup"><span data-stu-id="a1f6e-128">The error can be resolved by assigning the result of the expression to a property name.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#14)]  
  
-   <span data-ttu-id="a1f6e-129">Inferência de várias propriedades produz dois ou mais propriedades que têm o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="a1f6e-129">Inference for multiple properties produces two or more properties that have the same name.</span></span> <span data-ttu-id="a1f6e-130">Referência de volta às declarações nos exemplos anteriores, você não pode listar os dois `product.Name` e `car1.Name` como propriedades do mesmo tipo anônimo.</span><span class="sxs-lookup"><span data-stu-id="a1f6e-130">Referring back to declarations in earlier examples, you cannot list both `product.Name` and `car1.Name` as properties of the same anonymous type.</span></span> <span data-ttu-id="a1f6e-131">Isso ocorre porque o identificador inferido para cada um deles seria `Name`.</span><span class="sxs-lookup"><span data-stu-id="a1f6e-131">This is because the inferred identifier for each of these would be `Name`.</span></span>  
  
     `' Not valid.`  
  
     `' Dim anon5 = New With {Key product.Name, Key car1.Name}`  
  
     <span data-ttu-id="a1f6e-132">O problema pode ser resolvido por meio da atribuição de valores para nomes de propriedade distintos.</span><span class="sxs-lookup"><span data-stu-id="a1f6e-132">The problem can be solved by assigning the values to distinct property names.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#36)]  
  
     <span data-ttu-id="a1f6e-133">Observe que alterações caso (alterações entre letras maiusculas e minúsculas) não faça dois nomes distintos.</span><span class="sxs-lookup"><span data-stu-id="a1f6e-133">Note that changes in case (changes between uppercase and lowercase letters) do not make two names distinct.</span></span>  
  
     `Dim price = 0`  
  
     `' Not valid, because Price and price are the same name.`  
  
     `' Dim anon7 = New With {Key product.Price, Key price}`  
  
-   <span data-ttu-id="a1f6e-134">O tipo inicial e o valor de uma propriedade depende de outra propriedade que ainda não foi estabelecida.</span><span class="sxs-lookup"><span data-stu-id="a1f6e-134">The initial type and value of one property depends on another property that is not yet established.</span></span> <span data-ttu-id="a1f6e-135">Por exemplo, `.IDName = .LastName` não é válido em uma declaração de tipo anônimo, a menos que `.LastName` já foi inicializado.</span><span class="sxs-lookup"><span data-stu-id="a1f6e-135">For example, `.IDName = .LastName` is not valid in an anonymous type declaration unless `.LastName` is already initialized.</span></span>  
  
     `' Not valid.`  
  
     `' Dim anon8 = New With {Key .IDName = .LastName, Key .LastName = "Jones"}`  
  
     <span data-ttu-id="a1f6e-136">Neste exemplo, você pode corrigir o problema, invertendo a ordem na qual as propriedades são declaradas.</span><span class="sxs-lookup"><span data-stu-id="a1f6e-136">In this example, you can fix the problem by reversing the order in which the properties are declared.</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#15)]  
  
-   <span data-ttu-id="a1f6e-137">Um nome de propriedade do tipo anônimo é igual ao nome de um membro de <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="a1f6e-137">A property name of the anonymous type is the same as the name of a member of <xref:System.Object>.</span></span> <span data-ttu-id="a1f6e-138">Por exemplo, a seguinte declaração falhará porque `Equals` é um método de <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="a1f6e-138">For example, the following declaration fails because `Equals` is a method of <xref:System.Object>.</span></span>  
  
     `' Not valid.`  
  
     `' Dim relationsLabels1 = New With {Key .Equals = "equals", Key .Greater = _`  
  
     `'                       "greater than", Key .Less = "less than"}`  
  
     <span data-ttu-id="a1f6e-139">Você pode corrigir o problema, alterando o nome da propriedade:</span><span class="sxs-lookup"><span data-stu-id="a1f6e-139">You can fix the problem by changing the property name:</span></span>  
  
     [!code-vb[VbVbalrAnonymousTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#16)]  
  
## <a name="see-also"></a><span data-ttu-id="a1f6e-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a1f6e-140">See also</span></span>

- [<span data-ttu-id="a1f6e-141">Inicializadores de objeto: Tipos nomeados e anônimos</span><span class="sxs-lookup"><span data-stu-id="a1f6e-141">Object Initializers: Named and Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="a1f6e-142">Inferência de Tipo de Variável Local</span><span class="sxs-lookup"><span data-stu-id="a1f6e-142">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="a1f6e-143">Tipos Anônimos</span><span class="sxs-lookup"><span data-stu-id="a1f6e-143">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="a1f6e-144">Chave</span><span class="sxs-lookup"><span data-stu-id="a1f6e-144">Key</span></span>](../../../../visual-basic/language-reference/modifiers/key.md)
