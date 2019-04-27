---
title: 'Como: Chamar um procedimento de operador (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedure calls [Visual Basic], operator overloading
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- overloaded operators [Visual Basic], calling
- operator overloading
ms.assetid: 0dce42cc-f0b0-4c14-9f62-018b21f33497
ms.openlocfilehash: d68781aa12ab7c1c717031ca252c5f3120649edc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61863929"
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a><span data-ttu-id="ba8b8-102">Como: Chamar um procedimento de operador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba8b8-102">How to: Call an Operator Procedure (Visual Basic)</span></span>
<span data-ttu-id="ba8b8-103">Você pode chamar um procedimento de operador, usando o símbolo do operador em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="ba8b8-103">You call an operator procedure by using the operator symbol in an expression.</span></span> <span data-ttu-id="ba8b8-104">No caso de um operador de conversão, você chama o [função CType](../../../../visual-basic/language-reference/functions/ctype-function.md) para converter um valor de um tipo de dados para outro.</span><span class="sxs-lookup"><span data-stu-id="ba8b8-104">In the case of a conversion operator, you call the [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) to convert a value from one data type to another.</span></span>  
  
 <span data-ttu-id="ba8b8-105">Você não pode chamar procedimentos de operador explicitamente.</span><span class="sxs-lookup"><span data-stu-id="ba8b8-105">You do not call operator procedures explicitly.</span></span> <span data-ttu-id="ba8b8-106">Você apenas usa o operador, ou o `CType` função em uma instrução de atribuição ou uma expressão, da mesma maneira que você normalmente usa um operador.</span><span class="sxs-lookup"><span data-stu-id="ba8b8-106">You just use the operator, or the `CType` function, in an assignment statement or an expression, the same way you ordinarily use an operator.</span></span> <span data-ttu-id="ba8b8-107">Visual Basic faz a chamada para o procedimento de operador.</span><span class="sxs-lookup"><span data-stu-id="ba8b8-107">Visual Basic makes the call to the operator procedure.</span></span>  
  
 <span data-ttu-id="ba8b8-108">Definir um operador em uma classe ou estrutura também é chamado *sobrecarga* o operador.</span><span class="sxs-lookup"><span data-stu-id="ba8b8-108">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
### <a name="to-call-an-operator-procedure"></a><span data-ttu-id="ba8b8-109">Para chamar um procedimento de operador</span><span class="sxs-lookup"><span data-stu-id="ba8b8-109">To call an operator procedure</span></span>  
  
1. <span data-ttu-id="ba8b8-110">Use o símbolo do operador em uma expressão na forma comum.</span><span class="sxs-lookup"><span data-stu-id="ba8b8-110">Use the operator symbol in an expression in the ordinary way.</span></span>  
  
2. <span data-ttu-id="ba8b8-111">Certifique-se de que os tipos de dados dos operandos são apropriados para o operador e na ordem correta.</span><span class="sxs-lookup"><span data-stu-id="ba8b8-111">Be sure the data types of the operands are appropriate for the operator, and in the correct order.</span></span>  
  
3. <span data-ttu-id="ba8b8-112">O operador contribui para o valor da expressão conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="ba8b8-112">The operator contributes to the value of the expression as expected.</span></span>  
  
### <a name="to-call-a-conversion-operator-procedure"></a><span data-ttu-id="ba8b8-113">Para chamar um procedimento de operador de conversão</span><span class="sxs-lookup"><span data-stu-id="ba8b8-113">To call a conversion operator procedure</span></span>  
  
1. <span data-ttu-id="ba8b8-114">Use `CType` dentro de uma expressão.</span><span class="sxs-lookup"><span data-stu-id="ba8b8-114">Use `CType` inside an expression.</span></span>  
  
2. <span data-ttu-id="ba8b8-115">Certifique-se de que os tipos de dados dos operandos são apropriados para a conversão e na ordem correta.</span><span class="sxs-lookup"><span data-stu-id="ba8b8-115">Be sure the data types of the operands are appropriate for the conversion, and in the correct order.</span></span>  
  
3. <span data-ttu-id="ba8b8-116">`CType` chama o procedimento de operador de conversão e retorna o valor convertido.</span><span class="sxs-lookup"><span data-stu-id="ba8b8-116">`CType` calls the conversion operator procedure and returns the converted value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba8b8-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ba8b8-117">Example</span></span>  
 <span data-ttu-id="ba8b8-118">O exemplo a seguir cria dois <xref:System.TimeSpan> estruturas, adiciona-os juntos e armazena o resultado em uma terceira <xref:System.TimeSpan> estrutura.</span><span class="sxs-lookup"><span data-stu-id="ba8b8-118">The following example creates two <xref:System.TimeSpan> structures, adds them together, and stores the result in a third <xref:System.TimeSpan> structure.</span></span> <span data-ttu-id="ba8b8-119">O <xref:System.TimeSpan> estrutura define procedimentos de operador para sobrecarregar vários operadores padrão.</span><span class="sxs-lookup"><span data-stu-id="ba8b8-119">The <xref:System.TimeSpan> structure defines operator procedures to overload several standard operators.</span></span>  
  
 [!code-vb[VbVbcnProcedures#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#29)]  
  
 <span data-ttu-id="ba8b8-120">Porque <xref:System.TimeSpan> sobrecarrega o padrão `+` operador, o exemplo anterior chama um procedimento de operador quando ele calcula o valor de `combinedSpan`.</span><span class="sxs-lookup"><span data-stu-id="ba8b8-120">Because <xref:System.TimeSpan> overloads the standard `+` operator, the previous example calls an operator procedure when it calculates the value of `combinedSpan`.</span></span>  
  
 <span data-ttu-id="ba8b8-121">Para obter um exemplo de como chamar um procedimento de operador de conversa, consulte [como: Usar uma classe que define operadores](./how-to-use-a-class-that-defines-operators.md).</span><span class="sxs-lookup"><span data-stu-id="ba8b8-121">For an example of calling a conversation operator procedure, see [How to: Use a Class that Defines Operators](./how-to-use-a-class-that-defines-operators.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ba8b8-122">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="ba8b8-122">Compiling the Code</span></span>  
 <span data-ttu-id="ba8b8-123">Certifique-se de que a classe ou estrutura que você está usando define o operador que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="ba8b8-123">Be sure the class or structure you are using defines the operator you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba8b8-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ba8b8-124">See also</span></span>

- [<span data-ttu-id="ba8b8-125">Procedimentos de Operador</span><span class="sxs-lookup"><span data-stu-id="ba8b8-125">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="ba8b8-126">Como: Definir um operador</span><span class="sxs-lookup"><span data-stu-id="ba8b8-126">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="ba8b8-127">Como: Definir um operador de conversão</span><span class="sxs-lookup"><span data-stu-id="ba8b8-127">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="ba8b8-128">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="ba8b8-128">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="ba8b8-129">Ampliação</span><span class="sxs-lookup"><span data-stu-id="ba8b8-129">Widening</span></span>](../../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="ba8b8-130">Narrowing</span><span class="sxs-lookup"><span data-stu-id="ba8b8-130">Narrowing</span></span>](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="ba8b8-131">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="ba8b8-131">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="ba8b8-132">Como: declarar uma estrutura</span><span class="sxs-lookup"><span data-stu-id="ba8b8-132">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="ba8b8-133">Conversões Implícitas e Explícitas</span><span class="sxs-lookup"><span data-stu-id="ba8b8-133">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="ba8b8-134">Conversões de Widening e Narrowing</span><span class="sxs-lookup"><span data-stu-id="ba8b8-134">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
