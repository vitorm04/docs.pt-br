---
title: "foreach, in (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- foreach
- foreach_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
caps.latest.revision: 29
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: aed1d4f086f0b1334df750fd912d20d66326a043
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="foreach-in-c-reference"></a>foreach, in (Referência de C#)
Uma instrução `foreach` repete um grupo de instruções inseridas para cada elemento em uma matriz ou coleção que implementa a interface <xref:System.Collections.IEnumerable?displayProperty=fullName> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>. A instrução `foreach` é usada para iterar na coleção para obter as informações que você deseja, mas não pode ser usada para adicionar ou remover itens da coleção de origem para evitar efeitos colaterais imprevisíveis. Se você precisar adicionar ou remover itens da coleção de origem, use um loop [for](../../../csharp/language-reference/keywords/for.md).  
  
 As instruções inseridas continuam em execução para cada elemento da matriz ou coleção. Após a iteração ter sido concluída para todos os elementos na coleção, o controle é transferido para a próxima instrução que segue o bloco `foreach`.  
  
 Em qualquer ponto dentro do bloco `foreach`, você pode sair do loop usando a palavra-chave [break](../../../csharp/language-reference/keywords/break.md) ou seguir para a próxima iteração no loop, usando a palavra-chave [continue](../../../csharp/language-reference/keywords/continue.md).  
  
 Um loop `foreach` também pode ser encerrado pelas instruções [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md) ou [throw](../../../csharp/language-reference/keywords/throw.md).  
  
 Para obter mais informações sobre a palavra-chave `foreach` e exemplos de códigos, consulte os seguintes tópicos:  
  
 [Usando foreach com matrizes](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
  
 [Como acessar uma classe de coleção com foreach](../../../csharp/programming-guide/classes-and-structs/how-to-access-a-collection-class-with-foreach.md)  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra três exemplos:  
  
-   um típico loop `foreach` que exibe o conteúdo de uma matriz de inteiros  
  
-   um loop [for](../../../csharp/language-reference/keywords/for.md), que faz a mesma coisa  
  
-   um loop `foreach` que mantém uma contagem do número de elementos na matriz  
  
 [!code-cs[csrefKeywordsIteration#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/foreach-in_1.cs)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md)   
 [Instruções de Iteração](../../../csharp/language-reference/keywords/iteration-statements.md)   
 [for](../../../csharp/language-reference/keywords/for.md)

