---
title: "Como manter mais de um valor em uma vari&#225;vel (Visual Basic) | Microsoft Docs"
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
  - "matrizes [Visual Basic], erros de compilação"
  - "matrizes [Visual Basic], tipos de dados compostos"
  - "classes [Visual Basic], tipos de dados compostos"
  - "tipos de dados compostos"
  - "tipos compostos"
  - "tipos de dados [Visual Basic], composição"
  - "estruturas, tipos de dados compostos"
  - "tipos [Visual Basic], composição"
ms.assetid: 5fe0e558-aac2-4a40-b7f2-7cfea7336917
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como manter mais de um valor em uma vari&#225;vel (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Uma variável contém mais de um valor se você declará\-la para ser de um  *tipo de dados composto* .  
  
 [Tipos de dados compostos](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) incluem estruturas, arrays e classes.  Uma variável de um tipo de dados composto pode conter uma combinação de tipos de dados elementares e outros tipos compostos.  Estruturas e classes podem armazenar código bem como dados.  
  
### Manter mais de um valor em uma variável  
  
1.  Determine quais tipos de dados compostos você deseja usar para sua variável.  
  
2.  Se ainda não estiver definido o tipo de dados composto, defina\-o para que sua variável possa usá\-lo.  
  
    -   Defina uma estrutura com uma [Instrução Structure](../../../../visual-basic/language-reference/statements/structure-statement.md).  
  
    -   Defina um array com uma [Instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).  
  
    -   Defina uma classe com uma [Instrução Class](../../../../visual-basic/language-reference/statements/class-statement.md).  
  
3.  Declare a variável com uma declaração `Dim`.  
  
4.  Coloque a cláusula `As` após o nome da variável.  
  
5.  Após a palavra\-chave `As`,  coloque o nome do tipo de dados compostos apropriado.  
  
## Consulte também  
 [Tipos de dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Caracteres de tipo](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)   
 [Tipos de dados compostos](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)   
 [Estruturas](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [Objetos e classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [Tipos de valor e referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)