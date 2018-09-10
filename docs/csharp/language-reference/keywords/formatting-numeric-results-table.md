---
title: Tabela de formatação de resultados numéricos (Referência de C#)
ms.date: 07/20/2015
helpviewer_keywords:
- formatting [C#]
- numeric formatting [C#]
- String.Format method
- Console.Write method
ms.assetid: 120ba537-4448-4c62-8676-7a8fdd98f496
ms.openlocfilehash: 8d034955d5d5d31788eafc0c21246451d7fd1f35
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43508193"
---
# <a name="formatting-numeric-results-table-c-reference"></a>Tabela de formatação de resultados numéricos (Referência de C#)
Você pode formatar resultados numéricos usando o método <xref:System.String.Format%2A?displayProperty=nameWithType>, por meio dos métodos <xref:System.Console.Write%2A?displayProperty=nameWithType> ou <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> que chamam `String.Format`, ou usando a [interpolação de cadeia de caracteres](../tokens/interpolated.md). O formato é especificado usando cadeias de caracteres de formato. A tabela a seguir contém as cadeias de caracteres de formato padrão com suporte. A cadeia de caracteres de formato usa o seguinte formato: `Axx`, em que `A` é o especificador de formato e `xx` é o especificador de precisão. O especificador de formato controla o tipo de formatação aplicada ao valor numérico e o especificador de precisão controla o número de dígitos significativos ou casas decimais do resultado formatado. O valor do especificador de precisão varia de 0 a 99.  
  
 Para obter mais informações sobre cadeias de caracteres de formatação padrão e personalizadas, consulte [Tipos de Formatação](../../../standard/base-types/formatting-types.md).
  
|Especificador de Formato|Descrição|Exemplos|Saída|  
|----------------------|-----------------|--------------|------------|  
|“C” ou “c”|Moeda|Console.Write("{0:C}", 2.5);<br /><br /> Console.Write("{0:C}", -2.5);|$2.50<br /><br /> ($2,50)|  
|D ou d|Decimal|Console.Write("{0:D5}", 25);|00025|  
|"E" ou "e"|Científico|Console.Write("{0:E}", 250000);|2,500000E+005|  
|F ou f|Ponto fixo|Console.Write("{0:F2}", 25);<br /><br /> Console.Write("{0:F0}", 25);|25,00<br /><br /> 25|  
|"G" ou "g"|Geral|Console.Write("{0:G}", 2.5);|2.5|  
|"N" ou "n"|Número|Console.Write("{0:N}", 2500000);|2.500.000,00|  
|"X" ou "x"|Hexadecimal|Console.Write("{0:X}", 250);<br /><br /> Console.Write("{0:X}", 0xffff);|FA<br /><br /> FFFF|  
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Cadeias de Caracteres de Formato Numérico Padrão](../../../standard/base-types/standard-numeric-format-strings.md)  
- [Tabelas de referência de tipos](../../../csharp/language-reference/keywords/reference-tables-for-types.md)  
- [string](../../../csharp/language-reference/keywords/string.md)
