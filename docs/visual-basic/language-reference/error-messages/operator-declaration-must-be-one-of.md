---
title: 'Declaração do operador deve ser um destes: +,-, *,-, -, ^, &amp;, Like, Mod e, Or, Xor, não, <<>>,, <>, <, < =, >, > =, CType, IsTrue, IsFalse'
ms.date: 07/20/2015
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
ms.openlocfilehash: 4283547109ec312cc4fe07a054bbb8db3bff660f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946595"
---
# <a name="operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not--"></a><span data-ttu-id="723dc-102">Declaração do operador deve ser um destes: +,-, \*,\,/, ^, &amp;, Like, Mod e, Or, Xor, não, \< \<, >>...</span><span class="sxs-lookup"><span data-stu-id="723dc-102">Operator declaration must be one of:  +,-,\*,\,/,^, &amp;, Like, Mod, And, Or, Xor, Not, \<\<, >>...</span></span>
<span data-ttu-id="723dc-103">Você pode declarar somente um operador que é qualificado para a sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="723dc-103">You can declare only an operator that is eligible for overloading.</span></span> <span data-ttu-id="723dc-104">A tabela a seguir lista os operadores que você pode declarar.</span><span class="sxs-lookup"><span data-stu-id="723dc-104">The following table lists the operators you can declare.</span></span>  
  
|<span data-ttu-id="723dc-105">Tipo</span><span class="sxs-lookup"><span data-stu-id="723dc-105">Type</span></span>|<span data-ttu-id="723dc-106">Operadores</span><span class="sxs-lookup"><span data-stu-id="723dc-106">Operators</span></span>|  
|----------|---------------|  
|<span data-ttu-id="723dc-107">Unário</span><span class="sxs-lookup"><span data-stu-id="723dc-107">Unary</span></span>|<span data-ttu-id="723dc-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span><span class="sxs-lookup"><span data-stu-id="723dc-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span></span>|  
|<span data-ttu-id="723dc-109">Binário</span><span class="sxs-lookup"><span data-stu-id="723dc-109">Binary</span></span>|<span data-ttu-id="723dc-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span><span class="sxs-lookup"><span data-stu-id="723dc-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span></span>|  
|<span data-ttu-id="723dc-111">Conversão (unário)</span><span class="sxs-lookup"><span data-stu-id="723dc-111">Conversion (unary)</span></span>|`CType`|  
  
 <span data-ttu-id="723dc-112">Observe que o `=` operador na lista binária é o operador de comparação, não o operador de atribuição.</span><span class="sxs-lookup"><span data-stu-id="723dc-112">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>  
  
 <span data-ttu-id="723dc-113">**ID do erro:** BC33000</span><span class="sxs-lookup"><span data-stu-id="723dc-113">**Error ID:** BC33000</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="723dc-114">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="723dc-114">To correct this error</span></span>  
  
1. <span data-ttu-id="723dc-115">Selecione um operador do conjunto de operadores sobrecarregáveis.</span><span class="sxs-lookup"><span data-stu-id="723dc-115">Select an operator from the set of overloadable operators.</span></span>  
  
2. <span data-ttu-id="723dc-116">Se você precisar da funcionalidade de sobrecarregar um operador que você não pode sobrecarregar diretamente, crie um `Function` procedimento que usa os parâmetros apropriados e retorna o valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="723dc-116">If you need the functionality of overloading an operator that you cannot overload directly, create a `Function` procedure that takes the appropriate parameters and returns the appropriate value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="723dc-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="723dc-117">See also</span></span>

- [<span data-ttu-id="723dc-118">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="723dc-118">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="723dc-119">Procedimentos de Operador</span><span class="sxs-lookup"><span data-stu-id="723dc-119">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="723dc-120">Como: Definir um operador</span><span class="sxs-lookup"><span data-stu-id="723dc-120">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="723dc-121">Como: Definir um operador de conversão</span><span class="sxs-lookup"><span data-stu-id="723dc-121">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="723dc-122">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="723dc-122">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
