---
title: Instrução With...End With (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.With
helpviewer_keywords:
- With keyword [Visual Basic]
- loop structures [Visual Basic], and With...End With statements
- execution [Visual Basic], on object
- instructions, repeating
- With...End With statements [Visual Basic]
- With statement [Visual Basic]
- With statement [Visual Basic], nesting
- objects [Visual Basic], accessing
- With block
- End keyword [Visual Basic], With...End With statements
ms.assetid: 340d5fbb-4f43-48ec-a024-80843c137817
ms.openlocfilehash: de2edc6b16689673c3be6703ff1a201febe73526
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698636"
---
# <a name="withend-with-statement-visual-basic"></a><span data-ttu-id="5fb5f-102">Instrução With...End With (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5fb5f-102">With...End With Statement (Visual Basic)</span></span>
<span data-ttu-id="5fb5f-103">Executa uma série de instruções que referenciam repetidamente um único objeto ou estrutura de modo que as instruções possam usar uma sintaxe simplificada para acessar membros do objeto ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="5fb5f-103">Executes a series of statements that repeatedly refer to a single object or structure so that the statements can use a simplified syntax when accessing members of the object or structure.</span></span>  <span data-ttu-id="5fb5f-104">Ao usar uma estrutura, você só poderá ler os valores dos membros ou invocar métodos, e obterá um erro se tentar atribuir valores aos membros de uma estrutura usada em uma instrução `With...End With`.</span><span class="sxs-lookup"><span data-stu-id="5fb5f-104">When using a structure, you can only read the values of members or invoke methods, and you get an error if you try to assign values to members of a structure used in a `With...End With` statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fb5f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5fb5f-105">Syntax</span></span>  
  
```  
With objectExpression  
    [ statements ]  
End With  
```  
  
## <a name="parts"></a><span data-ttu-id="5fb5f-106">Partes</span><span class="sxs-lookup"><span data-stu-id="5fb5f-106">Parts</span></span>  
  
|<span data-ttu-id="5fb5f-107">Termo</span><span class="sxs-lookup"><span data-stu-id="5fb5f-107">Term</span></span>|<span data-ttu-id="5fb5f-108">Definição</span><span class="sxs-lookup"><span data-stu-id="5fb5f-108">Definition</span></span>|  
|---|---|  
|`objectExpression`|<span data-ttu-id="5fb5f-109">Necessário.</span><span class="sxs-lookup"><span data-stu-id="5fb5f-109">Required.</span></span> <span data-ttu-id="5fb5f-110">Uma expressão que avalia como um objeto.</span><span class="sxs-lookup"><span data-stu-id="5fb5f-110">An expression that evaluates to an object.</span></span> <span data-ttu-id="5fb5f-111">A expressão pode ser arbitrariamente complexa e é avaliada apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="5fb5f-111">The expression may be arbitrarily complex and is evaluated only once.</span></span> <span data-ttu-id="5fb5f-112">A expressão pode ser avaliada como qualquer tipo de dados, inclusive tipos elementares.</span><span class="sxs-lookup"><span data-stu-id="5fb5f-112">The expression can evaluate to any data type, including elementary types.</span></span>|  
|`statements`|<span data-ttu-id="5fb5f-113">Opcional.</span><span class="sxs-lookup"><span data-stu-id="5fb5f-113">Optional.</span></span> <span data-ttu-id="5fb5f-114">Uma ou mais instruções entre `With` e `End With` que podem fazer referência a membros de um objeto que é gerado pela avaliação de `objectExpression`.</span><span class="sxs-lookup"><span data-stu-id="5fb5f-114">One or more statements between `With` and `End With` that may refer to members of an object that's produced by the evaluation of `objectExpression`.</span></span>|  
|`End With`|<span data-ttu-id="5fb5f-115">Necessário.</span><span class="sxs-lookup"><span data-stu-id="5fb5f-115">Required.</span></span> <span data-ttu-id="5fb5f-116">Finaliza a definição do bloco `With`.</span><span class="sxs-lookup"><span data-stu-id="5fb5f-116">Terminates the definition of the `With` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5fb5f-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="5fb5f-117">Remarks</span></span>  
 <span data-ttu-id="5fb5f-118">Usando `With...End With`, você pode executar uma série de instruções em um objeto especificado sem especificar o nome do objeto várias vezes.</span><span class="sxs-lookup"><span data-stu-id="5fb5f-118">By using `With...End With`, you can perform a series of statements on a specified object without specifying the name of the object multiple times.</span></span> <span data-ttu-id="5fb5f-119">Dentro de um bloco de instrução `With`, você pode especificar um membro do objeto que começa com um ponto, como se o objeto de instrução `With` o precedesse.</span><span class="sxs-lookup"><span data-stu-id="5fb5f-119">Within a `With` statement block, you can specify a member of the object starting with a period, as if the `With` statement object preceded it.</span></span>  
  
 <span data-ttu-id="5fb5f-120">Por exemplo, para alterar várias propriedades diferentes em um único objeto, coloque as instruções de atribuição de propriedade dentro do bloco `With...End With`, fazendo referência ao objeto apenas uma vez em vez de uma vez para cada atribuição de propriedade.</span><span class="sxs-lookup"><span data-stu-id="5fb5f-120">For example, to change multiple properties on a single object, place the property assignment statements inside the `With...End With` block, referring to the object only once instead of once for each property assignment.</span></span>  
  
 <span data-ttu-id="5fb5f-121">Se seu código acessar o mesmo objeto em várias instruções, você ganhará os seguintes benefícios usando a instrução `With`:</span><span class="sxs-lookup"><span data-stu-id="5fb5f-121">If your code accesses the same object in multiple statements, you gain the following benefits by using the `With` statement:</span></span>  
  
- <span data-ttu-id="5fb5f-122">Você não precisa avaliar várias vezes uma expressão complexa ou atribuir o resultado a uma variável temporária para fazer referência a seus membros várias vezes.</span><span class="sxs-lookup"><span data-stu-id="5fb5f-122">You don't need to evaluate a complex expression multiple times or assign the result to a temporary variable to refer to its members multiple times.</span></span>  
  
- <span data-ttu-id="5fb5f-123">Você torna seu código mais legível eliminando expressões aplicáveis repetitivas.</span><span class="sxs-lookup"><span data-stu-id="5fb5f-123">You make your code more readable by eliminating repetitive qualifying expressions.</span></span>  
  
 <span data-ttu-id="5fb5f-124">O tipo de dados de `objectExpression` pode ser qualquer tipo de classe ou estrutura, ou até mesmo um tipo elementar do Visual Basic, como `Integer`.</span><span class="sxs-lookup"><span data-stu-id="5fb5f-124">The data type of `objectExpression` can be any class or structure type or even a Visual Basic elementary type such as `Integer`.</span></span>  <span data-ttu-id="5fb5f-125">Se `objectExpression` resultar em algo diferente de um objeto, você só poderá ler os valores de seus membros ou invocar métodos, e obterá um erro se tentar atribuir valores aos membros de uma estrutura usada em uma instrução `With...End With`.</span><span class="sxs-lookup"><span data-stu-id="5fb5f-125">If `objectExpression` results in anything other than an object, you can only read the values of its members or invoke methods, and you get an error if you try to assign values to members of a structure used in a `With...End With` statement.</span></span>  <span data-ttu-id="5fb5f-126">Esse é o mesmo erro que você obteria se invocasse um método que retornasse uma estrutura e imediatamente acessasse e atribuísse um valor a um membro do resultado da função, como `GetAPoint().x = 1`.</span><span class="sxs-lookup"><span data-stu-id="5fb5f-126">This is the same error you would get if you invoked a method that returned a structure and immediately accessed and assigned a value to a member of the function’s result, such as `GetAPoint().x = 1`.</span></span>  <span data-ttu-id="5fb5f-127">O problema em ambos os casos é que a estrutura só existe na pilha de chamadas, e não há maneira de um membro da estrutura alterada nessas situações gravar em um local de modo que qualquer outro código no programa possa observar a alteração.</span><span class="sxs-lookup"><span data-stu-id="5fb5f-127">The problem in both cases is that the structure exists only on the call stack, and there is no way a modified structure member in these situations can write to  a location such that any other code in the program can observe the change.</span></span>  
  
 <span data-ttu-id="5fb5f-128">`objectExpression` é avaliada uma vez, ao entrar no bloco.</span><span class="sxs-lookup"><span data-stu-id="5fb5f-128">The `objectExpression` is evaluated once, upon entry into the block.</span></span> <span data-ttu-id="5fb5f-129">Você não pode reatribuir `objectExpression` de dentro do bloco `With`.</span><span class="sxs-lookup"><span data-stu-id="5fb5f-129">You can't reassign the `objectExpression` from within the `With` block.</span></span>  
  
 <span data-ttu-id="5fb5f-130">Dentro de um bloco `With`, você pode acessar os métodos e as propriedades de apenas o objeto especificado sem qualificá-los.</span><span class="sxs-lookup"><span data-stu-id="5fb5f-130">Within a `With` block, you can access the methods and properties of only the specified object without qualifying them.</span></span> <span data-ttu-id="5fb5f-131">Você pode usar métodos e propriedades de outros objetos, mas deverá qualificá-los com seus nomes de objeto.</span><span class="sxs-lookup"><span data-stu-id="5fb5f-131">You can use methods and properties of other objects, but you must qualify them with their object names.</span></span>  
  
 <span data-ttu-id="5fb5f-132">Você pode colocar uma instrução `With...End With` dentro de outra.</span><span class="sxs-lookup"><span data-stu-id="5fb5f-132">You can place one `With...End With` statement within another.</span></span> <span data-ttu-id="5fb5f-133">As instruções `With...End With` aninhadas podem ser confusas se os objetos que estão sendo referidos não são claros em termos de contexto.</span><span class="sxs-lookup"><span data-stu-id="5fb5f-133">Nested `With...End With` statements may be confusing if the objects that are being referred to aren't clear from context.</span></span> <span data-ttu-id="5fb5f-134">Você deve fornecer uma referência totalmente qualificada a um objeto que esteja em um bloco `With` externo quando o objeto é referenciado dentro de um bloco `With` interno.</span><span class="sxs-lookup"><span data-stu-id="5fb5f-134">You must provide a fully qualified reference to an object that's in an outer `With` block when the object is referenced from within an inner `With` block.</span></span>  
  
 <span data-ttu-id="5fb5f-135">Você não pode ramificar em uma instrução `With` de fora do bloco.</span><span class="sxs-lookup"><span data-stu-id="5fb5f-135">You can't branch into a `With` statement block from outside the block.</span></span>  
  
 <span data-ttu-id="5fb5f-136">A menos que o bloco contenha um loop, as instruções são executadas somente uma vez.</span><span class="sxs-lookup"><span data-stu-id="5fb5f-136">Unless the block contains a loop, the statements run only once.</span></span> <span data-ttu-id="5fb5f-137">Você pode aninhar diferentes tipos de estruturas de controle.</span><span class="sxs-lookup"><span data-stu-id="5fb5f-137">You can nest different kinds of control structures.</span></span> <span data-ttu-id="5fb5f-138">Para obter mais informações, consulte [estruturas de controle aninhadas](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="5fb5f-138">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5fb5f-139">Você também pode usar a palavra-chave `With` em inicializadores de objetos.</span><span class="sxs-lookup"><span data-stu-id="5fb5f-139">You can use the `With` keyword in object initializers also.</span></span> <span data-ttu-id="5fb5f-140">Para obter mais informações e exemplos, consulte [inicializadores de objeto: Tipos nomeados e anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) e [tipos anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="5fb5f-140">For more information and examples, see [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) and [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
>   
>  <span data-ttu-id="5fb5f-141">Se você estiver usando um bloco `With` somente para inicializar as propriedades ou os campos de um objeto que acabou de instanciar, considere usar um inicializador do objeto como alternativa.</span><span class="sxs-lookup"><span data-stu-id="5fb5f-141">If you're using a `With` block only to initialize the properties or fields of an object that you've just instantiated, consider using an object initializer instead.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fb5f-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5fb5f-142">Example</span></span>  
 <span data-ttu-id="5fb5f-143">No exemplo a seguir, cada bloco `With` executa uma série de instruções em um único objeto.</span><span class="sxs-lookup"><span data-stu-id="5fb5f-143">In the following example, each `With` block executes a series of statements on a single object.</span></span>  
  
 [!code-vb[VbVbalrWithStatement#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="5fb5f-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5fb5f-144">Example</span></span>  
 <span data-ttu-id="5fb5f-145">O exemplo a seguir aninha instruções `With…End With`.</span><span class="sxs-lookup"><span data-stu-id="5fb5f-145">The following example nests `With…End With` statements.</span></span> <span data-ttu-id="5fb5f-146">Na instrução `With` aninhada, a sintaxe faz referência ao objeto interno.</span><span class="sxs-lookup"><span data-stu-id="5fb5f-146">Within the nested `With` statement, the syntax refers to the inner object.</span></span>  
  
 [!code-vb[VbVbalrWithStatement#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrwithstatement/vb/mainwindow.xaml.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="5fb5f-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5fb5f-147">See also</span></span>

- <xref:System.Collections.Generic.List%601>
- [<span data-ttu-id="5fb5f-148">Estruturas de Controle Aninhadas</span><span class="sxs-lookup"><span data-stu-id="5fb5f-148">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="5fb5f-149">Inicializadores de objeto: Tipos nomeados e anônimos</span><span class="sxs-lookup"><span data-stu-id="5fb5f-149">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="5fb5f-150">Tipos Anônimos</span><span class="sxs-lookup"><span data-stu-id="5fb5f-150">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
