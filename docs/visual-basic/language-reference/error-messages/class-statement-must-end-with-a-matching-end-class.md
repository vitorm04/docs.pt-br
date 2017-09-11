---
title: "Instrução &quot;Class&quot; deve finalizar com &quot;End Class&quot; correspondente | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30481
- bc30481
dev_langs:
- VB
helpviewer_keywords:
- BC30481
ms.assetid: 583f3029-bc3a-4e06-866f-92dbecc46f19
caps.latest.revision: 9
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
ms.openlocfilehash: f47993e4bb3979b2920f4444e3a3ac60278712f3
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="39class39-statement-must-end-with-a-matching-39end-class39"></a><span data-ttu-id="ea5c8-102">Instrução 'Class' deve finalizar com 'End Class' correspondente</span><span class="sxs-lookup"><span data-stu-id="ea5c8-102">&#39;Class&#39; statement must end with a matching &#39;End Class&#39;</span></span>
<span data-ttu-id="ea5c8-103">`Class`é usado para iniciar um `Class` bloco; portanto, ele só pode aparecer no início do bloco, com uma correspondência `End Class` terminando o bloco de instrução.</span><span class="sxs-lookup"><span data-stu-id="ea5c8-103">`Class` is used to initiate a `Class` block; hence it can only appear at the beginning of the block, with a matching `End Class` statement ending the block.</span></span> <span data-ttu-id="ea5c8-104">Ou você tem um redundantes `Class` instrução, ou você não encerrou o `Class` bloco com `End Class`.</span><span class="sxs-lookup"><span data-stu-id="ea5c8-104">Either you have a redundant `Class` statement, or you have not ended your `Class` block with `End Class`.</span></span>  
  
 <span data-ttu-id="ea5c8-105">**ID do erro:** BC30481</span><span class="sxs-lookup"><span data-stu-id="ea5c8-105">**Error ID:** BC30481</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ea5c8-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="ea5c8-106">To correct this error</span></span>  
  
-   <span data-ttu-id="ea5c8-107">Localize e remova os desnecessários `Class` instrução.</span><span class="sxs-lookup"><span data-stu-id="ea5c8-107">Locate and remove the unnecessary `Class` statement.</span></span>  
  
-   <span data-ttu-id="ea5c8-108">Conclua o `Class` bloco com uma correspondência `End Class`.</span><span class="sxs-lookup"><span data-stu-id="ea5c8-108">Conclude the `Class` block with a matching `End Class`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea5c8-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ea5c8-109">See Also</span></span>  
 <span data-ttu-id="ea5c8-110">[End \<palavra-chave > instrução](../../../visual-basic/language-reference/statements/end-keyword-statement.md) </span><span class="sxs-lookup"><span data-stu-id="ea5c8-110">[End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) </span></span>  
<span data-ttu-id="ea5c8-111"> [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)</span><span class="sxs-lookup"><span data-stu-id="ea5c8-111"> [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md)</span></span>
