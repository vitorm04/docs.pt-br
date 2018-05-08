---
title: Cadeia de caracteres de padrão inválido
ms.date: 07/20/2015
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
ms.openlocfilehash: 4905f74683989d8e1a2b041a8af4af4d7432ffab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="invalid-pattern-string"></a>Cadeia de caracteres de padrão inválido
A cadeia de caracteres padrão especificada no `Like` operação de uma pesquisa é inválida.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Examine os caracteres válidos para expressões da lista.  
  
2.  O intervalo padrão, certifique-se de que o caractere de intervalo de início é menor que o caractere de intervalo de término, como em `[a-z]`.  
  
3.  O intervalo padrão, certifique-se de que não haja vários hifens próximos um do outro, como em `[a--z]`.  
  
4.  Intervalos de padrão de término com um colchete de fechamento.  
  
## <a name="see-also"></a>Consulte também  
 [Operador Like](../../visual-basic/language-reference/operators/like-operator.md)
