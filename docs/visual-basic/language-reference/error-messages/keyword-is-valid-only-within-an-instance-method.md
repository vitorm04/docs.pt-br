---
title: '&#39;&lt;palavra-chave&gt; &#39; é válido somente dentro de um método de instância'
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: a464a059aa2d13e3472b9770960384b6be398092
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54595936"
---
# <a name="39ltkeywordgt39-is-valid-only-within-an-instance-method"></a><span data-ttu-id="c941e-102">&#39;&lt;palavra-chave&gt; &#39; é válido somente dentro de um método de instância</span><span class="sxs-lookup"><span data-stu-id="c941e-102">&#39;&lt;keyword&gt;&#39; is valid only within an instance method</span></span>
<span data-ttu-id="c941e-103">O `Me`, `MyClass`, e `MyBase` palavras-chave se referem a instâncias de classe específica.</span><span class="sxs-lookup"><span data-stu-id="c941e-103">The `Me`, `MyClass`, and `MyBase` keywords refer to specific class instances.</span></span> <span data-ttu-id="c941e-104">Você não pode usá-los dentro de um compartilhamento `Function` ou `Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="c941e-104">You cannot use them inside a shared `Function` or `Sub` procedure.</span></span>  
  
 <span data-ttu-id="c941e-105">**ID do erro:** BC30043</span><span class="sxs-lookup"><span data-stu-id="c941e-105">**Error ID:** BC30043</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c941e-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="c941e-106">To correct this error</span></span>  
  
-   <span data-ttu-id="c941e-107">Remova a palavra-chave do procedimento, ou remova o `Shared` palavra-chave da declaração de procedimento.</span><span class="sxs-lookup"><span data-stu-id="c941e-107">Remove the keyword from the procedure, or remove the `Shared` keyword from the procedure declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c941e-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c941e-108">See also</span></span>
- [<span data-ttu-id="c941e-109">Atribuição de variável do objeto</span><span class="sxs-lookup"><span data-stu-id="c941e-109">Object Variable Assignment</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="c941e-110">Me, My, MyBase e MyClass</span><span class="sxs-lookup"><span data-stu-id="c941e-110">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="c941e-111">Noções Básicas de Herança</span><span class="sxs-lookup"><span data-stu-id="c941e-111">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
