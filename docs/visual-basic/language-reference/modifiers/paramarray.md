---
title: "ParamArray (Visual Basic) | Microsoft Docs"
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
  - "vb.ParamArray"
  - "ParamArray"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Palavra-chave ParamArray"
  - "Palavra-chave ParamArray, sintaxe"
ms.assetid: a5f18789-92bd-488f-9c7e-cf3719963635
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ParamArray (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica que um parâmetro de procedimento usa uma matriz opcional de elementos do tipo especificado.  `ParamArray`pode ser usado somente no último parâmetro de uma lista de parâmetros.  
  
## Comentários  
 `ParamArray` permite que você passe um número arbitrário de argumentos para o procedimento.  Um parâmetro `ParamArray` sempre é declarado usando [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).  
  
 Você pode fornecer um ou mais argumentos para um parâmetro `ParamArray` ao passar uma matriz do tipo de dados apropriado, uma lista de valores, separada por vírgulas ou nada.  Para obter detalhes, consulte " Chamada de ParamArray " no [Matrizes de parâmetros](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).  
  
> [!IMPORTANT]
>  Sempre que você lidar com uma matriz que pode ser indefinidamente grande, há um risco de ultrapassar alguma capacidade interna da sua aplicação.  Se você aceitar uma matriz de parâmtros do modo de chamada, você deve testar seu tamanho e tomar passos apropriados se ele é muito grande para sua aplicação.  
  
 O modificador `ParamArray` pode ser utilizado nestes contextos:  
  
 [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## Consulte também  
 [Palavras\-chave](../../../visual-basic/language-reference/keywords/index.md)   
 [Matrizes de parâmetros](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)