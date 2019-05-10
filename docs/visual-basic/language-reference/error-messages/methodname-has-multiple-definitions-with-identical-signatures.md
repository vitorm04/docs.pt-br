---
title: "'<methodname>' tem várias definições com assinaturas idênticas"
ms.date: 07/20/2015
f1_keywords:
- vbc30269
- bc30269
helpviewer_keywords:
- BC30269
ms.assetid: 39489621-6617-4e5c-9b24-c2faf8273891
ms.openlocfilehash: b884220053bbcec633c964a41892bc8df42f41c7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64602436"
---
# <a name="methodname-has-multiple-definitions-with-identical-signatures"></a>'\<methodname >' tem várias definições com assinaturas idênticas
Um `Function` ou `Sub` declaração de procedimento usa a lista de nome e o argumento de procedimento idêntica de uma declaração anterior. Uma possível causa é uma tentativa de sobrecarregar o procedimento original. Procedimentos sobrecarregados devem ter listas de argumentos diferentes.  
  
 **ID do erro:** BC30269  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Alterar o nome do procedimento ou a lista de argumentos, ou remova a declaração duplicada.  
  
## <a name="see-also"></a>Consulte também

- [Referências a Elementos Declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Considerações sobre Procedimentos de Sobrecarga](../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)
