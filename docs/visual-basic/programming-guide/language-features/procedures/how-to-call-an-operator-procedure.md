---
title: 'Como: chamar um procedimento de operador (Visual Basic) | Documentos do Microsoft'
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
- operator procedures, calling
- procedures, operator
- procedure calls, operator overloading
- syntax, Operator procedures
- operators [Visual Basic], overloading
- return values, Operator procedures
- overloaded operators, calling
- operator overloading
ms.assetid: 0dce42cc-f0b0-4c14-9f62-018b21f33497
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: cd85a14a6f5534e90497268134f4b2b0cc292249
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a><span data-ttu-id="5f9ce-102">Como chamar um procedimento de operador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f9ce-102">How to: Call an Operator Procedure (Visual Basic)</span></span>
<span data-ttu-id="5f9ce-103">Você pode chamar um procedimento de operador usando o símbolo do operador em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="5f9ce-103">You call an operator procedure by using the operator symbol in an expression.</span></span> <span data-ttu-id="5f9ce-104">No caso de um operador de conversão, você chama o [função CType](../../../../visual-basic/language-reference/functions/ctype-function.md) para converter um valor de um tipo de dados para outro.</span><span class="sxs-lookup"><span data-stu-id="5f9ce-104">In the case of a conversion operator, you call the [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) to convert a value from one data type to another.</span></span>  
  
 <span data-ttu-id="5f9ce-105">Você não chama explicitamente procedimentos de operador.</span><span class="sxs-lookup"><span data-stu-id="5f9ce-105">You do not call operator procedures explicitly.</span></span> <span data-ttu-id="5f9ce-106">Você apenas usa o operador, ou o `CType` função em uma instrução de atribuição ou uma expressão, da mesma maneira que você normalmente usa um operador.</span><span class="sxs-lookup"><span data-stu-id="5f9ce-106">You just use the operator, or the `CType` function, in an assignment statement or an expression, the same way you ordinarily use an operator.</span></span> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="5f9ce-107">faz a chamada para o procedimento de operador.</span><span class="sxs-lookup"><span data-stu-id="5f9ce-107"> makes the call to the operator procedure.</span></span>  
  
 <span data-ttu-id="5f9ce-108">Definir um operador em uma classe ou estrutura também é chamado *sobrecarga* o operador.</span><span class="sxs-lookup"><span data-stu-id="5f9ce-108">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
### <a name="to-call-an-operator-procedure"></a><span data-ttu-id="5f9ce-109">Para chamar um procedimento de operador</span><span class="sxs-lookup"><span data-stu-id="5f9ce-109">To call an operator procedure</span></span>  
  
1.  <span data-ttu-id="5f9ce-110">Use o símbolo do operador em uma expressão na forma comum.</span><span class="sxs-lookup"><span data-stu-id="5f9ce-110">Use the operator symbol in an expression in the ordinary way.</span></span>  
  
2.  <span data-ttu-id="5f9ce-111">Certifique-se de que os tipos de dados dos operandos são apropriados para o operador e estão na ordem correta.</span><span class="sxs-lookup"><span data-stu-id="5f9ce-111">Be sure the data types of the operands are appropriate for the operator, and in the correct order.</span></span>  
  
3.  <span data-ttu-id="5f9ce-112">O operador contribui para o valor da expressão conforme o esperado.</span><span class="sxs-lookup"><span data-stu-id="5f9ce-112">The operator contributes to the value of the expression as expected.</span></span>  
  
### <a name="to-call-a-conversion-operator-procedure"></a><span data-ttu-id="5f9ce-113">Para chamar um procedimento de operador de conversão</span><span class="sxs-lookup"><span data-stu-id="5f9ce-113">To call a conversion operator procedure</span></span>  
  
1.  <span data-ttu-id="5f9ce-114">Use `CType` dentro de uma expressão.</span><span class="sxs-lookup"><span data-stu-id="5f9ce-114">Use `CType` inside an expression.</span></span>  
  
2.  <span data-ttu-id="5f9ce-115">Certifique-se de que os tipos de dados dos operandos são apropriados para a conversão e estão na ordem correta.</span><span class="sxs-lookup"><span data-stu-id="5f9ce-115">Be sure the data types of the operands are appropriate for the conversion, and in the correct order.</span></span>  
  
3.  <span data-ttu-id="5f9ce-116">`CType`chama o procedimento de operador de conversão e retorna o valor convertido.</span><span class="sxs-lookup"><span data-stu-id="5f9ce-116">`CType` calls the conversion operator procedure and returns the converted value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f9ce-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5f9ce-117">Example</span></span>  
 <span data-ttu-id="5f9ce-118">O exemplo a seguir cria dois <xref:System.TimeSpan>estruturas, adiciona-as e armazena o resultado em uma terceira <xref:System.TimeSpan>estrutura.</xref:System.TimeSpan> </xref:System.TimeSpan></span><span class="sxs-lookup"><span data-stu-id="5f9ce-118">The following example creates two <xref:System.TimeSpan> structures, adds them together, and stores the result in a third <xref:System.TimeSpan> structure.</span></span> <span data-ttu-id="5f9ce-119">O <xref:System.TimeSpan>estrutura define procedimentos de operador para sobrecarregar vários operadores padrão.</xref:System.TimeSpan></span><span class="sxs-lookup"><span data-stu-id="5f9ce-119">The <xref:System.TimeSpan> structure defines operator procedures to overload several standard operators.</span></span>  
  
 <span data-ttu-id="5f9ce-120">[!code-vb[29 VbVbcnProcedures](./codesnippet/VisualBasic/how-to-call-an-operator-procedure_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="5f9ce-120">[!code-vb[VbVbcnProcedures#29](./codesnippet/VisualBasic/how-to-call-an-operator-procedure_1.vb)]</span></span>  
  
 <span data-ttu-id="5f9ce-121">Porque <xref:System.TimeSpan>sobrecarrega o padrão `+` operador, o exemplo anterior chama um procedimento de operador quando ele calcula o valor de `combinedSpan`.</xref:System.TimeSpan></span><span class="sxs-lookup"><span data-stu-id="5f9ce-121">Because <xref:System.TimeSpan> overloads the standard `+` operator, the previous example calls an operator procedure when it calculates the value of `combinedSpan`.</span></span>  
  
 <span data-ttu-id="5f9ce-122">Para obter um exemplo de chamar um procedimento de operador de conversa, consulte [como: usar uma classe que define operadores](./how-to-use-a-class-that-defines-operators.md).</span><span class="sxs-lookup"><span data-stu-id="5f9ce-122">For an example of calling a conversation operator procedure, see [How to: Use a Class that Defines Operators](./how-to-use-a-class-that-defines-operators.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5f9ce-123">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="5f9ce-123">Compiling the Code</span></span>  
 <span data-ttu-id="5f9ce-124">Certifique-se de que a classe ou estrutura que você está usando define o operador que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="5f9ce-124">Be sure the class or structure you are using defines the operator you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f9ce-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5f9ce-125">See Also</span></span>  
 <span data-ttu-id="5f9ce-126">[Procedimentos de operador](./operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="5f9ce-126">[Operator Procedures](./operator-procedures.md) </span></span>  
<span data-ttu-id="5f9ce-127"> [Como: definir um operador](./how-to-define-an-operator.md) </span><span class="sxs-lookup"><span data-stu-id="5f9ce-127"> [How to: Define an Operator](./how-to-define-an-operator.md) </span></span>  
<span data-ttu-id="5f9ce-128"> [Como: definir um operador de conversão](./how-to-define-a-conversion-operator.md) </span><span class="sxs-lookup"><span data-stu-id="5f9ce-128"> [How to: Define a Conversion Operator](./how-to-define-a-conversion-operator.md) </span></span>  
<span data-ttu-id="5f9ce-129"> [Instrução Operator](../../../../visual-basic/language-reference/statements/operator-statement.md) </span><span class="sxs-lookup"><span data-stu-id="5f9ce-129"> [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md) </span></span>  
<span data-ttu-id="5f9ce-130"> [Ampliação](../../../../visual-basic/language-reference/modifiers/widening.md) </span><span class="sxs-lookup"><span data-stu-id="5f9ce-130"> [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) </span></span>  
<span data-ttu-id="5f9ce-131"> [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md) </span><span class="sxs-lookup"><span data-stu-id="5f9ce-131"> [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md) </span></span>  
<span data-ttu-id="5f9ce-132"> [Instrução Structure](../../../../visual-basic/language-reference/statements/structure-statement.md) </span><span class="sxs-lookup"><span data-stu-id="5f9ce-132"> [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md) </span></span>  
<span data-ttu-id="5f9ce-133"> [Como: declarar uma estrutura](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md) </span><span class="sxs-lookup"><span data-stu-id="5f9ce-133"> [How to: Declare a Structure](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md) </span></span>  
<span data-ttu-id="5f9ce-134"> [Conversões implícitas e explícitas](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="5f9ce-134"> [Implicit and Explicit Conversions](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) </span></span>  
<span data-ttu-id="5f9ce-135"> [Conversões de Widening e Narrowing](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)</span><span class="sxs-lookup"><span data-stu-id="5f9ce-135"> [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)</span></span>
