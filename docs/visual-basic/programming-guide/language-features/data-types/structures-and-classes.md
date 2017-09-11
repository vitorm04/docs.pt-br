---
title: Estruturas e Classes (Visual Basic) | Documentos do Microsoft
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
- classes [Visual Basic], vs. structures
- structures
- classes [Visual Basic]
- structures, compared to classes
- structures, structure variables
- structure variables
ms.assetid: a221e74a-ffcf-4bdc-a0f6-a088a9bf26cc
caps.latest.revision: 21
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
ms.openlocfilehash: c6874192a09db9ff5f247274247630d0bfa05ea3
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="structures-and-classes-visual-basic"></a><span data-ttu-id="17941-102">Estruturas e classes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="17941-102">Structures and Classes (Visual Basic)</span></span>
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="17941-103">unifica a sintaxe para estruturas e classes, com o resultado que ambas as entidades suportam a maioria dos mesmos recursos.</span><span class="sxs-lookup"><span data-stu-id="17941-103"> unifies the syntax for structures and classes, with the result that both entities support most of the same features.</span></span> <span data-ttu-id="17941-104">No entanto, também existem diferenças importantes entre as estruturas e classes.</span><span class="sxs-lookup"><span data-stu-id="17941-104">However, there are also important differences between structures and classes.</span></span>  
  
 <span data-ttu-id="17941-105">Classes têm a vantagem de ser tipos de referência — passar uma referência é mais eficiente do que passar uma variável de estrutura com todos os seus dados.</span><span class="sxs-lookup"><span data-stu-id="17941-105">Classes have the advantage of being reference types — passing a reference is more efficient than passing a structure variable with all its data.</span></span> <span data-ttu-id="17941-106">Por outro lado, as estruturas não requerem alocação de memória na pilha global.</span><span class="sxs-lookup"><span data-stu-id="17941-106">On the other hand, structures do not require allocation of memory on the global heap.</span></span>  
  
 <span data-ttu-id="17941-107">Como você não pode herdar de uma estrutura, estruturas devem ser usadas apenas para objetos que não precisam ser estendido.</span><span class="sxs-lookup"><span data-stu-id="17941-107">Because you cannot inherit from a structure, structures should be used only for objects that do not need to be extended.</span></span> <span data-ttu-id="17941-108">Use estruturas quando o objeto que você deseja criar tem uma instância de tamanho pequeno e levar em conta as características de desempenho de classes versus estruturas.</span><span class="sxs-lookup"><span data-stu-id="17941-108">Use structures when the object you wish to create has a small instance size, and take into account the performance characteristics of classes versus structures.</span></span>  
  
## <a name="similarities"></a><span data-ttu-id="17941-109">Semelhanças</span><span class="sxs-lookup"><span data-stu-id="17941-109">Similarities</span></span>  
 <span data-ttu-id="17941-110">Estruturas e classes são semelhantes nos seguintes aspectos:</span><span class="sxs-lookup"><span data-stu-id="17941-110">Structures and classes are similar in the following respects:</span></span>  
  
-   <span data-ttu-id="17941-111">Ambos são *contêiner* tipos, o que significa que elas contêm outros tipos como membros.</span><span class="sxs-lookup"><span data-stu-id="17941-111">Both are *container* types, meaning that they contain other types as members.</span></span>  
  
-   <span data-ttu-id="17941-112">Ambas ter membros, que podem incluir construtores, métodos, propriedades, campos, constantes, enumerações, eventos e manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="17941-112">Both have members, which can include constructors, methods, properties, fields, constants, enumerations, events, and event handlers.</span></span> <span data-ttu-id="17941-113">No entanto, não confunda esses membros com o declarados *elementos* de uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="17941-113">However, do not confuse these members with the declared *elements* of a structure.</span></span>  
  
-   <span data-ttu-id="17941-114">Membros de ambas podem ter níveis de acesso individualizados.</span><span class="sxs-lookup"><span data-stu-id="17941-114">Members of both can have individualized access levels.</span></span> <span data-ttu-id="17941-115">Por exemplo, um membro pode ser declarado `Public` e outro `Private`.</span><span class="sxs-lookup"><span data-stu-id="17941-115">For example, one member can be declared `Public` and another `Private`.</span></span>  
  
-   <span data-ttu-id="17941-116">Ambas podem implementar interfaces.</span><span class="sxs-lookup"><span data-stu-id="17941-116">Both can implement interfaces.</span></span>  
  
-   <span data-ttu-id="17941-117">Ambos podem ter construtores compartilhados, com ou sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="17941-117">Both can have shared constructors, with or without parameters.</span></span>  
  
-   <span data-ttu-id="17941-118">Ambos podem expor uma *propriedade padrão*, desde que a propriedade aceite pelo menos um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="17941-118">Both can expose a *default property*, provided that property takes at least one parameter.</span></span>  
  
-   <span data-ttu-id="17941-119">Ambas podem declarar e disparar eventos, e ambas podem declarar representantes.</span><span class="sxs-lookup"><span data-stu-id="17941-119">Both can declare and raise events, and both can declare delegates.</span></span>  
  
## <a name="differences"></a><span data-ttu-id="17941-120">Diferenças</span><span class="sxs-lookup"><span data-stu-id="17941-120">Differences</span></span>  
 <span data-ttu-id="17941-121">Estruturas e classes diferem nas particularidades a seguir:</span><span class="sxs-lookup"><span data-stu-id="17941-121">Structures and classes differ in the following particulars:</span></span>  
  
-   <span data-ttu-id="17941-122">Estruturas são *tipos de valor*; são classes *tipos de referência*.</span><span class="sxs-lookup"><span data-stu-id="17941-122">Structures are *value types*; classes are *reference types*.</span></span> <span data-ttu-id="17941-123">Uma variável de um tipo de estrutura contém dados a estrutura dos, em vez que contendo uma referência para os dados como um tipo de classe.</span><span class="sxs-lookup"><span data-stu-id="17941-123">A variable of a structure type contains the structure's data, rather than containing a reference to the data as a class type does.</span></span>  
  
-   <span data-ttu-id="17941-124">Estruturas usam alocação da pilha; classes usam alocação de heap.</span><span class="sxs-lookup"><span data-stu-id="17941-124">Structures use stack allocation; classes use heap allocation.</span></span>  
  
-   <span data-ttu-id="17941-125">Todos os elementos de estrutura são `Public` por padrão; classe variáveis e constantes são `Private` por padrão, enquanto outros membros da classe são `Public` por padrão.</span><span class="sxs-lookup"><span data-stu-id="17941-125">All structure elements are `Public` by default; class variables and constants are `Private` by default, while other class members are `Public` by default.</span></span> <span data-ttu-id="17941-126">Esse comportamento para membros de classe fornece compatibilidade com o sistema de padrões de Visual Basic 6.0.</span><span class="sxs-lookup"><span data-stu-id="17941-126">This behavior for class members provides compatibility with the Visual Basic 6.0 system of defaults.</span></span>  
  
-   <span data-ttu-id="17941-127">Uma estrutura deve ter pelo menos um não compartilhado variável ou não compartilhado e não personalizado elemento eventos; uma classe pode ser completamente vazia.</span><span class="sxs-lookup"><span data-stu-id="17941-127">A structure must have at least one nonshared variable or nonshared, noncustom event element; a class can be completely empty.</span></span>  
  
-   <span data-ttu-id="17941-128">Elementos de estrutura não podem ser declarados como `Protected`; membros de classe podem.</span><span class="sxs-lookup"><span data-stu-id="17941-128">Structure elements cannot be declared as `Protected`; class members can.</span></span>  
  
-   <span data-ttu-id="17941-129">Um procedimento de estrutura pode manipular eventos somente se ele for um [compartilhado](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub` procedimento e somente por meio do [instrução AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md); qualquer procedimento de classe pode manipular eventos, usando o [manipula](../../../../visual-basic/language-reference/statements/handles-clause.md) palavra-chave ou o `AddHandler` instrução.</span><span class="sxs-lookup"><span data-stu-id="17941-129">A structure procedure can handle events only if it is a [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)`Sub` procedure, and only by means of the [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md); any class procedure can handle events, using either the [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) keyword or the `AddHandler` statement.</span></span> <span data-ttu-id="17941-130">Para obter mais informações, consulte [eventos](../../../../visual-basic/programming-guide/language-features/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="17941-130">For more information, see [Events](../../../../visual-basic/programming-guide/language-features/events/index.md).</span></span>  
  
-   <span data-ttu-id="17941-131">Declarações de variável de estrutura não é possível especificar inicializadores ou tamanhos iniciais para matrizes; declarações de variável de classe podem.</span><span class="sxs-lookup"><span data-stu-id="17941-131">Structure variable declarations cannot specify initializers or initial sizes for arrays; class variable declarations can.</span></span>  
  
-   <span data-ttu-id="17941-132">Estruturas implicitamente herdam o <xref:System.ValueType?displayProperty=fullName>de classe e não podem herdar de nenhum outro tipo; classes podem herdar de qualquer classe ou classes diferentes <xref:System.ValueType?displayProperty=fullName>.</xref:System.ValueType?displayProperty=fullName> </xref:System.ValueType?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="17941-132">Structures implicitly inherit from the <xref:System.ValueType?displayProperty=fullName> class and cannot inherit from any other type; classes can inherit from any class or classes other than <xref:System.ValueType?displayProperty=fullName>.</span></span>  
  
-   <span data-ttu-id="17941-133">Estruturas não são herdáveis; classes são.</span><span class="sxs-lookup"><span data-stu-id="17941-133">Structures are not inheritable; classes are.</span></span>  
  
-   <span data-ttu-id="17941-134">Estruturas são nunca finalizadas, portanto, o common language runtime (CLR) nunca chama o <xref:System.Object.Finalize%2A>método em qualquer estrutura; as classes são finalizadas pelo coletor de lixo (GC), que chama <xref:System.Object.Finalize%2A>em uma classe quando ele detecta que há referências ativas restantes.</xref:System.Object.Finalize%2A> </xref:System.Object.Finalize%2A></span><span class="sxs-lookup"><span data-stu-id="17941-134">Structures are never terminated, so the common language runtime (CLR) never calls the <xref:System.Object.Finalize%2A> method on any structure; classes are terminated by the garbage collector (GC), which calls <xref:System.Object.Finalize%2A> on a class when it detects there are no active references remaining.</span></span>  
  
-   <span data-ttu-id="17941-135">Uma estrutura não requer um construtor; faz uma classe.</span><span class="sxs-lookup"><span data-stu-id="17941-135">A structure does not require a constructor; a class does.</span></span>  
  
-   <span data-ttu-id="17941-136">Estruturas podem ter construtores compartilhados somente se elas tiverem parâmetros; classes podem tê-los com ou sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="17941-136">Structures can have nonshared constructors only if they take parameters; classes can have them with or without parameters.</span></span>  
  
 <span data-ttu-id="17941-137">Cada estrutura tem um construtor público implícito sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="17941-137">Every structure has an implicit public constructor without parameters.</span></span> <span data-ttu-id="17941-138">Este construtor inicializa os elementos de dados do toda a estrutura para seus valores padrão.</span><span class="sxs-lookup"><span data-stu-id="17941-138">This constructor initializes all the structure's data elements to their default values.</span></span> <span data-ttu-id="17941-139">Você não pode redefinir esse comportamento.</span><span class="sxs-lookup"><span data-stu-id="17941-139">You cannot redefine this behavior.</span></span>  
  
## <a name="instances-and-variables"></a><span data-ttu-id="17941-140">Instâncias e variáveis</span><span class="sxs-lookup"><span data-stu-id="17941-140">Instances and Variables</span></span>  
 <span data-ttu-id="17941-141">Como estruturas são tipos de valor, cada variável de estrutura é permanentemente associada a uma instância de estrutura individual.</span><span class="sxs-lookup"><span data-stu-id="17941-141">Because structures are value types, each structure variable is permanently bound to an individual structure instance.</span></span> <span data-ttu-id="17941-142">Mas classes são tipos de referência e uma variável de objeto pode fazer referência a várias instâncias de classe em momentos diferentes.</span><span class="sxs-lookup"><span data-stu-id="17941-142">But classes are reference types, and an object variable can refer to various class instances at different times.</span></span> <span data-ttu-id="17941-143">Essa distinção afeta o uso de classes e estruturas das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="17941-143">This distinction affects your usage of structures and classes in the following ways:</span></span>  
  
-   <span data-ttu-id="17941-144">**Inicialização.**</span><span class="sxs-lookup"><span data-stu-id="17941-144">**Initialization.**</span></span> <span data-ttu-id="17941-145">Uma variável de estrutura implicitamente inclui uma inicialização dos elementos usando o construtor sem parâmetros da estrutura.</span><span class="sxs-lookup"><span data-stu-id="17941-145">A structure variable implicitly includes an initialization of the elements using the structure's parameterless constructor.</span></span> <span data-ttu-id="17941-146">Portanto, `Dim s As struct1` é equivalente a `Dim s As struct1 = New struct1()`.</span><span class="sxs-lookup"><span data-stu-id="17941-146">Therefore, `Dim s As struct1` is equivalent to `Dim s As struct1 = New struct1()`.</span></span>  
  
-   <span data-ttu-id="17941-147">**Atribuindo variáveis.**</span><span class="sxs-lookup"><span data-stu-id="17941-147">**Assigning Variables.**</span></span> <span data-ttu-id="17941-148">Quando você atribuir uma variável de estrutura para outro ou passa uma instância de estrutura para um argumento de procedimento, os valores atuais de todos os elementos de variáveis são copiados para a nova estrutura.</span><span class="sxs-lookup"><span data-stu-id="17941-148">When you assign one structure variable to another, or pass a structure instance to a procedure argument, the current values of all the variable elements are copied to the new structure.</span></span> <span data-ttu-id="17941-149">Quando você atribuir uma variável de objeto para outro ou passa uma variável de objeto para um procedimento, o ponteiro de referência é copiado.</span><span class="sxs-lookup"><span data-stu-id="17941-149">When you assign one object variable to another, or pass an object variable to a procedure, only the reference pointer is copied.</span></span>  
  
-   <span data-ttu-id="17941-150">**Atribuindo Nothing.**</span><span class="sxs-lookup"><span data-stu-id="17941-150">**Assigning Nothing.**</span></span> <span data-ttu-id="17941-151">Você pode atribuir o valor [nada](../../../../visual-basic/language-reference/nothing.md) a estrutura de uma variável, mas a instância continua a ser associado à variável.</span><span class="sxs-lookup"><span data-stu-id="17941-151">You can assign the value [Nothing](../../../../visual-basic/language-reference/nothing.md) to a structure variable, but the instance continues to be associated with the variable.</span></span> <span data-ttu-id="17941-152">Você ainda pode chamar seus métodos e acessar seus elementos de dados, embora os elementos de variável sejam reinicializados pela atribuição.</span><span class="sxs-lookup"><span data-stu-id="17941-152">You can still call its methods and access its data elements, although variable elements are reinitialized by the assignment.</span></span>  
  
     <span data-ttu-id="17941-153">Por outro lado, se você definir uma variável de objeto para `Nothing`, você o dissocia de qualquer instância de classe e não pode acessar todos os membros através da variável até que você atribua uma outra instância a ela.</span><span class="sxs-lookup"><span data-stu-id="17941-153">In contrast, if you set an object variable to `Nothing`, you dissociate it from any class instance, and you cannot access any members through the variable until you assign another instance to it.</span></span>  
  
-   <span data-ttu-id="17941-154">**Várias instâncias.**</span><span class="sxs-lookup"><span data-stu-id="17941-154">**Multiple Instances.**</span></span> <span data-ttu-id="17941-155">Uma variável de objeto pode ter instâncias de classe diferente atribuídas a ela em momentos diferentes, e várias variáveis de objeto podem referir-se à mesma instância de classe ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="17941-155">An object variable can have different class instances assigned to it at different times, and several object variables can refer to the same class instance at the same time.</span></span> <span data-ttu-id="17941-156">As alterações feitas aos valores de membros de classe afetarão esses membros quando acessados por outra variável apontando para a mesma instância.</span><span class="sxs-lookup"><span data-stu-id="17941-156">Changes you make to the values of class members affect those members when accessed through another variable pointing to the same instance.</span></span>  
  
     <span data-ttu-id="17941-157">Elementos de estrutura, no entanto, são isolados em sua própria instância.</span><span class="sxs-lookup"><span data-stu-id="17941-157">Structure elements, however, are isolated within their own instance.</span></span> <span data-ttu-id="17941-158">Alterações em seus valores não são refletidas em qualquer outra variável de estrutura, mesmo em outras instâncias do mesmo `Structure` declaração.</span><span class="sxs-lookup"><span data-stu-id="17941-158">Changes to their values are not reflected in any other structure variables, even in other instances of the same `Structure` declaration.</span></span>  
  
-   <span data-ttu-id="17941-159">**Igualdade.**</span><span class="sxs-lookup"><span data-stu-id="17941-159">**Equality.**</span></span> <span data-ttu-id="17941-160">Teste de igualdade de duas estruturas deve ser executada com um teste de elemento por elemento.</span><span class="sxs-lookup"><span data-stu-id="17941-160">Equality testing of two structures must be performed with an element-by-element test.</span></span> <span data-ttu-id="17941-161">Duas variáveis de objeto podem ser comparadas usando o <xref:System.Object.Equals%2A>método.</xref:System.Object.Equals%2A></span><span class="sxs-lookup"><span data-stu-id="17941-161">Two object variables can be compared using the <xref:System.Object.Equals%2A> method.</span></span> <span data-ttu-id="17941-162"><xref:System.Object.Equals%2A>Indica se as duas variáveis apontam para a mesma instância.</xref:System.Object.Equals%2A></span><span class="sxs-lookup"><span data-stu-id="17941-162"><xref:System.Object.Equals%2A> indicates whether the two variables point to the same instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17941-163">Consulte também</span><span class="sxs-lookup"><span data-stu-id="17941-163">See Also</span></span>  
 <span data-ttu-id="17941-164">[Tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="17941-164">[Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span></span>  
<span data-ttu-id="17941-165"> [Tipos de dados compostos](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="17941-165"> [Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) </span></span>  
<span data-ttu-id="17941-166"> [Tipos de valor e tipos de referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="17941-166"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span></span>  
<span data-ttu-id="17941-167"> [Estruturas](../../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span><span class="sxs-lookup"><span data-stu-id="17941-167"> [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span></span>  
<span data-ttu-id="17941-168"> [Solucionando problemas de tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="17941-168"> [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span></span>  
<span data-ttu-id="17941-169"> [Estruturas e outros elementos de programação](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md) </span><span class="sxs-lookup"><span data-stu-id="17941-169"> [Structures and Other Programming Elements](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md) </span></span>  
<span data-ttu-id="17941-170"> [Objetos e Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)</span><span class="sxs-lookup"><span data-stu-id="17941-170"> [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)</span></span>
