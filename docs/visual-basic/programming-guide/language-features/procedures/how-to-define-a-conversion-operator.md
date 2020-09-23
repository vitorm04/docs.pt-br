---
title: Como definir um operador de conversão
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
ms.openlocfilehash: 2fabcf6c6ceb38fe77d4eed4f02dcb5a5e447bf1
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085666"
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a><span data-ttu-id="14e4d-102">Como definir um operador de conversão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="14e4d-102">How to: Define a Conversion Operator (Visual Basic)</span></span>

<span data-ttu-id="14e4d-103">Se você tiver definido uma classe ou estrutura, poderá definir um operador de conversão de tipo entre o tipo de sua classe ou estrutura e outro tipo de dados (como `Integer` , `Double` ou `String` ).</span><span class="sxs-lookup"><span data-stu-id="14e4d-103">If you have defined a class or structure, you can define a type conversion operator between the type of your class or structure and another data type (such as `Integer`, `Double`, or `String`).</span></span>  
  
 <span data-ttu-id="14e4d-104">Defina a conversão de tipo como um procedimento de [função CType](../../../language-reference/functions/ctype-function.md) dentro da classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="14e4d-104">Define the type conversion as a [CType Function](../../../language-reference/functions/ctype-function.md) procedure within the class or structure.</span></span> <span data-ttu-id="14e4d-105">Todos os procedimentos de conversão devem ser `Public Shared` , e cada um deve especificar o [alargamento](../../../language-reference/modifiers/widening.md) ou [restringir](../../../language-reference/modifiers/narrowing.md).</span><span class="sxs-lookup"><span data-stu-id="14e4d-105">All conversion procedures must be `Public Shared`, and each one must specify either [Widening](../../../language-reference/modifiers/widening.md) or [Narrowing](../../../language-reference/modifiers/narrowing.md).</span></span>  
  
 <span data-ttu-id="14e4d-106">A definição de um operador em uma classe ou estrutura também é chamada de *sobrecarga* do operador.</span><span class="sxs-lookup"><span data-stu-id="14e4d-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14e4d-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="14e4d-107">Example</span></span>  

 <span data-ttu-id="14e4d-108">O exemplo a seguir define os operadores de conversão entre uma estrutura chamada `digit` e um `Byte` .</span><span class="sxs-lookup"><span data-stu-id="14e4d-108">The following example defines conversion operators between a structure called `digit` and a `Byte`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#27)]  
  
 <span data-ttu-id="14e4d-109">Você pode testar a estrutura `digit` com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="14e4d-109">You can test the structure `digit` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="14e4d-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="14e4d-110">See also</span></span>

- [<span data-ttu-id="14e4d-111">Procedimentos do operador</span><span class="sxs-lookup"><span data-stu-id="14e4d-111">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="14e4d-112">Como definir um operador</span><span class="sxs-lookup"><span data-stu-id="14e4d-112">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="14e4d-113">Como chamar um procedimento de operador</span><span class="sxs-lookup"><span data-stu-id="14e4d-113">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="14e4d-114">Como usar uma classe que define operadores</span><span class="sxs-lookup"><span data-stu-id="14e4d-114">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
- [<span data-ttu-id="14e4d-115">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="14e4d-115">Operator Statement</span></span>](../../../language-reference/statements/operator-statement.md)
- [<span data-ttu-id="14e4d-116">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="14e4d-116">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
- [<span data-ttu-id="14e4d-117">Como: Declarar uma estrutura</span><span class="sxs-lookup"><span data-stu-id="14e4d-117">How to: Declare a Structure</span></span>](../data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="14e4d-118">Conversões implícitas e explícitas</span><span class="sxs-lookup"><span data-stu-id="14e4d-118">Implicit and Explicit Conversions</span></span>](../data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="14e4d-119">Conversões de Widening e Narrowing</span><span class="sxs-lookup"><span data-stu-id="14e4d-119">Widening and Narrowing Conversions</span></span>](../data-types/widening-and-narrowing-conversions.md)
