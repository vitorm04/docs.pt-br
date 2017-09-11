---
title: Operador IsTrue (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.istrue
dev_langs:
- VB
helpviewer_keywords:
- IsTrue operator
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
caps.latest.revision: 17
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
ms.openlocfilehash: 70c9be04205d50e7b4518627b39df097f58c0caa
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="istrue-operator-visual-basic"></a><span data-ttu-id="39f96-102">Operador IsTrue (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39f96-102">IsTrue Operator (Visual Basic)</span></span>
<span data-ttu-id="39f96-103">Determina se uma expressão é `True`.</span><span class="sxs-lookup"><span data-stu-id="39f96-103">Determines whether an expression is `True`.</span></span>  
  
 <span data-ttu-id="39f96-104">Não é possível chamar `IsTrue` explicitamente no seu código, mas o Visual Basic compilador pode usá-lo para gerar código de `OrElse` cláusulas.</span><span class="sxs-lookup"><span data-stu-id="39f96-104">You cannot call `IsTrue` explicitly in your code, but the Visual Basic compiler can use it to generate code from `OrElse` clauses.</span></span> <span data-ttu-id="39f96-105">Se você definir uma classe ou estrutura e, em seguida, usar uma variável desse tipo em uma `OrElse` cláusula, você deve definir `IsTrue` na classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="39f96-105">If you define a class or structure and then use a variable of that type in an `OrElse` clause, you must define `IsTrue` on that class or structure.</span></span>  
  
 <span data-ttu-id="39f96-106">O compilador considera o `IsTrue` e `IsFalse` operadores como um *par correspondente*.</span><span class="sxs-lookup"><span data-stu-id="39f96-106">The compiler considers the `IsTrue` and `IsFalse` operators as a *matched pair*.</span></span> <span data-ttu-id="39f96-107">Isso significa que se você definir um deles, você deve também definir o outro.</span><span class="sxs-lookup"><span data-stu-id="39f96-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
## <a name="compiler-use-of-istrue"></a><span data-ttu-id="39f96-108">Uso do compilador de IsTrue</span><span class="sxs-lookup"><span data-stu-id="39f96-108">Compiler Use of IsTrue</span></span>  
 <span data-ttu-id="39f96-109">Quando você tiver definido uma classe ou estrutura, você pode usar uma variável desse tipo em uma `For`, `If`, `Else``If`, ou `While` instrução, ou em um `When` cláusula.</span><span class="sxs-lookup"><span data-stu-id="39f96-109">When you have defined a class or structure, you can use a variable of that type in a `For`, `If`, `Else``If`, or `While` statement, or in a `When` clause.</span></span> <span data-ttu-id="39f96-110">Se você fizer isso, o compilador exige um operador que converte o tipo em um `Boolean` para que ele possa testar uma condição de valor.</span><span class="sxs-lookup"><span data-stu-id="39f96-110">If you do this, the compiler requires an operator that converts your type into a `Boolean` value so it can test a condition.</span></span> <span data-ttu-id="39f96-111">Ele procura por um operador adequado na seguinte ordem:</span><span class="sxs-lookup"><span data-stu-id="39f96-111">It searches for a suitable operator in the following order:</span></span>  
  
1.  <span data-ttu-id="39f96-112">Um operador de conversão de ampliação de sua classe ou estrutura para `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="39f96-112">A widening conversion operator from your class or structure to `Boolean`.</span></span>  
  
2.  <span data-ttu-id="39f96-113">Um operador de conversão de ampliação de sua classe ou estrutura para `Boolean?`.</span><span class="sxs-lookup"><span data-stu-id="39f96-113">A widening conversion operator from your class or structure to `Boolean?`.</span></span>  
  
3.  <span data-ttu-id="39f96-114">O `IsTrue` operador em sua classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="39f96-114">The `IsTrue` operator on your class or structure.</span></span>  
  
4.  <span data-ttu-id="39f96-115">Uma conversão de redução para `Boolean?` que não envolvem uma conversão de `Boolean` para `Boolean?`.</span><span class="sxs-lookup"><span data-stu-id="39f96-115">A narrowing conversion to `Boolean?` that does not involve a conversion from `Boolean` to `Boolean?`.</span></span>  
  
5.  <span data-ttu-id="39f96-116">Um operador de conversão de redução de sua classe ou estrutura para `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="39f96-116">A narrowing conversion operator from your class or structure to `Boolean`.</span></span>  
  
 <span data-ttu-id="39f96-117">Se você não definiu qualquer conversão para `Boolean` ou um `IsTrue` operador, o compilador sinaliza um erro.</span><span class="sxs-lookup"><span data-stu-id="39f96-117">If you have not defined any conversion to `Boolean` or an `IsTrue` operator, the compiler signals an error.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="39f96-118">O `IsTrue` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando seu operando tem o tipo da classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="39f96-118">The `IsTrue` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="39f96-119">Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que você entende seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="39f96-119">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="39f96-120">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="39f96-120">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="39f96-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="39f96-121">Example</span></span>  
 <span data-ttu-id="39f96-122">O exemplo de código a seguir define o contorno de uma estrutura que inclui as definições para o `IsFalse` e `IsTrue` operadores.</span><span class="sxs-lookup"><span data-stu-id="39f96-122">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 <span data-ttu-id="39f96-123">[!code-vb[VbVbalrOperators&#28;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/istrue-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="39f96-123">[!code-vb[VbVbalrOperators#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/istrue-operator_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39f96-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="39f96-124">See Also</span></span>  
 <span data-ttu-id="39f96-125">[Operador IsFalse](../../../visual-basic/language-reference/operators/isfalse-operator.md) </span><span class="sxs-lookup"><span data-stu-id="39f96-125">[IsFalse Operator](../../../visual-basic/language-reference/operators/isfalse-operator.md) </span></span>  
<span data-ttu-id="39f96-126"> [Como: definir um operador](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md) </span><span class="sxs-lookup"><span data-stu-id="39f96-126"> [How to: Define an Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md) </span></span>  
<span data-ttu-id="39f96-127"> [Operador OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md)</span><span class="sxs-lookup"><span data-stu-id="39f96-127"> [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md)</span></span>
