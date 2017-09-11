---
title: "Palavra-chave switch (Referência de C#)"
ms.date: 2017-03-07
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- switch_CSharpKeyword
- switch
- case
- case_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- switch statement [C#]
- switch keyword [C#]
- case statement [C#]
- default keyword [C#]
ms.assetid: 44bae8b8-8841-4d85-826b-8a94277daecb
caps.latest.revision: 47
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 387c8c7e44ab818ca97e686330746f50df091bb9
ms.openlocfilehash: 5c151e3bbd46212f1234d46ff05d389f2384ca0e
ms.contentlocale: pt-br
ms.lasthandoff: 08/01/2017

---
# <a name="switch-c-reference"></a><span data-ttu-id="21b85-102">switch (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="21b85-102">switch (C# Reference)</span></span>
<span data-ttu-id="21b85-103">`switch` é uma instrução de seleção que escolhe uma única *seção switch* para ser executada de uma lista de candidatas com base em uma correspondência de padrão com a *expressão de correspondência*.</span><span class="sxs-lookup"><span data-stu-id="21b85-103">`switch` is a selection statement that chooses a single *switch section* to execute from a list of candidates based on a pattern match with the *match expression*.</span></span> 
  
 <span data-ttu-id="21b85-104">[!code-cs[switch#1](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="21b85-104">[!code-cs[switch#1](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]</span></span>  

<span data-ttu-id="21b85-105">A instrução `switch` geralmente é usada como uma alternativa para um constructo [if-else](if-else.md) se uma única expressão é testada com três ou mais condições.</span><span class="sxs-lookup"><span data-stu-id="21b85-105">The `switch` statement is often used as an alternative to an [if-else](if-else.md) construct if a single expression is tested against three or more conditions.</span></span> <span data-ttu-id="21b85-106">Por exemplo, a instrução `switch` a seguir determina se uma variável do tipo `Color` tem um dos três valores:</span><span class="sxs-lookup"><span data-stu-id="21b85-106">For example, the following `switch` statement determines whether a variable of type `Color` has one of three values:</span></span> 

<span data-ttu-id="21b85-107">[!code-cs[switch#3](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="21b85-107">[!code-cs[switch#3](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]</span></span> 

<span data-ttu-id="21b85-108">Ele é equivalente ao exemplo a seguir que usa um constructo `if`-`else`.</span><span class="sxs-lookup"><span data-stu-id="21b85-108">It is equivalent to the following example that uses an `if`-`else` construct.</span></span> 

<span data-ttu-id="21b85-109">[!code-cs[switch#3a](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="21b85-109">[!code-cs[switch#3a](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]</span></span> 

## <a name="the-match-expression"></a><span data-ttu-id="21b85-110">A expressão de correspondência</span><span class="sxs-lookup"><span data-stu-id="21b85-110">The match expression</span></span>

<span data-ttu-id="21b85-111">A expressão de correspondência fornece o valor para corresponder aos padrões nos rótulos `case`.</span><span class="sxs-lookup"><span data-stu-id="21b85-111">The match expression provides the value to match against the patterns in `case` labels.</span></span> <span data-ttu-id="21b85-112">A sintaxe é:</span><span class="sxs-lookup"><span data-stu-id="21b85-112">Its syntax is:</span></span>

```csharp
   switch (expr)
```

<span data-ttu-id="21b85-113">No C# 6, a expressão de correspondência deve ser uma expressão que retorna um valor dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="21b85-113">In C# 6, the match expression must be an expression that returns a value of the following types:</span></span>

- <span data-ttu-id="21b85-114">um [char](char.md).</span><span class="sxs-lookup"><span data-stu-id="21b85-114">a [char](char.md).</span></span>
- <span data-ttu-id="21b85-115">um [string](string.md).</span><span class="sxs-lookup"><span data-stu-id="21b85-115">a [string](string.md).</span></span>
- <span data-ttu-id="21b85-116">um [bool](bool.md).</span><span class="sxs-lookup"><span data-stu-id="21b85-116">a [bool](bool.md).</span></span> 
- <span data-ttu-id="21b85-117">um valor de inteiro, como um [int](int.md) ou um [long](long.md).</span><span class="sxs-lookup"><span data-stu-id="21b85-117">an integral value, such as an [int](int.md) or a [long](long.md).</span></span>
- <span data-ttu-id="21b85-118">um valor [enum](enum.md).</span><span class="sxs-lookup"><span data-stu-id="21b85-118">an [enum](enum.md) value.</span></span>

<span data-ttu-id="21b85-119">Começando com o C# 7, a expressão de correspondência pode ser qualquer expressão não nula.</span><span class="sxs-lookup"><span data-stu-id="21b85-119">Starting with C# 7, the match expression can be any non-null expression.</span></span>
 
## <a name="the-switch-section"></a><span data-ttu-id="21b85-120">A seção switch</span><span class="sxs-lookup"><span data-stu-id="21b85-120">The switch section</span></span>
 
 <span data-ttu-id="21b85-121">Uma instrução `switch` inclui uma ou mais seções do comutador.</span><span class="sxs-lookup"><span data-stu-id="21b85-121">A `switch` statement includes one or more switch sections.</span></span> <span data-ttu-id="21b85-122">Cada seção switch contém um ou mais *rótulos case* seguidos por uma ou mais instruções.</span><span class="sxs-lookup"><span data-stu-id="21b85-122">Each switch section contains one or more *case labels* followed by one or more statements.</span></span> <span data-ttu-id="21b85-123">O exemplo a seguir mostra uma instrução `switch` simples que tem três seções switch.</span><span class="sxs-lookup"><span data-stu-id="21b85-123">The following example shows a simple `switch` statement that has three switch sections.</span></span> <span data-ttu-id="21b85-124">Cada seção switch tem um rótulo case, como `case 1:` e duas instruções.</span><span class="sxs-lookup"><span data-stu-id="21b85-124">Each switch section has one case label, such as `case 1:`, and two statements.</span></span>
 
  <span data-ttu-id="21b85-125">Uma instrução `switch` pode incluir qualquer número de seções switch e cada seção pode ter um ou mais rótulos case, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="21b85-125">A `switch` statement can include any number of switch sections, and each section can have one or more case labels, as shown in the following example.</span></span> <span data-ttu-id="21b85-126">No entanto, dois rótulos case não podem conter a mesma expressão.</span><span class="sxs-lookup"><span data-stu-id="21b85-126">However, no two case labels may contain the same expression.</span></span>  

 <span data-ttu-id="21b85-127">[!code-cs[switch#2](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="21b85-127">[!code-cs[switch#2](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]</span></span>  

 <span data-ttu-id="21b85-128">Apenas uma seção switch em uma instrução switch é executada.</span><span class="sxs-lookup"><span data-stu-id="21b85-128">Only one switch section in a switch statement executes.</span></span> <span data-ttu-id="21b85-129">O C# não permite que a execução continue de uma seção switch para a próxima.</span><span class="sxs-lookup"><span data-stu-id="21b85-129">C# does not allow execution to continue from one switch section to the next.</span></span> <span data-ttu-id="21b85-130">Por isso, o código a seguir gera um erro do compilador, CS0163: "O controle não pode passar de um rótulo case (<case label>) para outro".</span><span class="sxs-lookup"><span data-stu-id="21b85-130">Because of this, the following code generates a compiler error, CS0163: "Control cannot fall through from one case label (<case label>) to another."</span></span>   

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
<span data-ttu-id="21b85-131">Esse requisito é atendido normalmente saindo explicitamente da seção switch usando uma instrução [break](break.md), [goto](goto.md) ou [return](return.md).</span><span class="sxs-lookup"><span data-stu-id="21b85-131">This requirement is usually met by explicitly exiting the switch section by using a [break](break.md), [goto](goto.md), or [return](return.md) statement.</span></span> <span data-ttu-id="21b85-132">No entanto, o código a seguir também é válido, pois garante que o controle do programa não pode passar para a seção switch `default`.</span><span class="sxs-lookup"><span data-stu-id="21b85-132">However, the following code is also valid, because it ensures that program control cannot fall through to the `default` switch section.</span></span>
  
 <span data-ttu-id="21b85-133">[!code-cs[switch#4](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="21b85-133">[!code-cs[switch#4](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]</span></span>    
  
 <span data-ttu-id="21b85-134">A execução da lista de instruções na seção switch com um rótulo case que corresponde à expressão de correspondência começa com a primeira instrução e continua pela lista de instruções, normalmente até uma instrução de salto como `break`, `goto case`, `goto label`, `return` ou `throw` ser atingida.</span><span class="sxs-lookup"><span data-stu-id="21b85-134">Execution of the statement list in the switch section with a case label that matches the match expression begins with the first statement and proceeds through the statement list, typically until a jump statement, such as a `break`, `goto case`, `goto label`, `return`, or `throw`, is reached.</span></span> <span data-ttu-id="21b85-135">Nesse ponto, o controle é transferido para fora da instrução `switch` ou para outro rótulo case.</span><span class="sxs-lookup"><span data-stu-id="21b85-135">At that point, control is transferred outside the `switch` statement or to another case label.</span></span> <span data-ttu-id="21b85-136">Se uma instrução `goto` for usada, ela deverá transferir controle para um rótulo de constante.</span><span class="sxs-lookup"><span data-stu-id="21b85-136">A `goto` statement, if it is used, must transfer control to a constant label.</span></span> <span data-ttu-id="21b85-137">Essa restrição é necessária, já que tentar transferir o controle para um rótulo não constante pode ter efeitos colaterais indesejáveis, tais como transferência do controle para um local não intencional no código ou criação de um loop infinito.</span><span class="sxs-lookup"><span data-stu-id="21b85-137">This restriction is necessary, since attempting to transfer control to a non-constant label can have undesirable side-effects, such transferring control to an unintended location in code or creating an endless loop.</span></span>

## <a name="case-labels"></a><span data-ttu-id="21b85-138">Rótulos case</span><span class="sxs-lookup"><span data-stu-id="21b85-138">Case labels</span></span>

 <span data-ttu-id="21b85-139">Cada rótulo case especifica um padrão a ser comparado com a expressão de correspondência (a variável `caseSwitch` nos exemplos anteriores).</span><span class="sxs-lookup"><span data-stu-id="21b85-139">Each case label specifies a pattern to compare to the match expression (the `caseSwitch` variable in the previous examples).</span></span> <span data-ttu-id="21b85-140">Se eles corresponderem, o controle será transferido para a seção switch que contém o **primeiro** rótulo case correspondente.</span><span class="sxs-lookup"><span data-stu-id="21b85-140">If they match, control is transferred to the switch section that contains the **first** matching case label.</span></span> <span data-ttu-id="21b85-141">Se nenhum padrão de rótulo case corresponder à expressão de correspondência, o controle será transferido para a seção com o rótulo case `default`, se existir um.</span><span class="sxs-lookup"><span data-stu-id="21b85-141">If no case label pattern matches the match expression, control is transfered to the section with the `default` case label, if there is one.</span></span> <span data-ttu-id="21b85-142">Se não houver nenhum case `default`, nenhuma declaração em qualquer seção switch será executada e o controle será transferido para fora da instrução `switch`.</span><span class="sxs-lookup"><span data-stu-id="21b85-142">If there is no `default` case, no statements in any switch section are executed, and control is transferred outside the `switch` statement.</span></span>

 <span data-ttu-id="21b85-143">Para obter informações sobre a instrução `switch` e a correspondência de padrões, consulte a seção [Correspondência de padrões com a instrução `switch`](#pattern).</span><span class="sxs-lookup"><span data-stu-id="21b85-143">For information on the `switch` statement and pattern matching, see the [Pattern matching with the `switch` statement](#pattern) section.</span></span>

 <span data-ttu-id="21b85-144">Como o C# 6 dá suporte apenas ao padrão de constante e não permite a repetição de valores de constantes, os rótulos case definem valores mutuamente exclusivos e apenas um padrão pode corresponder à expressão de correspondência.</span><span class="sxs-lookup"><span data-stu-id="21b85-144">Because C# 6 supports only the constant pattern and does not allow the repetition of constant values, case labels define mutually exclusive values, and only one pattern can match the match expression.</span></span> <span data-ttu-id="21b85-145">Como resultado, a ordem na qual as instruções `case` aparecem não é importante.</span><span class="sxs-lookup"><span data-stu-id="21b85-145">As a result, the order in which `case` statements appear is unimportant.</span></span>

 <span data-ttu-id="21b85-146">No C# 7, no entanto, como outros padrões têm suporte, os rótulos case não precisam definir valores mutuamente exclusivos e vários padrões podem corresponder à expressão de correspondência.</span><span class="sxs-lookup"><span data-stu-id="21b85-146">In C# 7, however, because other patterns are supported, case labels need not define mutually exclusive values, and multiple patterns can match the match expression.</span></span> <span data-ttu-id="21b85-147">Como apenas as instruções na seção switch que contém o primeiro padrão de correspondência são executadas, a ordem na qual as instruções `case` aparecem agora é importante.</span><span class="sxs-lookup"><span data-stu-id="21b85-147">Because only the statements in the switch section that contains the first matching pattern are executed, the order in which `case` statements appear is now important.</span></span> <span data-ttu-id="21b85-148">Se o C# detecta uma seção switch cujas instruções case são equivalentes ou são subconjuntos de instruções anteriores, ele gera um erro do compilador, CS8120, “O switch case já foi tratado por um case anterior”.</span><span class="sxs-lookup"><span data-stu-id="21b85-148">If C# detects a switch section whose case statement or statements are equivalent to or are subsets of previous statements, it generates a compiler error, CS8120, "The switch case has already been handled by a previous case."</span></span> 

 <span data-ttu-id="21b85-149">O exemplo a seguir ilustra uma instrução `switch` que usa uma variedade de padrões não mutuamente exclusivos.</span><span class="sxs-lookup"><span data-stu-id="21b85-149">The following example illustrates a `switch` statement that uses a variety of non-mutually exclusive patterns.</span></span> <span data-ttu-id="21b85-150">Se você mover a seção switch `case 0:` para que ela não seja mais a primeira seção na instrução `switch`, o C# gera um erro do compilador porque um inteiro cujo valor é zero é um subconjunto de todos os inteiros, que é o padrão definido pela instrução `case int val`.</span><span class="sxs-lookup"><span data-stu-id="21b85-150">If you move the `case 0:` switch section so that it is no longer the first section in the `switch` statement, C# generates a compiler error because an integer whose value is zero is a subset of all integers, which is the pattern defined by the `case int val` statement.</span></span>

 <span data-ttu-id="21b85-151">[!code-cs[switch#5](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="21b85-151">[!code-cs[switch#5](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]</span></span>    

<span data-ttu-id="21b85-152">Você pode corrigir esse problema e eliminar o aviso do compilador em uma das duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="21b85-152">You can correct this issue and eliminate the compiler warning in one of two ways:</span></span>

- <span data-ttu-id="21b85-153">Alterando a ordem das seções switch.</span><span class="sxs-lookup"><span data-stu-id="21b85-153">By changing the order of the switch sections.</span></span> 
 
- <span data-ttu-id="21b85-154">Usando uma </a name="when">cláusula when</a> no rótulo `case`.</span><span class="sxs-lookup"><span data-stu-id="21b85-154">By using a </a name="when">when clause</a> in the `case` label.</span></span>
 
## <a name="the-default-case"></a><span data-ttu-id="21b85-155">O case `default`</span><span class="sxs-lookup"><span data-stu-id="21b85-155">The `default` case</span></span>

<span data-ttu-id="21b85-156">O case `default` especifica a seção switch a ser executada se a expressão de correspondência não corresponder a nenhum outro rótulo `case`.</span><span class="sxs-lookup"><span data-stu-id="21b85-156">The `default` case specifies the switch section to execute if the match expression does not match any other `case` label.</span></span> <span data-ttu-id="21b85-157">Se um case `default` não estiver presente e a expressão de correspondência não corresponder a nenhum outro rótulo `case`, o fluxo do programa passará pela instrução `switch`.</span><span class="sxs-lookup"><span data-stu-id="21b85-157">If a `default` case is not present and the match expression does not match any other `case` label, program flow falls through the `switch` statement.</span></span>

<span data-ttu-id="21b85-158">O case `default` pode aparecer em qualquer ordem na instrução `switch`.</span><span class="sxs-lookup"><span data-stu-id="21b85-158">The `default` case can appear in any order in the `switch` statement.</span></span> <span data-ttu-id="21b85-159">Independentemente de sua ordem no código-fonte, ele é sempre avaliado por último, afinal os rótulos `case` foram avaliados.</span><span class="sxs-lookup"><span data-stu-id="21b85-159">Regardless of its order in the source code, it is always evaluated last, after all `case` labels have been evaluated.</span></span>

## <a name="a-namepattern--pattern-matching-with-the-switch-statement"></a><span data-ttu-id="21b85-160"><a name="pattern" /> Correspondência de padrões com a instrução `switch`</span><span class="sxs-lookup"><span data-stu-id="21b85-160"><a name="pattern" /> Pattern matching with the `switch` statement</span></span>
  
<span data-ttu-id="21b85-161">Cada instrução `case` define um padrão que, se corresponde à expressão de correspondência, faz com que sua seção switch recipiente seja executada.</span><span class="sxs-lookup"><span data-stu-id="21b85-161">Each `case` statement defines a pattern that, if it matches the match expression, causes its  containing switch section to be executed.</span></span> <span data-ttu-id="21b85-162">Todas as versões do C# dão suporte ao padrão de constante.</span><span class="sxs-lookup"><span data-stu-id="21b85-162">All versions of C# support the constant pattern.</span></span> <span data-ttu-id="21b85-163">Os padrões restantes têm suporte a partir do C# 7.</span><span class="sxs-lookup"><span data-stu-id="21b85-163">The remaining patterns are supported beginning with C# 7.</span></span> 
  
### <a name="constant-pattern"></a><span data-ttu-id="21b85-164">Padrão de constante</span><span class="sxs-lookup"><span data-stu-id="21b85-164">Constant pattern</span></span> 

<span data-ttu-id="21b85-165">O padrão de constante testa se a expressão de correspondência é igual a uma constante especificada.</span><span class="sxs-lookup"><span data-stu-id="21b85-165">The constant pattern tests whether the match expression equals a specified constant.</span></span> <span data-ttu-id="21b85-166">A sintaxe é:</span><span class="sxs-lookup"><span data-stu-id="21b85-166">Its syntax is:</span></span>

```csharp
   case constant:
```

<span data-ttu-id="21b85-167">em que *constant* é o valor para testar.</span><span class="sxs-lookup"><span data-stu-id="21b85-167">where *constant* is the value to test for.</span></span> <span data-ttu-id="21b85-168">*constant* pode ser qualquer uma das expressões de constante a seguir:</span><span class="sxs-lookup"><span data-stu-id="21b85-168">*constant* can be any of the following constant expressions:</span></span> 

- <span data-ttu-id="21b85-169">Um literal [bool](bool.md), `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="21b85-169">A [bool](bool.md) literal, either `true` or `false`.</span></span>
- <span data-ttu-id="21b85-170">Qualquer constante integral, como um [int](int.md), um [long](long.md) ou um [byte](byte.md).</span><span class="sxs-lookup"><span data-stu-id="21b85-170">Any integral constant, such as an [int](int.md), a [long](long.md), or a [byte](byte.md).</span></span> 
- <span data-ttu-id="21b85-171">O nome de uma variável `const` declarada.</span><span class="sxs-lookup"><span data-stu-id="21b85-171">The name of a declared `const` variable.</span></span>
- <span data-ttu-id="21b85-172">Uma constante de enumeração.</span><span class="sxs-lookup"><span data-stu-id="21b85-172">An enumeration constant.</span></span>
- <span data-ttu-id="21b85-173">Um literal [char](char.md).</span><span class="sxs-lookup"><span data-stu-id="21b85-173">A [char](char.md) literal.</span></span>
- <span data-ttu-id="21b85-174">Um literal [string](string.md).</span><span class="sxs-lookup"><span data-stu-id="21b85-174">A [string](string.md) literal.</span></span>

<span data-ttu-id="21b85-175">A expressão de constante é avaliada da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="21b85-175">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="21b85-176">Se *expr* e *constant* forem tipos integrais, o operador de igualdade de C# determinará se a expressão retorna `true` (ou seja, se `expr == constant`).</span><span class="sxs-lookup"><span data-stu-id="21b85-176">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="21b85-177">Caso contrário, o valor da expressão será determinado por uma chamada ao método estático [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)).</span><span class="sxs-lookup"><span data-stu-id="21b85-177">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>  

<span data-ttu-id="21b85-178">O exemplo a seguir usa o padrão de constante para determinar se uma data específica é um final de semana, o primeiro dia, o último dia ou o meio da semana de trabalho.</span><span class="sxs-lookup"><span data-stu-id="21b85-178">The following example uses the constant pattern to determine whether a particular date is a weekend, the first day of the work week, the last day of the work week, or the middle of the work week.</span></span> <span data-ttu-id="21b85-179">Ela avalia a propriedade [DateTime.DayOfWeek](xref:System.DateTime.DayOfWeek) do dia atual em relação aos membros da enumeração @System.DayOfWeek.</span><span class="sxs-lookup"><span data-stu-id="21b85-179">It evaluates the [DateTime.DayOfWeek](xref:System.DateTime.DayOfWeek) property of the current day against the members of the @System.DayOfWeek enumeration.</span></span> 

<span data-ttu-id="21b85-180">[!code-cs[switch#7](../../../../samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="21b85-180">[!code-cs[switch#7](../../../../samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]</span></span>

<span data-ttu-id="21b85-181">O exemplo a seguir usa o padrão de constante para manipular a entrada do usuário em um aplicativo de console que simula uma máquina de café automática.</span><span class="sxs-lookup"><span data-stu-id="21b85-181">The following example uses the constant pattern to handle user input in a console application that simulates an automatic coffee machine.</span></span>
  
 <span data-ttu-id="21b85-182">[!code-cs[switch#6](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]</span><span class="sxs-lookup"><span data-stu-id="21b85-182">[!code-cs[switch#6](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]</span></span>  

### <a name="type-pattern"></a><span data-ttu-id="21b85-183">Padrão de tipo</span><span class="sxs-lookup"><span data-stu-id="21b85-183">Type pattern</span></span>

<span data-ttu-id="21b85-184">O padrão de tipo permite a conversão e a avaliação do tipo concisa.</span><span class="sxs-lookup"><span data-stu-id="21b85-184">The type pattern enables concise type evaluation and conversion.</span></span> <span data-ttu-id="21b85-185">Quando usado com a instrução `switch` para realizar a correspondência de padrões, testa se uma expressão pode ser convertida para um tipo especificado e, se puder, o converte em uma variável desse tipo.</span><span class="sxs-lookup"><span data-stu-id="21b85-185">When used with the `switch` statement to perform pattern matching, it tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="21b85-186">A sintaxe é:</span><span class="sxs-lookup"><span data-stu-id="21b85-186">Its syntax is:</span></span>

```csharp
   case type varname 
```
<span data-ttu-id="21b85-187">em que *type* é o nome do tipo no qual o resultado de *expr* deverá ser convertido e *varname* é o objeto para o qual o resultado de *expr* é convertido se a correspondência é bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="21b85-187">where *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the match succeeds.</span></span> 

<span data-ttu-id="21b85-188">A expressão `case` será `true` se qualquer uma das condições seguintes for verdadeira:</span><span class="sxs-lookup"><span data-stu-id="21b85-188">The `case` expression is `true` if any of the following is true:</span></span>

- <span data-ttu-id="21b85-189">*expr* for uma instância do mesmo tipo que *type*.</span><span class="sxs-lookup"><span data-stu-id="21b85-189">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="21b85-190">*expr* for uma instância de um tipo derivado de *type*.</span><span class="sxs-lookup"><span data-stu-id="21b85-190">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="21b85-191">Em outras palavras, o resultado de *expr* pode sofrer upcast para uma instância de *type*.</span><span class="sxs-lookup"><span data-stu-id="21b85-191">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="21b85-192">*expr* tem um tipo de tempo de compilação que é uma classe base de *type* e *expr* tem um tipo de tempo de execução que é *type* ou é derivado de *type*.</span><span class="sxs-lookup"><span data-stu-id="21b85-192">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="21b85-193">O *tipo do tempo de compilação* de uma variável é o tipo da variável conforme definido em sua declaração de tipo.</span><span class="sxs-lookup"><span data-stu-id="21b85-193">The *compile-time type* of a variable is the variable's type as defined in its type declaration.</span></span> <span data-ttu-id="21b85-194">O *tipo de tempo de execução* de uma variável é o tipo da instância atribuída a essa variável.</span><span class="sxs-lookup"><span data-stu-id="21b85-194">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="21b85-195">*expr* é uma instância de um tipo que implementa a interface de *type*.</span><span class="sxs-lookup"><span data-stu-id="21b85-195">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="21b85-196">Se a expressão case for true, *varname* será definitivamente atribuído e terá o escopo local dentro da seção switch apenas.</span><span class="sxs-lookup"><span data-stu-id="21b85-196">If the case expression is true, *varname* is definitely assigned and has local scope within the switch section only.</span></span>

<span data-ttu-id="21b85-197">Observe que `null` não corresponde a um tipo.</span><span class="sxs-lookup"><span data-stu-id="21b85-197">Note that `null` does not match a type.</span></span> <span data-ttu-id="21b85-198">Para corresponder um `null`, use o seguinte rótulo `case`:</span><span class="sxs-lookup"><span data-stu-id="21b85-198">To match a `null`, you use the following `case` label:</span></span>

```csharp
case null:
```
 
<span data-ttu-id="21b85-199">O exemplo a seguir usa o padrão de tipo para fornecer informações sobre vários tipos de coleção.</span><span class="sxs-lookup"><span data-stu-id="21b85-199">The following example uses the type pattern to provide information about various kinds of collection types.</span></span>

<span data-ttu-id="21b85-200">[!code-cs[switch#5](../../../../samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="21b85-200">[!code-cs[switch#5](../../../../samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]</span></span>

<span data-ttu-id="21b85-201">Sem a correspondência de padrões, esse código pode ser escrito da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="21b85-201">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="21b85-202">O uso da correspondência de padrões de tipo produz um código mais compacto e legível eliminando a necessidade de testar se o resultado de uma conversão é um `null` ou executar conversões repetidas.</span><span class="sxs-lookup"><span data-stu-id="21b85-202">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null` or to perform repeated casts.</span></span>  

<span data-ttu-id="21b85-203">[!code-cs[switch#6](../../../../samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="21b85-203">[!code-cs[switch#6](../../../../samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]</span></span>

## <a name="the-case-statement-and-the-when-clause"></a><span data-ttu-id="21b85-204">A instrução `case` e a cláusula `when`</span><span class="sxs-lookup"><span data-stu-id="21b85-204">The `case` statement and the `when` clause</span></span>

<span data-ttu-id="21b85-205">A partir do C# 7, como as instruções case não precisam ser mutuamente exclusivas, você pode usar a adição de uma cláusula `when` para especificar uma condição adicional que deve ser atendida para a instrução case ser avaliada como true.</span><span class="sxs-lookup"><span data-stu-id="21b85-205">Starting with C# 7, because case statements need not be mutually exclusive, you can use add a `when` clause to specify an additional condition that must be satisfied for the case statement to evaluate to true.</span></span> <span data-ttu-id="21b85-206">A cláusula `when` pode ser qualquer expressão que retorna um valor booliano.</span><span class="sxs-lookup"><span data-stu-id="21b85-206">The `when` clause can be any expression that returns a Boolean value.</span></span> <span data-ttu-id="21b85-207">Um dos usos mais comuns para a cláusula `when` é para impedir que uma seção switch seja executada quando o valor de uma expressão de correspondência é `null`.</span><span class="sxs-lookup"><span data-stu-id="21b85-207">One of the more common uses for the `when` clause is used to prevent a switch section from executing when the value of a match expression is `null`.</span></span> 

 <span data-ttu-id="21b85-208">O exemplo a seguir define uma classe `Shape` base, uma classe `Rectangle` que deriva de `Shape` e uma classe `Square` que deriva de `Rectangle`.</span><span class="sxs-lookup"><span data-stu-id="21b85-208">The following example defines a base `Shape` class, a `Rectangle` class that derives from `Shape`, and a `Square` class that derives from `Rectangle`.</span></span> <span data-ttu-id="21b85-209">Ele usa a cláusula `when` para garantir que o trata `ShowShapeInfo` um objeto `Rectangle` que recebeu comprimentos e larguras como um `Square` mesmo se ele não tiver sido instanciado como um objeto `Square`.</span><span class="sxs-lookup"><span data-stu-id="21b85-209">It uses the `when` clause to ensure that the `ShowShapeInfo` treats a `Rectangle` object that has been assigned equal lengths and widths as a `Square` even if is has not been instantiated as a `Square` object.</span></span> <span data-ttu-id="21b85-210">O método não tenta exibir informações a sobre um objeto que é `null` ou uma forma cuja área é zero.</span><span class="sxs-lookup"><span data-stu-id="21b85-210">The method does not attempt to display information either about an object that is `null` or a shape whose area is zero.</span></span> 

<span data-ttu-id="21b85-211">[!code-cs[switch#8](../../../../samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="21b85-211">[!code-cs[switch#8](../../../../samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]</span></span>
  
<span data-ttu-id="21b85-212">Observe que a cláusula `when` no exemplo que tenta testar se um objeto `Shape` é `null` não é executada.</span><span class="sxs-lookup"><span data-stu-id="21b85-212">Note that the `when` clause in the example that attempts to test whether a `Shape` object is `null` does not execute.</span></span> <span data-ttu-id="21b85-213">O padrão de tipo correto para testar um `null` é `case null:`.</span><span class="sxs-lookup"><span data-stu-id="21b85-213">The correct type pattern to test for a `null` is `case null:`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="21b85-214">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="21b85-214">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="21b85-215">Consulte também</span><span class="sxs-lookup"><span data-stu-id="21b85-215">See Also</span></span>  

 <span data-ttu-id="21b85-216">[Referência de C#](../index.md) </span><span class="sxs-lookup"><span data-stu-id="21b85-216">[C# Reference](../index.md) </span></span>  
 <span data-ttu-id="21b85-217">[Guia de Programação em C#](../../programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="21b85-217">[C# Programming Guide](../../programming-guide/index.md) </span></span>  
 <span data-ttu-id="21b85-218">[Palavras-chave de C#](index.md) </span><span class="sxs-lookup"><span data-stu-id="21b85-218">[C# Keywords](index.md) </span></span>  
 <span data-ttu-id="21b85-219">[if-else](if-else.md) </span><span class="sxs-lookup"><span data-stu-id="21b85-219">[if-else](if-else.md) </span></span>  
 [<span data-ttu-id="21b85-220">Correspondência Padrão</span><span class="sxs-lookup"><span data-stu-id="21b85-220">Pattern Matching</span></span>](../../pattern-matching.md)   
 

 

