---
title: "'<methodname>' tem várias definições com assinaturas idênticas"
ms.date: 07/20/2015
f1_keywords:
- vbc30269
- bc30269
helpviewer_keywords:
- BC30269
ms.assetid: 39489621-6617-4e5c-9b24-c2faf8273891
ms.openlocfilehash: 2934a5666c55e1ca57b91ab86585261e6d71a2d3
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873735"
---
# <a name="methodname-has-multiple-definitions-with-identical-signatures"></a>'\<methodname>' tem várias definições com assinaturas idênticas

Uma `Function` `Sub` declaração de procedimento or usa o nome de procedimento idêntico e a lista de argumentos como uma declaração anterior. Uma causa possível é uma tentativa de sobrecarregar o procedimento original. Os procedimentos sobrecarregados devem ter diferentes listas de argumentos.  
  
 **ID do erro:** BC30269  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Altere o nome do procedimento ou a lista de argumentos ou remova a declaração duplicada.  
  
## <a name="see-also"></a>Confira também

- [Referências a elementos declarados](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Considerações sobre procedimentos de sobrecarga](../../programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)
