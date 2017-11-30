---
title: Lista de tipos (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 35e72414b236615dc230b654ccfeed290841fb31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="type-list-visual-basic"></a><span data-ttu-id="9c1f2-102">Lista de tipos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c1f2-102">Type List (Visual Basic)</span></span>
<span data-ttu-id="9c1f2-103">Especifica o *parâmetros de tipo* para um *genérico* elemento de programação.</span><span class="sxs-lookup"><span data-stu-id="9c1f2-103">Specifies the *type parameters* for a *generic* programming element.</span></span> <span data-ttu-id="9c1f2-104">Vários parâmetros são separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="9c1f2-104">Multiple parameters are separated by commas.</span></span> <span data-ttu-id="9c1f2-105">Esta é a sintaxe para um parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="9c1f2-105">Following is the syntax for one type parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c1f2-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9c1f2-106">Syntax</span></span>  
  
```  
[genericmodifier] typename [ As constraintlist ]  
```  
  
## <a name="parts"></a><span data-ttu-id="9c1f2-107">Partes</span><span class="sxs-lookup"><span data-stu-id="9c1f2-107">Parts</span></span>  
  
|<span data-ttu-id="9c1f2-108">Termo</span><span class="sxs-lookup"><span data-stu-id="9c1f2-108">Term</span></span>|<span data-ttu-id="9c1f2-109">Definição</span><span class="sxs-lookup"><span data-stu-id="9c1f2-109">Definition</span></span>|  
|---|---|  
|`genericmodifier`|<span data-ttu-id="9c1f2-110">Opcional.</span><span class="sxs-lookup"><span data-stu-id="9c1f2-110">Optional.</span></span> <span data-ttu-id="9c1f2-111">Pode ser usado somente em interfaces genéricas e delegados.</span><span class="sxs-lookup"><span data-stu-id="9c1f2-111">Can be used only in generic interfaces and delegates.</span></span> <span data-ttu-id="9c1f2-112">Você pode declarar um tipo covariant usando o [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md) palavra-chave ou contravariant usando o [na](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="9c1f2-112">You can declare a type covariant by using the [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md) keyword or contravariant by using the [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) keyword.</span></span> <span data-ttu-id="9c1f2-113">Consulte [Covariância e contravariância](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="9c1f2-113">See [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>|  
|`typename`|<span data-ttu-id="9c1f2-114">Necessário.</span><span class="sxs-lookup"><span data-stu-id="9c1f2-114">Required.</span></span> <span data-ttu-id="9c1f2-115">Nome do parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="9c1f2-115">Name of the type parameter.</span></span> <span data-ttu-id="9c1f2-116">Este é um espaço reservado, a ser substituído por um tipo definido fornecido pelo argumento de tipo correspondente.</span><span class="sxs-lookup"><span data-stu-id="9c1f2-116">This is a placeholder, to be replaced by a defined type supplied by the corresponding type argument.</span></span>|  
|`constraintlist`|<span data-ttu-id="9c1f2-117">Opcional.</span><span class="sxs-lookup"><span data-stu-id="9c1f2-117">Optional.</span></span> <span data-ttu-id="9c1f2-118">Lista de requisitos que restringe o tipo de dados que pode ser fornecido para `typename`.</span><span class="sxs-lookup"><span data-stu-id="9c1f2-118">List of requirements that constrain the data type that can be supplied for `typename`.</span></span> <span data-ttu-id="9c1f2-119">Se você tiver várias restrições, coloque-as entre chaves (`{ }`) e separe-as com vírgulas.</span><span class="sxs-lookup"><span data-stu-id="9c1f2-119">If you have multiple constraints, enclose them in curly braces (`{ }`) and separate them with commas.</span></span> <span data-ttu-id="9c1f2-120">Você deve apresentar a lista de restrições com a [como](../../../visual-basic/language-reference/statements/as-clause.md) palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="9c1f2-120">You must introduce the constraint list with the [As](../../../visual-basic/language-reference/statements/as-clause.md) keyword.</span></span> <span data-ttu-id="9c1f2-121">Você usa `As` apenas uma vez, no início da lista.</span><span class="sxs-lookup"><span data-stu-id="9c1f2-121">You use `As` only once, at the beginning of the list.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c1f2-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="9c1f2-122">Remarks</span></span>  
 <span data-ttu-id="9c1f2-123">Cada elemento de programação genérico deve levar pelo menos um parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="9c1f2-123">Every generic programming element must take at least one type parameter.</span></span> <span data-ttu-id="9c1f2-124">Um parâmetro de tipo é um espaço reservado para um tipo específico (um *elemento construído*) que o código do cliente especifica quando ele cria uma instância do tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="9c1f2-124">A type parameter is a placeholder for a specific type (a *constructed element*) that client code specifies when it creates an instance of the generic type.</span></span> <span data-ttu-id="9c1f2-125">Você pode definir uma classe genérica, estrutura, interface, procedimento ou delegado.</span><span class="sxs-lookup"><span data-stu-id="9c1f2-125">You can define a generic class, structure, interface, procedure, or delegate.</span></span>  
  
 <span data-ttu-id="9c1f2-126">Para obter mais informações sobre quando definir um tipo genérico, consulte [tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span><span class="sxs-lookup"><span data-stu-id="9c1f2-126">For more information on when to define a generic type, see [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).</span></span> <span data-ttu-id="9c1f2-127">Para obter mais informações sobre nomes de parâmetro de tipo, consulte [nomes de elemento declarado](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="9c1f2-127">For more information on type parameter names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="9c1f2-128">Regras</span><span class="sxs-lookup"><span data-stu-id="9c1f2-128">Rules</span></span>  
  
-   <span data-ttu-id="9c1f2-129">**Parênteses.**</span><span class="sxs-lookup"><span data-stu-id="9c1f2-129">**Parentheses.**</span></span> <span data-ttu-id="9c1f2-130">Se você fornecer uma lista de parâmetros de tipo, você deve colocá-la entre parênteses e você deve apresentar a lista com o [de](../../../visual-basic/language-reference/statements/of-clause.md) palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="9c1f2-130">If you supply a type parameter list, you must enclose it in parentheses, and you must introduce the list with the [Of](../../../visual-basic/language-reference/statements/of-clause.md) keyword.</span></span> <span data-ttu-id="9c1f2-131">Você usa `Of` apenas uma vez, no início da lista.</span><span class="sxs-lookup"><span data-stu-id="9c1f2-131">You use `Of` only once, at the beginning of the list.</span></span>  
  
-   <span data-ttu-id="9c1f2-132">**Restrições.**</span><span class="sxs-lookup"><span data-stu-id="9c1f2-132">**Constraints.**</span></span> <span data-ttu-id="9c1f2-133">Uma lista de *restrições* em um tipo de parâmetro pode incluir os seguintes itens em qualquer combinação:</span><span class="sxs-lookup"><span data-stu-id="9c1f2-133">A list of *constraints* on a type parameter can include the following items in any combination:</span></span>  
  
    -   <span data-ttu-id="9c1f2-134">Qualquer número de interfaces.</span><span class="sxs-lookup"><span data-stu-id="9c1f2-134">Any number of interfaces.</span></span> <span data-ttu-id="9c1f2-135">O tipo fornecido deve implementar cada interface nesta lista.</span><span class="sxs-lookup"><span data-stu-id="9c1f2-135">The supplied type must implement every interface in this list.</span></span>  
  
    -   <span data-ttu-id="9c1f2-136">No máximo uma classe.</span><span class="sxs-lookup"><span data-stu-id="9c1f2-136">At most one class.</span></span> <span data-ttu-id="9c1f2-137">O tipo fornecido deve herdar dessa classe.</span><span class="sxs-lookup"><span data-stu-id="9c1f2-137">The supplied type must inherit from that class.</span></span>  
  
    -   <span data-ttu-id="9c1f2-138">A palavra-chave `New`.</span><span class="sxs-lookup"><span data-stu-id="9c1f2-138">The `New` keyword.</span></span> <span data-ttu-id="9c1f2-139">O tipo fornecido deve expor um construtor sem parâmetros que pode acessar o tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="9c1f2-139">The supplied type must expose a parameterless constructor that your generic type can access.</span></span> <span data-ttu-id="9c1f2-140">Isso é útil se você restringir um parâmetro de tipo por uma ou mais interfaces.</span><span class="sxs-lookup"><span data-stu-id="9c1f2-140">This is useful if you constrain a type parameter by one or more interfaces.</span></span> <span data-ttu-id="9c1f2-141">Um tipo que implementa as interfaces não necessariamente expõe um construtor e, dependendo do nível de acesso de um construtor, o código dentro de tipo genérico não pode ser capaz de acessá-lo.</span><span class="sxs-lookup"><span data-stu-id="9c1f2-141">A type that implements interfaces does not necessarily expose a constructor, and depending on the access level of a constructor, the code within the generic type might not be able to access it.</span></span>  
  
    -   <span data-ttu-id="9c1f2-142">Ambos os `Class` palavra-chave ou o `Structure` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="9c1f2-142">Either the `Class` keyword or the `Structure` keyword.</span></span> <span data-ttu-id="9c1f2-143">O `Class` palavra-chave restringe um parâmetro de tipo genérico para exigir que qualquer argumento de tipo passado para ele seja um tipo de referência, por exemplo uma cadeia de caracteres, matriz ou delegado, ou um objeto criado a partir de uma classe.</span><span class="sxs-lookup"><span data-stu-id="9c1f2-143">The `Class` keyword constrains a generic type parameter to require that any type argument passed to it be a reference type, for example a string, array, or delegate, or an object created from a class.</span></span> <span data-ttu-id="9c1f2-144">O `Structure` palavra-chave restringe um parâmetro de tipo genérico para exigir que qualquer argumento de tipo passado para ele seja um tipo de valor, por exemplo, uma estrutura, enumeração ou dados elementares digite.</span><span class="sxs-lookup"><span data-stu-id="9c1f2-144">The `Structure` keyword constrains a generic type parameter to require that any type argument passed to it be a value type, for example a structure, enumeration, or elementary data type.</span></span> <span data-ttu-id="9c1f2-145">Você não pode incluir ambos `Class` e `Structure` no mesmo `constraintlist`.</span><span class="sxs-lookup"><span data-stu-id="9c1f2-145">You cannot include both `Class` and `Structure` in the same `constraintlist`.</span></span>  
  
     <span data-ttu-id="9c1f2-146">O tipo fornecido deve satisfazer cada requisito que você incluir no `constraintlist`.</span><span class="sxs-lookup"><span data-stu-id="9c1f2-146">The supplied type must satisfy every requirement you include in `constraintlist`.</span></span>  
  
     <span data-ttu-id="9c1f2-147">Restrições em cada parâmetro de tipo são independentes de restrições em outros parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="9c1f2-147">Constraints on each type parameter are independent of constraints on other type parameters.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="9c1f2-148">Comportamento</span><span class="sxs-lookup"><span data-stu-id="9c1f2-148">Behavior</span></span>  
  
-   <span data-ttu-id="9c1f2-149">**Substituição de tempo de compilação.**</span><span class="sxs-lookup"><span data-stu-id="9c1f2-149">**Compile-Time Substitution.**</span></span> <span data-ttu-id="9c1f2-150">Quando você cria um tipo construído de um elemento de programação genérico, você fornece um tipo definido para cada parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="9c1f2-150">When you create a constructed type from a generic programming element, you supply a defined type for each type parameter.</span></span> <span data-ttu-id="9c1f2-151">O compilador do Visual Basic substitui esse tipo fornecido para cada ocorrência de `typename` dentro do elemento genérico.</span><span class="sxs-lookup"><span data-stu-id="9c1f2-151">The Visual Basic compiler substitutes that supplied type for every occurrence of `typename` within the generic element.</span></span>  
  
-   <span data-ttu-id="9c1f2-152">**Ausência de restrições.**</span><span class="sxs-lookup"><span data-stu-id="9c1f2-152">**Absence of Constraints.**</span></span> <span data-ttu-id="9c1f2-153">Se você não especificar quaisquer restrições em um parâmetro de tipo, seu código está limitado às operações e membros com suporte a [tipo de dados de objeto](../../../visual-basic/language-reference/data-types/object-data-type.md) para esse parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="9c1f2-153">If you do not specify any constraints on a type parameter, your code is limited to the operations and members supported by the [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md) for that type parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c1f2-154">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9c1f2-154">Example</span></span>  
 <span data-ttu-id="9c1f2-155">O exemplo a seguir mostra uma definição de uma classe de dicionário genérica, incluindo uma função reduzida para adicionar uma nova entrada ao dicionário.</span><span class="sxs-lookup"><span data-stu-id="9c1f2-155">The following example shows a skeleton definition of a generic dictionary class, including a skeleton function to add a new entry to the dictionary.</span></span>  
  
 [!code-vb[VbVbalrStatements#3](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="9c1f2-156">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9c1f2-156">Example</span></span>  
 <span data-ttu-id="9c1f2-157">Porque `dictionary` é genérico, o código que o usa pode criar uma variedade de objetos, cada um tendo a mesma funcionalidade mas agindo em um tipo de dados diferente.</span><span class="sxs-lookup"><span data-stu-id="9c1f2-157">Because `dictionary` is generic, the code that uses it can create a variety of objects from it, each having the same functionality but acting on a different data type.</span></span> <span data-ttu-id="9c1f2-158">O exemplo a seguir mostra uma linha de código que cria um `dictionary` do objeto com `String` entradas e `Integer` chaves.</span><span class="sxs-lookup"><span data-stu-id="9c1f2-158">The following example shows a line of code that creates a `dictionary` object with `String` entries and `Integer` keys.</span></span>  
  
 [!code-vb[VbVbalrStatements#4](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="9c1f2-159">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9c1f2-159">Example</span></span>  
 <span data-ttu-id="9c1f2-160">O exemplo a seguir mostra a definição reduzida equivalente gerada pelo exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="9c1f2-160">The following example shows the equivalent skeleton definition generated by the preceding example.</span></span>  
  
 [!code-vb[VbVbalrStatements#5](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9c1f2-161">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9c1f2-161">See Also</span></span>  
 [<span data-ttu-id="9c1f2-162">Of</span><span class="sxs-lookup"><span data-stu-id="9c1f2-162">Of</span></span>](../../../visual-basic/language-reference/statements/of-clause.md)  
 [<span data-ttu-id="9c1f2-163">Operador New</span><span class="sxs-lookup"><span data-stu-id="9c1f2-163">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)  
 [<span data-ttu-id="9c1f2-164">Níveis de acesso no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9c1f2-164">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="9c1f2-165">Tipo de Dados Object</span><span class="sxs-lookup"><span data-stu-id="9c1f2-165">Object Data Type</span></span>](../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [<span data-ttu-id="9c1f2-166">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="9c1f2-166">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="9c1f2-167">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="9c1f2-167">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="9c1f2-168">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="9c1f2-168">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="9c1f2-169">Como usar uma classe genérica</span><span class="sxs-lookup"><span data-stu-id="9c1f2-169">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [<span data-ttu-id="9c1f2-170">Covariância e Contravariância</span><span class="sxs-lookup"><span data-stu-id="9c1f2-170">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)  
 [<span data-ttu-id="9c1f2-171">In</span><span class="sxs-lookup"><span data-stu-id="9c1f2-171">In</span></span>](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)  
 [<span data-ttu-id="9c1f2-172">Saída</span><span class="sxs-lookup"><span data-stu-id="9c1f2-172">Out</span></span>](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
