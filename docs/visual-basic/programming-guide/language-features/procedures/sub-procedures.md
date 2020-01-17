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
ms.openlocfilehash: 9ca1d302a0bc8e989e0b2dddf8cce68e89211d57
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163807"
---
# <a name="sub-procedures-visual-basic"></a><span data-ttu-id="6a70f-102">Sub procedimentos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6a70f-102">Sub procedures (Visual Basic)</span></span>

<span data-ttu-id="6a70f-103">Um procedimento `Sub` é uma série de instruções Visual Basic delimitadas pelas instruções `Sub` e `End Sub`.</span><span class="sxs-lookup"><span data-stu-id="6a70f-103">A `Sub` procedure is a series of Visual Basic statements enclosed by the `Sub` and `End Sub` statements.</span></span> <span data-ttu-id="6a70f-104">O procedimento de `Sub` executa uma tarefa e, em seguida, retorna o controle para o código de chamada, mas não retorna um valor para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="6a70f-104">The `Sub` procedure performs a task and then returns control to the calling code, but it does not return a value to the calling code.</span></span>

<span data-ttu-id="6a70f-105">Cada vez que o procedimento é chamado, suas instruções são executadas, começando com a primeira instrução executável após a instrução de `Sub` e terminando com a primeira instrução `End Sub`, `Exit Sub`ou `Return` encontrada.</span><span class="sxs-lookup"><span data-stu-id="6a70f-105">Each time the procedure is called, its statements are executed, starting with the first executable statement after the `Sub` statement and ending with the first `End Sub`, `Exit Sub`, or `Return` statement encountered.</span></span>

<span data-ttu-id="6a70f-106">Você pode definir um procedimento `Sub` em módulos, classes e estruturas.</span><span class="sxs-lookup"><span data-stu-id="6a70f-106">You can define a `Sub` procedure in modules, classes, and structures.</span></span> <span data-ttu-id="6a70f-107">Por padrão, é `Public`, o que significa que você pode chamá-lo de qualquer lugar em seu aplicativo que tenha acesso ao módulo, à classe ou à estrutura na qual você o definiu.</span><span class="sxs-lookup"><span data-stu-id="6a70f-107">By default, it is `Public`, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span> <span data-ttu-id="6a70f-108">O *método* Term descreve um `Sub` ou `Function` procedimento que é acessado de fora de sua definição de módulo, classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="6a70f-108">The term *method* describes a `Sub` or `Function` procedure that is accessed from outside its defining module, class, or structure.</span></span> <span data-ttu-id="6a70f-109">Para obter mais informações, consulte [Procedimentos](./index.md).</span><span class="sxs-lookup"><span data-stu-id="6a70f-109">For more information, see [Procedures](./index.md).</span></span>

<span data-ttu-id="6a70f-110">Um procedimento `Sub` pode receber argumentos, como constantes, variáveis ou expressões, que são passados para ele pelo código de chamada.</span><span class="sxs-lookup"><span data-stu-id="6a70f-110">A `Sub` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>

## <a name="declaration-syntax"></a><span data-ttu-id="6a70f-111">Sintaxe de declaração</span><span class="sxs-lookup"><span data-stu-id="6a70f-111">Declaration syntax</span></span>

<span data-ttu-id="6a70f-112">A sintaxe para declarar um procedimento `Sub` é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="6a70f-112">The syntax for declaring a `Sub` procedure is as follows:</span></span>

```vb
[modifiers] Sub SubName[(parameterList)]
    ' Statements of the Sub procedure.
End Sub
```

<span data-ttu-id="6a70f-113">O `modifiers` pode especificar o nível de acesso e informações sobre sobrecarga, substituição, compartilhamento e sombreamento.</span><span class="sxs-lookup"><span data-stu-id="6a70f-113">The `modifiers` can specify access level and information about overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="6a70f-114">Para obter mais informações, consulte [sub Statement](../../../language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6a70f-114">For more information, see [Sub Statement](../../../language-reference/statements/sub-statement.md).</span></span>

## <a name="parameter-declaration"></a><span data-ttu-id="6a70f-115">Declaração de parâmetro</span><span class="sxs-lookup"><span data-stu-id="6a70f-115">Parameter declaration</span></span>

<span data-ttu-id="6a70f-116">Você declara cada parâmetro de procedimento da mesma forma como declara uma variável, especificando o nome do parâmetro e o tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="6a70f-116">You declare each procedure parameter similarly to how you declare a variable, specifying the parameter name and data type.</span></span> <span data-ttu-id="6a70f-117">Você também pode especificar o mecanismo de passagem e se o parâmetro é opcional ou uma matriz de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="6a70f-117">You can also specify the passing mechanism, and whether the parameter is optional or a parameter array.</span></span>

<span data-ttu-id="6a70f-118">A sintaxe para cada parâmetro na lista de parâmetros é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="6a70f-118">The syntax for each parameter in the parameter list is as follows:</span></span>

```vb
[Optional] [ByVal | ByRef] [ParamArray] parameterName As DataType
```

<span data-ttu-id="6a70f-119">Se o parâmetro for opcional, você também deverá fornecer um valor padrão como parte de sua declaração.</span><span class="sxs-lookup"><span data-stu-id="6a70f-119">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="6a70f-120">A sintaxe para especificar um valor padrão é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="6a70f-120">The syntax for specifying a default value is as follows:</span></span>

```vb
Optional [ByVal | ByRef]  parameterName As DataType = defaultValue
```

### <a name="parameters-as-local-variables"></a><span data-ttu-id="6a70f-121">Parâmetros como variáveis locais</span><span class="sxs-lookup"><span data-stu-id="6a70f-121">Parameters as local variables</span></span>

<span data-ttu-id="6a70f-122">Quando o controle passa para o procedimento, cada parâmetro é tratado como uma variável local.</span><span class="sxs-lookup"><span data-stu-id="6a70f-122">When control passes to the procedure, each parameter is treated as a local variable.</span></span> <span data-ttu-id="6a70f-123">Isso significa que seu tempo de vida é o mesmo que o do procedimento, e seu escopo é o procedimento completo.</span><span class="sxs-lookup"><span data-stu-id="6a70f-123">This means that its lifetime is the same as that of the procedure, and its scope is the whole procedure.</span></span>

## <a name="calling-syntax"></a><span data-ttu-id="6a70f-124">Sintaxe de chamada</span><span class="sxs-lookup"><span data-stu-id="6a70f-124">Calling syntax</span></span>

<span data-ttu-id="6a70f-125">Você invoca um procedimento `Sub` explicitamente com uma instrução de chamada autônoma.</span><span class="sxs-lookup"><span data-stu-id="6a70f-125">You invoke a `Sub` procedure explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="6a70f-126">Você não pode chamá-lo usando seu nome em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="6a70f-126">You cannot call it by using its name in an expression.</span></span> <span data-ttu-id="6a70f-127">Você deve fornecer valores para todos os argumentos que não são opcionais, e você deve colocar a lista de argumentos entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="6a70f-127">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="6a70f-128">Se nenhum argumento for fornecido, você pode opcionalmente omitir os parênteses.</span><span class="sxs-lookup"><span data-stu-id="6a70f-128">If no arguments are supplied, you can optionally omit the parentheses.</span></span> <span data-ttu-id="6a70f-129">O uso da palavra-chave `Call` é opcional, mas não é recomendado.</span><span class="sxs-lookup"><span data-stu-id="6a70f-129">The use of the `Call` keyword is optional but not recommended.</span></span>

<span data-ttu-id="6a70f-130">A sintaxe de uma chamada para um procedimento `Sub` é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="6a70f-130">The syntax for a call to a `Sub` procedure is as follows:</span></span>

```vb
[Call] SubName[(argumentlist)]
```

<span data-ttu-id="6a70f-131">Você pode chamar um método `Sub` de fora da classe que o define.</span><span class="sxs-lookup"><span data-stu-id="6a70f-131">You can call a `Sub` method from outside the class that defines it.</span></span> <span data-ttu-id="6a70f-132">Primeiro, você precisa usar a palavra-chave `New` para criar uma instância da classe ou chamar um método que retorne uma instância da classe.</span><span class="sxs-lookup"><span data-stu-id="6a70f-132">First, you have to use the `New` keyword to create an instance of the class, or call a method that returns an instance of the class.</span></span> <span data-ttu-id="6a70f-133">Para obter mais informações, consulte [novo operador](../../../language-reference/operators/new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="6a70f-133">For more information, see [New Operator](../../../language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="6a70f-134">Em seguida, você pode usar a seguinte sintaxe para chamar o método `Sub` no objeto de instância:</span><span class="sxs-lookup"><span data-stu-id="6a70f-134">Then, you can use the following syntax to call the `Sub` method on the instance object:</span></span>

```vb
object.MethodName[(argumentList)]
```

### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="6a70f-135">Ilustração de declaração e chamada</span><span class="sxs-lookup"><span data-stu-id="6a70f-135">Illustration of declaration and call</span></span>

<span data-ttu-id="6a70f-136">O procedimento a seguir `Sub` informa ao operador do computador qual tarefa o aplicativo está prestes a executar e também exibe um carimbo de data/hora.</span><span class="sxs-lookup"><span data-stu-id="6a70f-136">The following `Sub` procedure tells the computer operator which task the application is about to perform, and also displays a time stamp.</span></span> <span data-ttu-id="6a70f-137">Em vez de duplicar esse código no início de cada tarefa, o aplicativo simplesmente chama `tellOperator` de vários locais.</span><span class="sxs-lookup"><span data-stu-id="6a70f-137">Instead of duplicating this code at the start of every task, the application just calls `tellOperator` from various locations.</span></span> <span data-ttu-id="6a70f-138">Cada chamada passa uma cadeia de caracteres no argumento `task` que identifica a tarefa que está sendo iniciada.</span><span class="sxs-lookup"><span data-stu-id="6a70f-138">Each call passes a string in the `task` argument that identifies the task being started.</span></span>

[!code-vb[VbVbcnProcedures#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#2)]

<span data-ttu-id="6a70f-139">O exemplo a seguir mostra uma chamada típica para `tellOperator`.</span><span class="sxs-lookup"><span data-stu-id="6a70f-139">The following example shows a typical call to `tellOperator`.</span></span>

[!code-vb[VbVbcnProcedures#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#3)]

## <a name="see-also"></a><span data-ttu-id="6a70f-140">Veja também</span><span class="sxs-lookup"><span data-stu-id="6a70f-140">See also</span></span>

- [<span data-ttu-id="6a70f-141">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="6a70f-141">Procedures</span></span>](./index.md)
- [<span data-ttu-id="6a70f-142">Procedimentos de Função</span><span class="sxs-lookup"><span data-stu-id="6a70f-142">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="6a70f-143">Procedimentos de Propriedade</span><span class="sxs-lookup"><span data-stu-id="6a70f-143">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="6a70f-144">Procedimentos de Operador</span><span class="sxs-lookup"><span data-stu-id="6a70f-144">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="6a70f-145">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="6a70f-145">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="6a70f-146">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="6a70f-146">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="6a70f-147">Como chamar um procedimento que não retorne um valor</span><span class="sxs-lookup"><span data-stu-id="6a70f-147">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)
- [<span data-ttu-id="6a70f-148">Como: chamar um manipulador de eventos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6a70f-148">How to: Call an Event Handler in Visual Basic</span></span>](./how-to-call-an-event-handler.md)
