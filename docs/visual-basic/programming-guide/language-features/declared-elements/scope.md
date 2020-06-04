---
title: Escopo
ms.date: 07/20/2015
helpviewer_keywords:
- module scope [Visual Basic]
- scope [Visual Basic], levels
- module level
- procedures [Visual Basic], scope
- declared elements [Visual Basic], scope
- namespaces [Visual Basic], scope
- scope [Visual Basic], declared elements
- scope [Visual Basic], about scope
- levels of scope [Visual Basic]
- block scope [Visual Basic]
- scope [Visual Basic], Visual Basic
- procedure scope [Visual Basic]
ms.assetid: 208106fe-79c9-4eec-93c6-55f08548895f
ms.openlocfilehash: 1bee904996257474b7457b2aefb1f17d250933cb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410728"
---
# <a name="scope-in-visual-basic"></a><span data-ttu-id="534ac-102">Escopo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="534ac-102">Scope in Visual Basic</span></span>

<span data-ttu-id="534ac-103">O *escopo* de um elemento declarado é o conjunto de todo o código que pode fazer referência a ele sem qualificar seu nome ou disponibilizá-lo por meio de uma [instrução Imports (namespace e tipo do .net)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="534ac-103">The *scope* of a declared element is the set of all code that can refer to it without qualifying its name or making it available through an [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span> <span data-ttu-id="534ac-104">Um elemento pode ter um escopo em um dos seguintes níveis:</span><span class="sxs-lookup"><span data-stu-id="534ac-104">An element can have scope at one of the following levels:</span></span>

|<span data-ttu-id="534ac-105">Nível</span><span class="sxs-lookup"><span data-stu-id="534ac-105">Level</span></span>|<span data-ttu-id="534ac-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="534ac-106">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="534ac-107">Escopo de bloco</span><span class="sxs-lookup"><span data-stu-id="534ac-107">Block scope</span></span>|<span data-ttu-id="534ac-108">Disponível somente dentro do bloco de código no qual ele é declarado</span><span class="sxs-lookup"><span data-stu-id="534ac-108">Available only within the code block in which it is declared</span></span>|
|<span data-ttu-id="534ac-109">Escopo do procedimento</span><span class="sxs-lookup"><span data-stu-id="534ac-109">Procedure scope</span></span>|<span data-ttu-id="534ac-110">Disponível para todo o código dentro do procedimento no qual ele é declarado</span><span class="sxs-lookup"><span data-stu-id="534ac-110">Available to all code within the procedure in which it is declared</span></span>|
|<span data-ttu-id="534ac-111">Escopo do módulo</span><span class="sxs-lookup"><span data-stu-id="534ac-111">Module scope</span></span>|<span data-ttu-id="534ac-112">Disponível para todo o código dentro do módulo, da classe ou da estrutura na qual ele é declarado</span><span class="sxs-lookup"><span data-stu-id="534ac-112">Available to all code within the module, class, or structure in which it is declared</span></span>|
|<span data-ttu-id="534ac-113">Escopo do namespace</span><span class="sxs-lookup"><span data-stu-id="534ac-113">Namespace scope</span></span>|<span data-ttu-id="534ac-114">Disponível para todo o código no namespace no qual ele é declarado</span><span class="sxs-lookup"><span data-stu-id="534ac-114">Available to all code in the namespace in which it is declared</span></span>|

<span data-ttu-id="534ac-115">Esses níveis de progresso do escopo do mais estreito (bloco) para o mais largo (namespace), em que o *escopo mais estreito* significa o menor conjunto de código que pode se referir ao elemento sem qualificação.</span><span class="sxs-lookup"><span data-stu-id="534ac-115">These levels of scope progress from the narrowest (block) to the widest (namespace), where *narrowest scope* means the smallest set of code that can refer to the element without qualification.</span></span> <span data-ttu-id="534ac-116">Para obter mais informações, consulte "níveis de escopo" nesta página.</span><span class="sxs-lookup"><span data-stu-id="534ac-116">For more information, see "Levels of Scope" on this page.</span></span>

## <a name="specifying-scope-and-defining-variables"></a><span data-ttu-id="534ac-117">Especificando o escopo e Definindo variáveis</span><span class="sxs-lookup"><span data-stu-id="534ac-117">Specifying Scope and Defining Variables</span></span>

<span data-ttu-id="534ac-118">Você especifica o escopo de um elemento ao declará-lo.</span><span class="sxs-lookup"><span data-stu-id="534ac-118">You specify the scope of an element when you declare it.</span></span> <span data-ttu-id="534ac-119">O escopo pode depender dos seguintes fatores:</span><span class="sxs-lookup"><span data-stu-id="534ac-119">The scope can depend on the following factors:</span></span>

- <span data-ttu-id="534ac-120">A região (bloco, procedimento, módulo, classe ou estrutura) na qual você declara o elemento</span><span class="sxs-lookup"><span data-stu-id="534ac-120">The region (block, procedure, module, class, or structure) in which you declare the element</span></span>

- <span data-ttu-id="534ac-121">O namespace que contém a declaração do elemento</span><span class="sxs-lookup"><span data-stu-id="534ac-121">The namespace containing the element's declaration</span></span>

- <span data-ttu-id="534ac-122">O nível de acesso que você declara para o elemento</span><span class="sxs-lookup"><span data-stu-id="534ac-122">The access level you declare for the element</span></span>

<span data-ttu-id="534ac-123">Tenha cuidado ao definir variáveis com o mesmo nome, mas com escopo diferente, porque isso pode levar a resultados inesperados.</span><span class="sxs-lookup"><span data-stu-id="534ac-123">Use care when you define variables with the same name but different scope, because doing so can lead to unexpected results.</span></span> <span data-ttu-id="534ac-124">Para obter mais informações, consulte [referências a elementos declarados](references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="534ac-124">For more information, see [References to Declared Elements](references-to-declared-elements.md).</span></span>

## <a name="levels-of-scope"></a><span data-ttu-id="534ac-125">Níveis de escopo</span><span class="sxs-lookup"><span data-stu-id="534ac-125">Levels of Scope</span></span>

<span data-ttu-id="534ac-126">Um elemento de programação está disponível em toda a região em que você o declara.</span><span class="sxs-lookup"><span data-stu-id="534ac-126">A programming element is available throughout the region in which you declare it.</span></span> <span data-ttu-id="534ac-127">Todo o código na mesma região pode se referir ao elemento sem qualificar seu nome.</span><span class="sxs-lookup"><span data-stu-id="534ac-127">All code in the same region can refer to the element without qualifying its name.</span></span>

### <a name="block-scope"></a><span data-ttu-id="534ac-128">Escopo do bloco</span><span class="sxs-lookup"><span data-stu-id="534ac-128">Block Scope</span></span>

<span data-ttu-id="534ac-129">Um bloco é um conjunto de instruções incluídas em instruções de declaração de início e término, como a seguinte:</span><span class="sxs-lookup"><span data-stu-id="534ac-129">A block is a set of statements enclosed within initiating and terminating declaration statements, such as the following:</span></span>

- <span data-ttu-id="534ac-130">`Do` e `Loop`</span><span class="sxs-lookup"><span data-stu-id="534ac-130">`Do` and `Loop`</span></span>

- <span data-ttu-id="534ac-131">`For`[ `Each` ] e`Next`</span><span class="sxs-lookup"><span data-stu-id="534ac-131">`For` [`Each`] and `Next`</span></span>

- <span data-ttu-id="534ac-132">`If` e `End If`</span><span class="sxs-lookup"><span data-stu-id="534ac-132">`If` and `End If`</span></span>

- <span data-ttu-id="534ac-133">`Select` e `End Select`</span><span class="sxs-lookup"><span data-stu-id="534ac-133">`Select` and `End Select`</span></span>

- <span data-ttu-id="534ac-134">`SyncLock` e `End SyncLock`</span><span class="sxs-lookup"><span data-stu-id="534ac-134">`SyncLock` and `End SyncLock`</span></span>

- <span data-ttu-id="534ac-135">`Try` e `End Try`</span><span class="sxs-lookup"><span data-stu-id="534ac-135">`Try` and `End Try`</span></span>

- <span data-ttu-id="534ac-136">`While` e `End While`</span><span class="sxs-lookup"><span data-stu-id="534ac-136">`While` and `End While`</span></span>

- <span data-ttu-id="534ac-137">`With` e `End With`</span><span class="sxs-lookup"><span data-stu-id="534ac-137">`With` and `End With`</span></span>

<span data-ttu-id="534ac-138">Se você declarar uma variável em um bloco, poderá usá-la somente dentro desse bloco.</span><span class="sxs-lookup"><span data-stu-id="534ac-138">If you declare a variable within a block, you can use it only within that block.</span></span> <span data-ttu-id="534ac-139">No exemplo a seguir, o escopo da variável de inteiro `cube` é o bloco entre `If` e `End If` , e você não pode mais se referir `cube` quando a execução passa para fora do bloco.</span><span class="sxs-lookup"><span data-stu-id="534ac-139">In the following example, the scope of the integer variable `cube` is the block between `If` and `End If`, and you can no longer refer to `cube` when execution passes out of the block.</span></span>

```vb
If n < 1291 Then
    Dim cube As Integer
    cube = n ^ 3
End If
```

> [!NOTE]
> <span data-ttu-id="534ac-140">Mesmo que o escopo de uma variável seja limitado a um bloco, seu tempo de vida ainda é o de todo o procedimento.</span><span class="sxs-lookup"><span data-stu-id="534ac-140">Even if the scope of a variable is limited to a block, its lifetime is still that of the entire procedure.</span></span> <span data-ttu-id="534ac-141">Se você inserir o bloco mais de uma vez durante o procedimento, cada variável de bloco manterá seu valor anterior.</span><span class="sxs-lookup"><span data-stu-id="534ac-141">If you enter the block more than once during the procedure, each block variable retains its previous value.</span></span> <span data-ttu-id="534ac-142">Para evitar resultados inesperados nesse caso, é recomendável inicializar variáveis de bloco no início do bloco.</span><span class="sxs-lookup"><span data-stu-id="534ac-142">To avoid unexpected results in such a case, it is wise to initialize block variables at the beginning of the block.</span></span>

### <a name="procedure-scope"></a><span data-ttu-id="534ac-143">Escopo do procedimento</span><span class="sxs-lookup"><span data-stu-id="534ac-143">Procedure Scope</span></span>

<span data-ttu-id="534ac-144">Um elemento declarado em um procedimento não está disponível fora desse procedimento.</span><span class="sxs-lookup"><span data-stu-id="534ac-144">An element declared within a procedure is not available outside that procedure.</span></span> <span data-ttu-id="534ac-145">Somente o procedimento que contém a declaração pode usá-lo.</span><span class="sxs-lookup"><span data-stu-id="534ac-145">Only the procedure that contains the declaration can use it.</span></span> <span data-ttu-id="534ac-146">As variáveis nesse nível também são conhecidas como *variáveis locais*.</span><span class="sxs-lookup"><span data-stu-id="534ac-146">Variables at this level are also known as *local variables*.</span></span> <span data-ttu-id="534ac-147">Você os declara com a [instrução Dim](../../../language-reference/statements/dim-statement.md), com ou sem a palavra-chave [static](../../../language-reference/modifiers/static.md) .</span><span class="sxs-lookup"><span data-stu-id="534ac-147">You declare them with the [Dim Statement](../../../language-reference/statements/dim-statement.md), with or without the [Static](../../../language-reference/modifiers/static.md) keyword.</span></span>

<span data-ttu-id="534ac-148">O procedimento e o escopo do bloco estão fortemente relacionados.</span><span class="sxs-lookup"><span data-stu-id="534ac-148">Procedure and block scope are closely related.</span></span> <span data-ttu-id="534ac-149">Se você declarar uma variável dentro de um procedimento, mas fora de qualquer bloco dentro desse procedimento, você pode considerar a variável como tendo o escopo de bloco, onde o bloco é o procedimento inteiro.</span><span class="sxs-lookup"><span data-stu-id="534ac-149">If you declare a variable inside a procedure but outside any block within that procedure, you can think of the variable as having block scope, where the block is the entire procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="534ac-150">Todos os elementos locais, mesmo que sejam `Static` variáveis, são privados para o procedimento no qual aparecem.</span><span class="sxs-lookup"><span data-stu-id="534ac-150">All local elements, even if they are `Static` variables, are private to the procedure in which they appear.</span></span> <span data-ttu-id="534ac-151">Você não pode declarar nenhum elemento usando a palavra-chave [Public](../../../language-reference/modifiers/public.md) em um procedimento.</span><span class="sxs-lookup"><span data-stu-id="534ac-151">You cannot declare any element using the [Public](../../../language-reference/modifiers/public.md) keyword within a procedure.</span></span>

### <a name="module-scope"></a><span data-ttu-id="534ac-152">Escopo do módulo</span><span class="sxs-lookup"><span data-stu-id="534ac-152">Module Scope</span></span>

<span data-ttu-id="534ac-153">Para sua conveniência, o *nível de módulo* de termo único aplica-se igualmente a módulos, classes e estruturas.</span><span class="sxs-lookup"><span data-stu-id="534ac-153">For convenience, the single term *module level* applies equally to modules, classes, and structures.</span></span> <span data-ttu-id="534ac-154">Você pode declarar elementos nesse nível colocando a instrução de declaração fora de qualquer procedimento ou bloco, mas dentro do módulo, da classe ou da estrutura.</span><span class="sxs-lookup"><span data-stu-id="534ac-154">You can declare elements at this level by placing the declaration statement outside of any procedure or block but within the module, class, or structure.</span></span>

<span data-ttu-id="534ac-155">Quando você faz uma declaração no nível do módulo, o nível de acesso que você escolhe determina o escopo.</span><span class="sxs-lookup"><span data-stu-id="534ac-155">When you make a declaration at the module level, the access level you choose determines the scope.</span></span> <span data-ttu-id="534ac-156">O namespace que contém o módulo, a classe ou a estrutura também afeta o escopo.</span><span class="sxs-lookup"><span data-stu-id="534ac-156">The namespace that contains the module, class, or structure also affects the scope.</span></span>

<span data-ttu-id="534ac-157">Os elementos para os quais você declara o nível de acesso [privado](../../../language-reference/modifiers/private.md) estão disponíveis para cada procedimento nesse módulo, mas não para qualquer código em um módulo diferente.</span><span class="sxs-lookup"><span data-stu-id="534ac-157">Elements for which you declare [Private](../../../language-reference/modifiers/private.md) access level are available to every procedure in that module, but not to any code in a different module.</span></span> <span data-ttu-id="534ac-158">A `Dim` instrução no nível do módulo será padronizada `Private` se você não usar nenhuma palavra-chave de nível de acesso.</span><span class="sxs-lookup"><span data-stu-id="534ac-158">The `Dim` statement at module level defaults to `Private` if you do not use any access level keywords.</span></span> <span data-ttu-id="534ac-159">No entanto, você pode tornar o nível de escopo e de acesso mais óbvio usando a `Private` palavra-chave na `Dim` instrução.</span><span class="sxs-lookup"><span data-stu-id="534ac-159">However, you can make the scope and access level more obvious by using the `Private` keyword in the `Dim` statement.</span></span>

<span data-ttu-id="534ac-160">No exemplo a seguir, todos os procedimentos definidos no módulo podem se referir à variável de cadeia de caracteres `strMsg` .</span><span class="sxs-lookup"><span data-stu-id="534ac-160">In the following example, all procedures defined in the module can refer to the string variable `strMsg`.</span></span> <span data-ttu-id="534ac-161">Quando o segundo procedimento é chamado, ele exibe o conteúdo da variável de cadeia de caracteres `strMsg` em uma caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="534ac-161">When the second procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.</span></span>

```vb
' Put the following declaration at module level (not in any procedure).
Private strMsg As String
' Put the following Sub procedure in the same module.
Sub initializePrivateVariable()
    strMsg = "This variable cannot be used outside this module."
End Sub
' Put the following Sub procedure in the same module.
Sub usePrivateVariable()
    MsgBox(strMsg)
End Sub
```

### <a name="namespace-scope"></a><span data-ttu-id="534ac-162">Escopo do namespace</span><span class="sxs-lookup"><span data-stu-id="534ac-162">Namespace Scope</span></span>

<span data-ttu-id="534ac-163">Se você declarar um elemento no nível do módulo usando a palavra-chave [Friend](../../../language-reference/modifiers/friend.md) ou [Public](../../../language-reference/modifiers/public.md) , ele ficará disponível para todos os procedimentos em todo o namespace no qual o elemento é declarado.</span><span class="sxs-lookup"><span data-stu-id="534ac-163">If you declare an element at module level using the [Friend](../../../language-reference/modifiers/friend.md) or [Public](../../../language-reference/modifiers/public.md) keyword, it becomes available to all procedures throughout the namespace in which the element is declared.</span></span> <span data-ttu-id="534ac-164">Com a seguinte alteração no exemplo anterior, a variável de cadeia de caracteres `strMsg` pode ser referenciada pelo código em qualquer lugar no namespace de sua declaração.</span><span class="sxs-lookup"><span data-stu-id="534ac-164">With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.</span></span>

```vb
' Include this declaration at module level (not inside any procedure).
Public strMsg As String
```

<span data-ttu-id="534ac-165">O escopo do namespace inclui namespaces aninhados.</span><span class="sxs-lookup"><span data-stu-id="534ac-165">Namespace scope includes nested namespaces.</span></span> <span data-ttu-id="534ac-166">Um elemento disponível de dentro de um namespace também está disponível de dentro de qualquer namespace aninhado dentro desse namespace.</span><span class="sxs-lookup"><span data-stu-id="534ac-166">An element available from within a namespace is also available from within any namespace nested inside that namespace.</span></span>

<span data-ttu-id="534ac-167">Se o seu projeto não contiver nenhuma [instrução de namespace](../../../language-reference/statements/namespace-statement.md)s, tudo no projeto estará no mesmo namespace.</span><span class="sxs-lookup"><span data-stu-id="534ac-167">If your project does not contain any [Namespace Statement](../../../language-reference/statements/namespace-statement.md)s, everything in the project is in the same namespace.</span></span> <span data-ttu-id="534ac-168">Nesse caso, o escopo do namespace pode ser considerado como escopo do projeto.</span><span class="sxs-lookup"><span data-stu-id="534ac-168">In this case, namespace scope can be thought of as project scope.</span></span> <span data-ttu-id="534ac-169">`Public`os elementos em um módulo, classe ou estrutura também estão disponíveis para qualquer projeto que faça referência a seu projeto.</span><span class="sxs-lookup"><span data-stu-id="534ac-169">`Public` elements in a module, class, or structure are also available to any project that references their project.</span></span>

## <a name="choice-of-scope"></a><span data-ttu-id="534ac-170">Escolha do escopo</span><span class="sxs-lookup"><span data-stu-id="534ac-170">Choice of Scope</span></span>

<span data-ttu-id="534ac-171">Ao declarar uma variável, você deve ter em mente os seguintes pontos ao escolher seu escopo.</span><span class="sxs-lookup"><span data-stu-id="534ac-171">When you declare a variable, you should keep in mind the following points when choosing its scope.</span></span>

### <a name="advantages-of-local-variables"></a><span data-ttu-id="534ac-172">Vantagens das variáveis locais</span><span class="sxs-lookup"><span data-stu-id="534ac-172">Advantages of Local Variables</span></span>

<span data-ttu-id="534ac-173">As variáveis locais são uma boa opção para qualquer tipo de cálculo temporário, pelos seguintes motivos:</span><span class="sxs-lookup"><span data-stu-id="534ac-173">Local variables are a good choice for any kind of temporary calculation, for the following reasons:</span></span>

- <span data-ttu-id="534ac-174">**Prevenção de conflito de nomes.**</span><span class="sxs-lookup"><span data-stu-id="534ac-174">**Name Conflict Avoidance.**</span></span> <span data-ttu-id="534ac-175">Nomes de variáveis locais não são suscetíveis a conflitos.</span><span class="sxs-lookup"><span data-stu-id="534ac-175">Local variable names are not susceptible to conflict.</span></span> <span data-ttu-id="534ac-176">Por exemplo, você pode criar vários procedimentos diferentes contendo uma variável chamada `intTemp` .</span><span class="sxs-lookup"><span data-stu-id="534ac-176">For example, you can create several different procedures containing a variable called `intTemp`.</span></span> <span data-ttu-id="534ac-177">Desde que cada `intTemp` um seja declarado como uma variável local, cada procedimento reconhece apenas sua própria versão do `intTemp` .</span><span class="sxs-lookup"><span data-stu-id="534ac-177">As long as each `intTemp` is declared as a local variable, each procedure recognizes only its own version of `intTemp`.</span></span> <span data-ttu-id="534ac-178">Qualquer procedimento pode alterar o valor em seu local `intTemp` sem afetar as `intTemp` variáveis em outros procedimentos.</span><span class="sxs-lookup"><span data-stu-id="534ac-178">Any one procedure can alter the value in its local `intTemp` without affecting `intTemp` variables in other procedures.</span></span>

- <span data-ttu-id="534ac-179">**Consumo de memória.**</span><span class="sxs-lookup"><span data-stu-id="534ac-179">**Memory Consumption.**</span></span> <span data-ttu-id="534ac-180">As variáveis locais consomem memória somente enquanto o procedimento está em execução.</span><span class="sxs-lookup"><span data-stu-id="534ac-180">Local variables consume memory only while their procedure is running.</span></span> <span data-ttu-id="534ac-181">Sua memória é liberada quando o procedimento retorna ao código de chamada.</span><span class="sxs-lookup"><span data-stu-id="534ac-181">Their memory is released when the procedure returns to the calling code.</span></span> <span data-ttu-id="534ac-182">Por outro lado, variáveis [compartilhadas](../../../language-reference/modifiers/shared.md) e [estáticas](../../../language-reference/modifiers/static.md) consomem recursos de memória até que seu aplicativo pare de funcionar, portanto, use-os somente quando necessário.</span><span class="sxs-lookup"><span data-stu-id="534ac-182">By contrast, [Shared](../../../language-reference/modifiers/shared.md) and [Static](../../../language-reference/modifiers/static.md) variables consume memory resources until your application stops running, so use them only when necessary.</span></span> <span data-ttu-id="534ac-183">As *variáveis de instância* consomem memória enquanto sua instância continua a existir, o que as torna menos eficiente do que as variáveis locais, mas potencialmente mais eficientes do que `Shared` ou `Static` variáveis.</span><span class="sxs-lookup"><span data-stu-id="534ac-183">*Instance variables* consume memory while their instance continues to exist, which makes them less efficient than local variables, but potentially more efficient than `Shared` or `Static` variables.</span></span>

### <a name="minimizing-scope"></a><span data-ttu-id="534ac-184">Minimizando o escopo</span><span class="sxs-lookup"><span data-stu-id="534ac-184">Minimizing Scope</span></span>

<span data-ttu-id="534ac-185">Em geral, ao declarar qualquer variável ou constante, é uma boa prática de programação tornar o escopo o mais estreito possível (o escopo do bloco é o mais estreito).</span><span class="sxs-lookup"><span data-stu-id="534ac-185">In general, when declaring any variable or constant, it is good programming practice to make the scope as narrow as possible (block scope is the narrowest).</span></span> <span data-ttu-id="534ac-186">Isso ajuda a conservar a memória e minimiza as chances de seu código se referir erroneamente à variável errada.</span><span class="sxs-lookup"><span data-stu-id="534ac-186">This helps conserve memory and minimizes the chances of your code erroneously referring to the wrong variable.</span></span> <span data-ttu-id="534ac-187">Da mesma forma, você deve declarar uma variável para ser [estática](../../../language-reference/modifiers/static.md) somente quando for necessário preservar seu valor entre chamadas de procedimento.</span><span class="sxs-lookup"><span data-stu-id="534ac-187">Similarly, you should declare a variable to be [Static](../../../language-reference/modifiers/static.md) only when it is necessary to preserve its value between procedure calls.</span></span>

## <a name="see-also"></a><span data-ttu-id="534ac-188">Confira também</span><span class="sxs-lookup"><span data-stu-id="534ac-188">See also</span></span>

- [<span data-ttu-id="534ac-189">Características do Elemento Declarado</span><span class="sxs-lookup"><span data-stu-id="534ac-189">Declared Element Characteristics</span></span>](declared-element-characteristics.md)
- [<span data-ttu-id="534ac-190">Como controlar o escopo de uma variável</span><span class="sxs-lookup"><span data-stu-id="534ac-190">How to: Control the Scope of a Variable</span></span>](how-to-control-the-scope-of-a-variable.md)
- [<span data-ttu-id="534ac-191">Tempo de vida no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="534ac-191">Lifetime in Visual Basic</span></span>](lifetime.md)
- [<span data-ttu-id="534ac-192">Níveis de acesso no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="534ac-192">Access levels in Visual Basic</span></span>](access-levels.md)
- [<span data-ttu-id="534ac-193">Referências a elementos declarados</span><span class="sxs-lookup"><span data-stu-id="534ac-193">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="534ac-194">Declaração de Variável</span><span class="sxs-lookup"><span data-stu-id="534ac-194">Variable Declaration</span></span>](../variables/variable-declaration.md)
