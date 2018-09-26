---
title: Padrões ativos (F#)
description: 'Saiba como usar padrões ativos para definir partições nomeadas que subdividem os dados de entrada a linguagem de programação F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 4fb7d3e2b9c7e6f1c1ed9d64a47728c7f40017c8
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47216741"
---
# <a name="active-patterns"></a><span data-ttu-id="c2cd1-103">Padrões ativos</span><span class="sxs-lookup"><span data-stu-id="c2cd1-103">Active Patterns</span></span>

<span data-ttu-id="c2cd1-104">*Padrões ativos* permitem definir partições nomeadas que subdividem os dados de entrada, para que você possa usar esses nomes em um padrão de expressão de correspondência de exatamente como você faria para uma união discriminada.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-104">*Active patterns* enable you to define named partitions that subdivide input data, so that you can use these names in a pattern matching expression just as you would for a discriminated union.</span></span> <span data-ttu-id="c2cd1-105">Você pode usar padrões ativos para decompor os dados de uma maneira personalizada para cada partição.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-105">You can use active patterns to decompose data in a customized manner for each partition.</span></span>

## <a name="syntax"></a><span data-ttu-id="c2cd1-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c2cd1-106">Syntax</span></span>

```fsharp
// Complete active pattern definition.
let (|identifer1|identifier2|...|) [ arguments ] = expression
// Partial active pattern definition.
let (|identifier|_|) [ arguments ] = expression
```

## <a name="remarks"></a><span data-ttu-id="c2cd1-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="c2cd1-107">Remarks</span></span>

<span data-ttu-id="c2cd1-108">Na sintaxe anterior, os identificadores são os nomes de partições de dados de entrada que são representados pela *argumentos*, ou, em outras palavras, os nomes de subconjuntos do conjunto de todos os valores dos argumentos.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-108">In the previous syntax, the identifiers are names for partitions of the input data that is represented by *arguments*, or, in other words, names for subsets of the set of all values of the arguments.</span></span> <span data-ttu-id="c2cd1-109">Pode haver até sete partições em uma definição de padrão ativo.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-109">There can be up to seven partitions in an active pattern definition.</span></span> <span data-ttu-id="c2cd1-110">O *expressão* descreve o formulário no qual a decompor os dados.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-110">The *expression* describes the form into which to decompose the data.</span></span> <span data-ttu-id="c2cd1-111">Você pode usar uma definição de padrão ativo para definir as regras para determinar quais partições nomeadas valores fornecidos como argumentos pertencem a.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-111">You can use an active pattern definition to define the rules for determining which of the named partitions the values given as arguments belong to.</span></span> <span data-ttu-id="c2cd1-112">O (| e |) símbolos são denominados *pipe* e é chamada de função criado por este tipo de associação let um *reconhecedor active*.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-112">The (| and |) symbols are referred to as *banana clips* and the function created by this type of let binding is called an *active recognizer*.</span></span>

<span data-ttu-id="c2cd1-113">Por exemplo, considere o seguinte padrão de Active Directory com um argumento.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-113">As an example, consider the following active pattern with an argument.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

<span data-ttu-id="c2cd1-114">Você pode usar o Active Directory padrão em um padrão de correspondência de expressão, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-114">You can use the active pattern in a pattern matching expression, as in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

<span data-ttu-id="c2cd1-115">A saída desse programa é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="c2cd1-115">The output of this program is as follows:</span></span>

```
7 is odd
11 is odd
32 is even
```

<span data-ttu-id="c2cd1-116">Outro uso dos padrões ativos é decompor os tipos de dados de várias maneiras, como quando os mesmos dados subjacentes tem diversas representações possíveis.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-116">Another use of active patterns is to decompose data types in multiple ways, such as when the same underlying data has various possible representations.</span></span> <span data-ttu-id="c2cd1-117">Por exemplo, um `Color` objeto pode ser decomposto em uma representação de RGB ou uma representação HSB.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-117">For example, a `Color` object could be decomposed into an RGB representation or an HSB representation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

<span data-ttu-id="c2cd1-118">A saída do programa acima é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="c2cd1-118">The output of the above program is as follows:</span></span>

```
Red
 Red: 255 Green: 0 Blue: 0
 Hue: 360.000000 Saturation: 1.000000 Brightness: 0.500000
Black
 Red: 0 Green: 0 Blue: 0
 Hue: 0.000000 Saturation: 0.000000 Brightness: 0.000000
White
 Red: 255 Green: 255 Blue: 255
 Hue: 0.000000 Saturation: 0.000000 Brightness: 1.000000
Gray
 Red: 128 Green: 128 Blue: 128
 Hue: 0.000000 Saturation: 0.000000 Brightness: 0.501961
BlanchedAlmond
 Red: 255 Green: 235 Blue: 205
 Hue: 36.000000 Saturation: 1.000000 Brightness: 0.901961
```

<span data-ttu-id="c2cd1-119">Em combinação, essas duas maneiras de usar padrões ativos permitem a partição e decompõem os dados em um formulário apropriado em executam os cálculos apropriados nos dados apropriados na forma mais conveniente para a computação.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-119">In combination, these two ways of using active patterns enable you to partition and decompose data into just the appropriate form and perform the appropriate computations on the appropriate data in the form most convenient for the computation.</span></span>

<span data-ttu-id="c2cd1-120">As expressões de correspondência de padrão resultante habilitar dados a serem gravados em uma maneira conveniente de ramificação potencialmente complexo muito legível, simplificando consideravelmente e o código de análise de dados.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-120">The resulting pattern matching expressions enable data to be written in a convenient way that is very readable, greatly simplifying potentially complex branching and data analysis code.</span></span>

## <a name="partial-active-patterns"></a><span data-ttu-id="c2cd1-121">Padrões ativos parciais</span><span class="sxs-lookup"><span data-stu-id="c2cd1-121">Partial Active Patterns</span></span>

<span data-ttu-id="c2cd1-122">Às vezes, você precisa apenas parte do espaço de entrada de partição.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-122">Sometimes, you need to partition only part of the input space.</span></span> <span data-ttu-id="c2cd1-123">Nesse caso, você escrever um conjunto de parciais padrões que corresponder algumas entradas, mas não corresponde a outras entradas.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-123">In that case, you write a set of partial patterns each of which match some inputs but fail to match other inputs.</span></span> <span data-ttu-id="c2cd1-124">Padrões ativos que não produzem um valor sempre são chamados *parciais padrões ativos*; eles têm um valor de retorno é um tipo de opção.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-124">Active patterns that do not always produce a value are called *partial active patterns*; they have a return value that is an option type.</span></span> <span data-ttu-id="c2cd1-125">Para definir um padrão ativo parcial, você pode usar um caractere curinga (\_) no final da lista de padrões de dentro do pipe.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-125">To define a partial active pattern, you use a wildcard character (\_) at the end of the list of patterns inside the banana clips.</span></span> <span data-ttu-id="c2cd1-126">O código a seguir ilustra o uso de um padrão ativo parcial.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-126">The following code illustrates the use of a partial active pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

<span data-ttu-id="c2cd1-127">A saída do exemplo anterior é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="c2cd1-127">The output of the previous example is as follows:</span></span>

```
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

<span data-ttu-id="c2cd1-128">Ao usar padrões ativos parciais, às vezes, as opções individuais podem ser contíguos ou mutuamente exclusivos, mas eles não precisam ser.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-128">When using partial active patterns, sometimes the individual choices can be disjoint or mutually exclusive, but they need not be.</span></span> <span data-ttu-id="c2cd1-129">No exemplo a seguir, o quadrado do padrão e o padrão de cubo não são não contíguos, porque alguns números são quadrados e cubos, como 64.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-129">In the following example, the pattern Square and the pattern Cube are not disjoint, because some numbers are both squares and cubes, such as 64.</span></span> <span data-ttu-id="c2cd1-130">O programa a seguir imprime todos os inteiros até 1000000 quadrados e cubos.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-130">The following program prints out all integers up to 1000000 that are both squares and cubes.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

<span data-ttu-id="c2cd1-131">A saída é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="c2cd1-131">The output is as follows:</span></span>

```
1
64
729
4096
15625
46656
117649
262144
531441
1000000
```

## <a name="parameterized-active-patterns"></a><span data-ttu-id="c2cd1-132">Padrões ativos com parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2cd1-132">Parameterized Active Patterns</span></span>

<span data-ttu-id="c2cd1-133">Padrões ativos sempre têm pelo menos um argumento para o item que está sendo correspondido, mas eles podem levar argumentos adicionais, bem, nesse caso, o nome *com parâmetros padrão ativo* se aplica.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-133">Active patterns always take at least one argument for the item being matched, but they may take additional arguments as well, in which case the name *parameterized active pattern* applies.</span></span> <span data-ttu-id="c2cd1-134">Argumentos adicionais permitem que um padrão geral ser especializados.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-134">Additional arguments allow a general pattern to be specialized.</span></span> <span data-ttu-id="c2cd1-135">Por exemplo, os padrões ativos que usam expressões regulares para analisar cadeias de caracteres geralmente incluem a expressão regular como um parâmetro extra, como no código a seguir, que também usa o padrão ativo parcial `Integer` definido no exemplo de código anterior.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-135">For example, active patterns that use regular expressions to parse strings often include the regular expression as an extra parameter, as in the following code, which also uses the partial active pattern `Integer` defined in the previous code example.</span></span> <span data-ttu-id="c2cd1-136">Neste exemplo, cadeias de caracteres que usam expressões regulares para vários formatos de data são fornecidas para personalizar o padrão do Active Directory de ParseRegex geral.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-136">In this example, strings that use regular expressions for various date formats are given to customize the general ParseRegex active pattern.</span></span> <span data-ttu-id="c2cd1-137">O padrão do Active Directory de inteiro é usado para converter as cadeias de caracteres correspondentes em números inteiros que podem ser passados ao construtor DateTime.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-137">The Integer active pattern is used to convert the matched strings into integers that can be passed to the DateTime constructor.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

<span data-ttu-id="c2cd1-138">A saída do código anterior é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="c2cd1-138">The output of the previous code is as follows:</span></span>

```
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

<span data-ttu-id="c2cd1-139">Padrões ativos não são restritos apenas a expressões de correspondência padrão, você também pode usá-los em associações permitem.</span><span class="sxs-lookup"><span data-stu-id="c2cd1-139">Active patterns are not restricted only to pattern matching expressions, you can also use them on let-bindings.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

<span data-ttu-id="c2cd1-140">A saída do código anterior é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="c2cd1-140">The output of the previous code is as follows:</span></span>

```
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a><span data-ttu-id="c2cd1-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c2cd1-141">See also</span></span>

- [<span data-ttu-id="c2cd1-142">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="c2cd1-142">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="c2cd1-143">Expressões Match</span><span class="sxs-lookup"><span data-stu-id="c2cd1-143">Match Expressions</span></span>](match-expressions.md)
