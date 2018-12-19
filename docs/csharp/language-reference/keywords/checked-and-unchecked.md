---
title: Contexto verificado e não verificado – Referência de C#
ms.custom: seodec18
ms.date: 05/15/2018
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: ba4ddd7fa87eb200de0de3aea6f0bc056a40f0e5
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235797"
---
# <a name="checked-and-unchecked-c-reference"></a>Contexto verificado e não verificado (Referência de C#)
Instruções C# podem ser executadas em contexto marcado ou desmarcado. Em um contexto marcado, o estouro aritmético gera uma exceção. Em um contexto não verificado, o estouro aritmético é ignorado, e o resultado é truncado descartando todos os bits de ordem superior que não se encaixam no tipo de destino.  
  
-   [verificado](checked.md) Especificar o contexto verificado.  
  
-   [não verificado](unchecked.md) Especificar o contexto não verificado.  
  
 As seguintes operações são afetadas pela verificação de estouro:  
  
-   Expressões que usam os seguintes operadores predefinidos em tipos integrais:  
  
     `++`, `--`, unário `-`, `+`, `-`, `*`, `/`  
  
-   Conversões numéricas explícitas entre tipos integrais ou de `float` ou `double` para um tipo integral.  
  
 Se nem `checked` ou `unchecked` for especificado, o contexto padrão de expressões de não constante (expressões que são avaliadas no tempo de execução) é definido pelo valor da opção do compilador [-checked](../compiler-options/checked-compiler-option.md). Por padrão, o valor dessa opção é removido e as operações aritméticas são executadas em um contexto não verificado.
 
 Para expressões de constante (expressões que podem ser totalmente avaliadas no tempo de compilação), o contexto padrão sempre é verificado. A menos que uma expressão de constante seja explicitamente colocada em um contexto não verificado, estouros que ocorrem durante a avaliação do tempo de compilação da expressão causam erros de tempo de compilação.
  
## <a name="see-also"></a>Consulte também  

- [Referência de C#](../index.md)  
- [Guia de Programação em C#](../../programming-guide/index.md)  
- [Palavras-chave do C#](index.md)  
- [Palavras-chave de instrução](statement-keywords.md)
