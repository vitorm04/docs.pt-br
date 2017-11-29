---
title: Compartilhado (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Shared
helpviewer_keywords:
- Shared keyword [Visual Basic]
- members [Visual Basic], shared
- shared members
- nonshared
- shared [elements VB]
- elements [Visual Basic], shared
ms.assetid: 2bf7cf2c-b0dd-485e-8749-b5d674dab4cd
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fce13c308a449e63eacc2bc4c94c274c7e25506a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="shared-visual-basic"></a><span data-ttu-id="5bfe3-102">Compartilhado (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5bfe3-102">Shared (Visual Basic)</span></span>
<span data-ttu-id="5bfe3-103">Especifica que um ou mais elementos de programação declarados estão associados com uma classe ou estrutura em geral e não com uma instância específica da classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="5bfe3-103">Specifies that one or more declared programming elements are associated with a class or structure at large, and not with a specific instance of the class or structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5bfe3-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="5bfe3-104">Remarks</span></span>  
  
## <a name="when-to-use-shared"></a><span data-ttu-id="5bfe3-105">Quando usar compartilhado</span><span class="sxs-lookup"><span data-stu-id="5bfe3-105">When to Use Shared</span></span>  
 <span data-ttu-id="5bfe3-106">Compartilhar um membro de uma classe ou estrutura torna disponível para cada instância, em vez de *não compartilhado*, onde cada instância tem sua própria cópia.</span><span class="sxs-lookup"><span data-stu-id="5bfe3-106">Sharing a member of a class or structure makes it available to every instance, rather than *nonshared*, where each instance keeps its own copy.</span></span> <span data-ttu-id="5bfe3-107">Isso é útil, por exemplo, se o valor de uma variável se aplica a todo o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5bfe3-107">This is useful, for example, if the value of a variable applies to the entire application.</span></span> <span data-ttu-id="5bfe3-108">Se você declarar essa variável como `Shared`, em seguida, todas as instâncias de acessam o mesmo local de armazenamento e se uma instância muda o valor da variável, todas as instâncias de acessam o valor atualizado.</span><span class="sxs-lookup"><span data-stu-id="5bfe3-108">If you declare that variable to be `Shared`, then all instances access the same storage location, and if one instance changes the variable's value, all instances access the updated value.</span></span>  
  
 <span data-ttu-id="5bfe3-109">Compartilhar não altera o nível de acesso de um membro.</span><span class="sxs-lookup"><span data-stu-id="5bfe3-109">Sharing does not alter the access level of a member.</span></span> <span data-ttu-id="5bfe3-110">Por exemplo, um membro da classe pode ser compartilhado e privado (acessível somente de dentro da classe), ou não compartilhado e público.</span><span class="sxs-lookup"><span data-stu-id="5bfe3-110">For example, a class member can be shared and private (accessible only from within the class), or nonshared and public.</span></span> <span data-ttu-id="5bfe3-111">Para obter mais informações, consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="5bfe3-111">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="5bfe3-112">Regras</span><span class="sxs-lookup"><span data-stu-id="5bfe3-112">Rules</span></span>  
  
-   <span data-ttu-id="5bfe3-113">**Contexto de declaração.**</span><span class="sxs-lookup"><span data-stu-id="5bfe3-113">**Declaration Context.**</span></span> <span data-ttu-id="5bfe3-114">Você pode usar `Shared` apenas no nível de módulo.</span><span class="sxs-lookup"><span data-stu-id="5bfe3-114">You can use `Shared` only at module level.</span></span> <span data-ttu-id="5bfe3-115">Isso significa que o contexto da declaração para um `Shared` elemento deve ser uma classe ou estrutura e não pode ser um arquivo de origem, namespace ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="5bfe3-115">This means the declaration context for a `Shared` element must be a class or structure, and cannot be a source file, namespace, or procedure.</span></span>  
  
-   <span data-ttu-id="5bfe3-116">**Modificadores combinados.**</span><span class="sxs-lookup"><span data-stu-id="5bfe3-116">**Combined Modifiers.**</span></span> <span data-ttu-id="5bfe3-117">Não é possível especificar `Shared` junto com [substitui](../../../visual-basic/language-reference/modifiers/overrides.md), [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md), ou [ Estático](../../../visual-basic/language-reference/modifiers/static.md) na mesma declaração.</span><span class="sxs-lookup"><span data-stu-id="5bfe3-117">You cannot specify `Shared` together with [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md), [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md), or [Static](../../../visual-basic/language-reference/modifiers/static.md) in the same declaration.</span></span>  
  
-   <span data-ttu-id="5bfe3-118">**Acessando.**</span><span class="sxs-lookup"><span data-stu-id="5bfe3-118">**Accessing.**</span></span> <span data-ttu-id="5bfe3-119">Você pode acessar um elemento compartilhado qualificando-o com seu nome de classe ou estrutura, não com o nome da variável de uma instância específica de sua classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="5bfe3-119">You access a shared element by qualifying it with its class or structure name, not with the variable name of a specific instance of its class or structure.</span></span> <span data-ttu-id="5bfe3-120">Até mesmo, você não precisa criar uma instância de uma classe ou estrutura para acessar seus membros compartilhados.</span><span class="sxs-lookup"><span data-stu-id="5bfe3-120">You do not even have to create an instance of a class or structure to access its shared members.</span></span>  
  
     <span data-ttu-id="5bfe3-121">O exemplo a seguir chama o procedimento compartilhado <xref:System.Double.IsNaN%2A> exposto pelo <xref:System.Double> estrutura.</span><span class="sxs-lookup"><span data-stu-id="5bfe3-121">The following example calls the shared procedure <xref:System.Double.IsNaN%2A> exposed by the <xref:System.Double> structure.</span></span>  
  
     `If Double.IsNaN(result) Then MsgBox("Result is mathematically undefined.")`  
  
-   <span data-ttu-id="5bfe3-122">**Compartilhamento implícito.**</span><span class="sxs-lookup"><span data-stu-id="5bfe3-122">**Implicit Sharing.**</span></span> <span data-ttu-id="5bfe3-123">Não é possível usar o `Shared` modificador em um [Declaração Const](../../../visual-basic/language-reference/statements/const-statement.md), mas constantes são implicitamente compartilhadas.</span><span class="sxs-lookup"><span data-stu-id="5bfe3-123">You cannot use the `Shared` modifier in a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md), but constants are implicitly shared.</span></span> <span data-ttu-id="5bfe3-124">Da mesma forma, você não pode declarar um membro de um módulo ou uma interface para ser `Shared`, mas eles são implicitamente compartilhados.</span><span class="sxs-lookup"><span data-stu-id="5bfe3-124">Similarly, you cannot declare a member of a module or an interface to be `Shared`, but they are implicitly shared.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="5bfe3-125">Comportamento</span><span class="sxs-lookup"><span data-stu-id="5bfe3-125">Behavior</span></span>  
  
-   <span data-ttu-id="5bfe3-126">**Armazenamento.**</span><span class="sxs-lookup"><span data-stu-id="5bfe3-126">**Storage.**</span></span> <span data-ttu-id="5bfe3-127">Uma variável compartilhada ou evento é armazenado na memória somente uma vez, não importa quantas vezes você criar de sua classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="5bfe3-127">A shared variable or event is stored in memory only once, no matter how many or few instances you create of its class or structure.</span></span> <span data-ttu-id="5bfe3-128">Da mesma forma, um procedimento compartilhado ou propriedade contém somente um conjunto de variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="5bfe3-128">Similarly, a shared procedure or property holds only one set of local variables.</span></span>  
  
-   <span data-ttu-id="5bfe3-129">**Acessando através de uma variável de instância.**</span><span class="sxs-lookup"><span data-stu-id="5bfe3-129">**Accessing through an Instance Variable.**</span></span> <span data-ttu-id="5bfe3-130">É possível acessar um elemento compartilhado qualificando-o com o nome de uma variável que contém uma instância específica de sua classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="5bfe3-130">It is possible to access a shared element by qualifying it with the name of a variable that contains a specific instance of its class or structure.</span></span> <span data-ttu-id="5bfe3-131">Embora isso geralmente funciona conforme o esperado, o compilador gera uma mensagem de aviso e faz o acesso através do nome de classe ou estrutura em vez da variável.</span><span class="sxs-lookup"><span data-stu-id="5bfe3-131">Although this usually works as expected, the compiler generates a warning message and makes the access through the class or structure name instead of the variable.</span></span>  
  
-   <span data-ttu-id="5bfe3-132">**Acessando através de uma expressão de instância.**</span><span class="sxs-lookup"><span data-stu-id="5bfe3-132">**Accessing through an Instance Expression.**</span></span> <span data-ttu-id="5bfe3-133">Se você acessar um elemento compartilhado através de uma expressão que retorna uma instância de sua classe ou estrutura, o compilador faz o acesso através do nome de classe ou estrutura em vez de avaliar a expressão.</span><span class="sxs-lookup"><span data-stu-id="5bfe3-133">If you access a shared element through an expression that returns an instance of its class or structure, the compiler makes the access through the class or structure name instead of evaluating the expression.</span></span> <span data-ttu-id="5bfe3-134">Isso produz resultados inesperados se você pretendia que a expressão para executar outras ações, bem como retornar a instância.</span><span class="sxs-lookup"><span data-stu-id="5bfe3-134">This produces unexpected results if you intended the expression to perform other actions as well as returning the instance.</span></span> <span data-ttu-id="5bfe3-135">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="5bfe3-135">The following example illustrates this.</span></span>  
  
    ```  
    Sub main()  
        shareTotal.total = 10  
        ' The preceding line is the preferred way to access total.  
        Dim instanceVar As New shareTotal  
        instanceVar.total += 100  
        ' The preceding line generates a compiler warning message and  
        ' accesses total through class shareTotal instead of through  
        ' the variable instanceVar. This works as expected and adds  
        ' 100 to total.  
        returnClass().total += 1000  
        ' The preceding line generates a compiler warning message and  
        ' accesses total through class shareTotal instead of calling  
        ' returnClass(). This adds 1000 to total but does not work as  
        ' expected, because the MsgBox in returnClass() does not run.  
        MsgBox("Value of total is " & CStr(shareTotal.total))  
    End Sub  
    Public Function returnClass() As shareTotal  
        MsgBox("Function returnClass() called")  
        Return New shareTotal  
    End Function  
    Public Class shareTotal  
        Public Shared total As Integer  
    End Class  
    ```  
  
     <span data-ttu-id="5bfe3-136">No exemplo anterior, o compilador gera uma mensagem de aviso nas duas vezes o código acessa a variável compartilhada `total` através de uma instância.</span><span class="sxs-lookup"><span data-stu-id="5bfe3-136">In the preceding example, the compiler generates a warning message both times the code accesses the shared variable `total` through an instance.</span></span> <span data-ttu-id="5bfe3-137">Em cada caso ele faz o acesso diretamente através da classe `shareTotal` e não faz uso de nenhuma instância.</span><span class="sxs-lookup"><span data-stu-id="5bfe3-137">In each case it makes the access directly through the class `shareTotal` and does not make use of any instance.</span></span> <span data-ttu-id="5bfe3-138">No caso da chamada pretendida ao procedimento `returnClass`, isso significa que ele nem gera uma chamada para `returnClass`, portanto, a ação adicional de mostrar "Function returnClass () chamado" não é executada.</span><span class="sxs-lookup"><span data-stu-id="5bfe3-138">In the case of the intended call to the procedure `returnClass`, this means it does not even generate a call to `returnClass`, so the additional action of displaying "Function returnClass() called" is not performed.</span></span>  
  
 <span data-ttu-id="5bfe3-139">O `Shared` modificador pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="5bfe3-139">The `Shared` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="5bfe3-140">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="5bfe3-140">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="5bfe3-141">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="5bfe3-141">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="5bfe3-142">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="5bfe3-142">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="5bfe3-143">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="5bfe3-143">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="5bfe3-144">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="5bfe3-144">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="5bfe3-145">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="5bfe3-145">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="5bfe3-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5bfe3-146">See Also</span></span>  
 [<span data-ttu-id="5bfe3-147">Sombras</span><span class="sxs-lookup"><span data-stu-id="5bfe3-147">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="5bfe3-148">Estático</span><span class="sxs-lookup"><span data-stu-id="5bfe3-148">Static</span></span>](../../../visual-basic/language-reference/modifiers/static.md)  
 [<span data-ttu-id="5bfe3-149">Tempo de vida no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5bfe3-149">Lifetime in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [<span data-ttu-id="5bfe3-150">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="5bfe3-150">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="5bfe3-151">Estruturas</span><span class="sxs-lookup"><span data-stu-id="5bfe3-151">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="5bfe3-152">Objetos e Classes</span><span class="sxs-lookup"><span data-stu-id="5bfe3-152">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
