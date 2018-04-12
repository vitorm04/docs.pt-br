---
title: '&#39; &lt;palavra-chave&gt;&#39; é válido somente dentro de um método de instância'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a61314c036cec0fd1412a9c844a610fbd1401add
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="39ltkeywordgt39-is-valid-only-within-an-instance-method"></a><span data-ttu-id="b5c3e-102">&#39; &lt;palavra-chave&gt;&#39; é válido somente dentro de um método de instância</span><span class="sxs-lookup"><span data-stu-id="b5c3e-102">&#39;&lt;keyword&gt;&#39; is valid only within an instance method</span></span>
<span data-ttu-id="b5c3e-103">O `Me`, `MyClass`, e `MyBase` palavras-chave se referem a instâncias de classe específica.</span><span class="sxs-lookup"><span data-stu-id="b5c3e-103">The `Me`, `MyClass`, and `MyBase` keywords refer to specific class instances.</span></span> <span data-ttu-id="b5c3e-104">Você não pode usá-las dentro de um compartilhado `Function` ou `Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="b5c3e-104">You cannot use them inside a shared `Function` or `Sub` procedure.</span></span>  
  
 <span data-ttu-id="b5c3e-105">**ID do erro:** BC30043</span><span class="sxs-lookup"><span data-stu-id="b5c3e-105">**Error ID:** BC30043</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b5c3e-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="b5c3e-106">To correct this error</span></span>  
  
-   <span data-ttu-id="b5c3e-107">Remova a palavra-chave do procedimento, ou remova o `Shared` palavra-chave da declaração de procedimento.</span><span class="sxs-lookup"><span data-stu-id="b5c3e-107">Remove the keyword from the procedure, or remove the `Shared` keyword from the procedure declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5c3e-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b5c3e-108">See Also</span></span>  
 [<span data-ttu-id="b5c3e-109">Atribuição de variável do objeto</span><span class="sxs-lookup"><span data-stu-id="b5c3e-109">Object Variable Assignment</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [<span data-ttu-id="b5c3e-110">Me, My, MyBase e MyClass</span><span class="sxs-lookup"><span data-stu-id="b5c3e-110">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [<span data-ttu-id="b5c3e-111">Noções Básicas de Herança</span><span class="sxs-lookup"><span data-stu-id="b5c3e-111">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
