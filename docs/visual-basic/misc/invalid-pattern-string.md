---
title: Cadeia de caracteres padrão inválida
ms.date: 07/20/2015
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
ms.openlocfilehash: bc2e91060ca1b0e21ea28b0f08febc3e0c54f4f1
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58027312"
---
# <a name="invalid-pattern-string"></a>Cadeia de caracteres padrão inválida
A cadeia de caracteres padrão especificada no `Like` operação de uma pesquisa é inválida.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Examine os caracteres válidos para expressões da lista.  
  
2.  No intervalo padrão, certifique-se de que o caractere de intervalo de início é menor que o caractere de intervalo de término, como em `[a-z]`.  
  
3.  No intervalo padrão, certifique-se de que não haja várias hifens próximos uns dos outros, como em `[a--z]`.  
  
4.  Intervalos de padrão de término com um colchete de fechamento.  
  
## <a name="see-also"></a>Consulte também

- [Operador Like](../../visual-basic/language-reference/operators/like-operator.md)
