---
title: O ordinal não é válido
ms.date: 07/20/2015
f1_keywords:
- vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
ms.openlocfilehash: 28f78161e14604c1f59872801855ccc918faec58
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59299248"
---
# <a name="ordinal-is-not-valid"></a><span data-ttu-id="a8533-102">O ordinal não é válido</span><span class="sxs-lookup"><span data-stu-id="a8533-102">Ordinal is not valid</span></span>
<span data-ttu-id="a8533-103">A chamada para uma biblioteca de vínculo dinâmico (DLL) indicado para usar um número em vez de um nome de procedimento, usando o `#num` sintaxe.</span><span class="sxs-lookup"><span data-stu-id="a8533-103">Your call to a dynamic-link library (DLL) indicated to use a number instead of a procedure name, using the `#num` syntax.</span></span> <span data-ttu-id="a8533-104">Esse erro tem as seguintes causas possíveis:</span><span class="sxs-lookup"><span data-stu-id="a8533-104">This error has the following possible causes:</span></span>  
  
-   <span data-ttu-id="a8533-105">Uma tentativa de converter o `#num` expressão a um ordinal falhou.</span><span class="sxs-lookup"><span data-stu-id="a8533-105">An attempt to convert the `#num` expression to an ordinal failed.</span></span>  
  
-   <span data-ttu-id="a8533-106">O `#num` especificado não especificar qualquer função na DLL.</span><span class="sxs-lookup"><span data-stu-id="a8533-106">The `#num` specified does not specify any function in the DLL.</span></span>  
  
-   <span data-ttu-id="a8533-107">Uma biblioteca de tipos tem uma declaração inválida, resultando no uso interno de um número ordinal inválido.</span><span class="sxs-lookup"><span data-stu-id="a8533-107">A type library has an invalid declaration resulting in internal use of an invalid ordinal number.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a8533-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="a8533-108">To correct this error</span></span>  
  
1. <span data-ttu-id="a8533-109">Verifique se que a expressão representa um número válido, ou chame o procedimento por nome.</span><span class="sxs-lookup"><span data-stu-id="a8533-109">Make sure the expression represents a valid number, or call the procedure by name.</span></span>  
  
2. <span data-ttu-id="a8533-110">Certifique-se de `#num` identifica uma função válida na DLL.</span><span class="sxs-lookup"><span data-stu-id="a8533-110">Make sure `#num` identifies a valid function in the DLL.</span></span>  
  
3. <span data-ttu-id="a8533-111">Isole a causa do problema comentando o código de chamada de procedimento.</span><span class="sxs-lookup"><span data-stu-id="a8533-111">Isolate the procedure call causing the problem by commenting out the code.</span></span> <span data-ttu-id="a8533-112">Gravar um `Declare` instrução para o procedimento e relatar o problema para o fornecedor da biblioteca de tipo.</span><span class="sxs-lookup"><span data-stu-id="a8533-112">Write a `Declare` statement for the procedure, and report the problem to the type library vendor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8533-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a8533-113">See also</span></span>

- [<span data-ttu-id="a8533-114">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="a8533-114">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
