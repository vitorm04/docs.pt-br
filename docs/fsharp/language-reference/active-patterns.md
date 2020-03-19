---
title: Padrões ativos
description: Aprenda a usar padrões ativos para definir partições nomeadas que subdividem dados de entrada na linguagem de programação F#.
ms.date: 05/16/2016
ms.openlocfilehash: 898ef201369683bfd49d53e863e86f919f5837fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187068"
---
# <a name="active-patterns"></a><span data-ttu-id="5bb38-103">Padrões ativos</span><span class="sxs-lookup"><span data-stu-id="5bb38-103">Active Patterns</span></span>

<span data-ttu-id="5bb38-104">*Padrões ativos* permitem definir partições nomeadas que subdividem dados de entrada, para que você possa usar esses nomes em uma expressão de correspondência de padrões, assim como você faria para uma união discriminada.</span><span class="sxs-lookup"><span data-stu-id="5bb38-104">*Active patterns* enable you to define named partitions that subdivide input data, so that you can use these names in a pattern matching expression just as you would for a discriminated union.</span></span> <span data-ttu-id="5bb38-105">Você pode usar padrões ativos para decompor os dados de uma maneira personalizada para cada partição.</span><span class="sxs-lookup"><span data-stu-id="5bb38-105">You can use active patterns to decompose data in a customized manner for each partition.</span></span>

## <a name="syntax"></a><span data-ttu-id="5bb38-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5bb38-106">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="5bb38-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="5bb38-107">Remarks</span></span>

<span data-ttu-id="5bb38-108">Na sintaxe anterior, os identificadores são nomes para partições dos dados de entrada que são representados por argumentos , ou, em *outras*palavras, nomes para subconjuntos do conjunto de todos os valores dos argumentos.</span><span class="sxs-lookup"><span data-stu-id="5bb38-108">In the previous syntax, the identifiers are names for partitions of the input data that is represented by *arguments*, or, in other words, names for subsets of the set of all values of the arguments.</span></span> <span data-ttu-id="5bb38-109">Pode haver até sete partições em uma definição de padrão ativo.</span><span class="sxs-lookup"><span data-stu-id="5bb38-109">There can be up to seven partitions in an active pattern definition.</span></span> <span data-ttu-id="5bb38-110">A *expressão* descreve a forma em que decompor os dados.</span><span class="sxs-lookup"><span data-stu-id="5bb38-110">The *expression* describes the form into which to decompose the data.</span></span> <span data-ttu-id="5bb38-111">Você pode usar uma definição de padrão ativo para definir as regras para determinar quais das partições nomeadas os valores dados como argumentos pertencem.</span><span class="sxs-lookup"><span data-stu-id="5bb38-111">You can use an active pattern definition to define the rules for determining which of the named partitions the values given as arguments belong to.</span></span> <span data-ttu-id="5bb38-112">Os símbolos (| e |) são chamados de *clipes* de banana e a função criada por esse tipo de vinculação de let é chamada de *reconhecedor ativo.*</span><span class="sxs-lookup"><span data-stu-id="5bb38-112">The (| and |) symbols are referred to as *banana clips* and the function created by this type of let binding is called an *active recognizer*.</span></span>

<span data-ttu-id="5bb38-113">Como exemplo, considere o seguinte padrão ativo com um argumento.</span><span class="sxs-lookup"><span data-stu-id="5bb38-113">As an example, consider the following active pattern with an argument.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

<span data-ttu-id="5bb38-114">Você pode usar o padrão ativo em uma expressão de correspondência de padrão, como no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="5bb38-114">You can use the active pattern in a pattern matching expression, as in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

<span data-ttu-id="5bb38-115">A saída deste programa é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="5bb38-115">The output of this program is as follows:</span></span>

```console
7 is odd
11 is odd
32 is even
```

<span data-ttu-id="5bb38-116">Outro uso de padrões ativos é decompor tipos de dados de várias maneiras, como quando os mesmos dados subjacentes têm várias representações possíveis.</span><span class="sxs-lookup"><span data-stu-id="5bb38-116">Another use of active patterns is to decompose data types in multiple ways, such as when the same underlying data has various possible representations.</span></span> <span data-ttu-id="5bb38-117">Por exemplo, `Color` um objeto pode ser decomposto em uma representação RGB ou uma representação HSB.</span><span class="sxs-lookup"><span data-stu-id="5bb38-117">For example, a `Color` object could be decomposed into an RGB representation or an HSB representation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

<span data-ttu-id="5bb38-118">A saída do programa acima é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="5bb38-118">The output of the above program is as follows:</span></span>

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

<span data-ttu-id="5bb38-119">Em combinação, essas duas maneiras de usar padrões ativos permitem que você particione e decomponha dados na forma apropriada e realize os cálculos apropriados sobre os dados apropriados na forma mais conveniente para a computação.</span><span class="sxs-lookup"><span data-stu-id="5bb38-119">In combination, these two ways of using active patterns enable you to partition and decompose data into just the appropriate form and perform the appropriate computations on the appropriate data in the form most convenient for the computation.</span></span>

<span data-ttu-id="5bb38-120">As expressões de correspondência de padrões resultantes permitem que os dados sejam escritos de forma conveniente, simplificando consideravelmente o código de ramificação e análise de dados potencialmente complexos.</span><span class="sxs-lookup"><span data-stu-id="5bb38-120">The resulting pattern matching expressions enable data to be written in a convenient way that is very readable, greatly simplifying potentially complex branching and data analysis code.</span></span>

## <a name="partial-active-patterns"></a><span data-ttu-id="5bb38-121">Padrões ativos parciais</span><span class="sxs-lookup"><span data-stu-id="5bb38-121">Partial Active Patterns</span></span>

<span data-ttu-id="5bb38-122">Às vezes, você precisa particionar apenas parte do espaço de entrada.</span><span class="sxs-lookup"><span data-stu-id="5bb38-122">Sometimes, you need to partition only part of the input space.</span></span> <span data-ttu-id="5bb38-123">Nesse caso, você escreve um conjunto de padrões parciais que correspondem a algumas entradas, mas não correspondem a outras entradas.</span><span class="sxs-lookup"><span data-stu-id="5bb38-123">In that case, you write a set of partial patterns each of which match some inputs but fail to match other inputs.</span></span> <span data-ttu-id="5bb38-124">Padrões ativos que nem sempre produzem um valor são chamados *de padrões ativos parciais;* eles têm um valor de retorno que é um tipo de opção.</span><span class="sxs-lookup"><span data-stu-id="5bb38-124">Active patterns that do not always produce a value are called *partial active patterns*; they have a return value that is an option type.</span></span> <span data-ttu-id="5bb38-125">Para definir um padrão ativo parcial, você\_usa um caractere curinga ( ) no final da lista de padrões dentro dos clipes de banana.</span><span class="sxs-lookup"><span data-stu-id="5bb38-125">To define a partial active pattern, you use a wildcard character (\_) at the end of the list of patterns inside the banana clips.</span></span> <span data-ttu-id="5bb38-126">O código a seguir ilustra o uso de um padrão ativo parcial.</span><span class="sxs-lookup"><span data-stu-id="5bb38-126">The following code illustrates the use of a partial active pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

<span data-ttu-id="5bb38-127">A saída do exemplo anterior é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="5bb38-127">The output of the previous example is as follows:</span></span>

```console
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

<span data-ttu-id="5bb38-128">Ao usar padrões ativos parciais, às vezes as escolhas individuais podem ser desarticuladas ou mutuamente exclusivas, mas não precisam ser.</span><span class="sxs-lookup"><span data-stu-id="5bb38-128">When using partial active patterns, sometimes the individual choices can be disjoint or mutually exclusive, but they need not be.</span></span> <span data-ttu-id="5bb38-129">No exemplo a seguir, o padrão Quadrado e o padrão Cubo não são desarticulados, pois alguns números são quadrados e cubos, como 64.</span><span class="sxs-lookup"><span data-stu-id="5bb38-129">In the following example, the pattern Square and the pattern Cube are not disjoint, because some numbers are both squares and cubes, such as 64.</span></span> <span data-ttu-id="5bb38-130">O programa a seguir usa o padrão E para combinar os padrões Quadrado e Cubo.</span><span class="sxs-lookup"><span data-stu-id="5bb38-130">The following program uses the AND pattern to combine the Square and Cube patterns.</span></span> <span data-ttu-id="5bb38-131">Ele imprime todos os inteiros até 1000 que são quadrados e cubos, bem como aqueles que são apenas cubos.</span><span class="sxs-lookup"><span data-stu-id="5bb38-131">It prints out all integers up to 1000 that are both squares and cubes, as well as those which are only cubes.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

<span data-ttu-id="5bb38-132">A saída é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="5bb38-132">The output is as follows:</span></span>

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

## <a name="parameterized-active-patterns"></a><span data-ttu-id="5bb38-133">Padrões ativos parametrizados</span><span class="sxs-lookup"><span data-stu-id="5bb38-133">Parameterized Active Patterns</span></span>

<span data-ttu-id="5bb38-134">Padrões ativos sempre levam pelo menos um argumento para que o item seja correspondido, mas eles podem ter argumentos adicionais também, nesse caso o *padrão ativo parametrizado* do nome se aplica.</span><span class="sxs-lookup"><span data-stu-id="5bb38-134">Active patterns always take at least one argument for the item being matched, but they may take additional arguments as well, in which case the name *parameterized active pattern* applies.</span></span> <span data-ttu-id="5bb38-135">Argumentos adicionais permitem que um padrão geral seja especializado.</span><span class="sxs-lookup"><span data-stu-id="5bb38-135">Additional arguments allow a general pattern to be specialized.</span></span> <span data-ttu-id="5bb38-136">Por exemplo, padrões ativos que usam expressões regulares para analisar as cordas geralmente incluem a expressão regular como `Integer` um parâmetro extra, como no código a seguir, que também usa o padrão ativo parcial definido no exemplo de código anterior.</span><span class="sxs-lookup"><span data-stu-id="5bb38-136">For example, active patterns that use regular expressions to parse strings often include the regular expression as an extra parameter, as in the following code, which also uses the partial active pattern `Integer` defined in the previous code example.</span></span> <span data-ttu-id="5bb38-137">Neste exemplo, as strings que usam expressões regulares para vários formatos de data são dadas para personalizar o padrão ativo geral Do ParseRegex.</span><span class="sxs-lookup"><span data-stu-id="5bb38-137">In this example, strings that use regular expressions for various date formats are given to customize the general ParseRegex active pattern.</span></span> <span data-ttu-id="5bb38-138">O padrão ativo Integer é usado para converter as strings combinadas em inteiros que podem ser passados para o construtor DateTime.</span><span class="sxs-lookup"><span data-stu-id="5bb38-138">The Integer active pattern is used to convert the matched strings into integers that can be passed to the DateTime constructor.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

<span data-ttu-id="5bb38-139">A saída do código anterior é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="5bb38-139">The output of the previous code is as follows:</span></span>

```console
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

<span data-ttu-id="5bb38-140">Os padrões ativos não estão restritos apenas às expressões de correspondência de padrões, você também pode usá-los em let-bindings.</span><span class="sxs-lookup"><span data-stu-id="5bb38-140">Active patterns are not restricted only to pattern matching expressions, you can also use them on let-bindings.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

<span data-ttu-id="5bb38-141">A saída do código anterior é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="5bb38-141">The output of the previous code is as follows:</span></span>

```console
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a><span data-ttu-id="5bb38-142">Confira também</span><span class="sxs-lookup"><span data-stu-id="5bb38-142">See also</span></span>

- [<span data-ttu-id="5bb38-143">Referência de idioma F#</span><span class="sxs-lookup"><span data-stu-id="5bb38-143">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="5bb38-144">Expressões de correspondência</span><span class="sxs-lookup"><span data-stu-id="5bb38-144">Match Expressions</span></span>](match-expressions.md)
