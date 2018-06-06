---
title: Procedimentos do operador (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
ms.assetid: 8c513d38-246b-4fb7-8b75-29e1364e555b
ms.openlocfilehash: 5b4641ce8509e3111a11ed803d36194d5a301bce
ms.sourcegitcommit: fc70fcb9c789b6a4aefcdace46f3643fd076450f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2018
ms.locfileid: "34805705"
---
# <a name="operator-procedures-visual-basic"></a><span data-ttu-id="ee52a-102">Procedimentos do operador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ee52a-102">Operator Procedures (Visual Basic)</span></span>
<span data-ttu-id="ee52a-103">Um procedimento de operador é uma série de instruções do Visual Basic que definem o comportamento de um operador padrão (como `*`, `<>`, ou `And`) em uma classe ou estrutura que você definiu.</span><span class="sxs-lookup"><span data-stu-id="ee52a-103">An operator procedure is a series of Visual Basic statements that define the behavior of a standard operator (such as `*`, `<>`, or `And`) on a class or structure you have defined.</span></span> <span data-ttu-id="ee52a-104">Isso também é chamado de *sobrecarga de operador*.</span><span class="sxs-lookup"><span data-stu-id="ee52a-104">This is also called *operator overloading*.</span></span>  
  
## <a name="when-to-define-operator-procedures"></a><span data-ttu-id="ee52a-105">Quando definir procedimentos de operador</span><span class="sxs-lookup"><span data-stu-id="ee52a-105">When to Define Operator Procedures</span></span>  
 <span data-ttu-id="ee52a-106">Quando você tiver definido uma classe ou estrutura, você pode declarar variáveis sejam do tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="ee52a-106">When you have defined a class or structure, you can declare variables to be of the type of that class or structure.</span></span> <span data-ttu-id="ee52a-107">Às vezes, tal variável precisa participar de uma operação como parte de uma expressão.</span><span class="sxs-lookup"><span data-stu-id="ee52a-107">Sometimes such a variable needs to participate in an operation as part of an expression.</span></span> <span data-ttu-id="ee52a-108">Para fazer isso, ele deve ser um operando de um operador.</span><span class="sxs-lookup"><span data-stu-id="ee52a-108">To do this, it must be an operand of an operator.</span></span>  
  
 <span data-ttu-id="ee52a-109">Visual Basic define operadores somente em seu tipo de dados básico.</span><span class="sxs-lookup"><span data-stu-id="ee52a-109">Visual Basic defines operators only on its fundamental data types.</span></span> <span data-ttu-id="ee52a-110">Você pode definir o comportamento de um operador quando um ou ambos os operandos são do tipo de sua classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="ee52a-110">You can define the behavior of an operator when one or both of the operands are of the type of your class or structure.</span></span>  
  
 <span data-ttu-id="ee52a-111">Para obter mais informações, consulte [instrução Operator](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ee52a-111">For more information, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
## <a name="types-of-operator-procedure"></a><span data-ttu-id="ee52a-112">Tipos de procedimento de operador</span><span class="sxs-lookup"><span data-stu-id="ee52a-112">Types of Operator Procedure</span></span>  
 <span data-ttu-id="ee52a-113">Um procedimento de operador pode ser um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="ee52a-113">An operator procedure can be one of the following types:</span></span>  
  
-   <span data-ttu-id="ee52a-114">Uma definição de um operador unário onde o argumento é do tipo de sua classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="ee52a-114">A definition of a unary operator where the argument is of the type of your class or structure.</span></span>  
  
-   <span data-ttu-id="ee52a-115">Uma definição de um operador binário onde pelo menos um dos argumentos é do tipo de sua classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="ee52a-115">A definition of a binary operator where at least one of the arguments is of the type of your class or structure.</span></span>  
  
-   <span data-ttu-id="ee52a-116">Uma definição de um operador de conversão onde o argumento é do tipo de sua classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="ee52a-116">A definition of a conversion operator where the argument is of the type of your class or structure.</span></span>  
  
-   <span data-ttu-id="ee52a-117">Uma definição de um operador de conversão que retorna o tipo de sua classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="ee52a-117">A definition of a conversion operator that returns the type of your class or structure.</span></span>  
  
 <span data-ttu-id="ee52a-118">Operadores de conversão são sempre unários, e você sempre usar `CType` como o operador que você está definindo.</span><span class="sxs-lookup"><span data-stu-id="ee52a-118">Conversion operators are always unary, and you always use `CType` as the operator you are defining.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="ee52a-119">Sintaxe da Declaração</span><span class="sxs-lookup"><span data-stu-id="ee52a-119">Declaration Syntax</span></span>  
 <span data-ttu-id="ee52a-120">A sintaxe para declarar um procedimento de operador é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="ee52a-120">The syntax for declaring an operator procedure is as follows:</span></span>  
  
 <span data-ttu-id="ee52a-121">`Public Shared`   `[Widening | Narrowing]`   `Operator`  *operatorsymbol* `(` *operando1*`[,`*operand2* `]) As` *tipo de dados*</span><span class="sxs-lookup"><span data-stu-id="ee52a-121">`Public Shared`   `[Widening | Narrowing]`   `Operator`  *operatorsymbol*  `(` *operand1*  `[,`  *operand2* `]) As`  *datatype*</span></span>  
  
 `' Statements of the operator procedure.`  
  
 `End Operator`  
  
 <span data-ttu-id="ee52a-122">Você usa o `Widening` ou `Narrowing` palavra-chave somente em um operador de conversão de tipo.</span><span class="sxs-lookup"><span data-stu-id="ee52a-122">You use the `Widening` or `Narrowing` keyword only on a type conversion operator.</span></span> <span data-ttu-id="ee52a-123">O símbolo do operador é sempre [função CType](../../../../visual-basic/language-reference/functions/ctype-function.md) para um operador de conversão de tipo.</span><span class="sxs-lookup"><span data-stu-id="ee52a-123">The operator symbol is always [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) for a type conversion operator.</span></span>  
  
 <span data-ttu-id="ee52a-124">Você declara dois operandos para definir um operador binário, e declara um operando para definir um operador unário, incluindo um operador de conversão de tipo.</span><span class="sxs-lookup"><span data-stu-id="ee52a-124">You declare two operands to define a binary operator, and you declare one operand to define a unary operator, including a type conversion operator.</span></span> <span data-ttu-id="ee52a-125">Todos os operandos devem ser declarados `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="ee52a-125">All operands must be declared `ByVal`.</span></span>  
  
 <span data-ttu-id="ee52a-126">Você declara cada operando da mesma maneira que você declarar parâmetros para [subprocedimentos](./sub-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="ee52a-126">You declare each operand the same way you declare parameters for [Sub Procedures](./sub-procedures.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="ee52a-127">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="ee52a-127">Data Type</span></span>  
 <span data-ttu-id="ee52a-128">Como você está definindo um operador em uma classe ou estrutura que você definiu, pelo menos um dos operandos deve ser do tipo de dados da classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="ee52a-128">Because you are defining an operator on a class or structure you have defined, at least one of the operands must be of the data type of that class or structure.</span></span> <span data-ttu-id="ee52a-129">Para um operador de conversão de tipo, o operando ou o tipo de retorno deve ser do tipo de dados da classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="ee52a-129">For a type conversion operator, either the operand or the return type must be of the data type of the class or structure.</span></span>  
  
 <span data-ttu-id="ee52a-130">Para obter mais detalhes, consulte [instrução Operator](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ee52a-130">For more details, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="ee52a-131">A sintaxe de chamada</span><span class="sxs-lookup"><span data-stu-id="ee52a-131">Calling Syntax</span></span>  
 <span data-ttu-id="ee52a-132">Você chamar um procedimento de operador implicitamente, usando o símbolo do operador em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="ee52a-132">You invoke an operator procedure implicitly by using the operator symbol in an expression.</span></span> <span data-ttu-id="ee52a-133">Você fornece os operandos da mesma maneira que faria para operadores predefinidos.</span><span class="sxs-lookup"><span data-stu-id="ee52a-133">You supply the operands the same way you do for predefined operators.</span></span>  
  
 <span data-ttu-id="ee52a-134">A sintaxe para chamar um procedimento de operador implícito é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="ee52a-134">The syntax for an implicit call to an operator procedure is as follows:</span></span>  
  
 <span data-ttu-id="ee52a-135">`Dim testStruct As`  *structurename*</span><span class="sxs-lookup"><span data-stu-id="ee52a-135">`Dim testStruct As`  *structurename*</span></span>  
  
 <span data-ttu-id="ee52a-136">`Dim testNewStruct As`  *structurename*`= testStruct`*operatorsymbol*  `10`</span><span class="sxs-lookup"><span data-stu-id="ee52a-136">`Dim testNewStruct As`  *structurename*  `= testStruct`  *operatorsymbol*  `10`</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="ee52a-137">Ilustração da declaração e chamada</span><span class="sxs-lookup"><span data-stu-id="ee52a-137">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="ee52a-138">A seguinte estrutura armazena um valor inteiro assinado de 128 bits como as partes superiores e inferiores constituintes.</span><span class="sxs-lookup"><span data-stu-id="ee52a-138">The following structure stores a signed 128-bit integer value as the constituent high-order and low-order parts.</span></span> <span data-ttu-id="ee52a-139">Define o `+` para adicionar dois `veryLong` valores e gerar um resultante `veryLong` valor.</span><span class="sxs-lookup"><span data-stu-id="ee52a-139">It defines the `+` operator to add two `veryLong` values and generate a resulting `veryLong` value.</span></span>  
  
 [!code-vb[VbVbcnProcedures#23](./codesnippet/VisualBasic/operator-procedures_1.vb)]  
  
 <span data-ttu-id="ee52a-140">O exemplo a seguir mostra uma chamada típica para o `+` operador definido em `veryLong`.</span><span class="sxs-lookup"><span data-stu-id="ee52a-140">The following example shows a typical call to the `+` operator defined on `veryLong`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#24](./codesnippet/VisualBasic/operator-procedures_2.vb)]  
  
 <span data-ttu-id="ee52a-141">Para obter mais informações e exemplos, consulte [Sobrecarga de operador no Visual Basic 2005](https://msdn.microsoft.com/library/ms379613(v=vs.80).aspx).</span><span class="sxs-lookup"><span data-stu-id="ee52a-141">For more information and examples, see [Operator Overloading in Visual Basic 2005](https://msdn.microsoft.com/library/ms379613(v=vs.80).aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee52a-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ee52a-142">See Also</span></span>  
 [<span data-ttu-id="ee52a-143">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="ee52a-143">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="ee52a-144">Subprocedimentos</span><span class="sxs-lookup"><span data-stu-id="ee52a-144">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="ee52a-145">Procedimentos de Função</span><span class="sxs-lookup"><span data-stu-id="ee52a-145">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="ee52a-146">Procedimentos de Propriedade</span><span class="sxs-lookup"><span data-stu-id="ee52a-146">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="ee52a-147">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="ee52a-147">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="ee52a-148">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="ee52a-148">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="ee52a-149">Como definir um operador</span><span class="sxs-lookup"><span data-stu-id="ee52a-149">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)  
 [<span data-ttu-id="ee52a-150">Como definir um operador de conversão</span><span class="sxs-lookup"><span data-stu-id="ee52a-150">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="ee52a-151">Como chamar um procedimento de operador</span><span class="sxs-lookup"><span data-stu-id="ee52a-151">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)  
 [<span data-ttu-id="ee52a-152">Como usar uma classe que define operadores</span><span class="sxs-lookup"><span data-stu-id="ee52a-152">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
