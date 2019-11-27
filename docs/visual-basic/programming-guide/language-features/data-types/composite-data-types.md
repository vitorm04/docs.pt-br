---
title: Tipos de dados compostos
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
ms.openlocfilehash: 1c099c5082f1c4173a50c70998c99135c94821e6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346383"
---
# <a name="composite-data-types-visual-basic"></a>Tipos de dados compostos (Visual Basic)
Além dos tipos de dados elementares Visual Basic suprimentos, você também pode montar itens de tipos diferentes para criar *tipos de dados compostos* , como estruturas, matrizes e classes. Você pode criar tipos de dados compostos de tipos elementares e de outros tipos compostos. Por exemplo, você pode definir uma matriz de elementos de estrutura ou uma estrutura com membros de matriz.  
  
## <a name="data-types"></a>Tipos de dados  
 Um tipo composto é diferente do tipo de dados de qualquer um de seus componentes. Por exemplo, uma matriz de elementos de `Integer` não é do tipo de dados `Integer`.  
  
 Um tipo de dados de matriz normalmente é representado usando o tipo de elemento, parênteses e vírgulas, conforme necessário. Por exemplo, uma matriz unidimensional de elementos `String` é representada como `String()`e uma matriz bidimensional de elementos `Boolean` é representada como `Boolean(,)`.  
  
## <a name="structure-types"></a>Tipos de estrutura  
 Não há nenhum tipo de dados único composto por todas as estruturas. Em vez disso, cada definição de uma estrutura representa um tipo de dados exclusivo, mesmo que duas estruturas definam elementos idênticos na mesma ordem. No entanto, se você criar duas ou mais instâncias da mesma estrutura, Visual Basic as considerará como sendo do mesmo tipo de dados.  
  
## <a name="tuples"></a>Tuples

Uma tupla é uma estrutura leve que contém dois ou mais campos cujos tipos são predefinidos. As tuplas têm suporte a partir do Visual Basic 2017. As tuplas são usadas com mais frequência para retornar vários valores de uma única chamada de método sem precisar passar argumentos por referência ou empacotamento dos campos retornados em uma classe ou estrutura mais pesada. Consulte o tópico [tuplas](tuples.md) para obter mais informações sobre tuplas.

## <a name="array-types"></a>Tipos de matriz  
 Não há nenhum tipo de dados único composto por todas as matrizes. O tipo de dados de uma determinada instância de uma matriz é determinado pelo seguinte:  
  
- O fato de ser uma matriz  
  
- A classificação (número de dimensões) da matriz  
  
- O tipo de elemento da matriz  
  
 Em particular, o comprimento de uma determinada dimensão não faz parte do tipo de dados da instância. O exemplo a seguir mostra isso.  
  
```vb  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 No exemplo anterior, as variáveis de matriz `arrayA` e `arrayB` são consideradas do mesmo tipo de dados — `Byte()` — mesmo que elas sejam inicializadas para diferentes comprimentos. As variáveis `arrayB` e `arrayC` não são do mesmo tipo porque seus tipos de elementos são diferentes. As variáveis `arrayC` e `arrayD` não são do mesmo tipo porque suas classificações são diferentes. As variáveis `arrayD` e `arrayE` têm o mesmo tipo — `Short(,)` — porque suas classificações e os tipos de elementos são os mesmos, mesmo que `arrayD` ainda não tenha sido inicializado.  
  
 Para obter mais informações sobre matrizes, consulte [matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="class-types"></a>Tipos de classe  
 Não há nenhum tipo de dados único que abranja todas as classes. Embora uma classe possa herdar de outra classe, cada uma é um tipo de dados separado. Várias instâncias da mesma classe são do mesmo tipo de dados. Se você atribuir uma variável de instância de classe a outra, não apenas elas terão o mesmo tipo de dados, elas apontarão para a mesma instância de classe na memória.  
  
 Para obter mais informações sobre classes, consulte [objetos e classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## <a name="see-also"></a>Consulte também

- [Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Tipos de Dados Elementares](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Tipos genéricos no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Tipos de Valor e Tipos de Referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Estruturas](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Solução de problemas de Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Como manter mais de um valor em uma variável](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)
