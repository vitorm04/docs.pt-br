---
title: '&#39;Módulo&#39; instruções só podem ocorrer no nível de namespace ou arquivo'
ms.date: 07/20/2015
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
ms.openlocfilehash: 53199c2d7081445dc5490d5c54c98f93ee7522eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593159"
---
# <a name="39module39-statements-can-occur-only-at-file-or-namespace-level"></a>&#39;Módulo&#39; instruções só podem ocorrer no nível de namespace ou arquivo
`Module` instruções devem aparecer na parte superior do seu arquivo de origem imediatamente após `Option` e `Imports` instruções, atributos globais e declarações de namespace, mas antes de todas as outras declarações.  
  
 **ID do erro:** BC30617  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Mover o `Module` à parte superior do seu arquivo de origem ou de declaração de namespace.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Module](../../../visual-basic/language-reference/statements/module-statement.md)
