---
title: "Instruções &quot;Module&quot; só podem ocorrer no nível de namespace ou arquivo | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30617
- vbc30617
dev_langs:
- VB
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
caps.latest.revision: 8
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
ms.openlocfilehash: d9942093b70cecc606c6fbae5ae0f590754ae6ae
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="39module39-statements-can-occur-only-at-file-or-namespace-level"></a><span data-ttu-id="d1168-102">Instruções 'Module' só podem ocorrer no nível de namespace ou arquivo</span><span class="sxs-lookup"><span data-stu-id="d1168-102">&#39;Module&#39; statements can occur only at file or namespace level</span></span>
<span data-ttu-id="d1168-103">`Module`instruções devem aparecer na parte superior do seu arquivo de origem imediatamente após `Option` e `Imports` instruções, atributos globais e declarações de namespace, mas antes de todas as outras declarações.</span><span class="sxs-lookup"><span data-stu-id="d1168-103">`Module` statements must appear at the top of your source file immediately after `Option` and `Imports` statements, global attributes, and namespace declarations, but before all other declarations.</span></span>  
  
 <span data-ttu-id="d1168-104">**ID do erro:** BC30617</span><span class="sxs-lookup"><span data-stu-id="d1168-104">**Error ID:** BC30617</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d1168-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="d1168-105">To correct this error</span></span>  
  
-   <span data-ttu-id="d1168-106">Mova o `Module` instrução na parte superior do seu arquivo de origem ou de declaração namespace.</span><span class="sxs-lookup"><span data-stu-id="d1168-106">Move the `Module` statement to the top of your namespace declaration or source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1168-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d1168-107">See Also</span></span>  
 [<span data-ttu-id="d1168-108">Instrução Module</span><span class="sxs-lookup"><span data-stu-id="d1168-108">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
