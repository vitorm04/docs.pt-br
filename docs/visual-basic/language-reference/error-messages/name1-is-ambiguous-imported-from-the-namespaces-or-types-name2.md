---
title: "'<name1>' é ambíguo, importado dos namespaces ou tipos '<name2>'"
ms.date: 07/20/2015
f1_keywords:
- vbc30561
- bc30561
helpviewer_keywords:
- BC30561
ms.assetid: 761091f7-1018-4299-b481-3966a4a2c126
ms.openlocfilehash: 73cc604f1e3a06687ca93779a01e698512be198b
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160178"
---
# <a name="bc30561-name1-is-ambiguous-imported-from-the-namespaces-or-types-name2"></a><span data-ttu-id="c17a5-102">BC30561: ' \<name1> ' é ambíguo, importado dos namespaces ou tipos ' \<name2> '</span><span class="sxs-lookup"><span data-stu-id="c17a5-102">BC30561: '\<name1>' is ambiguous, imported from the namespaces or types '\<name2>'</span></span>

<span data-ttu-id="c17a5-103">Você forneceu um nome ambíguo e, portanto, está em conflito com outro nome.</span><span class="sxs-lookup"><span data-stu-id="c17a5-103">You have provided a name that is ambiguous and therefore conflicts with another name.</span></span> <span data-ttu-id="c17a5-104">O compilador Visual Basic não tem nenhuma regra de resolução de conflitos; Você mesmo deve eliminar a ambiguidade dos nomes.</span><span class="sxs-lookup"><span data-stu-id="c17a5-104">The Visual Basic compiler does not have any conflict resolution rules; you must disambiguate names yourself.</span></span>

 <span data-ttu-id="c17a5-105">**ID do erro:** BC30561</span><span class="sxs-lookup"><span data-stu-id="c17a5-105">**Error ID:** BC30561</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="c17a5-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="c17a5-106">To correct this error</span></span>

- <span data-ttu-id="c17a5-107">Desfaça a ambiguidade do nome removendo importações de namespace.</span><span class="sxs-lookup"><span data-stu-id="c17a5-107">Disambiguate the name by removing namespace imports.</span></span>

- <span data-ttu-id="c17a5-108">Qualifique totalmente o nome.</span><span class="sxs-lookup"><span data-stu-id="c17a5-108">Fully qualify the name.</span></span>

## <a name="see-also"></a><span data-ttu-id="c17a5-109">Veja também</span><span class="sxs-lookup"><span data-stu-id="c17a5-109">See also</span></span>

- [<span data-ttu-id="c17a5-110">Instrução Imports (tipo e namespace .NET)</span><span class="sxs-lookup"><span data-stu-id="c17a5-110">Imports Statement (.NET Namespace and Type)</span></span>](../statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="c17a5-111">Namespaces no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c17a5-111">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="c17a5-112">Instrução Namespace</span><span class="sxs-lookup"><span data-stu-id="c17a5-112">Namespace Statement</span></span>](../statements/namespace-statement.md)
