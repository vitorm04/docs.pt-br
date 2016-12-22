---
title: "Par&#226;metros gen&#233;ricos usados como tipos de par&#226;metro opcionais devem ter a classe restrita | Microsoft Docs"
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
  - "vbc32124"
  - "bc32124"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32124"
ms.assetid: 55aa8b2a-9ce3-4620-a710-2f9b0feb6143
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Par&#226;metros gen&#233;ricos usados como tipos de par&#226;metro opcionais devem ter a classe restrita
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Um procedimento é declarado com um parâmetro opcional que usa um parâmetro de tipo que não é restrito para ser um tipo de referência.  
  
 Você sempre deve fornecer um valor padrão para cada parâmetro opcional.  Se o parâmetro é de um tipo de referência, o valor opcional deve ser `Nothing`, que é um valor válido para qualquer tipo de referência.  No entanto, se o parâmetro é de um tipo de valor, esse tipo deve ser um tipo de dados elementar predefinido pelo Visual Basic.  Isso acontece porque um tipo de valor composto, such as uma estrutura definida pelo usuário, não tem valor padrão válido.  
  
 Quando você usa um parâmetro de tipo para um parâmetro opcional, você deve garantir que se trata de uma tipo de referência para evitar a possibilidade de um tipo de valor com nenhum valor padrão válido.  Isso significa que você deve restringir o parâmetro de tipo com a palavra\-chave `Class` ou com o nome de uma classe específica.  
  
 **Identificação do erro:**  BC32124  
  
### Para corrigir este erro  
  
-   Restringir o parâmetro de tipo para aceitar apenas um tipo de referência, ou não usá\-lo para o parâmetro opcional.  
  
## Consulte também  
 [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Lista de tipos](../../../visual-basic/language-reference/statements/type-list.md)   
 [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)   
 [Parâmetros opcionais](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)   
 [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [nada](../../../visual-basic/language-reference/nothing.md)