---
description: switch (Referência em C#)
title: Instrução switch do C#
ms.date: 04/09/2019
f1_keywords:
- switch_CSharpKeyword
- switch
- case
- case_CSharpKeyword
helpviewer_keywords:
- switch statement [C#]
- switch keyword [C#]
- case statement [C#]
- default keyword [C#]
ms.assetid: 44bae8b8-8841-4d85-826b-8a94277daecb
ms.openlocfilehash: 20c1d9786eaa184088500cf1b37d33afc421b5e7
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142018"
---
# <a name="switch-c-reference"></a><span data-ttu-id="99fa6-103">switch (Referência em C#)</span><span class="sxs-lookup"><span data-stu-id="99fa6-103">switch (C# reference)</span></span>

<span data-ttu-id="99fa6-104">Este artigo aborda a `switch` instrução.</span><span class="sxs-lookup"><span data-stu-id="99fa6-104">This article covers the `switch` statement.</span></span> <span data-ttu-id="99fa6-105">Para obter informações sobre a `switch` expressão (introduzida no C# 8,0), consulte o artigo sobre [ `switch` expressões](../operators/switch-expression.md) na seção [expressões e operadores](../operators/index.md) .</span><span class="sxs-lookup"><span data-stu-id="99fa6-105">For information on the `switch` expression (introduced in C# 8.0), see the article on [`switch` expressions](../operators/switch-expression.md) in the [expressions and operators](../operators/index.md) section.</span></span>

<span data-ttu-id="99fa6-106">`switch` é uma instrução de seleção que escolhe uma única *seção de opção* para executar a partir de uma lista de candidatos com base em uma correspondência de padrão com a expressão de *correspondência*.</span><span class="sxs-lookup"><span data-stu-id="99fa6-106">`switch` is a selection statement that chooses a single *switch section* to execute from a list of candidates based on a pattern match with the *match expression*.</span></span>

[!code-csharp[switch#1](~/samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]

<span data-ttu-id="99fa6-107">A instrução `switch` geralmente é usada como uma alternativa para um constructo [if-else](if-else.md) se uma única expressão é testada com três ou mais condições.</span><span class="sxs-lookup"><span data-stu-id="99fa6-107">The `switch` statement is often used as an alternative to an [if-else](if-else.md) construct if a single expression is tested against three or more conditions.</span></span> <span data-ttu-id="99fa6-108">Por exemplo, a instrução `switch` a seguir determina se uma variável do tipo `Color` tem um dos três valores:</span><span class="sxs-lookup"><span data-stu-id="99fa6-108">For example, the following `switch` statement determines whether a variable of type `Color` has one of three values:</span></span>

[!code-csharp[switch#3](~/samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]

<span data-ttu-id="99fa6-109">Ela é equivalente ao exemplo a seguir que usa um constructo `if`-`else`.</span><span class="sxs-lookup"><span data-stu-id="99fa6-109">It's equivalent to the following example that uses an `if`-`else` construct.</span></span>

[!code-csharp[switch#3a](~/samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]

## <a name="the-match-expression"></a><span data-ttu-id="99fa6-110">A expressão de correspondência</span><span class="sxs-lookup"><span data-stu-id="99fa6-110">The match expression</span></span>

<span data-ttu-id="99fa6-111">A expressão de correspondência fornece o valor para corresponder aos padrões nos rótulos `case`.</span><span class="sxs-lookup"><span data-stu-id="99fa6-111">The match expression provides the value to match against the patterns in `case` labels.</span></span> <span data-ttu-id="99fa6-112">Sua sintaxe é:</span><span class="sxs-lookup"><span data-stu-id="99fa6-112">Its syntax is:</span></span>

```csharp
   switch (expr)
```

<span data-ttu-id="99fa6-113">No C# 6 e versões anteriores, a expressão de correspondência deve ser uma expressão que retorna um valor dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="99fa6-113">In C# 6 and earlier, the match expression must be an expression that returns a value of the following types:</span></span>

- <span data-ttu-id="99fa6-114">um [char](../builtin-types/char.md).</span><span class="sxs-lookup"><span data-stu-id="99fa6-114">a [char](../builtin-types/char.md).</span></span>
- <span data-ttu-id="99fa6-115">uma [cadeia de caracteres](../builtin-types/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="99fa6-115">a [string](../builtin-types/reference-types.md).</span></span>
- <span data-ttu-id="99fa6-116">um [bool](../builtin-types/bool.md).</span><span class="sxs-lookup"><span data-stu-id="99fa6-116">a [bool](../builtin-types/bool.md).</span></span>
- <span data-ttu-id="99fa6-117">um valor [integral](../builtin-types/integral-numeric-types.md) , como um `int` ou um `long` .</span><span class="sxs-lookup"><span data-stu-id="99fa6-117">an [integral](../builtin-types/integral-numeric-types.md) value, such as an `int` or a `long`.</span></span>
- <span data-ttu-id="99fa6-118">um valor de [Enumeração](../builtin-types/enum.md) .</span><span class="sxs-lookup"><span data-stu-id="99fa6-118">an [enum](../builtin-types/enum.md) value.</span></span>

<span data-ttu-id="99fa6-119">Começando com o C# 7.0, a expressão de correspondência pode ser qualquer expressão não nula.</span><span class="sxs-lookup"><span data-stu-id="99fa6-119">Starting with C# 7.0, the match expression can be any non-null expression.</span></span>

## <a name="the-switch-section"></a><span data-ttu-id="99fa6-120">A seção switch</span><span class="sxs-lookup"><span data-stu-id="99fa6-120">The switch section</span></span>

<span data-ttu-id="99fa6-121">Uma instrução `switch` inclui uma ou mais seções do comutador.</span><span class="sxs-lookup"><span data-stu-id="99fa6-121">A `switch` statement includes one or more switch sections.</span></span> <span data-ttu-id="99fa6-122">Cada seção do comutador contém um ou mais *Rótulos de caso* (um caso ou rótulo padrão) seguido por uma ou mais instruções.</span><span class="sxs-lookup"><span data-stu-id="99fa6-122">Each switch section contains one or more *case labels* (either a case or default label) followed by one or more statements.</span></span> <span data-ttu-id="99fa6-123">A instrução `switch` pode incluir no máximo um rótulo padrão colocado em qualquer seção switch.</span><span class="sxs-lookup"><span data-stu-id="99fa6-123">The `switch` statement may include at most one default label placed in any switch section.</span></span> <span data-ttu-id="99fa6-124">O exemplo a seguir mostra uma instrução `switch` simples que tem três seções switch, cada uma contendo duas instruções.</span><span class="sxs-lookup"><span data-stu-id="99fa6-124">The following example shows a simple `switch` statement that has three switch sections, each containing two statements.</span></span> <span data-ttu-id="99fa6-125">A segunda seção switch contém os rótulos `case 2:` e `case 3:`.</span><span class="sxs-lookup"><span data-stu-id="99fa6-125">The second switch section contains the `case 2:` and `case 3:` labels.</span></span>

<span data-ttu-id="99fa6-126">Uma instrução `switch` pode incluir qualquer número de seções switch e cada seção pode ter um ou mais rótulos case, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="99fa6-126">A `switch` statement can include any number of switch sections, and each section can have one or more case labels, as shown in the following example.</span></span> <span data-ttu-id="99fa6-127">No entanto, dois rótulos case não podem conter a mesma expressão.</span><span class="sxs-lookup"><span data-stu-id="99fa6-127">However, no two case labels may contain the same expression.</span></span>

[!code-csharp[switch#2](~/samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]

<span data-ttu-id="99fa6-128">Apenas uma seção switch em uma instrução switch é executada.</span><span class="sxs-lookup"><span data-stu-id="99fa6-128">Only one switch section in a switch statement executes.</span></span> <span data-ttu-id="99fa6-129">O C# não permite que a execução continue de uma seção switch para a próxima.</span><span class="sxs-lookup"><span data-stu-id="99fa6-129">C# doesn't allow execution to continue from one switch section to the next.</span></span> <span data-ttu-id="99fa6-130">Por isso, o código a seguir gera um erro do compilador, CS0163: "O controle não pode passar de um rótulo case (\<case label>) para outro".</span><span class="sxs-lookup"><span data-stu-id="99fa6-130">Because of this, the following code generates a compiler error, CS0163: "Control cannot fall through from one case label (\<case label>) to another."</span></span>

```csharp
switch (caseSwitch)
{
    // The following switch section causes an error.
    case 1:
        Console.WriteLine("Case 1...");
        // Add a break or other jump statement here.
    case 2:
        Console.WriteLine("... and/or Case 2");
        break;
}
```

<span data-ttu-id="99fa6-131">Esse requisito é atendido normalmente saindo explicitamente da seção switch usando uma instrução [break](break.md), [goto](goto.md) ou [return](return.md).</span><span class="sxs-lookup"><span data-stu-id="99fa6-131">This requirement is usually met by explicitly exiting the switch section by using a [break](break.md), [goto](goto.md), or [return](return.md) statement.</span></span> <span data-ttu-id="99fa6-132">No entanto, o código a seguir também é válido porque garante que o controle do programa não pode passar para a seção switch `default`.</span><span class="sxs-lookup"><span data-stu-id="99fa6-132">However, the following code is also valid, because it ensures that program control can't fall through to the `default` switch section.</span></span>

[!code-csharp[switch#4](~/samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]

<span data-ttu-id="99fa6-133">A execução da lista de instruções na seção switch com um rótulo case que corresponde à expressão de correspondência começa com a primeira instrução e continua pela lista de instruções, normalmente até uma instrução de salto como `break`, `goto case`, `goto label`, `return` ou `throw` ser atingida.</span><span class="sxs-lookup"><span data-stu-id="99fa6-133">Execution of the statement list in the switch section with a case label that matches the match expression begins with the first statement and proceeds through the statement list, typically until a jump statement, such as a `break`, `goto case`, `goto label`, `return`, or `throw`, is reached.</span></span> <span data-ttu-id="99fa6-134">Nesse ponto, o controle é transferido para fora da instrução `switch` ou para outro rótulo case.</span><span class="sxs-lookup"><span data-stu-id="99fa6-134">At that point, control is transferred outside the `switch` statement or to another case label.</span></span> <span data-ttu-id="99fa6-135">Se uma instrução `goto` for usada, ela deverá transferir controle para um rótulo de constante.</span><span class="sxs-lookup"><span data-stu-id="99fa6-135">A `goto` statement, if it's used, must transfer control to a constant label.</span></span> <span data-ttu-id="99fa6-136">Essa restrição é necessária, já que tentar transferir o controle para um rótulo não constante pode ter efeitos colaterais indesejáveis, tais como transferência do controle para um local não intencional no código ou criação de um loop infinito.</span><span class="sxs-lookup"><span data-stu-id="99fa6-136">This restriction is necessary, since attempting to transfer control to a non-constant label can have undesirable side-effects, such transferring control to an unintended location in code or creating an endless loop.</span></span>

## <a name="case-labels"></a><span data-ttu-id="99fa6-137">Rótulos case</span><span class="sxs-lookup"><span data-stu-id="99fa6-137">Case labels</span></span>

<span data-ttu-id="99fa6-138">Cada rótulo case especifica um padrão a ser comparado com a expressão de correspondência (a variável `caseSwitch` nos exemplos anteriores).</span><span class="sxs-lookup"><span data-stu-id="99fa6-138">Each case label specifies a pattern to compare to the match expression (the `caseSwitch` variable in the previous examples).</span></span> <span data-ttu-id="99fa6-139">Se eles corresponderem, o controle será transferido para a seção switch que contém o **primeiro** rótulo case correspondente.</span><span class="sxs-lookup"><span data-stu-id="99fa6-139">If they match, control is transferred to the switch section that contains the **first** matching case label.</span></span> <span data-ttu-id="99fa6-140">Se nenhum padrão de rótulo de caso corresponder à expressão de correspondência, o controle será transferido para a seção com o rótulo de caso `default`, se existir algum.</span><span class="sxs-lookup"><span data-stu-id="99fa6-140">If no case label pattern matches the match expression, control is transferred to the section with the `default` case label, if there's one.</span></span> <span data-ttu-id="99fa6-141">Se não houver nenhum case `default`, nenhuma declaração em qualquer seção switch será executada e o controle será transferido para fora da instrução `switch`.</span><span class="sxs-lookup"><span data-stu-id="99fa6-141">If there's no `default` case, no statements in any switch section are executed, and control is transferred outside the `switch` statement.</span></span>

<span data-ttu-id="99fa6-142">Para obter informações sobre a instrução `switch` e a correspondência de padrões, consulte a seção [Correspondência de padrões com a instrução `switch`](#pattern-matching with-the-switch-statement).</span><span class="sxs-lookup"><span data-stu-id="99fa6-142">For information on the `switch` statement and pattern matching, see the [Pattern matching with the `switch` statement](#pattern-matching with-the-switch-statement) section.</span></span>

<span data-ttu-id="99fa6-143">Como o C# 6 dá suporte apenas ao padrão de constante e não permite a repetição de valores de constantes, os rótulos case definem valores mutuamente exclusivos e apenas um padrão pode corresponder à expressão de correspondência.</span><span class="sxs-lookup"><span data-stu-id="99fa6-143">Because C# 6 supports only the constant pattern and doesn't allow the repetition of constant values, case labels define mutually exclusive values, and only one pattern can match the match expression.</span></span> <span data-ttu-id="99fa6-144">Como resultado, a ordem na qual as instruções `case` aparecem não é importante.</span><span class="sxs-lookup"><span data-stu-id="99fa6-144">As a result, the order in which `case` statements appear is unimportant.</span></span>

<span data-ttu-id="99fa6-145">No entanto, no C# 7.0, como há suporte para outros padrões, os rótulos case não precisam definir valores mutuamente exclusivos e vários padrões podem corresponder à expressão de correspondência.</span><span class="sxs-lookup"><span data-stu-id="99fa6-145">In C# 7.0, however, because other patterns are supported, case labels need not define mutually exclusive values, and multiple patterns can match the match expression.</span></span> <span data-ttu-id="99fa6-146">Como são executadas apenas as instruções na primeira seção switch que contém o primeiro padrão de correspondência, a ordem na qual as instruções `case` aparecem agora é importante.</span><span class="sxs-lookup"><span data-stu-id="99fa6-146">Because only the statements in the first switch section that contains the matching pattern are executed, the order in which `case` statements appear is now important.</span></span> <span data-ttu-id="99fa6-147">Se o C# detecta uma seção switch cujas instruções case são equivalentes ou são subconjuntos de instruções anteriores, ele gera um erro do compilador, CS8120, “O switch case já foi tratado por um case anterior”.</span><span class="sxs-lookup"><span data-stu-id="99fa6-147">If C# detects a switch section whose case statement or statements are equivalent to or are subsets of previous statements, it generates a compiler error, CS8120, "The switch case has already been handled by a previous case."</span></span>

<span data-ttu-id="99fa6-148">O exemplo a seguir ilustra uma instrução `switch` que usa uma variedade de padrões não mutuamente exclusivos.</span><span class="sxs-lookup"><span data-stu-id="99fa6-148">The following example illustrates a `switch` statement that uses a variety of non-mutually exclusive patterns.</span></span> <span data-ttu-id="99fa6-149">Se você mover a seção switch `case 0:` para que ela não seja mais a primeira seção na instrução `switch`, o C# gera um erro do compilador porque um inteiro cujo valor é zero é um subconjunto de todos os inteiros, que é o padrão definido pela instrução `case int val`.</span><span class="sxs-lookup"><span data-stu-id="99fa6-149">If you move the `case 0:` switch section so that it's no longer the first section in the `switch` statement, C# generates a compiler error because an integer whose value is zero is a subset of all integers, which is the pattern defined by the `case int val` statement.</span></span>

[!code-csharp[switch#5](~/samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]

<span data-ttu-id="99fa6-150">Você pode corrigir esse problema e eliminar o aviso do compilador em uma das duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="99fa6-150">You can correct this issue and eliminate the compiler warning in one of two ways:</span></span>

- <span data-ttu-id="99fa6-151">Alterando a ordem das seções switch.</span><span class="sxs-lookup"><span data-stu-id="99fa6-151">By changing the order of the switch sections.</span></span>

- <span data-ttu-id="99fa6-152">Usando uma [cláusula where](#the-case-statement-and-the-when-clause) no rótulo `case`.</span><span class="sxs-lookup"><span data-stu-id="99fa6-152">By using a [when clause](#the-case-statement-and-the-when-clause) in the `case` label.</span></span>

## <a name="the-default-case"></a><span data-ttu-id="99fa6-153">O case `default`</span><span class="sxs-lookup"><span data-stu-id="99fa6-153">The `default` case</span></span>

<span data-ttu-id="99fa6-154">O case `default` especifica a seção switch a ser executada se a expressão de correspondência não corresponder a nenhum outro rótulo `case`.</span><span class="sxs-lookup"><span data-stu-id="99fa6-154">The `default` case specifies the switch section to execute if the match expression doesn't match any other `case` label.</span></span> <span data-ttu-id="99fa6-155">Se um case `default` não estiver presente e a expressão de correspondência não corresponder a nenhum outro rótulo `case`, o fluxo do programa passará pela instrução `switch`.</span><span class="sxs-lookup"><span data-stu-id="99fa6-155">If a `default` case is not present and the match expression doesn't match any other `case` label, program flow falls through the `switch` statement.</span></span>

<span data-ttu-id="99fa6-156">O case `default` pode aparecer em qualquer ordem na instrução `switch`.</span><span class="sxs-lookup"><span data-stu-id="99fa6-156">The `default` case can appear in any order in the `switch` statement.</span></span> <span data-ttu-id="99fa6-157">Independentemente de sua ordem no código-fonte, ele é sempre avaliado por último, afinal os rótulos `case` foram avaliados.</span><span class="sxs-lookup"><span data-stu-id="99fa6-157">Regardless of its order in the source code, it's always evaluated last, after all `case` labels have been evaluated.</span></span>

## <a name="pattern-matching-with-the-switch-statement"></a><span data-ttu-id="99fa6-158"> Correspondência de padrões com a instrução `switch`</span><span class="sxs-lookup"><span data-stu-id="99fa6-158">Pattern matching with the `switch` statement</span></span>

<span data-ttu-id="99fa6-159">Cada instrução `case` define um padrão que, se corresponde à expressão de correspondência, faz com que sua seção switch recipiente seja executada.</span><span class="sxs-lookup"><span data-stu-id="99fa6-159">Each `case` statement defines a pattern that, if it matches the match expression, causes its  containing switch section to be executed.</span></span> <span data-ttu-id="99fa6-160">Todas as versões do C# dão suporte ao padrão de constante.</span><span class="sxs-lookup"><span data-stu-id="99fa6-160">All versions of C# support the constant pattern.</span></span> <span data-ttu-id="99fa6-161">Começando com o C# 7.0, há suporte para os padrões restantes.</span><span class="sxs-lookup"><span data-stu-id="99fa6-161">The remaining patterns are supported beginning with C# 7.0.</span></span>

### <a name="constant-pattern"></a><span data-ttu-id="99fa6-162">Padrão de constante</span><span class="sxs-lookup"><span data-stu-id="99fa6-162">Constant pattern</span></span>

<span data-ttu-id="99fa6-163">O padrão de constante testa se a expressão de correspondência é igual a uma constante especificada.</span><span class="sxs-lookup"><span data-stu-id="99fa6-163">The constant pattern tests whether the match expression equals a specified constant.</span></span> <span data-ttu-id="99fa6-164">Sua sintaxe é:</span><span class="sxs-lookup"><span data-stu-id="99fa6-164">Its syntax is:</span></span>

```csharp
   case constant:
```

<span data-ttu-id="99fa6-165">em que *constant* é o valor para testar.</span><span class="sxs-lookup"><span data-stu-id="99fa6-165">where *constant* is the value to test for.</span></span> <span data-ttu-id="99fa6-166">*constant* pode ser qualquer uma das expressões de constante a seguir:</span><span class="sxs-lookup"><span data-stu-id="99fa6-166">*constant* can be any of the following constant expressions:</span></span>

- <span data-ttu-id="99fa6-167">Um literal [bool](../builtin-types/bool.md) : `true` ou `false` .</span><span class="sxs-lookup"><span data-stu-id="99fa6-167">A [bool](../builtin-types/bool.md) literal: either `true` or `false`.</span></span>
- <span data-ttu-id="99fa6-168">Qualquer constante [integral](../builtin-types/integral-numeric-types.md) , como um `int` , um `long` ou um `byte` .</span><span class="sxs-lookup"><span data-stu-id="99fa6-168">Any [integral](../builtin-types/integral-numeric-types.md) constant, such as an `int`, a `long`, or a `byte`.</span></span>
- <span data-ttu-id="99fa6-169">O nome de uma variável `const` declarada.</span><span class="sxs-lookup"><span data-stu-id="99fa6-169">The name of a declared `const` variable.</span></span>
- <span data-ttu-id="99fa6-170">Uma constante de enumeração.</span><span class="sxs-lookup"><span data-stu-id="99fa6-170">An enumeration constant.</span></span>
- <span data-ttu-id="99fa6-171">Um literal [char](../builtin-types/char.md).</span><span class="sxs-lookup"><span data-stu-id="99fa6-171">A [char](../builtin-types/char.md) literal.</span></span>
- <span data-ttu-id="99fa6-172">Um literal [string](../builtin-types/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="99fa6-172">A [string](../builtin-types/reference-types.md) literal.</span></span>

<span data-ttu-id="99fa6-173">A expressão de constante é avaliada da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="99fa6-173">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="99fa6-174">Se *expr* e *constant* forem tipos integrais, o operador de igualdade de C# determinará se a expressão retorna `true` (ou seja, se `expr == constant`).</span><span class="sxs-lookup"><span data-stu-id="99fa6-174">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="99fa6-175">Caso contrário, o valor da expressão será determinado por uma chamada ao método estático [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)).</span><span class="sxs-lookup"><span data-stu-id="99fa6-175">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>

<span data-ttu-id="99fa6-176">O exemplo a seguir usa o padrão de constante para determinar se uma data específica é um final de semana, o primeiro dia, o último dia ou o meio da semana de trabalho.</span><span class="sxs-lookup"><span data-stu-id="99fa6-176">The following example uses the constant pattern to determine whether a particular date is a weekend, the first day of the work week, the last day of the work week, or the middle of the work week.</span></span> <span data-ttu-id="99fa6-177">Ele avalia a propriedade <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> do dia atual em relação aos membros da enumeração <xref:System.DayOfWeek>.</span><span class="sxs-lookup"><span data-stu-id="99fa6-177">It evaluates the <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> property of the current day against the members of the <xref:System.DayOfWeek> enumeration.</span></span>

[!code-csharp[switch#7](~/samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

<span data-ttu-id="99fa6-178">O exemplo a seguir usa o padrão de constante para manipular a entrada do usuário em um aplicativo de console que simula uma máquina de café automática.</span><span class="sxs-lookup"><span data-stu-id="99fa6-178">The following example uses the constant pattern to handle user input in a console application that simulates an automatic coffee machine.</span></span>

[!code-csharp[switch#6](~/samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]

### <a name="type-pattern"></a><span data-ttu-id="99fa6-179">Padrão de tipo</span><span class="sxs-lookup"><span data-stu-id="99fa6-179">Type pattern</span></span>

<span data-ttu-id="99fa6-180">O padrão de tipo permite a conversão e a avaliação do tipo concisa.</span><span class="sxs-lookup"><span data-stu-id="99fa6-180">The type pattern enables concise type evaluation and conversion.</span></span> <span data-ttu-id="99fa6-181">Quando usado com a instrução `switch` para realizar a correspondência de padrões, testa se uma expressão pode ser convertida para um tipo especificado e, se puder, o converte em uma variável desse tipo.</span><span class="sxs-lookup"><span data-stu-id="99fa6-181">When used with the `switch` statement to perform pattern matching, it tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="99fa6-182">Sua sintaxe é:</span><span class="sxs-lookup"><span data-stu-id="99fa6-182">Its syntax is:</span></span>

```csharp
   case type varname
```

<span data-ttu-id="99fa6-183">em que *type* é o nome do tipo no qual o resultado de *expr* deverá ser convertido e *varname* é o objeto para o qual o resultado de *expr* é convertido se a correspondência é bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="99fa6-183">where *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the match succeeds.</span></span> <span data-ttu-id="99fa6-184">O tipo de tempo de compilação *expr* pode ser um parâmetro de tipo genérico, começando com C# 7.1.</span><span class="sxs-lookup"><span data-stu-id="99fa6-184">The compile-time type of *expr* may be a generic type parameter, starting with C# 7.1.</span></span>

<span data-ttu-id="99fa6-185">A expressão `case` será `true` se qualquer uma das condições seguintes for verdadeira:</span><span class="sxs-lookup"><span data-stu-id="99fa6-185">The `case` expression is `true` if any of the following is true:</span></span>

- <span data-ttu-id="99fa6-186">*expr* for uma instância do mesmo tipo que *type*.</span><span class="sxs-lookup"><span data-stu-id="99fa6-186">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="99fa6-187">*expr* for uma instância de um tipo derivado de *type*.</span><span class="sxs-lookup"><span data-stu-id="99fa6-187">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="99fa6-188">Em outras palavras, o resultado de *expr* pode sofrer upcast para uma instância de *type*.</span><span class="sxs-lookup"><span data-stu-id="99fa6-188">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="99fa6-189">*expr* tem um tipo de tempo de compilação que é uma classe base de *type*, e *expr* tem um tipo de runtime que é *type* ou é derivado de *type*.</span><span class="sxs-lookup"><span data-stu-id="99fa6-189">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="99fa6-190">O *tipo do tempo de compilação* de uma variável é o tipo da variável conforme definido em sua declaração de tipo.</span><span class="sxs-lookup"><span data-stu-id="99fa6-190">The *compile-time type* of a variable is the variable's type as defined in its type declaration.</span></span> <span data-ttu-id="99fa6-191">O *tipo de runtime* de uma variável é o tipo da instância atribuída a essa variável.</span><span class="sxs-lookup"><span data-stu-id="99fa6-191">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="99fa6-192">*expr* é uma instância de um tipo que implementa a interface de *type*.</span><span class="sxs-lookup"><span data-stu-id="99fa6-192">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="99fa6-193">Se a expressão case for true, *varname* será definitivamente atribuído e terá o escopo local dentro da seção switch apenas.</span><span class="sxs-lookup"><span data-stu-id="99fa6-193">If the case expression is true, *varname* is definitely assigned and has local scope within the switch section only.</span></span>

<span data-ttu-id="99fa6-194">Observe que `null` não corresponde a um tipo.</span><span class="sxs-lookup"><span data-stu-id="99fa6-194">Note that `null` doesn't match a type.</span></span> <span data-ttu-id="99fa6-195">Para corresponder um `null`, use o seguinte rótulo `case`:</span><span class="sxs-lookup"><span data-stu-id="99fa6-195">To match a `null`, you use the following `case` label:</span></span>

```csharp
case null:
```

<span data-ttu-id="99fa6-196">O exemplo a seguir usa o padrão de tipo para fornecer informações sobre vários tipos de coleção.</span><span class="sxs-lookup"><span data-stu-id="99fa6-196">The following example uses the type pattern to provide information about various kinds of collection types.</span></span>

[!code-csharp[type-pattern#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

<span data-ttu-id="99fa6-197">Em vez de `object`, você poderia empregar um método genérico, usando o tipo da coleção como o parâmetro de tipo, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="99fa6-197">Instead of `object`, you could make a generic method, using the type of the collection as the type parameter, as shown in the following code:</span></span>

[!code-csharp[type-pattern#3](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern3.cs#1)]

<span data-ttu-id="99fa6-198">A versão genérica é diferente da primeira amostra de duas maneiras.</span><span class="sxs-lookup"><span data-stu-id="99fa6-198">The generic version is different than the first sample in two ways.</span></span> <span data-ttu-id="99fa6-199">Primeiro, você não pode usar o case `null`.</span><span class="sxs-lookup"><span data-stu-id="99fa6-199">First, you can't use the `null` case.</span></span> <span data-ttu-id="99fa6-200">Você não pode usar nenhum case constante porque o compilador não pode converter qualquer tipo arbitrário de `T` para qualquer tipo diferente de `object`.</span><span class="sxs-lookup"><span data-stu-id="99fa6-200">You can't use any constant case because the compiler can't convert any arbitrary type `T` to any type other than `object`.</span></span> <span data-ttu-id="99fa6-201">O que tinha sido o case `default` agora testa para um `object` não nulo.</span><span class="sxs-lookup"><span data-stu-id="99fa6-201">What had been the `default` case now tests for a non-null `object`.</span></span> <span data-ttu-id="99fa6-202">Isso significa que o case `default` testa apenas para `null`.</span><span class="sxs-lookup"><span data-stu-id="99fa6-202">That means the `default` case tests only for `null`.</span></span>

<span data-ttu-id="99fa6-203">Sem a correspondência de padrões, esse código pode ser escrito da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="99fa6-203">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="99fa6-204">O uso da correspondência de padrões de tipo produz um código mais compacto e legível eliminando a necessidade de testar se o resultado de uma conversão é um `null` ou executar conversões repetidas.</span><span class="sxs-lookup"><span data-stu-id="99fa6-204">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null` or to perform repeated casts.</span></span>

[!code-csharp[type-pattern2#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="the-case-statement-and-the-when-clause"></a><span data-ttu-id="99fa6-205">A instrução `case` e a cláusula `when`</span><span class="sxs-lookup"><span data-stu-id="99fa6-205">The `case` statement and the `when` clause</span></span>

<span data-ttu-id="99fa6-206">A partir do C# 7.0, como as instruções case não precisam ser mutuamente exclusivas, você pode usar a adição de uma cláusula `when` para especificar uma condição adicional que precisa ser atendida para que a instrução case seja avaliada como true.</span><span class="sxs-lookup"><span data-stu-id="99fa6-206">Starting with C# 7.0, because case statements need not be mutually exclusive, you can add a `when` clause to specify an additional condition that must be satisfied for the case statement to evaluate to true.</span></span> <span data-ttu-id="99fa6-207">A cláusula `when` pode ser qualquer expressão que retorna um valor booliano.</span><span class="sxs-lookup"><span data-stu-id="99fa6-207">The `when` clause can be any expression that returns a Boolean value.</span></span>

<span data-ttu-id="99fa6-208">O exemplo a seguir define uma classe `Shape` base, uma classe `Rectangle` que deriva de `Shape` e uma classe `Square` que deriva de `Rectangle`.</span><span class="sxs-lookup"><span data-stu-id="99fa6-208">The following example defines a base `Shape` class, a `Rectangle` class that derives from `Shape`, and a `Square` class that derives from `Rectangle`.</span></span> <span data-ttu-id="99fa6-209">Ele usa a cláusula `when` para garantir que o `ShowShapeInfo` trata um objeto `Rectangle` que recebeu comprimentos e larguras como um `Square` mesmo se ele não tiver sido instanciado como um objeto `Square`.</span><span class="sxs-lookup"><span data-stu-id="99fa6-209">It uses the `when` clause to ensure that the `ShowShapeInfo` treats a `Rectangle` object that has been assigned equal lengths and widths as a `Square` even if it hasn't been instantiated as a `Square` object.</span></span> <span data-ttu-id="99fa6-210">O método não tenta exibir informações sobre um objeto que é `null` ou uma forma cuja área é zero.</span><span class="sxs-lookup"><span data-stu-id="99fa6-210">The method doesn't attempt to display information either about an object that is `null` or a shape whose area is zero.</span></span>

[!code-csharp[when-clause#1](~/samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]

<span data-ttu-id="99fa6-211">Observe que a cláusula `when` no exemplo que tenta testar se um objeto `Shape` é `null` não é executada.</span><span class="sxs-lookup"><span data-stu-id="99fa6-211">Note that the `when` clause in the example that attempts to test whether a `Shape` object is `null` doesn't execute.</span></span> <span data-ttu-id="99fa6-212">O padrão de tipo correto para testar um `null` é `case null:`.</span><span class="sxs-lookup"><span data-stu-id="99fa6-212">The correct type pattern to test for a `null` is `case null:`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="99fa6-213">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="99fa6-213">C# language specification</span></span>

<span data-ttu-id="99fa6-214">Para obter mais informações, consulte [A instrução switch](~/_csharplang/spec/statements.md#the-switch-statement) na [Especificação da linguagem C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="99fa6-214">For more information, see [The switch statement](~/_csharplang/spec/statements.md#the-switch-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="99fa6-215">A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.</span><span class="sxs-lookup"><span data-stu-id="99fa6-215">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="99fa6-216">Confira também</span><span class="sxs-lookup"><span data-stu-id="99fa6-216">See also</span></span>

- [<span data-ttu-id="99fa6-217">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="99fa6-217">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="99fa6-218">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="99fa6-218">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="99fa6-219">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="99fa6-219">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="99fa6-220">if-else</span><span class="sxs-lookup"><span data-stu-id="99fa6-220">if-else</span></span>](if-else.md)
- [<span data-ttu-id="99fa6-221">Correspondência de padrões</span><span class="sxs-lookup"><span data-stu-id="99fa6-221">Pattern Matching</span></span>](../../pattern-matching.md)
