---
title: Tabela de formatação de resultados numéricos – Referência de C#
ms.custom: seodec18
description: Saiba mais sobre cadeias de caracteres de formato numérico padrão do C#
ms.date: 09/20/2018
helpviewer_keywords:
- formatting [C#]
- numeric formatting [C#]
- String.Format method
ms.assetid: 120ba537-4448-4c62-8676-7a8fdd98f496
ms.openlocfilehash: 853faf481e546f2980d799d5daf50a14c608c052
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345468"
---
# <a name="formatting-numeric-results-table-c-reference"></a>Tabela de formatação de resultados numéricos (Referência de C#)

A tabela a seguir mostra os especificadores de formato compatíveis para formatação de resultados numéricos. O resultado formatado na última coluna corresponde ao "en-US" <xref:System.Globalization.CultureInfo>.

|Especificador de formato|Descrição|Exemplos|Resultado|  
|----------------------|-----------------|--------------|------------|  
|“C” ou “c”|Moeda|`string s = $"{2.5:C}";`<br /><br /> `string s = $"{-2.5:C}";`|\\$2.50<br /><br /> (\\$2.50)|  
|D ou d|Decimal|`string s = $"{25:D5}";`|00025|  
|"E" ou "e"|Exponencial|`string s = $"{250000:E2}";`|2.50E+005|  
|F ou f|Ponto fixo|`string s = $"{2.5:F2}";`<br /><br /> `string s = $"{2.5:F0}";`|2,50<br /><br /> 3|  
|"G" ou "g"|Geral|`string s = $"{2.5:G}";`|2.5|  
|"N" ou "n"|Numeric|`string s = $"{2500000:N}";`|2\.500.000,00|  
|P ou p|Porcentagem|`string s = $"{0.25:P}";`|25,00%|  
|R ou r|Ida e volta|`string s = $"{2.5:R}";`|2.5|  
|"X" ou "x"|Hexadecimal|`string s = $"{250:X}";`<br /><br /> `string s = $"{0xffff:X}";`|FA<br /><br /> FFFF|  

## <a name="remarks"></a>Comentários

Você pode usar um especificador de formato para criar uma cadeia de caracteres de formato. A cadeia de caracteres de formato é da seguinte forma: `Axx`, em que

- `A` é o especificador de formato, que controla o tipo de formatação aplicada ao valor numérico.
- `xx` é o especificador de precisão, que afeta o número de dígitos na saída formatada. O valor do especificador de precisão varia de 0 a 99.

Os especificadores de formato decimal ("D" ou "d") e hexadecimal ("X" ou "x") são compatíveis apenas com tipos integrais. O especificador de formato de ida e volta ("R" ou "r") é compatível apenas com tipos <xref:System.Single>, <xref:System.Double> e <xref:System.Numerics.BigInteger>.

As cadeias de caractere de formato numérico padrão têm suporte de:

- Algumas sobrecargas do método `ToString` de todos os tipos numéricos. Por exemplo, você pode fornecer uma cadeia de caracteres de formato numérico para os métodos <xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType> e <xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>.

- O [recurso de formatação composta](../../../standard/base-types/composite-formatting.md) do .NET, que é compatível com o método <xref:System.String.Format%2A?displayProperty=nameWithType>, por exemplo.

- [Cadeias de caracteres interpoladas](../tokens/interpolated.md).

Para obter mais informações, confira [Cadeias de caracteres de formato numérico padrão](../../../standard/base-types/standard-numeric-format-strings.md).

## <a name="see-also"></a>Veja também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Formatando tipos](../../../standard/base-types/formatting-types.md)
- [Formatação de composição](../../../standard/base-types/composite-formatting.md)
- [Interpolação de cadeia de caracteres](../tokens/interpolated.md)
- [string](../builtin-types/reference-types.md)
