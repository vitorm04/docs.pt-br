---
title: "Como Determinar se uma Cadeia de Caracteres Representa um Valor Numérico (Guia de Programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
caps.latest.revision: 9
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
ms.openlocfilehash: 343e7304a83f396b8bdcc9c92e9123eed206be56
ms.contentlocale: pt-br
ms.lasthandoff: 05/10/2017

---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a>Como determinar se uma cadeia de caracteres representa um valor numérico (Guia de Programação em C#)
Para determinar se uma cadeia de caracteres é uma representação válida de um tipo numérico especificado, use o método estático `TryParse` implementado por todos os tipos numéricos primitivos e também por tipos como <xref:System.DateTime> e <xref:System.Net.IPAddress>. O exemplo a seguir mostra como determinar se "108" é um [int](../../../csharp/language-reference/keywords/int.md) válido.  
  
```  
int i = 0;   
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 Se a cadeia de caracteres contiver caracteres não numéricos ou o valor numérico for muito grande ou muito pequeno para o tipo especificado, `TryParse` retornará false e definirá o parâmetro de saída como zero. Caso contrário, ele retornará true e definirá o parâmetro de saída como o valor numérico da cadeia de caracteres.  
  
> [!NOTE]
>  Uma cadeia de caracteres pode conter apenas caracteres numéricos e ainda não ser válida para o método `TryParse` do tipo usado. Por exemplo, "256" não é um valor válido para `byte`, mas é válido para `int`. “98,6” não é um valor válido para `int`, mas é válido para `decimal`.  
  
## <a name="example"></a>Exemplo  
 Os exemplos a seguir mostram como usar `TryParse` com representações de cadeia de caracteres dos valores `long`, `byte` e `decimal`.  
  
 [!code-cs[csProgGuideStrings#14](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-determine-whether-a-string-represents-a-numeric-value_1.cs)]  
  
## <a name="robust-programming"></a>Programação robusta  
 Os tipos numéricos primitivos também implementam o método estático `Parse`, que lançará uma exceção se a cadeia de caracteres não for um número válido. Geralmente, `TryParse` é mais eficiente, pois retornará false apenas se o número não for válido.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Sempre use os métodos `TryParse` ou `Parse` para validar entradas de usuário em controles como caixas de texto e caixas de combinação.  
  
## <a name="see-also"></a>Consulte também  
 [Como Converter uma Matriz de Bytes em um int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md)   
 [Como Converter uma Cadeia de Caracteres em um Número](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)   
 [Como Converter entre Cadeias de Caracteres Hexadecimais e Tipos Numéricos](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)   
 [Analisando Cadeias de Caracteres Numéricas](../../../standard/base-types/parsing-numeric.md)   
 [Formatando Tipos](../../../standard/base-types/formatting-types.md)
