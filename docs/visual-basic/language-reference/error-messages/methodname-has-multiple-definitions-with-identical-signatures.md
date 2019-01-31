---
title: "'<methodname>' tem várias definições com assinaturas idênticas"
ms.date: 07/20/2015
f1_keywords:
- vbc30269
- bc30269
helpviewer_keywords:
- BC30269
ms.assetid: 39489621-6617-4e5c-9b24-c2faf8273891
ms.openlocfilehash: 97113227591c40f302d3d1a08a4248a8199817bc
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55285422"
---
# <a name="methodname-has-multiple-definitions-with-identical-signatures"></a>'\<methodname >' tem várias definições com assinaturas idênticas
Um `Function` ou `Sub` declaração de procedimento usa a lista de nome e o argumento de procedimento idêntica de uma declaração anterior. Uma possível causa é uma tentativa de sobrecarregar o procedimento original. Procedimentos sobrecarregados devem ter listas de argumentos diferentes.  
  
 **ID do erro:** BC30269  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Alterar o nome do procedimento ou a lista de argumentos, ou remova a declaração duplicada.  
  
## <a name="see-also"></a>Consulte também
- [Referências a Elementos Declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Considerações sobre Procedimentos de Sobrecarga](../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)
