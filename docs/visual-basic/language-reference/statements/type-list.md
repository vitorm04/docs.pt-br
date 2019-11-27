---
title: Lista de tipos
ms.date: 07/20/2015
f1_keywords:
- StructureConstraint
- vb.StructureConstraint
- ClassConstraint
- vb.ClassConstraint
helpviewer_keywords:
- class constraint
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- generics [Visual Basic], type list
- structure constraint
- constraints, in type parameters
- generics [Visual Basic], generic types
- parameters [Visual Basic], type
- constraints, Structure keyword
- type parameters [Visual Basic], constraints
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generics [Visual Basic], type parameters
- type parameters
- constraints, Class keyword
ms.assetid: 56db947a-2ae8-40f2-a70a-960764e9d0db
ms.openlocfilehash: 3f2aaa65293ed2bcc6c8eeb4bd77e49907d93425
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352770"
---
# <a name="type-list-visual-basic"></a><span data-ttu-id="4a322-102">Lista de tipos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4a322-102">Type List (Visual Basic)</span></span>

<span data-ttu-id="4a322-103">Especifica os *parâmetros de tipo* para um elemento de programação *genérico* .</span><span class="sxs-lookup"><span data-stu-id="4a322-103">Specifies the *type parameters* for a *generic* programming element.</span></span> <span data-ttu-id="4a322-104">Vários parâmetros são separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="4a322-104">Multiple parameters are separated by commas.</span></span> <span data-ttu-id="4a322-105">A seguir está a sintaxe para um parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="4a322-105">Following is the syntax for one type parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="4a322-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4a322-106">Syntax</span></span>

```vb
[genericmodifier] typename [ As constraintlist ]
```

## <a name="parts"></a><span data-ttu-id="4a322-107">Partes</span><span class="sxs-lookup"><span data-stu-id="4a322-107">Parts</span></span>

|<span data-ttu-id="4a322-108">Termo</span><span class="sxs-lookup"><span data-stu-id="4a322-108">Term</span></span>|<span data-ttu-id="4a322-109">Definição</span><span class="sxs-lookup"><span data-stu-id="4a322-109">Definition</span></span>|
|---|---|
|`genericmodifier`|<span data-ttu-id="4a322-110">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4a322-110">Optional.</span></span> <span data-ttu-id="4a322-111">Pode ser usado somente em interfaces e delegados genéricos.</span><span class="sxs-lookup"><span data-stu-id="4a322-111">Can be used only in generic interfaces and delegates.</span></span> <span data-ttu-id="4a322-112">Você pode declarar um tipo covariant usando a palavra-chave [out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md) ou contravariant usando a palavra-chave [in](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) .</span><span class="sxs-lookup"><span data-stu-id="4a322-112">You can declare a type covariant by using the [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md) keyword or contravariant by using the [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) keyword.</span></span> <span data-ttu-id="4a322-113">Consulte [Covariância e contravariância](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="4a322-113">See [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>|
|`typename`|<span data-ttu-id="4a322-114">Necessária.</span><span class="sxs-lookup"><span data-stu-id="4a322-114">Required.</span></span> <span data-ttu-id="4a322-115">Nome do parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="4a322-115">Name of the type parameter.</span></span> <span data-ttu-id="4a322-116">Este é um espaço reservado, a ser substituído por um tipo definido fornecido pelo argumento de tipo correspondente.</span><span class="sxs-lookup"><span data-stu-id="4a322-116">This is a placeholder, to be replaced by a defined type supplied by the corresponding type argument.</span></span>|
|`constraintlist`|<span data-ttu-id="4a322-117">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4a322-117">Optional.</span></span> <span data-ttu-id="4a322-118">Lista de requisitos que restringem o tipo de dados que pode ser fornecido para `typename`.</span><span class="sxs-lookup"><span data-stu-id="4a322-118">List of requirements that constrain the data type that can be supplied for `typename`.</span></span> <span data-ttu-id="4a322-119">Se você tiver várias restrições, coloque-as entre chaves (`{ }`) e separe-as com vírgulas.</span><span class="sxs-lookup"><span data-stu-id="4a322-119">If you have multiple constraints, enclose them in curly braces (`{ }`) and separate them with commas.</span></span> <span data-ttu-id="4a322-120">Você deve introduzir a lista de restrições com [a palavra-](../../../visual-basic/language-reference/statements/as-clause.md) chave as.</span><span class="sxs-lookup"><span data-stu-id="4a322-120">You must introduce the constraint list with the [As](../../../visual-basic/language-reference/statements/as-clause.md) keyword.</span></span> <span data-ttu-id="4a322-121">Você usa `As` apenas uma vez, no início da lista.</span><span class="sxs-lookup"><span data-stu-id="4a322-121">You use `As` only once, at the beginning of the list.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4a322-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="4a322-122">Remarks</span></span>

<span data-ttu-id="4a322-123">Cada elemento de programação genérico deve ter pelo menos um parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="4a322-123">Every generic programming element must take at least one type parameter.</span></span> <span data-ttu-id="4a322-124">Um parâmetro de tipo é um espaço reservado para um tipo específico (um *elemento construído*) que o código do cliente especifica quando ele cria uma instância do tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="4a322-124">A type parameter is a placeholder for a specific type (a *constructed element*) that client code specifies when it creates an instance of the generic type.</span></span> <span data-ttu-id="4a322-125">Você pode definir uma classe genérica, estrutura, interface, procedimento ou delegado.</span><span class="sxs-lookup"><span data-stu-id="4a322-125">You can define a generic class, structure, interface, procedure, or delegate.</span></span>

<span data-ttu-id="4a322-126">Para obter mais informações sobre quando definir um tipo genérico, consulte [tipos genéricos em Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="4a322-126">For more information on when to define a generic type, see [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span> <span data-ttu-id="4a322-127">Para obter mais informações sobre nomes de parâmetro de tipo, consulte [nomes de elemento declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="4a322-127">For more information on type parameter names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

## <a name="rules"></a><span data-ttu-id="4a322-128">Regras</span><span class="sxs-lookup"><span data-stu-id="4a322-128">Rules</span></span>

- <span data-ttu-id="4a322-129">**Parênteses.**</span><span class="sxs-lookup"><span data-stu-id="4a322-129">**Parentheses.**</span></span> <span data-ttu-id="4a322-130">Se você fornecer uma lista de parâmetros de tipo, deverá colocá-la entre parênteses e deverá introduzir a lista com a palavra-chave [de](../../../visual-basic/language-reference/statements/of-clause.md) .</span><span class="sxs-lookup"><span data-stu-id="4a322-130">If you supply a type parameter list, you must enclose it in parentheses, and you must introduce the list with the [Of](../../../visual-basic/language-reference/statements/of-clause.md) keyword.</span></span> <span data-ttu-id="4a322-131">Você usa `Of` apenas uma vez, no início da lista.</span><span class="sxs-lookup"><span data-stu-id="4a322-131">You use `Of` only once, at the beginning of the list.</span></span>

- <span data-ttu-id="4a322-132">**Reflexiva.**</span><span class="sxs-lookup"><span data-stu-id="4a322-132">**Constraints.**</span></span> <span data-ttu-id="4a322-133">Uma lista de *restrições* em um parâmetro de tipo pode incluir os seguintes itens em qualquer combinação:</span><span class="sxs-lookup"><span data-stu-id="4a322-133">A list of *constraints* on a type parameter can include the following items in any combination:</span></span>

  - <span data-ttu-id="4a322-134">Qualquer número de interfaces.</span><span class="sxs-lookup"><span data-stu-id="4a322-134">Any number of interfaces.</span></span> <span data-ttu-id="4a322-135">O tipo fornecido deve implementar todas as interfaces nesta lista.</span><span class="sxs-lookup"><span data-stu-id="4a322-135">The supplied type must implement every interface in this list.</span></span>

  - <span data-ttu-id="4a322-136">No máximo uma classe.</span><span class="sxs-lookup"><span data-stu-id="4a322-136">At most one class.</span></span> <span data-ttu-id="4a322-137">O tipo fornecido deve herdar dessa classe.</span><span class="sxs-lookup"><span data-stu-id="4a322-137">The supplied type must inherit from that class.</span></span>

  - <span data-ttu-id="4a322-138">A palavra-chave `New`.</span><span class="sxs-lookup"><span data-stu-id="4a322-138">The `New` keyword.</span></span> <span data-ttu-id="4a322-139">O tipo fornecido deve expor um construtor sem parâmetros que o seu tipo genérico possa acessar.</span><span class="sxs-lookup"><span data-stu-id="4a322-139">The supplied type must expose a parameterless constructor that your generic type can access.</span></span> <span data-ttu-id="4a322-140">Isso será útil se você restringir um parâmetro de tipo por uma ou mais interfaces.</span><span class="sxs-lookup"><span data-stu-id="4a322-140">This is useful if you constrain a type parameter by one or more interfaces.</span></span> <span data-ttu-id="4a322-141">Um tipo que implementa interfaces não expõe necessariamente um construtor e, dependendo do nível de acesso de um construtor, o código dentro do tipo genérico pode não ser capaz de acessá-lo.</span><span class="sxs-lookup"><span data-stu-id="4a322-141">A type that implements interfaces does not necessarily expose a constructor, and depending on the access level of a constructor, the code within the generic type might not be able to access it.</span></span>

  - <span data-ttu-id="4a322-142">A palavra-chave `Class` ou a palavra-chave `Structure`.</span><span class="sxs-lookup"><span data-stu-id="4a322-142">Either the `Class` keyword or the `Structure` keyword.</span></span> <span data-ttu-id="4a322-143">A palavra-chave `Class` restringe um parâmetro de tipo genérico para exigir que qualquer argumento de tipo passado para ele seja um tipo de referência, por exemplo, uma cadeia de caracteres, matriz ou delegado, ou um objeto criado a partir de uma classe.</span><span class="sxs-lookup"><span data-stu-id="4a322-143">The `Class` keyword constrains a generic type parameter to require that any type argument passed to it be a reference type, for example a string, array, or delegate, or an object created from a class.</span></span> <span data-ttu-id="4a322-144">A palavra-chave `Structure` restringe um parâmetro de tipo genérico para exigir que qualquer argumento de tipo passado para ele seja um tipo de valor, por exemplo, um tipo de dados de estrutura, enumeração ou elementar.</span><span class="sxs-lookup"><span data-stu-id="4a322-144">The `Structure` keyword constrains a generic type parameter to require that any type argument passed to it be a value type, for example a structure, enumeration, or elementary data type.</span></span> <span data-ttu-id="4a322-145">Você não pode incluir `Class` e `Structure` na mesma `constraintlist`.</span><span class="sxs-lookup"><span data-stu-id="4a322-145">You cannot include both `Class` and `Structure` in the same `constraintlist`.</span></span>

  <span data-ttu-id="4a322-146">O tipo fornecido deve atender a todos os requisitos que você incluir no `constraintlist`.</span><span class="sxs-lookup"><span data-stu-id="4a322-146">The supplied type must satisfy every requirement you include in `constraintlist`.</span></span>

  <span data-ttu-id="4a322-147">Restrições em cada parâmetro de tipo são independentes de restrições em outros parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="4a322-147">Constraints on each type parameter are independent of constraints on other type parameters.</span></span>

## <a name="behavior"></a><span data-ttu-id="4a322-148">Comportamento</span><span class="sxs-lookup"><span data-stu-id="4a322-148">Behavior</span></span>

- <span data-ttu-id="4a322-149">**Substituição de tempo de compilação.**</span><span class="sxs-lookup"><span data-stu-id="4a322-149">**Compile-Time Substitution.**</span></span> <span data-ttu-id="4a322-150">Quando você cria um tipo construído a partir de um elemento de programação genérico, você fornece um tipo definido para cada parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="4a322-150">When you create a constructed type from a generic programming element, you supply a defined type for each type parameter.</span></span> <span data-ttu-id="4a322-151">O compilador Visual Basic substitui esse tipo fornecido para cada ocorrência de `typename` dentro do elemento genérico.</span><span class="sxs-lookup"><span data-stu-id="4a322-151">The Visual Basic compiler substitutes that supplied type for every occurrence of `typename` within the generic element.</span></span>

- <span data-ttu-id="4a322-152">**Ausência de restrições.**</span><span class="sxs-lookup"><span data-stu-id="4a322-152">**Absence of Constraints.**</span></span> <span data-ttu-id="4a322-153">Se você não especificar nenhuma restrição em um parâmetro de tipo, seu código será limitado às operações e aos membros com suporte do [tipo de dados Object](../../../visual-basic/language-reference/data-types/object-data-type.md) para esse parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="4a322-153">If you do not specify any constraints on a type parameter, your code is limited to the operations and members supported by the [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md) for that type parameter.</span></span>

## <a name="example"></a><span data-ttu-id="4a322-154">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4a322-154">Example</span></span>

<span data-ttu-id="4a322-155">O exemplo a seguir mostra uma definição de esqueleto de uma classe de dicionário genérica, incluindo uma função de esqueleto para adicionar uma nova entrada ao dicionário.</span><span class="sxs-lookup"><span data-stu-id="4a322-155">The following example shows a skeleton definition of a generic dictionary class, including a skeleton function to add a new entry to the dictionary.</span></span>

[!code-vb[VbVbalrStatements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#3)]

## <a name="example"></a><span data-ttu-id="4a322-156">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4a322-156">Example</span></span>

<span data-ttu-id="4a322-157">Como `dictionary` é genérico, o código que o usa pode criar uma variedade de objetos a partir dele, cada um com a mesma funcionalidade, mas agindo em um tipo de dados diferente.</span><span class="sxs-lookup"><span data-stu-id="4a322-157">Because `dictionary` is generic, the code that uses it can create a variety of objects from it, each having the same functionality but acting on a different data type.</span></span> <span data-ttu-id="4a322-158">O exemplo a seguir mostra uma linha de código que cria um objeto `dictionary` com entradas de `String` e `Integer` chaves.</span><span class="sxs-lookup"><span data-stu-id="4a322-158">The following example shows a line of code that creates a `dictionary` object with `String` entries and `Integer` keys.</span></span>

[!code-vb[VbVbalrStatements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#4)]

## <a name="example"></a><span data-ttu-id="4a322-159">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4a322-159">Example</span></span>

<span data-ttu-id="4a322-160">O exemplo a seguir mostra a definição esqueleto equivalente gerada pelo exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="4a322-160">The following example shows the equivalent skeleton definition generated by the preceding example.</span></span>

[!code-vb[VbVbalrStatements#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#5)]

## <a name="see-also"></a><span data-ttu-id="4a322-161">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4a322-161">See also</span></span>

- [<span data-ttu-id="4a322-162">Of</span><span class="sxs-lookup"><span data-stu-id="4a322-162">Of</span></span>](../../../visual-basic/language-reference/statements/of-clause.md)
- [<span data-ttu-id="4a322-163">Operador New</span><span class="sxs-lookup"><span data-stu-id="4a322-163">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)
- [<span data-ttu-id="4a322-164">Níveis de acesso no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4a322-164">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="4a322-165">Tipo de Dados Object</span><span class="sxs-lookup"><span data-stu-id="4a322-165">Object Data Type</span></span>](../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="4a322-166">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="4a322-166">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="4a322-167">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="4a322-167">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="4a322-168">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="4a322-168">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="4a322-169">Como usar uma classe genérica</span><span class="sxs-lookup"><span data-stu-id="4a322-169">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="4a322-170">Covariância e Contravariância</span><span class="sxs-lookup"><span data-stu-id="4a322-170">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="4a322-171">In</span><span class="sxs-lookup"><span data-stu-id="4a322-171">In</span></span>](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [<span data-ttu-id="4a322-172">Saída</span><span class="sxs-lookup"><span data-stu-id="4a322-172">Out</span></span>](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
