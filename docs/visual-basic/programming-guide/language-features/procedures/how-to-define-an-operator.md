---
title: 'Como: definir um operador (Visual Basic) | Documentos do Microsoft'
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
- Visual Basic code, procedures
- operators [Visual Basic], defining
- procedures, operator
- Visual Basic code, operators
- syntax, Operator procedures
- operators [Visual Basic], overloading
- operator procedures, about operator procedures
- return values, Operator procedures
- operator overloading
ms.assetid: d4b0e253-092a-4e6e-9fe2-01f562140a29
caps.latest.revision: 15
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
ms.openlocfilehash: ef9c2cdb0c42bd6457f6f119326d689b4df5daf0
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-define-an-operator-visual-basic"></a><span data-ttu-id="fea31-102">Como definir um operador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fea31-102">How to: Define an Operator (Visual Basic)</span></span>
<span data-ttu-id="fea31-103">Se você tiver definido uma classe ou estrutura, você pode definir o comportamento de um operador padrão (como `*`, `<>`, ou `And`) quando um ou ambos os operandos é do tipo de sua classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="fea31-103">If you have defined a class or structure, you can define the behavior of a standard operator (such as `*`, `<>`, or `And`) when one or both of the operands is of the type of your class or structure.</span></span>  
  
 <span data-ttu-id="fea31-104">Defina o operador padrão como um procedimento de operador dentro da classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="fea31-104">Define the standard operator as an operator procedure within the class or structure.</span></span> <span data-ttu-id="fea31-105">Todos os procedimentos de operador devem ser `Public` `Shared`.</span><span class="sxs-lookup"><span data-stu-id="fea31-105">All operator procedures must be `Public` `Shared`.</span></span>  
  
 <span data-ttu-id="fea31-106">Definir um operador em uma classe ou estrutura também é chamado *sobrecarga* o operador.</span><span class="sxs-lookup"><span data-stu-id="fea31-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fea31-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fea31-107">Example</span></span>  
 <span data-ttu-id="fea31-108">O exemplo a seguir define o `+` chamado de operador para uma estrutura `height`.</span><span class="sxs-lookup"><span data-stu-id="fea31-108">The following example defines the `+` operator for a structure called `height`.</span></span> <span data-ttu-id="fea31-109">A estrutura usa alturas medidas em pés e polegadas.</span><span class="sxs-lookup"><span data-stu-id="fea31-109">The structure uses heights measured in feet and inches.</span></span> <span data-ttu-id="fea31-110">Um *polegadas* é 2,54 centímetros e *pés* é 12 polegadas.</span><span class="sxs-lookup"><span data-stu-id="fea31-110">One *inch* is 2.54 centimeters, and one *foot* is 12 inches.</span></span> <span data-ttu-id="fea31-111">Para garantir que os valores normalizados (polegadas < 12.0),="" the="" constructor="" performs=""> </> *módulo* 12 aritmética.</span><span class="sxs-lookup"><span data-stu-id="fea31-111">To ensure normalized values (inches < 12.0), the constructor performs *modulo* 12 arithmetic.</span></span> <span data-ttu-id="fea31-112">O `+` operador usa o construtor para gerar valores normalizados.</span><span class="sxs-lookup"><span data-stu-id="fea31-112">The `+` operator uses the constructor to generate normalized values.</span></span>  
  
 <span data-ttu-id="fea31-113">[!code-vb[25 VbVbcnProcedures](./codesnippet/VisualBasic/how-to-define-an-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="fea31-113">[!code-vb[VbVbcnProcedures#25](./codesnippet/VisualBasic/how-to-define-an-operator_1.vb)]</span></span>  
  
 <span data-ttu-id="fea31-114">Você pode testar a estrutura `height` com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="fea31-114">You can test the structure `height` with the following code.</span></span>  
  
 <span data-ttu-id="fea31-115">[!code-vb[VbVbcnProcedures&#26;](./codesnippet/VisualBasic/how-to-define-an-operator_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="fea31-115">[!code-vb[VbVbcnProcedures#26](./codesnippet/VisualBasic/how-to-define-an-operator_2.vb)]</span></span>  
  
 <span data-ttu-id="fea31-116">Para obter mais informações e exemplos, consulte [sobrecarga de operador no Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703).</span><span class="sxs-lookup"><span data-stu-id="fea31-116">For more information and examples, see [Operator Overloading in Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fea31-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fea31-117">See Also</span></span>  
 <span data-ttu-id="fea31-118">[Procedimentos de operador](./operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="fea31-118">[Operator Procedures](./operator-procedures.md) </span></span>  
<span data-ttu-id="fea31-119"> [Como: definir um operador de conversão](./how-to-define-a-conversion-operator.md) </span><span class="sxs-lookup"><span data-stu-id="fea31-119"> [How to: Define a Conversion Operator](./how-to-define-a-conversion-operator.md) </span></span>  
<span data-ttu-id="fea31-120"> [Como: chamar um procedimento de operador](./how-to-call-an-operator-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="fea31-120"> [How to: Call an Operator Procedure](./how-to-call-an-operator-procedure.md) </span></span>  
<span data-ttu-id="fea31-121"> [Como: usar uma classe que define operadores](./how-to-use-a-class-that-defines-operators.md) </span><span class="sxs-lookup"><span data-stu-id="fea31-121"> [How to: Use a Class that Defines Operators](./how-to-use-a-class-that-defines-operators.md) </span></span>  
<span data-ttu-id="fea31-122"> [Instrução Operator](../../../../visual-basic/language-reference/statements/operator-statement.md) </span><span class="sxs-lookup"><span data-stu-id="fea31-122"> [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md) </span></span>  
<span data-ttu-id="fea31-123"> [Instrução Structure](../../../../visual-basic/language-reference/statements/structure-statement.md) </span><span class="sxs-lookup"><span data-stu-id="fea31-123"> [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md) </span></span>  
<span data-ttu-id="fea31-124"> [Como: declarar uma estrutura](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md) </span><span class="sxs-lookup"><span data-stu-id="fea31-124"> [How to: Declare a Structure](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md) </span></span>  
<span data-ttu-id="fea31-125"> [Operador Mod](../../../../visual-basic/language-reference/operators/mod-operator.md)</span><span class="sxs-lookup"><span data-stu-id="fea31-125"> [Mod Operator](../../../../visual-basic/language-reference/operators/mod-operator.md)</span></span>
