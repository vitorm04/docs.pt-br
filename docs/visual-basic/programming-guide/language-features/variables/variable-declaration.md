---
title: "Declaração de variável no Visual Basic | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- variables [Visual Basic], declaring
- member variables, declarations
- Dim statement, variable declaration
- declaring variables
- variables [Visual Basic], scope
- variables [Visual Basic], data types
- data types [Visual Basic], variable declarations
- lifetime, variables
- variables [Visual Basic], lifetime
- access levels, variables
- scope, declaration statements
- variables [Visual Basic], access level
- local variables, declarations
- scope, variables
ms.assetid: d8f10226-92b1-480f-9f53-df377b2d7e15
caps.latest.revision: 31
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: dac536b99eb4515c75381dc4e28720a92e1001f0
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="variable-declaration-in-visual-basic"></a><span data-ttu-id="0db0d-102">Declaração de variável no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0db0d-102">Variable Declaration in Visual Basic</span></span>
<span data-ttu-id="0db0d-103">Você declara uma variável para especificar seu nome e suas características.</span><span class="sxs-lookup"><span data-stu-id="0db0d-103">You declare a variable to specify its name and characteristics.</span></span> <span data-ttu-id="0db0d-104">A instrução de declaração para variáveis é a [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0db0d-104">The declaration statement for variables is the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="0db0d-105">Sua localização e conteúdo determinam as características da variável.</span><span class="sxs-lookup"><span data-stu-id="0db0d-105">Its location and contents determine the variable's characteristics.</span></span>  
  
 <span data-ttu-id="0db0d-106">Para regras de nomenclatura de variáveis e considerações, consulte [nomes de elemento declarado](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="0db0d-106">For variable naming rules and considerations, see [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="declaration-levels"></a><span data-ttu-id="0db0d-107">Níveis de declaração</span><span class="sxs-lookup"><span data-stu-id="0db0d-107">Declaration Levels</span></span>  
  
### <a name="local-and-member-variables"></a><span data-ttu-id="0db0d-108">Local e variáveis de membro</span><span class="sxs-lookup"><span data-stu-id="0db0d-108">Local and Member Variables</span></span>  
 <span data-ttu-id="0db0d-109">A *variável local* é aquela declarada dentro de um procedimento.</span><span class="sxs-lookup"><span data-stu-id="0db0d-109">A *local variable* is one that is declared within a procedure.</span></span> <span data-ttu-id="0db0d-110">A *variável de membro* é um membro de um [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] digite; ela é declarada no nível de módulo, dentro de uma classe, estrutura ou módulo, mas não dentro de qualquer procedimento interno para essa classe, estrutura ou módulo.</span><span class="sxs-lookup"><span data-stu-id="0db0d-110">A *member variable* is a member of a [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] type; it is declared at module level, inside a class, structure, or module, but not within any procedure internal to that class, structure, or module.</span></span>  
  
### <a name="shared-and-instance-variables"></a><span data-ttu-id="0db0d-111">Compartilhado e variáveis de instância</span><span class="sxs-lookup"><span data-stu-id="0db0d-111">Shared and Instance Variables</span></span>  
 <span data-ttu-id="0db0d-112">Em uma classe ou estrutura, a categoria de uma variável de membro depende se ela é compartilhada.</span><span class="sxs-lookup"><span data-stu-id="0db0d-112">In a class or structure, the category of a member variable depends on whether or not it is shared.</span></span> <span data-ttu-id="0db0d-113">Se ela for declarada com a [compartilhado](../../../../visual-basic/language-reference/modifiers/shared.md) , é um *variável compartilhada*, e existe em uma única cópia compartilhada entre todas as instâncias da classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="0db0d-113">If it is declared with the [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) keyword, it is a *shared variable*, and it exists in a single copy shared among all instances of the class or structure.</span></span>  
  
 <span data-ttu-id="0db0d-114">Caso contrário, será uma *variável de instância*, e uma cópia separada é criada para cada instância da classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="0db0d-114">Otherwise it is an *instance variable*, and a separate copy of it is created for each instance of the class or structure.</span></span> <span data-ttu-id="0db0d-115">Uma cópia determinada de uma variável de instância está disponível somente para a instância da classe ou estrutura na qual ele foi criado.</span><span class="sxs-lookup"><span data-stu-id="0db0d-115">A given copy of an instance variable is available only to the instance of the class or structure in which it was created.</span></span> <span data-ttu-id="0db0d-116">Isso é independente de uma cópia da variável de instância em qualquer outra instância da classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="0db0d-116">It is independent of a copy of the instance variable in any other instance of the class or structure.</span></span>  
  
## <a name="declaring-data-type"></a><span data-ttu-id="0db0d-117">Declarar o tipo de dados</span><span class="sxs-lookup"><span data-stu-id="0db0d-117">Declaring Data Type</span></span>  
 <span data-ttu-id="0db0d-118">O [como](../../../../visual-basic/language-reference/statements/as-clause.md) cláusula na instrução de declaração permite que você defina o tipo de dados ou tipo de objeto da variável que é declarado.</span><span class="sxs-lookup"><span data-stu-id="0db0d-118">The [As](../../../../visual-basic/language-reference/statements/as-clause.md) clause in the declaration statement allows you to define the data type or object type of the variable you are declaring.</span></span> <span data-ttu-id="0db0d-119">Você pode especificar qualquer um dos seguintes tipos para uma variável:</span><span class="sxs-lookup"><span data-stu-id="0db0d-119">You can specify any of the following types for a variable:</span></span>  
  
-   <span data-ttu-id="0db0d-120">Digite um dados elementar, como `Boolean`, `Long`, ou`Decimal`</span><span class="sxs-lookup"><span data-stu-id="0db0d-120">An elementary data type, such as `Boolean`, `Long`, or `Decimal`</span></span>  
  
-   <span data-ttu-id="0db0d-121">Um tipo de dados compostos, como uma matriz ou estrutura</span><span class="sxs-lookup"><span data-stu-id="0db0d-121">A composite data type, such as an array or structure</span></span>  
  
-   <span data-ttu-id="0db0d-122">Um tipo de objeto ou classe, definida em seu aplicativo ou em outro aplicativo</span><span class="sxs-lookup"><span data-stu-id="0db0d-122">An object type, or class, defined either in your application or in another application</span></span>  
  
-   <span data-ttu-id="0db0d-123">A [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] classe, como <xref:System.Windows.Forms.Label>ou <xref:System.Windows.Forms.TextBox></xref:System.Windows.Forms.TextBox> </xref:System.Windows.Forms.Label></span><span class="sxs-lookup"><span data-stu-id="0db0d-123">A [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] class, such as <xref:System.Windows.Forms.Label> or <xref:System.Windows.Forms.TextBox></span></span>  
  
-   <span data-ttu-id="0db0d-124">Tipo de uma interface, como <xref:System.IComparable>ou <xref:System.IDisposable></xref:System.IDisposable> </xref:System.IComparable></span><span class="sxs-lookup"><span data-stu-id="0db0d-124">An interface type, such as <xref:System.IComparable> or <xref:System.IDisposable></span></span>  
  
 <span data-ttu-id="0db0d-125">Você pode declarar diversas variáveis em uma instrução sem a necessidade de repetir o tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="0db0d-125">You can declare several variables in one statement without having to repeat the data type.</span></span> <span data-ttu-id="0db0d-126">Nas instruções a seguir, as variáveis `i`, `j`, e `k` são declaradas como tipo `Integer`, `l` e `m` como `Long`, e `x` e `y` como `Single`:</span><span class="sxs-lookup"><span data-stu-id="0db0d-126">In the following statements, the variables `i`, `j`, and `k` are declared as type `Integer`, `l` and `m` as `Long`, and `x` and `y` as `Single`:</span></span>  
  
```  
Dim i, j, k As Integer  
' All three variables in the preceding statement are declared as Integer.  
Dim l, m As Long, x, y As Single  
' In the preceding statement, l and m are Long, x and y are Single.  
```  
  
 <span data-ttu-id="0db0d-127">Para obter mais informações sobre tipos de dados, consulte [tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="0db0d-127">For more information on data types, see [Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md).</span></span> <span data-ttu-id="0db0d-128">Para obter mais informações sobre objetos, consulte [objetos e Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) e [Programando com componentes](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3).</span><span class="sxs-lookup"><span data-stu-id="0db0d-128">For more information on objects, see [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) and [Programming with Components](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3).</span></span>  
  
## <a name="local-type-inference"></a><span data-ttu-id="0db0d-129">Inferência de tipo local</span><span class="sxs-lookup"><span data-stu-id="0db0d-129">Local Type Inference</span></span>  
 <span data-ttu-id="0db0d-130">*Inferência de tipo* é usado para determinar os tipos de dados de variáveis locais declarados sem um `As` cláusula.</span><span class="sxs-lookup"><span data-stu-id="0db0d-130">*Type inference* is used to determine the data types of local variables declared without an `As` clause.</span></span> <span data-ttu-id="0db0d-131">O compilador infere o tipo da variável do tipo da expressão de inicialização.</span><span class="sxs-lookup"><span data-stu-id="0db0d-131">The compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="0db0d-132">Isso permite que você declarar variáveis sem indicar um tipo explicitamente.</span><span class="sxs-lookup"><span data-stu-id="0db0d-132">This enables you to declare variables without explicitly stating a type.</span></span> <span data-ttu-id="0db0d-133">No exemplo a seguir, ambos `num1` e `num2` são fortemente tipadas como inteiros.</span><span class="sxs-lookup"><span data-stu-id="0db0d-133">In the following example, both `num1` and `num2` are strongly typed as integers.</span></span>  
  
 <span data-ttu-id="0db0d-134">[!code-vb[VbVbalrTypeInference n º&1;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/variable-declaration_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="0db0d-134">[!code-vb[VbVbalrTypeInference#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/variable-declaration_1.vb)]</span></span>  
  
 <span data-ttu-id="0db0d-135">Se você quiser usar inferência de tipo local, `Option Infer` deve ser definido como `On`.</span><span class="sxs-lookup"><span data-stu-id="0db0d-135">If you want to use local type inference, `Option Infer` must be set to `On`.</span></span> <span data-ttu-id="0db0d-136">Para obter mais informações, consulte [inferência de tipo Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) e [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0db0d-136">For more information, see [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) and [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span></span>  
  
## <a name="characteristics-of-declared-variables"></a><span data-ttu-id="0db0d-137">Características de variáveis declaradas</span><span class="sxs-lookup"><span data-stu-id="0db0d-137">Characteristics of Declared Variables</span></span>  
 <span data-ttu-id="0db0d-138">O *tempo de vida* de uma variável é o período de tempo durante o qual ele está disponível para uso.</span><span class="sxs-lookup"><span data-stu-id="0db0d-138">The *lifetime* of a variable is the period of time during which it is available for use.</span></span> <span data-ttu-id="0db0d-139">Em geral, existe uma variável como o elemento que declara (por exemplo, um procedimento ou classe) continua a existir.</span><span class="sxs-lookup"><span data-stu-id="0db0d-139">In general, a variable exists as long as the element that declares it (such as a procedure or class) continues to exist.</span></span> <span data-ttu-id="0db0d-140">Se a variável não precisa continuar existindo além do tempo de vida do elemento que a contém, você não precisa fazer nada especial na declaração.</span><span class="sxs-lookup"><span data-stu-id="0db0d-140">If the variable does not need to continue existing beyond the lifetime of its containing element, you do not need to do anything special in the declaration.</span></span> <span data-ttu-id="0db0d-141">Se a variável precisa continuar existindo mais que o elemento que contém, você pode incluir o `Static` ou `Shared` palavra-chave em seu `Dim` instrução.</span><span class="sxs-lookup"><span data-stu-id="0db0d-141">If the variable needs to continue to exist longer than its containing element, you can include the `Static` or `Shared` keyword in its `Dim` statement.</span></span> <span data-ttu-id="0db0d-142">Para obter mais informações, consulte [tempo de vida no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).</span><span class="sxs-lookup"><span data-stu-id="0db0d-142">For more information, see [Lifetime in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).</span></span>  
  
 <span data-ttu-id="0db0d-143">O *escopo* de uma variável é o conjunto de todo o código que pode fazer referência a ele sem qualificar seu nome.</span><span class="sxs-lookup"><span data-stu-id="0db0d-143">The *scope* of a variable is the set of all code that can refer to it without qualifying its name.</span></span> <span data-ttu-id="0db0d-144">Escopo de uma variável é determinado por onde ela é declarada.</span><span class="sxs-lookup"><span data-stu-id="0db0d-144">A variable's scope is determined by where it is declared.</span></span> <span data-ttu-id="0db0d-145">Código localizado em uma região determinada pode usar as variáveis definidas naquela região sem ter que qualificar seus nomes.</span><span class="sxs-lookup"><span data-stu-id="0db0d-145">Code located in a given region can use the variables defined in that region without having to qualify their names.</span></span> <span data-ttu-id="0db0d-146">Para obter mais informações, consulte [escopo no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span><span class="sxs-lookup"><span data-stu-id="0db0d-146">For more information, see [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span></span>  
  
 <span data-ttu-id="0db0d-147">Uma variável *nível de acesso* é a extensão de código que tenha permissão para acessá-lo.</span><span class="sxs-lookup"><span data-stu-id="0db0d-147">A variable's *access level* is the extent of code that has permission to access it.</span></span> <span data-ttu-id="0db0d-148">Isso é determinado pelo modificador de acesso (como [pública](../../../../visual-basic/language-reference/modifiers/public.md) ou [particular](../../../../visual-basic/language-reference/modifiers/private.md)) que você usar o `Dim` instrução.</span><span class="sxs-lookup"><span data-stu-id="0db0d-148">This is determined by the access modifier (such as [Public](../../../../visual-basic/language-reference/modifiers/public.md) or [Private](../../../../visual-basic/language-reference/modifiers/private.md)) that you use in the `Dim` statement.</span></span> <span data-ttu-id="0db0d-149">Para obter mais informações, consulte [níveis de acesso no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="0db0d-149">For more information, see [Access Levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0db0d-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0db0d-150">See Also</span></span>  
 <span data-ttu-id="0db0d-151">[Como: criar uma nova variável](../../../../visual-basic/programming-guide/language-features/variables/how-to-create-a-new-variable.md) </span><span class="sxs-lookup"><span data-stu-id="0db0d-151">[How to: Create a New Variable](../../../../visual-basic/programming-guide/language-features/variables/how-to-create-a-new-variable.md) </span></span>  
<span data-ttu-id="0db0d-152"> [Como: mover dados dentro e fora de uma variável](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md) </span><span class="sxs-lookup"><span data-stu-id="0db0d-152"> [How to: Move Data Into and Out of a Variable](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md) </span></span>  
<span data-ttu-id="0db0d-153"> [Tipos de dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="0db0d-153"> [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="0db0d-154"> [Protegido](../../../../visual-basic/language-reference/modifiers/protected.md) </span><span class="sxs-lookup"><span data-stu-id="0db0d-154"> [Protected](../../../../visual-basic/language-reference/modifiers/protected.md) </span></span>  
<span data-ttu-id="0db0d-155"> [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) </span><span class="sxs-lookup"><span data-stu-id="0db0d-155"> [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) </span></span>  
<span data-ttu-id="0db0d-156"> [Estático](../../../../visual-basic/language-reference/modifiers/static.md) </span><span class="sxs-lookup"><span data-stu-id="0db0d-156"> [Static](../../../../visual-basic/language-reference/modifiers/static.md) </span></span>  
<span data-ttu-id="0db0d-157"> [Características do elemento declarado](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md) </span><span class="sxs-lookup"><span data-stu-id="0db0d-157"> [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md) </span></span>  
<span data-ttu-id="0db0d-158"> [Inferência de tipo local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span><span class="sxs-lookup"><span data-stu-id="0db0d-158"> [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span></span>  
<span data-ttu-id="0db0d-159"> [Instrução Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md)</span><span class="sxs-lookup"><span data-stu-id="0db0d-159"> [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md)</span></span>
