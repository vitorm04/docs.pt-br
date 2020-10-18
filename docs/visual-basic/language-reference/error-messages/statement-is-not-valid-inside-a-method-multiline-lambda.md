---
title: A instrução não é válida dentro de um método/lambda de várias linhas
ms.date: 07/20/2015
f1_keywords:
- vbc30024
- bc30024
helpviewer_keywords:
- BC30024
ms.assetid: 758e7a8f-429b-42c1-9a78-778e5b480e04
ms.openlocfilehash: cef992c3eaa2b82bbf5e8993f9fccd64ae388c95
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159671"
---
# <a name="bc30024-statement-is-not-valid-inside-a-methodmultiline-lambda"></a><span data-ttu-id="95790-102">BC30024: a instrução não é válida dentro de um método/lambda de várias linhas</span><span class="sxs-lookup"><span data-stu-id="95790-102">BC30024: Statement is not valid inside a method/multiline lambda</span></span>

<span data-ttu-id="95790-103">A instrução não é válida dentro de `Sub` um `Function` procedimento,, propriedade `Get` ou propriedade `Set` .</span><span class="sxs-lookup"><span data-stu-id="95790-103">The statement is not valid within a `Sub`, `Function`, property `Get`, or property `Set` procedure.</span></span> <span data-ttu-id="95790-104">Algumas instruções podem ser colocadas no nível do módulo ou da classe.</span><span class="sxs-lookup"><span data-stu-id="95790-104">Some statements can be placed at the module or class level.</span></span> <span data-ttu-id="95790-105">Outros, como `Option Strict` , devem estar no nível de namespace e preceder todas as outras declarações.</span><span class="sxs-lookup"><span data-stu-id="95790-105">Others, such as `Option Strict`, must be at namespace level and precede all other declarations.</span></span>

 <span data-ttu-id="95790-106">**ID do erro:** BC30024</span><span class="sxs-lookup"><span data-stu-id="95790-106">**Error ID:** BC30024</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="95790-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="95790-107">To correct this error</span></span>

- <span data-ttu-id="95790-108">Remova a instrução do procedimento.</span><span class="sxs-lookup"><span data-stu-id="95790-108">Remove the statement from the procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="95790-109">Veja também</span><span class="sxs-lookup"><span data-stu-id="95790-109">See also</span></span>

- [<span data-ttu-id="95790-110">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="95790-110">Sub Statement</span></span>](../statements/sub-statement.md)
- [<span data-ttu-id="95790-111">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="95790-111">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="95790-112">Instrução Get</span><span class="sxs-lookup"><span data-stu-id="95790-112">Get Statement</span></span>](../statements/get-statement.md)
- [<span data-ttu-id="95790-113">Instrução SET</span><span class="sxs-lookup"><span data-stu-id="95790-113">Set Statement</span></span>](../statements/set-statement.md)
