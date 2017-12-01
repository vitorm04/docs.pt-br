---
title: "foreach, in (Referência de C#)"
ms.date: 10/11/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
caps.latest.revision: "29"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d5601682d53a01ff07aba7e416aa81ded4c03e4e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="foreach-in-c-reference"></a>foreach, in (Referência de C#)
Uma instrução `foreach` repete um grupo de instruções inseridas para cada elemento em uma matriz ou coleção que implementa a interface <xref:System.Collections.IEnumerable?displayProperty=nameWithType> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>. A instrução `foreach` é usada para iterar na coleção para obter as informações que você deseja, mas não pode ser usada para adicionar ou remover itens da coleção de origem para evitar efeitos colaterais imprevisíveis. Se você precisar adicionar ou remover itens da coleção de origem, use um loop [for](for.md).
  
 As instruções inseridas continuam em execução para cada elemento da matriz ou coleção. Após a iteração ter sido concluída para todos os elementos na coleção, o controle é transferido para a próxima instrução que segue o bloco `foreach`.
  
 Em qualquer ponto dentro do bloco `foreach`, você pode sair do loop usando a palavra-chave [break](break.md) ou seguir para a próxima iteração no loop, usando a palavra-chave [continue](continue.md).

 Um loop `foreach` também pode ser encerrado pelas instruções [goto](goto.md), [retorn](return.md) ou [throw](throw.md).

 Para obter mais informações sobre a palavra-chave `foreach` e exemplos de códigos, consulte os seguintes tópicos:  

 [Usando foreach com matrizes](../../programming-guide/arrays/using-foreach-with-arrays.md)  

 [Como acessar uma classe de coleção com foreach](../../programming-guide/classes-and-structs/how-to-access-a-collection-class-with-foreach.md)  

## <a name="example"></a>Exemplo
 O código a seguir mostra três exemplos.

> [!TIP]
> Você pode modificar os exemplos para fazer experiências com a sintaxe e tente usos diferentes que são mais semelhantes ao seu caso de uso. Pressione "Executar" para executar o código, em seguida, editar e pressione "Executar" novamente.

-   um típico loop `foreach` que exibe o conteúdo de uma matriz de inteiros

[!code-csharp-interactive[csrefKeywordsIteration#4](./codesnippet/CSharp/foreach-in_1.cs#L12-L26)]

-   um loop [for](../../../csharp/language-reference/keywords/for.md), que faz a mesma coisa

[!code-csharp-interactive[csrefKeywordsIteration#4](./codesnippet/CSharp/foreach-in_1.cs#L31-L46)]

-   um loop `foreach` que mantém uma contagem do número de elementos na matriz

[!code-csharp-interactive[csrefKeywordsIteration#4](./codesnippet/CSharp/foreach-in_1.cs#L51-L69)]
 
## <a name="c-language-specification"></a>Especificação da Linguagem C#
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também  

[Referência de C#](../index.md)

[Guia de Programação em C#](../../programming-guide/index.md)

[Palavras-chave do C#](index.md)

[Instruções de iteração](iteration-statements.md)

[for](for.md)
