---
title: 'A declaração do operador deve ser uma das: +,-, *,-,-, ^, &amp; , like, mod, and ou, Xor, not,  <<,  >>, =,  <>, <, <=, >, re>=, CType, IsTrue, IsFalse'
ms.date: 07/20/2015
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
ms.openlocfilehash: c388b1b0762dd7475ca365a8a62228d0b5d59414
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873609"
---
# <a name="operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not--"></a><span data-ttu-id="8369d-102">A declaração do operador deve ser um destes: +,-, \*, \, /, ^, &amp; , like, mod, and ou, Xor, not, \<\<, >>...</span><span class="sxs-lookup"><span data-stu-id="8369d-102">Operator declaration must be one of:  +,-,\*,\,/,^, &amp;, Like, Mod, And, Or, Xor, Not, \<\<, >>...</span></span>

<span data-ttu-id="8369d-103">Você pode declarar apenas um operador que seja elegível para sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="8369d-103">You can declare only an operator that is eligible for overloading.</span></span> <span data-ttu-id="8369d-104">A tabela a seguir lista os operadores que você pode declarar.</span><span class="sxs-lookup"><span data-stu-id="8369d-104">The following table lists the operators you can declare.</span></span>  
  
|<span data-ttu-id="8369d-105">Type</span><span class="sxs-lookup"><span data-stu-id="8369d-105">Type</span></span>|<span data-ttu-id="8369d-106">Operadores</span><span class="sxs-lookup"><span data-stu-id="8369d-106">Operators</span></span>|  
|----------|---------------|  
|<span data-ttu-id="8369d-107">Unário</span><span class="sxs-lookup"><span data-stu-id="8369d-107">Unary</span></span>|<span data-ttu-id="8369d-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span><span class="sxs-lookup"><span data-stu-id="8369d-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span></span>|  
|<span data-ttu-id="8369d-109">Binário</span><span class="sxs-lookup"><span data-stu-id="8369d-109">Binary</span></span>|<span data-ttu-id="8369d-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span><span class="sxs-lookup"><span data-stu-id="8369d-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span></span>|  
|<span data-ttu-id="8369d-111">Conversão (unário)</span><span class="sxs-lookup"><span data-stu-id="8369d-111">Conversion (unary)</span></span>|`CType`|  
  
 <span data-ttu-id="8369d-112">Observe que o operador `=` na lista binária é o operador de comparação, não o operador de atribuição.</span><span class="sxs-lookup"><span data-stu-id="8369d-112">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>  
  
 <span data-ttu-id="8369d-113">**ID do erro:** BC33000</span><span class="sxs-lookup"><span data-stu-id="8369d-113">**Error ID:** BC33000</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8369d-114">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="8369d-114">To correct this error</span></span>  
  
1. <span data-ttu-id="8369d-115">Selecione um operador do conjunto de operadores sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="8369d-115">Select an operator from the set of overloadable operators.</span></span>  
  
2. <span data-ttu-id="8369d-116">Se você precisar da funcionalidade de sobrecarregar um operador que você não pode sobrecarregar diretamente, crie um `Function` procedimento que aceite os parâmetros apropriados e retorne o valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="8369d-116">If you need the functionality of overloading an operator that you cannot overload directly, create a `Function` procedure that takes the appropriate parameters and returns the appropriate value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8369d-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="8369d-117">See also</span></span>

- [<span data-ttu-id="8369d-118">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="8369d-118">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="8369d-119">Procedimentos do operador</span><span class="sxs-lookup"><span data-stu-id="8369d-119">Operator Procedures</span></span>](../../programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="8369d-120">Como definir um operador</span><span class="sxs-lookup"><span data-stu-id="8369d-120">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="8369d-121">Como definir um operador de conversão</span><span class="sxs-lookup"><span data-stu-id="8369d-121">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="8369d-122">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="8369d-122">Function Statement</span></span>](../statements/function-statement.md)
