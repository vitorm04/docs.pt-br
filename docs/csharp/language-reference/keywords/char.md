---
title: "char (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 41f672e9b12481fa5cce78015e95d2c5245a26db
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="char-c-reference"></a>char (Referência de C#)
A palavra-chave `char` é usada para declarar uma instância da estrutura <xref:System.Char?displayProperty=nameWithType> que o .NET Framework usa para representar um caractere Unicode. O valor de um objeto `Char` é um valor numérico de 16 bits (ordinal).  
  
 Os caracteres Unicode são usados para representar a maioria dos idiomas escritos em todo o mundo.  
  
|Tipo|Intervalo|Tamanho|Tipo do .NET Framework|  
|----------|-----------|----------|-------------------------|  
|`char`|U+0000 a U+FFFF|Caractere Unicode de 16 bits|<xref:System.Char?displayProperty=nameWithType>|  
  
## <a name="literals"></a>Literais  
 As constantes de tipo `char` podem ser escritas como literais de caracteres, sequência de escape hexadecimal ou como representação Unicode. Você também pode converter os códigos de caracteres integrais. No exemplo a seguir, quatro variáveis `char` são inicializadas com o mesmo caractere `X`:  
  
 [!code-csharp[csrefKeywordsTypes#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/char_1.cs)]  
  
## <a name="conversions"></a>Conversões  
 Um `char` pode ser implicitamente convertido em [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md). No entanto, não há conversões implícitas de outros tipos para o tipo `char`.  
  
 O tipo <xref:System.Char?displayProperty=nameWithType> fornece vários métodos estáticos para trabalhar com valores `char`.  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Char>  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
 [Tabela de tipos integrais](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Tabela de tipos internos](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Tabela de conversões numéricas implícitas](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [Tabela de conversões numéricas explícitas](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
 [Tipos que permitem valor nulo](../../../csharp/programming-guide/nullable-types/index.md)  
 [Cadeias de Caracteres](../../../csharp/programming-guide/strings/index.md)
