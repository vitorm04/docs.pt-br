---
title: "&quot;&lt;palavra-chave&gt;&quot; só é válido em um método de instância | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30043
- vbc30043
dev_langs:
- VB
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 0c5fefff3a70350792eb1decc411c5405b10a998
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="39ltkeywordgt39-is-valid-only-within-an-instance-method"></a><span data-ttu-id="4b8bf-102">'&lt;palavra-chave&gt;' só é válido em um método de instância</span><span class="sxs-lookup"><span data-stu-id="4b8bf-102">&#39;&lt;keyword&gt;&#39; is valid only within an instance method</span></span>
<span data-ttu-id="4b8bf-103">O `Me`, `MyClass`, e `MyBase` palavras-chave se referem a instâncias de classe específica.</span><span class="sxs-lookup"><span data-stu-id="4b8bf-103">The `Me`, `MyClass`, and `MyBase` keywords refer to specific class instances.</span></span> <span data-ttu-id="4b8bf-104">Você não pode usá-las dentro de uma chave secreta `Function` ou `Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="4b8bf-104">You cannot use them inside a shared `Function` or `Sub` procedure.</span></span>  
  
 <span data-ttu-id="4b8bf-105">**ID do erro:** BC30043</span><span class="sxs-lookup"><span data-stu-id="4b8bf-105">**Error ID:** BC30043</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4b8bf-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="4b8bf-106">To correct this error</span></span>  
  
-   <span data-ttu-id="4b8bf-107">Remova a palavra-chave do procedimento, ou remova o `Shared` palavra-chave da declaração de procedimento.</span><span class="sxs-lookup"><span data-stu-id="4b8bf-107">Remove the keyword from the procedure, or remove the `Shared` keyword from the procedure declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b8bf-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4b8bf-108">See Also</span></span>  
 <span data-ttu-id="4b8bf-109">[Atribuição de variável de objeto](../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md) </span><span class="sxs-lookup"><span data-stu-id="4b8bf-109">[Object Variable Assignment](../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md) </span></span>  
<span data-ttu-id="4b8bf-110"> [Me, My, MyBase e MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md) </span><span class="sxs-lookup"><span data-stu-id="4b8bf-110"> [Me, My, MyBase, and MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md) </span></span>  
<span data-ttu-id="4b8bf-111"> [Noções Básicas de Herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)</span><span class="sxs-lookup"><span data-stu-id="4b8bf-111"> [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)</span></span>
