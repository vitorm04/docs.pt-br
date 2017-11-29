---
title: "Como determinar se uma cadeia de caracteres representa um valor numérico (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
caps.latest.revision: "9"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 850c5d0e7a246b2319ba841dae9884c90390d38c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
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
  
 [!code-csharp[csProgGuideStrings#14](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-determine-whether-a-string-represents-a-numeric-value_1.cs)]  
  
## <a name="robust-programming"></a>Programação robusta  
 Os tipos numéricos primitivos também implementam o método estático `Parse`, que lançará uma exceção se a cadeia de caracteres não for um número válido. Geralmente, `TryParse` é mais eficiente, pois retornará false apenas se o número não for válido.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Sempre use os métodos `TryParse` ou `Parse` para validar entradas de usuário em controles como caixas de texto e caixas de combinação.  
  
## <a name="see-also"></a>Consulte também  
 [Como converter uma matriz de bytes em um int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md)  
 [Como converter uma cadeia de caracteres em um número](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)  
 [Como converter entre cadeias de caracteres hexadecimais e tipos numéricos](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)  
 [Analisando cadeias de caracteres numéricas](../../../standard/base-types/parsing-numeric.md)  
 [Formatando Tipos](../../../standard/base-types/formatting-types.md)
