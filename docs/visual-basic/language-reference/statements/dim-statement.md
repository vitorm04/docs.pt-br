---
title: "Instrução Dim (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Dim
- Dim
helpviewer_keywords:
- Public keyword [Visual Basic], in Dim statement
- Dim statement [Visual Basic]
- fixed-length strings [Visual Basic], declaring
- variables [Visual Basic], declaring
- WithEvents keyword [Visual Basic], Dim statement
- dynamic arrays [Visual Basic], Dim statement
- variables [Visual Basic], initializing
- '{} braces'
- fields [Visual Basic], as member variables
- declarations [Visual Basic], dynamic arrays
- member variables [Visual Basic]
- default values [Visual Basic]
- data types [Visual Basic], assigning
- braces {}
- As keyword [Visual Basic], in Dim statement
- arrays [Visual Basic], declaring
- New keyword [Visual Basic], Dim statement
- To keyword [Visual Basic], in Dim statement
- storage [Visual Basic], allocating
- local variables [Visual Basic]
- declaration statements [Visual Basic]
- Dim statement [Visual Basic], syntax
- variables [Visual Basic], member and local
ms.assetid: fae3eca1-f0b2-4400-994b-7aa58a848448
caps.latest.revision: "72"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a428f8be7b62600ca8fffd3160039c1de911e34e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="dim-statement-visual-basic"></a><span data-ttu-id="a8985-102">Instrução Dim (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a8985-102">Dim Statement (Visual Basic)</span></span>
<span data-ttu-id="a8985-103">Declara e aloca espaço de armazenamento para uma ou mais variáveis.</span><span class="sxs-lookup"><span data-stu-id="a8985-103">Declares and allocates storage space for one or more variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8985-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a8985-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]   
Dim [ WithEvents ] variablelist  
```  
  
## <a name="parts"></a><span data-ttu-id="a8985-105">Partes</span><span class="sxs-lookup"><span data-stu-id="a8985-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="a8985-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="a8985-106">Optional.</span></span> <span data-ttu-id="a8985-107">Consulte [lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="a8985-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="a8985-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="a8985-108">Optional.</span></span> <span data-ttu-id="a8985-109">Pode ser um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="a8985-109">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="a8985-110">Público</span><span class="sxs-lookup"><span data-stu-id="a8985-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="a8985-111">Protegido</span><span class="sxs-lookup"><span data-stu-id="a8985-111">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="a8985-112">Friend</span><span class="sxs-lookup"><span data-stu-id="a8985-112">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="a8985-113">Privado</span><span class="sxs-lookup"><span data-stu-id="a8985-113">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     <span data-ttu-id="a8985-114">Consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="a8985-114">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `Shared`  
  
     <span data-ttu-id="a8985-115">Opcional.</span><span class="sxs-lookup"><span data-stu-id="a8985-115">Optional.</span></span> <span data-ttu-id="a8985-116">Consulte [compartilhado](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="a8985-116">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="a8985-117">Opcional.</span><span class="sxs-lookup"><span data-stu-id="a8985-117">Optional.</span></span> <span data-ttu-id="a8985-118">Consulte [sombras](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="a8985-118">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
-   `Static`  
  
     <span data-ttu-id="a8985-119">Opcional.</span><span class="sxs-lookup"><span data-stu-id="a8985-119">Optional.</span></span> <span data-ttu-id="a8985-120">Consulte [estático](../../../visual-basic/language-reference/modifiers/static.md).</span><span class="sxs-lookup"><span data-stu-id="a8985-120">See [Static](../../../visual-basic/language-reference/modifiers/static.md).</span></span>  
  
-   `ReadOnly`  
  
     <span data-ttu-id="a8985-121">Opcional.</span><span class="sxs-lookup"><span data-stu-id="a8985-121">Optional.</span></span> <span data-ttu-id="a8985-122">Consulte [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="a8985-122">See [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
-   `WithEvents`  
  
     <span data-ttu-id="a8985-123">Opcional.</span><span class="sxs-lookup"><span data-stu-id="a8985-123">Optional.</span></span> <span data-ttu-id="a8985-124">Especifica que eles são variáveis de objeto que se referem a instâncias de uma classe que pode gerar eventos.</span><span class="sxs-lookup"><span data-stu-id="a8985-124">Specifies that these are object variables that refer to instances of a class that can raise events.</span></span> <span data-ttu-id="a8985-125">Consulte [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md).</span><span class="sxs-lookup"><span data-stu-id="a8985-125">See [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md).</span></span>  
  
-   `variablelist`  
  
     <span data-ttu-id="a8985-126">Necessário.</span><span class="sxs-lookup"><span data-stu-id="a8985-126">Required.</span></span> <span data-ttu-id="a8985-127">Lista de variáveis que está sendo declarada nessa instrução.</span><span class="sxs-lookup"><span data-stu-id="a8985-127">List of variables being declared in this statement.</span></span>  
  
     `variable [ , variable ... ]`  
  
     <span data-ttu-id="a8985-128">Cada `variable` tem a seguinte sintaxe e partes:</span><span class="sxs-lookup"><span data-stu-id="a8985-128">Each `variable` has the following syntax and parts:</span></span>  
  
     <span data-ttu-id="a8985-129">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="a8985-129">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span></span>  
  
    |<span data-ttu-id="a8985-130">Parte</span><span class="sxs-lookup"><span data-stu-id="a8985-130">Part</span></span>|<span data-ttu-id="a8985-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="a8985-131">Description</span></span>|  
    |---|---|  
    |`variablename`|<span data-ttu-id="a8985-132">Necessário.</span><span class="sxs-lookup"><span data-stu-id="a8985-132">Required.</span></span> <span data-ttu-id="a8985-133">Nome da variável.</span><span class="sxs-lookup"><span data-stu-id="a8985-133">Name of the variable.</span></span> <span data-ttu-id="a8985-134">Consulte [declarado nomes de elemento](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="a8985-134">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
    |`boundslist`|<span data-ttu-id="a8985-135">Opcional.</span><span class="sxs-lookup"><span data-stu-id="a8985-135">Optional.</span></span> <span data-ttu-id="a8985-136">Lista de limites de cada dimensão de uma variável de matriz.</span><span class="sxs-lookup"><span data-stu-id="a8985-136">List of bounds of each dimension of an array variable.</span></span>|  
    |`New`|<span data-ttu-id="a8985-137">Opcional.</span><span class="sxs-lookup"><span data-stu-id="a8985-137">Optional.</span></span> <span data-ttu-id="a8985-138">Cria uma nova instância da classe quando o `Dim` instrução é executada.</span><span class="sxs-lookup"><span data-stu-id="a8985-138">Creates a new instance of the class when the `Dim` statement runs.</span></span>|  
    |`datatype`|<span data-ttu-id="a8985-139">Opcional.</span><span class="sxs-lookup"><span data-stu-id="a8985-139">Optional.</span></span> <span data-ttu-id="a8985-140">Tipo de dados da variável.</span><span class="sxs-lookup"><span data-stu-id="a8985-140">Data type of the variable.</span></span>|  
    |`With`|<span data-ttu-id="a8985-141">Opcional.</span><span class="sxs-lookup"><span data-stu-id="a8985-141">Optional.</span></span> <span data-ttu-id="a8985-142">Apresenta a lista de inicializador de objeto.</span><span class="sxs-lookup"><span data-stu-id="a8985-142">Introduces the object initializer list.</span></span>|  
    |`propertyname`|<span data-ttu-id="a8985-143">Opcional.</span><span class="sxs-lookup"><span data-stu-id="a8985-143">Optional.</span></span> <span data-ttu-id="a8985-144">O nome de uma propriedade na classe você estiver fazendo uma instância do.</span><span class="sxs-lookup"><span data-stu-id="a8985-144">The name of a property in the class you are making an instance of.</span></span>|  
    |`propinitializer`|<span data-ttu-id="a8985-145">Necessário após `propertyname` =.</span><span class="sxs-lookup"><span data-stu-id="a8985-145">Required after `propertyname` =.</span></span> <span data-ttu-id="a8985-146">A expressão que é avaliada e atribuída ao nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="a8985-146">The expression that is evaluated and assigned to the property name.</span></span>|  
    |`initializer`|<span data-ttu-id="a8985-147">Opcional se `New` não for especificado.</span><span class="sxs-lookup"><span data-stu-id="a8985-147">Optional if `New` is not specified.</span></span> <span data-ttu-id="a8985-148">Expressão que é avaliada e atribuída à variável quando ela é criada.</span><span class="sxs-lookup"><span data-stu-id="a8985-148">Expression that is evaluated and assigned to the variable when it is created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8985-149">Comentários</span><span class="sxs-lookup"><span data-stu-id="a8985-149">Remarks</span></span>  
 <span data-ttu-id="a8985-150">O compilador do Visual Basic usa o `Dim` instrução para determinar o tipo de dados e outras informações, como o código que pode acessar a variável.</span><span class="sxs-lookup"><span data-stu-id="a8985-150">The Visual Basic compiler uses the `Dim` statement to determine the variable's data type and other information, such as what code can access the variable.</span></span> <span data-ttu-id="a8985-151">O exemplo a seguir declara uma variável para manter uma `Integer` valor.</span><span class="sxs-lookup"><span data-stu-id="a8985-151">The following example declares a variable to hold an `Integer` value.</span></span>  
  
```vb  
Dim numberOfStudents As Integer  
```  
  
 <span data-ttu-id="a8985-152">Você pode especificar qualquer tipo de dados ou o nome de uma enumeração, estrutura, classe ou interface.</span><span class="sxs-lookup"><span data-stu-id="a8985-152">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
```vb  
Dim finished As Boolean  
Dim monitorBox As System.Windows.Forms.Form  
```  
  
 <span data-ttu-id="a8985-153">Para um tipo de referência, você deve usar o `New` palavra-chave para criar uma nova instância da classe ou estrutura que é especificada pelo tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="a8985-153">For a reference type, you use the `New` keyword to create a new instance of the class or structure that is specified by the data type.</span></span> <span data-ttu-id="a8985-154">Se você usar `New`, você não usar uma expressão de inicializador.</span><span class="sxs-lookup"><span data-stu-id="a8985-154">If you use `New`, you do not use an initializer expression.</span></span> <span data-ttu-id="a8985-155">Em vez disso, você fornecer argumentos, caso sejam necessárias para o construtor da classe da qual você está criando a variável.</span><span class="sxs-lookup"><span data-stu-id="a8985-155">Instead, you supply arguments, if they are required, to the constructor of the class from which you are creating the variable.</span></span>  
  
```vb  
Dim bottomLabel As New System.Windows.Forms.Label  
```  
  
 <span data-ttu-id="a8985-156">Você pode declarar uma variável em um procedimento, bloquear, classe, estrutura ou módulo.</span><span class="sxs-lookup"><span data-stu-id="a8985-156">You can declare a variable in a procedure, block, class, structure, or module.</span></span> <span data-ttu-id="a8985-157">Você não pode declarar uma variável em um arquivo de origem, namespace ou interface.</span><span class="sxs-lookup"><span data-stu-id="a8985-157">You cannot declare a variable in a source file, namespace, or interface.</span></span> <span data-ttu-id="a8985-158">Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="a8985-158">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="a8985-159">Uma variável que é declarada no nível de módulo, fora de qualquer procedimento, é um *variável membro* ou *campo*.</span><span class="sxs-lookup"><span data-stu-id="a8985-159">A variable that is declared at module level, outside any procedure, is a *member variable* or *field*.</span></span> <span data-ttu-id="a8985-160">Variáveis de membro estão no escopo em toda a sua classe, estrutura ou módulo.</span><span class="sxs-lookup"><span data-stu-id="a8985-160">Member variables are in scope throughout their class, structure, or module.</span></span> <span data-ttu-id="a8985-161">Uma variável que é declarada no nível de procedimento é um *variável local*.</span><span class="sxs-lookup"><span data-stu-id="a8985-161">A variable that is declared at procedure level is a *local variable*.</span></span> <span data-ttu-id="a8985-162">Variáveis locais estão no escopo somente dentro de seu procedimento ou bloco.</span><span class="sxs-lookup"><span data-stu-id="a8985-162">Local variables are in scope only within their procedure or block.</span></span>  
  
 <span data-ttu-id="a8985-163">Os modificadores de acesso a seguir são usados para declarar variáveis fora de um procedimento: `Public`, `Protected`, `Friend`, `Protected Friend`, e `Private`.</span><span class="sxs-lookup"><span data-stu-id="a8985-163">The following access modifiers are used to declare variables outside a procedure: `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private`.</span></span> <span data-ttu-id="a8985-164">Para obter mais informações, consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="a8985-164">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="a8985-165">O `Dim` palavra-chave é opcional e geralmente omitido se você especificar qualquer um dos seguintes modificadores: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, ou `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="a8985-165">The `Dim` keyword is optional and usually omitted if you specify any of the following modifiers: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, or `WithEvents`.</span></span>  
  
```vb  
Public maximumAllowed As Double  
Protected Friend currentUserName As String  
Private salary As Decimal  
Static runningTotal As Integer  
```  
  
 <span data-ttu-id="a8985-166">Se `Option Explicit` está on (o padrão), o compilador requer uma declaração para cada variável que você usa.</span><span class="sxs-lookup"><span data-stu-id="a8985-166">If `Option Explicit` is on (the default), the compiler requires a declaration for every variable you use.</span></span> <span data-ttu-id="a8985-167">Para obter mais informações, consulte [instrução Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a8985-167">For more information, see [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md).</span></span>  
  
## <a name="specifying-an-initial-value"></a><span data-ttu-id="a8985-168">Especificando um valor inicial</span><span class="sxs-lookup"><span data-stu-id="a8985-168">Specifying an Initial Value</span></span>  
 <span data-ttu-id="a8985-169">Você pode atribuir um valor a uma variável quando ela é criada.</span><span class="sxs-lookup"><span data-stu-id="a8985-169">You can assign a value to a variable when it is created.</span></span> <span data-ttu-id="a8985-170">Para um tipo de valor, você deve usar um *inicializador* para fornecer uma expressão a ser atribuído à variável.</span><span class="sxs-lookup"><span data-stu-id="a8985-170">For a value type, you use an *initializer* to supply an expression to be assigned to the variable.</span></span> <span data-ttu-id="a8985-171">A expressão deve ser avaliada como uma constante que pode ser calculada em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="a8985-171">The expression must evaluate to a constant that can be calculated at compile time.</span></span>  
  
```vb  
Dim quantity As Integer = 10  
Dim message As String = "Just started"  
```  
  
 <span data-ttu-id="a8985-172">Se um inicializador for especificado e não foi especificado um tipo de dados em um `As` cláusula, *inferência de tipo* é usada para inferir o tipo de dados do inicializador.</span><span class="sxs-lookup"><span data-stu-id="a8985-172">If an initializer is specified and a data type is not specified in an `As` clause, *type inference* is used to infer the data type from the initializer.</span></span> <span data-ttu-id="a8985-173">No exemplo a seguir, ambos `num1` e `num2` são fortemente tipadas como inteiros.</span><span class="sxs-lookup"><span data-stu-id="a8985-173">In the following example, both `num1` and `num2` are strongly typed as integers.</span></span> <span data-ttu-id="a8985-174">Na segunda declaração, a inferência de tipo infere o tipo do valor 3.</span><span class="sxs-lookup"><span data-stu-id="a8985-174">In the second declaration, type inference infers the type from the value 3.</span></span>  
  
```vb  
' Use explicit typing.  
Dim num1 As Integer = 3  
  
' Use local type inference.  
Dim num2 = 3  
```  
  
 <span data-ttu-id="a8985-175">Inferência de tipo aplica-se no nível do procedimento.</span><span class="sxs-lookup"><span data-stu-id="a8985-175">Type inference applies at the procedure level.</span></span> <span data-ttu-id="a8985-176">Não é aplicável fora de um procedimento em uma classe, estrutura, módulo ou interface.</span><span class="sxs-lookup"><span data-stu-id="a8985-176">It does not apply outside a procedure in a class, structure, module, or interface.</span></span> <span data-ttu-id="a8985-177">Para obter mais informações sobre a inferência de tipo, consulte [opção Infer instrução](../../../visual-basic/language-reference/statements/option-infer-statement.md) e [inferência de tipo Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="a8985-177">For more information about type inference, see [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
 <span data-ttu-id="a8985-178">Para obter informações sobre o que acontece quando um tipo de dados ou um inicializador não for especificado, consulte [tipos de dados padrão e valores](../../../visual-basic/language-reference/statements/dim-statement.md#default) mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="a8985-178">For information about what happens when a data type or initializer is not specified, see [Default Data Types and Values](../../../visual-basic/language-reference/statements/dim-statement.md#default) later in this topic.</span></span>  
  
 <span data-ttu-id="a8985-179">Você pode usar um *inicializador de objeto* para declarar as instâncias dos tipos nomeados e anônimos.</span><span class="sxs-lookup"><span data-stu-id="a8985-179">You can use an *object initializer* to declare instances of named and anonymous types.</span></span> <span data-ttu-id="a8985-180">O código a seguir cria uma instância de um `Student` classe e usa um inicializador de objeto para inicializar as propriedades.</span><span class="sxs-lookup"><span data-stu-id="a8985-180">The following code creates an instance of a `Student` class and uses an object initializer to initialize properties.</span></span>  
  
```vb  
Dim student1 As New Student With {.First = "Michael",   
                                  .Last = "Tucker"}  
```  
  
 <span data-ttu-id="a8985-181">Para obter mais informações sobre os inicializadores de objeto, consulte [como: declarar um objeto usando um inicializador de objeto](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [inicializadores de objeto: tipos nomeados e anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), e [tipos anônimos ](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="a8985-181">For more information about object initializers, see [How to: Declare an Object by Using an Object Initializer](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), and [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
## <a name="declaring-multiple-variables"></a><span data-ttu-id="a8985-182">Declarando variáveis múltiplas</span><span class="sxs-lookup"><span data-stu-id="a8985-182">Declaring Multiple Variables</span></span>  
 <span data-ttu-id="a8985-183">Você pode declarar diversas variáveis em uma declaração, especificando o nome da variável para cada um e após cada nome de matriz com parênteses.</span><span class="sxs-lookup"><span data-stu-id="a8985-183">You can declare several variables in one declaration statement, specifying the variable name for each one, and following each array name with parentheses.</span></span> <span data-ttu-id="a8985-184">Diversas variáveis são separadas por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="a8985-184">Multiple variables are separated by commas.</span></span>  
  
```vb  
Dim lastTime, nextTime, allTimes() As Date  
```  
  
 <span data-ttu-id="a8985-185">Se você declarar mais de uma variável com um `As` cláusula, você não pode fornecer um inicializador para esse grupo de variáveis.</span><span class="sxs-lookup"><span data-stu-id="a8985-185">If you declare more than one variable with one `As` clause, you cannot supply an initializer for that group of variables.</span></span>  
  
 <span data-ttu-id="a8985-186">Você pode especificar diferentes tipos de dados para variáveis diferentes usando um separado `As` cláusula para cada variável que você declarar.</span><span class="sxs-lookup"><span data-stu-id="a8985-186">You can specify different data types for different variables by using a separate `As` clause for each variable you declare.</span></span> <span data-ttu-id="a8985-187">Cada variável tem o tipo de dados especificado no primeiro `As` cláusula encontrados após o seu `variablename` parte.</span><span class="sxs-lookup"><span data-stu-id="a8985-187">Each variable takes the data type specified in the first `As` clause encountered after its `variablename` part.</span></span>  
  
```vb  
Dim a, b, c As Single, x, y As Double, i As Integer  
' a, b, and c are all Single; x and y are both Double  
```  
  
## <a name="arrays"></a><span data-ttu-id="a8985-188">Matrizes</span><span class="sxs-lookup"><span data-stu-id="a8985-188">Arrays</span></span>  
 <span data-ttu-id="a8985-189">Você pode declarar uma variável para manter uma *matriz*, que pode conter vários valores.</span><span class="sxs-lookup"><span data-stu-id="a8985-189">You can declare a variable to hold an *array*, which can hold multiple values.</span></span> <span data-ttu-id="a8985-190">Para especificar que uma variável contém uma matriz, siga seu `variablename` imediatamente com parênteses.</span><span class="sxs-lookup"><span data-stu-id="a8985-190">To specify that a variable holds an array, follow its `variablename` immediately with parentheses.</span></span> <span data-ttu-id="a8985-191">Para obter mais informações sobre matrizes, consulte [matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="a8985-191">For more information about arrays, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
 <span data-ttu-id="a8985-192">Você pode especificar o limite inferior e superior de cada dimensão de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="a8985-192">You can specify the lower and upper bound of each dimension of an array.</span></span> <span data-ttu-id="a8985-193">Para fazer isso, inclua um `boundslist` dentro dos parênteses.</span><span class="sxs-lookup"><span data-stu-id="a8985-193">To do this, include a `boundslist` inside the parentheses.</span></span> <span data-ttu-id="a8985-194">Para cada dimensão, o `boundslist` Especifica o limite superior e, opcionalmente, o limite inferior.</span><span class="sxs-lookup"><span data-stu-id="a8985-194">For each dimension, the `boundslist` specifies the upper bound and optionally the lower bound.</span></span> <span data-ttu-id="a8985-195">O limite inferior é sempre zero, se você especificar ou não.</span><span class="sxs-lookup"><span data-stu-id="a8985-195">The lower bound is always zero, whether you specify it or not.</span></span> <span data-ttu-id="a8985-196">Cada índice pode variar de zero por meio de seu valor de limite superior.</span><span class="sxs-lookup"><span data-stu-id="a8985-196">Each index can vary from zero through its upper bound value.</span></span>  
  
 <span data-ttu-id="a8985-197">As duas instruções a seguir são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="a8985-197">The following two statements are equivalent.</span></span> <span data-ttu-id="a8985-198">Cada instrução declara uma matriz de 21 `Integer` elementos.</span><span class="sxs-lookup"><span data-stu-id="a8985-198">Each statement declares an array of 21 `Integer` elements.</span></span> <span data-ttu-id="a8985-199">Quando você acessar a matriz, o índice pode variar de 0 a 20.</span><span class="sxs-lookup"><span data-stu-id="a8985-199">When you access the array, the index can vary from 0 through 20.</span></span>  
  
```vb  
Dim totals(20) As Integer  
Dim totals(0 To 20) As Integer  
```  
  
 <span data-ttu-id="a8985-200">A instrução a seguir declara uma matriz bidimensional de tipo `Double`.</span><span class="sxs-lookup"><span data-stu-id="a8985-200">The following statement declares a two-dimensional array of type `Double`.</span></span> <span data-ttu-id="a8985-201">A matriz tem 4 linhas (3 + 1) de 6 colunas (5 + 1).</span><span class="sxs-lookup"><span data-stu-id="a8985-201">The array has 4 rows (3 + 1) of 6 columns (5 + 1) each.</span></span> <span data-ttu-id="a8985-202">Observe que um limite superior representa o maior valor possível para o índice, não o comprimento da dimensão.</span><span class="sxs-lookup"><span data-stu-id="a8985-202">Note that an upper bound represents the highest possible value for the index, not the length of the dimension.</span></span> <span data-ttu-id="a8985-203">O comprimento da dimensão é o limite superior mais um.</span><span class="sxs-lookup"><span data-stu-id="a8985-203">The length of the dimension is the upper bound plus one.</span></span>  
  
```vb  
Dim matrix2(3, 5) As Double  
```  
  
 <span data-ttu-id="a8985-204">Uma matriz pode ter de 1 a 32 dimensões.</span><span class="sxs-lookup"><span data-stu-id="a8985-204">An array can have from 1 to 32 dimensions.</span></span>  
  
 <span data-ttu-id="a8985-205">Você pode deixar todos os limites em branco em uma declaração de matriz.</span><span class="sxs-lookup"><span data-stu-id="a8985-205">You can leave all the bounds blank in an array declaration.</span></span> <span data-ttu-id="a8985-206">Se você fizer isso, a matriz tem o número de dimensões que você especificar, mas ele não foi inicializado.</span><span class="sxs-lookup"><span data-stu-id="a8985-206">If you do this, the array has the number of dimensions you specify, but it is uninitialized.</span></span> <span data-ttu-id="a8985-207">Ele tem um valor de `Nothing` até que você inicializar pelo menos alguns de seus elementos.</span><span class="sxs-lookup"><span data-stu-id="a8985-207">It has a value of `Nothing` until you initialize at least some of its elements.</span></span> <span data-ttu-id="a8985-208">O `Dim` instrução deve especificar limites para todas as dimensões ou nenhuma dimensão.</span><span class="sxs-lookup"><span data-stu-id="a8985-208">The `Dim` statement must specify bounds either for all dimensions or for no dimensions.</span></span>  
  
```vb  
' Declare an array with blank array bounds.  
Dim messages() As String  
' Initialize the array.  
ReDim messages(4)  
```  
  
 <span data-ttu-id="a8985-209">Se a matriz tem mais de uma dimensão, você deve incluir vírgulas entre os parênteses para indicar o número de dimensões.</span><span class="sxs-lookup"><span data-stu-id="a8985-209">If the array has more than one dimension, you must include commas between the parentheses to indicate the number of dimensions.</span></span>  
  
```vb  
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte  
```  
  
 <span data-ttu-id="a8985-210">Você pode declarar uma *matriz de comprimento zero* declarando uma das dimensões da matriz para ser -1.</span><span class="sxs-lookup"><span data-stu-id="a8985-210">You can declare a *zero-length array* by declaring one of the array's dimensions to be -1.</span></span> <span data-ttu-id="a8985-211">Uma variável que contém uma matriz de comprimento zero não tem o valor `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="a8985-211">A variable that holds a zero-length array does not have the value `Nothing`.</span></span> <span data-ttu-id="a8985-212">Matrizes de comprimento zero são necessárias determinadas funções do common language runtime.</span><span class="sxs-lookup"><span data-stu-id="a8985-212">Zero-length arrays are required by certain common language runtime functions.</span></span> <span data-ttu-id="a8985-213">Se você tentar acessar essa matriz, ocorre uma exceção de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a8985-213">If you try to access such an array, a runtime exception occurs.</span></span> <span data-ttu-id="a8985-214">Para obter mais informações, consulte [matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="a8985-214">For more information, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
 <span data-ttu-id="a8985-215">Você pode inicializar os valores de uma matriz, usando um literal de matriz.</span><span class="sxs-lookup"><span data-stu-id="a8985-215">You can initialize the values of an array by using an array literal.</span></span> <span data-ttu-id="a8985-216">Para fazer isso, coloque os valores de inicialização com colchetes (`{}`).</span><span class="sxs-lookup"><span data-stu-id="a8985-216">To do this, surround the initialization values with braces (`{}`).</span></span>  
  
```vb  
Dim longArray() As Long = {0, 1, 2, 3}  
```  
  
 <span data-ttu-id="a8985-217">Para matrizes multidimensionais, a inicialização para cada dimensão separada é colocada entre chaves na dimensão externa.</span><span class="sxs-lookup"><span data-stu-id="a8985-217">For multidimensional arrays, the initialization for each separate dimension is enclosed in braces in the outer dimension.</span></span> <span data-ttu-id="a8985-218">Os elementos são especificados na ordem de linhas principais.</span><span class="sxs-lookup"><span data-stu-id="a8985-218">The elements are specified in row-major order.</span></span>  
  
```vb  
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}  
```  
  
 <span data-ttu-id="a8985-219">Para obter mais informações sobre literais de matriz, consulte [matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="a8985-219">For more information about array literals, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
##  <span data-ttu-id="a8985-220"><a name="default"></a>Tipos de dados padrão e valores</span><span class="sxs-lookup"><span data-stu-id="a8985-220"><a name="default"></a> Default Data Types and Values</span></span>  
 <span data-ttu-id="a8985-221">A tabela a seguir descreve os resultados de várias combinações de especificar o tipo de dados e o inicializador em uma instrução `Dim`.</span><span class="sxs-lookup"><span data-stu-id="a8985-221">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>  
  
|<span data-ttu-id="a8985-222">Tipo de dados especificado?</span><span class="sxs-lookup"><span data-stu-id="a8985-222">Data type specified?</span></span>|<span data-ttu-id="a8985-223">Inicializador especificado?</span><span class="sxs-lookup"><span data-stu-id="a8985-223">Initializer specified?</span></span>|<span data-ttu-id="a8985-224">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a8985-224">Example</span></span>|<span data-ttu-id="a8985-225">Resultado</span><span class="sxs-lookup"><span data-stu-id="a8985-225">Result</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="a8985-226">Não</span><span class="sxs-lookup"><span data-stu-id="a8985-226">No</span></span>|<span data-ttu-id="a8985-227">Não</span><span class="sxs-lookup"><span data-stu-id="a8985-227">No</span></span>|`Dim qty`|<span data-ttu-id="a8985-228">Se [Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) está desativado (padrão), a variável é definida como `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="a8985-228">If [Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="a8985-229">Se `Option Strict` estiver ativado, ocorre um erro de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="a8985-229">If `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="a8985-230">Não</span><span class="sxs-lookup"><span data-stu-id="a8985-230">No</span></span>|<span data-ttu-id="a8985-231">Sim</span><span class="sxs-lookup"><span data-stu-id="a8985-231">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="a8985-232">Se [Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) está on (o padrão), a variável usa os dados de tipo do inicializador.</span><span class="sxs-lookup"><span data-stu-id="a8985-232">If [Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="a8985-233">Consulte [inferência de tipo Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="a8985-233">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="a8985-234">Se `Option Infer` estiver desativado e `Option Strict` estiver desativado, a variável usa o tipo de dados do `Object`.</span><span class="sxs-lookup"><span data-stu-id="a8985-234">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="a8985-235">Se `Option Infer` estiver desativado e `Option Strict` estiver ativado, ocorre um erro de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="a8985-235">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="a8985-236">Sim</span><span class="sxs-lookup"><span data-stu-id="a8985-236">Yes</span></span>|<span data-ttu-id="a8985-237">Não</span><span class="sxs-lookup"><span data-stu-id="a8985-237">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="a8985-238">A variável é inicializada para o valor padrão para o tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="a8985-238">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="a8985-239">Consulte a tabela mais adiante nesta seção.</span><span class="sxs-lookup"><span data-stu-id="a8985-239">See the table later in this section.</span></span>|  
|<span data-ttu-id="a8985-240">Sim</span><span class="sxs-lookup"><span data-stu-id="a8985-240">Yes</span></span>|<span data-ttu-id="a8985-241">Sim</span><span class="sxs-lookup"><span data-stu-id="a8985-241">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="a8985-242">Se o tipo de dados do inicializador não for conversível para o tipo de dados especificado, ocorrerá um erro de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="a8985-242">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|  
  
 <span data-ttu-id="a8985-243">Se você especificar um tipo de dados, mas não especificar um inicializador [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] inicializa a variável para o valor padrão para seu tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="a8985-243">If you specify a data type but do not specify an initializer, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] initializes the variable to the default value for its data type.</span></span> <span data-ttu-id="a8985-244">A tabela a seguir mostra o padrão de valores de inicialização.</span><span class="sxs-lookup"><span data-stu-id="a8985-244">The following table shows the default initialization values.</span></span>  
  
|<span data-ttu-id="a8985-245">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="a8985-245">Data type</span></span>|<span data-ttu-id="a8985-246">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="a8985-246">Default value</span></span>|  
|---|---|  
|<span data-ttu-id="a8985-247">Todos os tipos numéricos (incluindo `Byte` e `SByte`)</span><span class="sxs-lookup"><span data-stu-id="a8985-247">All numeric types (including `Byte` and `SByte`)</span></span>|<span data-ttu-id="a8985-248">0</span><span class="sxs-lookup"><span data-stu-id="a8985-248">0</span></span>|  
|`Char`|<span data-ttu-id="a8985-249">0 binário</span><span class="sxs-lookup"><span data-stu-id="a8985-249">Binary 0</span></span>|  
|<span data-ttu-id="a8985-250">Todos os tipos de referência (incluindo `Object`, `String`e todas as matrizes)</span><span class="sxs-lookup"><span data-stu-id="a8985-250">All reference types (including `Object`, `String`, and all arrays)</span></span>|`Nothing`|  
|`Boolean`|`False`|  
|`Date`|<span data-ttu-id="a8985-251">12:00 AM de 1º de janeiro do ano 1 (01/01/0001 12:00:00 AM)</span><span class="sxs-lookup"><span data-stu-id="a8985-251">12:00 AM of January 1 of the year 1 (01/01/0001 12:00:00 AM)</span></span>|  
  
 <span data-ttu-id="a8985-252">Cada elemento de uma estrutura é inicializado como se fosse uma variável separada.</span><span class="sxs-lookup"><span data-stu-id="a8985-252">Each element of a structure is initialized as if it were a separate variable.</span></span> <span data-ttu-id="a8985-253">Se você declara o comprimento de uma matriz, mas não inicializar seus elementos, cada elemento é inicializado como se fosse uma variável separada.</span><span class="sxs-lookup"><span data-stu-id="a8985-253">If you declare the length of an array but do not initialize its elements, each element is initialized as if it were a separate variable.</span></span>  
  
## <a name="static-local-variable-lifetime"></a><span data-ttu-id="a8985-254">Vida útil variável Local estática</span><span class="sxs-lookup"><span data-stu-id="a8985-254">Static Local Variable Lifetime</span></span>  
 <span data-ttu-id="a8985-255">Um `Static` variável local tem um tempo de vida mais longo do que o procedimento no qual ela é declarada.</span><span class="sxs-lookup"><span data-stu-id="a8985-255">A `Static` local variable has a longer lifetime than that of the procedure in which it is declared.</span></span> <span data-ttu-id="a8985-256">Os limites de tempo de vida da variável dependem de onde o procedimento é declarado e se ela é `Shared`.</span><span class="sxs-lookup"><span data-stu-id="a8985-256">The boundaries of the variable's lifetime depend on where the procedure is declared and whether it is `Shared`.</span></span>  
  
|<span data-ttu-id="a8985-257">Declaração de procedimento</span><span class="sxs-lookup"><span data-stu-id="a8985-257">Procedure declaration</span></span>|<span data-ttu-id="a8985-258">Variável inicializada</span><span class="sxs-lookup"><span data-stu-id="a8985-258">Variable initialized</span></span>|<span data-ttu-id="a8985-259">Variável interrompe existente</span><span class="sxs-lookup"><span data-stu-id="a8985-259">Variable stops existing</span></span>|  
|---|---|---|  
|<span data-ttu-id="a8985-260">Em um módulo</span><span class="sxs-lookup"><span data-stu-id="a8985-260">In a module</span></span>|<span data-ttu-id="a8985-261">Na primeira vez em que o procedimento é chamado.</span><span class="sxs-lookup"><span data-stu-id="a8985-261">The first time the procedure is called</span></span>|<span data-ttu-id="a8985-262">Quando o programa para a execução</span><span class="sxs-lookup"><span data-stu-id="a8985-262">When your program stops execution</span></span>|  
|<span data-ttu-id="a8985-263">Em uma classe ou estrutura, o procedimento é`Shared`</span><span class="sxs-lookup"><span data-stu-id="a8985-263">In a class or structure, procedure is `Shared`</span></span>|<span data-ttu-id="a8985-264">Na primeira vez que o procedimento é chamado em uma instância específica ou na classe ou estrutura em si</span><span class="sxs-lookup"><span data-stu-id="a8985-264">The first time the procedure is called either on a specific instance or on the class or structure itself</span></span>|<span data-ttu-id="a8985-265">Quando o programa para a execução</span><span class="sxs-lookup"><span data-stu-id="a8985-265">When your program stops execution</span></span>|  
|<span data-ttu-id="a8985-266">Em uma classe ou estrutura, o procedimento não é`Shared`</span><span class="sxs-lookup"><span data-stu-id="a8985-266">In a class or structure, procedure isn't `Shared`</span></span>|<span data-ttu-id="a8985-267">Na primeira vez em que o procedimento é chamado em uma instância específica</span><span class="sxs-lookup"><span data-stu-id="a8985-267">The first time the procedure is called on a specific instance</span></span>|<span data-ttu-id="a8985-268">Quando a instância é liberada para coleta de lixo (GC)</span><span class="sxs-lookup"><span data-stu-id="a8985-268">When the instance is released for garbage collection (GC)</span></span>|  
  
## <a name="attributes-and-modifiers"></a><span data-ttu-id="a8985-269">Modificadores e atributos</span><span class="sxs-lookup"><span data-stu-id="a8985-269">Attributes and Modifiers</span></span>  
 <span data-ttu-id="a8985-270">Você pode aplicar atributos apenas para variáveis de membro, não para variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="a8985-270">You can apply attributes only to member variables, not to local variables.</span></span> <span data-ttu-id="a8985-271">Um atributo contribui com informações para metadados do assembly, que não é significativo para armazenamento temporário, como variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="a8985-271">An attribute contributes information to the assembly's metadata, which is not meaningful for temporary storage such as local variables.</span></span>  
  
 <span data-ttu-id="a8985-272">No nível de módulo, você não pode usar o `Static` modificador para declarar variáveis de membro.</span><span class="sxs-lookup"><span data-stu-id="a8985-272">At module level, you cannot use the `Static` modifier to declare member variables.</span></span> <span data-ttu-id="a8985-273">No nível de procedimento, você não pode usar `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, ou qualquer modificador de acesso para declarar variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="a8985-273">At procedure level, you cannot use `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, or any access modifiers to declare local variables.</span></span>  
  
 <span data-ttu-id="a8985-274">Você pode especificar qual código pode acessar uma variável, fornecendo um `accessmodifier`.</span><span class="sxs-lookup"><span data-stu-id="a8985-274">You can specify what code can access a variable by supplying an `accessmodifier`.</span></span> <span data-ttu-id="a8985-275">Classe e o módulo membro padrão de variáveis (fora de qualquer procedimento) para acesso privado e padrão de variáveis de membro de estrutura para acesso público.</span><span class="sxs-lookup"><span data-stu-id="a8985-275">Class and module member variables (outside any procedure) default to private access, and structure member variables default to public access.</span></span> <span data-ttu-id="a8985-276">Você pode ajustar os níveis de acesso com os modificadores de acesso.</span><span class="sxs-lookup"><span data-stu-id="a8985-276">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="a8985-277">Você não pode usar os modificadores de acesso em variáveis locais (dentro de um procedimento).</span><span class="sxs-lookup"><span data-stu-id="a8985-277">You cannot use access modifiers on local variables (inside a procedure).</span></span>  
  
 <span data-ttu-id="a8985-278">Você pode especificar `WithEvents` somente em variáveis de membro, não em variáveis locais dentro de um procedimento.</span><span class="sxs-lookup"><span data-stu-id="a8985-278">You can specify `WithEvents` only on member variables, not on local variables inside a procedure.</span></span> <span data-ttu-id="a8985-279">Se você especificar `WithEvents`, o tipo de dados da variável deve ser um tipo de classe específica, não `Object`.</span><span class="sxs-lookup"><span data-stu-id="a8985-279">If you specify `WithEvents`, the data type of the variable must be a specific class type, not `Object`.</span></span> <span data-ttu-id="a8985-280">Você não pode declarar uma matriz com `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="a8985-280">You cannot declare an array with `WithEvents`.</span></span> <span data-ttu-id="a8985-281">Para obter mais informações sobre eventos, consulte [eventos](../../../visual-basic/programming-guide/language-features/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="a8985-281">For more information about events, see [Events](../../../visual-basic/programming-guide/language-features/events/index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a8985-282">Código fora de uma classe, estrutura ou o módulo deve qualificar o nome de uma variável membro com o nome da classe, estrutura ou módulo.</span><span class="sxs-lookup"><span data-stu-id="a8985-282">Code outside a class, structure, or module must qualify a member variable's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="a8985-283">Código fora de que um procedimento ou bloco não pode se referir a todas as variáveis locais dentro desse procedimento ou bloco.</span><span class="sxs-lookup"><span data-stu-id="a8985-283">Code outside a procedure or block cannot refer to any local variables within that procedure or block.</span></span>  
  
## <a name="releasing-managed-resources"></a><span data-ttu-id="a8985-284">Liberar recursos gerenciados</span><span class="sxs-lookup"><span data-stu-id="a8985-284">Releasing Managed Resources</span></span>  
 <span data-ttu-id="a8985-285">O coletor de lixo do .NET Framework libera os recursos gerenciados sem qualquer codificação extra de sua parte.</span><span class="sxs-lookup"><span data-stu-id="a8985-285">The .NET Framework garbage collector disposes of managed resources without any extra coding on your part.</span></span> <span data-ttu-id="a8985-286">No entanto, você pode forçar o descarte de um recurso gerenciado em vez de esperar o coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="a8985-286">However, you can force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>  
  
 <span data-ttu-id="a8985-287">Se uma classe mantiver um recurso particularmente importante e escasso (como um identificador de arquivo ou a conexão de banco de dados), não convém esperar até a próxima coleta de lixo para limpar uma instância da classe que não está mais em uso.</span><span class="sxs-lookup"><span data-stu-id="a8985-287">If a class holds onto a particularly valuable and scarce resource (such as a database connection or file handle), you might not want to wait until the next garbage collection to clean up a class instance that's no longer in use.</span></span> <span data-ttu-id="a8985-288">Uma classe pode implementar o <xref:System.IDisposable> interface para fornecer uma maneira para liberar recursos antes de uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="a8985-288">A class may implement the <xref:System.IDisposable> interface to provide a way to release resources before a garbage collection.</span></span> <span data-ttu-id="a8985-289">Uma classe que implementa essa interface expõe um `Dispose` método que pode ser chamado para forçar valiosos recursos sejam liberados imediatamente.</span><span class="sxs-lookup"><span data-stu-id="a8985-289">A class that implements that interface exposes a `Dispose` method that can be called to force valuable resources to be released immediately.</span></span>  
  
 <span data-ttu-id="a8985-290">O `Using` instrução automatiza o processo de aquisição de um recurso, executando um conjunto de instruções e, em seguida, descarte do recurso.</span><span class="sxs-lookup"><span data-stu-id="a8985-290">The `Using` statement automates the process of acquiring a resource, executing a set of statements, and then disposing of the resource.</span></span> <span data-ttu-id="a8985-291">No entanto, o recurso deve implementar o <xref:System.IDisposable> interface.</span><span class="sxs-lookup"><span data-stu-id="a8985-291">However, the resource must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="a8985-292">Para obter mais informações, consulte [Instrução using](../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a8985-292">For more information, see [Using Statement](../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8985-293">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a8985-293">Example</span></span>  
 <span data-ttu-id="a8985-294">O exemplo a seguir declara variáveis usando a `Dim` instrução com várias opções.</span><span class="sxs-lookup"><span data-stu-id="a8985-294">The following example declares variables by using the `Dim` statement with various options.</span></span>  
  
 [!code-vb[VbVbalrStatements#141](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="a8985-295">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a8985-295">Example</span></span>  
 <span data-ttu-id="a8985-296">O exemplo a seguir lista os números primos entre 1 e 30.</span><span class="sxs-lookup"><span data-stu-id="a8985-296">The following example lists the prime numbers between 1 and 30.</span></span> <span data-ttu-id="a8985-297">O escopo de variáveis locais é descrito nos comentários de código.</span><span class="sxs-lookup"><span data-stu-id="a8985-297">The scope of local variables is described in code comments.</span></span>  
  
 [!code-vb[VbVbalrStatements#142](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="a8985-298">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a8985-298">Example</span></span>  
 <span data-ttu-id="a8985-299">No exemplo a seguir, o `speedValue` variável é declarada no nível de classe.</span><span class="sxs-lookup"><span data-stu-id="a8985-299">In the following example, the `speedValue` variable is declared at the class level.</span></span> <span data-ttu-id="a8985-300">O `Private` palavra-chave é usada para declarar a variável.</span><span class="sxs-lookup"><span data-stu-id="a8985-300">The `Private` keyword is used to declare the variable.</span></span> <span data-ttu-id="a8985-301">A variável pode ser acessada por qualquer procedimento de `Car` classe.</span><span class="sxs-lookup"><span data-stu-id="a8985-301">The variable can be accessed by any procedure in the `Car` class.</span></span>  
  
 [!code-vb[VbVbalrStatements#144](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_3.vb)]  
  
 [!code-vb[VbVbalrStatements#145](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a8985-302">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a8985-302">See Also</span></span>  
 [<span data-ttu-id="a8985-303">Instrução Const</span><span class="sxs-lookup"><span data-stu-id="a8985-303">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
 [<span data-ttu-id="a8985-304">Instrução ReDim</span><span class="sxs-lookup"><span data-stu-id="a8985-304">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="a8985-305">Instrução Option Explicit</span><span class="sxs-lookup"><span data-stu-id="a8985-305">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [<span data-ttu-id="a8985-306">Instrução Option Infer</span><span class="sxs-lookup"><span data-stu-id="a8985-306">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [<span data-ttu-id="a8985-307">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="a8985-307">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="a8985-308">Página de Compilação, Designer de Projeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a8985-308">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)  
 [<span data-ttu-id="a8985-309">Declaração de Variável</span><span class="sxs-lookup"><span data-stu-id="a8985-309">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="a8985-310">Matrizes</span><span class="sxs-lookup"><span data-stu-id="a8985-310">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="a8985-311">Inicializadores de objeto: tipos nomeados e anônimos</span><span class="sxs-lookup"><span data-stu-id="a8985-311">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [<span data-ttu-id="a8985-312">Tipos Anônimos</span><span class="sxs-lookup"><span data-stu-id="a8985-312">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [<span data-ttu-id="a8985-313">Inicializadores de objeto: tipos nomeados e anônimos</span><span class="sxs-lookup"><span data-stu-id="a8985-313">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [<span data-ttu-id="a8985-314">Como declarar um objeto usando um inicializador de objeto</span><span class="sxs-lookup"><span data-stu-id="a8985-314">How to: Declare an Object by Using an Object Initializer</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)  
 [<span data-ttu-id="a8985-315">Inferência de Tipo de Variável Local</span><span class="sxs-lookup"><span data-stu-id="a8985-315">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
