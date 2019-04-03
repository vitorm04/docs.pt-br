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
ms.openlocfilehash: bd512adf2f06ed0fbd3d36ed3175a0928bf1c57c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58829402"
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a><span data-ttu-id="e52f6-102">Como: Usar uma classe que define operadores (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e52f6-102">How to: Use a Class that Defines Operators (Visual Basic)</span></span>
<span data-ttu-id="e52f6-103">Se você estiver usando uma classe ou estrutura que define seus próprio operadores, você pode acessar os operadores do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e52f6-103">If you are using a class or structure that defines its own operators, you can access those operators from Visual Basic.</span></span>  
  
 <span data-ttu-id="e52f6-104">Definir um operador em uma classe ou estrutura também é chamado *sobrecarga* o operador.</span><span class="sxs-lookup"><span data-stu-id="e52f6-104">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e52f6-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e52f6-105">Example</span></span>  
 <span data-ttu-id="e52f6-106">O exemplo a seguir acessa a estrutura SQL <xref:System.Data.SqlTypes.SqlString>, que define os operadores de conversão ([função CType](../../../../visual-basic/language-reference/functions/ctype-function.md)) em ambas as direções entre uma cadeia de caracteres SQL e uma cadeia de caracteres do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e52f6-106">The following example accesses the SQL structure <xref:System.Data.SqlTypes.SqlString>, which defines the conversion operators ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) in both directions between a SQL string and a Visual Basic string.</span></span> <span data-ttu-id="e52f6-107">Use `CType(` *expressão de cadeia de caracteres SQL*, `String)` para converter uma cadeia de caracteres SQL em uma cadeia de caracteres do Visual Basic, e `CType(` *expressão de cadeia de caracteres do Visual Basic*, <xref:System.Data.SqlTypes.SqlString> `)` converter na outra direção.</span><span class="sxs-lookup"><span data-stu-id="e52f6-107">Use `CType(`*SQL string expression*, `String)` to convert a SQL string to a Visual Basic string, and `CType(`*Visual Basic string expression*, <xref:System.Data.SqlTypes.SqlString>`)` to convert in the other direction.</span></span>  
  
 [!code-vb[VbVbcnProcedures#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#30)]  
  
 [!code-vb[VbVbcnProcedures#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#31)]  
  
 <span data-ttu-id="e52f6-108">O <xref:System.Data.SqlTypes.SqlString> estrutura define um operador de conversão ([função CType](../../../../visual-basic/language-reference/functions/ctype-function.md)) de `String` para <xref:System.Data.SqlTypes.SqlString> e outra de <xref:System.Data.SqlTypes.SqlString> para `String`.</span><span class="sxs-lookup"><span data-stu-id="e52f6-108">The <xref:System.Data.SqlTypes.SqlString> structure defines a conversion operator ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) from `String` to <xref:System.Data.SqlTypes.SqlString> and another from <xref:System.Data.SqlTypes.SqlString> to `String`.</span></span> <span data-ttu-id="e52f6-109">A instrução que atribui `title` à `jobTitle` usa o operador first e o <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> chamada de função usa o segundo.</span><span class="sxs-lookup"><span data-stu-id="e52f6-109">The statement that assigns `title` to `jobTitle` makes use of the first operator, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function call uses the second.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e52f6-110">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="e52f6-110">Compiling the Code</span></span>  
 <span data-ttu-id="e52f6-111">Certifique-se de que a classe ou estrutura que você está usando define o operador que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="e52f6-111">Be sure the class or structure you are using defines the operator you want to use.</span></span> <span data-ttu-id="e52f6-112">Não presuma que a classe ou estrutura definiu todo disponível para a sobrecarga de operador.</span><span class="sxs-lookup"><span data-stu-id="e52f6-112">Do not assume that the class or structure has defined every operator available for overloading.</span></span> <span data-ttu-id="e52f6-113">Para obter uma lista de operadores disponíveis, consulte [instrução Operator](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e52f6-113">For a list of available operators, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
 <span data-ttu-id="e52f6-114">Inclua o `Imports` instrução para a cadeia de caracteres SQL no início do seu arquivo de origem (nesse caso, <xref:System.Data.SqlTypes>).</span><span class="sxs-lookup"><span data-stu-id="e52f6-114">Include the appropriate `Imports` statement for the SQL string at the beginning of your source file (in this case <xref:System.Data.SqlTypes>).</span></span>  
  
 <span data-ttu-id="e52f6-115">Seu projeto deve ter referências a System. Data e System. XML.</span><span class="sxs-lookup"><span data-stu-id="e52f6-115">Your project must have references to System.Data and System.XML.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e52f6-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e52f6-116">See also</span></span>

- [<span data-ttu-id="e52f6-117">Procedimentos de Operador</span><span class="sxs-lookup"><span data-stu-id="e52f6-117">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="e52f6-118">Como: Definir um operador</span><span class="sxs-lookup"><span data-stu-id="e52f6-118">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="e52f6-119">Como: Definir um operador de conversão</span><span class="sxs-lookup"><span data-stu-id="e52f6-119">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="e52f6-120">Como: Chamar um procedimento de operador</span><span class="sxs-lookup"><span data-stu-id="e52f6-120">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="e52f6-121">Ampliação</span><span class="sxs-lookup"><span data-stu-id="e52f6-121">Widening</span></span>](../../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="e52f6-122">Narrowing</span><span class="sxs-lookup"><span data-stu-id="e52f6-122">Narrowing</span></span>](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="e52f6-123">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="e52f6-123">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="e52f6-124">Como: declarar uma estrutura</span><span class="sxs-lookup"><span data-stu-id="e52f6-124">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="e52f6-125">Conversões Implícitas e Explícitas</span><span class="sxs-lookup"><span data-stu-id="e52f6-125">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="e52f6-126">Conversões de Widening e Narrowing</span><span class="sxs-lookup"><span data-stu-id="e52f6-126">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
