---
title: "Função procedimentos (Visual Basic) | Documentos do Microsoft"
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
- Function procedures
- return values, function procedures
- Visual Basic code, procedures
- procedures, calling
- procedures, Function procedures
- syntax, function procedures
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
caps.latest.revision: 27
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
ms.openlocfilehash: fb36ee41e4b53f6e690ce5d48d34bbfc9f86c177
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="function-procedures-visual-basic"></a><span data-ttu-id="c6c3f-102">Procedimentos de função (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6c3f-102">Function Procedures (Visual Basic)</span></span>
<span data-ttu-id="c6c3f-103">A `Function` procedimento é uma série de [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] dentro de instruções de `Function` e `End Function` instruções.</span><span class="sxs-lookup"><span data-stu-id="c6c3f-103">A `Function` procedure is a series of [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] statements enclosed by the `Function` and `End Function` statements.</span></span> <span data-ttu-id="c6c3f-104">O `Function` procedimento executa uma tarefa e, em seguida, retorna o controle para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="c6c3f-104">The `Function` procedure performs a task and then returns control to the calling code.</span></span> <span data-ttu-id="c6c3f-105">Quando ele retorna o controle, ele também retorna um valor para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="c6c3f-105">When it returns control, it also returns a value to the calling code.</span></span>  
  
 <span data-ttu-id="c6c3f-106">Cada vez que é chamada de procedimento, suas declarações são executadas, começando com a primeira instrução executável após o `Function` instrução e terminando com a primeira `End Function`, `Exit Function`, ou `Return` declaração encontrada.</span><span class="sxs-lookup"><span data-stu-id="c6c3f-106">Each time the procedure is called, its statements run, starting with the first executable statement after the `Function` statement and ending with the first `End Function`, `Exit Function`, or `Return` statement encountered.</span></span>  
  
 <span data-ttu-id="c6c3f-107">Você pode definir uma `Function` procedimento em um módulo, classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="c6c3f-107">You can define a `Function` procedure in a module, class, or structure.</span></span> <span data-ttu-id="c6c3f-108">É `Public` por padrão, que significa que você pode chamá-lo de qualquer lugar no seu aplicativo que acessou o módulo, classe ou estrutura na qual você a definiu.</span><span class="sxs-lookup"><span data-stu-id="c6c3f-108">It is `Public` by default, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span>  
  
 <span data-ttu-id="c6c3f-109">Um `Function` procedimento pode receber argumentos, como constantes, variáveis ou expressões, que são passadas a ele pelo código de chamada.</span><span class="sxs-lookup"><span data-stu-id="c6c3f-109">A `Function` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="c6c3f-110">Sintaxe da Declaração</span><span class="sxs-lookup"><span data-stu-id="c6c3f-110">Declaration Syntax</span></span>  
 <span data-ttu-id="c6c3f-111">A sintaxe para declarar uma `Function` procedimento é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c6c3f-111">The syntax for declaring a `Function` procedure is as follows:</span></span>  
  
```vb  
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType  
    [Statements]  
End Function  
```  
  
 <span data-ttu-id="c6c3f-112">O *modificadores* pode especificar o nível de acesso e informações sobre sobrecarregamento, substituições, compartilhamento e sombreamento.</span><span class="sxs-lookup"><span data-stu-id="c6c3f-112">The *modifiers* can specify access level and information regarding overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="c6c3f-113">Para obter mais informações, consulte [declaração de função](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c6c3f-113">For more information, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="c6c3f-114">Você declara cada parâmetro da mesma maneira que faria para [subprocedimentos](./sub-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="c6c3f-114">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="c6c3f-115">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="c6c3f-115">Data Type</span></span>  
 <span data-ttu-id="c6c3f-116">Cada `Function` procedimento tem um tipo de dados, assim como cada variável.</span><span class="sxs-lookup"><span data-stu-id="c6c3f-116">Every `Function` procedure has a data type, just as every variable does.</span></span> <span data-ttu-id="c6c3f-117">Esse tipo de dados é especificado pelo `As` cláusula de `Function` instrução e ele determina o tipo de dados do valor que a função retorna para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="c6c3f-117">This data type is specified by the `As` clause in the `Function` statement, and it determines the data type of the value the function returns to the calling code.</span></span> <span data-ttu-id="c6c3f-118">As declarações de exemplo a seguir ilustram isso.</span><span class="sxs-lookup"><span data-stu-id="c6c3f-118">The following sample declarations illustrate this.</span></span>  
  
```vb  
Function yesterday() As Date  
End Function  
  
Function findSqrt(ByVal radicand As Single) As Single  
End Function  
```  
  
 <span data-ttu-id="c6c3f-119">Para obter mais informações, veja "Partes" em [declaração de função](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c6c3f-119">For more information, see "Parts" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
## <a name="returning-values"></a><span data-ttu-id="c6c3f-120">Retornando valores</span><span class="sxs-lookup"><span data-stu-id="c6c3f-120">Returning Values</span></span>  
 <span data-ttu-id="c6c3f-121">O valor de uma `Function` procedimento envia de volta para o código de chamada é chamada seu valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="c6c3f-121">The value a `Function` procedure sends back to the calling code is called its return value.</span></span> <span data-ttu-id="c6c3f-122">O procedimento retorna o valor de uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="c6c3f-122">The procedure returns this value in one of two ways:</span></span>  
  
-   <span data-ttu-id="c6c3f-123">Ele usa o `Return` para especificar o valor de retorno e retorna o controle imediatamente para o programa de chamada.</span><span class="sxs-lookup"><span data-stu-id="c6c3f-123">It uses the `Return` statement to specify the return value, and returns control immediately to the calling program.</span></span> <span data-ttu-id="c6c3f-124">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="c6c3f-124">The following example illustrates this.</span></span>  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement immediately transfers control back  
    ' to the calling code and returns the value of Expression.  
    Return Expression  
End Function  
```  
  
-   <span data-ttu-id="c6c3f-125">Ele atribui um valor para o seu próprio nome de função em uma ou mais declarações do procedimento.</span><span class="sxs-lookup"><span data-stu-id="c6c3f-125">It assigns a value to its own function name in one or more statements of the procedure.</span></span> <span data-ttu-id="c6c3f-126">O controle retorna ao programa de chamada até que uma `Exit Function` ou `End Function` instrução é executada.</span><span class="sxs-lookup"><span data-stu-id="c6c3f-126">Control does not return to the calling program until an `Exit Function` or `End Function` statement is executed.</span></span> <span data-ttu-id="c6c3f-127">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="c6c3f-127">The following example illustrates this.</span></span>  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement does not transfer control back to the calling code.  
    FunctionName = Expression  
    ' When control returns to the calling code, Expression is the return value.  
End Function  
```  
  
 <span data-ttu-id="c6c3f-128">A vantagem de atribuir o valor de retorno ao nome da função é que o controle não retorna do procedimento até encontrar um `Exit Function` ou `End Function` instrução.</span><span class="sxs-lookup"><span data-stu-id="c6c3f-128">The advantage of assigning the return value to the function name is that control does not return from the procedure until it encounters an `Exit Function` or `End Function` statement.</span></span> <span data-ttu-id="c6c3f-129">Isso permite que você atribua um valor preliminar e ajustá-lo mais tarde, se necessário.</span><span class="sxs-lookup"><span data-stu-id="c6c3f-129">This allows you to assign a preliminary value and adjust it later if necessary.</span></span>  
  
 <span data-ttu-id="c6c3f-130">Para obter mais informações sobre como retornar valores, consulte [declaração de função](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c6c3f-130">For more information about returning values, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="c6c3f-131">Para obter informações sobre como retornar matrizes, consulte [matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="c6c3f-131">For information about returning arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="c6c3f-132">Sintaxe de chamada</span><span class="sxs-lookup"><span data-stu-id="c6c3f-132">Calling Syntax</span></span>  
 <span data-ttu-id="c6c3f-133">Você invocar um `Function` procedimento, incluindo seu nome e argumentos tanto no lado direito de uma instrução de atribuição ou em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="c6c3f-133">You invoke a `Function` procedure by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span> <span data-ttu-id="c6c3f-134">Você deve fornecer valores para todos os argumentos que não são opcionais, e você deve colocar a lista de argumentos entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="c6c3f-134">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="c6c3f-135">Se não for fornecido nenhum argumento, opcionalmente, você pode omitir os parênteses.</span><span class="sxs-lookup"><span data-stu-id="c6c3f-135">If no arguments are supplied, you can optionally omit the parentheses.</span></span>  
  
 <span data-ttu-id="c6c3f-136">A sintaxe para chamar um `Function` procedimento é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c6c3f-136">The syntax for a call to a `Function` procedure is as follows:</span></span>  
  
 <span data-ttu-id="c6c3f-137">*l-value*`=`*functionname* `[(` *argumentlist*    `)]`</span><span class="sxs-lookup"><span data-stu-id="c6c3f-137">*lvalue*  `=`  *functionname* `[(` *argumentlist* `)]`</span></span>  
  
 <span data-ttu-id="c6c3f-138">`If ((`*functionname* `[(` *argumentlist* `)] / 3) <=` *expressão*  `) Then`</span><span class="sxs-lookup"><span data-stu-id="c6c3f-138">`If ((` *functionname* `[(` *argumentlist* `)] / 3) <=`  *expression* `) Then`</span></span>  
  
 <span data-ttu-id="c6c3f-139">Quando você chama um `Function` procedimento, você não precisa usar seu valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="c6c3f-139">When you call a `Function` procedure, you do not have to use its return value.</span></span> <span data-ttu-id="c6c3f-140">Se você não fizer isso, todas as ações da função são executadas, mas o valor de retorno será ignorado.</span><span class="sxs-lookup"><span data-stu-id="c6c3f-140">If you do not, all the actions of the function are performed, but the return value is ignored.</span></span> <span data-ttu-id="c6c3f-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>é frequentemente chamado dessa maneira.</xref:Microsoft.VisualBasic.Interaction.MsgBox%2A></span><span class="sxs-lookup"><span data-stu-id="c6c3f-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> is often called in this manner.</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="c6c3f-142">Ilustração da declaração e chamada</span><span class="sxs-lookup"><span data-stu-id="c6c3f-142">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="c6c3f-143">O seguinte `Function` procedimento calcula o maior lado, ou hipotenusa, de um triângulo, considerando os valores para os dois lados.</span><span class="sxs-lookup"><span data-stu-id="c6c3f-143">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
 <span data-ttu-id="c6c3f-144">[!code-vb[VbVbcnProcedures n º&1;](./codesnippet/VisualBasic/function-procedures_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="c6c3f-144">[!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/function-procedures_1.vb)]</span></span>  
  
 <span data-ttu-id="c6c3f-145">O exemplo a seguir mostra uma chamada típica para `hypotenuse`.</span><span class="sxs-lookup"><span data-stu-id="c6c3f-145">The following example shows a typical call to `hypotenuse`.</span></span>  
  
 <span data-ttu-id="c6c3f-146">[!code-vb[VbVbcnProcedures n º&6;](./codesnippet/VisualBasic/function-procedures_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="c6c3f-146">[!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/function-procedures_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6c3f-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c6c3f-147">See Also</span></span>  
 <span data-ttu-id="c6c3f-148">[Procedimentos](./index.md) </span><span class="sxs-lookup"><span data-stu-id="c6c3f-148">[Procedures](./index.md) </span></span>  
<span data-ttu-id="c6c3f-149"> [Procedimentos Sub](./sub-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="c6c3f-149"> [Sub Procedures](./sub-procedures.md) </span></span>  
<span data-ttu-id="c6c3f-150"> [Procedimentos de propriedade](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="c6c3f-150"> [Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="c6c3f-151"> [Procedimentos de operador](./operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="c6c3f-151"> [Operator Procedures](./operator-procedures.md) </span></span>  
<span data-ttu-id="c6c3f-152"> [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="c6c3f-152"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="c6c3f-153"> [Instrução Function](../../../../visual-basic/language-reference/statements/function-statement.md) </span><span class="sxs-lookup"><span data-stu-id="c6c3f-153"> [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md) </span></span>  
<span data-ttu-id="c6c3f-154"> [Como: criar um procedimento que retorna um valor](./how-to-create-a-procedure-that-returns-a-value.md) </span><span class="sxs-lookup"><span data-stu-id="c6c3f-154"> [How to: Create a Procedure that Returns a Value](./how-to-create-a-procedure-that-returns-a-value.md) </span></span>  
<span data-ttu-id="c6c3f-155"> [Como: retornar um valor de um procedimento](./how-to-return-a-value-from-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="c6c3f-155"> [How to: Return a Value from a Procedure](./how-to-return-a-value-from-a-procedure.md) </span></span>  
<span data-ttu-id="c6c3f-156"> [Como chamar um procedimento que retorna um valor](./how-to-call-a-procedure-that-returns-a-value.md)</span><span class="sxs-lookup"><span data-stu-id="c6c3f-156"> [How to: Call a Procedure That Returns a Value](./how-to-call-a-procedure-that-returns-a-value.md)</span></span>
