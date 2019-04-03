---
title: Escopo no Visual Basic
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
ms.openlocfilehash: 6139af65958cefe43578f436204fa6836a71de0b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58823539"
---
# <a name="scope-in-visual-basic"></a><span data-ttu-id="5bc20-102">Escopo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5bc20-102">Scope in Visual Basic</span></span>
<span data-ttu-id="5bc20-103">O *escopo* de um elemento declarado é o conjunto de todo o código que pode fazer referência a ele sem qualificar seu nome ou tornando-os disponíveis por meio de uma [instrução Imports (tipo e Namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="5bc20-103">The *scope* of a declared element is the set of all code that can refer to it without qualifying its name or making it available through an [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span> <span data-ttu-id="5bc20-104">Um elemento pode ter escopo em um dos seguintes níveis:</span><span class="sxs-lookup"><span data-stu-id="5bc20-104">An element can have scope at one of the following levels:</span></span>  
  
|<span data-ttu-id="5bc20-105">Nível</span><span class="sxs-lookup"><span data-stu-id="5bc20-105">Level</span></span>|<span data-ttu-id="5bc20-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="5bc20-106">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5bc20-107">Escopo de bloco</span><span class="sxs-lookup"><span data-stu-id="5bc20-107">Block scope</span></span>|<span data-ttu-id="5bc20-108">Disponível somente dentro do código de bloco no qual ele é declarado</span><span class="sxs-lookup"><span data-stu-id="5bc20-108">Available only within the code block in which it is declared</span></span>|  
|<span data-ttu-id="5bc20-109">Escopo do procedimento</span><span class="sxs-lookup"><span data-stu-id="5bc20-109">Procedure scope</span></span>|<span data-ttu-id="5bc20-110">Disponível para todo o código dentro do procedimento no qual ela é declarada</span><span class="sxs-lookup"><span data-stu-id="5bc20-110">Available to all code within the procedure in which it is declared</span></span>|  
|<span data-ttu-id="5bc20-111">Escopo de módulo</span><span class="sxs-lookup"><span data-stu-id="5bc20-111">Module scope</span></span>|<span data-ttu-id="5bc20-112">Disponível para todo o código dentro do módulo, classe ou estrutura na qual ele está declarado</span><span class="sxs-lookup"><span data-stu-id="5bc20-112">Available to all code within the module, class, or structure in which it is declared</span></span>|  
|<span data-ttu-id="5bc20-113">Escopo de Namespace</span><span class="sxs-lookup"><span data-stu-id="5bc20-113">Namespace scope</span></span>|<span data-ttu-id="5bc20-114">Disponível para todo o código no namespace no qual ela é declarada</span><span class="sxs-lookup"><span data-stu-id="5bc20-114">Available to all code in the namespace in which it is declared</span></span>|  
  
 <span data-ttu-id="5bc20-115">Esses níveis de progresso de escopo de menor (bloco) para o mais amplo (namespace), onde *menor escopo* significa o menor conjunto de código que pode se referir ao elemento sem qualificação.</span><span class="sxs-lookup"><span data-stu-id="5bc20-115">These levels of scope progress from the narrowest (block) to the widest (namespace), where *narrowest scope* means the smallest set of code that can refer to the element without qualification.</span></span> <span data-ttu-id="5bc20-116">Para obter mais informações, consulte "Níveis de escopo" nesta página.</span><span class="sxs-lookup"><span data-stu-id="5bc20-116">For more information, see "Levels of Scope" on this page.</span></span>  
  
## <a name="specifying-scope-and-defining-variables"></a><span data-ttu-id="5bc20-117">Especificar o escopo e definir variáveis</span><span class="sxs-lookup"><span data-stu-id="5bc20-117">Specifying Scope and Defining Variables</span></span>  
 <span data-ttu-id="5bc20-118">Especifique o escopo de um elemento quando você declará-la.</span><span class="sxs-lookup"><span data-stu-id="5bc20-118">You specify the scope of an element when you declare it.</span></span> <span data-ttu-id="5bc20-119">O escopo pode depender dos seguintes fatores:</span><span class="sxs-lookup"><span data-stu-id="5bc20-119">The scope can depend on the following factors:</span></span>  
  
-   <span data-ttu-id="5bc20-120">A região (bloco, procedimento, módulo, classe ou estrutura) em que você declara o elemento</span><span class="sxs-lookup"><span data-stu-id="5bc20-120">The region (block, procedure, module, class, or structure) in which you declare the element</span></span>  
  
-   <span data-ttu-id="5bc20-121">O namespace que contém a declaração do elemento</span><span class="sxs-lookup"><span data-stu-id="5bc20-121">The namespace containing the element's declaration</span></span>  
  
-   <span data-ttu-id="5bc20-122">O nível de acesso que você declarar para o elemento</span><span class="sxs-lookup"><span data-stu-id="5bc20-122">The access level you declare for the element</span></span>  
  
 <span data-ttu-id="5bc20-123">Tenha cuidado ao definir variáveis com o mesmo nome mas com escopo diferente, porque isso pode levar a resultados inesperados.</span><span class="sxs-lookup"><span data-stu-id="5bc20-123">Use care when you define variables with the same name but different scope, because doing so can lead to unexpected results.</span></span> <span data-ttu-id="5bc20-124">Para obter mais informações, consulte [referências a elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="5bc20-124">For more information, see [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
## <a name="levels-of-scope"></a><span data-ttu-id="5bc20-125">Níveis de escopo</span><span class="sxs-lookup"><span data-stu-id="5bc20-125">Levels of Scope</span></span>  
 <span data-ttu-id="5bc20-126">Um elemento de programação está disponível em toda a região na qual você declará-la.</span><span class="sxs-lookup"><span data-stu-id="5bc20-126">A programming element is available throughout the region in which you declare it.</span></span> <span data-ttu-id="5bc20-127">Todo o código na mesma região pode se referir ao elemento sem qualificar seu nome.</span><span class="sxs-lookup"><span data-stu-id="5bc20-127">All code in the same region can refer to the element without qualifying its name.</span></span>  
  
### <a name="block-scope"></a><span data-ttu-id="5bc20-128">Escopo de bloco</span><span class="sxs-lookup"><span data-stu-id="5bc20-128">Block Scope</span></span>  
 <span data-ttu-id="5bc20-129">Um bloco é um conjunto de instruções entre Iniciando e encerrando instruções de declaração, como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="5bc20-129">A block is a set of statements enclosed within initiating and terminating declaration statements, such as the following:</span></span>  
  
-   <span data-ttu-id="5bc20-130">`Do` e `Loop`</span><span class="sxs-lookup"><span data-stu-id="5bc20-130">`Do` and `Loop`</span></span>  
  
-   <span data-ttu-id="5bc20-131">`For` [`Each`] e `Next`</span><span class="sxs-lookup"><span data-stu-id="5bc20-131">`For` [`Each`] and `Next`</span></span>  
  
-   <span data-ttu-id="5bc20-132">`If` e `End If`</span><span class="sxs-lookup"><span data-stu-id="5bc20-132">`If` and `End If`</span></span>  
  
-   <span data-ttu-id="5bc20-133">`Select` e `End Select`</span><span class="sxs-lookup"><span data-stu-id="5bc20-133">`Select` and `End Select`</span></span>  
  
-   <span data-ttu-id="5bc20-134">`SyncLock` e `End SyncLock`</span><span class="sxs-lookup"><span data-stu-id="5bc20-134">`SyncLock` and `End SyncLock`</span></span>  
  
-   <span data-ttu-id="5bc20-135">`Try` e `End Try`</span><span class="sxs-lookup"><span data-stu-id="5bc20-135">`Try` and `End Try`</span></span>  
  
-   <span data-ttu-id="5bc20-136">`While` e `End While`</span><span class="sxs-lookup"><span data-stu-id="5bc20-136">`While` and `End While`</span></span>  
  
-   <span data-ttu-id="5bc20-137">`With` e `End With`</span><span class="sxs-lookup"><span data-stu-id="5bc20-137">`With` and `End With`</span></span>  
  
 <span data-ttu-id="5bc20-138">Se você declarar uma variável dentro de um bloco, você pode usá-lo apenas dentro desse bloco.</span><span class="sxs-lookup"><span data-stu-id="5bc20-138">If you declare a variable within a block, you can use it only within that block.</span></span> <span data-ttu-id="5bc20-139">No exemplo a seguir, o escopo da variável de inteiro `cube` é o bloco entre `If` e `End If`, e você não pode consultar `cube` quando a execução passa para fora do bloco.</span><span class="sxs-lookup"><span data-stu-id="5bc20-139">In the following example, the scope of the integer variable `cube` is the block between `If` and `End If`, and you can no longer refer to `cube` when execution passes out of the block.</span></span>  
  
```  
If n < 1291 Then  
    Dim cube As Integer  
    cube = n ^ 3  
End If  
```  
  
> [!NOTE]
>  <span data-ttu-id="5bc20-140">Mesmo se o escopo de uma variável é limitado a um bloco, seu tempo de vida ainda é que todo o procedimento.</span><span class="sxs-lookup"><span data-stu-id="5bc20-140">Even if the scope of a variable is limited to a block, its lifetime is still that of the entire procedure.</span></span> <span data-ttu-id="5bc20-141">Se você inserir o bloco mais de uma vez durante o procedimento, cada variável de bloco reterá seu valor anterior.</span><span class="sxs-lookup"><span data-stu-id="5bc20-141">If you enter the block more than once during the procedure, each block variable retains its previous value.</span></span> <span data-ttu-id="5bc20-142">Para evitar resultados inesperados, nesse caso, é prudente inicializar variáveis de bloco no início do bloco.</span><span class="sxs-lookup"><span data-stu-id="5bc20-142">To avoid unexpected results in such a case, it is wise to initialize block variables at the beginning of the block.</span></span>  
  
### <a name="procedure-scope"></a><span data-ttu-id="5bc20-143">Escopo do procedimento</span><span class="sxs-lookup"><span data-stu-id="5bc20-143">Procedure Scope</span></span>  
 <span data-ttu-id="5bc20-144">Um elemento declarado dentro de um procedimento não está disponível fora desse procedimento.</span><span class="sxs-lookup"><span data-stu-id="5bc20-144">An element declared within a procedure is not available outside that procedure.</span></span> <span data-ttu-id="5bc20-145">Somente o procedimento que contém a declaração pode usá-lo.</span><span class="sxs-lookup"><span data-stu-id="5bc20-145">Only the procedure that contains the declaration can use it.</span></span> <span data-ttu-id="5bc20-146">Variáveis com esse nível também são conhecidos como *variáveis locais*.</span><span class="sxs-lookup"><span data-stu-id="5bc20-146">Variables at this level are also known as *local variables*.</span></span> <span data-ttu-id="5bc20-147">Você declará-las com o [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md), com ou sem o [estático](../../../../visual-basic/language-reference/modifiers/static.md) palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="5bc20-147">You declare them with the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md), with or without the [Static](../../../../visual-basic/language-reference/modifiers/static.md) keyword.</span></span>  
  
 <span data-ttu-id="5bc20-148">Escopo de procedimento e bloco estão intimamente relacionados.</span><span class="sxs-lookup"><span data-stu-id="5bc20-148">Procedure and block scope are closely related.</span></span> <span data-ttu-id="5bc20-149">Se você declarar uma variável dentro de um procedimento, mas fora de qualquer bloco dentro desse procedimento, você pode pensar a variável como tendo o escopo de bloco, onde o bloco é todo o procedimento.</span><span class="sxs-lookup"><span data-stu-id="5bc20-149">If you declare a variable inside a procedure but outside any block within that procedure, you can think of the variable as having block scope, where the block is the entire procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5bc20-150">Todos os elementos locais, mesmo se forem `Static` as variáveis são particulares ao procedimento em que aparecem.</span><span class="sxs-lookup"><span data-stu-id="5bc20-150">All local elements, even if they are `Static` variables, are private to the procedure in which they appear.</span></span> <span data-ttu-id="5bc20-151">Você não pode declarar qualquer elemento usando o [pública](../../../../visual-basic/language-reference/modifiers/public.md) palavra-chave dentro de um procedimento.</span><span class="sxs-lookup"><span data-stu-id="5bc20-151">You cannot declare any element using the [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword within a procedure.</span></span>  
  
### <a name="module-scope"></a><span data-ttu-id="5bc20-152">Escopo de módulo</span><span class="sxs-lookup"><span data-stu-id="5bc20-152">Module Scope</span></span>  
 <span data-ttu-id="5bc20-153">Para sua conveniência, o termo simples *nível de módulo* se aplica igualmente a módulos, classes e estruturas.</span><span class="sxs-lookup"><span data-stu-id="5bc20-153">For convenience, the single term *module level* applies equally to modules, classes, and structures.</span></span> <span data-ttu-id="5bc20-154">Você pode declarar elementos nesse nível, colocando a instrução de declaração fora de qualquer procedimento ou bloco, mas dentro do módulo, classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="5bc20-154">You can declare elements at this level by placing the declaration statement outside of any procedure or block but within the module, class, or structure.</span></span>  
  
 <span data-ttu-id="5bc20-155">Quando você fizer uma declaração no nível de módulo, o nível de acesso que você escolha determina o escopo.</span><span class="sxs-lookup"><span data-stu-id="5bc20-155">When you make a declaration at the module level, the access level you choose determines the scope.</span></span> <span data-ttu-id="5bc20-156">O namespace que contém o módulo, classe ou estrutura também afeta o escopo.</span><span class="sxs-lookup"><span data-stu-id="5bc20-156">The namespace that contains the module, class, or structure also affects the scope.</span></span>  
  
 <span data-ttu-id="5bc20-157">Os elementos para os quais você deve declarar [privada](../../../../visual-basic/language-reference/modifiers/private.md) nível de acesso estão disponíveis para cada procedimento desse módulo, mas não para qualquer código em um módulo diferente.</span><span class="sxs-lookup"><span data-stu-id="5bc20-157">Elements for which you declare [Private](../../../../visual-basic/language-reference/modifiers/private.md) access level are available to every procedure in that module, but not to any code in a different module.</span></span> <span data-ttu-id="5bc20-158">O `Dim` instrução no nível de módulo padrão é `Private` se você não usar quaisquer palavras-chave de nível de acesso.</span><span class="sxs-lookup"><span data-stu-id="5bc20-158">The `Dim` statement at module level defaults to `Private` if you do not use any access level keywords.</span></span> <span data-ttu-id="5bc20-159">No entanto, você pode fazer o nível de escopo e o acesso mais óbvio, usando o `Private` palavra-chave no `Dim` instrução.</span><span class="sxs-lookup"><span data-stu-id="5bc20-159">However, you can make the scope and access level more obvious by using the `Private` keyword in the `Dim` statement.</span></span>  
  
 <span data-ttu-id="5bc20-160">No exemplo a seguir, todos os procedimentos definidos no módulo podem se referir à variável de cadeia de caracteres `strMsg`.</span><span class="sxs-lookup"><span data-stu-id="5bc20-160">In the following example, all procedures defined in the module can refer to the string variable `strMsg`.</span></span> <span data-ttu-id="5bc20-161">Quando o segundo procedimento é chamado, ele exibe o conteúdo da variável de cadeia de caracteres `strMsg` em uma caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="5bc20-161">When the second procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.</span></span>  
  
```  
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
  
### <a name="namespace-scope"></a><span data-ttu-id="5bc20-162">Escopo de Namespace</span><span class="sxs-lookup"><span data-stu-id="5bc20-162">Namespace Scope</span></span>  
 <span data-ttu-id="5bc20-163">Se você declarar um elemento no nível de módulo usando o [amigo](../../../../visual-basic/language-reference/modifiers/friend.md) ou [público](../../../../visual-basic/language-reference/modifiers/public.md) palavra-chave, ele fica disponível para todos os procedimentos em todo o namespace no qual o elemento é declarado.</span><span class="sxs-lookup"><span data-stu-id="5bc20-163">If you declare an element at module level using the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) or [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword, it becomes available to all procedures throughout the namespace in which the element is declared.</span></span> <span data-ttu-id="5bc20-164">Com a seguinte alteração ao exemplo anterior, a variável de cadeia de caracteres `strMsg` pode ser chamada pelo código em qualquer lugar no namespace da sua declaração.</span><span class="sxs-lookup"><span data-stu-id="5bc20-164">With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.</span></span>  
  
```  
' Include this declaration at module level (not inside any procedure).  
Public strMsg As String  
```  
  
 <span data-ttu-id="5bc20-165">Escopo de Namespace inclui namespaces aninhados.</span><span class="sxs-lookup"><span data-stu-id="5bc20-165">Namespace scope includes nested namespaces.</span></span> <span data-ttu-id="5bc20-166">Um elemento disponível dentro de um namespace também está disponível de dentro de qualquer namespace aninhado dentro desse namespace.</span><span class="sxs-lookup"><span data-stu-id="5bc20-166">An element available from within a namespace is also available from within any namespace nested inside that namespace.</span></span>  
  
 <span data-ttu-id="5bc20-167">Se seu projeto não contém nenhum [declaração de Namespace](../../../../visual-basic/language-reference/statements/namespace-statement.md), tudo no projeto está no mesmo namespace.</span><span class="sxs-lookup"><span data-stu-id="5bc20-167">If your project does not contain any [Namespace Statement](../../../../visual-basic/language-reference/statements/namespace-statement.md)s, everything in the project is in the same namespace.</span></span> <span data-ttu-id="5bc20-168">Nesse caso, o escopo de namespace pode ser pensado como escopo do projeto.</span><span class="sxs-lookup"><span data-stu-id="5bc20-168">In this case, namespace scope can be thought of as project scope.</span></span> <span data-ttu-id="5bc20-169">`Public` elementos em um módulo, classe ou estrutura também estão disponíveis para qualquer projeto que referencia o seu projeto.</span><span class="sxs-lookup"><span data-stu-id="5bc20-169">`Public` elements in a module, class, or structure are also available to any project that references their project.</span></span>  
  
## <a name="choice-of-scope"></a><span data-ttu-id="5bc20-170">Opção de escopo</span><span class="sxs-lookup"><span data-stu-id="5bc20-170">Choice of Scope</span></span>  
 <span data-ttu-id="5bc20-171">Quando você declara uma variável, você deve manter em mente os seguintes pontos ao escolher seu escopo.</span><span class="sxs-lookup"><span data-stu-id="5bc20-171">When you declare a variable, you should keep in mind the following points when choosing its scope.</span></span>  
  
### <a name="advantages-of-local-variables"></a><span data-ttu-id="5bc20-172">Vantagens de variáveis locais</span><span class="sxs-lookup"><span data-stu-id="5bc20-172">Advantages of Local Variables</span></span>  
 <span data-ttu-id="5bc20-173">Variáveis locais são uma boa escolha para qualquer tipo de cálculo temporário, pelos seguintes motivos:</span><span class="sxs-lookup"><span data-stu-id="5bc20-173">Local variables are a good choice for any kind of temporary calculation, for the following reasons:</span></span>  
  
-   <span data-ttu-id="5bc20-174">**Prevenção de conflitos de nome.**</span><span class="sxs-lookup"><span data-stu-id="5bc20-174">**Name Conflict Avoidance.**</span></span> <span data-ttu-id="5bc20-175">Nomes de variável local não são suscetíveis a entrar em conflito.</span><span class="sxs-lookup"><span data-stu-id="5bc20-175">Local variable names are not susceptible to conflict.</span></span> <span data-ttu-id="5bc20-176">Por exemplo, você pode criar vários procedimentos diferentes que contém uma variável chamada `intTemp`.</span><span class="sxs-lookup"><span data-stu-id="5bc20-176">For example, you can create several different procedures containing a variable called `intTemp`.</span></span> <span data-ttu-id="5bc20-177">Desde que cada `intTemp` é declarado como uma variável local, cada procedimento reconhece apenas sua própria versão do `intTemp`.</span><span class="sxs-lookup"><span data-stu-id="5bc20-177">As long as each `intTemp` is declared as a local variable, each procedure recognizes only its own version of `intTemp`.</span></span> <span data-ttu-id="5bc20-178">Qualquer procedimento pode alterar o valor em seu local `intTemp` sem afetar `intTemp` variáveis em outros procedimentos.</span><span class="sxs-lookup"><span data-stu-id="5bc20-178">Any one procedure can alter the value in its local `intTemp` without affecting `intTemp` variables in other procedures.</span></span>  
  
-   <span data-ttu-id="5bc20-179">**Consumo de memória.**</span><span class="sxs-lookup"><span data-stu-id="5bc20-179">**Memory Consumption.**</span></span> <span data-ttu-id="5bc20-180">As variáveis locais consomem memória somente enquanto seu procedimento está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="5bc20-180">Local variables consume memory only while their procedure is running.</span></span> <span data-ttu-id="5bc20-181">Sua memória é liberada quando o procedimento retorna ao código de chamada.</span><span class="sxs-lookup"><span data-stu-id="5bc20-181">Their memory is released when the procedure returns to the calling code.</span></span> <span data-ttu-id="5bc20-182">Por outro lado, [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) e [estático](../../../../visual-basic/language-reference/modifiers/static.md) variáveis consomem recursos de memória até que seu aplicativo é interrompido, portanto, use-as quando necessário.</span><span class="sxs-lookup"><span data-stu-id="5bc20-182">By contrast, [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) and [Static](../../../../visual-basic/language-reference/modifiers/static.md) variables consume memory resources until your application stops running, so use them only when necessary.</span></span> <span data-ttu-id="5bc20-183">*Variáveis de instância* consomem memória enquanto sua instância continuará a existir, o que as torna menos eficiente do que as variáveis locais, mas potencialmente mais eficiente do que `Shared` ou `Static` variáveis.</span><span class="sxs-lookup"><span data-stu-id="5bc20-183">*Instance variables* consume memory while their instance continues to exist, which makes them less efficient than local variables, but potentially more efficient than `Shared` or `Static` variables.</span></span>  
  
### <a name="minimizing-scope"></a><span data-ttu-id="5bc20-184">Minimizando o escopo</span><span class="sxs-lookup"><span data-stu-id="5bc20-184">Minimizing Scope</span></span>  
 <span data-ttu-id="5bc20-185">Em geral, ao declarar qualquer variável ou constante, é boa prática para tornar o escopo tão restrito quanto possível (o escopo de bloco é o menor).</span><span class="sxs-lookup"><span data-stu-id="5bc20-185">In general, when declaring any variable or constant, it is good programming practice to make the scope as narrow as possible (block scope is the narrowest).</span></span> <span data-ttu-id="5bc20-186">Isso ajuda a conservar a memória e minimiza as chances de seu código erroneamente referir-se a variável errada.</span><span class="sxs-lookup"><span data-stu-id="5bc20-186">This helps conserve memory and minimizes the chances of your code erroneously referring to the wrong variable.</span></span> <span data-ttu-id="5bc20-187">Da mesma forma, você deve declarar uma variável para ser [estático](../../../../visual-basic/language-reference/modifiers/static.md) somente quando for necessário preservar seu valor entre chamadas de procedimento.</span><span class="sxs-lookup"><span data-stu-id="5bc20-187">Similarly, you should declare a variable to be [Static](../../../../visual-basic/language-reference/modifiers/static.md) only when it is necessary to preserve its value between procedure calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bc20-188">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5bc20-188">See also</span></span>

- [<span data-ttu-id="5bc20-189">Características do Elemento Declarado</span><span class="sxs-lookup"><span data-stu-id="5bc20-189">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="5bc20-190">Como: Controlar o escopo de uma variável</span><span class="sxs-lookup"><span data-stu-id="5bc20-190">How to: Control the Scope of a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)
- [<span data-ttu-id="5bc20-191">Tempo de vida no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5bc20-191">Lifetime in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="5bc20-192">Níveis de acesso no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5bc20-192">Access levels in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="5bc20-193">Referências a Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="5bc20-193">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="5bc20-194">Declaração de Variável</span><span class="sxs-lookup"><span data-stu-id="5bc20-194">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
