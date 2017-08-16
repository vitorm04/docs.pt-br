---
title: "Cadeia de caracteres de padrão inválido | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 02105ef1da16b8a19a6c1234f78211597450588f
ms.lasthandoff: 03/13/2017

---
# <a name="invalid-pattern-string"></a>Cadeia de caracteres de padrão inválido
A cadeia de caracteres padrão especificada no `Like` operação de uma pesquisa é inválida.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Examine os caracteres válidos para expressões da lista.  
  
2.  O intervalo padrão, certifique-se de que o caractere de intervalo de início é menor que o caractere de intervalo de término, como em `[a-z]`.  
  
3.  O intervalo padrão, certifique-se de que não haja vários hifens próximos uns dos outros, como em `[a--z]`.  
  
4.  Finalizar intervalos padrão com um colchete de fechamento.  
  
## <a name="see-also"></a>Consulte também  
 [Operador Like](../../visual-basic/language-reference/operators/like-operator.md)
