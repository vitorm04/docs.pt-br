---
title: Padrões ativos
description: Saiba como usar padrões ativos para definir partições nomeadas que subdividem dados de F# entrada na linguagem de programação.
ms.date: 05/16/2016
ms.openlocfilehash: f5ed4a8600cba10d23d01628aba6ca07e543c586
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425101"
---
# <a name="active-patterns"></a><span data-ttu-id="25e34-103">Padrões ativos</span><span class="sxs-lookup"><span data-stu-id="25e34-103">Active Patterns</span></span>

<span data-ttu-id="25e34-104">Os *padrões ativos* permitem que você defina partições nomeadas que subdividem dados de entrada, para que você possa usar esses nomes em uma expressão de correspondência de padrões, exatamente como faria para uma união discriminada.</span><span class="sxs-lookup"><span data-stu-id="25e34-104">*Active patterns* enable you to define named partitions that subdivide input data, so that you can use these names in a pattern matching expression just as you would for a discriminated union.</span></span> <span data-ttu-id="25e34-105">Você pode usar padrões ativos para decompor os dados de uma maneira personalizada para cada partição.</span><span class="sxs-lookup"><span data-stu-id="25e34-105">You can use active patterns to decompose data in a customized manner for each partition.</span></span>

## <a name="syntax"></a><span data-ttu-id="25e34-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="25e34-106">Syntax</span></span>

```fsharp
// Active pattern of one choice.
let (|identifier|) [arguments] valueToMatch= expression

// Active Pattern with multiple choices.
// Uses a FSharp.Core.Choice<_,...,_> based on the number of case names. In F#, the limitation n <= 7 applies.
let (|identifer1|identifier2|...|) valueToMatch = expression

// Partial active pattern definition.
// Uses a FSharp.Core.option<_> to represent if the type is satisfied at the call site.
let (|identifier|_|) [arguments ] valueToMatch = expression
```

## <a name="remarks"></a><span data-ttu-id="25e34-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="25e34-107">Remarks</span></span>

<span data-ttu-id="25e34-108">Na sintaxe anterior, os identificadores são nomes de partições dos dados de entrada que são representados por *argumentos*ou, em outras palavras, nomes para subconjuntos do conjunto de todos os valores dos argumentos.</span><span class="sxs-lookup"><span data-stu-id="25e34-108">In the previous syntax, the identifiers are names for partitions of the input data that is represented by *arguments*, or, in other words, names for subsets of the set of all values of the arguments.</span></span> <span data-ttu-id="25e34-109">Pode haver até sete partições em uma definição de padrão ativo.</span><span class="sxs-lookup"><span data-stu-id="25e34-109">There can be up to seven partitions in an active pattern definition.</span></span> <span data-ttu-id="25e34-110">A *expressão* descreve o formulário no qual os dados são decompostos.</span><span class="sxs-lookup"><span data-stu-id="25e34-110">The *expression* describes the form into which to decompose the data.</span></span> <span data-ttu-id="25e34-111">Você pode usar uma definição de padrão ativo para definir as regras para determinar a quais das partições nomeadas os valores fornecidos como argumentos pertencem.</span><span class="sxs-lookup"><span data-stu-id="25e34-111">You can use an active pattern definition to define the rules for determining which of the named partitions the values given as arguments belong to.</span></span> <span data-ttu-id="25e34-112">Os símbolos (| e |) são chamados de *clipes banana* e a função criada por esse tipo de associação de Let é chamada de *reconhecedor ativo*.</span><span class="sxs-lookup"><span data-stu-id="25e34-112">The (| and |) symbols are referred to as *banana clips* and the function created by this type of let binding is called an *active recognizer*.</span></span>

<span data-ttu-id="25e34-113">Como exemplo, considere o seguinte padrão ativo com um argumento.</span><span class="sxs-lookup"><span data-stu-id="25e34-113">As an example, consider the following active pattern with an argument.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

<span data-ttu-id="25e34-114">Você pode usar o padrão ativo em uma expressão de correspondência de padrões, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="25e34-114">You can use the active pattern in a pattern matching expression, as in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

<span data-ttu-id="25e34-115">A saída desse programa é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="25e34-115">The output of this program is as follows:</span></span>

```console
7 is odd
11 is odd
32 is even
```

<span data-ttu-id="25e34-116">Outro uso de padrões ativos é decompor tipos de dados de várias maneiras, como quando os mesmos dados subjacentes têm várias representações possíveis.</span><span class="sxs-lookup"><span data-stu-id="25e34-116">Another use of active patterns is to decompose data types in multiple ways, such as when the same underlying data has various possible representations.</span></span> <span data-ttu-id="25e34-117">Por exemplo, um objeto `Color` pode ser decomposto em uma representação RGB ou em uma representação HSB.</span><span class="sxs-lookup"><span data-stu-id="25e34-117">For example, a `Color` object could be decomposed into an RGB representation or an HSB representation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

<span data-ttu-id="25e34-118">A saída do programa acima é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="25e34-118">The output of the above program is as follows:</span></span>

```console
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

<span data-ttu-id="25e34-119">Em combinação, essas duas maneiras de usar padrões ativos permitem que você particione e decompoa dados apenas no formulário apropriado e execute os cálculos apropriados nos dados apropriados na forma mais conveniente para a computação.</span><span class="sxs-lookup"><span data-stu-id="25e34-119">In combination, these two ways of using active patterns enable you to partition and decompose data into just the appropriate form and perform the appropriate computations on the appropriate data in the form most convenient for the computation.</span></span>

<span data-ttu-id="25e34-120">As expressões de correspondência de padrões resultantes permitem que os dados sejam gravados de uma maneira conveniente que seja muito legível, simplificando bastante a ramificação potencialmente complexa e o código de análise de dados.</span><span class="sxs-lookup"><span data-stu-id="25e34-120">The resulting pattern matching expressions enable data to be written in a convenient way that is very readable, greatly simplifying potentially complex branching and data analysis code.</span></span>

## <a name="partial-active-patterns"></a><span data-ttu-id="25e34-121">Padrões ativos parciais</span><span class="sxs-lookup"><span data-stu-id="25e34-121">Partial Active Patterns</span></span>

<span data-ttu-id="25e34-122">Às vezes, você precisa particionar apenas parte do espaço de entrada.</span><span class="sxs-lookup"><span data-stu-id="25e34-122">Sometimes, you need to partition only part of the input space.</span></span> <span data-ttu-id="25e34-123">Nesse caso, você escreve um conjunto de padrões parciais, cada um dos quais corresponde a algumas entradas, mas não corresponde a outras entradas.</span><span class="sxs-lookup"><span data-stu-id="25e34-123">In that case, you write a set of partial patterns each of which match some inputs but fail to match other inputs.</span></span> <span data-ttu-id="25e34-124">Padrões ativos que nem sempre produzem um valor são chamados de *padrões ativos parciais*; Eles têm um valor de retorno que é um tipo de opção.</span><span class="sxs-lookup"><span data-stu-id="25e34-124">Active patterns that do not always produce a value are called *partial active patterns*; they have a return value that is an option type.</span></span> <span data-ttu-id="25e34-125">Para definir um padrão ativo parcial, use um caractere curinga (\_) no final da lista de padrões dentro dos clipes banana.</span><span class="sxs-lookup"><span data-stu-id="25e34-125">To define a partial active pattern, you use a wildcard character (\_) at the end of the list of patterns inside the banana clips.</span></span> <span data-ttu-id="25e34-126">O código a seguir ilustra o uso de um padrão ativo parcial.</span><span class="sxs-lookup"><span data-stu-id="25e34-126">The following code illustrates the use of a partial active pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

<span data-ttu-id="25e34-127">A saída do exemplo anterior é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="25e34-127">The output of the previous example is as follows:</span></span>

```console
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

<span data-ttu-id="25e34-128">Ao usar padrões ativos parciais, às vezes, as escolhas individuais podem ser separadas ou mutuamente exclusivas, mas não precisam ser.</span><span class="sxs-lookup"><span data-stu-id="25e34-128">When using partial active patterns, sometimes the individual choices can be disjoint or mutually exclusive, but they need not be.</span></span> <span data-ttu-id="25e34-129">No exemplo a seguir, o quadrado padrão e o cubo de padrão não são contíguos, pois alguns números são quadrados e cubos, como 64.</span><span class="sxs-lookup"><span data-stu-id="25e34-129">In the following example, the pattern Square and the pattern Cube are not disjoint, because some numbers are both squares and cubes, such as 64.</span></span> <span data-ttu-id="25e34-130">O programa a seguir usa o padrão e para combinar os padrões de cubo e quadrado.</span><span class="sxs-lookup"><span data-stu-id="25e34-130">The following program uses the AND pattern to combine the Square and Cube patterns.</span></span> <span data-ttu-id="25e34-131">Ele imprime todos os inteiros de até 1000 que são quadrados e cubos, bem como aqueles que são apenas cubos.</span><span class="sxs-lookup"><span data-stu-id="25e34-131">It print out all integers up to 1000 that are both squares and cubes, as well as those which are only cubes.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

<span data-ttu-id="25e34-132">A saída é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="25e34-132">The output is as follows:</span></span>

```console
1 is a cube and a square
8 is a cube
27 is a cube
64 is a cube and a square
125 is a cube
216 is a cube
343 is a cube
512 is a cube
729 is a cube and a square
1000 is a cube
```

## <a name="parameterized-active-patterns"></a><span data-ttu-id="25e34-133">Padrões ativos com parâmetros</span><span class="sxs-lookup"><span data-stu-id="25e34-133">Parameterized Active Patterns</span></span>

<span data-ttu-id="25e34-134">Os padrões ativos sempre recebem pelo menos um argumento para o item que está sendo correspondido, mas também podem levar argumentos adicionais; nesse caso, o nome *padrão ativo com parâmetros* se aplica.</span><span class="sxs-lookup"><span data-stu-id="25e34-134">Active patterns always take at least one argument for the item being matched, but they may take additional arguments as well, in which case the name *parameterized active pattern* applies.</span></span> <span data-ttu-id="25e34-135">Argumentos adicionais permitem que um padrão geral seja especializado.</span><span class="sxs-lookup"><span data-stu-id="25e34-135">Additional arguments allow a general pattern to be specialized.</span></span> <span data-ttu-id="25e34-136">Por exemplo, padrões ativos que usam expressões regulares para analisar cadeias de caracteres geralmente incluem a expressão regular como um parâmetro extra, como no código a seguir, que também usa o padrão ativo parcial `Integer` definido no exemplo de código anterior.</span><span class="sxs-lookup"><span data-stu-id="25e34-136">For example, active patterns that use regular expressions to parse strings often include the regular expression as an extra parameter, as in the following code, which also uses the partial active pattern `Integer` defined in the previous code example.</span></span> <span data-ttu-id="25e34-137">Neste exemplo, as cadeias de caracteres que usam expressões regulares para vários formatos de data são fornecidas para personalizar o padrão ativo ParseRegex geral.</span><span class="sxs-lookup"><span data-stu-id="25e34-137">In this example, strings that use regular expressions for various date formats are given to customize the general ParseRegex active pattern.</span></span> <span data-ttu-id="25e34-138">O padrão ativo inteiro é usado para converter as cadeias de caracteres correspondentes em números inteiros que podem ser passados para o Construtor DateTime.</span><span class="sxs-lookup"><span data-stu-id="25e34-138">The Integer active pattern is used to convert the matched strings into integers that can be passed to the DateTime constructor.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

<span data-ttu-id="25e34-139">A saída do código anterior é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="25e34-139">The output of the previous code is as follows:</span></span>

```console
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

<span data-ttu-id="25e34-140">Os padrões ativos não são restritos apenas às expressões de correspondência de padrões, você também pode usá-los em associações Let.</span><span class="sxs-lookup"><span data-stu-id="25e34-140">Active patterns are not restricted only to pattern matching expressions, you can also use them on let-bindings.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

<span data-ttu-id="25e34-141">A saída do código anterior é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="25e34-141">The output of the previous code is as follows:</span></span>

```console
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a><span data-ttu-id="25e34-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25e34-142">See also</span></span>

- [<span data-ttu-id="25e34-143">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="25e34-143">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="25e34-144">Expressões Match</span><span class="sxs-lookup"><span data-stu-id="25e34-144">Match Expressions</span></span>](match-expressions.md)
