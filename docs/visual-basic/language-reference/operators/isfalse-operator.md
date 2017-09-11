---
title: Operador IsFalse (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.isfalse
dev_langs:
- VB
helpviewer_keywords:
- AndAlso operator
- IsFalse operator
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
caps.latest.revision: 14
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
ms.openlocfilehash: 1d729a33021a5658350cf4847b9bff5758ca831d
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="isfalse-operator-visual-basic"></a><span data-ttu-id="31eda-102">Operador IsFalse (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31eda-102">IsFalse Operator (Visual Basic)</span></span>
<span data-ttu-id="31eda-103">Determina se uma expressão é `False`.</span><span class="sxs-lookup"><span data-stu-id="31eda-103">Determines whether an expression is `False`.</span></span>  
  
 <span data-ttu-id="31eda-104">Não é possível chamar `IsFalse` explicitamente no seu código, mas o Visual Basic compilador pode usá-lo para gerar código de `AndAlso` cláusulas.</span><span class="sxs-lookup"><span data-stu-id="31eda-104">You cannot call `IsFalse` explicitly in your code, but the Visual Basic compiler can use it to generate code from `AndAlso` clauses.</span></span> <span data-ttu-id="31eda-105">Se você definir uma classe ou estrutura e, em seguida, usar uma variável desse tipo em uma `AndAlso` cláusula, você deve definir `IsFalse` na classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="31eda-105">If you define a class or structure and then use a variable of that type in an `AndAlso` clause, you must define `IsFalse` on that class or structure.</span></span>  
  
 <span data-ttu-id="31eda-106">O compilador considera o `IsFalse` e `IsTrue` operadores como um *par correspondente*.</span><span class="sxs-lookup"><span data-stu-id="31eda-106">The compiler considers the `IsFalse` and `IsTrue` operators as a *matched pair*.</span></span> <span data-ttu-id="31eda-107">Isso significa que se você definir um deles, você deve também definir o outro.</span><span class="sxs-lookup"><span data-stu-id="31eda-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="31eda-108">O `IsFalse` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando seu operando tem o tipo da classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="31eda-108">The `IsFalse` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="31eda-109">Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que você entende seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="31eda-109">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="31eda-110">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="31eda-110">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="31eda-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="31eda-111">Example</span></span>  
 <span data-ttu-id="31eda-112">O exemplo de código a seguir define o contorno de uma estrutura que inclui as definições para o `IsFalse` e `IsTrue` operadores.</span><span class="sxs-lookup"><span data-stu-id="31eda-112">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 <span data-ttu-id="31eda-113">[!code-vb[VbVbalrOperators&#28;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isfalse-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="31eda-113">[!code-vb[VbVbalrOperators#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isfalse-operator_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31eda-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="31eda-114">See Also</span></span>  
 <span data-ttu-id="31eda-115">[Operador IsTrue](../../../visual-basic/language-reference/operators/istrue-operator.md) </span><span class="sxs-lookup"><span data-stu-id="31eda-115">[IsTrue Operator](../../../visual-basic/language-reference/operators/istrue-operator.md) </span></span>  
<span data-ttu-id="31eda-116"> [Como: definir um operador](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md) </span><span class="sxs-lookup"><span data-stu-id="31eda-116"> [How to: Define an Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md) </span></span>  
<span data-ttu-id="31eda-117"> [Operador AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md)</span><span class="sxs-lookup"><span data-stu-id="31eda-117"> [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md)</span></span>
