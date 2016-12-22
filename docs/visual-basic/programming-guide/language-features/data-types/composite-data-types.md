---
title: "Tipos de dados compostos (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "matrizes [Visual Basic], tipos de dados compostos"
  - "classes [Visual Basic], tipos de dados compostos"
  - "classes [Visual Basic], tipos compostos"
  - "tipos de dados compostos"
  - "tipos compostos"
  - "tipos de dados [Visual Basic], composição"
  - "estruturas, tipos de dados compostos"
  - "tipos [Visual Basic], composição"
ms.assetid: 62970f2e-52c0-4369-8963-613820f1f434
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipos de dados compostos (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Além dos tipos de dados [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] elementares, você também pode montar itens de diferentes tipos para criar  *tipos de dados compostos*  como estruturas, arrays e classes.  Você pode criar tipos de dados compostos a partir de tipos elementares e de outros tipos compostos.  Por exemplo, você pode definir um array de elementos de estrutura, ou uma estrutura com arrays.  
  
## Tipos de dados  
 Um tipo composto é diferente do tipo de dados de qualquer um dos seus componentes.  Por exemplo, um array de elementos `Integer` não é do tipo de dados `Integer`.  
  
 Um tipo de dados array é normalmente representado usando o tipo do elemento, vírgulas e parênteses, conforme necessrio.  Por exemplo, um array unidimensional de elementos `String` é representado como `String()`,e um array bidimensional de elementos `Boolean` é representado como `Boolean(,)`.  
  
## Tipos de estrutura  
 Não há nenhum tipo de dados único contendo todas as estruturas.  Em vez disso, cada definição de uma estrutura representa um tipo de dados exclusivo, mesmo se duas estruturas definem elementos idênticos na mesma ordem.  No entanto, se você criar duas ou mais instâncias da mesma estrutura, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] considera que elas têm o mesmo tipo de dados.  
  
## Tipos de matriz  
 Não há nenhum tipo de dados único contendo todas os arrays.  O tipo de dados de uma determinada instância de um array é determinado pelo seguinte:  
  
-   O fato de ser um array  
  
-   A classificação \(número de dimensões\) do array.  
  
-   O tipo de elemento do array  
  
 Em particular, o comprimento de uma dada dimensão não é parte do tipo de dados da instância.  O exemplo a seguir ilustra isto:  
  
```  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 No exemplo anterior, as variáveis array `arrayA`e `arrayB` são consideradas como do mesmo tipo de dados — `Byte()` — mesmo que eles sejam inicializados para diferentes comprimentos.  As variáveis `arrayB` e `arrayC` não são do mesmo tipo porque seus elementos têm tipos diferentes.  As variáveis `arrayC` e `arrayD` não são do mesmo tipo porque suas classificações são diferentes.  As variáveis `arrayD` e `arrayE` têm o mesmo tipo — `Short(,)` — porque suas classificações e tipos de elemento são os mesmos, mesmo que `arrayD` ainda não esteja inicializado.  
  
 Para obter mais informações sobre arrays, consulte [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## Tipos de classes  
 Não há nenhum tipo de dados único contendo todas as classes.  Embora uma classe possa herdar de outra classe, cada uma é um tipo de dados separado.  Várias instâncias da mesma classe são do mesmo tipo de dados.  Se você atribuir uma variável de instância de classe a outra, não apenas elas têm o mesmo tipo de dados, mas também apontam para a mesma instância de classe na memória.  
  
 Para mais informações sobre classes, consulte [Objetos e classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## Consulte também  
 [Tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Tipos de dados elementares](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Tipos genéricos no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Tipos de valor e referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Estruturas](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Solucionando problemas de tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Como manter mais de um valor em uma variável](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)