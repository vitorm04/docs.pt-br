---
title: "Como Converter uma Cadeia de Caracteres em um Número (Guia de Programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
caps.latest.revision: 34
author: BillWagner
ms.author: wiwagn
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e6ebc67300a1f4456ae031a7962f4cd1f5306dd5
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a>Como converter uma cadeia de caracteres em um número (Guia de Programação em C#)
É possível converter uma [cadeia de caracteres](../../../csharp/language-reference/keywords/string.md) em um número por meio dos métodos na classe <xref:System.Convert> ou usando o método `TryParse` encontrado nos diversos tipos numéricos (int, long, float etc.).  
  
 Caso haja uma cadeia de caracteres, é um pouco mais eficiente e simples chamar um método `TryParse` (por exemplo, `int.TryParse(“11”)`).  Usar um método `Convert` é mais útil para objetos gerais que implementam <xref:System.IConvertible>.  
  
 É possível usar métodos `Parse` ou `TryParse` no tipo numérico que se espera que a cadeia de caracteres contenha, como o tipo <xref:System.Int32?displayProperty=fullName>.  O método <xref:System.Convert.ToUInt32%2A?displayProperty=fullName> usa <xref:System.Int32.Parse%2A> internamente.  Se a cadeia de caracteres não estiver em um formato válido, `Parse` lançará uma exceção, ao passo que `TryParse` retornará [false](../../../csharp/language-reference/keywords/false.md).  
  
## <a name="example"></a>Exemplo  
 Os métodos `Parse` e `TryParse` ignoram o espaço em branco no início e no final da cadeia de caracteres, porém, todos os outros caracteres devem formar o tipo numérico correto (int, long, ulong, float, decimal etc.).  Os espaços em branco dentro dos caracteres que formam o número causam um erro.  Por exemplo, é possível usar `decimal.TryParse` para analisar “10”, “10.3”, “  10  “, mas não é possível utilizar esse método para analisar 10 de “10X”, “1 0” (observe o espaço), “10 .3” (observe o espaço), “10e1” (`float.TryParse` funcionará neste caso) e assim por diante.  
  
 Os exemplos abaixo demonstram chamadas com e sem êxito a `Parse` e `TryParse`.  
  
 [!code-cs[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]  
[!code-cs[csProgGuideTypes#25](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_2.cs)]  
[!code-cs[csProgGuideTypes#26](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_3.cs)]  
[!code-cs[csProgGuideTypes#27](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_4.cs)]  
[!code-cs[csProgGuideTypes#28](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_5.cs)]  
[!code-cs[csProgGuideTypes#100](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_6.cs)]  
  
## <a name="example"></a>Exemplo  
 A tabela a seguir lista alguns dos métodos da classe <xref:System.Convert> que podem ser utilizados.  
  
|Tipo numérico|Método|  
|------------------|------------|  
|`decimal`|<xref:System.Convert.ToDecimal%28System.String%29>|  
|`float`|<xref:System.Convert.ToSingle%28System.String%29>|  
|`double`|<xref:System.Convert.ToDouble%28System.String%29>|  
|`short`|<xref:System.Convert.ToInt16%28System.String%29>|  
|`int`|<xref:System.Convert.ToInt32%28System.String%29>|  
|`long`|<xref:System.Convert.ToInt64%28System.String%29>|  
|`ushort`|<xref:System.Convert.ToUInt16%28System.String%29>|  
|`uint`|<xref:System.Convert.ToUInt32%28System.String%29>|  
|`ulong`|<xref:System.Convert.ToUInt64%28System.String%29>|  
  
 Este exemplo chama o método <xref:System.Convert.ToInt32%28System.String%29?displayProperty=fullName> para converter uma [cadeia de caracteres](../../../csharp/language-reference/keywords/string.md) de entrada em um [int](../../../csharp/language-reference/keywords/int.md). O código captura as duas exceções mais comuns que podem ser lançadas por esse método, <xref:System.FormatException> e <xref:System.OverflowException>. Se o número pode ser incrementado sem estourar o local de armazenamento de inteiros, o programa adiciona 1 ao resultado e imprime a saída.  
  
 [!code-cs[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]  
[!code-cs[csProgGuideTypes#24](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_7.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Tipos](../../../csharp/programming-guide/types/index.md)   
 [Como Determinar se uma Cadeia de Caracteres Representa um Valor Numérico](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)   
 [.NET Framework 4 Formatting Utility](http://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)
