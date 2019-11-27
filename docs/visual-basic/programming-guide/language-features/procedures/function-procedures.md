---
title: Procedimentos de função
ms.date: 07/20/2015
helpviewer_keywords:
- Function procedures
- return values [Visual Basic], function procedures
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], Function procedures
- syntax [Visual Basic], function procedures
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
ms.openlocfilehash: b62a730e8ade211821826afbb55fa8858ea311a3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74341084"
---
# <a name="function-procedures-visual-basic"></a><span data-ttu-id="c0965-102">Procedimentos de função (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c0965-102">Function Procedures (Visual Basic)</span></span>
<span data-ttu-id="c0965-103">Um procedimento `Function` é uma série de instruções Visual Basic delimitadas pelas instruções `Function` e `End Function`.</span><span class="sxs-lookup"><span data-stu-id="c0965-103">A `Function` procedure is a series of Visual Basic statements enclosed by the `Function` and `End Function` statements.</span></span> <span data-ttu-id="c0965-104">O procedimento de `Function` executa uma tarefa e, em seguida, retorna o controle para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="c0965-104">The `Function` procedure performs a task and then returns control to the calling code.</span></span> <span data-ttu-id="c0965-105">Quando ele retorna o controle, ele também retorna um valor para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="c0965-105">When it returns control, it also returns a value to the calling code.</span></span>  
  
 <span data-ttu-id="c0965-106">Cada vez que o procedimento é chamado, suas instruções são executadas, começando com a primeira instrução executável após a instrução de `Function` e terminando com a primeira instrução `End Function`, `Exit Function`ou `Return` encontrada.</span><span class="sxs-lookup"><span data-stu-id="c0965-106">Each time the procedure is called, its statements run, starting with the first executable statement after the `Function` statement and ending with the first `End Function`, `Exit Function`, or `Return` statement encountered.</span></span>  
  
 <span data-ttu-id="c0965-107">Você pode definir um procedimento `Function` em um módulo, classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="c0965-107">You can define a `Function` procedure in a module, class, or structure.</span></span> <span data-ttu-id="c0965-108">É `Public` por padrão, o que significa que você pode chamá-lo de qualquer lugar em seu aplicativo que tenha acesso ao módulo, à classe ou à estrutura na qual você o definiu.</span><span class="sxs-lookup"><span data-stu-id="c0965-108">It is `Public` by default, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span>  
  
 <span data-ttu-id="c0965-109">Um procedimento `Function` pode receber argumentos, como constantes, variáveis ou expressões, que são passados para ele pelo código de chamada.</span><span class="sxs-lookup"><span data-stu-id="c0965-109">A `Function` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="c0965-110">Sintaxe de Declaração</span><span class="sxs-lookup"><span data-stu-id="c0965-110">Declaration Syntax</span></span>  
 <span data-ttu-id="c0965-111">A sintaxe para declarar um procedimento `Function` é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="c0965-111">The syntax for declaring a `Function` procedure is as follows:</span></span>  
  
```vb  
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType  
    [Statements]  
End Function  
```  
  
 <span data-ttu-id="c0965-112">Os *modificadores* podem especificar o nível de acesso e as informações sobre sobrecarga, substituição, compartilhamento e sombreamento.</span><span class="sxs-lookup"><span data-stu-id="c0965-112">The *modifiers* can specify access level and information regarding overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="c0965-113">Para obter mais informações, consulte [instrução de função](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c0965-113">For more information, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="c0965-114">Você declara cada parâmetro da mesma maneira que faz para [procedimentos sub](./sub-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="c0965-114">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="c0965-115">Tipo de Dados</span><span class="sxs-lookup"><span data-stu-id="c0965-115">Data Type</span></span>  
 <span data-ttu-id="c0965-116">Cada procedimento de `Function` tem um tipo de dados, da mesma forma que cada variável.</span><span class="sxs-lookup"><span data-stu-id="c0965-116">Every `Function` procedure has a data type, just as every variable does.</span></span> <span data-ttu-id="c0965-117">Esse tipo de dados é especificado pela cláusula `As` na instrução `Function` e determina o tipo de dados do valor que a função retorna para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="c0965-117">This data type is specified by the `As` clause in the `Function` statement, and it determines the data type of the value the function returns to the calling code.</span></span> <span data-ttu-id="c0965-118">As declarações de exemplo a seguir ilustram isso.</span><span class="sxs-lookup"><span data-stu-id="c0965-118">The following sample declarations illustrate this.</span></span>  
  
```vb  
Function yesterday() As Date  
End Function  
  
Function findSqrt(ByVal radicand As Single) As Single  
End Function  
```  
  
 <span data-ttu-id="c0965-119">Para obter mais informações, consulte "partes" na [instrução function](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c0965-119">For more information, see "Parts" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
## <a name="returning-values"></a><span data-ttu-id="c0965-120">Retornando valores</span><span class="sxs-lookup"><span data-stu-id="c0965-120">Returning Values</span></span>  
 <span data-ttu-id="c0965-121">O valor que um procedimento `Function` envia de volta para o código de chamada é chamado de valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="c0965-121">The value a `Function` procedure sends back to the calling code is called its return value.</span></span> <span data-ttu-id="c0965-122">O procedimento retorna esse valor de uma das duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="c0965-122">The procedure returns this value in one of two ways:</span></span>  
  
- <span data-ttu-id="c0965-123">Ele usa a instrução `Return` para especificar o valor de retorno e retorna o controle imediatamente para o programa de chamada.</span><span class="sxs-lookup"><span data-stu-id="c0965-123">It uses the `Return` statement to specify the return value, and returns control immediately to the calling program.</span></span> <span data-ttu-id="c0965-124">O exemplo a seguir mostra isso.</span><span class="sxs-lookup"><span data-stu-id="c0965-124">The following example illustrates this.</span></span>  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement immediately transfers control back  
    ' to the calling code and returns the value of Expression.  
    Return Expression  
End Function  
```  
  
- <span data-ttu-id="c0965-125">Ele atribui um valor ao seu próprio nome de função em uma ou mais instruções do procedimento.</span><span class="sxs-lookup"><span data-stu-id="c0965-125">It assigns a value to its own function name in one or more statements of the procedure.</span></span> <span data-ttu-id="c0965-126">O controle não retorna ao programa de chamada até que uma instrução `Exit Function` ou `End Function` seja executada.</span><span class="sxs-lookup"><span data-stu-id="c0965-126">Control does not return to the calling program until an `Exit Function` or `End Function` statement is executed.</span></span> <span data-ttu-id="c0965-127">O exemplo a seguir mostra isso.</span><span class="sxs-lookup"><span data-stu-id="c0965-127">The following example illustrates this.</span></span>  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement does not transfer control back to the calling code.  
    FunctionName = Expression  
    ' When control returns to the calling code, Expression is the return value.  
End Function  
```  
  
 <span data-ttu-id="c0965-128">A vantagem de atribuir o valor de retorno ao nome da função é que o controle não retorna do procedimento até encontrar uma instrução `Exit Function` ou `End Function`.</span><span class="sxs-lookup"><span data-stu-id="c0965-128">The advantage of assigning the return value to the function name is that control does not return from the procedure until it encounters an `Exit Function` or `End Function` statement.</span></span> <span data-ttu-id="c0965-129">Isso permite que você atribua um valor preliminar e ajuste-o posteriormente, se necessário.</span><span class="sxs-lookup"><span data-stu-id="c0965-129">This allows you to assign a preliminary value and adjust it later if necessary.</span></span>  
  
 <span data-ttu-id="c0965-130">Para obter mais informações sobre valores de retorno, consulte [instrução de função](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c0965-130">For more information about returning values, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="c0965-131">Para obter informações sobre como retornar matrizes, consulte [matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="c0965-131">For information about returning arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="c0965-132">Sintaxe de chamada</span><span class="sxs-lookup"><span data-stu-id="c0965-132">Calling Syntax</span></span>  
 <span data-ttu-id="c0965-133">Você invoca um procedimento de `Function` incluindo seu nome e argumentos no lado direito de uma instrução de atribuição ou em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="c0965-133">You invoke a `Function` procedure by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span> <span data-ttu-id="c0965-134">Você deve fornecer valores para todos os argumentos que não são opcionais, e você deve colocar a lista de argumentos entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="c0965-134">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="c0965-135">Se nenhum argumento for fornecido, você pode opcionalmente omitir os parênteses.</span><span class="sxs-lookup"><span data-stu-id="c0965-135">If no arguments are supplied, you can optionally omit the parentheses.</span></span>  
  
 <span data-ttu-id="c0965-136">A sintaxe de uma chamada para um procedimento `Function` é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="c0965-136">The syntax for a call to a `Function` procedure is as follows:</span></span>  
  
 <span data-ttu-id="c0965-137">*lvalue*`=`*FunctionName* `[(` *argumentolist* `)]`</span><span class="sxs-lookup"><span data-stu-id="c0965-137">*lvalue*  `=`  *functionname* `[(` *argumentlist* `)]`</span></span>  
  
 <span data-ttu-id="c0965-138">`If ((` *functionname* `[(` *argumentolist* `)] / 3) <=`*expressão* `) Then`</span><span class="sxs-lookup"><span data-stu-id="c0965-138">`If ((` *functionname* `[(` *argumentlist* `)] / 3) <=`  *expression* `) Then`</span></span>  
  
 <span data-ttu-id="c0965-139">Ao chamar um procedimento de `Function`, você não precisa usar seu valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="c0965-139">When you call a `Function` procedure, you do not have to use its return value.</span></span> <span data-ttu-id="c0965-140">Se você não fizer isso, todas as ações da função serão executadas, mas o valor de retorno será ignorado.</span><span class="sxs-lookup"><span data-stu-id="c0965-140">If you do not, all the actions of the function are performed, but the return value is ignored.</span></span> <span data-ttu-id="c0965-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> geralmente é chamado dessa maneira.</span><span class="sxs-lookup"><span data-stu-id="c0965-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> is often called in this manner.</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="c0965-142">Ilustração de declaração e chamada</span><span class="sxs-lookup"><span data-stu-id="c0965-142">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="c0965-143">O procedimento a seguir `Function` calcula o lado mais longo, ou hipotenusa, de um triângulo à direita, dado os valores para os outros dois lados.</span><span class="sxs-lookup"><span data-stu-id="c0965-143">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
 <span data-ttu-id="c0965-144">O exemplo a seguir mostra uma chamada típica para `hypotenuse`.</span><span class="sxs-lookup"><span data-stu-id="c0965-144">The following example shows a typical call to `hypotenuse`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="c0965-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c0965-145">See also</span></span>

- [<span data-ttu-id="c0965-146">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="c0965-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="c0965-147">Subprocedimentos</span><span class="sxs-lookup"><span data-stu-id="c0965-147">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="c0965-148">Procedimentos de Propriedade</span><span class="sxs-lookup"><span data-stu-id="c0965-148">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="c0965-149">Procedimentos de Operador</span><span class="sxs-lookup"><span data-stu-id="c0965-149">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="c0965-150">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="c0965-150">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="c0965-151">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="c0965-151">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="c0965-152">Como criar um procedimento que retorne um valor</span><span class="sxs-lookup"><span data-stu-id="c0965-152">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="c0965-153">Como retornar um valor de um procedimento</span><span class="sxs-lookup"><span data-stu-id="c0965-153">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="c0965-154">Como chamar um procedimento que retorna um valor</span><span class="sxs-lookup"><span data-stu-id="c0965-154">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
