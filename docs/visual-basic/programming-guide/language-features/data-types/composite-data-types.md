---
title: Tipos de dados compostos (Visual Basic)
ms.date: 04/25/2017
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- classes [Visual Basic], composite types
- types [Visual Basic], composite
ms.assetid: 62970f2e-52c0-4369-8963-613820f1f434
ms.openlocfilehash: ea719b60a6bcd40494666d4923fad296a8ddae70
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58833809"
---
# <a name="composite-data-types-visual-basic"></a>Tipos de dados compostos (Visual Basic)
Além das fontes de Visual Basic de tipos de dados elementar, você também pode montar itens de diferentes tipos para criar *tipos de dados compostos* como classes, matrizes e estruturas. Você pode criar tipos de dados compostos de tipos elementares e de outros tipos compostos. Por exemplo, você pode definir uma matriz de elementos de estrutura, ou uma estrutura com membros da matriz.  
  
## <a name="data-types"></a>Tipos de Dados  
 Um tipo composto é diferente do tipo de dados de qualquer um dos seus componentes. Por exemplo, uma matriz de `Integer` elementos não é do `Integer` tipo de dados.  
  
 Um tipo de dados de matriz normalmente é representado usando o tipo de elemento, parênteses e vírgulas conforme necessário. Por exemplo, uma matriz unidimensional do `String` elementos é representado como `String()`e uma matriz bidimensional de `Boolean` elementos é representado como `Boolean(,)`.  
  
## <a name="structure-types"></a>Tipos de estrutura  
 Não há nenhum tipo de dados único que inclui todas as estruturas. Em vez disso, cada definição de uma estrutura representa um tipo de dados exclusivo, mesmo se duas estruturas definem elementos idênticos na mesma ordem. No entanto, se você criar duas ou mais instâncias da mesma estrutura, o Visual Basic considera que eles sejam do mesmo tipo de dados.  
  
## <a name="tuples"></a>Tuplas

Uma tupla é uma estrutura leve que contém dois ou mais campos cujos tipos são predefinidos. As tuplas têm suporte, começando com o Visual Basic 2017. As tuplas são mais comumente usadas para retornar vários valores de uma única chamada de método sem ter que passar argumentos por referência ou Empacotando os campos retornados em uma classe ou estrutura em mais pesada. Consulte a [tuplas](tuples.md) tópico para obter mais informações sobre as tuplas.

## <a name="array-types"></a>Tipos de matriz  
 Não há nenhum tipo de dados único que inclui todas as matrizes. O tipo de dados de uma instância específica de uma matriz é determinado pelo seguinte:  
  
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
  
 No exemplo anterior, as variáveis de matriz `arrayA` e `arrayB` são considerados para ser do mesmo tipo de dados — `Byte()` — mesmo que eles são inicializados para diferentes comprimentos. Variáveis `arrayB` e `arrayC` não são do mesmo tipo porque seus tipos de elemento são diferentes. Variáveis `arrayC` e `arrayD` não são do mesmo tipo porque suas classificações são diferentes. Variáveis `arrayD` e `arrayE` têm o mesmo tipo — `Short(,)` — porque suas classificações e os tipos de elemento são os mesmos, embora `arrayD` ainda não foi inicializado.  
  
 Para obter mais informações sobre matrizes, consulte [matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="class-types"></a>Tipos de classe  
 Não há nenhum tipo de dados único que inclui todas as classes. Embora uma classe pode herdar de outra classe, cada um é um tipo de dados separado. Várias instâncias da mesma classe são do mesmo tipo de dados. Se você atribuir uma variável de instância de classe para outra, não apenas têm os mesmos dados de tipo, eles apontam para a mesma instância de classe na memória.  
  
 Para obter mais informações sobre classes, consulte [objetos e Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## <a name="see-also"></a>Consulte também

- [Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Tipos de Dados Elementares](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Tipos genéricos no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Tipos de Valor e Tipos de Referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Estruturas](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Solução de problemas de Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Como: manter mais de um valor em uma variável](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)
