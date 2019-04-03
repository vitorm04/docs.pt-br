---
title: O ordinal não é válido
ms.date: 07/20/2015
f1_keywords:
- vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
ms.openlocfilehash: f3207c2cc237ae22c295c2b3ed56f18601625226
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822239"
---
# <a name="ordinal-is-not-valid"></a><span data-ttu-id="47cde-102">O ordinal não é válido</span><span class="sxs-lookup"><span data-stu-id="47cde-102">Ordinal is not valid</span></span>
<span data-ttu-id="47cde-103">A chamada para uma biblioteca de vínculo dinâmico (DLL) indicado para usar um número em vez de um nome de procedimento, usando o `#num` sintaxe.</span><span class="sxs-lookup"><span data-stu-id="47cde-103">Your call to a dynamic-link library (DLL) indicated to use a number instead of a procedure name, using the `#num` syntax.</span></span> <span data-ttu-id="47cde-104">Esse erro tem as seguintes causas possíveis:</span><span class="sxs-lookup"><span data-stu-id="47cde-104">This error has the following possible causes:</span></span>  
  
-   <span data-ttu-id="47cde-105">Uma tentativa de converter o `#num` expressão a um ordinal falhou.</span><span class="sxs-lookup"><span data-stu-id="47cde-105">An attempt to convert the `#num` expression to an ordinal failed.</span></span>  
  
-   <span data-ttu-id="47cde-106">O `#num` especificado não especificar qualquer função na DLL.</span><span class="sxs-lookup"><span data-stu-id="47cde-106">The `#num` specified does not specify any function in the DLL.</span></span>  
  
-   <span data-ttu-id="47cde-107">Uma biblioteca de tipos tem uma declaração inválida, resultando no uso interno de um número ordinal inválido.</span><span class="sxs-lookup"><span data-stu-id="47cde-107">A type library has an invalid declaration resulting in internal use of an invalid ordinal number.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="47cde-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="47cde-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="47cde-109">Verifique se que a expressão representa um número válido, ou chame o procedimento por nome.</span><span class="sxs-lookup"><span data-stu-id="47cde-109">Make sure the expression represents a valid number, or call the procedure by name.</span></span>  
  
2.  <span data-ttu-id="47cde-110">Certifique-se de `#num` identifica uma função válida na DLL.</span><span class="sxs-lookup"><span data-stu-id="47cde-110">Make sure `#num` identifies a valid function in the DLL.</span></span>  
  
3.  <span data-ttu-id="47cde-111">Isole a causa do problema comentando o código de chamada de procedimento.</span><span class="sxs-lookup"><span data-stu-id="47cde-111">Isolate the procedure call causing the problem by commenting out the code.</span></span> <span data-ttu-id="47cde-112">Gravar um `Declare` instrução para o procedimento e relatar o problema para o fornecedor da biblioteca de tipo.</span><span class="sxs-lookup"><span data-stu-id="47cde-112">Write a `Declare` statement for the procedure, and report the problem to the type library vendor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47cde-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="47cde-113">See also</span></span>

- [<span data-ttu-id="47cde-114">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="47cde-114">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
