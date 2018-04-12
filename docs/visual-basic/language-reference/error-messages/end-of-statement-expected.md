---
title: Fim de instrução esperado
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords:
- BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4934952015cb4871bcd90cef982eab5425b1617f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="end-of-statement-expected"></a>Fim de instrução esperado
A instrução está sintaticamente completa, mas um elemento de programação adicional vem depois do elemento que conclui a declaração. Um terminador de linha é necessário no final de cada instrução.
  
 Um terminador de linha divide os caracteres de um arquivo de origem do Visual Basic em linhas. Exemplos de terminadores de linha são o Unicode carro retorno caractere (& HD), o Unicode avanço de linha caractere (& HA), e o Unicode retorno de carro seguido pelo caractere de avanço de linha Unicode do caractere. Para obter mais informações sobre os terminadores de linha, consulte o [especificação da linguagem Visual Basic](../../../visual-basic/reference/language-specification/index.md).
  
 **ID do erro:** BC30205
  
## <a name="to-correct-this-error"></a>Para corrigir este erro
  
1.  Verifique se duas declarações diferentes foram inadvertidamente colocadas na mesma linha.
  
2.  Insira um terminador de linha após o elemento que conclui a declaração.
  
## <a name="see-also"></a>Consulte também  
 [Como quebrar e combinar instruções no código](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)
