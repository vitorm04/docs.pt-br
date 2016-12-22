---
title: "Instru&#231;&#227;o Erase (Visual Basic) | Microsoft Docs"
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
  - "vb.Erase"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "palavra-chave Erase"
  - "instrução Erase"
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o Erase (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Usado para liberar variáveis de matriz e desalocar a memória utilizada para seus elementos.  
  
## Sintaxe  
  
```  
Erase arraylist  
```  
  
## Partes  
 `arraylist`  
 Obrigatório.  Lista de variáveis de matriz a ser apagada.  Diversas variáveis são separadas por vírgulas.  
  
## Comentários  
 A instrução `Erase` pode ser exibido somente em nível de procedimento.  Isso significa que você pode liberar matrizes dentro de um procedimento mas não no nível de classe ou módulo.  
  
 A instrução `Erase` é equivalente ao atribuir `Nothing` a cada variável de matriz.  
  
## Exemplo  
 O exemplo a seguir utiliza a instrução `Erase` Para limpar duas matrizes e liberar seu memória \(elementos de armazenamento 1000 e 100, respectivamente\).  A instrução `ReDim` Em seguida, atribui uma nova instância de matriz à matriz tridimensional.  
  
 [!code-vb[VbVbalrStatements#19](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/erase-statement_1.vb)]  
  
## Consulte também  
 [nada](../../../visual-basic/language-reference/nothing.md)   
 [Instrução ReDim](../../../visual-basic/language-reference/statements/redim-statement.md)