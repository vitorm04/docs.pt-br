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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58825437"
---
# <a name="module-statements-can-occur-only-at-file-or-namespace-level"></a>Instruções 'Module' só podem ocorrer no nível de namespace ou arquivo
`Module` as instruções devem aparecer na parte superior do seu arquivo de origem imediatamente após `Option` e `Imports` instruções, atributos globais e declarações de namespace, mas antes de todas as outras declarações.  
  
 **ID do erro:** BC30617  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Mover o `Module` instrução na parte superior do seu arquivo de origem ou de declaração de namespace.  
  
## <a name="see-also"></a>Consulte também

- [Instrução Module](../../../visual-basic/language-reference/statements/module-statement.md)
