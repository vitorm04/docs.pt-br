---
title: '&#39;&lt;MethodName&gt; &#39; tem várias definições com assinaturas idênticas'
ms.date: 07/20/2015
f1_keywords:
- vbc30269
- bc30269
helpviewer_keywords:
- BC30269
ms.assetid: 39489621-6617-4e5c-9b24-c2faf8273891
ms.openlocfilehash: 059d152cf9c3fae77ab53a4a9248b36d99614c8b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="39ltmethodnamegt39-has-multiple-definitions-with-identical-signatures"></a>&#39;&lt;MethodName&gt; &#39; tem várias definições com assinaturas idênticas
Um `Function` ou `Sub` declaração de procedimento usa a lista de nome e o argumento de procedimento idêntica de uma declaração anterior. Uma possível causa é uma tentativa para sobrecarregar o procedimento original. Procedimentos sobrecarregados devem ter listas diferentes de argumentos.  
  
 **ID do erro:** BC30269  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Alterar o nome do procedimento ou a lista de argumentos, ou remova a declaração duplicada.  
  
## <a name="see-also"></a>Consulte também  
 [Referências a Elementos Declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Considerações sobre Procedimentos de Sobrecarga](../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)
