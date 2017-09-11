---
title: Procedimentos no Visual Basic
ms.custom: 
ms.date: 2017-04-28
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- procedures, structured code
- Visual Basic code, procedures
- procedures, types of
- structured code, procedures
- procedures
ms.assetid: 9effbcf0-80a0-4d1a-98f4-2c6920592766
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: fd1a369ecfc1fa23cba694941fa47ab872ca1368
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="procedures-in-visual-basic"></a><span data-ttu-id="e852a-102">Procedimentos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e852a-102">Procedures in Visual Basic</span></span>
<span data-ttu-id="e852a-103">Um *procedimento* é um bloco de demonstrativos [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] incluídos por um demonstrativo de declaração (`Function`, `Sub`, `Operator`, `Get`, `Set`) e por uma declaração `End` de correspondência.</span><span class="sxs-lookup"><span data-stu-id="e852a-103">A *procedure* is a block of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] statements enclosed by a declaration statement (`Function`, `Sub`, `Operator`, `Get`, `Set`) and a matching `End` declaration.</span></span> <span data-ttu-id="e852a-104">Todos os demonstrativos executáveis em [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] devem estar incluídos em algum procedimento.</span><span class="sxs-lookup"><span data-stu-id="e852a-104">All executable statements in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] must be within some procedure.</span></span>  
  
## <a name="calling-a-procedure"></a><span data-ttu-id="e852a-105">Chamar um procedimento</span><span class="sxs-lookup"><span data-stu-id="e852a-105">Calling a Procedure</span></span>  
 <span data-ttu-id="e852a-106">Você invoca um procedimento de algum outro lugar no código.</span><span class="sxs-lookup"><span data-stu-id="e852a-106">You invoke a procedure from some other place in the code.</span></span> <span data-ttu-id="e852a-107">Isso é conhecido como uma *chamada de procedimento*.</span><span class="sxs-lookup"><span data-stu-id="e852a-107">This is known as a *procedure call*.</span></span> <span data-ttu-id="e852a-108">Quando a execução do procedimento termina, ele retorna o controle para o código que o invocou, que é conhecido como o *código de chamada*.</span><span class="sxs-lookup"><span data-stu-id="e852a-108">When the procedure is finished running, it returns control to the code that invoked it, which is known as the *calling code*.</span></span> <span data-ttu-id="e852a-109">O código de chamada é um demonstrativo, ou uma expressão incluída em um demonstrativo, que especifica o procedimento pelo nome e transfere o controle a ele.</span><span class="sxs-lookup"><span data-stu-id="e852a-109">The calling code is a statement, or an expression within a statement, that specifies the procedure by name and transfers control to it.</span></span>  
  
## <a name="returning-from-a-procedure"></a><span data-ttu-id="e852a-110">Retorno de um procedimento</span><span class="sxs-lookup"><span data-stu-id="e852a-110">Returning from a Procedure</span></span>  
 <span data-ttu-id="e852a-111">Um procedimento retorna o controle ao código de chamada quando termina a execução.</span><span class="sxs-lookup"><span data-stu-id="e852a-111">A procedure returns control to the calling code when it has finished running.</span></span> <span data-ttu-id="e852a-112">Para fazer isso, ele pode usar um [Demonstrativo de Retorno](../../../../visual-basic/language-reference/statements/return-statement.md), o [Demonstrativo de Saída](../../../../visual-basic/language-reference/statements/exit-statement.md) apropriado para o procedimento ou o demonstrativo [Final \<Palavra-chave > Demonstrativo](../../../../visual-basic/language-reference/statements/end-keyword-statement.md) do procedimento.</span><span class="sxs-lookup"><span data-stu-id="e852a-112">To do this, it can use a [Return Statement](../../../../visual-basic/language-reference/statements/return-statement.md), the appropriate [Exit Statement](../../../../visual-basic/language-reference/statements/exit-statement.md) statement for the procedure, or the procedure's [End \<keyword> Statement](../../../../visual-basic/language-reference/statements/end-keyword-statement.md) statement.</span></span> <span data-ttu-id="e852a-113">O controle, então, é transmitido para o código de chamada, seguindo o ponto da chamada de procedimento.</span><span class="sxs-lookup"><span data-stu-id="e852a-113">Control then passes to the calling code following the point of the procedure call.</span></span>  
  
-   <span data-ttu-id="e852a-114">Com um demonstrativo `Return`, o controle retorna imediatamente para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="e852a-114">With a `Return` statement, control returns immediately to the calling code.</span></span> <span data-ttu-id="e852a-115">Os demonstrativos que seguem o demonstrativo `Return` não são executados.</span><span class="sxs-lookup"><span data-stu-id="e852a-115">Statements following the `Return` statement do not run.</span></span> <span data-ttu-id="e852a-116">Você pode ter mais de um demonstrativo `Return` no mesmo procedimento.</span><span class="sxs-lookup"><span data-stu-id="e852a-116">You can have more than one `Return` statement in the same procedure.</span></span>  
  
-   <span data-ttu-id="e852a-117">Com um demonstrativo `Exit Sub` ou `Exit Function`, o controle retorna imediatamente para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="e852a-117">With an `Exit Sub` or `Exit Function` statement, control returns immediately to the calling code.</span></span> <span data-ttu-id="e852a-118">Os demonstrativos que seguem o demonstrativo `Exit` não são executados.</span><span class="sxs-lookup"><span data-stu-id="e852a-118">Statements following the `Exit` statement do not run.</span></span> <span data-ttu-id="e852a-119">Você pode ter mais de um demonstrativo `Exit` no mesmo procedimento e mesclar os demonstrativos `Return` e `Exit` no mesmo procedimento.</span><span class="sxs-lookup"><span data-stu-id="e852a-119">You can have more than one `Exit` statement in the same procedure, and you can mix `Return` and `Exit` statements in the same procedure.</span></span>  
  
-   <span data-ttu-id="e852a-120">Se um procedimento não tiver nenhum demonstrativo `Return` ou `Exit`, ele será concluído com um demonstrativo `End Sub` ou `End Function`, `End Get` ou `End Set` após o último demonstrativo do corpo do procedimento.</span><span class="sxs-lookup"><span data-stu-id="e852a-120">If a procedure has no `Return` or `Exit` statements, it concludes with an `End Sub` or `End Function`, `End Get`, or `End Set` statement following the last statement of the procedure body.</span></span> <span data-ttu-id="e852a-121">O demonstrativo `End` retorna o controle imediatamente para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="e852a-121">The `End` statement returns control immediately to the calling code.</span></span> <span data-ttu-id="e852a-122">Você pode ter apenas um demonstrativo `End` em um procedimento.</span><span class="sxs-lookup"><span data-stu-id="e852a-122">You can have only one `End` statement in a procedure.</span></span>  
  
## <a name="parameters-and-arguments"></a><span data-ttu-id="e852a-123">Parâmetros e argumentos</span><span class="sxs-lookup"><span data-stu-id="e852a-123">Parameters and Arguments</span></span>  
 <span data-ttu-id="e852a-124">Na maioria dos casos, um procedimento precisa operar em diferentes dados cada vez que é chamado.</span><span class="sxs-lookup"><span data-stu-id="e852a-124">In most cases, a procedure needs to operate on different data each time you call it.</span></span> <span data-ttu-id="e852a-125">Você pode transmitir essas informações para o procedimento como parte da chamada de procedimento.</span><span class="sxs-lookup"><span data-stu-id="e852a-125">You can pass this information to the procedure as part of the procedure call.</span></span> <span data-ttu-id="e852a-126">O procedimento define zero ou mais *parâmetros* e cada um deles representa um valor que se espera que seja transmitido.</span><span class="sxs-lookup"><span data-stu-id="e852a-126">The procedure defines zero or more *parameters*, each of which represents a value it expects you to pass to it.</span></span> <span data-ttu-id="e852a-127">A correspondência com cada parâmetro na definição do procedimento é um *argumento* na chamada de procedimento.</span><span class="sxs-lookup"><span data-stu-id="e852a-127">Corresponding to each parameter in the procedure definition is an *argument* in the procedure call.</span></span> <span data-ttu-id="e852a-128">Um argumento representa o valor que você transmite ao parâmetro correspondente em uma determinada chamada de procedimento.</span><span class="sxs-lookup"><span data-stu-id="e852a-128">An argument represents the value you pass to the corresponding parameter in a given procedure call.</span></span>  
  
## <a name="types-of-procedures"></a><span data-ttu-id="e852a-129">Tipos de procedimentos</span><span class="sxs-lookup"><span data-stu-id="e852a-129">Types of Procedures</span></span>  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="e852a-130"> usa vários tipos de procedimentos:</span><span class="sxs-lookup"><span data-stu-id="e852a-130"> uses several types of procedures:</span></span>  
  
-   <span data-ttu-id="e852a-131">Os [procedimentos Sub](./sub-procedures.md) executam ações, mas não retornam um valor para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="e852a-131">[Sub Procedures](./sub-procedures.md) perform actions but do not return a value to the calling code.</span></span>  
  
-   <span data-ttu-id="e852a-132">Os procedimentos de manipulação de eventos são procedimentos `Sub` que são executados em resposta a um evento gerado por uma ação do usuário ou por uma ocorrência em um programa.</span><span class="sxs-lookup"><span data-stu-id="e852a-132">Event-handling procedures are `Sub` procedures that execute in response to an event raised by user action or by an occurrence in a program.</span></span>  
  
-   <span data-ttu-id="e852a-133">Os [procedimentos Function](./function-procedures.md) retornam um valor para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="e852a-133">[Function Procedures](./function-procedures.md) return a value to the calling code.</span></span> <span data-ttu-id="e852a-134">Eles podem executar outras ações antes de retornar.</span><span class="sxs-lookup"><span data-stu-id="e852a-134">They can perform other actions before returning.</span></span>

    <span data-ttu-id="e852a-135">Algumas funções escritas em C# devolvem um *valor retornado de referência*.</span><span class="sxs-lookup"><span data-stu-id="e852a-135">Some functions written in C# return a *reference return value*.</span></span> <span data-ttu-id="e852a-136">Os chamadores da função podem modificar o valor retornado, e essa modificação é refletida no estado do objeto de chamada.</span><span class="sxs-lookup"><span data-stu-id="e852a-136">Function callers can modify the return value, and this modification is reflected in the state of the called object.</span></span> <span data-ttu-id="e852a-137">Começando com o Visual Basic 2017, o código do Visual Basic pode consumir valores retornados de referência, embora não possa retornar um valor por referência.</span><span class="sxs-lookup"><span data-stu-id="e852a-137">Starting with Visual Basic 2017, Visual Basic code can consume reference return values, although it cannot return a value by reference.</span></span> <span data-ttu-id="e852a-138">Para obter mais informações, consulte [Reference return values](ref-return-values.md) (Valores retornados de referência).</span><span class="sxs-lookup"><span data-stu-id="e852a-138">For more information, see [Reference return values](ref-return-values.md).</span></span>
  
-   <span data-ttu-id="e852a-139">Os [procedimentos de propriedade](./property-procedures.md) retornam e atribuem valores de propriedades em objetos ou módulos.</span><span class="sxs-lookup"><span data-stu-id="e852a-139">[Property Procedures](./property-procedures.md) return and assign values of properties on objects or modules.</span></span>  
  
-   <span data-ttu-id="e852a-140">Os [procedimentos de operador](./operator-procedures.md) definem o comportamento de um operador padrão quando um ou ambos os operandos são uma classe ou estrutura definida recentemente.</span><span class="sxs-lookup"><span data-stu-id="e852a-140">[Operator Procedures](./operator-procedures.md) define the behavior of a standard operator when one or both of the operands is a newly-defined class or structure.</span></span>  
  
-   <span data-ttu-id="e852a-141">Os [procedimentos genéricos no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md) definem um ou mais *parâmetros de tipo*, além de seus parâmetros normais, para que o código de chamada possa transmitir tipos de dados específicos cada vez que faz uma chamada.</span><span class="sxs-lookup"><span data-stu-id="e852a-141">[Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md) define one or more *type parameters* in addition to their normal parameters, so the calling code can pass specific data types each time it makes a call.</span></span>  
  
## <a name="procedures-and-structured-code"></a><span data-ttu-id="e852a-142">Procedimentos e código estruturado</span><span class="sxs-lookup"><span data-stu-id="e852a-142">Procedures and Structured Code</span></span>  
 <span data-ttu-id="e852a-143">Cada linha de código executável em seu aplicativo deve estar em algum procedimento, como `Main`, `calculate` ou `Button1_Click`.</span><span class="sxs-lookup"><span data-stu-id="e852a-143">Every line of executable code in your application must be inside some procedure, such as `Main`, `calculate`, or `Button1_Click`.</span></span> <span data-ttu-id="e852a-144">Se você subdividir procedimentos grandes em menores, seu aplicativo ficará mais legível.</span><span class="sxs-lookup"><span data-stu-id="e852a-144">If you subdivide large procedures into smaller ones, your application is more readable.</span></span>  
  
 <span data-ttu-id="e852a-145">Os procedimentos são úteis para executar tarefas repetidas ou compartilhadas, como cálculos frequentemente usados, manipulação e controle de texto e operações de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="e852a-145">Procedures are useful for performing repeated or shared tasks, such as frequently used calculations, text and control manipulation, and database operations.</span></span> <span data-ttu-id="e852a-146">Você pode chamar um procedimento de vários locais diferentes em seu código. Desse modo, você pode usar procedimentos como blocos de construção para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e852a-146">You can call a procedure from many different places in your code, so you can use procedures as building blocks for your application.</span></span>  
  
 <span data-ttu-id="e852a-147">Estruturar seu código com procedimentos lhe oferece os seguintes benefícios:</span><span class="sxs-lookup"><span data-stu-id="e852a-147">Structuring your code with procedures gives you the following benefits:</span></span>  
  
-   <span data-ttu-id="e852a-148">Os procedimentos permitem que você divida seus programas em unidades lógicas distintas.</span><span class="sxs-lookup"><span data-stu-id="e852a-148">Procedures allow you to break your programs into discrete logical units.</span></span> <span data-ttu-id="e852a-149">Você pode depurar unidades separadas mais facilmente do que depurar um programa inteiro sem procedimentos.</span><span class="sxs-lookup"><span data-stu-id="e852a-149">You can debug separate units more easily than you can debug an entire program without procedures.</span></span>  
  
-   <span data-ttu-id="e852a-150">Depois de desenvolver procedimentos para uso em um programa, você pode usá-los em outros programas, geralmente com pouca ou nenhuma modificação.</span><span class="sxs-lookup"><span data-stu-id="e852a-150">After you develop procedures for use in one program, you can use them in other programs, often with little or no modification.</span></span> <span data-ttu-id="e852a-151">Isso ajuda a evitar a duplicação de código.</span><span class="sxs-lookup"><span data-stu-id="e852a-151">This helps you avoid code duplication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e852a-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e852a-152">See Also</span></span>  
 <span data-ttu-id="e852a-153">[Como criar um procedimento](./how-to-create-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="e852a-153">[How to: Create a Procedure](./how-to-create-a-procedure.md) </span></span>  
 <span data-ttu-id="e852a-154">[Subprocedimentos](./sub-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="e852a-154">[Sub Procedures](./sub-procedures.md) </span></span>  
 <span data-ttu-id="e852a-155">[Procedimentos de Função](./function-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="e852a-155">[Function Procedures](./function-procedures.md) </span></span>  
 <span data-ttu-id="e852a-156">[Procedimentos de Propriedade](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="e852a-156">[Property Procedures](./property-procedures.md) </span></span>  
 <span data-ttu-id="e852a-157">[Procedimentos de Operador](./operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="e852a-157">[Operator Procedures](./operator-procedures.md) </span></span>  
 <span data-ttu-id="e852a-158">[Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="e852a-158">[Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
 <span data-ttu-id="e852a-159">[Procedimentos Recursivos](./recursive-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="e852a-159">[Recursive Procedures](./recursive-procedures.md) </span></span>  
 <span data-ttu-id="e852a-160">[Sobrecarga de Procedimento](./procedure-overloading.md) </span><span class="sxs-lookup"><span data-stu-id="e852a-160">[Procedure Overloading](./procedure-overloading.md) </span></span>  
 <span data-ttu-id="e852a-161">[Procedimentos genéricos no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="e852a-161">[Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md) </span></span>  
 [<span data-ttu-id="e852a-162">Objetos e Classes</span><span class="sxs-lookup"><span data-stu-id="e852a-162">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)

