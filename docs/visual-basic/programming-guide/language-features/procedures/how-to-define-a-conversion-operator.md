---
title: "Como: definir um operador de conversão (Visual Basic) | Documentos do Microsoft"
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
- procedures, defining
- operators [Visual Basic], defining
- procedures, operator
- operators [Visual Basic], overloading
- return values, Operator procedures
- operator overloading
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
caps.latest.revision: 14
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
ms.openlocfilehash: f65be6c283d33cac7699665e120a61474538b952
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a><span data-ttu-id="ef1b1-102">Como definir um operador de conversão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ef1b1-102">How to: Define a Conversion Operator (Visual Basic)</span></span>
<span data-ttu-id="ef1b1-103">Se você tiver definido uma classe ou estrutura, você pode definir um operador de conversão de tipos entre o tipo de sua classe ou estrutura e outro tipo de dados (como `Integer`, `Double`, ou `String`).</span><span class="sxs-lookup"><span data-stu-id="ef1b1-103">If you have defined a class or structure, you can define a type conversion operator between the type of your class or structure and another data type (such as `Integer`, `Double`, or `String`).</span></span>  
  
 <span data-ttu-id="ef1b1-104">Defina a conversão de tipo como um [função CType](../../../../visual-basic/language-reference/functions/ctype-function.md) procedimento dentro da classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="ef1b1-104">Define the type conversion as a [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) procedure within the class or structure.</span></span> <span data-ttu-id="ef1b1-105">Todos os procedimentos de conversão devem ser `Public Shared`, e cada um deles deve especificar ou [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) ou [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md).</span><span class="sxs-lookup"><span data-stu-id="ef1b1-105">All conversion procedures must be `Public Shared`, and each one must specify either [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) or [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md).</span></span>  
  
 <span data-ttu-id="ef1b1-106">Definir um operador em uma classe ou estrutura também é chamado *sobrecarga* o operador.</span><span class="sxs-lookup"><span data-stu-id="ef1b1-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef1b1-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ef1b1-107">Example</span></span>  
 <span data-ttu-id="ef1b1-108">O exemplo a seguir define os operadores de conversão entre uma estrutura chamada `digit` e um `Byte`.</span><span class="sxs-lookup"><span data-stu-id="ef1b1-108">The following example defines conversion operators between a structure called `digit` and a `Byte`.</span></span>  
  
 <span data-ttu-id="ef1b1-109">[!code-vb[VbVbcnProcedures&#27;](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="ef1b1-109">[!code-vb[VbVbcnProcedures#27](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_1.vb)]</span></span>  
  
 <span data-ttu-id="ef1b1-110">Você pode testar a estrutura `digit` com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="ef1b1-110">You can test the structure `digit` with the following code.</span></span>  
  
 <span data-ttu-id="ef1b1-111">[!code-vb[VbVbcnProcedures&#28;](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="ef1b1-111">[!code-vb[VbVbcnProcedures#28](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef1b1-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ef1b1-112">See Also</span></span>  
 <span data-ttu-id="ef1b1-113">[Procedimentos de operador](./operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="ef1b1-113">[Operator Procedures](./operator-procedures.md) </span></span>  
<span data-ttu-id="ef1b1-114"> [Como: definir um operador](./how-to-define-an-operator.md) </span><span class="sxs-lookup"><span data-stu-id="ef1b1-114"> [How to: Define an Operator](./how-to-define-an-operator.md) </span></span>  
<span data-ttu-id="ef1b1-115"> [Como: chamar um procedimento de operador](./how-to-call-an-operator-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="ef1b1-115"> [How to: Call an Operator Procedure](./how-to-call-an-operator-procedure.md) </span></span>  
<span data-ttu-id="ef1b1-116"> [Como: usar uma classe que define operadores](./how-to-use-a-class-that-defines-operators.md) </span><span class="sxs-lookup"><span data-stu-id="ef1b1-116"> [How to: Use a Class that Defines Operators](./how-to-use-a-class-that-defines-operators.md) </span></span>  
<span data-ttu-id="ef1b1-117"> [Instrução Operator](../../../../visual-basic/language-reference/statements/operator-statement.md) </span><span class="sxs-lookup"><span data-stu-id="ef1b1-117"> [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md) </span></span>  
<span data-ttu-id="ef1b1-118"> [Instrução Structure](../../../../visual-basic/language-reference/statements/structure-statement.md) </span><span class="sxs-lookup"><span data-stu-id="ef1b1-118"> [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md) </span></span>  
<span data-ttu-id="ef1b1-119"> [Como: declarar uma estrutura](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md) </span><span class="sxs-lookup"><span data-stu-id="ef1b1-119"> [How to: Declare a Structure](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md) </span></span>  
<span data-ttu-id="ef1b1-120"> [Conversões implícitas e explícitas](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="ef1b1-120"> [Implicit and Explicit Conversions](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) </span></span>  
<span data-ttu-id="ef1b1-121"> [Conversões de Widening e Narrowing](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)</span><span class="sxs-lookup"><span data-stu-id="ef1b1-121"> [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)</span></span>
