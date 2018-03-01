---
title: "Não foi possível concluir a operação porque o diretório de destino está no diretório de origem"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0a17877b2335ee010a97f0b522bd4c399867cd7d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a>Não foi possível concluir a operação porque o diretório de destino está no diretório de origem
Uma operação cíclica falhou. Ciclo de operações cíclicas e, portanto, não é possível concluir. Por exemplo, o objeto A pode tentar herdar do objeto B, que por sua vez, herda do objeto A.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Ao herdar, certifique-se de que não há nenhuma referência cíclica.  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de Erro](../../visual-basic/programming-guide/language-features/error-types.md)  
 [Noções básicas de depuração: pontos de interrupção](http://msdn.microsoft.com/library/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e)
