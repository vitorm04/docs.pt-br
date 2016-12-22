---
title: "Como converter uma cadeia de caracteres em um n&#250;mero (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "conversões [C#]"
  - "conversões [C#], cadeia de caracteres para int"
  - "convertendo cadeias de caracteres em int [C#]"
  - "cadeias de caracteres [C#], convertendo em int"
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
caps.latest.revision: 34
caps.handback.revision: 34
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como converter uma cadeia de caracteres em um n&#250;mero (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Você pode converter um [cadeia de caracteres](../../../csharp/language-reference/keywords/string.md) para um número usando métodos o <xref:System.Convert> classe ou usando o `TryParse` método encontrado em vários tipos numéricos \(int, long, float, etc.\).  
  
 Se você tiver uma cadeia de caracteres, é um pouco mais eficiente e simples chamar um `TryParse` método \(por exemplo, `int.TryParse(“11”)`\).  Usando um `Convert` método é mais útil para objetos gerais que implementam <xref:System.IConvertible>.  
  
 Você pode usar `Parse` ou `TryParse` métodos no tipo numérico esperado contém a cadeia de caracteres, como o <xref:System.Int32?displayProperty=fullName> tipo.  O método <xref:System.Convert.ToUInt32%2A?displayProperty=fullName> usa <xref:System.Int32.Parse%2A> internamente.  Se a cadeia de caracteres não estiver em um formato válido, `Parse` lança uma exceção enquanto `TryParse` retorna [false](../../../csharp/language-reference/keywords/false.md).  
  
## Exemplo  
 O `Parse` e `TryParse` métodos ignoram espaço em branco no início e no final da cadeia de caracteres, mas todos os outros caracteres devem ser caracteres que formam o tipo numérico apropriado \(int, long, ulong, etc decimal, float,.\).  Qualquer espaço em branco dentro dos caracteres que formam o número causa um erro.  Por exemplo, você pode usar `decimal.TryParse` para analisar "10", "10.3", "10", mas você não pode usar esse método para analisar 10 de "10 X", "1 0" \(Observação espaço\), "10. 3" \(Observação espaço\), "10e1" \(`float.TryParse` funciona aqui\) e assim por diante.  
  
 Os exemplos abaixo demonstram chamadas com e sem êxito a `Parse` e `TryParse`.  
  
 [!code-cs[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]  
[!code-cs[csProgGuideTypes#25](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_2.cs)]  
[!code-cs[csProgGuideTypes#26](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_3.cs)]  
[!code-cs[csProgGuideTypes#27](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_4.cs)]  
[!code-cs[csProgGuideTypes#28](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_5.cs)]  
[!code-cs[csProgGuideTypes#100](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_6.cs)]  
  
## Exemplo  
 A tabela a seguir lista alguns dos métodos da <xref:System.Convert> classe que você pode usar.  
  
|Tipo numérico|Método|  
|-------------------|------------|  
|`decimal`|<xref:System.Convert.ToDecimal%28System.String%29>|  
|`float`|<xref:System.Convert.ToSingle%28System.String%29>|  
|`double`|<xref:System.Convert.ToDouble%28System.String%29>|  
|`short`|<xref:System.Convert.ToInt16%28System.String%29>|  
|`int`|<xref:System.Convert.ToInt32%28System.String%29>|  
|`long`|<xref:System.Convert.ToInt64%28System.String%29>|  
|`ushort`|<xref:System.Convert.ToUInt16%28System.String%29>|  
|`uint`|<xref:System.Convert.ToUInt32%28System.String%29>|  
|`ulong`|<xref:System.Convert.ToUInt64%28System.String%29>|  
  
 Este exemplo chama o método <xref:System.Convert.ToInt32%28System.String%29?displayProperty=fullName> para converter uma entrada [string](../../../csharp/language-reference/keywords/string.md) em [int](../../../csharp/language-reference/keywords/int.md).  O código captura as duas exceções mais comuns que podem ser lançadas por esse método, <xref:System.FormatException> e <xref:System.OverflowException>.  Se o número pode ser incrementado sem estourar o local de armazenamento de inteiros, o programa adiciona 1 ao resultado e imprime a saída.  
  
 [!code-cs[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]  
[!code-cs[csProgGuideTypes#24](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_7.cs)]  
  
## Consulte também  
 [Tipos](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Como determinar se uma cadeia de caracteres representa um valor numérico](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)   
 [utilitário de formatação do .NET Framework 4](http://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)