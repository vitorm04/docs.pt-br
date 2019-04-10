---
title: Fim de instrução esperado
ms.date: 07/20/2015
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords:
- BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
ms.openlocfilehash: 1ce5c793a09df34ac17e70e3253e98108bf76fb8
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59321466"
---
# <a name="end-of-statement-expected"></a>Fim de instrução esperado
A instrução está sintaticamente completa, mas um elemento de programação adicional após o elemento que conclui a declaração. Um terminador de linha é necessário no final de cada instrução.
  
 Um terminador de linha divide os caracteres de um arquivo de origem do Visual Basic em linhas. Exemplos de terminadores de linha são o Unicode carro retorno caractere (& HD), o Unicode avanço de linha caractere (& HA), e o Unicode retorno de carro seguido pelo caractere de avanço de linha Unicode do caractere. Para obter mais informações sobre os terminadores de linha, consulte o [especificação da linguagem Visual Basic](~/_vblang/spec/lexical-grammar.md#line-terminators).
  
 **ID do erro:** BC30205
  
## <a name="to-correct-this-error"></a>Para corrigir este erro
  
1. Verifique se as duas instruções diferentes inadvertidamente tem sido colocadas na mesma linha.
  
2. Insira um terminador de linha após o elemento que conclui a declaração.
  
## <a name="see-also"></a>Consulte também

- [Como: Quebrar e combinar instruções no código](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
- [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)
