---
title: Instruções 'Module' só podem ocorrer no nível de namespace ou arquivo
ms.date: 07/20/2015
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
ms.openlocfilehash: 0820763cce9cc27f9a379ed5e766e0691a75f36b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271259"
---
# <a name="module-statements-can-occur-only-at-file-or-namespace-level"></a>Instruções 'Module' só podem ocorrer no nível de namespace ou arquivo
`Module` as instruções devem aparecer na parte superior do seu arquivo de origem imediatamente após `Option` e `Imports` instruções, atributos globais e declarações de namespace, mas antes de todas as outras declarações.  
  
 **ID do erro:** BC30617  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Mover o `Module` instrução na parte superior do seu arquivo de origem ou de declaração de namespace.  
  
## <a name="see-also"></a>Consulte também
- [Instrução Module](../../../visual-basic/language-reference/statements/module-statement.md)
