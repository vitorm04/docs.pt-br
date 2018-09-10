---
title: Instrução switch do C#
ms.date: 08/14/2018
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
ms.openlocfilehash: 08b63d67b6175d18bee1317cc8908d876fbb4039
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44252084"
---
# <a name="switch-c-reference"></a><span data-ttu-id="54363-102">switch (Referência em C#)</span><span class="sxs-lookup"><span data-stu-id="54363-102">switch (C# reference)</span></span>

<span data-ttu-id="54363-103">`switch` é uma instrução de seleção que escolhe uma única *seção switch* para ser executada de uma lista de candidatas com base em uma correspondência de padrão com a *expressão de correspondência*.</span><span class="sxs-lookup"><span data-stu-id="54363-103">`switch` is a selection statement that chooses a single *switch section* to execute from a list of candidates based on a pattern match with the *match expression*.</span></span>

[!code-csharp[switch#1](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]

<span data-ttu-id="54363-104">A instrução `switch` geralmente é usada como uma alternativa para um constructo [if-else](if-else.md) se uma única expressão é testada com três ou mais condições.</span><span class="sxs-lookup"><span data-stu-id="54363-104">The `switch` statement is often used as an alternative to an [if-else](if-else.md) construct if a single expression is tested against three or more conditions.</span></span> <span data-ttu-id="54363-105">Por exemplo, a instrução `switch` a seguir determina se uma variável do tipo `Color` tem um dos três valores:</span><span class="sxs-lookup"><span data-stu-id="54363-105">For example, the following `switch` statement determines whether a variable of type `Color` has one of three values:</span></span>

[!code-csharp[switch#3](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]

<span data-ttu-id="54363-106">Ele é equivalente ao exemplo a seguir que usa um constructo `if`-`else`.</span><span class="sxs-lookup"><span data-stu-id="54363-106">It is equivalent to the following example that uses an `if`-`else` construct.</span></span>

[!code-csharp[switch#3a](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]

## <a name="the-match-expression"></a><span data-ttu-id="54363-107">A expressão de correspondência</span><span class="sxs-lookup"><span data-stu-id="54363-107">The match expression</span></span>

<span data-ttu-id="54363-108">A expressão de correspondência fornece o valor para corresponder aos padrões nos rótulos `case`.</span><span class="sxs-lookup"><span data-stu-id="54363-108">The match expression provides the value to match against the patterns in `case` labels.</span></span> <span data-ttu-id="54363-109">A sintaxe é:</span><span class="sxs-lookup"><span data-stu-id="54363-109">Its syntax is:</span></span>

```csharp
   switch (expr)
```

<span data-ttu-id="54363-110">No C# 6, a expressão de correspondência deve ser uma expressão que retorna um valor dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="54363-110">In C# 6, the match expression must be an expression that returns a value of the following types:</span></span>

- <span data-ttu-id="54363-111">um [char](char.md).</span><span class="sxs-lookup"><span data-stu-id="54363-111">a [char](char.md).</span></span>
- <span data-ttu-id="54363-112">um [string](string.md).</span><span class="sxs-lookup"><span data-stu-id="54363-112">a [string](string.md).</span></span>
- <span data-ttu-id="54363-113">um [bool](bool.md).</span><span class="sxs-lookup"><span data-stu-id="54363-113">a [bool](bool.md).</span></span>
- <span data-ttu-id="54363-114">um valor de inteiro, como um [int](int.md) ou um [long](long.md).</span><span class="sxs-lookup"><span data-stu-id="54363-114">an integral value, such as an [int](int.md) or a [long](long.md).</span></span>
- <span data-ttu-id="54363-115">um valor [enum](enum.md).</span><span class="sxs-lookup"><span data-stu-id="54363-115">an [enum](enum.md) value.</span></span>

<span data-ttu-id="54363-116">Começando com o C# 7.0, a expressão de correspondência pode ser qualquer expressão não nula.</span><span class="sxs-lookup"><span data-stu-id="54363-116">Starting with C# 7.0, the match expression can be any non-null expression.</span></span>

## <a name="the-switch-section"></a><span data-ttu-id="54363-117">A seção switch</span><span class="sxs-lookup"><span data-stu-id="54363-117">The switch section</span></span>

<span data-ttu-id="54363-118">Uma instrução `switch` inclui uma ou mais seções do comutador.</span><span class="sxs-lookup"><span data-stu-id="54363-118">A `switch` statement includes one or more switch sections.</span></span> <span data-ttu-id="54363-119">Cada seção switch contém um ou mais *rótulos case* (em um rótulo case ou padrão) seguidos por uma ou mais instruções.</span><span class="sxs-lookup"><span data-stu-id="54363-119">Each switch section contains one or more *case labels* (either a case or default label) followed by one or more statements.</span></span> <span data-ttu-id="54363-120">A instrução `switch` pode incluir no máximo um rótulo padrão colocado em qualquer seção switch.</span><span class="sxs-lookup"><span data-stu-id="54363-120">The `switch` statement may include at most one default label placed in any switch section.</span></span> <span data-ttu-id="54363-121">O exemplo a seguir mostra uma instrução `switch` simples que tem três seções switch, cada uma contendo duas instruções.</span><span class="sxs-lookup"><span data-stu-id="54363-121">The following example shows a simple `switch` statement that has three switch sections, each containing two statements.</span></span> <span data-ttu-id="54363-122">A segunda seção switch contém os rótulos `case 2:` e `case 3:`.</span><span class="sxs-lookup"><span data-stu-id="54363-122">The second switch section contains the `case 2:` and `case 3:` labels.</span></span>

<span data-ttu-id="54363-123">Uma instrução `switch` pode incluir qualquer número de seções switch e cada seção pode ter um ou mais rótulos case, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="54363-123">A `switch` statement can include any number of switch sections, and each section can have one or more case labels, as shown in the following example.</span></span> <span data-ttu-id="54363-124">No entanto, dois rótulos case não podem conter a mesma expressão.</span><span class="sxs-lookup"><span data-stu-id="54363-124">However, no two case labels may contain the same expression.</span></span>

[!code-csharp[switch#2](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]

<span data-ttu-id="54363-125">Apenas uma seção switch em uma instrução switch é executada.</span><span class="sxs-lookup"><span data-stu-id="54363-125">Only one switch section in a switch statement executes.</span></span> <span data-ttu-id="54363-126">O C# não permite que a execução continue de uma seção switch para a próxima.</span><span class="sxs-lookup"><span data-stu-id="54363-126">C# does not allow execution to continue from one switch section to the next.</span></span> <span data-ttu-id="54363-127">Por isso, o código a seguir gera um erro do compilador, CS0163: "O controle não pode passar de um rótulo case (<case label>) para outro".</span><span class="sxs-lookup"><span data-stu-id="54363-127">Because of this, the following code generates a compiler error, CS0163: "Control cannot fall through from one case label (<case label>) to another."</span></span>

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

<span data-ttu-id="54363-128">Esse requisito é atendido normalmente saindo explicitamente da seção switch usando uma instrução [break](break.md), [goto](goto.md) ou [return](return.md).</span><span class="sxs-lookup"><span data-stu-id="54363-128">This requirement is usually met by explicitly exiting the switch section by using a [break](break.md), [goto](goto.md), or [return](return.md) statement.</span></span> <span data-ttu-id="54363-129">No entanto, o código a seguir também é válido, pois garante que o controle do programa não pode passar para a seção switch `default`.</span><span class="sxs-lookup"><span data-stu-id="54363-129">However, the following code is also valid, because it ensures that program control cannot fall through to the `default` switch section.</span></span>

[!code-csharp[switch#4](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]

<span data-ttu-id="54363-130">A execução da lista de instruções na seção switch com um rótulo case que corresponde à expressão de correspondência começa com a primeira instrução e continua pela lista de instruções, normalmente até uma instrução de salto como `break`, `goto case`, `goto label`, `return` ou `throw` ser atingida.</span><span class="sxs-lookup"><span data-stu-id="54363-130">Execution of the statement list in the switch section with a case label that matches the match expression begins with the first statement and proceeds through the statement list, typically until a jump statement, such as a `break`, `goto case`, `goto label`, `return`, or `throw`, is reached.</span></span> <span data-ttu-id="54363-131">Nesse ponto, o controle é transferido para fora da instrução `switch` ou para outro rótulo case.</span><span class="sxs-lookup"><span data-stu-id="54363-131">At that point, control is transferred outside the `switch` statement or to another case label.</span></span> <span data-ttu-id="54363-132">Se uma instrução `goto` for usada, ela deverá transferir controle para um rótulo de constante.</span><span class="sxs-lookup"><span data-stu-id="54363-132">A `goto` statement, if it is used, must transfer control to a constant label.</span></span> <span data-ttu-id="54363-133">Essa restrição é necessária, já que tentar transferir o controle para um rótulo não constante pode ter efeitos colaterais indesejáveis, tais como transferência do controle para um local não intencional no código ou criação de um loop infinito.</span><span class="sxs-lookup"><span data-stu-id="54363-133">This restriction is necessary, since attempting to transfer control to a non-constant label can have undesirable side-effects, such transferring control to an unintended location in code or creating an endless loop.</span></span>

## <a name="case-labels"></a><span data-ttu-id="54363-134">Rótulos case</span><span class="sxs-lookup"><span data-stu-id="54363-134">Case labels</span></span>

<span data-ttu-id="54363-135">Cada rótulo case especifica um padrão a ser comparado com a expressão de correspondência (a variável `caseSwitch` nos exemplos anteriores).</span><span class="sxs-lookup"><span data-stu-id="54363-135">Each case label specifies a pattern to compare to the match expression (the `caseSwitch` variable in the previous examples).</span></span> <span data-ttu-id="54363-136">Se eles corresponderem, o controle será transferido para a seção switch que contém o **primeiro** rótulo case correspondente.</span><span class="sxs-lookup"><span data-stu-id="54363-136">If they match, control is transferred to the switch section that contains the **first** matching case label.</span></span> <span data-ttu-id="54363-137">Se nenhum padrão de rótulo de caso corresponder à expressão de correspondência, o controle será transferido para a seção com o rótulo de caso `default`, se existir algum.</span><span class="sxs-lookup"><span data-stu-id="54363-137">If no case label pattern matches the match expression, control is transferred to the section with the `default` case label, if there is one.</span></span> <span data-ttu-id="54363-138">Se não houver nenhum case `default`, nenhuma declaração em qualquer seção switch será executada e o controle será transferido para fora da instrução `switch`.</span><span class="sxs-lookup"><span data-stu-id="54363-138">If there is no `default` case, no statements in any switch section are executed, and control is transferred outside the `switch` statement.</span></span>

<span data-ttu-id="54363-139">Para obter informações sobre a instrução `switch` e a correspondência de padrões, consulte a seção [Correspondência de padrões com a instrução `switch`](#pattern).</span><span class="sxs-lookup"><span data-stu-id="54363-139">For information on the `switch` statement and pattern matching, see the [Pattern matching with the `switch` statement](#pattern) section.</span></span>

<span data-ttu-id="54363-140">Como o C# 6 dá suporte apenas ao padrão de constante e não permite a repetição de valores de constantes, os rótulos case definem valores mutuamente exclusivos e apenas um padrão pode corresponder à expressão de correspondência.</span><span class="sxs-lookup"><span data-stu-id="54363-140">Because C# 6 supports only the constant pattern and does not allow the repetition of constant values, case labels define mutually exclusive values, and only one pattern can match the match expression.</span></span> <span data-ttu-id="54363-141">Como resultado, a ordem na qual as instruções `case` aparecem não é importante.</span><span class="sxs-lookup"><span data-stu-id="54363-141">As a result, the order in which `case` statements appear is unimportant.</span></span>

<span data-ttu-id="54363-142">No entanto, no C# 7.0, como há suporte para outros padrões, os rótulos case não precisam definir valores mutuamente exclusivos e vários padrões podem corresponder à expressão de correspondência.</span><span class="sxs-lookup"><span data-stu-id="54363-142">In C# 7.0, however, because other patterns are supported, case labels need not define mutually exclusive values, and multiple patterns can match the match expression.</span></span> <span data-ttu-id="54363-143">Como apenas as instruções na seção switch que contém o primeiro padrão de correspondência são executadas, a ordem na qual as instruções `case` aparecem agora é importante.</span><span class="sxs-lookup"><span data-stu-id="54363-143">Because only the statements in the switch section that contains the first matching pattern are executed, the order in which `case` statements appear is now important.</span></span> <span data-ttu-id="54363-144">Se o C# detecta uma seção switch cujas instruções case são equivalentes ou são subconjuntos de instruções anteriores, ele gera um erro do compilador, CS8120, “O switch case já foi tratado por um case anterior”.</span><span class="sxs-lookup"><span data-stu-id="54363-144">If C# detects a switch section whose case statement or statements are equivalent to or are subsets of previous statements, it generates a compiler error, CS8120, "The switch case has already been handled by a previous case."</span></span>

<span data-ttu-id="54363-145">O exemplo a seguir ilustra uma instrução `switch` que usa uma variedade de padrões não mutuamente exclusivos.</span><span class="sxs-lookup"><span data-stu-id="54363-145">The following example illustrates a `switch` statement that uses a variety of non-mutually exclusive patterns.</span></span> <span data-ttu-id="54363-146">Se você mover a seção switch `case 0:` para que ela não seja mais a primeira seção na instrução `switch`, o C# gera um erro do compilador porque um inteiro cujo valor é zero é um subconjunto de todos os inteiros, que é o padrão definido pela instrução `case int val`.</span><span class="sxs-lookup"><span data-stu-id="54363-146">If you move the `case 0:` switch section so that it is no longer the first section in the `switch` statement, C# generates a compiler error because an integer whose value is zero is a subset of all integers, which is the pattern defined by the `case int val` statement.</span></span>

[!code-csharp[switch#5](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]

<span data-ttu-id="54363-147">Você pode corrigir esse problema e eliminar o aviso do compilador em uma das duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="54363-147">You can correct this issue and eliminate the compiler warning in one of two ways:</span></span>

- <span data-ttu-id="54363-148">Alterando a ordem das seções switch.</span><span class="sxs-lookup"><span data-stu-id="54363-148">By changing the order of the switch sections.</span></span>

- <span data-ttu-id="54363-149">Usando uma </a name="when">cláusula when</a> no rótulo `case`.</span><span class="sxs-lookup"><span data-stu-id="54363-149">By using a </a name="when">when clause</a> in the `case` label.</span></span>

## <a name="the-default-case"></a><span data-ttu-id="54363-150">O case `default`</span><span class="sxs-lookup"><span data-stu-id="54363-150">The `default` case</span></span>

<span data-ttu-id="54363-151">O case `default` especifica a seção switch a ser executada se a expressão de correspondência não corresponder a nenhum outro rótulo `case`.</span><span class="sxs-lookup"><span data-stu-id="54363-151">The `default` case specifies the switch section to execute if the match expression does not match any other `case` label.</span></span> <span data-ttu-id="54363-152">Se um case `default` não estiver presente e a expressão de correspondência não corresponder a nenhum outro rótulo `case`, o fluxo do programa passará pela instrução `switch`.</span><span class="sxs-lookup"><span data-stu-id="54363-152">If a `default` case is not present and the match expression does not match any other `case` label, program flow falls through the `switch` statement.</span></span>

<span data-ttu-id="54363-153">O case `default` pode aparecer em qualquer ordem na instrução `switch`.</span><span class="sxs-lookup"><span data-stu-id="54363-153">The `default` case can appear in any order in the `switch` statement.</span></span> <span data-ttu-id="54363-154">Independentemente de sua ordem no código-fonte, ele é sempre avaliado por último, afinal os rótulos `case` foram avaliados.</span><span class="sxs-lookup"><span data-stu-id="54363-154">Regardless of its order in the source code, it is always evaluated last, after all `case` labels have been evaluated.</span></span>

## <a name="a-namepattern--pattern-matching-with-the-switch-statement"></a><span data-ttu-id="54363-155"><a name="pattern" /> Correspondência de padrões com a instrução `switch`</span><span class="sxs-lookup"><span data-stu-id="54363-155"><a name="pattern" /> Pattern matching with the `switch` statement</span></span>

<span data-ttu-id="54363-156">Cada instrução `case` define um padrão que, se corresponde à expressão de correspondência, faz com que sua seção switch recipiente seja executada.</span><span class="sxs-lookup"><span data-stu-id="54363-156">Each `case` statement defines a pattern that, if it matches the match expression, causes its  containing switch section to be executed.</span></span> <span data-ttu-id="54363-157">Todas as versões do C# dão suporte ao padrão de constante.</span><span class="sxs-lookup"><span data-stu-id="54363-157">All versions of C# support the constant pattern.</span></span> <span data-ttu-id="54363-158">Começando com o C# 7.0, há suporte para os padrões restantes.</span><span class="sxs-lookup"><span data-stu-id="54363-158">The remaining patterns are supported beginning with C# 7.0.</span></span>

### <a name="constant-pattern"></a><span data-ttu-id="54363-159">Padrão de constante</span><span class="sxs-lookup"><span data-stu-id="54363-159">Constant pattern</span></span>

<span data-ttu-id="54363-160">O padrão de constante testa se a expressão de correspondência é igual a uma constante especificada.</span><span class="sxs-lookup"><span data-stu-id="54363-160">The constant pattern tests whether the match expression equals a specified constant.</span></span> <span data-ttu-id="54363-161">A sintaxe é:</span><span class="sxs-lookup"><span data-stu-id="54363-161">Its syntax is:</span></span>

```csharp
   case constant:
```

<span data-ttu-id="54363-162">em que *constant* é o valor para testar.</span><span class="sxs-lookup"><span data-stu-id="54363-162">where *constant* is the value to test for.</span></span> <span data-ttu-id="54363-163">*constant* pode ser qualquer uma das expressões de constante a seguir:</span><span class="sxs-lookup"><span data-stu-id="54363-163">*constant* can be any of the following constant expressions:</span></span>

- <span data-ttu-id="54363-164">Um literal [bool](bool.md), `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="54363-164">A [bool](bool.md) literal, either `true` or `false`.</span></span>
- <span data-ttu-id="54363-165">Qualquer constante integral, como um [int](int.md), um [long](long.md) ou um [byte](byte.md).</span><span class="sxs-lookup"><span data-stu-id="54363-165">Any integral constant, such as an [int](int.md), a [long](long.md), or a [byte](byte.md).</span></span>
- <span data-ttu-id="54363-166">O nome de uma variável `const` declarada.</span><span class="sxs-lookup"><span data-stu-id="54363-166">The name of a declared `const` variable.</span></span>
- <span data-ttu-id="54363-167">Uma constante de enumeração.</span><span class="sxs-lookup"><span data-stu-id="54363-167">An enumeration constant.</span></span>
- <span data-ttu-id="54363-168">Um literal [char](char.md).</span><span class="sxs-lookup"><span data-stu-id="54363-168">A [char](char.md) literal.</span></span>
- <span data-ttu-id="54363-169">Um literal [string](string.md).</span><span class="sxs-lookup"><span data-stu-id="54363-169">A [string](string.md) literal.</span></span>

<span data-ttu-id="54363-170">A expressão de constante é avaliada da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="54363-170">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="54363-171">Se *expr* e *constant* forem tipos integrais, o operador de igualdade de C# determinará se a expressão retorna `true` (ou seja, se `expr == constant`).</span><span class="sxs-lookup"><span data-stu-id="54363-171">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="54363-172">Caso contrário, o valor da expressão será determinado por uma chamada ao método estático [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)).</span><span class="sxs-lookup"><span data-stu-id="54363-172">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>

<span data-ttu-id="54363-173">O exemplo a seguir usa o padrão de constante para determinar se uma data específica é um final de semana, o primeiro dia, o último dia ou o meio da semana de trabalho.</span><span class="sxs-lookup"><span data-stu-id="54363-173">The following example uses the constant pattern to determine whether a particular date is a weekend, the first day of the work week, the last day of the work week, or the middle of the work week.</span></span> <span data-ttu-id="54363-174">Ele avalia a propriedade <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> do dia atual em relação aos membros da enumeração <xref:System.DayOfWeek>.</span><span class="sxs-lookup"><span data-stu-id="54363-174">It evaluates the <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> property of the current day against the members of the <xref:System.DayOfWeek> enumeration.</span></span>

[!code-csharp[switch#7](../../../../samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

<span data-ttu-id="54363-175">O exemplo a seguir usa o padrão de constante para manipular a entrada do usuário em um aplicativo de console que simula uma máquina de café automática.</span><span class="sxs-lookup"><span data-stu-id="54363-175">The following example uses the constant pattern to handle user input in a console application that simulates an automatic coffee machine.</span></span>

[!code-csharp[switch#6](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]

### <a name="type-pattern"></a><span data-ttu-id="54363-176">Padrão de tipo</span><span class="sxs-lookup"><span data-stu-id="54363-176">Type pattern</span></span>

<span data-ttu-id="54363-177">O padrão de tipo permite a conversão e a avaliação do tipo concisa.</span><span class="sxs-lookup"><span data-stu-id="54363-177">The type pattern enables concise type evaluation and conversion.</span></span> <span data-ttu-id="54363-178">Quando usado com a instrução `switch` para realizar a correspondência de padrões, testa se uma expressão pode ser convertida para um tipo especificado e, se puder, o converte em uma variável desse tipo.</span><span class="sxs-lookup"><span data-stu-id="54363-178">When used with the `switch` statement to perform pattern matching, it tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="54363-179">A sintaxe é:</span><span class="sxs-lookup"><span data-stu-id="54363-179">Its syntax is:</span></span>

```csharp
   case type varname
```

<span data-ttu-id="54363-180">em que *type* é o nome do tipo no qual o resultado de *expr* deverá ser convertido e *varname* é o objeto para o qual o resultado de *expr* é convertido se a correspondência é bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="54363-180">where *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the match succeeds.</span></span>

<span data-ttu-id="54363-181">A expressão `case` será `true` se qualquer uma das condições seguintes for verdadeira:</span><span class="sxs-lookup"><span data-stu-id="54363-181">The `case` expression is `true` if any of the following is true:</span></span>

- <span data-ttu-id="54363-182">*expr* for uma instância do mesmo tipo que *type*.</span><span class="sxs-lookup"><span data-stu-id="54363-182">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="54363-183">*expr* for uma instância de um tipo derivado de *type*.</span><span class="sxs-lookup"><span data-stu-id="54363-183">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="54363-184">Em outras palavras, o resultado de *expr* pode sofrer upcast para uma instância de *type*.</span><span class="sxs-lookup"><span data-stu-id="54363-184">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="54363-185">*expr* tem um tipo de tempo de compilação que é uma classe base de *type* e *expr* tem um tipo de tempo de execução que é *type* ou é derivado de *type*.</span><span class="sxs-lookup"><span data-stu-id="54363-185">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="54363-186">O *tipo do tempo de compilação* de uma variável é o tipo da variável conforme definido em sua declaração de tipo.</span><span class="sxs-lookup"><span data-stu-id="54363-186">The *compile-time type* of a variable is the variable's type as defined in its type declaration.</span></span> <span data-ttu-id="54363-187">O *tipo de tempo de execução* de uma variável é o tipo da instância atribuída a essa variável.</span><span class="sxs-lookup"><span data-stu-id="54363-187">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="54363-188">*expr* é uma instância de um tipo que implementa a interface de *type*.</span><span class="sxs-lookup"><span data-stu-id="54363-188">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="54363-189">Se a expressão case for true, *varname* será definitivamente atribuído e terá o escopo local dentro da seção switch apenas.</span><span class="sxs-lookup"><span data-stu-id="54363-189">If the case expression is true, *varname* is definitely assigned and has local scope within the switch section only.</span></span>

<span data-ttu-id="54363-190">Observe que `null` não corresponde a um tipo.</span><span class="sxs-lookup"><span data-stu-id="54363-190">Note that `null` does not match a type.</span></span> <span data-ttu-id="54363-191">Para corresponder um `null`, use o seguinte rótulo `case`:</span><span class="sxs-lookup"><span data-stu-id="54363-191">To match a `null`, you use the following `case` label:</span></span>

```csharp
case null:
```

<span data-ttu-id="54363-192">O exemplo a seguir usa o padrão de tipo para fornecer informações sobre vários tipos de coleção.</span><span class="sxs-lookup"><span data-stu-id="54363-192">The following example uses the type pattern to provide information about various kinds of collection types.</span></span>

[!code-csharp[switch#5](../../../../samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

<span data-ttu-id="54363-193">Sem a correspondência de padrões, esse código pode ser escrito da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="54363-193">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="54363-194">O uso da correspondência de padrões de tipo produz um código mais compacto e legível eliminando a necessidade de testar se o resultado de uma conversão é um `null` ou executar conversões repetidas.</span><span class="sxs-lookup"><span data-stu-id="54363-194">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null` or to perform repeated casts.</span></span>

[!code-csharp[switch#6](../../../../samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="a-namewhen--the-case-statement-and-the-when-clause"></a><span data-ttu-id="54363-195"><a name="when" /> A instrução `case` e a cláusula `when`</span><span class="sxs-lookup"><span data-stu-id="54363-195"><a name="when" /> The `case` statement and the `when` clause</span></span>

<span data-ttu-id="54363-196">A partir do C# 7.0, como as instruções case não precisam ser mutuamente exclusivas, você pode usar a adição de uma cláusula `when` para especificar uma condição adicional que precisa ser atendida para que a instrução case seja avaliada como true.</span><span class="sxs-lookup"><span data-stu-id="54363-196">Starting with C# 7.0, because case statements need not be mutually exclusive, you can add a `when` clause to specify an additional condition that must be satisfied for the case statement to evaluate to true.</span></span> <span data-ttu-id="54363-197">A cláusula `when` pode ser qualquer expressão que retorna um valor booliano.</span><span class="sxs-lookup"><span data-stu-id="54363-197">The `when` clause can be any expression that returns a Boolean value.</span></span>

<span data-ttu-id="54363-198">O exemplo a seguir define uma classe `Shape` base, uma classe `Rectangle` que deriva de `Shape` e uma classe `Square` que deriva de `Rectangle`.</span><span class="sxs-lookup"><span data-stu-id="54363-198">The following example defines a base `Shape` class, a `Rectangle` class that derives from `Shape`, and a `Square` class that derives from `Rectangle`.</span></span> <span data-ttu-id="54363-199">Ele usa a cláusula `when` para garantir que o `ShowShapeInfo` trata um objeto `Rectangle` que recebeu comprimentos e larguras como um `Square` mesmo se ele não tiver sido instanciado como um objeto `Square`.</span><span class="sxs-lookup"><span data-stu-id="54363-199">It uses the `when` clause to ensure that the `ShowShapeInfo` treats a `Rectangle` object that has been assigned equal lengths and widths as a `Square` even if it has not been instantiated as a `Square` object.</span></span> <span data-ttu-id="54363-200">O método não tenta exibir informações a sobre um objeto que é `null` ou uma forma cuja área é zero.</span><span class="sxs-lookup"><span data-stu-id="54363-200">The method does not attempt to display information either about an object that is `null` or a shape whose area is zero.</span></span>

[!code-csharp[switch#8](../../../../samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]

<span data-ttu-id="54363-201">Observe que a cláusula `when` no exemplo que tenta testar se um objeto `Shape` é `null` não é executada.</span><span class="sxs-lookup"><span data-stu-id="54363-201">Note that the `when` clause in the example that attempts to test whether a `Shape` object is `null` does not execute.</span></span> <span data-ttu-id="54363-202">O padrão de tipo correto para testar um `null` é `case null:`.</span><span class="sxs-lookup"><span data-stu-id="54363-202">The correct type pattern to test for a `null` is `case null:`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="54363-203">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="54363-203">C# language specification</span></span>

<span data-ttu-id="54363-204">Para obter mais informações, consulte [A instrução switch](/dotnet/csharp/language-reference/language-specification/statements#the-switch-statement) na [Especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="54363-204">For more information, see [The switch statement](/dotnet/csharp/language-reference/language-specification/statements#the-switch-statement) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="54363-205">A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.</span><span class="sxs-lookup"><span data-stu-id="54363-205">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="54363-206">Consulte também</span><span class="sxs-lookup"><span data-stu-id="54363-206">See also</span></span>

- [<span data-ttu-id="54363-207">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="54363-207">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="54363-208">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="54363-208">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="54363-209">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="54363-209">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="54363-210">if-else</span><span class="sxs-lookup"><span data-stu-id="54363-210">if-else</span></span>](if-else.md)
- [<span data-ttu-id="54363-211">Correspondência Padrão</span><span class="sxs-lookup"><span data-stu-id="54363-211">Pattern Matching</span></span>](../../pattern-matching.md)