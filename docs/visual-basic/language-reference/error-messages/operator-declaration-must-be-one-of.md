---
title: "Declaração do operador deve ser um dos: +,-, *,-, -, ^, &amp;, Like, Mod e, Or, Xor, não, &lt; &lt;, &gt; &gt;, =, &lt; &gt;, &lt;, &lt;= &gt; , &gt;=, CType, IsTrue, IsFalse"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords: BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 80c8358dd13105c18e73e94735a51b02d5bd22c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not-ltlt-gtgt"></a><span data-ttu-id="3ee8b-102">Declaração do operador deve ser um dos: +,-, *,\,/, ^, &amp;, Like, Mod e, Or, Xor, não, &lt; &lt;, &gt; &gt;...</span><span class="sxs-lookup"><span data-stu-id="3ee8b-102">Operator declaration must be one of:  +,-,*,\,/,^, &amp;, Like, Mod, And, Or, Xor, Not, &lt;&lt;, &gt;&gt;...</span></span>
<span data-ttu-id="3ee8b-103">Você pode declarar somente um operador que é qualificado para a sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="3ee8b-103">You can declare only an operator that is eligible for overloading.</span></span> <span data-ttu-id="3ee8b-104">A tabela a seguir lista os operadores que você pode declarar.</span><span class="sxs-lookup"><span data-stu-id="3ee8b-104">The following table lists the operators you can declare.</span></span>  
  
|<span data-ttu-id="3ee8b-105">Tipo</span><span class="sxs-lookup"><span data-stu-id="3ee8b-105">Type</span></span>|<span data-ttu-id="3ee8b-106">Operadores</span><span class="sxs-lookup"><span data-stu-id="3ee8b-106">Operators</span></span>|  
|----------|---------------|  
|<span data-ttu-id="3ee8b-107">Unário</span><span class="sxs-lookup"><span data-stu-id="3ee8b-107">Unary</span></span>|<span data-ttu-id="3ee8b-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span><span class="sxs-lookup"><span data-stu-id="3ee8b-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span></span>|  
|<span data-ttu-id="3ee8b-109">Binário</span><span class="sxs-lookup"><span data-stu-id="3ee8b-109">Binary</span></span>|<span data-ttu-id="3ee8b-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span><span class="sxs-lookup"><span data-stu-id="3ee8b-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span></span>|  
|<span data-ttu-id="3ee8b-111">Conversão (unário)</span><span class="sxs-lookup"><span data-stu-id="3ee8b-111">Conversion (unary)</span></span>|`CType`|  
  
 <span data-ttu-id="3ee8b-112">Observe que o `=` operador na lista binária é o operador de comparação, não o operador de atribuição.</span><span class="sxs-lookup"><span data-stu-id="3ee8b-112">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>  
  
 <span data-ttu-id="3ee8b-113">**ID do erro:** BC33000</span><span class="sxs-lookup"><span data-stu-id="3ee8b-113">**Error ID:** BC33000</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3ee8b-114">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="3ee8b-114">To correct this error</span></span>  
  
1.  <span data-ttu-id="3ee8b-115">Selecione um operador de conjunto de operadores que pode ser sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="3ee8b-115">Select an operator from the set of overloadable operators.</span></span>  
  
2.  <span data-ttu-id="3ee8b-116">Se você precisar da funcionalidade de sobrecarregar um operador que você não pode sobrecarregar diretamente, crie um `Function` procedimento que usa os parâmetros apropriados e retorna o valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="3ee8b-116">If you need the functionality of overloading an operator that you cannot overload directly, create a `Function` procedure that takes the appropriate parameters and returns the appropriate value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ee8b-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3ee8b-117">See Also</span></span>  
 [<span data-ttu-id="3ee8b-118">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="3ee8b-118">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="3ee8b-119">Procedimentos de Operador</span><span class="sxs-lookup"><span data-stu-id="3ee8b-119">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [<span data-ttu-id="3ee8b-120">Como definir um operador</span><span class="sxs-lookup"><span data-stu-id="3ee8b-120">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="3ee8b-121">Como definir um operador de conversão</span><span class="sxs-lookup"><span data-stu-id="3ee8b-121">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="3ee8b-122">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="3ee8b-122">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
