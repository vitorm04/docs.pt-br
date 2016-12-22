---
title: "Operador IsNot (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.isnot"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Operador IsNot"
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operador IsNot (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Compara duas variáveis de referência a objeto.  
  
## Sintaxe  
  
```  
  
result = object1 IsNot object2  
```  
  
## Partes  
 `result`  
 Obrigatório.  Um valor `Boolean`.  
  
 `object1`  
 Obrigatório.  Qualquer variável `Object` ou expressão.  
  
 `object2`  
 Obrigatório.  Qualquer variável `Object` ou expressão.  
  
## Comentários  
 O operador `IsNot` determina se duas referências a objeto referem\-se a objetos diferentes.  Entretanto, não realiza comparações de valor.  Se ambos `object1`e `object2` referem\-se à mesma instância de objeto, `result` tem valor `False`; se eles não se referem, `result` tem valor `True`.  
  
 `IsNot`é o oposto do operador `Is`.  A vantagem de `IsNot` é fato de que você pode evitar sintaxes estranhas com `Not` e `Is` que podem ser difíceis de se ler.  
  
 Você pode utilizar os operadores `Is` e `IsNot` para testar objetos early\-bound e late\-bound.  
  
> [!NOTE]
>  O `IsNot` operador não pode ser usado para comparar expressões retornadas a partir do `TypeOf` operador.  Em vez disso, você deve usar o `Not` e `Is` operadores.  
  
## Exemplo  
 O exemplo seguinte de código usa tanto o operador `Is` quando o operador `IsNot` para realizar a mesma comparação.  
  
 [!CODE [VbVbalrOperators#29](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#29)]  
  
## Consulte também  
 [Operador Is](../../../visual-basic/language-reference/operators/is-operator.md)   
 [Operador TypeOf](../../../visual-basic/language-reference/operators/typeof-operator.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Como testar se dois objetos são iguais](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)