---
title: Operador IsTrue (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: 1152f4b512a85ae183f8fc8d476b69685e2926ef
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966912"
---
# <a name="istrue-operator-visual-basic"></a><span data-ttu-id="1bcf4-102">Operador IsTrue (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1bcf4-102">IsTrue Operator (Visual Basic)</span></span>
<span data-ttu-id="1bcf4-103">Determina se uma expressão é `True`.</span><span class="sxs-lookup"><span data-stu-id="1bcf4-103">Determines whether an expression is `True`.</span></span>  
  
 <span data-ttu-id="1bcf4-104">Você não pode `IsTrue` chamar explicitamente em seu código, mas o compilador Visual Basic pode usá-lo para gerar `OrElse` código de cláusulas.</span><span class="sxs-lookup"><span data-stu-id="1bcf4-104">You cannot call `IsTrue` explicitly in your code, but the Visual Basic compiler can use it to generate code from `OrElse` clauses.</span></span> <span data-ttu-id="1bcf4-105">Se você definir uma classe ou estrutura e, em seguida, usar uma variável desse tipo `OrElse` em uma cláusula, deverá `IsTrue` definir nessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="1bcf4-105">If you define a class or structure and then use a variable of that type in an `OrElse` clause, you must define `IsTrue` on that class or structure.</span></span>  
  
 <span data-ttu-id="1bcf4-106">O compilador considera os `IsTrue` operadores `IsFalse` e como um *par correspondente*.</span><span class="sxs-lookup"><span data-stu-id="1bcf4-106">The compiler considers the `IsTrue` and `IsFalse` operators as a *matched pair*.</span></span> <span data-ttu-id="1bcf4-107">Isso significa que, se você definir um deles, também deverá definir o outro.</span><span class="sxs-lookup"><span data-stu-id="1bcf4-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
## <a name="compiler-use-of-istrue"></a><span data-ttu-id="1bcf4-108">Uso do compilador de IsTrue</span><span class="sxs-lookup"><span data-stu-id="1bcf4-108">Compiler Use of IsTrue</span></span>  
 <span data-ttu-id="1bcf4-109">Quando você tiver definido uma classe ou estrutura, poderá usar uma variável `For`desse tipo em uma instrução `Else If`, `If`, ou `While` , ou em uma `When` cláusula.</span><span class="sxs-lookup"><span data-stu-id="1bcf4-109">When you have defined a class or structure, you can use a variable of that type in a `For`, `If`, `Else If`, or `While` statement, or in a `When` clause.</span></span> <span data-ttu-id="1bcf4-110">Se você fizer isso, o compilador exigirá um operador que converte o tipo em `Boolean` um valor para que ele possa testar uma condição.</span><span class="sxs-lookup"><span data-stu-id="1bcf4-110">If you do this, the compiler requires an operator that converts your type into a `Boolean` value so it can test a condition.</span></span> <span data-ttu-id="1bcf4-111">Ele procura um operador adequado na seguinte ordem:</span><span class="sxs-lookup"><span data-stu-id="1bcf4-111">It searches for a suitable operator in the following order:</span></span>  
  
1. <span data-ttu-id="1bcf4-112">Um operador de conversão de ampliação de sua classe ou `Boolean`estrutura para.</span><span class="sxs-lookup"><span data-stu-id="1bcf4-112">A widening conversion operator from your class or structure to `Boolean`.</span></span>  
  
2. <span data-ttu-id="1bcf4-113">Um operador de conversão de ampliação de sua classe ou `Boolean?`estrutura para.</span><span class="sxs-lookup"><span data-stu-id="1bcf4-113">A widening conversion operator from your class or structure to `Boolean?`.</span></span>  
  
3. <span data-ttu-id="1bcf4-114">O `IsTrue` operador em sua classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="1bcf4-114">The `IsTrue` operator on your class or structure.</span></span>  
  
4. <span data-ttu-id="1bcf4-115">Uma conversão de restrição para `Boolean?` que não envolve uma conversão de `Boolean` para `Boolean?`.</span><span class="sxs-lookup"><span data-stu-id="1bcf4-115">A narrowing conversion to `Boolean?` that does not involve a conversion from `Boolean` to `Boolean?`.</span></span>  
  
5. <span data-ttu-id="1bcf4-116">Um operador de conversão de restrição de sua classe ou estrutura `Boolean`para.</span><span class="sxs-lookup"><span data-stu-id="1bcf4-116">A narrowing conversion operator from your class or structure to `Boolean`.</span></span>  
  
 <span data-ttu-id="1bcf4-117">Se você não tiver definido nenhuma conversão para `Boolean` ou um `IsTrue` operador, o compilador sinalizará um erro.</span><span class="sxs-lookup"><span data-stu-id="1bcf4-117">If you have not defined any conversion to `Boolean` or an `IsTrue` operator, the compiler signals an error.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1bcf4-118">O `IsTrue` operador pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando seu operando tem o tipo dessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="1bcf4-118">The `IsTrue` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="1bcf4-119">Se o seu código usar esse operador em uma classe ou estrutura desse tipo, certifique-se de entender seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="1bcf4-119">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="1bcf4-120">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="1bcf4-120">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bcf4-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1bcf4-121">Example</span></span>  
 <span data-ttu-id="1bcf4-122">O exemplo de código a seguir define o contorno de uma estrutura que inclui `IsFalse` definições `IsTrue` para os operadores e.</span><span class="sxs-lookup"><span data-stu-id="1bcf4-122">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="1bcf4-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1bcf4-123">See also</span></span>

- [<span data-ttu-id="1bcf4-124">Operador IsFalse</span><span class="sxs-lookup"><span data-stu-id="1bcf4-124">IsFalse Operator</span></span>](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [<span data-ttu-id="1bcf4-125">Como: Definir um operador</span><span class="sxs-lookup"><span data-stu-id="1bcf4-125">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="1bcf4-126">Operador OrElse</span><span class="sxs-lookup"><span data-stu-id="1bcf4-126">OrElse Operator</span></span>](../../../visual-basic/language-reference/operators/orelse-operator.md)
