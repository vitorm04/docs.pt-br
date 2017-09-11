---
title: "Declaração do operador deve ser um destes: +,-, *,-, -, ^, &amp;, Like, Mod e, Or, Xor, não, &lt; &lt;, &gt; &gt;, =, &lt; &gt;, &lt;, &lt;= &gt;, &gt;=, CType, IsTrue, IsFalse | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc33000
- vbc33000
dev_langs:
- VB
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
caps.latest.revision: 12
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
ms.openlocfilehash: b3122bca1ae003132e643a6c08a6b6450616c9ca
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not-ltlt-gtgt"></a><span data-ttu-id="6caf1-102">Declaração do operador deve ser um destes: +,-, *,\,/, ^, &amp;, Like, Mod e, Or, Xor, não, &lt; &lt;, &gt; &gt;...</span><span class="sxs-lookup"><span data-stu-id="6caf1-102">Operator declaration must be one of:  +,-,*,\,/,^, &amp;, Like, Mod, And, Or, Xor, Not, &lt;&lt;, &gt;&gt;...</span></span>
<span data-ttu-id="6caf1-103">Você pode declarar somente um operador que está qualificado para a sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="6caf1-103">You can declare only an operator that is eligible for overloading.</span></span> <span data-ttu-id="6caf1-104">A tabela a seguir lista os operadores que você pode declarar.</span><span class="sxs-lookup"><span data-stu-id="6caf1-104">The following table lists the operators you can declare.</span></span>  
  
|<span data-ttu-id="6caf1-105">Tipo</span><span class="sxs-lookup"><span data-stu-id="6caf1-105">Type</span></span>|<span data-ttu-id="6caf1-106">Operadores</span><span class="sxs-lookup"><span data-stu-id="6caf1-106">Operators</span></span>|  
|----------|---------------|  
|<span data-ttu-id="6caf1-107">Unário</span><span class="sxs-lookup"><span data-stu-id="6caf1-107">Unary</span></span>|<span data-ttu-id="6caf1-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span><span class="sxs-lookup"><span data-stu-id="6caf1-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span></span>|  
|<span data-ttu-id="6caf1-109">Binário</span><span class="sxs-lookup"><span data-stu-id="6caf1-109">Binary</span></span>|<span data-ttu-id="6caf1-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span><span class="sxs-lookup"><span data-stu-id="6caf1-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span></span>|  
|<span data-ttu-id="6caf1-111">Conversão (unário)</span><span class="sxs-lookup"><span data-stu-id="6caf1-111">Conversion (unary)</span></span>|`CType`|  
  
 <span data-ttu-id="6caf1-112">Observe que o `=` operador na lista binária é o operador de comparação, não o operador de atribuição.</span><span class="sxs-lookup"><span data-stu-id="6caf1-112">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>  
  
 <span data-ttu-id="6caf1-113">**ID do erro:** BC33000</span><span class="sxs-lookup"><span data-stu-id="6caf1-113">**Error ID:** BC33000</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6caf1-114">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="6caf1-114">To correct this error</span></span>  
  
1.  <span data-ttu-id="6caf1-115">Selecione um operador de conjunto de operadores que pode ser sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="6caf1-115">Select an operator from the set of overloadable operators.</span></span>  
  
2.  <span data-ttu-id="6caf1-116">Se você precisar da funcionalidade de sobrecarregar um operador que você não pode sobrecarregar diretamente, crie uma `Function` procedimento que usa os parâmetros apropriados e retorna o valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="6caf1-116">If you need the functionality of overloading an operator that you cannot overload directly, create a `Function` procedure that takes the appropriate parameters and returns the appropriate value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6caf1-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6caf1-117">See Also</span></span>  
 <span data-ttu-id="6caf1-118">[Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md) </span><span class="sxs-lookup"><span data-stu-id="6caf1-118">[Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md) </span></span>  
<span data-ttu-id="6caf1-119"> [Procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="6caf1-119"> [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md) </span></span>  
<span data-ttu-id="6caf1-120"> [Como: definir um operador](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md) </span><span class="sxs-lookup"><span data-stu-id="6caf1-120"> [How to: Define an Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md) </span></span>  
<span data-ttu-id="6caf1-121"> [Como: definir um operador de conversão](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md) </span><span class="sxs-lookup"><span data-stu-id="6caf1-121"> [How to: Define a Conversion Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md) </span></span>  
<span data-ttu-id="6caf1-122"> [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)</span><span class="sxs-lookup"><span data-stu-id="6caf1-122"> [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)</span></span>
