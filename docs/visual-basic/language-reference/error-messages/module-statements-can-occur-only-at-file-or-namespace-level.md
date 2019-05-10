---
title: Instruções 'Module' só podem ocorrer no nível de namespace ou arquivo
ms.date: 07/20/2015
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
ms.openlocfilehash: fc3c102dbfe7c55e66093421bc11379d48ba000d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592091"
---
# <a name="module-statements-can-occur-only-at-file-or-namespace-level"></a><span data-ttu-id="00d62-102">Instruções 'Module' só podem ocorrer no nível de namespace ou arquivo</span><span class="sxs-lookup"><span data-stu-id="00d62-102">'Module' statements can occur only at file or namespace level</span></span>
<span data-ttu-id="00d62-103">`Module` as instruções devem aparecer na parte superior do seu arquivo de origem imediatamente após `Option` e `Imports` instruções, atributos globais e declarações de namespace, mas antes de todas as outras declarações.</span><span class="sxs-lookup"><span data-stu-id="00d62-103">`Module` statements must appear at the top of your source file immediately after `Option` and `Imports` statements, global attributes, and namespace declarations, but before all other declarations.</span></span>  
  
 <span data-ttu-id="00d62-104">**ID do erro:** BC30617</span><span class="sxs-lookup"><span data-stu-id="00d62-104">**Error ID:** BC30617</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="00d62-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="00d62-105">To correct this error</span></span>  
  
- <span data-ttu-id="00d62-106">Mover o `Module` instrução na parte superior do seu arquivo de origem ou de declaração de namespace.</span><span class="sxs-lookup"><span data-stu-id="00d62-106">Move the `Module` statement to the top of your namespace declaration or source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00d62-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="00d62-107">See also</span></span>

- [<span data-ttu-id="00d62-108">Instrução Module</span><span class="sxs-lookup"><span data-stu-id="00d62-108">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
