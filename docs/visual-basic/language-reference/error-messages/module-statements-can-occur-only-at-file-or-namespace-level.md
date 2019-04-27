---
title: Instruções 'Module' só podem ocorrer no nível de namespace ou arquivo
ms.date: 07/20/2015
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
ms.openlocfilehash: bf0239422fb5a98e4670aea407f684753d3a7ea4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61920855"
---
# <a name="module-statements-can-occur-only-at-file-or-namespace-level"></a><span data-ttu-id="e9728-102">Instruções 'Module' só podem ocorrer no nível de namespace ou arquivo</span><span class="sxs-lookup"><span data-stu-id="e9728-102">'Module' statements can occur only at file or namespace level</span></span>
<span data-ttu-id="e9728-103">`Module` as instruções devem aparecer na parte superior do seu arquivo de origem imediatamente após `Option` e `Imports` instruções, atributos globais e declarações de namespace, mas antes de todas as outras declarações.</span><span class="sxs-lookup"><span data-stu-id="e9728-103">`Module` statements must appear at the top of your source file immediately after `Option` and `Imports` statements, global attributes, and namespace declarations, but before all other declarations.</span></span>  
  
 <span data-ttu-id="e9728-104">**ID do erro:** BC30617</span><span class="sxs-lookup"><span data-stu-id="e9728-104">**Error ID:** BC30617</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e9728-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="e9728-105">To correct this error</span></span>  
  
-   <span data-ttu-id="e9728-106">Mover o `Module` instrução na parte superior do seu arquivo de origem ou de declaração de namespace.</span><span class="sxs-lookup"><span data-stu-id="e9728-106">Move the `Module` statement to the top of your namespace declaration or source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9728-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e9728-107">See also</span></span>

- [<span data-ttu-id="e9728-108">Instrução Module</span><span class="sxs-lookup"><span data-stu-id="e9728-108">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
