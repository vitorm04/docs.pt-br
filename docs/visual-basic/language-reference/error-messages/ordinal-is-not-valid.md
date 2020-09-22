---
title: O ordinal não é válido
ms.date: 07/20/2015
f1_keywords:
- vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
ms.openlocfilehash: 64f56b2ecace0ceafb310a175ea605e6959b7256
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871385"
---
# <a name="ordinal-is-not-valid"></a><span data-ttu-id="e26cc-102">O ordinal não é válido</span><span class="sxs-lookup"><span data-stu-id="e26cc-102">Ordinal is not valid</span></span>

<span data-ttu-id="e26cc-103">Sua chamada para uma DLL (biblioteca de vínculo dinâmico) indicou usar um número em vez de um nome de procedimento, usando a `#num` sintaxe.</span><span class="sxs-lookup"><span data-stu-id="e26cc-103">Your call to a dynamic-link library (DLL) indicated to use a number instead of a procedure name, using the `#num` syntax.</span></span> <span data-ttu-id="e26cc-104">Esse erro tem as seguintes causas possíveis:</span><span class="sxs-lookup"><span data-stu-id="e26cc-104">This error has the following possible causes:</span></span>  
  
- <span data-ttu-id="e26cc-105">Falha ao tentar converter a `#num` expressão em um ordinal.</span><span class="sxs-lookup"><span data-stu-id="e26cc-105">An attempt to convert the `#num` expression to an ordinal failed.</span></span>  
  
- <span data-ttu-id="e26cc-106">O `#num` especificado não especifica nenhuma função na dll.</span><span class="sxs-lookup"><span data-stu-id="e26cc-106">The `#num` specified does not specify any function in the DLL.</span></span>  
  
- <span data-ttu-id="e26cc-107">Uma biblioteca de tipos tem uma declaração inválida que resulta em uso interno de um número ordinal inválido.</span><span class="sxs-lookup"><span data-stu-id="e26cc-107">A type library has an invalid declaration resulting in internal use of an invalid ordinal number.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e26cc-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="e26cc-108">To correct this error</span></span>  
  
1. <span data-ttu-id="e26cc-109">Verifique se a expressão representa um número válido ou chame o procedimento por nome.</span><span class="sxs-lookup"><span data-stu-id="e26cc-109">Make sure the expression represents a valid number, or call the procedure by name.</span></span>  
  
2. <span data-ttu-id="e26cc-110">Certifique-se de que `#num` identifica uma função válida na dll.</span><span class="sxs-lookup"><span data-stu-id="e26cc-110">Make sure `#num` identifies a valid function in the DLL.</span></span>  
  
3. <span data-ttu-id="e26cc-111">Isole a chamada de procedimento que está causando o problema comentando o código.</span><span class="sxs-lookup"><span data-stu-id="e26cc-111">Isolate the procedure call causing the problem by commenting out the code.</span></span> <span data-ttu-id="e26cc-112">Escreva uma `Declare` instrução para o procedimento e relate o problema ao fornecedor da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="e26cc-112">Write a `Declare` statement for the procedure, and report the problem to the type library vendor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e26cc-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="e26cc-113">See also</span></span>

- [<span data-ttu-id="e26cc-114">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="e26cc-114">Declare Statement</span></span>](../statements/declare-statement.md)
