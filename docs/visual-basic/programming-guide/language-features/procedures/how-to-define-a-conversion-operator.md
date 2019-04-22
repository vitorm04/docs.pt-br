---
title: 'Como: Definir um operador de conversão (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
ms.openlocfilehash: cf7bfdd09c7f3429f9c730a7aec34b24af3f2e9f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58829220"
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a><span data-ttu-id="99ee5-102">Como: Definir um operador de conversão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99ee5-102">How to: Define a Conversion Operator (Visual Basic)</span></span>
<span data-ttu-id="99ee5-103">Se você tiver definido uma classe ou estrutura, você pode definir um operador de conversão de tipo entre o tipo de sua classe ou estrutura e outro tipo de dados (como `Integer`, `Double`, ou `String`).</span><span class="sxs-lookup"><span data-stu-id="99ee5-103">If you have defined a class or structure, you can define a type conversion operator between the type of your class or structure and another data type (such as `Integer`, `Double`, or `String`).</span></span>  
  
 <span data-ttu-id="99ee5-104">Defina a conversão de tipo como uma [função CType](../../../../visual-basic/language-reference/functions/ctype-function.md) procedimento dentro da classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="99ee5-104">Define the type conversion as a [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) procedure within the class or structure.</span></span> <span data-ttu-id="99ee5-105">Todos os procedimentos de conversão devem ser `Public Shared`, e cada um deles deve especificar [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) ou [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md).</span><span class="sxs-lookup"><span data-stu-id="99ee5-105">All conversion procedures must be `Public Shared`, and each one must specify either [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) or [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md).</span></span>  
  
 <span data-ttu-id="99ee5-106">Definir um operador em uma classe ou estrutura também é chamado *sobrecarga* o operador.</span><span class="sxs-lookup"><span data-stu-id="99ee5-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99ee5-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="99ee5-107">Example</span></span>  
 <span data-ttu-id="99ee5-108">O exemplo a seguir define os operadores de conversão entre uma estrutura chamada `digit` e um `Byte`.</span><span class="sxs-lookup"><span data-stu-id="99ee5-108">The following example defines conversion operators between a structure called `digit` and a `Byte`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#27)]  
  
 <span data-ttu-id="99ee5-109">Você pode testar a estrutura `digit` com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="99ee5-109">You can test the structure `digit` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="99ee5-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="99ee5-110">See also</span></span>

- [<span data-ttu-id="99ee5-111">Procedimentos de Operador</span><span class="sxs-lookup"><span data-stu-id="99ee5-111">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="99ee5-112">Como: Definir um operador</span><span class="sxs-lookup"><span data-stu-id="99ee5-112">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="99ee5-113">Como: Chamar um procedimento de operador</span><span class="sxs-lookup"><span data-stu-id="99ee5-113">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="99ee5-114">Como: Usar uma classe que define operadores</span><span class="sxs-lookup"><span data-stu-id="99ee5-114">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
- [<span data-ttu-id="99ee5-115">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="99ee5-115">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="99ee5-116">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="99ee5-116">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="99ee5-117">Como: declarar uma estrutura</span><span class="sxs-lookup"><span data-stu-id="99ee5-117">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="99ee5-118">Conversões Implícitas e Explícitas</span><span class="sxs-lookup"><span data-stu-id="99ee5-118">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="99ee5-119">Conversões de Widening e Narrowing</span><span class="sxs-lookup"><span data-stu-id="99ee5-119">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
