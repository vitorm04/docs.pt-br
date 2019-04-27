---
title: Conversões de Widening e Narrowing (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- widening conversions [Visual Basic]
- narrowing conversions [Visual Basic]
- conversions [Visual Basic], type
- data types [Visual Basic], changing
- variables [Visual Basic], changing data type
- conversions [Visual Basic], exceptions during conversion
- type conversion [Visual Basic], exceptions during conversion
- conversions [Visual Basic], data type
- conversions [Visual Basic], narrowing
- type conversion [Visual Basic], narrowing
- data type conversion [Visual Basic], widening
- data type conversion [Visual Basic], narrowing
- changing data types [Visual Basic]
- type conversion [Visual Basic], widening
- data type conversion [Visual Basic], exceptions during conversion
- conversions [Visual Basic], widening
ms.assetid: 058c3152-6c28-4268-af44-2209e774f0bd
ms.openlocfilehash: 9f1a71e8e2e3e4ebb9b412be74b5ea8702eb164f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61827150"
---
# <a name="widening-and-narrowing-conversions-visual-basic"></a>Conversões de Widening e Narrowing (Visual Basic)
Uma consideração importante com uma conversão de tipo é se o resultado da conversão é dentro do intervalo do tipo de dados de destino.  
  
 Um *conversão de ampliação* altera um valor para um tipo de dados que pode permitir que qualquer valor possível dos dados originais.  Conversões de ampliação preservam o valor de origem, mas podem alterar sua representação. Isso ocorre se você converter de um tipo integral para `Decimal`, ou de `Char` para `String`.  
  
 Um *conversão de estreitamento* altera um valor para um tipo de dados que pode não ser capaz de armazenar alguns dos possíveis valores. Por exemplo, um valor fracionário é arredondado quando ele é convertido em um tipo integral e um tipo numérico que está sendo convertido em `Boolean` é reduzido para `True` ou `False`.  
  
## <a name="widening-conversions"></a>Conversões de expansão  
 A tabela a seguir mostra as conversões ampliadoras padrão.  
  
|Tipo de dados|Amplia a tipos de dados <sup>1</sup>|  
|---|---|  
|[SByte](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[Byte](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|`Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[Short](../../../../visual-basic/language-reference/data-types/short-data-type.md)|`Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[UShort](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[Integer](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|`Integer`, `Long`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[UInteger](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|`UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Long](../../../../visual-basic/language-reference/data-types/long-data-type.md)|`Long`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[ULong](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|`ULong`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Decimal](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Simples](../../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`, `Double`|  
|[Duplo](../../../../visual-basic/language-reference/data-types/double-data-type.md)|`Double`|  
|Qualquer tipo enumerado ([Enum](../../../../visual-basic/language-reference/statements/enum-statement.md))|Seu tipo integral subjacente e qualquer tipo ao qual o tipo subjacente amplia.|  
|[Char](../../../../visual-basic/language-reference/data-types/char-data-type.md)|`Char`, `String`|  
|Matriz `Char`|`Char` array, `String`|  
|Qualquer tipo|[Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)|  
|Qualquer tipo derivado|Qualquer tipo do qual ele é derivado de base <sup>3</sup>.|  
|Qualquer tipo|Qualquer interface que ele implementa.|  
|[Nothing](../../../../visual-basic/language-reference/nothing.md)|Qualquer tipo de dados ou o tipo de objeto.|  
  
 <sup>1</sup> por definição, cada tipo de dados amplia a mesmo.  
  
 <sup>2</sup> conversões de `Integer`, `UInteger`, `Long`, `ULong`, ou `Decimal` para `Single` ou `Double` pode resultar em perda de precisão, mas nunca na perda de magnitude. Nesse sentido, elas não provocam perda de informações.  
  
 <sup>3</sup> pode parecer surpreendente que uma conversão de um tipo derivado em um dos seus tipos base é de ampliação. A justificação é que o tipo derivado contém todos os membros do tipo base, para que ela se qualificar como uma instância do tipo base. Na direção oposta, o tipo base não contém quaisquer novos membros definidos por um tipo derivado.  
  
 Conversões de ampliação sempre ter êxito em tempo de execução e nunca incorrerá em perda de dados. Você sempre pode executá-los implicitamente, se o [instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) define o tipo de comutador para a verificação `On` ou a `Off`.  
  
## <a name="narrowing-conversions"></a>Conversões de redução  
 As conversões de estreitamento padrão incluem o seguinte:  
  
-   As direções inversas das conversões ampliadoras anteriormente na tabela (exceto pelo fato de cada tipo amplia a mesmo)  
  
-   Conversões em ambas as direções entre [Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) e qualquer tipo numérico  
  
-   Conversões de qualquer tipo numérico para qualquer tipo de enumerado (`Enum`)  
  
-   Conversões em ambas as direções entre [cadeia de caracteres](../../../../visual-basic/language-reference/data-types/string-data-type.md) e qualquer tipo numérico, `Boolean`, ou [data](../../../../visual-basic/language-reference/data-types/date-data-type.md)  
  
-   As conversões de um tipo de dados ou objeto de tipo para um tipo derivado dele  
  
 Conversões de estreitamento nem sempre ter êxito em tempo de execução e pode falhar ou causar a perda de dados. Ocorrerá um erro se o tipo de dados de destino não puder receber o valor que está sendo convertido. Por exemplo, uma conversão numérica pode resultar em um estouro. O compilador não permite que você execute conversões redutoras implicitamente, a menos que o [instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) define o tipo de verificação de alternar para `Off`.  
  
> [!NOTE]
>  O erro de conversão de estreitamento será suprimido para conversões de elementos em um `For Each…Next` coleção para a variável de controle de loop. Para obter mais informações e exemplos, consulte a seção "Conversões de estreitamento" [para cada um... Próxima instrução](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
### <a name="when-to-use-narrowing-conversions"></a>Quando usar conversões de estreitamento  
 Quando você souber que o valor de origem pode ser convertido no tipo de dados de destino sem erro ou perda de dados, você usar uma conversão de estreitamento. Por exemplo, se você tiver um `String` que você saiba que contém "True" ou "False", você pode usar o `CBool` palavra-chave para convertê-lo para `Boolean`.  
  
## <a name="exceptions-during-conversion"></a>Exceções durante conversão  
 Como conversões ampliadoras sempre ter êxito, eles não geram exceções. Conversões de redução, quando ocorre uma falha, mais comumente lançam as seguintes exceções:  
  
-   <xref:System.InvalidCastException> — Se nenhuma conversão é definida entre os dois tipos  
  
-   <xref:System.OverflowException> — (tipos integral somente) se o valor convertido for muito grande para o tipo de destino  
  
 Se uma classe ou estrutura define um [função CType](../../../../visual-basic/language-reference/functions/ctype-function.md) para servir como um operador de conversão para ou de classe ou estrutura, que `CType` pode lançar qualquer exceção que achar apropriado. Além disso, que `CType` pode chamar funções do Visual Basic ou [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] métodos, que por sua vez, podem acionar uma variedade de exceções.  
  
## <a name="changes-during-reference-type-conversions"></a>Alterações durante conversões de tipo de referência  
 Uma conversão de um *tipo de referência* copia somente o ponteiro para o valor. O valor em si não é copiado nem alterado de alguma forma. A única coisa que pode alterar é o tipo de dados da variável que contém o ponteiro. No exemplo a seguir, o tipo de dados é convertido da classe derivada em sua classe base, mas o objeto que as duas variáveis agora apontam para permanece inalterado.  
  
```  
' Assume class cSquare inherits from class cShape.  
Dim shape As cShape  
Dim square As cSquare = New cSquare  
' The following statement performs a widening  
' conversion from a derived class to its base class.  
shape = square  
```  
  
## <a name="see-also"></a>Consulte também

- [Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Conversões Implícitas e Explícitas](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Conversões entre Cadeias de Caracteres e Outros Tipos](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [Como: Converter um objeto em outro tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [Conversões de Matriz](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [Tipos de Dados](../../../../visual-basic/language-reference/data-types/index.md)
- [Funções de Conversão do Tipo](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
