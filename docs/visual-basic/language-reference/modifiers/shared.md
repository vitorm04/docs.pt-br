---
title: Compartilhado (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Shared
dev_langs:
- VB
helpviewer_keywords:
- Shared keyword
- members, shared
- shared members
- nonshared
- shared elements
- elements, shared
ms.assetid: 2bf7cf2c-b0dd-485e-8749-b5d674dab4cd
caps.latest.revision: 16
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
ms.openlocfilehash: ba3a33e8c652f0e02eb5705b69ba4d5c828a809f
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="shared-visual-basic"></a><span data-ttu-id="5fc9e-102">Compartilhado (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5fc9e-102">Shared (Visual Basic)</span></span>
<span data-ttu-id="5fc9e-103">Especifica que um ou mais elementos de programação declarados estão associados com uma classe ou estrutura em geral e não com uma instância específica da classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-103">Specifies that one or more declared programming elements are associated with a class or structure at large, and not with a specific instance of the class or structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5fc9e-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="5fc9e-104">Remarks</span></span>  
  
## <a name="when-to-use-shared"></a><span data-ttu-id="5fc9e-105">Para usar compartilhamento</span><span class="sxs-lookup"><span data-stu-id="5fc9e-105">When to Use Shared</span></span>  
 <span data-ttu-id="5fc9e-106">Compartilhar um membro de uma classe ou estrutura torna disponível para cada instância, em vez de *compartilhados*, onde cada instância tem sua própria cópia.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-106">Sharing a member of a class or structure makes it available to every instance, rather than *nonshared*, where each instance keeps its own copy.</span></span> <span data-ttu-id="5fc9e-107">Isso é útil, por exemplo, se o valor de uma variável se aplica a todo o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-107">This is useful, for example, if the value of a variable applies to the entire application.</span></span> <span data-ttu-id="5fc9e-108">Se você declarar essa variável como `Shared`, em seguida, todas as instâncias acessam o mesmo local de armazenamento e se uma instância muda o valor da variável, todas instâncias acessam o valor atualizado.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-108">If you declare that variable to be `Shared`, then all instances access the same storage location, and if one instance changes the variable's value, all instances access the updated value.</span></span>  
  
 <span data-ttu-id="5fc9e-109">Compartilhar não altera o nível de acesso de um membro.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-109">Sharing does not alter the access level of a member.</span></span> <span data-ttu-id="5fc9e-110">Por exemplo, um membro da classe pode ser compartilhado e privado (acessível somente de dentro da classe), ou não compartilhado e público.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-110">For example, a class member can be shared and private (accessible only from within the class), or nonshared and public.</span></span> <span data-ttu-id="5fc9e-111">Para obter mais informações, consulte [níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="5fc9e-111">For more information, see [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="5fc9e-112">Regras</span><span class="sxs-lookup"><span data-stu-id="5fc9e-112">Rules</span></span>  
  
-   <span data-ttu-id="5fc9e-113">**Contexto de declaração.**</span><span class="sxs-lookup"><span data-stu-id="5fc9e-113">**Declaration Context.**</span></span> <span data-ttu-id="5fc9e-114">Você pode usar `Shared` somente no nível de módulo.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-114">You can use `Shared` only at module level.</span></span> <span data-ttu-id="5fc9e-115">Isso significa que o contexto da declaração para um `Shared` elemento deve ser uma classe ou estrutura e não pode ser um arquivo fonte, namespace ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-115">This means the declaration context for a `Shared` element must be a class or structure, and cannot be a source file, namespace, or procedure.</span></span>  
  
-   <span data-ttu-id="5fc9e-116">**Modificadores combinados.**</span><span class="sxs-lookup"><span data-stu-id="5fc9e-116">**Combined Modifiers.**</span></span> <span data-ttu-id="5fc9e-117">Não é possível especificar `Shared` junto com [substituições](../../../visual-basic/language-reference/modifiers/overrides.md), [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md), ou [estático](../../../visual-basic/language-reference/modifiers/static.md) na mesma declaração.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-117">You cannot specify `Shared` together with [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md), [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md), or [Static](../../../visual-basic/language-reference/modifiers/static.md) in the same declaration.</span></span>  
  
-   <span data-ttu-id="5fc9e-118">**Acessando.**</span><span class="sxs-lookup"><span data-stu-id="5fc9e-118">**Accessing.**</span></span> <span data-ttu-id="5fc9e-119">Você pode acessar um elemento compartilhado qualificando-o com seu nome de classe ou estrutura, não com o nome da variável de uma instância específica de sua classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-119">You access a shared element by qualifying it with its class or structure name, not with the variable name of a specific instance of its class or structure.</span></span> <span data-ttu-id="5fc9e-120">Até mesmo, você não precisa criar uma instância de uma classe ou estrutura para acessar seus membros compartilhados.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-120">You do not even have to create an instance of a class or structure to access its shared members.</span></span>  
  
     <span data-ttu-id="5fc9e-121">O exemplo a seguir chama o procedimento compartilhado <xref:System.Double.IsNaN%2A>exposto pelo <xref:System.Double>estrutura.</xref:System.Double> </xref:System.Double.IsNaN%2A></span><span class="sxs-lookup"><span data-stu-id="5fc9e-121">The following example calls the shared procedure <xref:System.Double.IsNaN%2A> exposed by the <xref:System.Double> structure.</span></span>  
  
     `If Double.IsNaN(result) Then MsgBox("Result is mathematically undefined.")`  
  
-   <span data-ttu-id="5fc9e-122">**Compartilhamento implícito.**</span><span class="sxs-lookup"><span data-stu-id="5fc9e-122">**Implicit Sharing.**</span></span> <span data-ttu-id="5fc9e-123">Não é possível usar o `Shared` modificador em um [instrução Const](../../../visual-basic/language-reference/statements/const-statement.md), mas constantes são implicitamente compartilhadas.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-123">You cannot use the `Shared` modifier in a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md), but constants are implicitly shared.</span></span> <span data-ttu-id="5fc9e-124">Da mesma forma, você não pode declarar um membro de um módulo ou interface como `Shared`, mas eles são implicitamente compartilhados.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-124">Similarly, you cannot declare a member of a module or an interface to be `Shared`, but they are implicitly shared.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="5fc9e-125">Comportamento</span><span class="sxs-lookup"><span data-stu-id="5fc9e-125">Behavior</span></span>  
  
-   <span data-ttu-id="5fc9e-126">**Armazenamento.**</span><span class="sxs-lookup"><span data-stu-id="5fc9e-126">**Storage.**</span></span> <span data-ttu-id="5fc9e-127">Uma variável compartilhada ou evento é armazenado na memória somente uma vez, não importa quantas vezes você criar de sua classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-127">A shared variable or event is stored in memory only once, no matter how many or few instances you create of its class or structure.</span></span> <span data-ttu-id="5fc9e-128">Da mesma forma, um procedimento compartilhado ou propriedade contém somente um conjunto de variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-128">Similarly, a shared procedure or property holds only one set of local variables.</span></span>  
  
-   <span data-ttu-id="5fc9e-129">**Acessando através de uma variável de instância.**</span><span class="sxs-lookup"><span data-stu-id="5fc9e-129">**Accessing through an Instance Variable.**</span></span> <span data-ttu-id="5fc9e-130">É possível acessar um elemento compartilhado qualificando-o com o nome de uma variável que contém uma instância específica de sua classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-130">It is possible to access a shared element by qualifying it with the name of a variable that contains a specific instance of its class or structure.</span></span> <span data-ttu-id="5fc9e-131">Embora isso geralmente funciona conforme o esperado, o compilador gera uma mensagem de aviso e faz o acesso através do nome da classe ou estrutura em vez da variável.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-131">Although this usually works as expected, the compiler generates a warning message and makes the access through the class or structure name instead of the variable.</span></span>  
  
-   <span data-ttu-id="5fc9e-132">**Acessando através de uma expressão de instância.**</span><span class="sxs-lookup"><span data-stu-id="5fc9e-132">**Accessing through an Instance Expression.**</span></span> <span data-ttu-id="5fc9e-133">Se você acessar um elemento compartilhado através de uma expressão que retorna uma instância de sua classe ou estrutura, o compilador faz o acesso através do nome da classe ou estrutura em vez de avaliar a expressão.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-133">If you access a shared element through an expression that returns an instance of its class or structure, the compiler makes the access through the class or structure name instead of evaluating the expression.</span></span> <span data-ttu-id="5fc9e-134">Isso produz resultados inesperados se você pretendia que a expressão para executar outras ações, bem como retornar a instância.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-134">This produces unexpected results if you intended the expression to perform other actions as well as returning the instance.</span></span> <span data-ttu-id="5fc9e-135">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-135">The following example illustrates this.</span></span>  
  
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
  
     <span data-ttu-id="5fc9e-136">No exemplo anterior, o compilador gera uma mensagem de aviso nas duas vezes que o código acessa a variável compartilhada `total` através de uma instância.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-136">In the preceding example, the compiler generates a warning message both times the code accesses the shared variable `total` through an instance.</span></span> <span data-ttu-id="5fc9e-137">Em cada caso ele faz o acesso diretamente através da classe `shareTotal` e não faz uso de nenhuma instância.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-137">In each case it makes the access directly through the class `shareTotal` and does not make use of any instance.</span></span> <span data-ttu-id="5fc9e-138">No caso da chamada pretendida ao procedimento `returnClass`, isso significa que ele nem gera uma chamada para `returnClass`, portanto, a ação adicional de mostrar "Function returnClass () chamado" não é executada.</span><span class="sxs-lookup"><span data-stu-id="5fc9e-138">In the case of the intended call to the procedure `returnClass`, this means it does not even generate a call to `returnClass`, so the additional action of displaying "Function returnClass() called" is not performed.</span></span>  
  
 <span data-ttu-id="5fc9e-139">O `Shared` modificador pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="5fc9e-139">The `Shared` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="5fc9e-140">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="5fc9e-140">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="5fc9e-141">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="5fc9e-141">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="5fc9e-142">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="5fc9e-142">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="5fc9e-143">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="5fc9e-143">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="5fc9e-144">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="5fc9e-144">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="5fc9e-145">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="5fc9e-145">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="5fc9e-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5fc9e-146">See Also</span></span>  
 <span data-ttu-id="5fc9e-147">[Sombras](../../../visual-basic/language-reference/modifiers/shadows.md) </span><span class="sxs-lookup"><span data-stu-id="5fc9e-147">[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) </span></span>  
<span data-ttu-id="5fc9e-148"> [Estático](../../../visual-basic/language-reference/modifiers/static.md) </span><span class="sxs-lookup"><span data-stu-id="5fc9e-148"> [Static](../../../visual-basic/language-reference/modifiers/static.md) </span></span>  
<span data-ttu-id="5fc9e-149"> [Tempo de vida no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md) </span><span class="sxs-lookup"><span data-stu-id="5fc9e-149"> [Lifetime in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md) </span></span>  
<span data-ttu-id="5fc9e-150"> [Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/index.md) </span><span class="sxs-lookup"><span data-stu-id="5fc9e-150"> [Procedures](../../../visual-basic/programming-guide/language-features/procedures/index.md) </span></span>  
<span data-ttu-id="5fc9e-151"> [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span><span class="sxs-lookup"><span data-stu-id="5fc9e-151"> [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span></span>  
<span data-ttu-id="5fc9e-152"> [Objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)</span><span class="sxs-lookup"><span data-stu-id="5fc9e-152"> [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)</span></span>
