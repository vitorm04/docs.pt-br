---
title: Como definir um operador de conversão (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
ms.openlocfilehash: 24bbe41af67f757cae661a78d482a423ff0ffd85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648467"
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a><span data-ttu-id="50648-102">Como definir um operador de conversão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="50648-102">How to: Define a Conversion Operator (Visual Basic)</span></span>
<span data-ttu-id="50648-103">Se você tiver definido uma classe ou estrutura, você pode definir um operador de conversão de tipo entre o tipo de sua classe ou estrutura e outro tipo de dados (como `Integer`, `Double`, ou `String`).</span><span class="sxs-lookup"><span data-stu-id="50648-103">If you have defined a class or structure, you can define a type conversion operator between the type of your class or structure and another data type (such as `Integer`, `Double`, or `String`).</span></span>  
  
 <span data-ttu-id="50648-104">Defina a conversão de tipo como um [função CType](../../../../visual-basic/language-reference/functions/ctype-function.md) procedimento dentro da classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="50648-104">Define the type conversion as a [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) procedure within the class or structure.</span></span> <span data-ttu-id="50648-105">Todos os procedimentos de conversão devem ser `Public Shared`, e cada um deles deve especificar ou [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) ou [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md).</span><span class="sxs-lookup"><span data-stu-id="50648-105">All conversion procedures must be `Public Shared`, and each one must specify either [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) or [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md).</span></span>  
  
 <span data-ttu-id="50648-106">Definir um operador em uma classe ou estrutura também é chamado *sobrecarga* o operador.</span><span class="sxs-lookup"><span data-stu-id="50648-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50648-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="50648-107">Example</span></span>  
 <span data-ttu-id="50648-108">O exemplo a seguir define os operadores de conversão entre uma estrutura chamada `digit` e um `Byte`.</span><span class="sxs-lookup"><span data-stu-id="50648-108">The following example defines conversion operators between a structure called `digit` and a `Byte`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#27](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_1.vb)]  
  
 <span data-ttu-id="50648-109">Você pode testar a estrutura `digit` com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="50648-109">You can test the structure `digit` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#28](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="50648-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="50648-110">See Also</span></span>  
 [<span data-ttu-id="50648-111">Procedimentos de Operador</span><span class="sxs-lookup"><span data-stu-id="50648-111">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="50648-112">Como definir um operador</span><span class="sxs-lookup"><span data-stu-id="50648-112">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)  
 [<span data-ttu-id="50648-113">Como chamar um procedimento de operador</span><span class="sxs-lookup"><span data-stu-id="50648-113">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)  
 [<span data-ttu-id="50648-114">Como usar uma classe que define operadores</span><span class="sxs-lookup"><span data-stu-id="50648-114">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)  
 [<span data-ttu-id="50648-115">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="50648-115">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="50648-116">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="50648-116">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="50648-117">Como declarar uma estrutura</span><span class="sxs-lookup"><span data-stu-id="50648-117">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="50648-118">Conversões Implícitas e Explícitas</span><span class="sxs-lookup"><span data-stu-id="50648-118">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="50648-119">Conversões de Widening e Narrowing</span><span class="sxs-lookup"><span data-stu-id="50648-119">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
