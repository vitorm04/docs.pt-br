---
title: 'Como: determinar se uma cadeia de caracteres representa um valor numérico – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: 831f0fc83c8a7066b40d64e4765a312b8b4847bc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921775"
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a>Como: determinar se uma cadeia de caracteres representa um valor numérico (Guia de Programação em C#)
Para determinar se uma cadeia de caracteres é uma representação válida de um tipo numérico especificado, use o método estático `TryParse` implementado por todos os tipos numéricos primitivos e também por tipos como <xref:System.DateTime> e <xref:System.Net.IPAddress>. O exemplo a seguir mostra como determinar se "108" é um [int](../../language-reference/builtin-types/integral-numeric-types.md) válido.  
  
```  
int i = 0;   
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 Se a cadeia de caracteres contiver caracteres não numéricos ou o valor numérico for muito grande ou muito pequeno para o tipo especificado, `TryParse` retornará false e definirá o parâmetro de saída como zero. Caso contrário, ele retornará true e definirá o parâmetro de saída como o valor numérico da cadeia de caracteres.  
  
> [!NOTE]
> Uma cadeia de caracteres pode conter apenas caracteres numéricos e ainda não ser válida para o método `TryParse` do tipo usado. Por exemplo, "256" não é um valor válido para `byte`, mas é válido para `int`. “98,6” não é um valor válido para `int`, mas é válido para `decimal`.  
  
## <a name="example"></a>Exemplo  
 Os exemplos a seguir mostram como usar `TryParse` com representações de cadeia de caracteres dos valores `long`, `byte` e `decimal`.  
  
 [!code-csharp[csProgGuideStrings#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#14)]  
  
## <a name="robust-programming"></a>Programação robusta  
 Os tipos numéricos primitivos também implementam o método estático `Parse`, que lançará uma exceção se a cadeia de caracteres não for um número válido. Geralmente, `TryParse` é mais eficiente, pois retornará false apenas se o número não for válido.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Sempre use os métodos `TryParse` ou `Parse` para validar entradas de usuário em controles como caixas de texto e caixas de combinação.  
  
## <a name="see-also"></a>Consulte também

- [Como: converter uma matriz de bytes em um int](../types/how-to-convert-a-byte-array-to-an-int.md)
- [Como: converter uma cadeia de caracteres em um número](../types/how-to-convert-a-string-to-a-number.md)
- [Como: converter entre cadeias de caracteres hexadecimais e tipos numéricos](../types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)
- [Analisando cadeias de caracteres numéricas](../../../standard/base-types/parsing-numeric.md)
- [Formatando Tipos](../../../standard/base-types/formatting-types.md)
