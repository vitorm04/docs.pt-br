---
title: 'Como: Definir um operador (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- operator procedures [Visual Basic], about operator procedures
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: d4b0e253-092a-4e6e-9fe2-01f562140a29
ms.openlocfilehash: fb150298562c1ec91f73f3c8075f4f8a4fc20b27
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54679520"
---
# <a name="how-to-define-an-operator-visual-basic"></a><span data-ttu-id="339df-102">Como: Definir um operador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="339df-102">How to: Define an Operator (Visual Basic)</span></span>
<span data-ttu-id="339df-103">Se você tiver definido uma classe ou estrutura, você pode definir o comportamento de um operador padrão (como `*`, `<>`, ou `And`) quando um ou ambos os operandos é do tipo de sua classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="339df-103">If you have defined a class or structure, you can define the behavior of a standard operator (such as `*`, `<>`, or `And`) when one or both of the operands is of the type of your class or structure.</span></span>  
  
 <span data-ttu-id="339df-104">Defina o operador padrão como um procedimento de operador dentro da classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="339df-104">Define the standard operator as an operator procedure within the class or structure.</span></span> <span data-ttu-id="339df-105">Todos os procedimentos de operador devem ser `Public` `Shared`.</span><span class="sxs-lookup"><span data-stu-id="339df-105">All operator procedures must be `Public` `Shared`.</span></span>  
  
 <span data-ttu-id="339df-106">Definir um operador em uma classe ou estrutura também é chamado *sobrecarga* o operador.</span><span class="sxs-lookup"><span data-stu-id="339df-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="339df-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="339df-107">Example</span></span>  
 <span data-ttu-id="339df-108">O exemplo a seguir define o `+` chamado de operador para uma estrutura `height`.</span><span class="sxs-lookup"><span data-stu-id="339df-108">The following example defines the `+` operator for a structure called `height`.</span></span> <span data-ttu-id="339df-109">A estrutura usa a altura é medida em pés e polegadas.</span><span class="sxs-lookup"><span data-stu-id="339df-109">The structure uses heights measured in feet and inches.</span></span> <span data-ttu-id="339df-110">Uma *polegada* é 2,54 centímetros e uma *pés* é 12 polegadas.</span><span class="sxs-lookup"><span data-stu-id="339df-110">One *inch* is 2.54 centimeters, and one *foot* is 12 inches.</span></span> <span data-ttu-id="339df-111">Para garantir que os valores normalizados (polegadas < 12.0), o construtor executa *módulo* 12 aritmético.</span><span class="sxs-lookup"><span data-stu-id="339df-111">To ensure normalized values (inches < 12.0), the constructor performs *modulo* 12 arithmetic.</span></span> <span data-ttu-id="339df-112">O `+` operador usa o construtor para gerar valores normalizados.</span><span class="sxs-lookup"><span data-stu-id="339df-112">The `+` operator uses the constructor to generate normalized values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#25](./codesnippet/VisualBasic/how-to-define-an-operator_1.vb)]  
  
 <span data-ttu-id="339df-113">Você pode testar a estrutura `height` com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="339df-113">You can test the structure `height` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#26](./codesnippet/VisualBasic/how-to-define-an-operator_2.vb)]  
  
 <span data-ttu-id="339df-114">Para obter mais informações e exemplos, consulte [Sobrecarga de operador no Visual Basic 2005](https://msdn.microsoft.com/library/ms379613(v=vs.80).aspx).</span><span class="sxs-lookup"><span data-stu-id="339df-114">For more information and examples, see [Operator Overloading in Visual Basic 2005](https://msdn.microsoft.com/library/ms379613(v=vs.80).aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="339df-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="339df-115">See also</span></span>
- [<span data-ttu-id="339df-116">Procedimentos de Operador</span><span class="sxs-lookup"><span data-stu-id="339df-116">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="339df-117">Como: Definir um operador de conversão</span><span class="sxs-lookup"><span data-stu-id="339df-117">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="339df-118">Como: Chamar um procedimento de operador</span><span class="sxs-lookup"><span data-stu-id="339df-118">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="339df-119">Como: Usar uma classe que define operadores</span><span class="sxs-lookup"><span data-stu-id="339df-119">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
- [<span data-ttu-id="339df-120">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="339df-120">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="339df-121">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="339df-121">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="339df-122">Como: declarar uma estrutura</span><span class="sxs-lookup"><span data-stu-id="339df-122">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="339df-123">Operador Mod</span><span class="sxs-lookup"><span data-stu-id="339df-123">Mod Operator</span></span>](../../../../visual-basic/language-reference/operators/mod-operator.md)
