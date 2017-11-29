---
title: "Como concatenar várias cadeias de caracteres (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ca240523e2483289e11433fd58d9630a31721b33
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-concatenate-multiple-strings-c-programming-guide"></a>Como concatenar várias cadeias de caracteres (Guia de Programação em C#)
*Concatenação* é o processo de acrescentar uma cadeia de caracteres ao final de outra cadeia de caracteres. Ao concatenar literais ou constantes de cadeia de caracteres usando o operador `+`, o compilador cria uma única cadeia de caracteres. A concatenação em tempo de execução não ocorre. No entanto, as variáveis de cadeia de caracteres podem ser concatenadas somente em tempo de execução. Nesse caso, é necessário entender as implicações de desempenho das várias abordagens.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como dividir um literal de cadeia de caracteres longo em cadeias de caracteres menores, a fim de melhorar a legibilidade no código-fonte. Essas partes serão concatenadas em uma única cadeia de caracteres em tempo de compilação. Não há custos de desempenho em tempo de execução, independentemente da quantidade de cadeias de caracteres envolvidas.  
  
 [!code-csharp[csProgGuideStrings#30](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_1.cs)]  
  
## <a name="example"></a>Exemplo  
 Para concatenar variáveis de cadeia de caracteres, você pode usar os operadores `+` ou `+=`, ou então os métodos <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Format%2A?displayProperty=nameWithType> ou <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType>. O operador `+` é fácil de usar e torna o código intuitivo. Mesmo ao usar vários operadores + em uma instrução, o conteúdo da cadeia de caracteres será copiada apenas uma vez. Porém, se essa operação for repetida várias vezes, por exemplo, em um loop, problemas de eficiência poderão ocorrer. Por exemplo, observe o código a seguir:  
  
 [!code-csharp[csProgGuideStrings#23](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_2.cs)]  
  
> [!NOTE]
>  Em operações de concatenação de cadeia de caracteres, o compilador C# trata uma cadeia de caracteres nula da mesma maneira que uma cadeia de caracteres vazia, mas não converte o valor da cadeia de caracteres nula original.  
  
 Se você não estiver concatenando grandes quantidades de cadeias de caracteres (por exemplo, em um loop), o custo de desempenho provavelmente não será significativo. O mesmo é verdadeiro para os métodos <xref:System.String.Concat%2A?displayProperty=nameWithType> e <xref:System.String.Format%2A?displayProperty=nameWithType>.  
  
 No entanto, quando o desempenho for importante, sempre use a classe <xref:System.Text.StringBuilder> para concatenar cadeias de caracteres. O código a seguir usa o método <xref:System.Text.StringBuilder.Append%2A> da classe <xref:System.Text.StringBuilder> para concatenar cadeias de caracteres sem o efeito de encadeamento do operador `+`.  
  
 [!code-csharp[csProgGuideStrings#22](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_3.cs)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.String>  
 <xref:System.Text.StringBuilder>  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Cadeias de Caracteres](../../../csharp/programming-guide/strings/index.md)
