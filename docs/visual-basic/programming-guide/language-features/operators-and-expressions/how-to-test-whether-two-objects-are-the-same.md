---
title: "Como testar se dois objetos s&#227;o iguais (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Operador Is [Visual Basic], comparando objetos"
  - "objetos [Visual Basic], variáveis referentes ao mesmo"
  - "variáveis de referência"
  - "variáveis [Visual Basic], referência"
  - "variáveis [Visual Basic], referindo-se ao mesmo objeto"
  - "código do Visual Basic, operadores"
ms.assetid: f760e828-8704-4256-bc2d-c22a4c93b524
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como testar se dois objetos s&#227;o iguais (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Se você tiver duas variáveis que se referem a objetos, você pode usar tanto o `Is` ou `IsNot` operador, ou ambas, para determinar se eles se referem à mesma instância.  
  
### Para testar se os dois objetos são iguais  
  
-   Use o [Operador Is](../../../../visual-basic/language-reference/operators/is-operator.md) ou o [Operador IsNot](../../../../visual-basic/language-reference/operators/isnot-operator.md) com as duas variáveis como operandos.  
  
     [!CODE [VbVbalrOperators#69](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#69)]  
  
 Você talvez queira levar a uma determinada ação, dependendo se dois objetos se referir à mesma instância.  O exemplo anterior compara o controle `c` contra o controle ativo no formulário `f`.  Se não há nenhum controle ativo, ou se houver um, mas não é a mesma instância do controle como `c`, em seguida, a `If` falha de declaração e o procedimento retorna sem processamento adicional.  
  
 Se você usa `Is` ou `IsNot` é uma questão de conveniência pessoal para você.  Um pode ser mais fácil de ler que o outro em uma determinada expressão.  
  
## Consulte também  
 [Operadores de comparação no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)