---
title: Compartilhado
ms.date: 07/20/2015
f1_keywords:
- vb.Shared
helpviewer_keywords:
- Shared keyword [Visual Basic]
- members [Visual Basic], shared
- shared members
- nonshared
- shared [elements VB]
- elements [Visual Basic], shared
ms.assetid: 2bf7cf2c-b0dd-485e-8749-b5d674dab4cd
ms.openlocfilehash: d8c9879ea2f62bfbeaa378d0aaee806623ea1c55
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579106"
---
# <a name="shared-visual-basic"></a><span data-ttu-id="f83da-102">Compartilhado (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f83da-102">Shared (Visual Basic)</span></span>

<span data-ttu-id="f83da-103">Especifica que um ou mais elementos de programação declarados estão associados a uma classe ou estrutura em tamanho grande, e não com uma instância específica da classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="f83da-103">Specifies that one or more declared programming elements are associated with a class or structure at large, and not with a specific instance of the class or structure.</span></span>

## <a name="when-to-use-shared"></a><span data-ttu-id="f83da-104">Quando usar compartilhado</span><span class="sxs-lookup"><span data-stu-id="f83da-104">When to Use Shared</span></span>

<span data-ttu-id="f83da-105">O compartilhamento de um membro de uma classe ou estrutura torna-o disponível para cada instância, em vez de *não compartilhado*, em que cada instância mantém sua própria cópia.</span><span class="sxs-lookup"><span data-stu-id="f83da-105">Sharing a member of a class or structure makes it available to every instance, rather than *non-shared*, where each instance keeps its own copy.</span></span> <span data-ttu-id="f83da-106">Isso é útil, por exemplo, se o valor de uma variável se aplicar a todo o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f83da-106">This is useful, for example, if the value of a variable applies to the entire application.</span></span> <span data-ttu-id="f83da-107">Se você declarar essa variável como sendo `Shared` , todas as instâncias acessarão o mesmo local de armazenamento e, se uma instância alterar o valor da variável, todas as instâncias acessarão o valor atualizado.</span><span class="sxs-lookup"><span data-stu-id="f83da-107">If you declare that variable to be `Shared`, then all instances access the same storage location, and if one instance changes the variable's value, all instances access the updated value.</span></span>

<span data-ttu-id="f83da-108">O compartilhamento não altera o nível de acesso de um membro.</span><span class="sxs-lookup"><span data-stu-id="f83da-108">Sharing does not alter the access level of a member.</span></span> <span data-ttu-id="f83da-109">Por exemplo, um membro de classe pode ser compartilhado e privado (acessível somente de dentro da classe), ou não compartilhado e público.</span><span class="sxs-lookup"><span data-stu-id="f83da-109">For example, a class member can be shared and private (accessible only from within the class), or non-shared and public.</span></span> <span data-ttu-id="f83da-110">Para obter mais informações, consulte [níveis de acesso em Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="f83da-110">For more information, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

## <a name="rules"></a><span data-ttu-id="f83da-111">Regras</span><span class="sxs-lookup"><span data-stu-id="f83da-111">Rules</span></span>

- <span data-ttu-id="f83da-112">**Contexto de declaração.**</span><span class="sxs-lookup"><span data-stu-id="f83da-112">**Declaration Context.**</span></span> <span data-ttu-id="f83da-113">Você pode usar `Shared` somente no nível do módulo.</span><span class="sxs-lookup"><span data-stu-id="f83da-113">You can use `Shared` only at module level.</span></span> <span data-ttu-id="f83da-114">Isso significa que o contexto de declaração de um `Shared` elemento deve ser uma classe ou estrutura e não pode ser um arquivo de origem, namespace ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="f83da-114">This means the declaration context for a `Shared` element must be a class or structure, and cannot be a source file, namespace, or procedure.</span></span>

- <span data-ttu-id="f83da-115">**Modificadores combinados.**</span><span class="sxs-lookup"><span data-stu-id="f83da-115">**Combined Modifiers.**</span></span> <span data-ttu-id="f83da-116">Você não pode especificar `Shared` junto com [Overrides](overrides.md), [Overridable, NotOverridable](overridable.md), [MustOverride](mustoverride.md)ou [static](static.md) na mesma declaração. [NotOverridable](notoverridable.md)</span><span class="sxs-lookup"><span data-stu-id="f83da-116">You cannot specify `Shared` together with [Overrides](overrides.md), [Overridable](overridable.md), [NotOverridable](notoverridable.md), [MustOverride](mustoverride.md), or [Static](static.md) in the same declaration.</span></span>

- <span data-ttu-id="f83da-117">**Acess.**</span><span class="sxs-lookup"><span data-stu-id="f83da-117">**Accessing.**</span></span> <span data-ttu-id="f83da-118">Você acessa um elemento compartilhado qualificando-o com seu nome de classe ou estrutura, não com o nome da variável de uma instância específica de sua classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="f83da-118">You access a shared element by qualifying it with its class or structure name, not with the variable name of a specific instance of its class or structure.</span></span> <span data-ttu-id="f83da-119">Você não precisa nem criar uma instância de uma classe ou estrutura para acessar seus membros compartilhados.</span><span class="sxs-lookup"><span data-stu-id="f83da-119">You do not even have to create an instance of a class or structure to access its shared members.</span></span>

     <span data-ttu-id="f83da-120">O exemplo a seguir chama o procedimento compartilhado <xref:System.Double.IsNaN%2A> exposto pela <xref:System.Double> estrutura.</span><span class="sxs-lookup"><span data-stu-id="f83da-120">The following example calls the shared procedure <xref:System.Double.IsNaN%2A> exposed by the <xref:System.Double> structure.</span></span>

     ```vb
     If Double.IsNaN(result) Then Console.WriteLine("Result is mathematically undefined.")
     ```

- <span data-ttu-id="f83da-121">**Compartilhamento implícito.**</span><span class="sxs-lookup"><span data-stu-id="f83da-121">**Implicit Sharing.**</span></span> <span data-ttu-id="f83da-122">Você não pode usar o `Shared` modificador em uma [instrução const](../statements/const-statement.md), mas as constantes são compartilhadas implicitamente.</span><span class="sxs-lookup"><span data-stu-id="f83da-122">You cannot use the `Shared` modifier in a [Const Statement](../statements/const-statement.md), but constants are implicitly shared.</span></span> <span data-ttu-id="f83da-123">Da mesma forma, você não pode declarar um membro de um módulo ou uma interface para ser `Shared` , mas eles são compartilhados implicitamente.</span><span class="sxs-lookup"><span data-stu-id="f83da-123">Similarly, you cannot declare a member of a module or an interface to be `Shared`, but they are implicitly shared.</span></span>

## <a name="behavior"></a><span data-ttu-id="f83da-124">Comportamento</span><span class="sxs-lookup"><span data-stu-id="f83da-124">Behavior</span></span>

- <span data-ttu-id="f83da-125">**Repositório.**</span><span class="sxs-lookup"><span data-stu-id="f83da-125">**Storage.**</span></span> <span data-ttu-id="f83da-126">Uma variável ou evento compartilhado é armazenado na memória apenas uma vez, independentemente de quantas instâncias você criar de sua classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="f83da-126">A shared variable or event is stored in memory only once, no matter how many or few instances you create of its class or structure.</span></span> <span data-ttu-id="f83da-127">Da mesma forma, um procedimento compartilhado ou propriedade mantém apenas um conjunto de variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="f83da-127">Similarly, a shared procedure or property holds only one set of local variables.</span></span>

- <span data-ttu-id="f83da-128">**Acessando por meio de uma variável de instância.**</span><span class="sxs-lookup"><span data-stu-id="f83da-128">**Accessing through an Instance Variable.**</span></span> <span data-ttu-id="f83da-129">É possível acessar um elemento compartilhado qualificando-o com o nome de uma variável que contém uma instância específica de sua classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="f83da-129">It is possible to access a shared element by qualifying it with the name of a variable that contains a specific instance of its class or structure.</span></span> <span data-ttu-id="f83da-130">Embora isso normalmente funcione conforme o esperado, o compilador gera uma mensagem de aviso e faz o acesso por meio do nome da classe ou da estrutura em vez da variável.</span><span class="sxs-lookup"><span data-stu-id="f83da-130">Although this usually works as expected, the compiler generates a warning message and makes the access through the class or structure name instead of the variable.</span></span>

- <span data-ttu-id="f83da-131">**Acessando por meio de uma expressão de instância.**</span><span class="sxs-lookup"><span data-stu-id="f83da-131">**Accessing through an Instance Expression.**</span></span> <span data-ttu-id="f83da-132">Se você acessar um elemento compartilhado por meio de uma expressão que retorna uma instância de sua classe ou estrutura, o compilador fará o acesso por meio do nome da classe ou da estrutura em vez de avaliar a expressão.</span><span class="sxs-lookup"><span data-stu-id="f83da-132">If you access a shared element through an expression that returns an instance of its class or structure, the compiler makes the access through the class or structure name instead of evaluating the expression.</span></span> <span data-ttu-id="f83da-133">Isso produzirá resultados inesperados se você pretende que a expressão execute outras ações, bem como o retorno da instância.</span><span class="sxs-lookup"><span data-stu-id="f83da-133">This produces unexpected results if you intended the expression to perform other actions as well as returning the instance.</span></span> <span data-ttu-id="f83da-134">O exemplo a seguir ilustra isto.</span><span class="sxs-lookup"><span data-stu-id="f83da-134">The following example illustrates this.</span></span>
  
    ```vb
    Sub Main()
        ' The following line is the preferred way to access Total.
        ShareTotal.Total = 10

        ' The following line generates a compiler warning message and
        ' accesses total through class ShareTotal instead of through
        ' the variable instanceVar. This works as expected and adds
        ' 100 to Total.
        Dim instanceVar As New ShareTotal
        instanceVar.Total += 100

        ' The following line generates a compiler warning message and
        ' accesses total through class ShareTotal instead of calling
        ' ReturnClass(). This adds 1000 to total but does not work as
        ' expected, because the WriteLine in ReturnClass() does not run.
        Console.WriteLine("Value of total is " & CStr(ShareTotal.Total))
        ReturnClass().Total += 1000
    End Sub

    Public Function ReturnClass() As ShareTotal
        Console.WriteLine("Function ReturnClass() called")
        Return New ShareTotal
    End Function

    Public Class ShareTotal
        Public Shared Property Total As Integer
    End Class
    ```

     <span data-ttu-id="f83da-135">No exemplo anterior, o compilador gera uma mensagem de aviso duas vezes o código acessa a propriedade compartilhada `Total` por meio de uma instância.</span><span class="sxs-lookup"><span data-stu-id="f83da-135">In the preceding example, the compiler generates a warning message both times the code accesses the shared property `Total` through an instance.</span></span> <span data-ttu-id="f83da-136">Em cada caso, ele faz o acesso diretamente por meio da classe `ShareTotal` e não faz uso de nenhuma instância.</span><span class="sxs-lookup"><span data-stu-id="f83da-136">In each case it makes the access directly through the class `ShareTotal` and does not make use of any instance.</span></span> <span data-ttu-id="f83da-137">No caso da chamada pretendida para o procedimento `ReturnClass` , isso significa que ele não gera uma chamada para `ReturnClass` , portanto, a ação adicional de exibir "função ReturnClass () chamada" não é executada.</span><span class="sxs-lookup"><span data-stu-id="f83da-137">In the case of the intended call to the procedure `ReturnClass`, this means it does not even generate a call to `ReturnClass`, so the additional action of displaying "Function ReturnClass() called" is not performed.</span></span>

<span data-ttu-id="f83da-138">O `Shared` modificador pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="f83da-138">The `Shared` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="f83da-139">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="f83da-139">Dim Statement</span></span>](../statements/dim-statement.md)
- [<span data-ttu-id="f83da-140">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="f83da-140">Event Statement</span></span>](../statements/event-statement.md)
- [<span data-ttu-id="f83da-141">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="f83da-141">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="f83da-142">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="f83da-142">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="f83da-143">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="f83da-143">Property Statement</span></span>](../statements/property-statement.md)
- [<span data-ttu-id="f83da-144">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="f83da-144">Sub Statement</span></span>](../statements/sub-statement.md)
  
## <a name="see-also"></a><span data-ttu-id="f83da-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f83da-145">See also</span></span>

- [<span data-ttu-id="f83da-146">Sombras</span><span class="sxs-lookup"><span data-stu-id="f83da-146">Shadows</span></span>](shadows.md)
- [<span data-ttu-id="f83da-147">Estático</span><span class="sxs-lookup"><span data-stu-id="f83da-147">Static</span></span>](static.md)
- [<span data-ttu-id="f83da-148">Tempo de vida no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f83da-148">Lifetime in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="f83da-149">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="f83da-149">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="f83da-150">Estruturas</span><span class="sxs-lookup"><span data-stu-id="f83da-150">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="f83da-151">Objetos e classes</span><span class="sxs-lookup"><span data-stu-id="f83da-151">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
