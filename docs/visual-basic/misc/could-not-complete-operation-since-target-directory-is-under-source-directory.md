---
title: "Não foi possível concluir a operação pois o diretório de destino está sob o diretório de origem | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
caps.latest.revision: 10
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
ms.openlocfilehash: 27666d69cd60cb64edec329491408d0134fbfb89
ms.lasthandoff: 03/13/2017

---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a>Não foi possível concluir a operação pois o diretório de destino está sob o diretório de origem
Uma operação cíclica falhou. Ciclo de operações cíclicas e, portanto, não é possível concluir. Por exemplo, um objeto pode tentar herdar do objeto B, que por sua vez herda do objeto A.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Quando herdar, certifique-se de que não há nenhuma referência cíclica.  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de Erro](../../visual-basic/programming-guide/language-features/error-types.md)   
 [Noções básicas de depuração: pontos de interrupção](http://msdn.microsoft.com/en-us/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e)
