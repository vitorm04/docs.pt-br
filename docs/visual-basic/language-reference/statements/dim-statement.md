---
title: Instrução Dim (Visual Basic)
ms.date: 05/12/2018
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
ms.openlocfilehash: b3384b771748a1f2c9e841407042f81ce6ebe76d
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34234721"
---
# <a name="dim-statement-visual-basic"></a><span data-ttu-id="3855a-102">Instrução Dim (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3855a-102">Dim Statement (Visual Basic)</span></span>
<span data-ttu-id="3855a-103">Declara e aloca espaço de armazenamento para uma ou mais variáveis.</span><span class="sxs-lookup"><span data-stu-id="3855a-103">Declares and allocates storage space for one or more variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3855a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3855a-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]   
Dim [ WithEvents ] variablelist  
```  
  
## <a name="parts"></a><span data-ttu-id="3855a-105">Partes</span><span class="sxs-lookup"><span data-stu-id="3855a-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="3855a-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="3855a-106">Optional.</span></span> <span data-ttu-id="3855a-107">Consulte [lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="3855a-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="3855a-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="3855a-108">Optional.</span></span> <span data-ttu-id="3855a-109">Pode ser um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="3855a-109">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="3855a-110">Público</span><span class="sxs-lookup"><span data-stu-id="3855a-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="3855a-111">Protegido</span><span class="sxs-lookup"><span data-stu-id="3855a-111">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="3855a-112">Friend</span><span class="sxs-lookup"><span data-stu-id="3855a-112">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="3855a-113">Privado</span><span class="sxs-lookup"><span data-stu-id="3855a-113">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   [<span data-ttu-id="3855a-114">Friend protegido</span><span class="sxs-lookup"><span data-stu-id="3855a-114">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)
    
    - [<span data-ttu-id="3855a-115">Privado protegido</span><span class="sxs-lookup"><span data-stu-id="3855a-115">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)

     <span data-ttu-id="3855a-116">Consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="3855a-116">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `Shared`  
  
     <span data-ttu-id="3855a-117">Opcional.</span><span class="sxs-lookup"><span data-stu-id="3855a-117">Optional.</span></span> <span data-ttu-id="3855a-118">Consulte [compartilhado](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="3855a-118">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="3855a-119">Opcional.</span><span class="sxs-lookup"><span data-stu-id="3855a-119">Optional.</span></span> <span data-ttu-id="3855a-120">Consulte [sombras](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="3855a-120">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
-   `Static`  
  
     <span data-ttu-id="3855a-121">Opcional.</span><span class="sxs-lookup"><span data-stu-id="3855a-121">Optional.</span></span> <span data-ttu-id="3855a-122">Consulte [estático](../../../visual-basic/language-reference/modifiers/static.md).</span><span class="sxs-lookup"><span data-stu-id="3855a-122">See [Static](../../../visual-basic/language-reference/modifiers/static.md).</span></span>  
  
-   `ReadOnly`  
  
     <span data-ttu-id="3855a-123">Opcional.</span><span class="sxs-lookup"><span data-stu-id="3855a-123">Optional.</span></span> <span data-ttu-id="3855a-124">Consulte [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="3855a-124">See [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
-   `WithEvents`  
  
     <span data-ttu-id="3855a-125">Opcional.</span><span class="sxs-lookup"><span data-stu-id="3855a-125">Optional.</span></span> <span data-ttu-id="3855a-126">Especifica que eles são variáveis de objeto que se referem a instâncias de uma classe que pode gerar eventos.</span><span class="sxs-lookup"><span data-stu-id="3855a-126">Specifies that these are object variables that refer to instances of a class that can raise events.</span></span> <span data-ttu-id="3855a-127">Consulte [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md).</span><span class="sxs-lookup"><span data-stu-id="3855a-127">See [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md).</span></span>  
  
-   `variablelist`  
  
     <span data-ttu-id="3855a-128">Necessário.</span><span class="sxs-lookup"><span data-stu-id="3855a-128">Required.</span></span> <span data-ttu-id="3855a-129">Lista de variáveis que está sendo declarada nessa instrução.</span><span class="sxs-lookup"><span data-stu-id="3855a-129">List of variables being declared in this statement.</span></span>  
  
     `variable [ , variable ... ]`  
  
     <span data-ttu-id="3855a-130">Cada `variable` tem a seguinte sintaxe e partes:</span><span class="sxs-lookup"><span data-stu-id="3855a-130">Each `variable` has the following syntax and parts:</span></span>  
  
     <span data-ttu-id="3855a-131">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="3855a-131">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span></span>  
  
    |<span data-ttu-id="3855a-132">Parte</span><span class="sxs-lookup"><span data-stu-id="3855a-132">Part</span></span>|<span data-ttu-id="3855a-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="3855a-133">Description</span></span>|  
    |---|---|  
    |`variablename`|<span data-ttu-id="3855a-134">Necessário.</span><span class="sxs-lookup"><span data-stu-id="3855a-134">Required.</span></span> <span data-ttu-id="3855a-135">Nome da variável.</span><span class="sxs-lookup"><span data-stu-id="3855a-135">Name of the variable.</span></span> <span data-ttu-id="3855a-136">Consulte [declarado nomes de elemento](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="3855a-136">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
    |`boundslist`|<span data-ttu-id="3855a-137">Opcional.</span><span class="sxs-lookup"><span data-stu-id="3855a-137">Optional.</span></span> <span data-ttu-id="3855a-138">Lista de limites de cada dimensão de uma variável de matriz.</span><span class="sxs-lookup"><span data-stu-id="3855a-138">List of bounds of each dimension of an array variable.</span></span>|  
    |`New`|<span data-ttu-id="3855a-139">Opcional.</span><span class="sxs-lookup"><span data-stu-id="3855a-139">Optional.</span></span> <span data-ttu-id="3855a-140">Cria uma nova instância da classe quando o `Dim` instrução é executada.</span><span class="sxs-lookup"><span data-stu-id="3855a-140">Creates a new instance of the class when the `Dim` statement runs.</span></span>|  
    |`datatype`|<span data-ttu-id="3855a-141">Opcional.</span><span class="sxs-lookup"><span data-stu-id="3855a-141">Optional.</span></span> <span data-ttu-id="3855a-142">Tipo de dados da variável.</span><span class="sxs-lookup"><span data-stu-id="3855a-142">Data type of the variable.</span></span>|  
    |`With`|<span data-ttu-id="3855a-143">Opcional.</span><span class="sxs-lookup"><span data-stu-id="3855a-143">Optional.</span></span> <span data-ttu-id="3855a-144">Apresenta a lista de inicializador de objeto.</span><span class="sxs-lookup"><span data-stu-id="3855a-144">Introduces the object initializer list.</span></span>|  
    |`propertyname`|<span data-ttu-id="3855a-145">Opcional.</span><span class="sxs-lookup"><span data-stu-id="3855a-145">Optional.</span></span> <span data-ttu-id="3855a-146">O nome de uma propriedade na classe você estiver fazendo uma instância do.</span><span class="sxs-lookup"><span data-stu-id="3855a-146">The name of a property in the class you are making an instance of.</span></span>|  
    |`propinitializer`|<span data-ttu-id="3855a-147">Necessário após `propertyname` =.</span><span class="sxs-lookup"><span data-stu-id="3855a-147">Required after `propertyname` =.</span></span> <span data-ttu-id="3855a-148">A expressão que é avaliada e atribuída ao nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="3855a-148">The expression that is evaluated and assigned to the property name.</span></span>|  
    |`initializer`|<span data-ttu-id="3855a-149">Opcional se `New` não for especificado.</span><span class="sxs-lookup"><span data-stu-id="3855a-149">Optional if `New` is not specified.</span></span> <span data-ttu-id="3855a-150">Expressão que é avaliada e atribuída à variável quando ela é criada.</span><span class="sxs-lookup"><span data-stu-id="3855a-150">Expression that is evaluated and assigned to the variable when it is created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3855a-151">Comentários</span><span class="sxs-lookup"><span data-stu-id="3855a-151">Remarks</span></span>  
 <span data-ttu-id="3855a-152">O compilador do Visual Basic usa o `Dim` instrução para determinar o tipo de dados e outras informações, como o código que pode acessar a variável.</span><span class="sxs-lookup"><span data-stu-id="3855a-152">The Visual Basic compiler uses the `Dim` statement to determine the variable's data type and other information, such as what code can access the variable.</span></span> <span data-ttu-id="3855a-153">O exemplo a seguir declara uma variável para manter uma `Integer` valor.</span><span class="sxs-lookup"><span data-stu-id="3855a-153">The following example declares a variable to hold an `Integer` value.</span></span>  
  
```vb  
Dim numberOfStudents As Integer  
```  
  
 <span data-ttu-id="3855a-154">Você pode especificar qualquer tipo de dados ou o nome de uma enumeração, estrutura, classe ou interface.</span><span class="sxs-lookup"><span data-stu-id="3855a-154">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
```vb  
Dim finished As Boolean  
Dim monitorBox As System.Windows.Forms.Form  
```  
  
 <span data-ttu-id="3855a-155">Para um tipo de referência, você deve usar o `New` palavra-chave para criar uma nova instância da classe ou estrutura que é especificada pelo tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="3855a-155">For a reference type, you use the `New` keyword to create a new instance of the class or structure that is specified by the data type.</span></span> <span data-ttu-id="3855a-156">Se você usar `New`, você não usar uma expressão de inicializador.</span><span class="sxs-lookup"><span data-stu-id="3855a-156">If you use `New`, you do not use an initializer expression.</span></span> <span data-ttu-id="3855a-157">Em vez disso, você fornecer argumentos, caso sejam necessárias para o construtor da classe da qual você está criando a variável.</span><span class="sxs-lookup"><span data-stu-id="3855a-157">Instead, you supply arguments, if they are required, to the constructor of the class from which you are creating the variable.</span></span>  
  
```vb  
Dim bottomLabel As New System.Windows.Forms.Label  
```  
  
 <span data-ttu-id="3855a-158">Você pode declarar uma variável em um procedimento, bloquear, classe, estrutura ou módulo.</span><span class="sxs-lookup"><span data-stu-id="3855a-158">You can declare a variable in a procedure, block, class, structure, or module.</span></span> <span data-ttu-id="3855a-159">Você não pode declarar uma variável em um arquivo de origem, namespace ou interface.</span><span class="sxs-lookup"><span data-stu-id="3855a-159">You cannot declare a variable in a source file, namespace, or interface.</span></span> <span data-ttu-id="3855a-160">Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="3855a-160">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="3855a-161">Uma variável que é declarada no nível de módulo, fora de qualquer procedimento, é um *variável membro* ou *campo*.</span><span class="sxs-lookup"><span data-stu-id="3855a-161">A variable that is declared at module level, outside any procedure, is a *member variable* or *field*.</span></span> <span data-ttu-id="3855a-162">Variáveis de membro estão no escopo em toda a sua classe, estrutura ou módulo.</span><span class="sxs-lookup"><span data-stu-id="3855a-162">Member variables are in scope throughout their class, structure, or module.</span></span> <span data-ttu-id="3855a-163">Uma variável que é declarada no nível de procedimento é um *variável local*.</span><span class="sxs-lookup"><span data-stu-id="3855a-163">A variable that is declared at procedure level is a *local variable*.</span></span> <span data-ttu-id="3855a-164">Variáveis locais estão no escopo somente dentro de seu procedimento ou bloco.</span><span class="sxs-lookup"><span data-stu-id="3855a-164">Local variables are in scope only within their procedure or block.</span></span>  
  
 <span data-ttu-id="3855a-165">Os modificadores de acesso a seguir são usados para declarar variáveis fora de um procedimento: `Public`, `Protected`, `Friend`, `Protected Friend`, e `Private`.</span><span class="sxs-lookup"><span data-stu-id="3855a-165">The following access modifiers are used to declare variables outside a procedure: `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private`.</span></span> <span data-ttu-id="3855a-166">Para obter mais informações, consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="3855a-166">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="3855a-167">O `Dim` palavra-chave é opcional e geralmente omitido se você especificar qualquer um dos seguintes modificadores: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, ou `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="3855a-167">The `Dim` keyword is optional and usually omitted if you specify any of the following modifiers: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, or `WithEvents`.</span></span>  
  
```vb  
Public maximumAllowed As Double  
Protected Friend currentUserName As String  
Private salary As Decimal  
Static runningTotal As Integer  
```  
  
 <span data-ttu-id="3855a-168">Se `Option Explicit` está on (o padrão), o compilador requer uma declaração para cada variável que você usa.</span><span class="sxs-lookup"><span data-stu-id="3855a-168">If `Option Explicit` is on (the default), the compiler requires a declaration for every variable you use.</span></span> <span data-ttu-id="3855a-169">Para obter mais informações, consulte [instrução Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3855a-169">For more information, see [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md).</span></span>  
  
## <a name="specifying-an-initial-value"></a><span data-ttu-id="3855a-170">Especificando um valor inicial</span><span class="sxs-lookup"><span data-stu-id="3855a-170">Specifying an Initial Value</span></span>  
 <span data-ttu-id="3855a-171">Você pode atribuir um valor a uma variável quando ela é criada.</span><span class="sxs-lookup"><span data-stu-id="3855a-171">You can assign a value to a variable when it is created.</span></span> <span data-ttu-id="3855a-172">Para um tipo de valor, você deve usar um *inicializador* para fornecer uma expressão a ser atribuído à variável.</span><span class="sxs-lookup"><span data-stu-id="3855a-172">For a value type, you use an *initializer* to supply an expression to be assigned to the variable.</span></span> <span data-ttu-id="3855a-173">A expressão deve ser avaliada como uma constante que pode ser calculada em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="3855a-173">The expression must evaluate to a constant that can be calculated at compile time.</span></span>  
  
```vb  
Dim quantity As Integer = 10  
Dim message As String = "Just started"  
```  
  
 <span data-ttu-id="3855a-174">Se um inicializador for especificado e não foi especificado um tipo de dados em um `As` cláusula, *inferência de tipo* é usada para inferir o tipo de dados do inicializador.</span><span class="sxs-lookup"><span data-stu-id="3855a-174">If an initializer is specified and a data type is not specified in an `As` clause, *type inference* is used to infer the data type from the initializer.</span></span> <span data-ttu-id="3855a-175">No exemplo a seguir, ambos `num1` e `num2` são fortemente tipadas como inteiros.</span><span class="sxs-lookup"><span data-stu-id="3855a-175">In the following example, both `num1` and `num2` are strongly typed as integers.</span></span> <span data-ttu-id="3855a-176">Na segunda declaração, a inferência de tipo infere o tipo do valor 3.</span><span class="sxs-lookup"><span data-stu-id="3855a-176">In the second declaration, type inference infers the type from the value 3.</span></span>  
  
```vb  
' Use explicit typing.  
Dim num1 As Integer = 3  
  
' Use local type inference.  
Dim num2 = 3  
```  
  
 <span data-ttu-id="3855a-177">Inferência de tipo aplica-se no nível do procedimento.</span><span class="sxs-lookup"><span data-stu-id="3855a-177">Type inference applies at the procedure level.</span></span> <span data-ttu-id="3855a-178">Não é aplicável fora de um procedimento em uma classe, estrutura, módulo ou interface.</span><span class="sxs-lookup"><span data-stu-id="3855a-178">It does not apply outside a procedure in a class, structure, module, or interface.</span></span> <span data-ttu-id="3855a-179">Para obter mais informações sobre a inferência de tipo, consulte [opção Infer instrução](../../../visual-basic/language-reference/statements/option-infer-statement.md) e [inferência de tipo Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="3855a-179">For more information about type inference, see [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
 <span data-ttu-id="3855a-180">Para obter informações sobre o que acontece quando um tipo de dados ou um inicializador não for especificado, consulte [tipos de dados padrão e valores](../../../visual-basic/language-reference/statements/dim-statement.md#default) mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="3855a-180">For information about what happens when a data type or initializer is not specified, see [Default Data Types and Values](../../../visual-basic/language-reference/statements/dim-statement.md#default) later in this topic.</span></span>  
  
 <span data-ttu-id="3855a-181">Você pode usar um *inicializador de objeto* para declarar as instâncias dos tipos nomeados e anônimos.</span><span class="sxs-lookup"><span data-stu-id="3855a-181">You can use an *object initializer* to declare instances of named and anonymous types.</span></span> <span data-ttu-id="3855a-182">O código a seguir cria uma instância de um `Student` classe e usa um inicializador de objeto para inicializar as propriedades.</span><span class="sxs-lookup"><span data-stu-id="3855a-182">The following code creates an instance of a `Student` class and uses an object initializer to initialize properties.</span></span>  
  
```vb  
Dim student1 As New Student With {.First = "Michael",   
                                  .Last = "Tucker"}  
```  
  
 <span data-ttu-id="3855a-183">Para obter mais informações sobre os inicializadores de objeto, consulte [como: declarar um objeto usando um inicializador de objeto](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [inicializadores de objeto: tipos nomeados e anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), e [tipos anônimos ](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="3855a-183">For more information about object initializers, see [How to: Declare an Object by Using an Object Initializer](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), and [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
## <a name="declaring-multiple-variables"></a><span data-ttu-id="3855a-184">Declarando variáveis múltiplas</span><span class="sxs-lookup"><span data-stu-id="3855a-184">Declaring Multiple Variables</span></span>  
 <span data-ttu-id="3855a-185">Você pode declarar diversas variáveis em uma declaração, especificando o nome da variável para cada um e após cada nome de matriz com parênteses.</span><span class="sxs-lookup"><span data-stu-id="3855a-185">You can declare several variables in one declaration statement, specifying the variable name for each one, and following each array name with parentheses.</span></span> <span data-ttu-id="3855a-186">Diversas variáveis são separadas por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="3855a-186">Multiple variables are separated by commas.</span></span>  
  
```vb  
Dim lastTime, nextTime, allTimes() As Date  
```  
  
 <span data-ttu-id="3855a-187">Se você declarar mais de uma variável com um `As` cláusula, você não pode fornecer um inicializador para esse grupo de variáveis.</span><span class="sxs-lookup"><span data-stu-id="3855a-187">If you declare more than one variable with one `As` clause, you cannot supply an initializer for that group of variables.</span></span>  
  
 <span data-ttu-id="3855a-188">Você pode especificar diferentes tipos de dados para variáveis diferentes usando um separado `As` cláusula para cada variável que você declarar.</span><span class="sxs-lookup"><span data-stu-id="3855a-188">You can specify different data types for different variables by using a separate `As` clause for each variable you declare.</span></span> <span data-ttu-id="3855a-189">Cada variável tem o tipo de dados especificado no primeiro `As` cláusula encontrados após o seu `variablename` parte.</span><span class="sxs-lookup"><span data-stu-id="3855a-189">Each variable takes the data type specified in the first `As` clause encountered after its `variablename` part.</span></span>  
  
```vb  
Dim a, b, c As Single, x, y As Double, i As Integer  
' a, b, and c are all Single; x and y are both Double  
```  
  
## <a name="arrays"></a><span data-ttu-id="3855a-190">Matrizes</span><span class="sxs-lookup"><span data-stu-id="3855a-190">Arrays</span></span>  
 <span data-ttu-id="3855a-191">Você pode declarar uma variável para manter uma *matriz*, que pode conter vários valores.</span><span class="sxs-lookup"><span data-stu-id="3855a-191">You can declare a variable to hold an *array*, which can hold multiple values.</span></span> <span data-ttu-id="3855a-192">Para especificar que uma variável contém uma matriz, siga seu `variablename` imediatamente com parênteses.</span><span class="sxs-lookup"><span data-stu-id="3855a-192">To specify that a variable holds an array, follow its `variablename` immediately with parentheses.</span></span> <span data-ttu-id="3855a-193">Para obter mais informações sobre matrizes, consulte [matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="3855a-193">For more information about arrays, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
 <span data-ttu-id="3855a-194">Você pode especificar o limite inferior e superior de cada dimensão de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="3855a-194">You can specify the lower and upper bound of each dimension of an array.</span></span> <span data-ttu-id="3855a-195">Para fazer isso, inclua um `boundslist` dentro dos parênteses.</span><span class="sxs-lookup"><span data-stu-id="3855a-195">To do this, include a `boundslist` inside the parentheses.</span></span> <span data-ttu-id="3855a-196">Para cada dimensão, o `boundslist` Especifica o limite superior e, opcionalmente, o limite inferior.</span><span class="sxs-lookup"><span data-stu-id="3855a-196">For each dimension, the `boundslist` specifies the upper bound and optionally the lower bound.</span></span> <span data-ttu-id="3855a-197">O limite inferior é sempre zero, se você especificar ou não.</span><span class="sxs-lookup"><span data-stu-id="3855a-197">The lower bound is always zero, whether you specify it or not.</span></span> <span data-ttu-id="3855a-198">Cada índice pode variar de zero por meio de seu valor de limite superior.</span><span class="sxs-lookup"><span data-stu-id="3855a-198">Each index can vary from zero through its upper bound value.</span></span>  
  
 <span data-ttu-id="3855a-199">As duas instruções a seguir são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="3855a-199">The following two statements are equivalent.</span></span> <span data-ttu-id="3855a-200">Cada instrução declara uma matriz de 21 `Integer` elementos.</span><span class="sxs-lookup"><span data-stu-id="3855a-200">Each statement declares an array of 21 `Integer` elements.</span></span> <span data-ttu-id="3855a-201">Quando você acessar a matriz, o índice pode variar de 0 a 20.</span><span class="sxs-lookup"><span data-stu-id="3855a-201">When you access the array, the index can vary from 0 through 20.</span></span>  
  
```vb  
Dim totals(20) As Integer  
Dim totals(0 To 20) As Integer  
```  
  
 <span data-ttu-id="3855a-202">A instrução a seguir declara uma matriz bidimensional de tipo `Double`.</span><span class="sxs-lookup"><span data-stu-id="3855a-202">The following statement declares a two-dimensional array of type `Double`.</span></span> <span data-ttu-id="3855a-203">A matriz tem 4 linhas (3 + 1) de 6 colunas (5 + 1).</span><span class="sxs-lookup"><span data-stu-id="3855a-203">The array has 4 rows (3 + 1) of 6 columns (5 + 1) each.</span></span> <span data-ttu-id="3855a-204">Observe que um limite superior representa o maior valor possível para o índice, não o comprimento da dimensão.</span><span class="sxs-lookup"><span data-stu-id="3855a-204">Note that an upper bound represents the highest possible value for the index, not the length of the dimension.</span></span> <span data-ttu-id="3855a-205">O comprimento da dimensão é o limite superior mais um.</span><span class="sxs-lookup"><span data-stu-id="3855a-205">The length of the dimension is the upper bound plus one.</span></span>  
  
```vb  
Dim matrix2(3, 5) As Double  
```  
  
 <span data-ttu-id="3855a-206">Uma matriz pode ter de 1 a 32 dimensões.</span><span class="sxs-lookup"><span data-stu-id="3855a-206">An array can have from 1 to 32 dimensions.</span></span>  
  
 <span data-ttu-id="3855a-207">Você pode deixar todos os limites em branco em uma declaração de matriz.</span><span class="sxs-lookup"><span data-stu-id="3855a-207">You can leave all the bounds blank in an array declaration.</span></span> <span data-ttu-id="3855a-208">Se você fizer isso, a matriz tem o número de dimensões que você especificar, mas ele não foi inicializado.</span><span class="sxs-lookup"><span data-stu-id="3855a-208">If you do this, the array has the number of dimensions you specify, but it is uninitialized.</span></span> <span data-ttu-id="3855a-209">Ele tem um valor de `Nothing` até que você inicializar pelo menos alguns de seus elementos.</span><span class="sxs-lookup"><span data-stu-id="3855a-209">It has a value of `Nothing` until you initialize at least some of its elements.</span></span> <span data-ttu-id="3855a-210">O `Dim` instrução deve especificar limites para todas as dimensões ou nenhuma dimensão.</span><span class="sxs-lookup"><span data-stu-id="3855a-210">The `Dim` statement must specify bounds either for all dimensions or for no dimensions.</span></span>  
  
```vb  
' Declare an array with blank array bounds.  
Dim messages() As String  
' Initialize the array.  
ReDim messages(4)  
```  
  
 <span data-ttu-id="3855a-211">Se a matriz tem mais de uma dimensão, você deve incluir vírgulas entre os parênteses para indicar o número de dimensões.</span><span class="sxs-lookup"><span data-stu-id="3855a-211">If the array has more than one dimension, you must include commas between the parentheses to indicate the number of dimensions.</span></span>  
  
```vb  
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte  
```  
  
 <span data-ttu-id="3855a-212">Você pode declarar uma *matriz de comprimento zero* declarando uma das dimensões da matriz para ser -1.</span><span class="sxs-lookup"><span data-stu-id="3855a-212">You can declare a *zero-length array* by declaring one of the array's dimensions to be -1.</span></span> <span data-ttu-id="3855a-213">Uma variável que contém uma matriz de comprimento zero não tem o valor `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="3855a-213">A variable that holds a zero-length array does not have the value `Nothing`.</span></span> <span data-ttu-id="3855a-214">Matrizes de comprimento zero são necessárias determinadas funções do common language runtime.</span><span class="sxs-lookup"><span data-stu-id="3855a-214">Zero-length arrays are required by certain common language runtime functions.</span></span> <span data-ttu-id="3855a-215">Se você tentar acessar essa matriz, ocorre uma exceção de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="3855a-215">If you try to access such an array, a runtime exception occurs.</span></span> <span data-ttu-id="3855a-216">Para obter mais informações, consulte [matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="3855a-216">For more information, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
 <span data-ttu-id="3855a-217">Você pode inicializar os valores de uma matriz, usando um literal de matriz.</span><span class="sxs-lookup"><span data-stu-id="3855a-217">You can initialize the values of an array by using an array literal.</span></span> <span data-ttu-id="3855a-218">Para fazer isso, coloque os valores de inicialização com colchetes (`{}`).</span><span class="sxs-lookup"><span data-stu-id="3855a-218">To do this, surround the initialization values with braces (`{}`).</span></span>  
  
```vb  
Dim longArray() As Long = {0, 1, 2, 3}  
```  
  
 <span data-ttu-id="3855a-219">Para matrizes multidimensionais, a inicialização para cada dimensão separada é colocada entre chaves na dimensão externa.</span><span class="sxs-lookup"><span data-stu-id="3855a-219">For multidimensional arrays, the initialization for each separate dimension is enclosed in braces in the outer dimension.</span></span> <span data-ttu-id="3855a-220">Os elementos são especificados na ordem de linhas principais.</span><span class="sxs-lookup"><span data-stu-id="3855a-220">The elements are specified in row-major order.</span></span>  
  
```vb  
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}  
```  
  
 <span data-ttu-id="3855a-221">Para obter mais informações sobre literais de matriz, consulte [matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="3855a-221">For more information about array literals, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
##  <a name="default"></a> <span data-ttu-id="3855a-222">Tipos de dados padrão e valores</span><span class="sxs-lookup"><span data-stu-id="3855a-222">Default Data Types and Values</span></span>  
 <span data-ttu-id="3855a-223">A tabela a seguir descreve os resultados de várias combinações de especificar o tipo de dados e o inicializador em uma instrução `Dim`.</span><span class="sxs-lookup"><span data-stu-id="3855a-223">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>  
  
|<span data-ttu-id="3855a-224">Tipo de dados especificado?</span><span class="sxs-lookup"><span data-stu-id="3855a-224">Data type specified?</span></span>|<span data-ttu-id="3855a-225">Inicializador especificado?</span><span class="sxs-lookup"><span data-stu-id="3855a-225">Initializer specified?</span></span>|<span data-ttu-id="3855a-226">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3855a-226">Example</span></span>|<span data-ttu-id="3855a-227">Resultado</span><span class="sxs-lookup"><span data-stu-id="3855a-227">Result</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="3855a-228">Não</span><span class="sxs-lookup"><span data-stu-id="3855a-228">No</span></span>|<span data-ttu-id="3855a-229">Não</span><span class="sxs-lookup"><span data-stu-id="3855a-229">No</span></span>|`Dim qty`|<span data-ttu-id="3855a-230">Se [Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) está desativado (padrão), a variável é definida como `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="3855a-230">If [Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="3855a-231">Se `Option Strict` estiver ativado, ocorre um erro de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="3855a-231">If `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="3855a-232">Não</span><span class="sxs-lookup"><span data-stu-id="3855a-232">No</span></span>|<span data-ttu-id="3855a-233">Sim</span><span class="sxs-lookup"><span data-stu-id="3855a-233">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="3855a-234">Se [Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) está on (o padrão), a variável usa os dados de tipo do inicializador.</span><span class="sxs-lookup"><span data-stu-id="3855a-234">If [Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="3855a-235">Consulte [inferência de tipo Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="3855a-235">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="3855a-236">Se `Option Infer` estiver desativado e `Option Strict` estiver desativado, a variável usa o tipo de dados do `Object`.</span><span class="sxs-lookup"><span data-stu-id="3855a-236">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="3855a-237">Se `Option Infer` estiver desativado e `Option Strict` estiver ativado, ocorre um erro de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="3855a-237">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="3855a-238">Sim</span><span class="sxs-lookup"><span data-stu-id="3855a-238">Yes</span></span>|<span data-ttu-id="3855a-239">Não</span><span class="sxs-lookup"><span data-stu-id="3855a-239">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="3855a-240">A variável é inicializada para o valor padrão para o tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="3855a-240">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="3855a-241">Consulte a tabela mais adiante nesta seção.</span><span class="sxs-lookup"><span data-stu-id="3855a-241">See the table later in this section.</span></span>|  
|<span data-ttu-id="3855a-242">Sim</span><span class="sxs-lookup"><span data-stu-id="3855a-242">Yes</span></span>|<span data-ttu-id="3855a-243">Sim</span><span class="sxs-lookup"><span data-stu-id="3855a-243">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="3855a-244">Se o tipo de dados do inicializador não for conversível para o tipo de dados especificado, ocorrerá um erro de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="3855a-244">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|  
  
 <span data-ttu-id="3855a-245">Se você especificar um tipo de dados, mas não especificar um inicializador, Visual Basic inicializa a variável para o valor padrão para seu tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="3855a-245">If you specify a data type but do not specify an initializer, Visual Basic initializes the variable to the default value for its data type.</span></span> <span data-ttu-id="3855a-246">A tabela a seguir mostra o padrão de valores de inicialização.</span><span class="sxs-lookup"><span data-stu-id="3855a-246">The following table shows the default initialization values.</span></span>  
  
|<span data-ttu-id="3855a-247">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="3855a-247">Data type</span></span>|<span data-ttu-id="3855a-248">Valor padrão</span><span class="sxs-lookup"><span data-stu-id="3855a-248">Default value</span></span>|  
|---|---|  
|<span data-ttu-id="3855a-249">Todos os tipos numéricos (incluindo `Byte` e `SByte`)</span><span class="sxs-lookup"><span data-stu-id="3855a-249">All numeric types (including `Byte` and `SByte`)</span></span>|<span data-ttu-id="3855a-250">0</span><span class="sxs-lookup"><span data-stu-id="3855a-250">0</span></span>|  
|`Char`|<span data-ttu-id="3855a-251">0 binário</span><span class="sxs-lookup"><span data-stu-id="3855a-251">Binary 0</span></span>|  
|<span data-ttu-id="3855a-252">Todos os tipos de referência (incluindo `Object`, `String`e todas as matrizes)</span><span class="sxs-lookup"><span data-stu-id="3855a-252">All reference types (including `Object`, `String`, and all arrays)</span></span>|`Nothing`|  
|`Boolean`|`False`|  
|`Date`|<span data-ttu-id="3855a-253">12:00 AM de 1º de janeiro do ano 1 (01/01/0001 12:00:00 AM)</span><span class="sxs-lookup"><span data-stu-id="3855a-253">12:00 AM of January 1 of the year 1 (01/01/0001 12:00:00 AM)</span></span>|  
  
 <span data-ttu-id="3855a-254">Cada elemento de uma estrutura é inicializado como se fosse uma variável separada.</span><span class="sxs-lookup"><span data-stu-id="3855a-254">Each element of a structure is initialized as if it were a separate variable.</span></span> <span data-ttu-id="3855a-255">Se você declara o comprimento de uma matriz, mas não inicializar seus elementos, cada elemento é inicializado como se fosse uma variável separada.</span><span class="sxs-lookup"><span data-stu-id="3855a-255">If you declare the length of an array but do not initialize its elements, each element is initialized as if it were a separate variable.</span></span>  
  
## <a name="static-local-variable-lifetime"></a><span data-ttu-id="3855a-256">Vida útil variável Local estática</span><span class="sxs-lookup"><span data-stu-id="3855a-256">Static Local Variable Lifetime</span></span>  
 <span data-ttu-id="3855a-257">Um `Static` variável local tem um tempo de vida mais longo do que o procedimento no qual ela é declarada.</span><span class="sxs-lookup"><span data-stu-id="3855a-257">A `Static` local variable has a longer lifetime than that of the procedure in which it is declared.</span></span> <span data-ttu-id="3855a-258">Os limites de tempo de vida da variável dependem de onde o procedimento é declarado e se ela é `Shared`.</span><span class="sxs-lookup"><span data-stu-id="3855a-258">The boundaries of the variable's lifetime depend on where the procedure is declared and whether it is `Shared`.</span></span>  
  
|<span data-ttu-id="3855a-259">Declaração de procedimento</span><span class="sxs-lookup"><span data-stu-id="3855a-259">Procedure declaration</span></span>|<span data-ttu-id="3855a-260">Variável inicializada</span><span class="sxs-lookup"><span data-stu-id="3855a-260">Variable initialized</span></span>|<span data-ttu-id="3855a-261">Variável interrompe existente</span><span class="sxs-lookup"><span data-stu-id="3855a-261">Variable stops existing</span></span>|  
|---|---|---|  
|<span data-ttu-id="3855a-262">Em um módulo</span><span class="sxs-lookup"><span data-stu-id="3855a-262">In a module</span></span>|<span data-ttu-id="3855a-263">Na primeira vez em que o procedimento é chamado.</span><span class="sxs-lookup"><span data-stu-id="3855a-263">The first time the procedure is called</span></span>|<span data-ttu-id="3855a-264">Quando o programa para a execução</span><span class="sxs-lookup"><span data-stu-id="3855a-264">When your program stops execution</span></span>|  
|<span data-ttu-id="3855a-265">Em uma classe ou estrutura, o procedimento é `Shared`</span><span class="sxs-lookup"><span data-stu-id="3855a-265">In a class or structure, procedure is `Shared`</span></span>|<span data-ttu-id="3855a-266">Na primeira vez que o procedimento é chamado em uma instância específica ou na classe ou estrutura em si</span><span class="sxs-lookup"><span data-stu-id="3855a-266">The first time the procedure is called either on a specific instance or on the class or structure itself</span></span>|<span data-ttu-id="3855a-267">Quando o programa para a execução</span><span class="sxs-lookup"><span data-stu-id="3855a-267">When your program stops execution</span></span>|  
|<span data-ttu-id="3855a-268">Em uma classe ou estrutura, o procedimento não é `Shared`</span><span class="sxs-lookup"><span data-stu-id="3855a-268">In a class or structure, procedure isn't `Shared`</span></span>|<span data-ttu-id="3855a-269">Na primeira vez em que o procedimento é chamado em uma instância específica</span><span class="sxs-lookup"><span data-stu-id="3855a-269">The first time the procedure is called on a specific instance</span></span>|<span data-ttu-id="3855a-270">Quando a instância é liberada para coleta de lixo (GC)</span><span class="sxs-lookup"><span data-stu-id="3855a-270">When the instance is released for garbage collection (GC)</span></span>|  
  
## <a name="attributes-and-modifiers"></a><span data-ttu-id="3855a-271">Modificadores e atributos</span><span class="sxs-lookup"><span data-stu-id="3855a-271">Attributes and Modifiers</span></span>  
 <span data-ttu-id="3855a-272">Você pode aplicar atributos apenas para variáveis de membro, não para variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="3855a-272">You can apply attributes only to member variables, not to local variables.</span></span> <span data-ttu-id="3855a-273">Um atributo contribui com informações para metadados do assembly, que não é significativo para armazenamento temporário, como variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="3855a-273">An attribute contributes information to the assembly's metadata, which is not meaningful for temporary storage such as local variables.</span></span>  
  
 <span data-ttu-id="3855a-274">No nível de módulo, você não pode usar o `Static` modificador para declarar variáveis de membro.</span><span class="sxs-lookup"><span data-stu-id="3855a-274">At module level, you cannot use the `Static` modifier to declare member variables.</span></span> <span data-ttu-id="3855a-275">No nível de procedimento, você não pode usar `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, ou qualquer modificador de acesso para declarar variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="3855a-275">At procedure level, you cannot use `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, or any access modifiers to declare local variables.</span></span>  
  
 <span data-ttu-id="3855a-276">Você pode especificar qual código pode acessar uma variável, fornecendo um `accessmodifier`.</span><span class="sxs-lookup"><span data-stu-id="3855a-276">You can specify what code can access a variable by supplying an `accessmodifier`.</span></span> <span data-ttu-id="3855a-277">Classe e o módulo membro padrão de variáveis (fora de qualquer procedimento) para acesso privado e padrão de variáveis de membro de estrutura para acesso público.</span><span class="sxs-lookup"><span data-stu-id="3855a-277">Class and module member variables (outside any procedure) default to private access, and structure member variables default to public access.</span></span> <span data-ttu-id="3855a-278">Você pode ajustar os níveis de acesso com os modificadores de acesso.</span><span class="sxs-lookup"><span data-stu-id="3855a-278">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="3855a-279">Você não pode usar os modificadores de acesso em variáveis locais (dentro de um procedimento).</span><span class="sxs-lookup"><span data-stu-id="3855a-279">You cannot use access modifiers on local variables (inside a procedure).</span></span>  
  
 <span data-ttu-id="3855a-280">Você pode especificar `WithEvents` somente em variáveis de membro, não em variáveis locais dentro de um procedimento.</span><span class="sxs-lookup"><span data-stu-id="3855a-280">You can specify `WithEvents` only on member variables, not on local variables inside a procedure.</span></span> <span data-ttu-id="3855a-281">Se você especificar `WithEvents`, o tipo de dados da variável deve ser um tipo de classe específica, não `Object`.</span><span class="sxs-lookup"><span data-stu-id="3855a-281">If you specify `WithEvents`, the data type of the variable must be a specific class type, not `Object`.</span></span> <span data-ttu-id="3855a-282">Você não pode declarar uma matriz com `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="3855a-282">You cannot declare an array with `WithEvents`.</span></span> <span data-ttu-id="3855a-283">Para obter mais informações sobre eventos, consulte [eventos](../../../visual-basic/programming-guide/language-features/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="3855a-283">For more information about events, see [Events](../../../visual-basic/programming-guide/language-features/events/index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3855a-284">Código fora de uma classe, estrutura ou o módulo deve qualificar o nome de uma variável membro com o nome da classe, estrutura ou módulo.</span><span class="sxs-lookup"><span data-stu-id="3855a-284">Code outside a class, structure, or module must qualify a member variable's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="3855a-285">Código fora de que um procedimento ou bloco não pode se referir a todas as variáveis locais dentro desse procedimento ou bloco.</span><span class="sxs-lookup"><span data-stu-id="3855a-285">Code outside a procedure or block cannot refer to any local variables within that procedure or block.</span></span>  
  
## <a name="releasing-managed-resources"></a><span data-ttu-id="3855a-286">Liberar recursos gerenciados</span><span class="sxs-lookup"><span data-stu-id="3855a-286">Releasing Managed Resources</span></span>  
 <span data-ttu-id="3855a-287">O coletor de lixo do .NET Framework libera os recursos gerenciados sem qualquer codificação extra de sua parte.</span><span class="sxs-lookup"><span data-stu-id="3855a-287">The .NET Framework garbage collector disposes of managed resources without any extra coding on your part.</span></span> <span data-ttu-id="3855a-288">No entanto, você pode forçar o descarte de um recurso gerenciado em vez de esperar o coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="3855a-288">However, you can force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>  
  
 <span data-ttu-id="3855a-289">Se uma classe mantiver um recurso particularmente importante e escasso (como um identificador de arquivo ou a conexão de banco de dados), não convém esperar até a próxima coleta de lixo para limpar uma instância da classe que não está mais em uso.</span><span class="sxs-lookup"><span data-stu-id="3855a-289">If a class holds onto a particularly valuable and scarce resource (such as a database connection or file handle), you might not want to wait until the next garbage collection to clean up a class instance that's no longer in use.</span></span> <span data-ttu-id="3855a-290">Uma classe pode implementar o <xref:System.IDisposable> interface para fornecer uma maneira para liberar recursos antes de uma coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="3855a-290">A class may implement the <xref:System.IDisposable> interface to provide a way to release resources before a garbage collection.</span></span> <span data-ttu-id="3855a-291">Uma classe que implementa essa interface expõe um `Dispose` método que pode ser chamado para forçar valiosos recursos sejam liberados imediatamente.</span><span class="sxs-lookup"><span data-stu-id="3855a-291">A class that implements that interface exposes a `Dispose` method that can be called to force valuable resources to be released immediately.</span></span>  
  
 <span data-ttu-id="3855a-292">O `Using` instrução automatiza o processo de aquisição de um recurso, executando um conjunto de instruções e, em seguida, descarte do recurso.</span><span class="sxs-lookup"><span data-stu-id="3855a-292">The `Using` statement automates the process of acquiring a resource, executing a set of statements, and then disposing of the resource.</span></span> <span data-ttu-id="3855a-293">No entanto, o recurso deve implementar o <xref:System.IDisposable> interface.</span><span class="sxs-lookup"><span data-stu-id="3855a-293">However, the resource must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="3855a-294">Para obter mais informações, consulte [Instrução using](../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3855a-294">For more information, see [Using Statement](../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3855a-295">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3855a-295">Example</span></span>  
 <span data-ttu-id="3855a-296">O exemplo a seguir declara variáveis usando a `Dim` instrução com várias opções.</span><span class="sxs-lookup"><span data-stu-id="3855a-296">The following example declares variables by using the `Dim` statement with various options.</span></span>  
  
 [!code-vb[VbVbalrStatements#141](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="3855a-297">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3855a-297">Example</span></span>  
 <span data-ttu-id="3855a-298">O exemplo a seguir lista os números primos entre 1 e 30.</span><span class="sxs-lookup"><span data-stu-id="3855a-298">The following example lists the prime numbers between 1 and 30.</span></span> <span data-ttu-id="3855a-299">O escopo de variáveis locais é descrito nos comentários de código.</span><span class="sxs-lookup"><span data-stu-id="3855a-299">The scope of local variables is described in code comments.</span></span>  
  
 [!code-vb[VbVbalrStatements#142](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="3855a-300">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3855a-300">Example</span></span>  
 <span data-ttu-id="3855a-301">No exemplo a seguir, o `speedValue` variável é declarada no nível de classe.</span><span class="sxs-lookup"><span data-stu-id="3855a-301">In the following example, the `speedValue` variable is declared at the class level.</span></span> <span data-ttu-id="3855a-302">O `Private` palavra-chave é usada para declarar a variável.</span><span class="sxs-lookup"><span data-stu-id="3855a-302">The `Private` keyword is used to declare the variable.</span></span> <span data-ttu-id="3855a-303">A variável pode ser acessada por qualquer procedimento de `Car` classe.</span><span class="sxs-lookup"><span data-stu-id="3855a-303">The variable can be accessed by any procedure in the `Car` class.</span></span>  
  
 [!code-vb[VbVbalrStatements#144](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_3.vb)]  
  
 [!code-vb[VbVbalrStatements#145](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="3855a-304">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3855a-304">See Also</span></span>  
 [<span data-ttu-id="3855a-305">Instrução Const</span><span class="sxs-lookup"><span data-stu-id="3855a-305">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
 [<span data-ttu-id="3855a-306">Instrução ReDim</span><span class="sxs-lookup"><span data-stu-id="3855a-306">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="3855a-307">Instrução Option Explicit</span><span class="sxs-lookup"><span data-stu-id="3855a-307">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [<span data-ttu-id="3855a-308">Instrução Option Infer</span><span class="sxs-lookup"><span data-stu-id="3855a-308">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [<span data-ttu-id="3855a-309">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="3855a-309">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="3855a-310">Página de Compilação, Designer de Projeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3855a-310">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)  
 [<span data-ttu-id="3855a-311">Declaração de Variável</span><span class="sxs-lookup"><span data-stu-id="3855a-311">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="3855a-312">Matrizes</span><span class="sxs-lookup"><span data-stu-id="3855a-312">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="3855a-313">Inicializadores de objeto: tipos nomeados e anônimos</span><span class="sxs-lookup"><span data-stu-id="3855a-313">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [<span data-ttu-id="3855a-314">Tipos Anônimos</span><span class="sxs-lookup"><span data-stu-id="3855a-314">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [<span data-ttu-id="3855a-315">Inicializadores de objeto: tipos nomeados e anônimos</span><span class="sxs-lookup"><span data-stu-id="3855a-315">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [<span data-ttu-id="3855a-316">Como declarar um objeto usando um inicializador de objeto</span><span class="sxs-lookup"><span data-stu-id="3855a-316">How to: Declare an Object by Using an Object Initializer</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)  
 [<span data-ttu-id="3855a-317">Inferência de Tipo de Variável Local</span><span class="sxs-lookup"><span data-stu-id="3855a-317">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
