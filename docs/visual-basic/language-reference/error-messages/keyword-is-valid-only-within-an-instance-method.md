---
title: "'<keyword>' só é valido dentro de um método de instância"
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: ad39ade294b362b20f2dfb93455445bf41d056cd
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163318"
---
# <a name="bc30043-keyword-is-valid-only-within-an-instance-method"></a><span data-ttu-id="6094f-102">BC30043: ' \<keyword> ' é válido somente dentro de um método de instância</span><span class="sxs-lookup"><span data-stu-id="6094f-102">BC30043: '\<keyword>' is valid only within an instance method</span></span>

<span data-ttu-id="6094f-103">As `Me` `MyClass` `MyBase` palavras-chave,, e se referem a instâncias de classe específicas.</span><span class="sxs-lookup"><span data-stu-id="6094f-103">The `Me`, `MyClass`, and `MyBase` keywords refer to specific class instances.</span></span> <span data-ttu-id="6094f-104">Você não pode usá-los dentro de um `Function` procedimento compartilhado ou `Sub` .</span><span class="sxs-lookup"><span data-stu-id="6094f-104">You cannot use them inside a shared `Function` or `Sub` procedure.</span></span>

<span data-ttu-id="6094f-105">*ID do erro:*\* BC30043</span><span class="sxs-lookup"><span data-stu-id="6094f-105">*Error ID:*\* BC30043</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="6094f-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="6094f-106">To correct this error</span></span>

- <span data-ttu-id="6094f-107">Remova a palavra-chave do procedimento ou remova a `Shared` palavra-chave da declaração do procedimento.</span><span class="sxs-lookup"><span data-stu-id="6094f-107">Remove the keyword from the procedure, or remove the `Shared` keyword from the procedure declaration.</span></span>

## <a name="see-also"></a><span data-ttu-id="6094f-108">Veja também</span><span class="sxs-lookup"><span data-stu-id="6094f-108">See also</span></span>

- [<span data-ttu-id="6094f-109">Atribuição de variável do objeto</span><span class="sxs-lookup"><span data-stu-id="6094f-109">Object Variable Assignment</span></span>](../../programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="6094f-110">Me, My, MyBase e MyClass</span><span class="sxs-lookup"><span data-stu-id="6094f-110">Me, My, MyBase, and MyClass</span></span>](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="6094f-111">Noções básicas de herança</span><span class="sxs-lookup"><span data-stu-id="6094f-111">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
