---
title: "Estouro (erro de tempo de execu&#231;&#227;o do Visual Basic) | Microsoft Docs"
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
  - "vbrERRID_Overflow"
dev_langs: 
  - "VB"
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Estouro (erro de tempo de execu&#231;&#227;o do Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Um estouro resultados quando você tenta executar uma atribuição que ultrapasse os limites de destino da atribuição.  
  
### Para corrigir este erro  
  
1.  Certifique\-se de que os resultados do tipo de dados, cálculos e atribuições de conversões não são muito grande para ser representado dentro do intervalo permitido para esse tipo de valor de variáveis e atribuir o valor a uma variável de um tipo que podem conter um intervalo maior de valores, se necessário.  
  
2.  Certifique\-se de atribuições para propriedades ajustar o intervalo da propriedade para o qual são feitas.  
  
3.  Certifique\-se de que os números usados em cálculos que são forçados para números inteiros não tem resultados maiores do que números inteiros.  
  
## Consulte também  
 <xref:System.Int32.MaxValue?displayProperty=fullName>   
 <xref:System.Double.MaxValue?displayProperty=fullName>   
 [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Tipos de erro](../../../visual-basic/programming-guide/language-features/error-types.md)