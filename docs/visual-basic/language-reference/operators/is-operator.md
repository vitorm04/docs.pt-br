---
title: "Operador Is (Visual Basic) | Microsoft Docs"
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
  - "vb.is"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "operadores de comparação"
  - "objetos equivalentes"
  - "Operador Is [Visual Basic]"
  - "expressão TypeOf...Is"
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operador Is (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Compara duas variáveis de referência a objeto.  
  
## Sintaxe  
  
```  
  
result = object1 Is object2  
```  
  
## Partes  
 `result`  
 Obrigatório.  Qualquer valor `Boolean`.  
  
 `object1`  
 Obrigatório.  Qualquer nome `Object`.  
  
 `object2`  
 Obrigatório.  Qualquer nome `Object`.  
  
## Comentários  
 O operador `Is` determina se duas referências de objeto referem\-se ao mesmo objeto.  Entretanto, não realiza comparações de valor.  Se ambos `object1`e `object2` referem\-se à mesma instância de objeto, `result` tem valor `True`; se eles não se referem, `result` tem valor `False`.  
  
 `Is` também pode ser usado com a palavra\-chave `TypeOf` para criar uma expressão `TypeOf`...`Is`, a qual testa se uma variável de objeto é compatível com um tipo de dados.  
  
> [!NOTE]
>  O `Is` palavra\-chave também é usada a [Instrução Select...Case](../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## Exemplo  
 O exemplo a seguir utiliza o operador `Is` para comparar pares de referências de objetos.  Os resultados são designados a um valor `Boolean` representando se os dois objetos são idênticos.  
  
 [!CODE [VbVbalrOperators#27](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#27)]  
  
 Como o exemplo anterior demonstra, você pode usar o operador `Is` para testar tanto objetos ligados cedo quanto ligados tarde.  
  
## Consulte também  
 [Operador TypeOf](../../../visual-basic/language-reference/operators/typeof-operator.md)   
 [Operador IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md)   
 [Operadores de comparação no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Operadores e expressões](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)