---
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
ms.openlocfilehash: 9335399be2d4909a02fecbf2959c6f5608664732
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493663"
---
# <a name="switch-c-reference"></a><span data-ttu-id="8ec1f-102">switch (Referência em C#)</span><span class="sxs-lookup"><span data-stu-id="8ec1f-102">switch (C# reference)</span></span>

<span data-ttu-id="8ec1f-103">Este artigo aborda a `switch` instrução.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-103">This article covers the `switch` statement.</span></span> <span data-ttu-id="8ec1f-104">Para obter informações sobre a `switch` expressão (introduzida no C# 8,0), consulte o artigo sobre [ `switch` expressões](../operators/switch-expression.md) na seção [expressões e operadores](../operators/index.md) .</span><span class="sxs-lookup"><span data-stu-id="8ec1f-104">For information on the `switch` expression (introduced in C# 8.0), see the article on [`switch` expressions](../operators/switch-expression.md) in the [expressions and operators](../operators/index.md) section.</span></span>

<span data-ttu-id="8ec1f-105">`switch` é uma instrução de seleção que escolhe uma única *seção switch* para ser executada de uma lista de candidatas com base em uma correspondência de padrão com a *expressão de correspondência*.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-105">`switch` is a selection statement that chooses a single *switch section* to execute from a list of candidates based on a pattern match with the *match expression*.</span></span>

[!code-csharp[switch#1](~/samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]

<span data-ttu-id="8ec1f-106">A instrução `switch` geralmente é usada como uma alternativa para um constructo [if-else](if-else.md) se uma única expressão é testada com três ou mais condições.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-106">The `switch` statement is often used as an alternative to an [if-else](if-else.md) construct if a single expression is tested against three or more conditions.</span></span> <span data-ttu-id="8ec1f-107">Por exemplo, a instrução `switch` a seguir determina se uma variável do tipo `Color` tem um dos três valores:</span><span class="sxs-lookup"><span data-stu-id="8ec1f-107">For example, the following `switch` statement determines whether a variable of type `Color` has one of three values:</span></span>

[!code-csharp[switch#3](~/samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]

<span data-ttu-id="8ec1f-108">Ela é equivalente ao exemplo a seguir que usa um constructo `if`-`else`.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-108">It's equivalent to the following example that uses an `if`-`else` construct.</span></span>

[!code-csharp[switch#3a](~/samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]

## <a name="the-match-expression"></a><span data-ttu-id="8ec1f-109">A expressão de correspondência</span><span class="sxs-lookup"><span data-stu-id="8ec1f-109">The match expression</span></span>

<span data-ttu-id="8ec1f-110">A expressão de correspondência fornece o valor para corresponder aos padrões nos rótulos `case`.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-110">The match expression provides the value to match against the patterns in `case` labels.</span></span> <span data-ttu-id="8ec1f-111">Sua sintaxe é:</span><span class="sxs-lookup"><span data-stu-id="8ec1f-111">Its syntax is:</span></span>

```csharp
   switch (expr)
```

<span data-ttu-id="8ec1f-112">No C# 6 e versões anteriores, a expressão de correspondência deve ser uma expressão que retorna um valor dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="8ec1f-112">In C# 6 and earlier, the match expression must be an expression that returns a value of the following types:</span></span>

- <span data-ttu-id="8ec1f-113">um [char](../builtin-types/char.md).</span><span class="sxs-lookup"><span data-stu-id="8ec1f-113">a [char](../builtin-types/char.md).</span></span>
- <span data-ttu-id="8ec1f-114">uma [cadeia de caracteres](../builtin-types/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="8ec1f-114">a [string](../builtin-types/reference-types.md).</span></span>
- <span data-ttu-id="8ec1f-115">um [bool](../builtin-types/bool.md).</span><span class="sxs-lookup"><span data-stu-id="8ec1f-115">a [bool](../builtin-types/bool.md).</span></span>
- <span data-ttu-id="8ec1f-116">um valor [integral](../builtin-types/integral-numeric-types.md) , como um `int` ou um `long` .</span><span class="sxs-lookup"><span data-stu-id="8ec1f-116">an [integral](../builtin-types/integral-numeric-types.md) value, such as an `int` or a `long`.</span></span>
- <span data-ttu-id="8ec1f-117">um valor de [Enumeração](../builtin-types/enum.md) .</span><span class="sxs-lookup"><span data-stu-id="8ec1f-117">an [enum](../builtin-types/enum.md) value.</span></span>

<span data-ttu-id="8ec1f-118">Começando com o C# 7.0, a expressão de correspondência pode ser qualquer expressão não nula.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-118">Starting with C# 7.0, the match expression can be any non-null expression.</span></span>

## <a name="the-switch-section"></a><span data-ttu-id="8ec1f-119">A seção switch</span><span class="sxs-lookup"><span data-stu-id="8ec1f-119">The switch section</span></span>

<span data-ttu-id="8ec1f-120">Uma instrução `switch` inclui uma ou mais seções do comutador.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-120">A `switch` statement includes one or more switch sections.</span></span> <span data-ttu-id="8ec1f-121">Cada seção switch contém um ou mais *rótulos case* (em um rótulo case ou padrão) seguidos por uma ou mais instruções.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-121">Each switch section contains one or more *case labels* (either a case or default label) followed by one or more statements.</span></span> <span data-ttu-id="8ec1f-122">A instrução `switch` pode incluir no máximo um rótulo padrão colocado em qualquer seção switch.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-122">The `switch` statement may include at most one default label placed in any switch section.</span></span> <span data-ttu-id="8ec1f-123">O exemplo a seguir mostra uma instrução `switch` simples que tem três seções switch, cada uma contendo duas instruções.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-123">The following example shows a simple `switch` statement that has three switch sections, each containing two statements.</span></span> <span data-ttu-id="8ec1f-124">A segunda seção switch contém os rótulos `case 2:` e `case 3:`.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-124">The second switch section contains the `case 2:` and `case 3:` labels.</span></span>

<span data-ttu-id="8ec1f-125">Uma instrução `switch` pode incluir qualquer número de seções switch e cada seção pode ter um ou mais rótulos case, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-125">A `switch` statement can include any number of switch sections, and each section can have one or more case labels, as shown in the following example.</span></span> <span data-ttu-id="8ec1f-126">No entanto, dois rótulos case não podem conter a mesma expressão.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-126">However, no two case labels may contain the same expression.</span></span>

[!code-csharp[switch#2](~/samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]

<span data-ttu-id="8ec1f-127">Apenas uma seção switch em uma instrução switch é executada.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-127">Only one switch section in a switch statement executes.</span></span> <span data-ttu-id="8ec1f-128">O C# não permite que a execução continue de uma seção switch para a próxima.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-128">C# doesn't allow execution to continue from one switch section to the next.</span></span> <span data-ttu-id="8ec1f-129">Por isso, o código a seguir gera um erro do compilador, CS0163: "O controle não pode passar de um rótulo case (\<case label>) para outro".</span><span class="sxs-lookup"><span data-stu-id="8ec1f-129">Because of this, the following code generates a compiler error, CS0163: "Control cannot fall through from one case label (\<case label>) to another."</span></span>

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

<span data-ttu-id="8ec1f-130">Esse requisito é atendido normalmente saindo explicitamente da seção switch usando uma instrução [break](break.md), [goto](goto.md) ou [return](return.md).</span><span class="sxs-lookup"><span data-stu-id="8ec1f-130">This requirement is usually met by explicitly exiting the switch section by using a [break](break.md), [goto](goto.md), or [return](return.md) statement.</span></span> <span data-ttu-id="8ec1f-131">No entanto, o código a seguir também é válido porque garante que o controle do programa não pode passar para a seção switch `default`.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-131">However, the following code is also valid, because it ensures that program control can't fall through to the `default` switch section.</span></span>

[!code-csharp[switch#4](~/samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]

<span data-ttu-id="8ec1f-132">A execução da lista de instruções na seção switch com um rótulo case que corresponde à expressão de correspondência começa com a primeira instrução e continua pela lista de instruções, normalmente até uma instrução de salto como `break`, `goto case`, `goto label`, `return` ou `throw` ser atingida.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-132">Execution of the statement list in the switch section with a case label that matches the match expression begins with the first statement and proceeds through the statement list, typically until a jump statement, such as a `break`, `goto case`, `goto label`, `return`, or `throw`, is reached.</span></span> <span data-ttu-id="8ec1f-133">Nesse ponto, o controle é transferido para fora da instrução `switch` ou para outro rótulo case.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-133">At that point, control is transferred outside the `switch` statement or to another case label.</span></span> <span data-ttu-id="8ec1f-134">Se uma instrução `goto` for usada, ela deverá transferir controle para um rótulo de constante.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-134">A `goto` statement, if it's used, must transfer control to a constant label.</span></span> <span data-ttu-id="8ec1f-135">Essa restrição é necessária, já que tentar transferir o controle para um rótulo não constante pode ter efeitos colaterais indesejáveis, tais como transferência do controle para um local não intencional no código ou criação de um loop infinito.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-135">This restriction is necessary, since attempting to transfer control to a non-constant label can have undesirable side-effects, such transferring control to an unintended location in code or creating an endless loop.</span></span>

## <a name="case-labels"></a><span data-ttu-id="8ec1f-136">Rótulos case</span><span class="sxs-lookup"><span data-stu-id="8ec1f-136">Case labels</span></span>

<span data-ttu-id="8ec1f-137">Cada rótulo case especifica um padrão a ser comparado com a expressão de correspondência (a variável `caseSwitch` nos exemplos anteriores).</span><span class="sxs-lookup"><span data-stu-id="8ec1f-137">Each case label specifies a pattern to compare to the match expression (the `caseSwitch` variable in the previous examples).</span></span> <span data-ttu-id="8ec1f-138">Se eles corresponderem, o controle será transferido para a seção switch que contém o **primeiro** rótulo case correspondente.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-138">If they match, control is transferred to the switch section that contains the **first** matching case label.</span></span> <span data-ttu-id="8ec1f-139">Se nenhum padrão de rótulo de caso corresponder à expressão de correspondência, o controle será transferido para a seção com o rótulo de caso `default`, se existir algum.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-139">If no case label pattern matches the match expression, control is transferred to the section with the `default` case label, if there's one.</span></span> <span data-ttu-id="8ec1f-140">Se não houver nenhum case `default`, nenhuma declaração em qualquer seção switch será executada e o controle será transferido para fora da instrução `switch`.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-140">If there's no `default` case, no statements in any switch section are executed, and control is transferred outside the `switch` statement.</span></span>

<span data-ttu-id="8ec1f-141">Para obter informações sobre a instrução `switch` e a correspondência de padrões, consulte a seção [Correspondência de padrões com a instrução `switch`](#pattern-matching with-the-switch-statement).</span><span class="sxs-lookup"><span data-stu-id="8ec1f-141">For information on the `switch` statement and pattern matching, see the [Pattern matching with the `switch` statement](#pattern-matching with-the-switch-statement) section.</span></span>

<span data-ttu-id="8ec1f-142">Como o C# 6 dá suporte apenas ao padrão de constante e não permite a repetição de valores de constantes, os rótulos case definem valores mutuamente exclusivos e apenas um padrão pode corresponder à expressão de correspondência.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-142">Because C# 6 supports only the constant pattern and doesn't allow the repetition of constant values, case labels define mutually exclusive values, and only one pattern can match the match expression.</span></span> <span data-ttu-id="8ec1f-143">Como resultado, a ordem na qual as instruções `case` aparecem não é importante.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-143">As a result, the order in which `case` statements appear is unimportant.</span></span>

<span data-ttu-id="8ec1f-144">No entanto, no C# 7.0, como há suporte para outros padrões, os rótulos case não precisam definir valores mutuamente exclusivos e vários padrões podem corresponder à expressão de correspondência.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-144">In C# 7.0, however, because other patterns are supported, case labels need not define mutually exclusive values, and multiple patterns can match the match expression.</span></span> <span data-ttu-id="8ec1f-145">Como são executadas apenas as instruções na primeira seção switch que contém o primeiro padrão de correspondência, a ordem na qual as instruções `case` aparecem agora é importante.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-145">Because only the statements in the first switch section that contains the matching pattern are executed, the order in which `case` statements appear is now important.</span></span> <span data-ttu-id="8ec1f-146">Se o C# detecta uma seção switch cujas instruções case são equivalentes ou são subconjuntos de instruções anteriores, ele gera um erro do compilador, CS8120, “O switch case já foi tratado por um case anterior”.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-146">If C# detects a switch section whose case statement or statements are equivalent to or are subsets of previous statements, it generates a compiler error, CS8120, "The switch case has already been handled by a previous case."</span></span>

<span data-ttu-id="8ec1f-147">O exemplo a seguir ilustra uma instrução `switch` que usa uma variedade de padrões não mutuamente exclusivos.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-147">The following example illustrates a `switch` statement that uses a variety of non-mutually exclusive patterns.</span></span> <span data-ttu-id="8ec1f-148">Se você mover a seção switch `case 0:` para que ela não seja mais a primeira seção na instrução `switch`, o C# gera um erro do compilador porque um inteiro cujo valor é zero é um subconjunto de todos os inteiros, que é o padrão definido pela instrução `case int val`.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-148">If you move the `case 0:` switch section so that it's no longer the first section in the `switch` statement, C# generates a compiler error because an integer whose value is zero is a subset of all integers, which is the pattern defined by the `case int val` statement.</span></span>

[!code-csharp[switch#5](~/samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]

<span data-ttu-id="8ec1f-149">Você pode corrigir esse problema e eliminar o aviso do compilador em uma das duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="8ec1f-149">You can correct this issue and eliminate the compiler warning in one of two ways:</span></span>

- <span data-ttu-id="8ec1f-150">Alterando a ordem das seções switch.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-150">By changing the order of the switch sections.</span></span>

- <span data-ttu-id="8ec1f-151">Usando uma [cláusula where](#the-case-statement-and-the-when-clause) no rótulo `case`.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-151">By using a [when clause](#the-case-statement-and-the-when-clause) in the `case` label.</span></span>

## <a name="the-default-case"></a><span data-ttu-id="8ec1f-152">O case `default`</span><span class="sxs-lookup"><span data-stu-id="8ec1f-152">The `default` case</span></span>

<span data-ttu-id="8ec1f-153">O case `default` especifica a seção switch a ser executada se a expressão de correspondência não corresponder a nenhum outro rótulo `case`.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-153">The `default` case specifies the switch section to execute if the match expression doesn't match any other `case` label.</span></span> <span data-ttu-id="8ec1f-154">Se um case `default` não estiver presente e a expressão de correspondência não corresponder a nenhum outro rótulo `case`, o fluxo do programa passará pela instrução `switch`.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-154">If a `default` case is not present and the match expression doesn't match any other `case` label, program flow falls through the `switch` statement.</span></span>

<span data-ttu-id="8ec1f-155">O case `default` pode aparecer em qualquer ordem na instrução `switch`.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-155">The `default` case can appear in any order in the `switch` statement.</span></span> <span data-ttu-id="8ec1f-156">Independentemente de sua ordem no código-fonte, ele é sempre avaliado por último, afinal os rótulos `case` foram avaliados.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-156">Regardless of its order in the source code, it's always evaluated last, after all `case` labels have been evaluated.</span></span>

## <a name="pattern-matching-with-the-switch-statement"></a><span data-ttu-id="8ec1f-157"> Correspondência de padrões com a instrução `switch`</span><span class="sxs-lookup"><span data-stu-id="8ec1f-157">Pattern matching with the `switch` statement</span></span>

<span data-ttu-id="8ec1f-158">Cada instrução `case` define um padrão que, se corresponde à expressão de correspondência, faz com que sua seção switch recipiente seja executada.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-158">Each `case` statement defines a pattern that, if it matches the match expression, causes its  containing switch section to be executed.</span></span> <span data-ttu-id="8ec1f-159">Todas as versões do C# dão suporte ao padrão de constante.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-159">All versions of C# support the constant pattern.</span></span> <span data-ttu-id="8ec1f-160">Começando com o C# 7.0, há suporte para os padrões restantes.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-160">The remaining patterns are supported beginning with C# 7.0.</span></span>

### <a name="constant-pattern"></a><span data-ttu-id="8ec1f-161">Padrão de constante</span><span class="sxs-lookup"><span data-stu-id="8ec1f-161">Constant pattern</span></span>

<span data-ttu-id="8ec1f-162">O padrão de constante testa se a expressão de correspondência é igual a uma constante especificada.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-162">The constant pattern tests whether the match expression equals a specified constant.</span></span> <span data-ttu-id="8ec1f-163">Sua sintaxe é:</span><span class="sxs-lookup"><span data-stu-id="8ec1f-163">Its syntax is:</span></span>

```csharp
   case constant:
```

<span data-ttu-id="8ec1f-164">em que *constant* é o valor para testar.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-164">where *constant* is the value to test for.</span></span> <span data-ttu-id="8ec1f-165">*constant* pode ser qualquer uma das expressões de constante a seguir:</span><span class="sxs-lookup"><span data-stu-id="8ec1f-165">*constant* can be any of the following constant expressions:</span></span>

- <span data-ttu-id="8ec1f-166">Um literal [bool](../builtin-types/bool.md) : `true` ou `false` .</span><span class="sxs-lookup"><span data-stu-id="8ec1f-166">A [bool](../builtin-types/bool.md) literal: either `true` or `false`.</span></span>
- <span data-ttu-id="8ec1f-167">Qualquer constante [integral](../builtin-types/integral-numeric-types.md) , como um `int` , um `long` ou um `byte` .</span><span class="sxs-lookup"><span data-stu-id="8ec1f-167">Any [integral](../builtin-types/integral-numeric-types.md) constant, such as an `int`, a `long`, or a `byte`.</span></span>
- <span data-ttu-id="8ec1f-168">O nome de uma variável `const` declarada.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-168">The name of a declared `const` variable.</span></span>
- <span data-ttu-id="8ec1f-169">Uma constante de enumeração.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-169">An enumeration constant.</span></span>
- <span data-ttu-id="8ec1f-170">Um literal [char](../builtin-types/char.md).</span><span class="sxs-lookup"><span data-stu-id="8ec1f-170">A [char](../builtin-types/char.md) literal.</span></span>
- <span data-ttu-id="8ec1f-171">Um literal [string](../builtin-types/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="8ec1f-171">A [string](../builtin-types/reference-types.md) literal.</span></span>

<span data-ttu-id="8ec1f-172">A expressão de constante é avaliada da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="8ec1f-172">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="8ec1f-173">Se *expr* e *constant* forem tipos integrais, o operador de igualdade de C# determinará se a expressão retorna `true` (ou seja, se `expr == constant`).</span><span class="sxs-lookup"><span data-stu-id="8ec1f-173">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="8ec1f-174">Caso contrário, o valor da expressão será determinado por uma chamada ao método estático [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)).</span><span class="sxs-lookup"><span data-stu-id="8ec1f-174">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>

<span data-ttu-id="8ec1f-175">O exemplo a seguir usa o padrão de constante para determinar se uma data específica é um final de semana, o primeiro dia, o último dia ou o meio da semana de trabalho.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-175">The following example uses the constant pattern to determine whether a particular date is a weekend, the first day of the work week, the last day of the work week, or the middle of the work week.</span></span> <span data-ttu-id="8ec1f-176">Ele avalia a propriedade <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> do dia atual em relação aos membros da enumeração <xref:System.DayOfWeek>.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-176">It evaluates the <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> property of the current day against the members of the <xref:System.DayOfWeek> enumeration.</span></span>

[!code-csharp[switch#7](~/samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

<span data-ttu-id="8ec1f-177">O exemplo a seguir usa o padrão de constante para manipular a entrada do usuário em um aplicativo de console que simula uma máquina de café automática.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-177">The following example uses the constant pattern to handle user input in a console application that simulates an automatic coffee machine.</span></span>

[!code-csharp[switch#6](~/samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]

### <a name="type-pattern"></a><span data-ttu-id="8ec1f-178">Padrão de tipo</span><span class="sxs-lookup"><span data-stu-id="8ec1f-178">Type pattern</span></span>

<span data-ttu-id="8ec1f-179">O padrão de tipo permite a conversão e a avaliação do tipo concisa.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-179">The type pattern enables concise type evaluation and conversion.</span></span> <span data-ttu-id="8ec1f-180">Quando usado com a instrução `switch` para realizar a correspondência de padrões, testa se uma expressão pode ser convertida para um tipo especificado e, se puder, o converte em uma variável desse tipo.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-180">When used with the `switch` statement to perform pattern matching, it tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="8ec1f-181">Sua sintaxe é:</span><span class="sxs-lookup"><span data-stu-id="8ec1f-181">Its syntax is:</span></span>

```csharp
   case type varname
```

<span data-ttu-id="8ec1f-182">em que *type* é o nome do tipo no qual o resultado de *expr* deverá ser convertido e *varname* é o objeto para o qual o resultado de *expr* é convertido se a correspondência é bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-182">where *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the match succeeds.</span></span> <span data-ttu-id="8ec1f-183">O tipo de tempo de compilação *expr* pode ser um parâmetro de tipo genérico, começando com C# 7.1.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-183">The compile-time type of *expr* may be a generic type parameter, starting with C# 7.1.</span></span>

<span data-ttu-id="8ec1f-184">A expressão `case` será `true` se qualquer uma das condições seguintes for verdadeira:</span><span class="sxs-lookup"><span data-stu-id="8ec1f-184">The `case` expression is `true` if any of the following is true:</span></span>

- <span data-ttu-id="8ec1f-185">*expr* for uma instância do mesmo tipo que *type*.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-185">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="8ec1f-186">*expr* for uma instância de um tipo derivado de *type*.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-186">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="8ec1f-187">Em outras palavras, o resultado de *expr* pode sofrer upcast para uma instância de *type*.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-187">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="8ec1f-188">*expr* tem um tipo de tempo de compilação que é uma classe base de *type*, e *expr* tem um tipo de runtime que é *type* ou é derivado de *type*.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-188">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="8ec1f-189">O *tipo do tempo de compilação* de uma variável é o tipo da variável conforme definido em sua declaração de tipo.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-189">The *compile-time type* of a variable is the variable's type as defined in its type declaration.</span></span> <span data-ttu-id="8ec1f-190">O *tipo de runtime* de uma variável é o tipo da instância atribuída a essa variável.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-190">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="8ec1f-191">*expr* é uma instância de um tipo que implementa a interface de *type*.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-191">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="8ec1f-192">Se a expressão case for true, *varname* será definitivamente atribuído e terá o escopo local dentro da seção switch apenas.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-192">If the case expression is true, *varname* is definitely assigned and has local scope within the switch section only.</span></span>

<span data-ttu-id="8ec1f-193">Observe que `null` não corresponde a um tipo.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-193">Note that `null` doesn't match a type.</span></span> <span data-ttu-id="8ec1f-194">Para corresponder um `null`, use o seguinte rótulo `case`:</span><span class="sxs-lookup"><span data-stu-id="8ec1f-194">To match a `null`, you use the following `case` label:</span></span>

```csharp
case null:
```

<span data-ttu-id="8ec1f-195">O exemplo a seguir usa o padrão de tipo para fornecer informações sobre vários tipos de coleção.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-195">The following example uses the type pattern to provide information about various kinds of collection types.</span></span>

[!code-csharp[type-pattern#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

<span data-ttu-id="8ec1f-196">Em vez de `object`, você poderia empregar um método genérico, usando o tipo da coleção como o parâmetro de tipo, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="8ec1f-196">Instead of `object`, you could make a generic method, using the type of the collection as the type parameter, as shown in the following code:</span></span>

[!code-csharp[type-pattern#3](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern3.cs#1)]

<span data-ttu-id="8ec1f-197">A versão genérica é diferente da primeira amostra de duas maneiras.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-197">The generic version is different than the first sample in two ways.</span></span> <span data-ttu-id="8ec1f-198">Primeiro, você não pode usar o case `null`.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-198">First, you can't use the `null` case.</span></span> <span data-ttu-id="8ec1f-199">Você não pode usar nenhum case constante porque o compilador não pode converter qualquer tipo arbitrário de `T` para qualquer tipo diferente de `object`.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-199">You can't use any constant case because the compiler can't convert any arbitrary type `T` to any type other than `object`.</span></span> <span data-ttu-id="8ec1f-200">O que tinha sido o case `default` agora testa para um `object` não nulo.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-200">What had been the `default` case now tests for a non-null `object`.</span></span> <span data-ttu-id="8ec1f-201">Isso significa que o case `default` testa apenas para `null`.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-201">That means the `default` case tests only for `null`.</span></span>

<span data-ttu-id="8ec1f-202">Sem a correspondência de padrões, esse código pode ser escrito da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-202">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="8ec1f-203">O uso da correspondência de padrões de tipo produz um código mais compacto e legível eliminando a necessidade de testar se o resultado de uma conversão é um `null` ou executar conversões repetidas.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-203">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null` or to perform repeated casts.</span></span>

[!code-csharp[type-pattern2#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="the-case-statement-and-the-when-clause"></a><span data-ttu-id="8ec1f-204">A instrução `case` e a cláusula `when`</span><span class="sxs-lookup"><span data-stu-id="8ec1f-204">The `case` statement and the `when` clause</span></span>

<span data-ttu-id="8ec1f-205">A partir do C# 7.0, como as instruções case não precisam ser mutuamente exclusivas, você pode usar a adição de uma cláusula `when` para especificar uma condição adicional que precisa ser atendida para que a instrução case seja avaliada como true.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-205">Starting with C# 7.0, because case statements need not be mutually exclusive, you can add a `when` clause to specify an additional condition that must be satisfied for the case statement to evaluate to true.</span></span> <span data-ttu-id="8ec1f-206">A cláusula `when` pode ser qualquer expressão que retorna um valor booliano.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-206">The `when` clause can be any expression that returns a Boolean value.</span></span>

<span data-ttu-id="8ec1f-207">O exemplo a seguir define uma classe `Shape` base, uma classe `Rectangle` que deriva de `Shape` e uma classe `Square` que deriva de `Rectangle`.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-207">The following example defines a base `Shape` class, a `Rectangle` class that derives from `Shape`, and a `Square` class that derives from `Rectangle`.</span></span> <span data-ttu-id="8ec1f-208">Ele usa a cláusula `when` para garantir que o `ShowShapeInfo` trata um objeto `Rectangle` que recebeu comprimentos e larguras como um `Square` mesmo se ele não tiver sido instanciado como um objeto `Square`.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-208">It uses the `when` clause to ensure that the `ShowShapeInfo` treats a `Rectangle` object that has been assigned equal lengths and widths as a `Square` even if it hasn't been instantiated as a `Square` object.</span></span> <span data-ttu-id="8ec1f-209">O método não tenta exibir informações sobre um objeto que é `null` ou uma forma cuja área é zero.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-209">The method doesn't attempt to display information either about an object that is `null` or a shape whose area is zero.</span></span>

[!code-csharp[when-clause#1](~/samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]

<span data-ttu-id="8ec1f-210">Observe que a cláusula `when` no exemplo que tenta testar se um objeto `Shape` é `null` não é executada.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-210">Note that the `when` clause in the example that attempts to test whether a `Shape` object is `null` doesn't execute.</span></span> <span data-ttu-id="8ec1f-211">O padrão de tipo correto para testar um `null` é `case null:`.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-211">The correct type pattern to test for a `null` is `case null:`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8ec1f-212">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="8ec1f-212">C# language specification</span></span>

<span data-ttu-id="8ec1f-213">Para obter mais informações, consulte [A instrução switch](~/_csharplang/spec/statements.md#the-switch-statement) na [Especificação da linguagem C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="8ec1f-213">For more information, see [The switch statement](~/_csharplang/spec/statements.md#the-switch-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="8ec1f-214">A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.</span><span class="sxs-lookup"><span data-stu-id="8ec1f-214">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="8ec1f-215">Confira também</span><span class="sxs-lookup"><span data-stu-id="8ec1f-215">See also</span></span>

- [<span data-ttu-id="8ec1f-216">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="8ec1f-216">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8ec1f-217">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="8ec1f-217">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8ec1f-218">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="8ec1f-218">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="8ec1f-219">if-else</span><span class="sxs-lookup"><span data-stu-id="8ec1f-219">if-else</span></span>](if-else.md)
- [<span data-ttu-id="8ec1f-220">Correspondência padrão</span><span class="sxs-lookup"><span data-stu-id="8ec1f-220">Pattern Matching</span></span>](../../pattern-matching.md)
