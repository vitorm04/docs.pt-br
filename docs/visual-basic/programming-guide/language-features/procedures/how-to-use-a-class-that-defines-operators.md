---
title: Como usar uma classe que define operadores
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
ms.openlocfilehash: fe15e976e6a5469f2a9d1b3521a70a3e1860fdd3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414344"
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a><span data-ttu-id="fd0dd-102">Como usar uma classe que define operadores (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fd0dd-102">How to: Use a Class that Defines Operators (Visual Basic)</span></span>
<span data-ttu-id="fd0dd-103">Se você estiver usando uma classe ou estrutura que define seus próprios operadores, poderá acessar esses operadores de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fd0dd-103">If you are using a class or structure that defines its own operators, you can access those operators from Visual Basic.</span></span>  
  
 <span data-ttu-id="fd0dd-104">A definição de um operador em uma classe ou estrutura também é chamada de *sobrecarga* do operador.</span><span class="sxs-lookup"><span data-stu-id="fd0dd-104">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd0dd-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fd0dd-105">Example</span></span>  
 <span data-ttu-id="fd0dd-106">O exemplo a seguir acessa a estrutura SQL <xref:System.Data.SqlTypes.SqlString> , que define os operadores de conversão ([função CType](../../../language-reference/functions/ctype-function.md)) em ambas as direções entre uma cadeia de caracteres SQL e uma Visual Basic Cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="fd0dd-106">The following example accesses the SQL structure <xref:System.Data.SqlTypes.SqlString>, which defines the conversion operators ([CType Function](../../../language-reference/functions/ctype-function.md)) in both directions between a SQL string and a Visual Basic string.</span></span> <span data-ttu-id="fd0dd-107">Use a `CType(` *expressão de cadeia de caracteres SQL*, `String)` para converter uma cadeia de caracteres SQL em uma Visual Basic Cadeia de caracteres e `CType(` *Visual Basic expressão de cadeia de caracteres*, <xref:System.Data.SqlTypes.SqlString> `)` para converter na outra direção.</span><span class="sxs-lookup"><span data-stu-id="fd0dd-107">Use `CType(`*SQL string expression*, `String)` to convert a SQL string to a Visual Basic string, and `CType(`*Visual Basic string expression*, <xref:System.Data.SqlTypes.SqlString>`)` to convert in the other direction.</span></span>  
  
 [!code-vb[VbVbcnProcedures#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#30)]  
  
 [!code-vb[VbVbcnProcedures#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#31)]  
  
 <span data-ttu-id="fd0dd-108">A <xref:System.Data.SqlTypes.SqlString> estrutura define um operador de conversão ([função CType](../../../language-reference/functions/ctype-function.md)) de `String` para <xref:System.Data.SqlTypes.SqlString> e outra de <xref:System.Data.SqlTypes.SqlString> para `String` .</span><span class="sxs-lookup"><span data-stu-id="fd0dd-108">The <xref:System.Data.SqlTypes.SqlString> structure defines a conversion operator ([CType Function](../../../language-reference/functions/ctype-function.md)) from `String` to <xref:System.Data.SqlTypes.SqlString> and another from <xref:System.Data.SqlTypes.SqlString> to `String`.</span></span> <span data-ttu-id="fd0dd-109">A instrução que o atribui `title` para usa `jobTitle` o primeiro operador e a <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> chamada de função usa a segunda.</span><span class="sxs-lookup"><span data-stu-id="fd0dd-109">The statement that assigns `title` to `jobTitle` makes use of the first operator, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function call uses the second.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="fd0dd-110">Compilar o código</span><span class="sxs-lookup"><span data-stu-id="fd0dd-110">Compile the code</span></span>  
 <span data-ttu-id="fd0dd-111">Certifique-se de que a classe ou estrutura que você está usando define o operador que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="fd0dd-111">Be sure the class or structure you are using defines the operator you want to use.</span></span> <span data-ttu-id="fd0dd-112">Não presuma que a classe ou estrutura tenha definido todos os operadores disponíveis para sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="fd0dd-112">Do not assume that the class or structure has defined every operator available for overloading.</span></span> <span data-ttu-id="fd0dd-113">Para obter uma lista de operadores disponíveis, consulte a [instrução Operator](../../../language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fd0dd-113">For a list of available operators, see [Operator Statement](../../../language-reference/statements/operator-statement.md).</span></span>  
  
 <span data-ttu-id="fd0dd-114">Inclua a `Imports` instrução apropriada para a cadeia de caracteres SQL no início do seu arquivo de origem (nesse caso <xref:System.Data.SqlTypes> ).</span><span class="sxs-lookup"><span data-stu-id="fd0dd-114">Include the appropriate `Imports` statement for the SQL string at the beginning of your source file (in this case <xref:System.Data.SqlTypes>).</span></span>  
  
 <span data-ttu-id="fd0dd-115">Seu projeto deve ter referências a System. Data e System. XML.</span><span class="sxs-lookup"><span data-stu-id="fd0dd-115">Your project must have references to System.Data and System.XML.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd0dd-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="fd0dd-116">See also</span></span>

- [<span data-ttu-id="fd0dd-117">Procedimentos do operador</span><span class="sxs-lookup"><span data-stu-id="fd0dd-117">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="fd0dd-118">Como definir um operador</span><span class="sxs-lookup"><span data-stu-id="fd0dd-118">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="fd0dd-119">Como definir um operador de conversão</span><span class="sxs-lookup"><span data-stu-id="fd0dd-119">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="fd0dd-120">Como chamar um procedimento de operador</span><span class="sxs-lookup"><span data-stu-id="fd0dd-120">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="fd0dd-121">Widening</span><span class="sxs-lookup"><span data-stu-id="fd0dd-121">Widening</span></span>](../../../language-reference/modifiers/widening.md)
- [<span data-ttu-id="fd0dd-122">Narrowing</span><span class="sxs-lookup"><span data-stu-id="fd0dd-122">Narrowing</span></span>](../../../language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="fd0dd-123">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="fd0dd-123">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
- [<span data-ttu-id="fd0dd-124">Como: Declarar uma estrutura</span><span class="sxs-lookup"><span data-stu-id="fd0dd-124">How to: Declare a Structure</span></span>](../data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="fd0dd-125">Conversões implícitas e explícitas</span><span class="sxs-lookup"><span data-stu-id="fd0dd-125">Implicit and Explicit Conversions</span></span>](../data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="fd0dd-126">Conversões de Widening e Narrowing</span><span class="sxs-lookup"><span data-stu-id="fd0dd-126">Widening and Narrowing Conversions</span></span>](../data-types/widening-and-narrowing-conversions.md)
