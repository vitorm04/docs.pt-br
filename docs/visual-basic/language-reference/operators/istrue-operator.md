---
title: Operador IsTrue
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: 4b863eed8406a10b9a44d7139f8659ac5cb758ad
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349509"
---
# <a name="istrue-operator-visual-basic"></a><span data-ttu-id="c97e8-102">Operador IsTrue (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c97e8-102">IsTrue Operator (Visual Basic)</span></span>
<span data-ttu-id="c97e8-103">Determina se uma expressão é `True`da.</span><span class="sxs-lookup"><span data-stu-id="c97e8-103">Determines whether an expression is `True`.</span></span>  
  
 <span data-ttu-id="c97e8-104">Você não pode chamar `IsTrue` explicitamente em seu código, mas o compilador Visual Basic pode usá-lo para gerar código de cláusulas `OrElse`.</span><span class="sxs-lookup"><span data-stu-id="c97e8-104">You cannot call `IsTrue` explicitly in your code, but the Visual Basic compiler can use it to generate code from `OrElse` clauses.</span></span> <span data-ttu-id="c97e8-105">Se você definir uma classe ou estrutura e, em seguida, usar uma variável desse tipo em uma cláusula `OrElse`, deverá definir `IsTrue` nessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="c97e8-105">If you define a class or structure and then use a variable of that type in an `OrElse` clause, you must define `IsTrue` on that class or structure.</span></span>  
  
 <span data-ttu-id="c97e8-106">O compilador considera os operadores `IsTrue` e `IsFalse` como um *par correspondente*.</span><span class="sxs-lookup"><span data-stu-id="c97e8-106">The compiler considers the `IsTrue` and `IsFalse` operators as a *matched pair*.</span></span> <span data-ttu-id="c97e8-107">Isso significa que, se você definir um deles, também deverá definir o outro.</span><span class="sxs-lookup"><span data-stu-id="c97e8-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
## <a name="compiler-use-of-istrue"></a><span data-ttu-id="c97e8-108">Uso do compilador de IsTrue</span><span class="sxs-lookup"><span data-stu-id="c97e8-108">Compiler Use of IsTrue</span></span>  
 <span data-ttu-id="c97e8-109">Quando você tiver definido uma classe ou estrutura, poderá usar uma variável desse tipo em uma `For`, `If`, `Else If`ou instrução de `While` ou em uma cláusula `When`.</span><span class="sxs-lookup"><span data-stu-id="c97e8-109">When you have defined a class or structure, you can use a variable of that type in a `For`, `If`, `Else If`, or `While` statement, or in a `When` clause.</span></span> <span data-ttu-id="c97e8-110">Se você fizer isso, o compilador exigirá um operador que converte o tipo em um valor `Boolean` para que possa testar uma condição.</span><span class="sxs-lookup"><span data-stu-id="c97e8-110">If you do this, the compiler requires an operator that converts your type into a `Boolean` value so it can test a condition.</span></span> <span data-ttu-id="c97e8-111">Ele procura um operador adequado na seguinte ordem:</span><span class="sxs-lookup"><span data-stu-id="c97e8-111">It searches for a suitable operator in the following order:</span></span>  
  
1. <span data-ttu-id="c97e8-112">Um operador de conversão de ampliação de sua classe ou estrutura para `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="c97e8-112">A widening conversion operator from your class or structure to `Boolean`.</span></span>  
  
2. <span data-ttu-id="c97e8-113">Um operador de conversão de ampliação de sua classe ou estrutura para `Boolean?`.</span><span class="sxs-lookup"><span data-stu-id="c97e8-113">A widening conversion operator from your class or structure to `Boolean?`.</span></span>  
  
3. <span data-ttu-id="c97e8-114">O operador de `IsTrue` em sua classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="c97e8-114">The `IsTrue` operator on your class or structure.</span></span>  
  
4. <span data-ttu-id="c97e8-115">Uma conversão de restrição para `Boolean?` que não envolve uma conversão de `Boolean` para `Boolean?`.</span><span class="sxs-lookup"><span data-stu-id="c97e8-115">A narrowing conversion to `Boolean?` that does not involve a conversion from `Boolean` to `Boolean?`.</span></span>  
  
5. <span data-ttu-id="c97e8-116">Um operador de conversão de restrição de sua classe ou estrutura para `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="c97e8-116">A narrowing conversion operator from your class or structure to `Boolean`.</span></span>  
  
 <span data-ttu-id="c97e8-117">Se você não tiver definido nenhuma conversão para `Boolean` ou um operador de `IsTrue`, o compilador sinalizará um erro.</span><span class="sxs-lookup"><span data-stu-id="c97e8-117">If you have not defined any conversion to `Boolean` or an `IsTrue` operator, the compiler signals an error.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c97e8-118">O operador `IsTrue` pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando seu operando tem o tipo dessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="c97e8-118">The `IsTrue` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="c97e8-119">Se o seu código usar esse operador em uma classe ou estrutura desse tipo, certifique-se de entender seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="c97e8-119">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="c97e8-120">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="c97e8-120">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c97e8-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c97e8-121">Example</span></span>  
 <span data-ttu-id="c97e8-122">O exemplo de código a seguir define o contorno de uma estrutura que inclui definições para os operadores de `IsFalse` e `IsTrue`.</span><span class="sxs-lookup"><span data-stu-id="c97e8-122">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="c97e8-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c97e8-123">See also</span></span>

- [<span data-ttu-id="c97e8-124">Operador IsFalse</span><span class="sxs-lookup"><span data-stu-id="c97e8-124">IsFalse Operator</span></span>](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [<span data-ttu-id="c97e8-125">Como definir um operador</span><span class="sxs-lookup"><span data-stu-id="c97e8-125">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="c97e8-126">Operador OrElse</span><span class="sxs-lookup"><span data-stu-id="c97e8-126">OrElse Operator</span></span>](../../../visual-basic/language-reference/operators/orelse-operator.md)
