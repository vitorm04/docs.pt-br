---
title: Como definir um operador (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 51921ee38204fd528ed19436806fc9433abbdc5e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-an-operator-visual-basic"></a><span data-ttu-id="99a7c-102">Como definir um operador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99a7c-102">How to: Define an Operator (Visual Basic)</span></span>
<span data-ttu-id="99a7c-103">Se você tiver definido uma classe ou estrutura, você pode definir o comportamento de um operador padrão (como `*`, `<>`, ou `And`) quando um ou ambos os operandos é do tipo de sua classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="99a7c-103">If you have defined a class or structure, you can define the behavior of a standard operator (such as `*`, `<>`, or `And`) when one or both of the operands is of the type of your class or structure.</span></span>  
  
 <span data-ttu-id="99a7c-104">Defina o operador padrão como um procedimento de operador dentro da classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="99a7c-104">Define the standard operator as an operator procedure within the class or structure.</span></span> <span data-ttu-id="99a7c-105">Todos os procedimentos de operador devem ser `Public` `Shared`.</span><span class="sxs-lookup"><span data-stu-id="99a7c-105">All operator procedures must be `Public` `Shared`.</span></span>  
  
 <span data-ttu-id="99a7c-106">Definir um operador em uma classe ou estrutura também é chamado *sobrecarga* o operador.</span><span class="sxs-lookup"><span data-stu-id="99a7c-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99a7c-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="99a7c-107">Example</span></span>  
 <span data-ttu-id="99a7c-108">O exemplo a seguir define o `+` chamado de operador para uma estrutura `height`.</span><span class="sxs-lookup"><span data-stu-id="99a7c-108">The following example defines the `+` operator for a structure called `height`.</span></span> <span data-ttu-id="99a7c-109">A estrutura usa alturas medidas em pés e polegadas.</span><span class="sxs-lookup"><span data-stu-id="99a7c-109">The structure uses heights measured in feet and inches.</span></span> <span data-ttu-id="99a7c-110">Um *polegadas* é 2,54 centímetros e *pés* 12 polegadas.</span><span class="sxs-lookup"><span data-stu-id="99a7c-110">One *inch* is 2.54 centimeters, and one *foot* is 12 inches.</span></span> <span data-ttu-id="99a7c-111">Verifique os valores normalizados (polegadas < 12.0), o construtor executa *módulo* 12 aritmética.</span><span class="sxs-lookup"><span data-stu-id="99a7c-111">To ensure normalized values (inches < 12.0), the constructor performs *modulo* 12 arithmetic.</span></span> <span data-ttu-id="99a7c-112">O `+` operador usa o construtor para gerar valores normalizados.</span><span class="sxs-lookup"><span data-stu-id="99a7c-112">The `+` operator uses the constructor to generate normalized values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#25](./codesnippet/VisualBasic/how-to-define-an-operator_1.vb)]  
  
 <span data-ttu-id="99a7c-113">Você pode testar a estrutura `height` com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="99a7c-113">You can test the structure `height` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#26](./codesnippet/VisualBasic/how-to-define-an-operator_2.vb)]  
  
 <span data-ttu-id="99a7c-114">Para obter mais informações e exemplos, consulte [Sobrecarga de operador no Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703).</span><span class="sxs-lookup"><span data-stu-id="99a7c-114">For more information and examples, see [Operator Overloading in Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99a7c-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="99a7c-115">See Also</span></span>  
 [<span data-ttu-id="99a7c-116">Procedimentos de Operador</span><span class="sxs-lookup"><span data-stu-id="99a7c-116">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="99a7c-117">Como definir um operador de conversão</span><span class="sxs-lookup"><span data-stu-id="99a7c-117">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="99a7c-118">Como chamar um procedimento de operador</span><span class="sxs-lookup"><span data-stu-id="99a7c-118">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)  
 [<span data-ttu-id="99a7c-119">Como usar uma classe que define operadores</span><span class="sxs-lookup"><span data-stu-id="99a7c-119">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)  
 [<span data-ttu-id="99a7c-120">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="99a7c-120">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="99a7c-121">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="99a7c-121">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="99a7c-122">Como declarar uma estrutura</span><span class="sxs-lookup"><span data-stu-id="99a7c-122">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="99a7c-123">Operador Mod</span><span class="sxs-lookup"><span data-stu-id="99a7c-123">Mod Operator</span></span>](../../../../visual-basic/language-reference/operators/mod-operator.md)
