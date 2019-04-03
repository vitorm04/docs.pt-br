---
title: Conversões implícitas e explícitas (Visual Basic)
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
ms.openlocfilehash: 82ff710629089cd14c7e982b4afa4301d0790811
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833991"
---
# <a name="implicit-and-explicit-conversions-visual-basic"></a>Conversões implícitas e explícitas (Visual Basic)
Uma *conversão implícita* não requer nenhuma sintaxe especial no código-fonte. No exemplo a seguir, o Visual Basic converte implicitamente o valor de `k` para um valor de ponto flutuante de precisão simples antes de atribuí-lo para `q`.  
  
```  
Dim k As Integer  
Dim q As Double  
' Integer widens to Double, so you can do this with Option Strict On.  
k = 432  
q = k  
```  
  
 Uma *conversão explícita* usa uma palavra-chave de conversão de tipo. Visual Basic fornece várias palavras-chave tais, que força uma expressão entre parênteses para o tipo de dados desejado. Essas palavras-chave atuam como funções, mas o compilador gera o código embutido, portanto, a execução é ligeiramente mais rápida do que com uma chamada de função.  
  
 Na seguinte extensão do exemplo anterior, o `CInt` palavra-chave converte o valor de `q` volta para um número inteiro antes de atribuí-lo para `k`.  
  
```  
' q had been assigned the value 432 from k.  
q = Math.Sqrt(q)  
k = CInt(q)  
' k now has the value 21 (rounded square root of 432).  
```  
  
## <a name="conversion-keywords"></a>Palavras-chave de conversão  
 A tabela a seguir mostra as palavras-chave de conversão disponíveis.  
  
|Palavra-chave de conversão de tipo|Converte uma expressão em tipo de dados|Tipos de dados permitido de expressão a ser convertido|  
|---|---|---|  
|`CBool`|[Tipo de Dados Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)|Qualquer tipo numérico (incluindo `Byte`, `SByte`e os tipos enumerados), `String`, `Object`|  
|`CByte`|[Tipo de Dados Byte](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|Qualquer tipo numérico (incluindo `SByte` e os tipos enumerados), `Boolean`, `String`, `Object`|  
|`CChar`|[Tipo de Dados de Caractere](../../../../visual-basic/language-reference/data-types/char-data-type.md)|`String`, `Object`|  
|`CDate`|[Tipo de Dados de Data](../../../../visual-basic/language-reference/data-types/date-data-type.md)|`String`, `Object`|  
|`CDbl`|[Tipo de Dados Duplo](../../../../visual-basic/language-reference/data-types/double-data-type.md)|Qualquer tipo numérico (incluindo `Byte`, `SByte`e os tipos enumerados), `Boolean`, `String`, `Object`|  
|`CDec`|[Tipo de Dados Decimal](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|Qualquer tipo numérico (incluindo `Byte`, `SByte`e os tipos enumerados), `Boolean`, `String`, `Object`|  
|`CInt`|[Tipo de Dados Integer](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|Qualquer tipo numérico (incluindo `Byte`, `SByte`e os tipos enumerados), `Boolean`, `String`, `Object`|  
|`CLng`|[Tipo de Dados Long](../../../../visual-basic/language-reference/data-types/long-data-type.md)|Qualquer tipo numérico (incluindo `Byte`, `SByte`e os tipos enumerados), `Boolean`, `String`, `Object`|  
|`CObj`|[Tipo de Dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)|Qualquer tipo|  
|`CSByte`|[Tipo de Dados SByte](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|Qualquer tipo numérico (incluindo `Byte` e os tipos enumerados), `Boolean`, `String`, `Object`|  
|`CShort`|[Tipo de Dados Short](../../../../visual-basic/language-reference/data-types/short-data-type.md)|Qualquer tipo numérico (incluindo `Byte`, `SByte`e os tipos enumerados), `Boolean`, `String`, `Object`|  
|`CSng`|[Tipo de Dados Simples](../../../../visual-basic/language-reference/data-types/single-data-type.md)|Qualquer tipo numérico (incluindo `Byte`, `SByte`e os tipos enumerados), `Boolean`, `String`, `Object`|  
|`CStr`|[Tipo de Dados String](../../../../visual-basic/language-reference/data-types/string-data-type.md)|Qualquer tipo numérico (incluindo `Byte`, `SByte`e os tipos enumerados), `Boolean`, `Char`, `Char` matriz, `Date`, `Object`|  
|`CType`|Tipo especificado após a vírgula (`,`)|Ao converter para um *tipo de dados elementar* (incluindo uma matriz de um tipo elementar), os mesmos tipos como permitido para a palavra-chave de conversão correspondente<br /><br /> Ao converter para um *tipo de dados composto*, as interfaces que ele implementa e as classes da qual ela herda<br /><br /> Ao converter em uma classe ou estrutura na qual você tenha sobrecarregado `CType`, classe ou estrutura|  
|`CUInt`|[Tipo de Dados UInteger](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|Qualquer tipo numérico (incluindo `Byte`, `SByte`e os tipos enumerados), `Boolean`, `String`, `Object`|  
|`CULng`|[Tipo de Dados ULong](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|Qualquer tipo numérico (incluindo `Byte`, `SByte`e os tipos enumerados), `Boolean`, `String`, `Object`|  
|`CUShort`|[Tipo de Dados UShort](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|Qualquer tipo numérico (incluindo `Byte`, `SByte`e os tipos enumerados), `Boolean`, `String`, `Object`|  
  
## <a name="the-ctype-function"></a>A função CType  
 O [função CType](../../../../visual-basic/language-reference/functions/ctype-function.md) opera em dois argumentos. A primeira é a expressão a ser convertida e a segunda é a classe de objeto ou tipo de dados do destino. Observe que o primeiro argumento deve ser uma expressão, não é um tipo.  
  
 `CType` é um *função embutida*, o que significa que o código compilado faz a conversão, muitas vezes sem gerar uma função chamada. Isso melhora o desempenho.  
  
 Para obter uma comparação `CType` com o outro tipo conversão palavras-chave, consulte [operador DirectCast](../../../../visual-basic/language-reference/operators/directcast-operator.md) e [operador TryCast](../../../../visual-basic/language-reference/operators/trycast-operator.md).  
  
### <a name="elementary-types"></a>Tipos elementares  
 O exemplo a seguir demonstra o uso de `CType`.  
  
```  
k = CType(q, Integer)  
' The following statement coerces w to the specific object class Label.  
f = CType(w, Label)  
```  
  
### <a name="composite-types"></a>Tipos compostos  
 Você pode usar `CType` para converter valores em tipos de dados compostos, bem como para tipos elementares. Você também pode usá-lo para forçar uma classe de objeto para o tipo de uma de suas interfaces, como no exemplo a seguir.  
  
```  
' Assume class cZone implements interface iZone.  
Dim h As Object  
' The first argument to CType must be an expression, not a type.  
Dim cZ As cZone  
' The following statement coerces a cZone object to its interface iZone.  
h = CType(cZ, iZone)  
```  
  
### <a name="array-types"></a>Tipos de matriz  
 `CType` também pode converter tipos de dados de matriz, como no exemplo a seguir.  
  
```  
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
  
### <a name="types-defining-ctype"></a>Tipos definindo CType  
 Você pode definir `CType` em uma classe ou estrutura que você definiu. Isso permite que você converter valores de e para o tipo de sua classe ou estrutura. Para obter mais informações e um exemplo, consulte [como: Definir um operador de conversão](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
> [!NOTE]
>  Valores usados com uma palavra-chave de conversão devem ser válidos para o tipo de dados de destino, ou ocorrerá um erro. Por exemplo, se você tentar converter um `Long` para um `Integer`, o valor da `Long` deve estar dentro do intervalo válido para o `Integer` tipo de dados.  
  
> [!CAUTION]
>  Especificando `CType` para converter de um tipo de classe para outra falha no tempo de execução se o tipo de origem não é derivado do tipo de destino. Uma falha gera um <xref:System.InvalidCastException> exceção.  
  
 No entanto, se um dos tipos é uma estrutura ou classe definida por você, e se você tiver definido `CType` sobre essa classe ou estrutura, uma conversão pode ser bem-sucedida se ele satisfaz os requisitos de seu `CType`. Confira [Como Definir um operador de conversão](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
 Executar uma conversão explícita é também conhecido como *conversão* uma expressão para uma classe de objeto ou tipo de dados especificados.  
  
## <a name="see-also"></a>Consulte também

- [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Conversões entre Cadeias de Caracteres e Outros Tipos](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [Como: Converter um objeto em outro tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [Estruturas](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Tipos de Dados](../../../../visual-basic/language-reference/data-types/index.md)
- [Funções de Conversão do Tipo](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Solução de problemas de Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
