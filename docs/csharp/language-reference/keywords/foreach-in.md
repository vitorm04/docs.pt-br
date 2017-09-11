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
# <a name="foreach-in-c-reference"></a><span data-ttu-id="b7211-102">foreach, in (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="b7211-102">foreach, in (C# Reference)</span></span>
<span data-ttu-id="b7211-103">Uma instrução `foreach` repete um grupo de instruções inseridas para cada elemento em uma matriz ou coleção que implementa a interface <xref:System.Collections.IEnumerable?displayProperty=fullName> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="b7211-103">The `foreach` statement repeats a group of embedded statements for each element in an array or an object collection that implements the <xref:System.Collections.IEnumerable?displayProperty=fullName> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> interface.</span></span> <span data-ttu-id="b7211-104">A instrução `foreach` é usada para iterar na coleção para obter as informações que você deseja, mas não pode ser usada para adicionar ou remover itens da coleção de origem para evitar efeitos colaterais imprevisíveis.</span><span class="sxs-lookup"><span data-stu-id="b7211-104">The `foreach` statement is used to iterate through the collection to get the information that you want, but can not be used to add or remove items from the source collection to avoid unpredictable side effects.</span></span> <span data-ttu-id="b7211-105">Se você precisar adicionar ou remover itens da coleção de origem, use um loop [for](../../../csharp/language-reference/keywords/for.md).</span><span class="sxs-lookup"><span data-stu-id="b7211-105">If you need to add or remove items from the source collection, use a [for](../../../csharp/language-reference/keywords/for.md) loop.</span></span>  
  
 <span data-ttu-id="b7211-106">As instruções inseridas continuam em execução para cada elemento da matriz ou coleção.</span><span class="sxs-lookup"><span data-stu-id="b7211-106">The embedded statements continue to execute for each element in the array or collection.</span></span> <span data-ttu-id="b7211-107">Após a iteração ter sido concluída para todos os elementos na coleção, o controle é transferido para a próxima instrução que segue o bloco `foreach`.</span><span class="sxs-lookup"><span data-stu-id="b7211-107">After the iteration has been completed for all the elements in the collection, control is transferred to the next statement following the `foreach` block.</span></span>  
  
 <span data-ttu-id="b7211-108">Em qualquer ponto dentro do bloco `foreach`, você pode sair do loop usando a palavra-chave [break](../../../csharp/language-reference/keywords/break.md) ou seguir para a próxima iteração no loop, usando a palavra-chave [continue](../../../csharp/language-reference/keywords/continue.md).</span><span class="sxs-lookup"><span data-stu-id="b7211-108">At any point within the `foreach` block, you can break out of the loop by using the [break](../../../csharp/language-reference/keywords/break.md) keyword, or step to the next iteration in the loop by using the [continue](../../../csharp/language-reference/keywords/continue.md) keyword.</span></span>  
  
 <span data-ttu-id="b7211-109">Um loop `foreach` também pode ser encerrado pelas instruções [goto](../../../csharp/language-reference/keywords/goto.md), [retorn](../../../csharp/language-reference/keywords/return.md) ou [throw](../../../csharp/language-reference/keywords/throw.md).</span><span class="sxs-lookup"><span data-stu-id="b7211-109">A `foreach` loop can also be exited by the [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md), or [throw](../../../csharp/language-reference/keywords/throw.md) statements.</span></span>  
  
 <span data-ttu-id="b7211-110">Para obter mais informações sobre a palavra-chave `foreach` e exemplos de códigos, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="b7211-110">For more information about the `foreach` keyword and code samples, see the following topics:</span></span>  
  
 [<span data-ttu-id="b7211-111">Usando foreach com matrizes</span><span class="sxs-lookup"><span data-stu-id="b7211-111">Using foreach with Arrays</span></span>](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
  
 [<span data-ttu-id="b7211-112">Como acessar uma classe de coleção com foreach</span><span class="sxs-lookup"><span data-stu-id="b7211-112">How to: Access a Collection Class with foreach</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-access-a-collection-class-with-foreach.md)  
  
## <a name="example"></a><span data-ttu-id="b7211-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b7211-113">Example</span></span>  
 <span data-ttu-id="b7211-114">O código a seguir mostra três exemplos:</span><span class="sxs-lookup"><span data-stu-id="b7211-114">The following code shows three examples:</span></span>  
  
-   <span data-ttu-id="b7211-115">um típico loop `foreach` que exibe o conteúdo de uma matriz de inteiros</span><span class="sxs-lookup"><span data-stu-id="b7211-115">a typical `foreach` loop that displays the contents of an array of integers</span></span>  
  
-   <span data-ttu-id="b7211-116">um loop [for](../../../csharp/language-reference/keywords/for.md), que faz a mesma coisa</span><span class="sxs-lookup"><span data-stu-id="b7211-116">a [for](../../../csharp/language-reference/keywords/for.md) loop that does the same thing</span></span>  
  
-   <span data-ttu-id="b7211-117">um loop `foreach` que mantém uma contagem do número de elementos na matriz</span><span class="sxs-lookup"><span data-stu-id="b7211-117">a `foreach` loop that maintains a count of the number of elements in the array</span></span>  
  
 <span data-ttu-id="b7211-118">[!code-cs[csrefKeywordsIteration#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/foreach-in_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="b7211-118">[!code-cs[csrefKeywordsIteration#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/foreach-in_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="b7211-119">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="b7211-119">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b7211-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7211-120">See Also</span></span>  
 <span data-ttu-id="b7211-121">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="b7211-121">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="b7211-122">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="b7211-122">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="b7211-123">[Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="b7211-123">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="b7211-124">[Instruções de Iteração](../../../csharp/language-reference/keywords/iteration-statements.md) </span><span class="sxs-lookup"><span data-stu-id="b7211-124">[Iteration Statements](../../../csharp/language-reference/keywords/iteration-statements.md) </span></span>  
 [<span data-ttu-id="b7211-125">for</span><span class="sxs-lookup"><span data-stu-id="b7211-125">for</span></span>](../../../csharp/language-reference/keywords/for.md)

