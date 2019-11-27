---
title: Subprocedimentos
ms.date: 07/20/2015
helpviewer_keywords:
- Sub procedures [Visual Basic], about Sub procedures
- statement blocks
- Sub procedures [Visual Basic], calling
- procedures [Visual Basic], calling
- Sub procedures [Visual Basic], syntax
- Sub procedures
- procedures [Visual Basic], Sub
- syntax [Visual Basic], Sub procedures
ms.assetid: 6a0a4958-ed0a-4d3d-8d31-0772c82bda58
ms.openlocfilehash: 7848dc07d6462622685cdbea92202585f4d5d2c4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352531"
---
# <a name="sub-procedures-visual-basic"></a><span data-ttu-id="f73a4-102">Subprocedimentos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f73a4-102">Sub Procedures (Visual Basic)</span></span>
<span data-ttu-id="f73a4-103">Um procedimento `Sub` é uma série de instruções Visual Basic delimitadas pelas instruções `Sub` e `End Sub`.</span><span class="sxs-lookup"><span data-stu-id="f73a4-103">A `Sub` procedure is a series of Visual Basic statements enclosed by the `Sub` and `End Sub` statements.</span></span> <span data-ttu-id="f73a4-104">O procedimento de `Sub` executa uma tarefa e, em seguida, retorna o controle para o código de chamada, mas não retorna um valor para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="f73a4-104">The `Sub` procedure performs a task and then returns control to the calling code, but it does not return a value to the calling code.</span></span>  
  
 <span data-ttu-id="f73a4-105">Cada vez que o procedimento é chamado, suas instruções são executadas, começando com a primeira instrução executável após a instrução de `Sub` e terminando com a primeira instrução `End Sub`, `Exit Sub`ou `Return` encontrada.</span><span class="sxs-lookup"><span data-stu-id="f73a4-105">Each time the procedure is called, its statements are executed, starting with the first executable statement after the `Sub` statement and ending with the first `End Sub`, `Exit Sub`, or `Return` statement encountered.</span></span>  
  
 <span data-ttu-id="f73a4-106">Você pode definir um procedimento `Sub` em módulos, classes e estruturas.</span><span class="sxs-lookup"><span data-stu-id="f73a4-106">You can define a `Sub` procedure in modules, classes, and structures.</span></span> <span data-ttu-id="f73a4-107">Por padrão, é `Public`, o que significa que você pode chamá-lo de qualquer lugar em seu aplicativo que tenha acesso ao módulo, à classe ou à estrutura na qual você o definiu.</span><span class="sxs-lookup"><span data-stu-id="f73a4-107">By default, it is `Public`, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span> <span data-ttu-id="f73a4-108">O termo, *método*, descreve um `Sub` ou `Function` procedimento que é acessado de fora de sua definição de módulo, classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="f73a4-108">The term, *method*, describes a `Sub` or `Function` procedure that is accessed from outside its defining module, class, or structure.</span></span> <span data-ttu-id="f73a4-109">Para obter mais informações, consulte [Procedimentos](./index.md).</span><span class="sxs-lookup"><span data-stu-id="f73a4-109">For more information, see [Procedures](./index.md).</span></span>  
  
 <span data-ttu-id="f73a4-110">Um procedimento `Sub` pode receber argumentos, como constantes, variáveis ou expressões, que são passados para ele pelo código de chamada.</span><span class="sxs-lookup"><span data-stu-id="f73a4-110">A `Sub` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="f73a4-111">Sintaxe de Declaração</span><span class="sxs-lookup"><span data-stu-id="f73a4-111">Declaration Syntax</span></span>  
 <span data-ttu-id="f73a4-112">A sintaxe para declarar um procedimento `Sub` é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="f73a4-112">The syntax for declaring a `Sub` procedure is as follows:</span></span>  
  
 <span data-ttu-id="f73a4-113">`[` *modificadores* `] Sub`*subnome* `[(` *parameterlist* `)]`</span><span class="sxs-lookup"><span data-stu-id="f73a4-113">`[` *modifiers* `] Sub`  *subname* `[(` *parameterlist* `)]`</span></span>  
  
 `' Statements of the Sub procedure.`  
  
 `End Sub`  
  
 <span data-ttu-id="f73a4-114">O `modifiers` pode especificar o nível de acesso e informações sobre sobrecarga, substituição, compartilhamento e sombreamento.</span><span class="sxs-lookup"><span data-stu-id="f73a4-114">The `modifiers` can specify access level and information about overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="f73a4-115">Para obter mais informações, consulte [sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f73a4-115">For more information, see [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="parameter-declaration"></a><span data-ttu-id="f73a4-116">Declaração de parâmetro</span><span class="sxs-lookup"><span data-stu-id="f73a4-116">Parameter Declaration</span></span>  
 <span data-ttu-id="f73a4-117">Você declara cada parâmetro de procedimento da mesma forma como declara uma variável, especificando o nome do parâmetro e o tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="f73a4-117">You declare each procedure parameter similarly to how you declare a variable, specifying the parameter name and data type.</span></span> <span data-ttu-id="f73a4-118">Você também pode especificar o mecanismo de passagem e se o parâmetro é opcional ou uma matriz de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="f73a4-118">You can also specify the passing mechanism, and whether the parameter is optional or a parameter array.</span></span>  
  
 <span data-ttu-id="f73a4-119">A sintaxe para cada parâmetro na lista de parâmetros é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="f73a4-119">The syntax for each parameter in the parameter list is as follows:</span></span>  
  
 <span data-ttu-id="f73a4-120">*tipo de dados* `[Optional] [ByVal | ByRef] [ParamArray]`*ParameterName*`As`</span><span class="sxs-lookup"><span data-stu-id="f73a4-120">`[Optional] [ByVal | ByRef] [ParamArray]`  *parametername*  `As`  *datatype*</span></span>  
  
 <span data-ttu-id="f73a4-121">Se o parâmetro for opcional, você também deverá fornecer um valor padrão como parte de sua declaração.</span><span class="sxs-lookup"><span data-stu-id="f73a4-121">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="f73a4-122">A sintaxe para especificar um valor padrão é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="f73a4-122">The syntax for specifying a default value is as follows:</span></span>  
  
 <span data-ttu-id="f73a4-123">`Optional [ByVal | ByRef]`*parametername*`As`*DataType*`=`*DefaultValue*</span><span class="sxs-lookup"><span data-stu-id="f73a4-123">`Optional [ByVal | ByRef]`  *parametername*  `As`  *datatype*  `=`  *defaultvalue*</span></span>  
  
### <a name="parameters-as-local-variables"></a><span data-ttu-id="f73a4-124">Parâmetros como variáveis locais</span><span class="sxs-lookup"><span data-stu-id="f73a4-124">Parameters as Local Variables</span></span>  
 <span data-ttu-id="f73a4-125">Quando o controle passa para o procedimento, cada parâmetro é tratado como uma variável local.</span><span class="sxs-lookup"><span data-stu-id="f73a4-125">When control passes to the procedure, each parameter is treated as a local variable.</span></span> <span data-ttu-id="f73a4-126">Isso significa que seu tempo de vida é o mesmo que o do procedimento, e seu escopo é o procedimento completo.</span><span class="sxs-lookup"><span data-stu-id="f73a4-126">This means that its lifetime is the same as that of the procedure, and its scope is the whole procedure.</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="f73a4-127">Sintaxe de chamada</span><span class="sxs-lookup"><span data-stu-id="f73a4-127">Calling Syntax</span></span>  
 <span data-ttu-id="f73a4-128">Você invoca um procedimento `Sub` explicitamente com uma instrução de chamada autônoma.</span><span class="sxs-lookup"><span data-stu-id="f73a4-128">You invoke a `Sub` procedure explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="f73a4-129">Você não pode chamá-lo usando seu nome em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="f73a4-129">You cannot call it by using its name in an expression.</span></span> <span data-ttu-id="f73a4-130">Você deve fornecer valores para todos os argumentos que não são opcionais, e você deve colocar a lista de argumentos entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="f73a4-130">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="f73a4-131">Se nenhum argumento for fornecido, você pode opcionalmente omitir os parênteses.</span><span class="sxs-lookup"><span data-stu-id="f73a4-131">If no arguments are supplied, you can optionally omit the parentheses.</span></span> <span data-ttu-id="f73a4-132">O uso da palavra-chave `Call` é opcional, mas não é recomendado.</span><span class="sxs-lookup"><span data-stu-id="f73a4-132">The use of the `Call` keyword is optional but not recommended.</span></span>  
  
 <span data-ttu-id="f73a4-133">A sintaxe de uma chamada para um procedimento `Sub` é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="f73a4-133">The syntax for a call to a `Sub` procedure is as follows:</span></span>  
  
 <span data-ttu-id="f73a4-134">*subnome* de `[Call]``[(` *ArgumentList* `)]`</span><span class="sxs-lookup"><span data-stu-id="f73a4-134">`[Call]`  *subname* `[(` *argumentlist* `)]`</span></span>  
  
 <span data-ttu-id="f73a4-135">Você pode chamar um método `Sub` de fora da classe que o define.</span><span class="sxs-lookup"><span data-stu-id="f73a4-135">You can call a `Sub` method from outside the class that defines it.</span></span> <span data-ttu-id="f73a4-136">Primeiro, você precisa usar a palavra-chave `New` para criar uma instância da classe ou chamar um método que retorne uma instância da classe.</span><span class="sxs-lookup"><span data-stu-id="f73a4-136">First, you have to use the `New` keyword to create an instance of the class, or call a method that returns an instance of the class.</span></span> <span data-ttu-id="f73a4-137">Para obter mais informações, consulte [novo operador](../../../../visual-basic/language-reference/operators/new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="f73a4-137">For more information, see [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="f73a4-138">Em seguida, você pode usar a seguinte sintaxe para chamar o método `Sub` no objeto de instância:</span><span class="sxs-lookup"><span data-stu-id="f73a4-138">Then, you can use the following syntax to call the `Sub` method on the instance object:</span></span>  
  
 <span data-ttu-id="f73a4-139">*Objeto*. *methodname*`[(`*ArgumentList*`)]`</span><span class="sxs-lookup"><span data-stu-id="f73a4-139">*Object*.*methodname*`[(`*argumentlist*`)]`</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="f73a4-140">Ilustração de declaração e chamada</span><span class="sxs-lookup"><span data-stu-id="f73a4-140">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="f73a4-141">O procedimento a seguir `Sub` informa ao operador do computador qual tarefa o aplicativo está prestes a executar e também exibe um carimbo de data/hora.</span><span class="sxs-lookup"><span data-stu-id="f73a4-141">The following `Sub` procedure tells the computer operator which task the application is about to perform, and also displays a time stamp.</span></span> <span data-ttu-id="f73a4-142">Em vez de duplicar esse código no início de cada tarefa, o aplicativo simplesmente chama `tellOperator` de vários locais.</span><span class="sxs-lookup"><span data-stu-id="f73a4-142">Instead of duplicating this code at the start of every task, the application just calls `tellOperator` from various locations.</span></span> <span data-ttu-id="f73a4-143">Cada chamada passa uma cadeia de caracteres no argumento `task` que identifica a tarefa que está sendo iniciada.</span><span class="sxs-lookup"><span data-stu-id="f73a4-143">Each call passes a string in the `task` argument that identifies the task being started.</span></span>  
  
 [!code-vb[VbVbcnProcedures#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#2)]  
  
 <span data-ttu-id="f73a4-144">O exemplo a seguir mostra uma chamada típica para `tellOperator`.</span><span class="sxs-lookup"><span data-stu-id="f73a4-144">The following example shows a typical call to `tellOperator`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="f73a4-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f73a4-145">See also</span></span>

- [<span data-ttu-id="f73a4-146">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="f73a4-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="f73a4-147">Procedimentos de Função</span><span class="sxs-lookup"><span data-stu-id="f73a4-147">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="f73a4-148">Procedimentos de Propriedade</span><span class="sxs-lookup"><span data-stu-id="f73a4-148">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="f73a4-149">Procedimentos de Operador</span><span class="sxs-lookup"><span data-stu-id="f73a4-149">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="f73a4-150">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="f73a4-150">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="f73a4-151">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="f73a4-151">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="f73a4-152">Como chamar um procedimento que não retorne um valor</span><span class="sxs-lookup"><span data-stu-id="f73a4-152">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)
- [<span data-ttu-id="f73a4-153">Como: chamar um manipulador de eventos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f73a4-153">How to: Call an Event Handler in Visual Basic</span></span>](./how-to-call-an-event-handler.md)
