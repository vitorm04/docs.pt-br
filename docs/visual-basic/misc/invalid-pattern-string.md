---
title: Cadeia de caracteres de padrão inválida
ms.date: 07/20/2015
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
ms.openlocfilehash: 5ef12ac27e96205f9ef1c964293847f56b11cb78
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91090684"
---
# <a name="invalid-pattern-string"></a>Cadeia de caracteres de padrão inválida

A cadeia de caracteres de padrão especificada na `Like` operação de uma pesquisa é inválida.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Examine os caracteres válidos para expressões de lista.  
  
2. No intervalo de padrões, verifique se o caractere de intervalo inicial é menor que o caractere de intervalo final, como em `[a-z]` .  
  
3. No intervalo de padrões, verifique se não há vários hifens próximos um do outro, como em `[a--z]` .  
  
4. Intervalos de padrão de término com um colchete de fechamento.  
  
## <a name="see-also"></a>Confira também

- [Operador Like](../language-reference/operators/like-operator.md)
