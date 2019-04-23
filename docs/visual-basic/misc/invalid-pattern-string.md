---
title: Cadeia de caracteres padrão inválida
ms.date: 07/20/2015
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
ms.openlocfilehash: 7390b9b32eea248969813b52f8d9799798718de0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59298676"
---
# <a name="invalid-pattern-string"></a>Cadeia de caracteres padrão inválida
A cadeia de caracteres padrão especificada no `Like` operação de uma pesquisa é inválida.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Examine os caracteres válidos para expressões da lista.  
  
2. No intervalo padrão, certifique-se de que o caractere de intervalo de início é menor que o caractere de intervalo de término, como em `[a-z]`.  
  
3. No intervalo padrão, certifique-se de que não haja várias hifens próximos uns dos outros, como em `[a--z]`.  
  
4. Intervalos de padrão de término com um colchete de fechamento.  
  
## <a name="see-also"></a>Consulte também

- [Operador Like](../../visual-basic/language-reference/operators/like-operator.md)
