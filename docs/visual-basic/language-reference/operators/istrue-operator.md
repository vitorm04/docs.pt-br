---
title: Operador IsTrue
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: 2e67a4adabe58ab12d317ae6318c0a2fac29da7d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866948"
---
# <a name="istrue-operator-visual-basic"></a><span data-ttu-id="cb0c9-102">Operador IsTrue (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb0c9-102">IsTrue Operator (Visual Basic)</span></span>

<span data-ttu-id="cb0c9-103">Determina se uma expressão é `True` .</span><span class="sxs-lookup"><span data-stu-id="cb0c9-103">Determines whether an expression is `True`.</span></span>  
  
 <span data-ttu-id="cb0c9-104">Você não pode chamar `IsTrue` explicitamente em seu código, mas o compilador Visual Basic pode usá-lo para gerar código de `OrElse` cláusulas.</span><span class="sxs-lookup"><span data-stu-id="cb0c9-104">You cannot call `IsTrue` explicitly in your code, but the Visual Basic compiler can use it to generate code from `OrElse` clauses.</span></span> <span data-ttu-id="cb0c9-105">Se você definir uma classe ou estrutura e, em seguida, usar uma variável desse tipo em uma `OrElse` cláusula, deverá definir `IsTrue` nessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="cb0c9-105">If you define a class or structure and then use a variable of that type in an `OrElse` clause, you must define `IsTrue` on that class or structure.</span></span>  
  
 <span data-ttu-id="cb0c9-106">O compilador considera os `IsTrue` `IsFalse` operadores e como um *par correspondente*.</span><span class="sxs-lookup"><span data-stu-id="cb0c9-106">The compiler considers the `IsTrue` and `IsFalse` operators as a *matched pair*.</span></span> <span data-ttu-id="cb0c9-107">Isso significa que, se você definir um deles, também deverá definir o outro.</span><span class="sxs-lookup"><span data-stu-id="cb0c9-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
## <a name="compiler-use-of-istrue"></a><span data-ttu-id="cb0c9-108">Uso do compilador de IsTrue</span><span class="sxs-lookup"><span data-stu-id="cb0c9-108">Compiler Use of IsTrue</span></span>  

 <span data-ttu-id="cb0c9-109">Quando você tiver definido uma classe ou estrutura, poderá usar uma variável desse tipo em uma `For` instrução,, `If` `Else If` ou `While` , ou em uma `When` cláusula.</span><span class="sxs-lookup"><span data-stu-id="cb0c9-109">When you have defined a class or structure, you can use a variable of that type in a `For`, `If`, `Else If`, or `While` statement, or in a `When` clause.</span></span> <span data-ttu-id="cb0c9-110">Se você fizer isso, o compilador exigirá um operador que converte o tipo em um `Boolean` valor para que ele possa testar uma condição.</span><span class="sxs-lookup"><span data-stu-id="cb0c9-110">If you do this, the compiler requires an operator that converts your type into a `Boolean` value so it can test a condition.</span></span> <span data-ttu-id="cb0c9-111">Ele procura um operador adequado na seguinte ordem:</span><span class="sxs-lookup"><span data-stu-id="cb0c9-111">It searches for a suitable operator in the following order:</span></span>  
  
1. <span data-ttu-id="cb0c9-112">Um operador de conversão de ampliação de sua classe ou estrutura para `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="cb0c9-112">A widening conversion operator from your class or structure to `Boolean`.</span></span>  
  
2. <span data-ttu-id="cb0c9-113">Um operador de conversão de ampliação de sua classe ou estrutura para `Boolean?` .</span><span class="sxs-lookup"><span data-stu-id="cb0c9-113">A widening conversion operator from your class or structure to `Boolean?`.</span></span>  
  
3. <span data-ttu-id="cb0c9-114">O `IsTrue` operador em sua classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="cb0c9-114">The `IsTrue` operator on your class or structure.</span></span>  
  
4. <span data-ttu-id="cb0c9-115">Uma conversão de restrição para `Boolean?` que não envolve uma conversão de `Boolean` para `Boolean?` .</span><span class="sxs-lookup"><span data-stu-id="cb0c9-115">A narrowing conversion to `Boolean?` that does not involve a conversion from `Boolean` to `Boolean?`.</span></span>  
  
5. <span data-ttu-id="cb0c9-116">Um operador de conversão de restrição de sua classe ou estrutura para `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="cb0c9-116">A narrowing conversion operator from your class or structure to `Boolean`.</span></span>  
  
 <span data-ttu-id="cb0c9-117">Se você não tiver definido nenhuma conversão para `Boolean` ou um `IsTrue` operador, o compilador sinalizará um erro.</span><span class="sxs-lookup"><span data-stu-id="cb0c9-117">If you have not defined any conversion to `Boolean` or an `IsTrue` operator, the compiler signals an error.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cb0c9-118">O `IsTrue` operador pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando seu operando tem o tipo dessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="cb0c9-118">The `IsTrue` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="cb0c9-119">Se o seu código usar esse operador em uma classe ou estrutura desse tipo, certifique-se de entender seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="cb0c9-119">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="cb0c9-120">Para obter mais informações, consulte [procedimentos de operador](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="cb0c9-120">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb0c9-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cb0c9-121">Example</span></span>  

 <span data-ttu-id="cb0c9-122">O exemplo de código a seguir define o contorno de uma estrutura que inclui definições para os `IsFalse` `IsTrue` operadores e.</span><span class="sxs-lookup"><span data-stu-id="cb0c9-122">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="cb0c9-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="cb0c9-123">See also</span></span>

- [<span data-ttu-id="cb0c9-124">Operador IsFalse</span><span class="sxs-lookup"><span data-stu-id="cb0c9-124">IsFalse Operator</span></span>](isfalse-operator.md)
- [<span data-ttu-id="cb0c9-125">Como definir um operador</span><span class="sxs-lookup"><span data-stu-id="cb0c9-125">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="cb0c9-126">Operador OrElse</span><span class="sxs-lookup"><span data-stu-id="cb0c9-126">OrElse Operator</span></span>](orelse-operator.md)
