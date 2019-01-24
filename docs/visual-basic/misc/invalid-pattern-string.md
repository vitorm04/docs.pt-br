---
title: Cadeia de caracteres padrão inválida
ms.date: 07/20/2015
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
ms.openlocfilehash: 3fa42632ad6d69642d7b8ec36bf2880bc10a5024
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732473"
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
