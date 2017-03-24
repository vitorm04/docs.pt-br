---
title: "Conversões implícitas e explícitas (Visual Basic) | Documentos do Microsoft"
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
- conversions, type
- variables [Visual Basic], changing data type
- casting
- conversions, data type
- type conversion, implicit conversions
- CType function, conversions
- casting, data types
- data type conversion, explicit
- type conversion, explicit conversions
- data types [Visual Basic], casting
- conversions, implicit
- explicit data type conversions
- conversions
- changing data types
- conversions, explicit
- data type conversion, implicit
- implicit data type conversions
ms.assetid: 77de1659-af8a-492c-967e-e7ef60ccce66
caps.latest.revision: 25
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 24c434df4be480c290b3e4e36bd9f294d12b99ef
ms.lasthandoff: 03/13/2017

---
# <a name="implicit-and-explicit-conversions-visual-basic"></a>Conversões implícitas e explícitas (Visual Basic)
Um *conversão implícita* não requer nenhuma sintaxe especial no código-fonte. No exemplo a seguir, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] implicitamente converte o valor de `k` para um valor de ponto flutuante de precisão única antes de atribuí-lo para `q`.  
  
```  
Dim k As Integer  
Dim q As Double  
' Integer widens to Double, so you can do this with Option Strict On.  
k = 432  
q = k  
```  
  
 Um *conversão explícita* usa uma palavra-chave de conversão de tipo. [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]fornece várias palavras-chave tais, que força uma expressão entre parênteses ao tipo de dados desejado. Essas palavras-chave atuam como funções, mas o compilador gera o código embutido, portanto execução é ligeiramente mais rápida do que com uma chamada de função.  
  
 Na seguinte extensão do exemplo anterior, o `CInt` palavra-chave converte o valor de `q` para um número inteiro antes de atribuí-lo para `k`.  
  
```  
' q had been assigned the value 432 from k.  
q = Math.Sqrt(q)  
k = CInt(q)  
' k now has the value 21 (rounded square root of 432).  
```  
  
## <a name="conversion-keywords"></a>Palavras-chave de conversão  
 A tabela a seguir mostra as palavras-chave conversão disponível.  
  
|Palavra-chave de conversão de tipo|Converte uma expressão em tipo de dados|Tipos de dados permitido de expressão a ser convertido|  
|---|---|---|  
|`CBool`|[Tipo de Dados Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)|Qualquer tipo numérico (incluindo `Byte`, `SByte`e os tipos enumerados), `String`,`Object`|  
|`CByte`|[Tipo de Dados Byte](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|Qualquer tipo numérico (incluindo `SByte` e os tipos enumerados), `Boolean`, `String`,`Object`|  
|`CChar`|[Tipo de Dados de Caractere](../../../../visual-basic/language-reference/data-types/char-data-type.md)|`String`, `Object`|  
|`CDate`|[Tipo de Dados de Data](../../../../visual-basic/language-reference/data-types/date-data-type.md)|`String`, `Object`|  
|`CDbl`|[Tipo de Dados Duplo](../../../../visual-basic/language-reference/data-types/double-data-type.md)|Qualquer tipo numérico (incluindo `Byte`, `SByte`e os tipos enumerados), `Boolean`, `String`,`Object`|  
|`CDec`|[Tipo de Dados Decimal](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|Qualquer tipo numérico (incluindo `Byte`, `SByte`e os tipos enumerados), `Boolean`, `String`,`Object`|  
|`CInt`|[Tipo de Dados Integer](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|Qualquer tipo numérico (incluindo `Byte`, `SByte`e os tipos enumerados), `Boolean`, `String`,`Object`|  
|`CLng`|[Tipo de Dados Long](../../../../visual-basic/language-reference/data-types/long-data-type.md)|Qualquer tipo numérico (incluindo `Byte`, `SByte`e os tipos enumerados), `Boolean`, `String`,`Object`|  
|`CObj`|[Tipo de Dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)|Qualquer tipo|  
|`CSByte`|[Tipo de Dados SByte](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|Qualquer tipo numérico (incluindo `Byte` e os tipos enumerados), `Boolean`, `String`,`Object`|  
|`CShort`|[Tipo de Dados Short](../../../../visual-basic/language-reference/data-types/short-data-type.md)|Qualquer tipo numérico (incluindo `Byte`, `SByte`e os tipos enumerados), `Boolean`, `String`,`Object`|  
|`CSng`|[Tipo de Dados Simples](../../../../visual-basic/language-reference/data-types/single-data-type.md)|Qualquer tipo numérico (incluindo `Byte`, `SByte`e os tipos enumerados), `Boolean`, `String`,`Object`|  
|`CStr`|[Tipo de Dados String](../../../../visual-basic/language-reference/data-types/string-data-type.md)|Qualquer tipo numérico (incluindo `Byte`, `SByte`e os tipos enumerados), `Boolean`, `Char`, `Char` matriz, `Date`,`Object`|  
|`CType`|Tipo especificado após a vírgula (`,`)|Ao converter para um *tipo de dados elementar* (incluindo uma matriz de um tipo elementar), os mesmos tipos como permitido para a palavra-chave conversão correspondente<br /><br /> Ao converter para um *tipo de dados composto*, as interfaces que ele implementa e as classes do qual ele herda<br /><br /> Ao converter a uma classe ou estrutura na qual você tenha sobrecarregado `CType`, classe ou estrutura|  
|`CUInt`|[Tipo de Dados UInteger](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|Qualquer tipo numérico (incluindo `Byte`, `SByte`e os tipos enumerados), `Boolean`, `String`,`Object`|  
|`CULng`|[Tipo de Dados ULong](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|Qualquer tipo numérico (incluindo `Byte`, `SByte`e os tipos enumerados), `Boolean`, `String`,`Object`|  
|`CUShort`|[Tipo de Dados UShort](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|Qualquer tipo numérico (incluindo `Byte`, `SByte`e os tipos enumerados), `Boolean`, `String`,`Object`|  
  
## <a name="the-ctype-function"></a>A função CType  
 O [função CType](../../../../visual-basic/language-reference/functions/ctype-function.md) opera em dois argumentos. A primeira é a expressão a ser convertida e o segundo é a classe de objeto ou tipo de dados do destino. Observe que o primeiro argumento deve ser uma expressão, não um tipo.  
  
 `CType`é um *função embutida*, que significa que o código compilado faz a conversão, com frequência sem gerar uma função chamada. Isso melhora o desempenho.  
  
 Para obter uma comparação de `CType` com as outras keywords de conversão de tipo, consulte [operador DirectCast](../../../../visual-basic/language-reference/operators/directcast-operator.md) e [operador TryCast](../../../../visual-basic/language-reference/operators/trycast-operator.md).  
  
### <a name="elementary-types"></a>Tipos elementares  
 O exemplo a seguir demonstra o uso de `CType`.  
  
```  
k = CType(q, Integer)  
' The following statement coerces w to the specific object class Label.  
f = CType(w, Label)  
```  
  
### <a name="composite-types"></a>Tipos compostos  
 Você pode usar `CType` para converter valores em tipos de dados compostos bem como para tipos elementares. Você também pode usá-lo para forçar uma classe de objeto para o tipo de uma das suas interfaces, como no exemplo a seguir.  
  
```  
' Assume class cZone implements interface iZone.  
Dim h As Object  
' The first argument to CType must be an expression, not a type.  
Dim cZ As cZone  
' The following statement coerces a cZone object to its interface iZone.  
h = CType(cZ, iZone)  
```  
  
### <a name="array-types"></a>Tipos de matriz  
 `CType`também pode converter tipos de dados de matriz, como no exemplo a seguir.  
  
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
 Você pode definir `CType` em uma classe ou estrutura que você definiu. Isso permite que você converter valores de e para o tipo de sua classe ou estrutura. Para obter mais informações e um exemplo, consulte [como: definir um operador de conversão](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
> [!NOTE]
>  Valores usados com uma palavra-chave de conversão devem ser válidos para o tipo de dados de destino, ou ocorrerá um erro. Por exemplo, se você tentar converter uma `Long` para um `Integer`, o valor da `Long` deve estar dentro do intervalo válido para o `Integer` tipo de dados.  
  
> [!CAUTION]
>  Especificando `CType` para converter de um tipo de classe para outra falha no tempo de execução se o tipo de origem não é derivado do tipo de destino. Uma falha gera uma <xref:System.InvalidCastException>exceção.</xref:System.InvalidCastException>  
  
 No entanto, se um dos tipos é uma estrutura ou classe que você definiu, e se você tiver definido `CType` em que classe ou estrutura, uma conversão pode terá êxito se ele satisfaz os requisitos de seu `CType`. Consulte [como: definir um operador de conversão](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
 Executar uma conversão explícita é também conhecido como *conversão* uma expressão a uma classe de objeto ou tipo de dados especificados.  
  
## <a name="see-also"></a>Consulte também  
 [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Conversões entre cadeias de caracteres e outros tipos](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)   
 [Como: converter um objeto em outro tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)   
 [Estruturas](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Tipos de dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Funções de conversão de tipo](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Solução de problemas de Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
