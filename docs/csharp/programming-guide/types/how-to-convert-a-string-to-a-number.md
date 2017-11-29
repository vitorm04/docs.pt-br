---
title: "Como converter uma cadeia de caracteres em um número (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
caps.latest.revision: "34"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3dc67bc2f25bba14df0e3ce6859bb8bc9094871c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a>Como converter uma cadeia de caracteres em um número (Guia de Programação em C#)
É possível converter uma [string](../../../csharp/language-reference/keywords/string.md) em um número usando os métodos na classe <xref:System.Convert> ou usando o método `TryParse` encontrado nos diversos tipos numéricos (int, long, float, etc.).  
  
 Caso haja uma cadeia de caracteres, é um pouco mais eficiente e simples chamar um método `TryParse` (por exemplo, `int.TryParse("11")`).  Usar um método `Convert` é mais útil para objetos gerais que implementam <xref:System.IConvertible>.  
  
 É possível usar métodos `Parse` ou `TryParse` no tipo numérico que se espera que a cadeia de caracteres contenha, como o tipo <xref:System.Int32?displayProperty=nameWithType>.  O método <xref:System.Convert.ToUInt32%2A?displayProperty=nameWithType> usa <xref:System.Int32.Parse%2A> internamente.  Se a cadeia de caracteres não estiver em um formato válido, `Parse` lançará uma exceção, ao passo que `TryParse` retornará [false](../../../csharp/language-reference/keywords/false.md).  
  
## <a name="example"></a>Exemplo  
 Os métodos `Parse` e `TryParse` ignoram o espaço em branco no início e no final da cadeia de caracteres, porém, todos os outros caracteres devem formar o tipo numérico correto (int, long, ulong, float, decimal etc.).  Os espaços em branco dentro dos caracteres que formam o número causam um erro.  Por exemplo, é possível usar `decimal.TryParse` para analisar "10", "10.3", "  10  ", mas não é possível usar esse método para analisar 10 de "10X", "1 0" (observe o espaço), "10 .3" (observe o espaço), "10e1" (`float.TryParse` funcionará neste caso) e assim por diante.  
  
 Os exemplos abaixo demonstram chamadas com e sem êxito a `Parse` e `TryParse`.  
  
 [!code-csharp[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]  
[!code-csharp[csProgGuideTypes#25](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_2.cs)]  
[!code-csharp[csProgGuideTypes#26](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_3.cs)]  
[!code-csharp[csProgGuideTypes#27](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_4.cs)]  
[!code-csharp[csProgGuideTypes#28](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_5.cs)]  
[!code-csharp[csProgGuideTypes#100](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_6.cs)]  
  
## <a name="example"></a>Exemplo  
 A tabela a seguir lista alguns dos métodos da classe <xref:System.Convert> que você pode usar.  
  
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
  
 Este exemplo chama o método <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> para converter uma entrada [string](../../../csharp/language-reference/keywords/string.md) em [int](../../../csharp/language-reference/keywords/int.md). O código captura as duas exceções mais comuns que podem ser geradas por esse método, <xref:System.FormatException> e <xref:System.OverflowException>. Se o número pode ser incrementado sem estourar o local de armazenamento de inteiros, o programa adiciona 1 ao resultado e imprime a saída.  
  
 [!code-csharp[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]  
[!code-csharp[csProgGuideTypes#24](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_7.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Tipos](../../../csharp/programming-guide/types/index.md)  
 [Como determinar se uma cadeia de caracteres representa um valor numérico](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)  
 [.NET Framework 4 Formatting Utility](http://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)
