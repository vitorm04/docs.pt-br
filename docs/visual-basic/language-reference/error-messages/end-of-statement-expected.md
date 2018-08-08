---
title: Fim de instrução esperado
ms.date: 07/20/2015
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords:
- BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
ms.openlocfilehash: 7b91d13cbcb9d211d4ca18c8e48c7494bf6eccc6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588074"
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
