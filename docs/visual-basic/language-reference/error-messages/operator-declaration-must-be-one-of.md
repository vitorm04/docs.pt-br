---
title: "A declara&#231;&#227;o do operador deve ser um de: +,-,*,\,/,^, &amp;, Like, Mod, And, Or, Xor, Not, &lt;&lt;, &gt;&gt;, =, &lt;&gt;, &lt;, &lt;=, &gt;, &gt;=, CType, IsTrue, IsFalse | Microsoft Docs"
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
  - "bc33000"
  - "vbc33000"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC33000"
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A declara&#231;&#227;o do operador deve ser um de: +,-,*,\,/,^, &amp;, Like, Mod, And, Or, Xor, Not, &lt;&lt;, &gt;&gt;, =, &lt;&gt;, &lt;, &lt;=, &gt;, &gt;=, CType, IsTrue, IsFalse
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Você pode declarar somente um operador que está qualificado para a sobrecarga.  A tabela a seguir lista os operadores que você pode declarar.  
  
|Tipo|Operadores|  
|----------|----------------|  
|Unário|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|  
|Binário|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|  
|Conversão \(Unário\)|`CType`|  
  
 Observe que o operador `=` na lista binária é o operador de comparação, não o operador de atribuição.  
  
 **Identificação do erro:**  BC33000  
  
### Para corrigir este erro  
  
1.  Selecione um operador do conjunto de operadores sobrecarregáveis.  
  
2.  Se você precisar da funcionalidade de sobrecarregar um operador que você não pode sobrecarregar diretamente, crie um procedimento `Function` que recebe os parâmetros apropriados e retorna o valor apropriado.  
  
## Consulte também  
 [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Procedimentos do operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Como definir um operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Como definir um operador de conversão](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)   
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)