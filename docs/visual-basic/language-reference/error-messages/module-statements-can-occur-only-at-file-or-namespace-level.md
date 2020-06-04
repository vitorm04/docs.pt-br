---
title: Instruções 'Module' só podem ocorrer no nível de namespace ou arquivo
ms.date: 07/20/2015
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
ms.openlocfilehash: d01c30571fc34e142300ac8706c56d5e99175fcf
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397201"
---
# <a name="module-statements-can-occur-only-at-file-or-namespace-level"></a><span data-ttu-id="fa29f-102">Instruções 'Module' só podem ocorrer no nível de namespace ou arquivo</span><span class="sxs-lookup"><span data-stu-id="fa29f-102">'Module' statements can occur only at file or namespace level</span></span>
<span data-ttu-id="fa29f-103">`Module`as instruções devem aparecer na parte superior do arquivo de origem imediatamente após `Option` e `Imports` instruções, atributos globais e declarações de namespace, mas antes de todas as outras declarações.</span><span class="sxs-lookup"><span data-stu-id="fa29f-103">`Module` statements must appear at the top of your source file immediately after `Option` and `Imports` statements, global attributes, and namespace declarations, but before all other declarations.</span></span>  
  
 <span data-ttu-id="fa29f-104">**ID do erro:** BC30617</span><span class="sxs-lookup"><span data-stu-id="fa29f-104">**Error ID:** BC30617</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fa29f-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="fa29f-105">To correct this error</span></span>  
  
- <span data-ttu-id="fa29f-106">Mova a `Module` instrução para a parte superior da sua declaração de namespace ou arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="fa29f-106">Move the `Module` statement to the top of your namespace declaration or source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa29f-107">Confira também</span><span class="sxs-lookup"><span data-stu-id="fa29f-107">See also</span></span>

- [<span data-ttu-id="fa29f-108">Instrução Module</span><span class="sxs-lookup"><span data-stu-id="fa29f-108">Module Statement</span></span>](../statements/module-statement.md)
