---
title: "Como converter entre cadeias de caracteres hexadecimais e tipos numéricos (Guia de Programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
caps.latest.revision: 19
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
ms.translationtype: Human Translation
ms.sourcegitcommit: fe32676f0e39ed109a68f39584cf41aec5f5ce90
ms.openlocfilehash: bbc5a3aebfd0086388a4a5b020ad8679395cb74b
ms.contentlocale: pt-br
ms.lasthandoff: 05/10/2017

---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a>Como converter entre cadeias de caracteres hexadecimais e tipos numéricos (Guia de Programação em C#)
Estes exemplos mostram como realizar as seguintes tarefas:  
  
-   Obter o valor hexadecimal de cada caractere em uma [cadeia de caracteres](../../../csharp/language-reference/keywords/string.md).  
  
-   Obter o [char](../../../csharp/language-reference/keywords/char.md) que corresponde a cada valor em uma cadeia de caracteres hexadecimal.  
  
-   Converter um `string` hexadecimal em um [int](../../../csharp/language-reference/keywords/int.md).  
  
-   Converter um `string` hexadecimal em um [float](../../../csharp/language-reference/keywords/float.md).  
  
-   Como converter uma matriz de [bytes](../../../csharp/language-reference/keywords/byte.md) em um `string` hexadecimal.  
  
## <a name="example"></a>Exemplo  
 Este exemplo gera o valor hexadecimal de cada caractere em um `string`. Primeiro, ele analisa o `string` como uma matriz de caracteres. Em seguida, ele chama <xref:System.Convert.ToInt32%28System.Char%29> em cada caractere para obter seu valor numérico. Por fim, ele formata o número como sua representação hexadecimal em um `string`.  
  
 [!code-cs[csProgGuideTypes#30](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_1.cs)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo analisa um `string` de valores hexadecimais e gera o caractere correspondente a cada valor hexadecimal. Primeiro, ele chama o método [Split(Char\[\])](xref:System.String.Split(System.Char[])) para obter cada valor hexadecimal como um `string` individual em uma matriz. Em seguida, ele chama <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> para converter o valor hexadecimal para um valor decimal representado como um [int](../../../csharp/language-reference/keywords/int.md). Ele mostra duas maneiras diferentes de obter o caractere correspondente ao código de caractere. A primeira técnica usa <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, que retorna o caractere correspondente ao argumento de inteiro como um `string`. A segunda técnica converte explicitamente o `int` em um [char](../../../csharp/language-reference/keywords/char.md).  
  
 [!code-cs[csProgGuideTypes#31](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_2.cs)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo mostra outra maneira de converter um hexadecimal `string` em um inteiro, chamando o método <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29>.  
  
 [!code-cs[csProgGuideTypes#32](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_3.cs)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como converter um hexadecimal `string` para um [float](../../../csharp/language-reference/keywords/float.md) usando a classe <xref:System.BitConverter?displayProperty=fullName> e o método <xref:System.Int32.Parse%2A?displayProperty=fullName>.  
  
 [!code-cs[csProgGuideTypes#39](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_4.cs)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como converter uma matriz de [bytes](../../../csharp/language-reference/keywords/byte.md) em uma cadeia de caracteres hexadecimal usando a classe <xref:System.BitConverter?displayProperty=fullName>.  
  
 [!code-cs[csProgGuideTypes#38](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_5.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Cadeias de Caracteres de Formato Numérico Padrão](../../../standard/base-types/standard-numeric-format-strings.md)   
 [Tipos](../../../csharp/programming-guide/types/index.md)   
 [Como determinar se uma cadeia de caracteres representa um valor numérico](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)

