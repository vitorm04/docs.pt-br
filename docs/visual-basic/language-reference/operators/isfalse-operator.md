---
title: Operador IsFalse
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: bbcdb9bcf645a4e9cb54c657ccd46e04437d207e
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873379"
---
# <a name="isfalse-operator-visual-basic"></a><span data-ttu-id="f544e-102">Operador IsFalse (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f544e-102">IsFalse Operator (Visual Basic)</span></span>

<span data-ttu-id="f544e-103">Determina se uma expressão é `False` .</span><span class="sxs-lookup"><span data-stu-id="f544e-103">Determines whether an expression is `False`.</span></span>  
  
 <span data-ttu-id="f544e-104">Você não pode chamar `IsFalse` explicitamente em seu código, mas o compilador Visual Basic pode usá-lo para gerar código de `AndAlso` cláusulas.</span><span class="sxs-lookup"><span data-stu-id="f544e-104">You cannot call `IsFalse` explicitly in your code, but the Visual Basic compiler can use it to generate code from `AndAlso` clauses.</span></span> <span data-ttu-id="f544e-105">Se você definir uma classe ou estrutura e, em seguida, usar uma variável desse tipo em uma `AndAlso` cláusula, deverá definir `IsFalse` nessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="f544e-105">If you define a class or structure and then use a variable of that type in an `AndAlso` clause, you must define `IsFalse` on that class or structure.</span></span>  
  
 <span data-ttu-id="f544e-106">O compilador considera os `IsFalse` `IsTrue` operadores e como um *par correspondente*.</span><span class="sxs-lookup"><span data-stu-id="f544e-106">The compiler considers the `IsFalse` and `IsTrue` operators as a *matched pair*.</span></span> <span data-ttu-id="f544e-107">Isso significa que, se você definir um deles, também deverá definir o outro.</span><span class="sxs-lookup"><span data-stu-id="f544e-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f544e-108">O `IsFalse` operador pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando seu operando tem o tipo dessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="f544e-108">The `IsFalse` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="f544e-109">Se o seu código usar esse operador em uma classe ou estrutura desse tipo, certifique-se de entender seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="f544e-109">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="f544e-110">Para obter mais informações, consulte [procedimentos de operador](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="f544e-110">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f544e-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f544e-111">Example</span></span>  

 <span data-ttu-id="f544e-112">O exemplo de código a seguir define o contorno de uma estrutura que inclui definições para os `IsFalse` `IsTrue` operadores e.</span><span class="sxs-lookup"><span data-stu-id="f544e-112">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="f544e-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="f544e-113">See also</span></span>

- [<span data-ttu-id="f544e-114">Operador IsTrue</span><span class="sxs-lookup"><span data-stu-id="f544e-114">IsTrue Operator</span></span>](istrue-operator.md)
- [<span data-ttu-id="f544e-115">Como definir um operador</span><span class="sxs-lookup"><span data-stu-id="f544e-115">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="f544e-116">Operador AndAlso</span><span class="sxs-lookup"><span data-stu-id="f544e-116">AndAlso Operator</span></span>](andalso-operator.md)
