---
title: "'<keyword>' só é valido dentro de um método de instância"
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: 8ec1e704815ee10cb98d8cc20fb5982ee4b92832
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662006"
---
# <a name="keyword-is-valid-only-within-an-instance-method"></a><span data-ttu-id="ce20c-102">'\<palavra-chave >' é válido somente dentro de um método de instância</span><span class="sxs-lookup"><span data-stu-id="ce20c-102">'\<keyword>' is valid only within an instance method</span></span>
<span data-ttu-id="ce20c-103">O `Me`, `MyClass`, e `MyBase` palavras-chave se referem a instâncias de classe específica.</span><span class="sxs-lookup"><span data-stu-id="ce20c-103">The `Me`, `MyClass`, and `MyBase` keywords refer to specific class instances.</span></span> <span data-ttu-id="ce20c-104">Você não pode usá-los dentro de um compartilhamento `Function` ou `Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="ce20c-104">You cannot use them inside a shared `Function` or `Sub` procedure.</span></span>  
  
 <span data-ttu-id="ce20c-105">**ID do erro:** BC30043</span><span class="sxs-lookup"><span data-stu-id="ce20c-105">**Error ID:** BC30043</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ce20c-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="ce20c-106">To correct this error</span></span>  
  
- <span data-ttu-id="ce20c-107">Remova a palavra-chave do procedimento, ou remova o `Shared` palavra-chave da declaração de procedimento.</span><span class="sxs-lookup"><span data-stu-id="ce20c-107">Remove the keyword from the procedure, or remove the `Shared` keyword from the procedure declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce20c-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ce20c-108">See also</span></span>

- [<span data-ttu-id="ce20c-109">Atribuição de variável do objeto</span><span class="sxs-lookup"><span data-stu-id="ce20c-109">Object Variable Assignment</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="ce20c-110">Me, My, MyBase e MyClass</span><span class="sxs-lookup"><span data-stu-id="ce20c-110">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="ce20c-111">Noções Básicas de Herança</span><span class="sxs-lookup"><span data-stu-id="ce20c-111">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
