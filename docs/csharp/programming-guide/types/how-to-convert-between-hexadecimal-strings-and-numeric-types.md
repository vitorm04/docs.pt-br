---
title: "Como converter entre cadeias de caracteres hexadecimais e tipos num&#233;ricos (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "conversões [C#], cadeias de caracteres hexadecimais"
  - "cadeias de caracteres hexadecimais [C#]"
  - "cadeias de caracteres hexadecimais [C#], convertendo em tipo numérico"
  - "cadeias de caracteres [C#], convertendo cadeias de caracteres hexadecimais"
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como converter entre cadeias de caracteres hexadecimais e tipos num&#233;ricos (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Estes exemplos mostram como realizar as seguintes tarefas:  
  
-   Obtenha o valor hexadecimal de cada caractere em um  [seqüência de caracteres](../../../csharp/language-reference/keywords/string.md).  
  
-   Obter o  [char](../../../csharp/language-reference/keywords/char.md) que corresponde a cada valor em uma seqüência de caracteres hexadecimal.  
  
-   Converter hexadecimal `string` para um  [int](../../../csharp/language-reference/keywords/int.md).  
  
-   Converter hexadecimal `string` para um  [float](../../../csharp/language-reference/keywords/float.md).  
  
-   Converter um  [bytes](../../../csharp/language-reference/keywords/byte.md) array para hexadecimal `string`.  
  
## Exemplo  
 Este exemplo produz o valor hexadecimal de cada caractere em um `string`.  Primeiro analisa o `string` a uma matriz de caracteres.  Em seguida, ele chama <xref:System.Convert.ToInt32%28System.Char%29> cada caractere, para obter seu valor numérico.  Finalmente, ele formata o número como sua representação hexadecimal em um `string`.  
  
 [!code-cs[csProgGuideTypes#30](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_1.cs)]  
  
## Exemplo  
 Este exemplo analisa um `string` de valores de hexadecimal e gera o caractere correspondente a cada valor hexadecimal.  Primeiro chama o [Split\(Char\[\]\)](assetId:///M:System.String.Split(System.Char[])?qualifyHint=False&autoUpgrade=False) método para obter cada valor hexadecimal como um indivíduo `string` em uma matriz.  Em seguida, ele chama <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> para converter o valor hexadecimal em um valor decimal representado como um  [int](../../../csharp/language-reference/keywords/int.md).  Ela mostra duas maneiras diferentes para obter o caractere correspondente a esse código de caractere.  A primeira técnica usa <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, que retorna o caractere correspondente ao argumento de inteiro como um `string`.  A segunda técnica explicitamente projeta o `int` para um  [char](../../../csharp/language-reference/keywords/char.md).  
  
 [!code-cs[csProgGuideTypes#31](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_2.cs)]  
  
## Exemplo  
 Este exemplo mostra outra maneira de converter hexadecimal `string` como um inteiro, chamando o <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> método.  
  
 [!code-cs[csProgGuideTypes#32](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_3.cs)]  
  
## Exemplo  
 O exemplo a seguir mostra como converter hexadecimal `string` para um  [float](../../../csharp/language-reference/keywords/float.md) usando o <xref:System.BitConverter?displayProperty=fullName> classe e o <xref:System.Int32.Parse%2A?displayProperty=fullName> método.  
  
 [!code-cs[csProgGuideTypes#39](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_4.cs)]  
  
## Exemplo  
 O exemplo a seguir mostra como converter um  [bytes](../../../csharp/language-reference/keywords/byte.md) matriz como uma seqüência hexadecimal, usando o <xref:System.BitConverter?displayProperty=fullName> classe.  
  
 [!code-cs[csProgGuideTypes#38](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_5.cs)]  
  
## Consulte também  
 [Cadeias de caracteres de formato numérico padrão](../Topic/Standard%20Numeric%20Format%20Strings.md)   
 [Tipos](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Como determinar se uma cadeia de caracteres representa um valor numérico](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)