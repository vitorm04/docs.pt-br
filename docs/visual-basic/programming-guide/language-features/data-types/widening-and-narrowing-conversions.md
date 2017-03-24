---
title: "Conversões (Visual Basic) entre | Documentos do Microsoft"
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
- widening conversions
- narrowing conversions
- conversions, type
- data types [Visual Basic], changing
- variables [Visual Basic], changing data type
- conversions, exceptions during conversion
- type conversion, exceptions during conversion
- conversions, data type
- conversions, narrowing
- type conversion, narrowing
- data type conversion, widening
- data type conversion, narrowing
- changing data types
- type conversion, widening
- data type conversion, exceptions during conversion
- conversions, widening
ms.assetid: 058c3152-6c28-4268-af44-2209e774f0bd
caps.latest.revision: 27
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
ms.openlocfilehash: 88c5db6e7e82a88ae8015b581e5a795ec389d003
ms.lasthandoff: 03/13/2017

---
# <a name="widening-and-narrowing-conversions-visual-basic"></a>Conversões de Widening e Narrowing (Visual Basic)
Uma consideração importante com uma conversão de tipos é se o resultado da conversão está dentro do intervalo do tipo de dados de destino.  
  
 A *conversões ampliadoras* muda o valor para um tipo de dados que pode permitir que qualquer valor possível dos dados originais.  Conversões ampliadoras preservar o valor de origem, mas podem alterar sua representação. Isso ocorre se você converter de um tipo integral para `Decimal`, ou de `Char` para `String`.  
  
 A *conversão de redução* muda o valor para um tipo de dados que pode não ser capaz de armazenar alguns dos possíveis valores. Por exemplo, um valor fracionário é arredondado quando ele é convertido em um tipo integral e um tipo numérico sendo convertido em `Boolean` é reduzido para `True` ou `False`.  
  
## <a name="widening-conversions"></a>Conversões de expansão  
 A tabela a seguir mostra as conversões ampliadoras padrão.  
  
|Tipo de dados|Amplia a tipos de dados <sup>1</sup>|  
|---|---|  
|[SByte](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[Byte](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|`Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[Curto](../../../../visual-basic/language-reference/data-types/short-data-type.md)|`Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[UShort](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[Número inteiro](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|`Integer`, `Long`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[UInteger](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|`UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Longas](../../../../visual-basic/language-reference/data-types/long-data-type.md)|`Long`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[ULong](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|`ULong`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Decimal](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Simples](../../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`, `Double`|  
|[Duplo](../../../../visual-basic/language-reference/data-types/double-data-type.md)|`Double`|  
|Qualquer tipo enumerado ([Enum](../../../../visual-basic/language-reference/statements/enum-statement.md))|Seu tipo integral subjacente e qualquer tipo ao qual o tipo subjacente amplia.|  
|[Char](../../../../visual-basic/language-reference/data-types/char-data-type.md)|`Char`, `String`|  
|Matriz `Char`|`Char`matriz,`String`|  
|Qualquer tipo|[Objeto](../../../../visual-basic/language-reference/data-types/object-data-type.md)|  
|Qualquer tipo derivado|Qualquer tipo do qual ele é derivado de base <sup>3</sup>.|  
|Qualquer tipo|Qualquer interface que ele implementa.|  
|[Nothing](../../../../visual-basic/language-reference/nothing.md)|Qualquer tipo de dados ou tipo de objeto.|  
  
 <sup>1</sup> por definição, cada tipo de dados amplia a mesmo.  
  
 <sup>2</sup> conversões de `Integer`, `UInteger`, `Long`, `ULong`, ou `Decimal` para `Single` ou `Double` pode resultar em perda de precisão, mas nunca na perda de magnitude. Nesse sentido, elas não provocam perda de informações.  
  
 <sup>3</sup> pode parecer estranho que uma conversão de um tipo derivado em um dos seus tipos base é ampliadora. A justificativa é que o tipo derivado contém todos os membros do tipo base, portanto, ele qualifica como uma instância do tipo base. Na direção oposta, o tipo base não contém quaisquer novos membros definidos pelo tipo derivado.  
  
 Conversões de ampliação sempre são bem-sucedidas em tempo de execução e nunca provocam perda de dados. Você pode sempre executá-las implicitamente, se o [instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) define o tipo de verificação alternar para `On` ou `Off`.  
  
## <a name="narrowing-conversions"></a>Conversões de redução  
 As conversões de estreitamento padrão incluem o seguinte:  
  
-   As direções inversas das conversões ampliadoras na anterior tabela (exceto pelo fato de cada tipo amplia a mesmo)  
  
-   Conversões em ambas as direções entre [Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) e qualquer tipo numérico  
  
-   Conversões de qualquer tipo numérico para qualquer tipo enumerado (`Enum`)  
  
-   Conversões em ambas as direções entre [sequência](../../../../visual-basic/language-reference/data-types/string-data-type.md) e qualquer tipo numérico, `Boolean`, ou [data](../../../../visual-basic/language-reference/data-types/date-data-type.md)  
  
-   Conversões de um tipo de dados ou objeto de tipo para um tipo derivado dele  
  
 Conversões de estreitamento nem sempre bem-sucedidas em tempo de execução e podem falhar ou provoca perda de dados. Ocorrerá um erro se o tipo de dados de destino não pode receber o valor que está sendo convertido. Por exemplo, uma conversão numérica pode resultar em um estouro. O compilador não permite executar conversões de estreitamento implicitamente, a menos que o [instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) define o tipo de verificação alternar para `Off`.  
  
> [!NOTE]
>  O erro de conversão de estreitamento será suprimido para conversões de elementos em um `For Each…Next` coleção para a variável de controle de loop. Para obter mais informações e exemplos, consulte a seção "Conversões de estreitamento" [para cada uma... Próxima instrução](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
### <a name="when-to-use-narrowing-conversions"></a>Quando usar conversões de estreitamento  
 Use uma conversão de restrição quando você souber que o valor de origem pode ser convertido no tipo de dados de destino sem erro ou perda de dados. Por exemplo, se você tiver um `String` que você sabe que contém "Verdadeiro" ou "False", você pode usar o `CBool` palavra-chave para convertê-lo para `Boolean`.  
  
## <a name="exceptions-during-conversion"></a>Exceções durante conversão  
 Como conversões ampliadoras sempre são bem-sucedida, elas não lançam exceções. Conversões de restrição, quando elas falham, mais comumente lançam as seguintes exceções:  
  
-   <xref:System.InvalidCastException>— Se nenhuma conversão for definida entre os dois tipos</xref:System.InvalidCastException>  
  
-   <xref:System.OverflowException>— (tipos integral somente) se o valor convertido é muito grande para o tipo de destino</xref:System.OverflowException>  
  
 Se uma classe ou estrutura define um [função CType](../../../../visual-basic/language-reference/functions/ctype-function.md) para servir como um operador de conversão entre classe ou estrutura, que `CType` pode acionar qualquer exceção que achar apropriada. Além disso, que `CType` pode chamar [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] funções ou [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] métodos, que por sua vez, podem acionar uma variedade de exceções.  
  
## <a name="changes-during-reference-type-conversions"></a>Alterações durante conversões de tipo de referência  
 Uma conversão de um *tipo de referência* copia apenas o ponteiro ao valor. O valor em si não é copiado nem alterado de alguma forma. A única coisa que pode mudar é o tipo de dados da variável mantendo o ponteiro. No exemplo a seguir, o tipo de dados é convertido da classe derivada para sua classe base, mas o objeto que ambas as variáveis apontam está inalterado.  
  
```  
' Assume class cSquare inherits from class cShape.  
Dim shape As cShape  
Dim square As cSquare = New cSquare  
' The following statement performs a widening  
' conversion from a derived class to its base class.  
shape = square  
```  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Conversões de tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Conversões implícitas e explícitas](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Conversões entre cadeias de caracteres e outros tipos](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)   
 [Como: converter um objeto em outro tipo no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)   
 [Conversões de matriz](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)   
 [Tipos de dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Funções de Conversão do Tipo](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
