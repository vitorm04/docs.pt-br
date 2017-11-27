---
title: "Cadeia de caracteres de padrão inválido"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f824a5844d6d2b365358030119826266a4b42ef3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
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
