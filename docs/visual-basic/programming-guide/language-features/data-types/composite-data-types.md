---
title: Tipos de dados compostos (Visual Basic) | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types
- composite data types
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures, composite data types
- classes [Visual Basic], composite types
- types [Visual Basic], composite
ms.assetid: 62970f2e-52c0-4369-8963-613820f1f434
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d81b2c08155cb16754e780fdfb341b596322302d
ms.lasthandoff: 03/13/2017

---
# <a name="composite-data-types-visual-basic"></a>Tipos de dados compostos (Visual Basic)
Além dos tipos de dados elementares [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fontes, você também pode montar itens de diferentes tipos para criar *tipos de dados compostos* como classes, matrizes e estruturas. Você pode criar tipos de dados compostos de tipos elementares e de outros tipos compostos. Por exemplo, você pode definir uma matriz de elementos de estrutura, ou uma estrutura com membros da matriz.  
  
## <a name="data-types"></a>Tipos de Dados  
 Um tipo composto é diferente do tipo de dados de qualquer um de seus componentes. Por exemplo, uma matriz de `Integer` elementos não tem o `Integer` tipo de dados.  
  
 Um tipo de dados array é normalmente representado usando o tipo de elemento, parênteses e vírgulas conforme necessário. Por exemplo, uma matriz unidimensional de `String` elementos é representado como `String()`e uma matriz bidimensional de `Boolean` elementos é representado como `Boolean(,)`.  
  
## <a name="structure-types"></a>Tipos de estrutura  
 Não há nenhum tipo de dados único contendo todas as estruturas. Em vez disso, cada definição de uma estrutura representa um tipo de dados exclusivo, mesmo se duas estruturas definem elementos idênticos na mesma ordem. No entanto, se você criar duas ou mais instâncias da mesma estrutura, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] considera ser do mesmo tipo de dados.  
  
## <a name="array-types"></a>Tipos de matriz  
 Não há nenhum tipo de dados único contendo todas as matrizes. O tipo de dados de uma instância específica de uma matriz é determinado pelo seguinte:  
  
-   O fato de ser uma matriz  
  
-   A classificação (número de dimensões) da matriz  
  
-   O tipo de elemento da matriz  
  
 Em particular, o comprimento de uma determinada dimensão não é parte da instância tipo de dados. O exemplo a seguir ilustra essa situação.  
  
```  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 No exemplo anterior, as variáveis array `arrayA` e `arrayB` são considerados para ser do mesmo tipo de dados — `Byte()` — mesmo que eles sejam inicializados para diferentes comprimentos. Variáveis de `arrayB` e `arrayC` não são do mesmo tipo porque seus tipos de elemento são diferentes. Variáveis de `arrayC` e `arrayD` não são do mesmo tipo porque suas classificações são diferentes. Variáveis de `arrayD` e `arrayE` têm o mesmo tipo — `Short(,)` — porque suas classificações e tipos de elemento são os mesmos, embora `arrayD` ainda não foi inicializado.  
  
 Para obter mais informações sobre matrizes, consulte [matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="class-types"></a>Tipos de classe  
 Não há nenhum tipo de dados único contendo todas as classes. Embora uma classe pode herdar de outra classe, cada um é um tipo de dados separado. Várias instâncias da mesma classe são do mesmo tipo de dados. Se você atribuir uma variável de instância de classe para outra, não apenas eles têm os mesmos dados de tipo, eles apontam para a mesma instância de classe na memória.  
  
 Para obter mais informações sobre classes, consulte [objetos e Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Tipos de dados elementares](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Tipos genéricos no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Tipos de valor e tipos de referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Estruturas](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Solucionando problemas de tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Como manter mais de um valor em uma variável](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)
