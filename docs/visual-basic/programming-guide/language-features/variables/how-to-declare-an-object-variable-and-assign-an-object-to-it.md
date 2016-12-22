---
title: "Como declarar uma vari&#225;vel de objeto e atribuir um objeto a ela no Visual Basic | Microsoft Docs"
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
  - "declarando variáveis de objeto"
  - "variáveis de objeto, declarando"
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como declarar uma vari&#225;vel de objeto e atribuir um objeto a ela no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Você declara uma variável de tipo [Tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md) especificando `As Object` numa [Instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).  Você atribui um objeto para tal variável colocando o objeto depois do sinal igual \(`=`\) numa instrução de atribuição ou cláusula de inicialização.  
  
## Exemplo  
 O exemplo a seguir declara uma variável `Object` e atribui a instância atual à mesma.  
  
```  
  
      Dim thisObject As Object  
thisObject = "This is an Object"  
```  
  
 Você pode combinar a declaração e atribuição inicializando a variável com parte de sua declaração.  O exemplo a seguir é equivalente ao exemplo anterior.  
  
```  
Dim thisObject As Object = "This is an Object"  
```  
  
## Compilando o código  
 Este exemplo requer:  
  
-   Uma referência ao namespace <xref:System>.  
  
-   Uma classe, estrutura ou o módulo no qual colocar a instrução `Dim`.  
  
-   Um procedimento no qual colocar a instrução de atribuição.  
  
## Consulte também  
 [Declaração de variável](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Declaração de variável do objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [Tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [Instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)   
 [Inferência de tipo local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)