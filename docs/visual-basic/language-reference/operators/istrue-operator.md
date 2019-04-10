---
title: Operador IsTrue (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: 6c5ec6d953d174b525dee7ad3034d2d01ae4950f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59344943"
---
# <a name="istrue-operator-visual-basic"></a><span data-ttu-id="91959-102">Operador IsTrue (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91959-102">IsTrue Operator (Visual Basic)</span></span>
<span data-ttu-id="91959-103">Determina se uma expressão é `True`.</span><span class="sxs-lookup"><span data-stu-id="91959-103">Determines whether an expression is `True`.</span></span>  
  
 <span data-ttu-id="91959-104">Você não pode chamar `IsTrue` explicitamente no seu código, mas o Visual Basic compilador pode usá-lo para gerar o código de `OrElse` cláusulas.</span><span class="sxs-lookup"><span data-stu-id="91959-104">You cannot call `IsTrue` explicitly in your code, but the Visual Basic compiler can use it to generate code from `OrElse` clauses.</span></span> <span data-ttu-id="91959-105">Se você definir uma classe ou estrutura e, em seguida, usar uma variável desse tipo em uma `OrElse` cláusula, você deve definir `IsTrue` nessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="91959-105">If you define a class or structure and then use a variable of that type in an `OrElse` clause, you must define `IsTrue` on that class or structure.</span></span>  
  
 <span data-ttu-id="91959-106">O compilador considera a `IsTrue` e `IsFalse` operadores como um *par correspondente*.</span><span class="sxs-lookup"><span data-stu-id="91959-106">The compiler considers the `IsTrue` and `IsFalse` operators as a *matched pair*.</span></span> <span data-ttu-id="91959-107">Isso significa que se você definir um deles, você deve também definir outro.</span><span class="sxs-lookup"><span data-stu-id="91959-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
## <a name="compiler-use-of-istrue"></a><span data-ttu-id="91959-108">Uso do compilador de IsTrue</span><span class="sxs-lookup"><span data-stu-id="91959-108">Compiler Use of IsTrue</span></span>  
 <span data-ttu-id="91959-109">Quando você tiver definido uma classe ou estrutura, você pode usar uma variável desse tipo em uma `For`, `If`, `Else If`, ou `While` instrução, ou em um `When` cláusula.</span><span class="sxs-lookup"><span data-stu-id="91959-109">When you have defined a class or structure, you can use a variable of that type in a `For`, `If`, `Else If`, or `While` statement, or in a `When` clause.</span></span> <span data-ttu-id="91959-110">Se você fizer isso, o compilador exige um operador que converte seu tipo em um `Boolean` para que ele possa testar uma condição de valor.</span><span class="sxs-lookup"><span data-stu-id="91959-110">If you do this, the compiler requires an operator that converts your type into a `Boolean` value so it can test a condition.</span></span> <span data-ttu-id="91959-111">Ele procura por um operador adequado na seguinte ordem:</span><span class="sxs-lookup"><span data-stu-id="91959-111">It searches for a suitable operator in the following order:</span></span>  
  
1. <span data-ttu-id="91959-112">Um operador de conversão de ampliação de sua classe ou estrutura para `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="91959-112">A widening conversion operator from your class or structure to `Boolean`.</span></span>  
  
2. <span data-ttu-id="91959-113">Um operador de conversão de ampliação de sua classe ou estrutura para `Boolean?`.</span><span class="sxs-lookup"><span data-stu-id="91959-113">A widening conversion operator from your class or structure to `Boolean?`.</span></span>  
  
3. <span data-ttu-id="91959-114">O `IsTrue` operador em sua classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="91959-114">The `IsTrue` operator on your class or structure.</span></span>  
  
4. <span data-ttu-id="91959-115">Uma conversão de estreitamento `Boolean?` que não envolve uma conversão de `Boolean` para `Boolean?`.</span><span class="sxs-lookup"><span data-stu-id="91959-115">A narrowing conversion to `Boolean?` that does not involve a conversion from `Boolean` to `Boolean?`.</span></span>  
  
5. <span data-ttu-id="91959-116">Um operador de conversão de estreitamento de sua classe ou estrutura para `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="91959-116">A narrowing conversion operator from your class or structure to `Boolean`.</span></span>  
  
 <span data-ttu-id="91959-117">Se você não definiu qualquer conversão para `Boolean` ou um `IsTrue` operador, o compilador sinaliza um erro.</span><span class="sxs-lookup"><span data-stu-id="91959-117">If you have not defined any conversion to `Boolean` or an `IsTrue` operator, the compiler signals an error.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="91959-118">O `IsTrue` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando o operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="91959-118">The `IsTrue` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="91959-119">Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que você entende seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="91959-119">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="91959-120">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="91959-120">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="91959-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="91959-121">Example</span></span>  
 <span data-ttu-id="91959-122">O exemplo de código a seguir define o contorno de uma estrutura que inclui as definições para o `IsFalse` e `IsTrue` operadores.</span><span class="sxs-lookup"><span data-stu-id="91959-122">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="91959-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="91959-123">See also</span></span>

- [<span data-ttu-id="91959-124">Operador IsFalse</span><span class="sxs-lookup"><span data-stu-id="91959-124">IsFalse Operator</span></span>](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [<span data-ttu-id="91959-125">Como: definir um operador</span><span class="sxs-lookup"><span data-stu-id="91959-125">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="91959-126">Operador OrElse</span><span class="sxs-lookup"><span data-stu-id="91959-126">OrElse Operator</span></span>](../../../visual-basic/language-reference/operators/orelse-operator.md)
