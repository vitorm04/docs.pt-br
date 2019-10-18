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
ms.openlocfilehash: 46afbbe411a1adf27960e3c7d9d3ca98046ecec5
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524532"
---
# <a name="operator-procedures-visual-basic"></a><span data-ttu-id="5a156-102">Procedimentos do operador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a156-102">Operator Procedures (Visual Basic)</span></span>

<span data-ttu-id="5a156-103">Um procedimento de operador é uma série de instruções Visual Basic que definem o comportamento de um operador padrão (como `*`, `<>` ou `And`) em uma classe ou estrutura que você definiu.</span><span class="sxs-lookup"><span data-stu-id="5a156-103">An operator procedure is a series of Visual Basic statements that define the behavior of a standard operator (such as `*`, `<>`, or `And`) on a class or structure you have defined.</span></span> <span data-ttu-id="5a156-104">Isso também é chamado de *sobrecarga de operador*.</span><span class="sxs-lookup"><span data-stu-id="5a156-104">This is also called *operator overloading*.</span></span>

## <a name="when-to-define-operator-procedures"></a><span data-ttu-id="5a156-105">Quando definir procedimentos de operador</span><span class="sxs-lookup"><span data-stu-id="5a156-105">When to Define Operator Procedures</span></span>

<span data-ttu-id="5a156-106">Quando você tiver definido uma classe ou estrutura, poderá declarar variáveis como sendo do tipo dessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="5a156-106">When you have defined a class or structure, you can declare variables to be of the type of that class or structure.</span></span> <span data-ttu-id="5a156-107">Às vezes, essa variável precisa participar de uma operação como parte de uma expressão.</span><span class="sxs-lookup"><span data-stu-id="5a156-107">Sometimes such a variable needs to participate in an operation as part of an expression.</span></span> <span data-ttu-id="5a156-108">Para fazer isso, ele deve ser um operando de um operador.</span><span class="sxs-lookup"><span data-stu-id="5a156-108">To do this, it must be an operand of an operator.</span></span>

<span data-ttu-id="5a156-109">Visual Basic define operadores somente em seus tipos de dados fundamentais.</span><span class="sxs-lookup"><span data-stu-id="5a156-109">Visual Basic defines operators only on its fundamental data types.</span></span> <span data-ttu-id="5a156-110">Você pode definir o comportamento de um operador quando um ou ambos os operandos forem do tipo de sua classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="5a156-110">You can define the behavior of an operator when one or both of the operands are of the type of your class or structure.</span></span>

<span data-ttu-id="5a156-111">Para obter mais informações, consulte [instrução Operator](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5a156-111">For more information, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>

## <a name="types-of-operator-procedure"></a><span data-ttu-id="5a156-112">Tipos de procedimento de operador</span><span class="sxs-lookup"><span data-stu-id="5a156-112">Types of Operator Procedure</span></span>

<span data-ttu-id="5a156-113">Um procedimento de operador pode ser um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="5a156-113">An operator procedure can be one of the following types:</span></span>

- <span data-ttu-id="5a156-114">Uma definição de um operador unário em que o argumento é do tipo de sua classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="5a156-114">A definition of a unary operator where the argument is of the type of your class or structure.</span></span>

- <span data-ttu-id="5a156-115">Uma definição de um operador binário em que pelo menos um dos argumentos é do tipo de sua classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="5a156-115">A definition of a binary operator where at least one of the arguments is of the type of your class or structure.</span></span>

- <span data-ttu-id="5a156-116">Uma definição de um operador de conversão em que o argumento é do tipo de sua classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="5a156-116">A definition of a conversion operator where the argument is of the type of your class or structure.</span></span>

- <span data-ttu-id="5a156-117">Uma definição de um operador de conversão que retorna o tipo de sua classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="5a156-117">A definition of a conversion operator that returns the type of your class or structure.</span></span>

 <span data-ttu-id="5a156-118">Os operadores de conversão são sempre unários e você sempre usa `CType` como o operador que está definindo.</span><span class="sxs-lookup"><span data-stu-id="5a156-118">Conversion operators are always unary, and you always use `CType` as the operator you are defining.</span></span>

## <a name="declaration-syntax"></a><span data-ttu-id="5a156-119">Sintaxe da Declaração</span><span class="sxs-lookup"><span data-stu-id="5a156-119">Declaration Syntax</span></span>

<span data-ttu-id="5a156-120">A sintaxe para declarar um procedimento de operador é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="5a156-120">The syntax for declaring an operator procedure is as follows:</span></span>

```vb
Public Shared [Widening | Narrowing] Operator operatorsymbol ( operand1 [,  operand2 ]) As datatype

' Statements of the operator procedure.

End Operator
```

<span data-ttu-id="5a156-121">Você usa a palavra-chave `Widening` ou `Narrowing` apenas em um operador de conversão de tipo.</span><span class="sxs-lookup"><span data-stu-id="5a156-121">You use the `Widening` or `Narrowing` keyword only on a type conversion operator.</span></span> <span data-ttu-id="5a156-122">O símbolo de operador é sempre a [função CType](../../../../visual-basic/language-reference/functions/ctype-function.md) para um operador de conversão de tipo.</span><span class="sxs-lookup"><span data-stu-id="5a156-122">The operator symbol is always [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) for a type conversion operator.</span></span>

<span data-ttu-id="5a156-123">Você declara dois operandos para definir um operador binário e declara um operando para definir um operador unário, incluindo um operador de conversão de tipo.</span><span class="sxs-lookup"><span data-stu-id="5a156-123">You declare two operands to define a binary operator, and you declare one operand to define a unary operator, including a type conversion operator.</span></span> <span data-ttu-id="5a156-124">Todos os operandos devem ser declarados `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="5a156-124">All operands must be declared `ByVal`.</span></span>

<span data-ttu-id="5a156-125">Você declara cada operando da mesma maneira que declara parâmetros para [procedimentos sub](./sub-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="5a156-125">You declare each operand the same way you declare parameters for [Sub Procedures](./sub-procedures.md).</span></span>

### <a name="data-type"></a><span data-ttu-id="5a156-126">Tipo de dados</span><span class="sxs-lookup"><span data-stu-id="5a156-126">Data Type</span></span>

<span data-ttu-id="5a156-127">Como você está definindo um operador em uma classe ou estrutura que você definiu, pelo menos um dos operandos deve ser do tipo de dados dessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="5a156-127">Because you are defining an operator on a class or structure you have defined, at least one of the operands must be of the data type of that class or structure.</span></span> <span data-ttu-id="5a156-128">Para um operador de conversão de tipo, o operando ou o tipo de retorno deve ser do tipo de dados da classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="5a156-128">For a type conversion operator, either the operand or the return type must be of the data type of the class or structure.</span></span>

<span data-ttu-id="5a156-129">Para obter mais detalhes, consulte a [instrução Operator](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5a156-129">For more details, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>

## <a name="calling-syntax"></a><span data-ttu-id="5a156-130">Sintaxe de chamada</span><span class="sxs-lookup"><span data-stu-id="5a156-130">Calling Syntax</span></span>

<span data-ttu-id="5a156-131">Você invoca um procedimento de operador implicitamente usando o símbolo do operador em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="5a156-131">You invoke an operator procedure implicitly by using the operator symbol in an expression.</span></span> <span data-ttu-id="5a156-132">Você fornece os operandos da mesma maneira que faz para operadores predefinidos.</span><span class="sxs-lookup"><span data-stu-id="5a156-132">You supply the operands the same way you do for predefined operators.</span></span>

<span data-ttu-id="5a156-133">A sintaxe de uma chamada implícita para um procedimento de operador é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="5a156-133">The syntax for an implicit call to an operator procedure is as follows:</span></span>

<span data-ttu-id="5a156-134">`Dim testStruct As`  *structurename*</span><span class="sxs-lookup"><span data-stu-id="5a156-134">`Dim testStruct As`  *structurename*</span></span>

<span data-ttu-id="5a156-135">`Dim testNewStruct As`*structurename* `= testStruct`*operatorsymbol* `10`</span><span class="sxs-lookup"><span data-stu-id="5a156-135">`Dim testNewStruct As`  *structurename*  `= testStruct`  *operatorsymbol*  `10`</span></span>

### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="5a156-136">Ilustração de declaração e chamada</span><span class="sxs-lookup"><span data-stu-id="5a156-136">Illustration of Declaration and Call</span></span>

<span data-ttu-id="5a156-137">A estrutura a seguir armazena um valor inteiro de 128 bits assinado como as partes de ordem superior e de ordem inferior do constituinte.</span><span class="sxs-lookup"><span data-stu-id="5a156-137">The following structure stores a signed 128-bit integer value as the constituent high-order and low-order parts.</span></span> <span data-ttu-id="5a156-138">Ele define o operador de `+` para adicionar dois valores de `veryLong` e gerar um valor de `veryLong` resultante.</span><span class="sxs-lookup"><span data-stu-id="5a156-138">It defines the `+` operator to add two `veryLong` values and generate a resulting `veryLong` value.</span></span>

[!code-vb[VbVbcnProcedures#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#23)]

<span data-ttu-id="5a156-139">O exemplo a seguir mostra uma chamada típica para o operador de `+` definido em `veryLong`.</span><span class="sxs-lookup"><span data-stu-id="5a156-139">The following example shows a typical call to the `+` operator defined on `veryLong`.</span></span>

[!code-vb[VbVbcnProcedures#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#24)]

## <a name="see-also"></a><span data-ttu-id="5a156-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5a156-140">See also</span></span>

- [<span data-ttu-id="5a156-141">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="5a156-141">Procedures</span></span>](./index.md)
- [<span data-ttu-id="5a156-142">Subprocedimentos</span><span class="sxs-lookup"><span data-stu-id="5a156-142">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="5a156-143">Procedimentos de Função</span><span class="sxs-lookup"><span data-stu-id="5a156-143">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="5a156-144">Procedimentos de Propriedade</span><span class="sxs-lookup"><span data-stu-id="5a156-144">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="5a156-145">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="5a156-145">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="5a156-146">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="5a156-146">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="5a156-147">Como definir um operador</span><span class="sxs-lookup"><span data-stu-id="5a156-147">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="5a156-148">Como definir um operador de conversão</span><span class="sxs-lookup"><span data-stu-id="5a156-148">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="5a156-149">Como chamar um procedimento de operador</span><span class="sxs-lookup"><span data-stu-id="5a156-149">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="5a156-150">Como usar uma classe que define operadores</span><span class="sxs-lookup"><span data-stu-id="5a156-150">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
