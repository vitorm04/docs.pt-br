---
title: "Tabela de Formatação de Resultados Numéricos (Referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- formatting [C#]
- numeric formatting [C#]
- String.Format method
- Console.Write method
ms.assetid: 120ba537-4448-4c62-8676-7a8fdd98f496
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7e6feae4b0d03bb8570106d37868462d12d937cf
ms.lasthandoff: 03/13/2017

---
# <a name="formatting-numeric-results-table-c-reference"></a>Tabela de formatação de resultados numéricos (Referência de C#)
É possível formatar resultados numéricos usando o método <xref:System.String.Format%2A?displayProperty=fullName> ou por meio do <xref:System.Console.Write%2A?displayProperty=fullName> ou do método <xref:System.Console.WriteLine%2A?displayProperty=fullName>, que chama `String.Format`. O formato é especificado usando cadeias de caracteres de formato. A tabela a seguir contém as cadeias de caracteres de formato padrão com suporte. A cadeia de caracteres de formato usa o seguinte formato: `Axx`, em que `A` é o especificador de formato e `xx` é o especificador de precisão. O especificador de formato controla o tipo de formatação aplicada ao valor numérico e o especificador de precisão controla o número de dígitos significativos ou casas decimais do resultado formatado. O valor do especificador de precisão varia de 0 a 99.  
  
 Para obter mais informações sobre cadeias de caracteres de formatação padrão e personalizadas, consulte [Tipos de Formatação](../../../standard/base-types/formatting-types.md). Para obter mais informações sobre o método `String.Format`, consulte <xref:System.String.Format%2A?displayProperty=fullName>.  
  
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
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Cadeias de Caracteres de Formato Numérico Padrão](http://msdn.microsoft.com/library/580e57eb-ac47-4ffd-bccd-3a1637c2f467)   
 [Tabelas de Referência de Tipos](../../../csharp/language-reference/keywords/reference-tables-for-types.md)   
 [string](../../../csharp/language-reference/keywords/string.md)
