---
title: "N&#227;o foi poss&#237;vel inferir argumentos de tipo a partir do delegado | Microsoft Docs"
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
  - "bc36564"
  - "vbc36564"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC36564"
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# N&#227;o foi poss&#237;vel inferir argumentos de tipo a partir do delegado
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma declaração de atribuição usa `AddressOf` para atribuir o endereço de um procedimento genérico para um delegado , mas não fornece nenhum argumento de tipo para o procedimento genérico.  
  
 Normalmente, quando você invoca um tipo genérico, você fornece um argumento de tipo para cada parâmetro de tipo que o tipo genérico define.  Se você não fornecer nenhum argumento de tipo, o compilador tenta inferir os tipos a serem passados para os parâmetros de tipo.  Se o contexto não fornece informação suficiente para o compilador inferir os tipos, um erro é gerado.  
  
 **Identificação do erro:**  BC36564  
  
### Para corrigir este erro  
  
-   Na expressão `AddressOf`, especifique os argumentos de tipo para o procedimento genérico.  
  
## Consulte também  
 [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Operador AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Procedimentos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)   
 [Lista de tipos](../../../visual-basic/language-reference/statements/type-list.md)   
 [Métodos de extensão](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)