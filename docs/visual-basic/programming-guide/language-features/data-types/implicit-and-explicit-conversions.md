---
title: Conversões implícitas e explícitas
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [Visual Basic], type
- variables [Visual Basic], changing data type
- casting
- conversions [Visual Basic], data type
- type conversion [Visual Basic], implicit conversions
- CType function [Visual Basic], conversions
- casting, data types
- data type conversion [Visual Basic], explicit
- type conversion [Visual Basic], explicit conversions
- data types [Visual Basic], casting
- conversions [Visual Basic], implicit
- explicit data type conversions [Visual Basic]
- conversions [Visual Basic]
- changing data types [Visual Basic]
- conversions [Visual Basic], explicit
- data type conversion [Visual Basic], implicit
- implicit data type conversions [Visual Basic]
ms.assetid: 77de1659-af8a-492c-967e-e7ef60ccce66
ms.openlocfilehash: b7215933cec89b7023f08e8996a283b39b3a3c83
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346364"
---
# <a name="implicit-and-explicit-conversions-visual-basic"></a>Conversões implícitas e explícitas (Visual Basic)

Uma *conversão implícita* não requer nenhuma sintaxe especial no código-fonte. No exemplo a seguir, Visual Basic converte implicitamente o valor de `k` em um valor de ponto flutuante de precisão simples antes de atribuí-lo ao `q`.

```vb
Dim k As Integer
Dim q As Double
' Integer widens to Double, so you can do this with Option Strict On.
k = 432
q = k
```

Uma *conversão explícita* usa uma palavra-chave de conversão de tipo. Visual Basic fornece várias palavras-chave, que forçam uma expressão entre parênteses e o tipo de dados desejado. Essas palavras-chave atuam como funções, mas o compilador gera o código embutido, portanto a execução é ligeiramente mais rápida do que com uma chamada de função.

Na seguinte extensão do exemplo anterior, a palavra-chave `CInt` converte o valor de `q` de volta para um inteiro antes de atribuí-lo ao `k`.

```vb
' q had been assigned the value 432 from k.
q = Math.Sqrt(q)
k = CInt(q)
' k now has the value 21 (rounded square root of 432).
```

## <a name="conversion-keywords"></a>Palavras-chave de conversão

A tabela a seguir mostra as palavras-chave de conversão disponíveis.

|Palavra-chave de conversão de tipo|Converte uma expressão em tipo de dados|Tipos de dados permitidos da expressão a serem convertidos|
|---|---|---|
|`CBool`|[Tipo de Dados Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)|Qualquer tipo numérico (incluindo `Byte`, `SByte`e tipos enumerados), `String``Object`|
|`CByte`|[Tipo de Dados Byte](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|Qualquer tipo numérico (incluindo `SByte` e tipos enumerados), `Boolean`, `String``Object`|
|`CChar`|[Tipo de Dados de Caractere](../../../../visual-basic/language-reference/data-types/char-data-type.md)|`String`, `Object`|
|`CDate`|[Tipo de Dados de Data](../../../../visual-basic/language-reference/data-types/date-data-type.md)|`String`, `Object`|
|`CDbl`|[Tipo de Dados Duplo](../../../../visual-basic/language-reference/data-types/double-data-type.md)|Qualquer tipo numérico (incluindo `Byte`, `SByte`e tipos enumerados), `Boolean`, `String`, `Object`|
|`CDec`|[Tipo de Dados Decimal](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|Qualquer tipo numérico (incluindo `Byte`, `SByte`e tipos enumerados), `Boolean`, `String`, `Object`|
|`CInt`|[Tipo de Dados Integer](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|Qualquer tipo numérico (incluindo `Byte`, `SByte`e tipos enumerados), `Boolean`, `String`, `Object`|
|`CLng`|[Tipo de Dados Long](../../../../visual-basic/language-reference/data-types/long-data-type.md)|Qualquer tipo numérico (incluindo `Byte`, `SByte`e tipos enumerados), `Boolean`, `String`, `Object`|
|`CObj`|[Tipo de Dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)|Qualquer tipo|
|`CSByte`|[Tipo de Dados SByte](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|Qualquer tipo numérico (incluindo `Byte` e tipos enumerados), `Boolean`, `String``Object`|
|`CShort`|[Tipo de Dados Short](../../../../visual-basic/language-reference/data-types/short-data-type.md)|Qualquer tipo numérico (incluindo `Byte`, `SByte`e tipos enumerados), `Boolean`, `String`, `Object`|
|`CSng`|[Tipo de Dados Simples](../../../../visual-basic/language-reference/data-types/single-data-type.md)|Qualquer tipo numérico (incluindo `Byte`, `SByte`e tipos enumerados), `Boolean`, `String`, `Object`|
|`CStr`|[Tipo de Dados String](../../../../visual-basic/language-reference/data-types/string-data-type.md)|Qualquer tipo numérico (incluindo `Byte`, `SByte`e tipos enumerados), `Boolean`, `Char`, `Char` matriz, `Date`, `Object`|
|`CType`|Tipo especificado após a vírgula (`,`)|Ao converter para um *tipo de dados elementar* (incluindo uma matriz de um tipo elementar), os mesmos tipos permitidos para a palavra-chave de conversão correspondente<br /><br /> Ao converter para um *tipo de dados composto*, as interfaces que ele implementa e as classes das quais ele herda<br /><br /> Ao converter para uma classe ou estrutura na qual você tem sobrecarregado `CType`, essa classe ou estrutura|
|`CUInt`|[Tipo de Dados UInteger](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|Qualquer tipo numérico (incluindo `Byte`, `SByte`e tipos enumerados), `Boolean`, `String`, `Object`|
|`CULng`|[Tipo de Dados ULong](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|Qualquer tipo numérico (incluindo `Byte`, `SByte`e tipos enumerados), `Boolean`, `String`, `Object`|
|`CUShort`|[Tipo de Dados UShort](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|Qualquer tipo numérico (incluindo `Byte`, `SByte`e tipos enumerados), `Boolean`, `String`, `Object`|

## <a name="the-ctype-function"></a>A função CType

A [função CType](../../../../visual-basic/language-reference/functions/ctype-function.md) opera em dois argumentos. A primeira é a expressão a ser convertida e a segunda é o tipo de dados de destino ou a classe de objeto. Observe que o primeiro argumento deve ser uma expressão, não um tipo.

`CType` é uma *função embutida*, o que significa que o código compilado faz a conversão, muitas vezes sem gerar uma chamada de função. Isso melhora o desempenho.

Para obter uma comparação de `CType` com as outras palavras-chave de conversão de tipo, consulte operador [DirectCast](../../../../visual-basic/language-reference/operators/directcast-operator.md) e [Operador TryCast](../../../../visual-basic/language-reference/operators/trycast-operator.md).

### <a name="elementary-types"></a>Tipos elementares

O exemplo a seguir demonstra o uso de `CType`.

```vb
k = CType(q, Integer)
' The following statement coerces w to the specific object class Label.
f = CType(w, Label)
```

### <a name="composite-types"></a>Tipos compostos

Você pode usar `CType` para converter valores em tipos de dados compostos, bem como em tipos elementares. Você também pode usá-lo para forçar uma classe de objeto para o tipo de uma de suas interfaces, como no exemplo a seguir.

```vb
' Assume class cZone implements interface iZone.
Dim h As Object
' The first argument to CType must be an expression, not a type.
Dim cZ As cZone
' The following statement coerces a cZone object to its interface iZone.
h = CType(cZ, iZone)
```

### <a name="array-types"></a>Tipos de matriz

`CType` também pode converter tipos de dados de matriz, como no exemplo a seguir.

```vb
Dim v() As classV
Dim obArray() As Object
' Assume some object array has been assigned to obArray.
' Check for run-time type compatibility.
If TypeOf obArray Is classV()
    ' obArray can be converted to classV.
    v = CType(obArray, classV())
End If
```

Para obter mais informações e um exemplo, consulte [conversões de matriz](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md).

### <a name="types-defining-ctype"></a>Tipos que definem CType

Você pode definir `CType` em uma classe ou estrutura que você definiu. Isso permite que você converta valores de e para o tipo de sua classe ou estrutura. Para obter mais informações e um exemplo, consulte [como definir um operador de conversão](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).

> [!NOTE]
> Os valores usados com uma palavra-chave de conversão devem ser válidos para o tipo de dados de destino ou ocorre um erro. Por exemplo, se você tentar converter um `Long` em um `Integer`, o valor da `Long` deverá estar dentro do intervalo válido para o tipo de dados `Integer`.

> [!CAUTION]
> A especificação de `CType` para converter de um tipo de classe para outro falhará em tempo de execução se o tipo de origem não for derivado do tipo de destino. Uma falha desse tipo gera uma exceção de <xref:System.InvalidCastException>.

No entanto, se um dos tipos for uma estrutura ou classe que você definiu, e se você tiver definido `CType` nessa estrutura ou classe, uma conversão poderá ter sucesso se atender aos requisitos de seu `CType`. Consulte [como: definir um operador de conversão](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).

A execução de uma conversão explícita também é conhecida como *conversão* de uma expressão em um determinado tipo de dados ou classe de objeto.

## <a name="see-also"></a>Consulte também

- [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Conversões entre Cadeias de Caracteres e Outros Tipos](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [Como converter um objeto em outro tipo em Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [Estruturas](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Tipos de Dados](../../../../visual-basic/language-reference/data-types/index.md)
- [Funções de Conversão do Tipo](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Solução de problemas de Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
