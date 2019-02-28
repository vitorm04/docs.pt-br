---
title: 'Como: Usar uma classe que define operadores (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedures [Visual Basic], calling
- examples [Visual Basic], CType
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 7ccce94a-6ca0-47d1-9f3f-13385d34f5d5
ms.openlocfilehash: 358e81904f48ad844351a20a448b615a0fef8f89
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972503"
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a><span data-ttu-id="b9bef-102">Como: Usar uma classe que define operadores (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9bef-102">How to: Use a Class that Defines Operators (Visual Basic)</span></span>
<span data-ttu-id="b9bef-103">Se você estiver usando uma classe ou estrutura que define seus próprio operadores, você pode acessar os operadores do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b9bef-103">If you are using a class or structure that defines its own operators, you can access those operators from Visual Basic.</span></span>  
  
 <span data-ttu-id="b9bef-104">Definir um operador em uma classe ou estrutura também é chamado *sobrecarga* o operador.</span><span class="sxs-lookup"><span data-stu-id="b9bef-104">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9bef-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b9bef-105">Example</span></span>  
 <span data-ttu-id="b9bef-106">O exemplo a seguir acessa a estrutura SQL <xref:System.Data.SqlTypes.SqlString>, que define os operadores de conversão ([função CType](../../../../visual-basic/language-reference/functions/ctype-function.md)) em ambas as direções entre uma cadeia de caracteres SQL e uma cadeia de caracteres do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b9bef-106">The following example accesses the SQL structure <xref:System.Data.SqlTypes.SqlString>, which defines the conversion operators ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) in both directions between a SQL string and a Visual Basic string.</span></span> <span data-ttu-id="b9bef-107">Use `CType(` *expressão de cadeia de caracteres SQL*, `String)` para converter uma cadeia de caracteres SQL em uma cadeia de caracteres do Visual Basic, e `CType(` *expressão de cadeia de caracteres do Visual Basic*, <xref:System.Data.SqlTypes.SqlString> `)` converter na outra direção.</span><span class="sxs-lookup"><span data-stu-id="b9bef-107">Use `CType(`*SQL string expression*, `String)` to convert a SQL string to a Visual Basic string, and `CType(`*Visual Basic string expression*, <xref:System.Data.SqlTypes.SqlString>`)` to convert in the other direction.</span></span>  
  
 [!code-vb[VbVbcnProcedures#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#30)]  
  
 [!code-vb[VbVbcnProcedures#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#31)]  
  
 <span data-ttu-id="b9bef-108">O <xref:System.Data.SqlTypes.SqlString> estrutura define um operador de conversão ([função CType](../../../../visual-basic/language-reference/functions/ctype-function.md)) de `String` para <xref:System.Data.SqlTypes.SqlString> e outra de <xref:System.Data.SqlTypes.SqlString> para `String`.</span><span class="sxs-lookup"><span data-stu-id="b9bef-108">The <xref:System.Data.SqlTypes.SqlString> structure defines a conversion operator ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) from `String` to <xref:System.Data.SqlTypes.SqlString> and another from <xref:System.Data.SqlTypes.SqlString> to `String`.</span></span> <span data-ttu-id="b9bef-109">A instrução que atribui `title` à `jobTitle` usa o operador first e o <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> chamada de função usa o segundo.</span><span class="sxs-lookup"><span data-stu-id="b9bef-109">The statement that assigns `title` to `jobTitle` makes use of the first operator, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function call uses the second.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b9bef-110">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="b9bef-110">Compiling the Code</span></span>  
 <span data-ttu-id="b9bef-111">Certifique-se de que a classe ou estrutura que você está usando define o operador que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="b9bef-111">Be sure the class or structure you are using defines the operator you want to use.</span></span> <span data-ttu-id="b9bef-112">Não presuma que a classe ou estrutura definiu todo disponível para a sobrecarga de operador.</span><span class="sxs-lookup"><span data-stu-id="b9bef-112">Do not assume that the class or structure has defined every operator available for overloading.</span></span> <span data-ttu-id="b9bef-113">Para obter uma lista de operadores disponíveis, consulte [instrução Operator](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b9bef-113">For a list of available operators, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
 <span data-ttu-id="b9bef-114">Inclua o `Imports` instrução para a cadeia de caracteres SQL no início do seu arquivo de origem (nesse caso, <xref:System.Data.SqlTypes>).</span><span class="sxs-lookup"><span data-stu-id="b9bef-114">Include the appropriate `Imports` statement for the SQL string at the beginning of your source file (in this case <xref:System.Data.SqlTypes>).</span></span>  
  
 <span data-ttu-id="b9bef-115">Seu projeto deve ter referências a System. Data e System. XML.</span><span class="sxs-lookup"><span data-stu-id="b9bef-115">Your project must have references to System.Data and System.XML.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9bef-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b9bef-116">See also</span></span>
- [<span data-ttu-id="b9bef-117">Procedimentos de Operador</span><span class="sxs-lookup"><span data-stu-id="b9bef-117">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="b9bef-118">Como: Definir um operador</span><span class="sxs-lookup"><span data-stu-id="b9bef-118">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="b9bef-119">Como: Definir um operador de conversão</span><span class="sxs-lookup"><span data-stu-id="b9bef-119">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="b9bef-120">Como: Chamar um procedimento de operador</span><span class="sxs-lookup"><span data-stu-id="b9bef-120">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="b9bef-121">Ampliação</span><span class="sxs-lookup"><span data-stu-id="b9bef-121">Widening</span></span>](../../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="b9bef-122">Narrowing</span><span class="sxs-lookup"><span data-stu-id="b9bef-122">Narrowing</span></span>](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="b9bef-123">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="b9bef-123">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="b9bef-124">Como: declarar uma estrutura</span><span class="sxs-lookup"><span data-stu-id="b9bef-124">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="b9bef-125">Conversões Implícitas e Explícitas</span><span class="sxs-lookup"><span data-stu-id="b9bef-125">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="b9bef-126">Conversões de Widening e Narrowing</span><span class="sxs-lookup"><span data-stu-id="b9bef-126">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
