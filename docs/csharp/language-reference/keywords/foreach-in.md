---
title: foreach, in (Referência de C#)
ms.date: 10/11/2017
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: f00ae873e615f653d3e760f82b157a57fdaef6ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="d314a-102">foreach, in (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="d314a-102">foreach, in (C# Reference)</span></span>
<span data-ttu-id="d314a-103">Uma instrução `foreach` repete um grupo de instruções inseridas para cada elemento em uma matriz ou coleção que implementa a interface <xref:System.Collections.IEnumerable?displayProperty=nameWithType> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d314a-103">The `foreach` statement repeats a group of embedded statements for each element in an array or an object collection that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="d314a-104">A instrução `foreach` é usada para iterar na coleção para obter as informações que você deseja, mas não pode ser usada para adicionar ou remover itens da coleção de origem para evitar efeitos colaterais imprevisíveis.</span><span class="sxs-lookup"><span data-stu-id="d314a-104">The `foreach` statement is used to iterate through the collection to get the information that you want, but can not be used to add or remove items from the source collection to avoid unpredictable side effects.</span></span> <span data-ttu-id="d314a-105">Se você precisar adicionar ou remover itens da coleção de origem, use um loop [for](for.md).</span><span class="sxs-lookup"><span data-stu-id="d314a-105">If you need to add or remove items from the source collection, use a [for](for.md) loop.</span></span>
  
 <span data-ttu-id="d314a-106">As instruções inseridas continuam em execução para cada elemento da matriz ou coleção.</span><span class="sxs-lookup"><span data-stu-id="d314a-106">The embedded statements continue to execute for each element in the array or collection.</span></span> <span data-ttu-id="d314a-107">Após a iteração ter sido concluída para todos os elementos na coleção, o controle é transferido para a próxima instrução que segue o bloco `foreach`.</span><span class="sxs-lookup"><span data-stu-id="d314a-107">After the iteration has been completed for all the elements in the collection, control is transferred to the next statement following the `foreach` block.</span></span>
  
 <span data-ttu-id="d314a-108">Em qualquer ponto dentro do bloco `foreach`, você pode sair do loop usando a palavra-chave [break](break.md) ou seguir para a próxima iteração no loop, usando a palavra-chave [continue](continue.md).</span><span class="sxs-lookup"><span data-stu-id="d314a-108">At any point within the `foreach` block, you can break out of the loop by using the [break](break.md) keyword, or step to the next iteration in the loop by using the [continue](continue.md) keyword.</span></span>

 <span data-ttu-id="d314a-109">Um loop `foreach` também pode ser encerrado pelas instruções [goto](goto.md), [retorn](return.md) ou [throw](throw.md).</span><span class="sxs-lookup"><span data-stu-id="d314a-109">A `foreach` loop can also be exited by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

 <span data-ttu-id="d314a-110">Para obter mais informações sobre a palavra-chave `foreach` e exemplos de códigos, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="d314a-110">For more information about the `foreach` keyword and code samples, see the following topics:</span></span>  

 [<span data-ttu-id="d314a-111">Usando foreach com matrizes</span><span class="sxs-lookup"><span data-stu-id="d314a-111">Using foreach with Arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)  

 [<span data-ttu-id="d314a-112">Como acessar uma classe de coleção com foreach</span><span class="sxs-lookup"><span data-stu-id="d314a-112">How to: Access a Collection Class with foreach</span></span>](../../programming-guide/classes-and-structs/how-to-access-a-collection-class-with-foreach.md)  

## <a name="example"></a><span data-ttu-id="d314a-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d314a-113">Example</span></span>
 <span data-ttu-id="d314a-114">O código a seguir mostra três exemplos.</span><span class="sxs-lookup"><span data-stu-id="d314a-114">The following code shows three examples.</span></span>

> [!TIP]
> <span data-ttu-id="d314a-115">Você pode modificar os exemplos para fazer experimentos com a sintaxe e tentar usos diferentes que são mais semelhantes ao seu caso de uso.</span><span class="sxs-lookup"><span data-stu-id="d314a-115">You can modify the examples to experiment with the syntax and try different usages that are more similar to your use case.</span></span> <span data-ttu-id="d314a-116">Pressione "Executar" para executar o código e, em seguida, edite-o e pressione "Executar" novamente.</span><span class="sxs-lookup"><span data-stu-id="d314a-116">Press "Run" to run the code, then edit and press "Run" again.</span></span>

-   <span data-ttu-id="d314a-117">um típico loop `foreach` que exibe o conteúdo de uma matriz de inteiros</span><span class="sxs-lookup"><span data-stu-id="d314a-117">a typical `foreach` loop that displays the contents of an array of integers</span></span>

[!code-csharp-interactive[csrefKeywordsIteration#4](./codesnippet/CSharp/foreach-in_1.cs#L12-L26)]

-   <span data-ttu-id="d314a-118">um loop [for](../../../csharp/language-reference/keywords/for.md), que faz a mesma coisa</span><span class="sxs-lookup"><span data-stu-id="d314a-118">a [for](../../../csharp/language-reference/keywords/for.md) loop that does the same thing</span></span>

[!code-csharp-interactive[csrefKeywordsIteration#4](./codesnippet/CSharp/foreach-in_1.cs#L31-L46)]

-   <span data-ttu-id="d314a-119">um loop `foreach` que mantém uma contagem do número de elementos na matriz</span><span class="sxs-lookup"><span data-stu-id="d314a-119">a `foreach` loop that maintains a count of the number of elements in the array</span></span>

[!code-csharp-interactive[csrefKeywordsIteration#4](./codesnippet/CSharp/foreach-in_1.cs#L51-L69)]
 
## <a name="c-language-specification"></a><span data-ttu-id="d314a-120">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="d314a-120">C# Language Specification</span></span>
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="d314a-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d314a-121">See Also</span></span>  

[<span data-ttu-id="d314a-122">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="d314a-122">C# Reference</span></span>](../index.md)

[<span data-ttu-id="d314a-123">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="d314a-123">C# Programming Guide</span></span>](../../programming-guide/index.md)

[<span data-ttu-id="d314a-124">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="d314a-124">C# Keywords</span></span>](index.md)

[<span data-ttu-id="d314a-125">Instruções de iteração</span><span class="sxs-lookup"><span data-stu-id="d314a-125">Iteration Statements</span></span>](iteration-statements.md)

[<span data-ttu-id="d314a-126">for</span><span class="sxs-lookup"><span data-stu-id="d314a-126">for</span></span>](for.md)
