---
title: Como usar uma classe que define operadores (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7e0bcfaeca638dfabb841a9e935b872f76fdf957
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a><span data-ttu-id="5646e-102">Como usar uma classe que define operadores (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5646e-102">How to: Use a Class that Defines Operators (Visual Basic)</span></span>
<span data-ttu-id="5646e-103">Se você estiver usando uma classe ou estrutura que define suas própria operadores, você pode acessar os operadores do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5646e-103">If you are using a class or structure that defines its own operators, you can access those operators from Visual Basic.</span></span>  
  
 <span data-ttu-id="5646e-104">Definir um operador em uma classe ou estrutura também é chamado *sobrecarga* o operador.</span><span class="sxs-lookup"><span data-stu-id="5646e-104">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5646e-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5646e-105">Example</span></span>  
 <span data-ttu-id="5646e-106">O exemplo a seguir acessa a estrutura SQL <xref:System.Data.SqlTypes.SqlString>, que define os operadores de conversão ([função CType](../../../../visual-basic/language-reference/functions/ctype-function.md)) em ambas as direções entre uma cadeia de caracteres SQL e uma cadeia de caracteres do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5646e-106">The following example accesses the SQL structure <xref:System.Data.SqlTypes.SqlString>, which defines the conversion operators ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) in both directions between a SQL string and a Visual Basic string.</span></span> <span data-ttu-id="5646e-107">Use `CType(` *expressão de cadeia de caracteres SQL*, `String)` para converter uma cadeia de caracteres SQL em uma cadeia de caracteres do Visual Basic e `CType(` *expressão de cadeia de caracteres do Visual Basic*, <xref:System.Data.SqlTypes.SqlString> `)` para converter na outra direção.</span><span class="sxs-lookup"><span data-stu-id="5646e-107">Use `CType(`*SQL string expression*, `String)` to convert a SQL string to a Visual Basic string, and `CType(`*Visual Basic string expression*, <xref:System.Data.SqlTypes.SqlString>`)` to convert in the other direction.</span></span>  
  
 [!code-vb[VbVbcnProcedures#30](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#31](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_2.vb)]  
  
 <span data-ttu-id="5646e-108">O <xref:System.Data.SqlTypes.SqlString> estrutura define um operador de conversão ([função CType](../../../../visual-basic/language-reference/functions/ctype-function.md)) de `String` para <xref:System.Data.SqlTypes.SqlString> e outro de <xref:System.Data.SqlTypes.SqlString> para `String`.</span><span class="sxs-lookup"><span data-stu-id="5646e-108">The <xref:System.Data.SqlTypes.SqlString> structure defines a conversion operator ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) from `String` to <xref:System.Data.SqlTypes.SqlString> and another from <xref:System.Data.SqlTypes.SqlString> to `String`.</span></span> <span data-ttu-id="5646e-109">A instrução que atribui `title` para `jobTitle` faz uso do operador primeiro e o <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> chamada de função usa a segunda.</span><span class="sxs-lookup"><span data-stu-id="5646e-109">The statement that assigns `title` to `jobTitle` makes use of the first operator, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function call uses the second.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5646e-110">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="5646e-110">Compiling the Code</span></span>  
 <span data-ttu-id="5646e-111">Certifique-se de que a classe ou estrutura que você está usando define o operador que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="5646e-111">Be sure the class or structure you are using defines the operator you want to use.</span></span> <span data-ttu-id="5646e-112">Não suponha que a classe ou estrutura tenha definido cada operador disponível para a sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="5646e-112">Do not assume that the class or structure has defined every operator available for overloading.</span></span> <span data-ttu-id="5646e-113">Para obter uma lista de operadores disponíveis, consulte [instrução Operator](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5646e-113">For a list of available operators, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
 <span data-ttu-id="5646e-114">Inclua o `Imports` instrução para a cadeia de caracteres SQL no início do seu arquivo de origem (neste caso <xref:System.Data.SqlTypes>).</span><span class="sxs-lookup"><span data-stu-id="5646e-114">Include the appropriate `Imports` statement for the SQL string at the beginning of your source file (in this case <xref:System.Data.SqlTypes>).</span></span>  
  
 <span data-ttu-id="5646e-115">O projeto deve ter referências a System. Data e System. XML.</span><span class="sxs-lookup"><span data-stu-id="5646e-115">Your project must have references to System.Data and System.XML.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5646e-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5646e-116">See Also</span></span>  
 [<span data-ttu-id="5646e-117">Procedimentos de Operador</span><span class="sxs-lookup"><span data-stu-id="5646e-117">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="5646e-118">Como definir um operador</span><span class="sxs-lookup"><span data-stu-id="5646e-118">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)  
 [<span data-ttu-id="5646e-119">Como definir um operador de conversão</span><span class="sxs-lookup"><span data-stu-id="5646e-119">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="5646e-120">Como chamar um procedimento de operador</span><span class="sxs-lookup"><span data-stu-id="5646e-120">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)  
 [<span data-ttu-id="5646e-121">Ampliação</span><span class="sxs-lookup"><span data-stu-id="5646e-121">Widening</span></span>](../../../../visual-basic/language-reference/modifiers/widening.md)  
 [<span data-ttu-id="5646e-122">Narrowing</span><span class="sxs-lookup"><span data-stu-id="5646e-122">Narrowing</span></span>](../../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [<span data-ttu-id="5646e-123">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="5646e-123">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="5646e-124">Como declarar uma estrutura</span><span class="sxs-lookup"><span data-stu-id="5646e-124">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="5646e-125">Conversões Implícitas e Explícitas</span><span class="sxs-lookup"><span data-stu-id="5646e-125">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="5646e-126">Conversões de Widening e Narrowing</span><span class="sxs-lookup"><span data-stu-id="5646e-126">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
