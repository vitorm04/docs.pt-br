---
title: Tipos de dados numéricos
ms.date: 07/20/2015
helpviewer_keywords:
- integral types [Visual Basic], Visual Basic
- Short data type [Visual Basic], numeric data types
- Double data type [Visual Basic], numeric data types
- Long data type [Visual Basic], Visual Basic numeric data types
- numbers [Visual Basic], whole
- fractions
- numbers
- whole numbers
- integer numbers
- numbers [Visual Basic], integer
- fractional data types [Visual Basic]
- mantissas, of fractional numbers
- mantissas
- data types [Visual Basic], numeric
- Integer data type [Visual Basic], numeric data types
- exponent, of fractional numbers
- integers [Visual Basic]
- numeric data types [Visual Basic], Visual Basic
- Single data type [Visual Basic], numeric types
- Decimal data type [Visual Basic], numeric data types
ms.assetid: a27bd4d0-7e14-43eb-9cc4-b42eaab323c9
ms.openlocfilehash: dc8b630eebc48e5733344a00664b453360769c0b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346317"
---
# <a name="numeric-data-types-visual-basic"></a>Tipos de dados numéricos (Visual Basic)
O Visual Basic fornece vários *tipos de dados numéricos* para lidar com números em várias representações. Tipos *integrais* representam apenas números inteiros (positivos, negativos e zero) e tipos não *integrais* representam números com partes inteiras e fracionárias.  
  
 Para uma tabela que mostra uma comparação lado a lado do Visual Basic tipos de dados, consulte [tipos de dados](../../../../visual-basic/language-reference/data-types/index.md).  
  
## <a name="integral-numeric-types"></a>Tipos numéricos inteiros  
 Os *tipos de dados integral* são aqueles que representam apenas números sem partes fracionárias.  
  
 Os tipos de dados integrais *assinados* são [tipo de dados SByte](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md) (8 bits), tipo de dados [curto](../../../../visual-basic/language-reference/data-types/short-data-type.md) (16 bits), [tipo de dados Integer](../../../../visual-basic/language-reference/data-types/integer-data-type.md) (32 bits) e [tipo de dados Long](../../../../visual-basic/language-reference/data-types/long-data-type.md) (64 bits). Se uma variável sempre armazenar inteiros em vez de números fracionários, declare-o como um desses tipos.  
  
 Os tipos integral *não assinados* são [tipo de dados de byte](../../../../visual-basic/language-reference/data-types/byte-data-type.md) (8 bits), [tipo de dados UShort](../../../../visual-basic/language-reference/data-types/ushort-data-type.md) (16 bits), [tipo de dados UInteger](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md) (32 bits) e [tipo de dados ULong](../../../../visual-basic/language-reference/data-types/ulong-data-type.md) (64 bits). Se uma variável contiver dados binários, ou dados de natureza desconhecida, declare-a como um desses tipos.  
  
### <a name="performance"></a>Desempenho  
 As operações aritméticas são mais rápidas com tipos integrais do que com outros tipos de dados. Eles são mais rápidos com os tipos `Integer` e `UInteger` em Visual Basic.  
  
### <a name="large-integers"></a>Inteiros grandes  
 Se você precisar manter um inteiro maior do que o tipo de dados `Integer` pode conter, você poderá usar o tipo de dados `Long` em vez disso. `Long` variáveis podem conter números de-9.223.372.036.854.775.808 até 9.223.372.036.854.775.807. As operações com `Long` são um pouco mais lentas do que com `Integer`.  
  
 Se você precisar de valores ainda maiores, poderá usar o [tipo de dados decimal](../../../../visual-basic/language-reference/data-types/decimal-data-type.md). Você pode armazenar números de-79228162514264337593543950335 por meio de 79228162514264337593543950335 em uma variável `Decimal` se não usar nenhuma casa decimal. No entanto, as operações com números de `Decimal` são consideravelmente mais lentas do que com qualquer outro tipo de dados numéricos.  
  
### <a name="small-integers"></a>Inteiros pequenos  
 Se você não precisar do intervalo completo do tipo de dados `Integer`, poderá usar o tipo de dados `Short`, que pode conter números inteiros de-32.768 a 32.767. Para o menor intervalo inteiro, o tipo de dados `SByte` contém números inteiros de-128 a 127. Se você tiver um número muito grande de variáveis que contenham inteiros pequenos, a Common Language Runtime poderá, às vezes, armazenar suas `Short` e `SByte` variáveis com mais eficiência e economizar o consumo de memória. No entanto, as operações com `Short` e `SByte` são um pouco mais lentas do que com `Integer`.  
  
### <a name="unsigned-integers"></a>Inteiros não assinados  
 Se você sabe que a variável nunca precisa conter um número negativo, você pode usar os *tipos não assinados*`Byte`, `UShort`, `UInteger`e `ULong`. Cada um desses tipos de dados pode conter um inteiro positivo duas vezes maior que o tipo assinado correspondente (`SByte`, `Short`, `Integer`e `Long`). Em termos de desempenho, cada tipo não assinado é exatamente tão eficiente quanto seu tipo assinado correspondente. Em particular, `UInteger` compartilhamentos com `Integer` a diferença de ser a mais eficiente de todos os tipos de dados numéricos elementares.  
  
## <a name="nonintegral-numeric-types"></a>Tipos numéricos não integrais  
 Os *tipos de dados não integral* são aqueles que representam números com partes inteiras e fracionárias.  
  
 Os tipos de dados numéricos não integral são `Decimal` (ponto fixo de 128 bits), [tipo de dados único](../../../../visual-basic/language-reference/data-types/single-data-type.md) (ponto flutuante de 32 bits) e [tipo de dados duplo](../../../../visual-basic/language-reference/data-types/double-data-type.md) (ponto flutuante de 64 bits). Eles são todos os tipos assinados. Se uma variável puder conter uma fração, declare-a como um desses tipos.  
  
 `Decimal` não é um tipo de dados de ponto flutuante. `Decimal` números têm um valor inteiro binário e um fator de dimensionamento inteiro que especifica qual parte do valor é uma fração decimal.  
  
 Você pode usar variáveis de `Decimal` para valores monetários. A vantagem é a precisão dos valores. O tipo de dados `Double` é mais rápido e requer menos memória, mas está sujeito a erros de arredondamento. O tipo de dados `Decimal` mantém a precisão completa para 28 casas decimais.  
  
 Números de ponto flutuante (`Single` e `Double`) têm intervalos maiores do que `Decimal` números, mas podem estar sujeitos a erros de arredondamento. Os tipos de ponto flutuante dão suporte a menos dígitos significativos que `Decimal`, mas podem representar valores de magnitude maior.  
  
 Valores de número não integral podem ser expressos como mmmEeee, em que Mmm é o *mantissa* (os dígitos significativos) e EEE é o *expoente* (uma potência de 10). Os valores positivos mais altos dos tipos não integrais são 7.9228162514264337593543950335 E + 28 para `Decimal`, 3.4028235 E + 38 para `Single`e 1.79769313486231570 E + 308 para `Double`.  
  
### <a name="performance"></a>Desempenho  
 `Double` é a mais eficiente dos tipos de dados fracionários, porque os processadores em plataformas atuais executam operações de ponto flutuante em precisão dupla. No entanto, as operações com `Double` não são tão rápidas quanto com os tipos integrais, como `Integer`.  
  
### <a name="small-magnitudes"></a>Pequenas magnitudes  
 Para números com a menor magnitude possível (mais próxima de 0), `Double` variáveis podem conter números tão pequenos quanto-4.94065645841246544 E-324 para valores negativos e 4.94065645841246544 E-324 para valores positivos.  
  
### <a name="small-fractional-numbers"></a>Números fracionários pequenos  
 Se você não precisar do intervalo completo do tipo de dados `Double`, poderá usar o tipo de dados `Single`, que pode conter números de ponto flutuante de-3.4028235 E + 38 a 3.4028235 E + 38. As menores magnitudes para variáveis de `Single` são-1.401298 E-45 para valores negativos e 1.401298 E-45 para valores positivos. Se você tiver um número muito grande de variáveis que contenham números pequenos de ponto flutuante, a Common Language Runtime às vezes poderá armazenar suas variáveis de `Single` com mais eficiência e economizar o consumo de memória.  
  
## <a name="see-also"></a>Consulte também

- [Tipos de Dados Elementares](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Tipos de Dados de Caractere](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)
- [Tipos de Dados Diversos](../../../../visual-basic/programming-guide/language-features/data-types/miscellaneous-data-types.md)
- [Solução de problemas de Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Como chamar uma função do Windows que use tipos não assinados](../../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
