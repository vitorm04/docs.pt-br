---
title: Novidades no C# 6 – Guia do C#
description: Aprenda os novos recursos da versão 6 do C#
ms.date: 12/12/2018
ms.openlocfilehash: 49247109bd1acbf697f5700b5cfe9a2b85393b2c
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68235720"
---
# <a name="whats-new-in-c-6"></a><span data-ttu-id="c9508-103">Novidades no C# 6</span><span class="sxs-lookup"><span data-stu-id="c9508-103">What's New in C# 6</span></span>

<span data-ttu-id="c9508-104">A versão 6.0 do C# tinha muitos recursos para melhorar a produtividade para desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="c9508-104">The 6.0 release of C# contained many features that improve productivity for developers.</span></span> <span data-ttu-id="c9508-105">O efeito geral desses recursos é que você escreve código mais conciso e também mais legível.</span><span class="sxs-lookup"><span data-stu-id="c9508-105">The overall effect of these features is that you write more concise code that is also more readable.</span></span> <span data-ttu-id="c9508-106">A sintaxe contém menos cerimônia para várias práticas comuns.</span><span class="sxs-lookup"><span data-stu-id="c9508-106">The syntax contains less ceremony for many common practices.</span></span> <span data-ttu-id="c9508-107">É mais fácil de ver a intenção do design com menos cerimônia.</span><span class="sxs-lookup"><span data-stu-id="c9508-107">It's easier to see the design intent with less ceremony.</span></span> <span data-ttu-id="c9508-108">Aprenda bem esses recursos para ser mais produtivo e escrever um código mais legível.</span><span class="sxs-lookup"><span data-stu-id="c9508-108">Learn these features well, and you'll be more productive and write more readable code.</span></span> <span data-ttu-id="c9508-109">Você pode se concentrar mais nos recursos do que nos constructos da linguagem.</span><span class="sxs-lookup"><span data-stu-id="c9508-109">You can concentrate more on your features than on the constructs of the language.</span></span>

<span data-ttu-id="c9508-110">O restante deste artigo oferece uma visão geral de cada um desses recursos, com um link para explorá-los.</span><span class="sxs-lookup"><span data-stu-id="c9508-110">The rest of this article provides an overview of each of these features, with a link to explore each feature.</span></span> <span data-ttu-id="c9508-111">Explore também os recursos em uma [exploração interativa sobre o C# 6](../tutorials/exploration/csharp-6.yml) na seção de tutoriais.</span><span class="sxs-lookup"><span data-stu-id="c9508-111">You can also explore the features in an [interactive exploration on C# 6](../tutorials/exploration/csharp-6.yml) in the tutorials section.</span></span>

## <a name="read-only-auto-properties"></a><span data-ttu-id="c9508-112">Propriedades automáticas somente leitura</span><span class="sxs-lookup"><span data-stu-id="c9508-112">Read-only auto-properties</span></span>

<span data-ttu-id="c9508-113">As *Propriedades automáticas somente leitura* fornecem uma sintaxe mais concisa para criar tipos imutáveis.</span><span class="sxs-lookup"><span data-stu-id="c9508-113">*Read-only auto-properties* provide a more concise syntax to create immutable types.</span></span> <span data-ttu-id="c9508-114">Você declara a propriedade automática apenas com um acessador get:</span><span class="sxs-lookup"><span data-stu-id="c9508-114">You declare the auto-property with only a get accessor:</span></span>

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

<span data-ttu-id="c9508-115">As propriedades `FirstName` e `LastName` só podem ser definidas no corpo de um construtor:</span><span class="sxs-lookup"><span data-stu-id="c9508-115">The `FirstName` and `LastName` properties can be set only in the body of a constructor:</span></span>

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

<span data-ttu-id="c9508-116">A tentativa de definir `LastName` em outro método gera um erro de compilação `CS0200`:</span><span class="sxs-lookup"><span data-stu-id="c9508-116">Trying to set `LastName` in another method generates a `CS0200` compilation error:</span></span>

```csharp
public class Student
{
    public string LastName { get;  }

    public void ChangeName(string newLastName)
    {
        // Generates CS0200: Property or indexer cannot be assigned to -- it is read only
        LastName = newLastName;
    }
}
```

<span data-ttu-id="c9508-117">Esse recurso habilita o suporte real à linguagem para criar tipos imutáveis e usar a sintaxe de propriedade automática mais concisa e conveniente.</span><span class="sxs-lookup"><span data-stu-id="c9508-117">This feature enables true language support for creating immutable types and uses the more concise and convenient auto-property syntax.</span></span>

<span data-ttu-id="c9508-118">Se a adição dessa sintaxe não remover um método acessível, essa será uma [alteração compatível com binário](version-update-considerations.md#binary-compatible-changes).</span><span class="sxs-lookup"><span data-stu-id="c9508-118">If adding this syntax doesn't remove an accessible method, it's a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>

## <a name="auto-property-initializers"></a><span data-ttu-id="c9508-119">Inicializadores de propriedade automática</span><span class="sxs-lookup"><span data-stu-id="c9508-119">Auto-property initializers</span></span>

<span data-ttu-id="c9508-120">Os *Inicializadores de propriedade automática* permitem que você declare o valor inicial de uma propriedade automática como parte da declaração de propriedade.</span><span class="sxs-lookup"><span data-stu-id="c9508-120">*Auto-property initializers* let you declare the initial value for an auto-property as part of the property declaration.</span></span>

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

<span data-ttu-id="c9508-121">O membro `Grades` é inicializado no local em que é declarado.</span><span class="sxs-lookup"><span data-stu-id="c9508-121">The `Grades` member is initialized where it's declared.</span></span> <span data-ttu-id="c9508-122">Isso facilita realizar a inicialização exatamente uma vez.</span><span class="sxs-lookup"><span data-stu-id="c9508-122">That makes it easier to perform the initialization exactly once.</span></span> <span data-ttu-id="c9508-123">A inicialização faz parte da declaração de propriedade, tornando mais fácil igualar a alocação de armazenamento com a interface pública para objetos `Student`.</span><span class="sxs-lookup"><span data-stu-id="c9508-123">The initialization is part of the property declaration, making it easier to equate the storage allocation with the public interface for `Student` objects.</span></span>

## <a name="expression-bodied-function-members"></a><span data-ttu-id="c9508-124">Membros de função aptos para expressão</span><span class="sxs-lookup"><span data-stu-id="c9508-124">Expression-bodied function members</span></span>

<span data-ttu-id="c9508-125">Muitos membros que você escreve são instruções simples que poderiam ser expressões simples.</span><span class="sxs-lookup"><span data-stu-id="c9508-125">Many members that you write are single statements that could be single expressions.</span></span> <span data-ttu-id="c9508-126">Nesse caso, escreva um membro apto para expressão.</span><span class="sxs-lookup"><span data-stu-id="c9508-126">Write an expression-bodied member instead.</span></span> <span data-ttu-id="c9508-127">Isso funciona para métodos e propriedades somente leitura.</span><span class="sxs-lookup"><span data-stu-id="c9508-127">It works for methods and read-only properties.</span></span> <span data-ttu-id="c9508-128">Por exemplo, uma substituição de `ToString()` é, geralmente, uma ótima candidata:</span><span class="sxs-lookup"><span data-stu-id="c9508-128">For example, an override of `ToString()` is often a great candidate:</span></span>

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

<span data-ttu-id="c9508-129">Você também pode usar essa sintaxe para propriedades somente leitura:</span><span class="sxs-lookup"><span data-stu-id="c9508-129">You can also use this syntax for read-only properties:</span></span>

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

<span data-ttu-id="c9508-130">A alteração de um membro existente para um membro de corpo da expressão é uma [alteração compatível com binário](version-update-considerations.md#binary-compatible-changes).</span><span class="sxs-lookup"><span data-stu-id="c9508-130">Changing an existing member to an expression bodied member is a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>

## <a name="using-static"></a><span data-ttu-id="c9508-131">usando estático</span><span class="sxs-lookup"><span data-stu-id="c9508-131">using static</span></span>

<span data-ttu-id="c9508-132">O aprimoramento *using static* permite que você importe os métodos estáticos de uma única classe.</span><span class="sxs-lookup"><span data-stu-id="c9508-132">The *using static* enhancement enables you to import the static methods of a single class.</span></span> <span data-ttu-id="c9508-133">Você especifica a classe que está usando:</span><span class="sxs-lookup"><span data-stu-id="c9508-133">You specify the class you're using:</span></span>

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

<span data-ttu-id="c9508-134">O <xref:System.Math> não contém nenhum método de instância.</span><span class="sxs-lookup"><span data-stu-id="c9508-134">The <xref:System.Math> does not contain any instance methods.</span></span> <span data-ttu-id="c9508-135">Você também pode usar `using static` para importar os métodos estáticos de uma classe para uma classe que tem os métodos estáticos e de instância.</span><span class="sxs-lookup"><span data-stu-id="c9508-135">You can also use `using static` to import a class' static methods for a class that has both static and instance methods.</span></span> <span data-ttu-id="c9508-136">Um dos exemplos mais úteis é <xref:System.String>:</span><span class="sxs-lookup"><span data-stu-id="c9508-136">One of the most useful examples is <xref:System.String>:</span></span>

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> <span data-ttu-id="c9508-137">Você precisa usar o nome de classe totalmente qualificado, `System.String` em uma instrução using estática.</span><span class="sxs-lookup"><span data-stu-id="c9508-137">You must use the fully qualified class name, `System.String`  in a static using statement.</span></span>  <span data-ttu-id="c9508-138">Não é possível usar a palavra-chave `string` em vez disso.</span><span class="sxs-lookup"><span data-stu-id="c9508-138">You cannot use the `string` keyword instead.</span></span>

<span data-ttu-id="c9508-139">Quando importados de uma instrução `static using`, os métodos de extensão apenas estão no escopo quando chamados usando a sintaxe de invocação de método de extensão.</span><span class="sxs-lookup"><span data-stu-id="c9508-139">When imported from a `static using` statement, extension methods are only in scope when called using the extension method invocation syntax.</span></span> <span data-ttu-id="c9508-140">Eles não estão no escopo quando chamados como um método estático.</span><span class="sxs-lookup"><span data-stu-id="c9508-140">They aren't in scope when called as a static method.</span></span> <span data-ttu-id="c9508-141">Você verá isso com frequência em consultas LINQ.</span><span class="sxs-lookup"><span data-stu-id="c9508-141">You'll often see this in LINQ queries.</span></span> <span data-ttu-id="c9508-142">Você pode importar o padrão LINQ importando <xref:System.Linq.Enumerable> ou <xref:System.Linq.Queryable>.</span><span class="sxs-lookup"><span data-stu-id="c9508-142">You can import the LINQ pattern by importing <xref:System.Linq.Enumerable>, or <xref:System.Linq.Queryable>.</span></span>

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

<span data-ttu-id="c9508-143">Normalmente, os métodos de extensão são chamados usando expressões de invocação de método de extensão.</span><span class="sxs-lookup"><span data-stu-id="c9508-143">You typically call extension methods using extension method invocation expressions.</span></span> <span data-ttu-id="c9508-144">No caso raro em que você os chama usando a sintaxe de chamada de método estático, adicione o nome de classe para resolver a ambiguidade.</span><span class="sxs-lookup"><span data-stu-id="c9508-144">Adding the class name in the rare case where you call them using static method call syntax resolves ambiguity.</span></span>

<span data-ttu-id="c9508-145">A diretiva `static using` também importa todos tipos aninhados.</span><span class="sxs-lookup"><span data-stu-id="c9508-145">The `static using` directive also imports any nested types.</span></span> <span data-ttu-id="c9508-146">Você pode referenciar qualquer tipo aninhado sem qualificação.</span><span class="sxs-lookup"><span data-stu-id="c9508-146">You can reference any nested types without qualification.</span></span>

## <a name="null-conditional-operators"></a><span data-ttu-id="c9508-147">Operadores condicionais null</span><span class="sxs-lookup"><span data-stu-id="c9508-147">Null-conditional operators</span></span>

<span data-ttu-id="c9508-148">O *operador condicional nulo* torna as verificações de nulos muito mais fáceis e fluidas.</span><span class="sxs-lookup"><span data-stu-id="c9508-148">The *null conditional operator* makes null checks much easier and fluid.</span></span> <span data-ttu-id="c9508-149">Substitua o acesso do membro `.` por `?.`:</span><span class="sxs-lookup"><span data-stu-id="c9508-149">Replace the member access `.` with `?.`:</span></span>

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

<span data-ttu-id="c9508-150">No exemplo anterior, a variável `first` é atribuída como `null` se o objeto person é `null`.</span><span class="sxs-lookup"><span data-stu-id="c9508-150">In the preceding example, the variable `first` is assigned `null` if the person object is `null`.</span></span> <span data-ttu-id="c9508-151">Caso contrário, ele receberá o valor da propriedade `FirstName`.</span><span class="sxs-lookup"><span data-stu-id="c9508-151">Otherwise, it is assigned the value of the `FirstName` property.</span></span> <span data-ttu-id="c9508-152">Mais importante, o `?.` significa que essa linha de código não gera uma `NullReferenceException` quando a variável `person` é `null`.</span><span class="sxs-lookup"><span data-stu-id="c9508-152">Most importantly, the `?.` means that this line of code doesn't generate a `NullReferenceException` if the `person` variable is `null`.</span></span> <span data-ttu-id="c9508-153">Em vez disso, ele causa um curto-circuito e retorna `null`.</span><span class="sxs-lookup"><span data-stu-id="c9508-153">Instead, it short-circuits and returns `null`.</span></span> <span data-ttu-id="c9508-154">Você também pode usar um operador condicional nulo para acesso de matriz ou de indexador.</span><span class="sxs-lookup"><span data-stu-id="c9508-154">You can also use a null conditional operator for array or indexer access.</span></span> <span data-ttu-id="c9508-155">Substitua `[]` por `?[]` na expressão do índice.</span><span class="sxs-lookup"><span data-stu-id="c9508-155">Replace `[]` with `?[]` in the index expression.</span></span>

<span data-ttu-id="c9508-156">A seguinte expressão retorna um `string`, independentemente do valor de `person`.</span><span class="sxs-lookup"><span data-stu-id="c9508-156">The following expression returns a `string`, regardless of the value of `person`.</span></span> <span data-ttu-id="c9508-157">Geralmente esse constructo é usado com o operador de *união nulo* para atribuir valores padrão quando uma das propriedades é `null`.</span><span class="sxs-lookup"><span data-stu-id="c9508-157">You often use this construct with the *null coalescing* operator to assign default values when one of the properties is `null`.</span></span> <span data-ttu-id="c9508-158">Quando a expressão causa um curto-circuito, o valor de `null` retornado é tipado para corresponder à expressão completa.</span><span class="sxs-lookup"><span data-stu-id="c9508-158">When the expression short-circuits, the `null` value returned is typed to match the full expression.</span></span>

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

<span data-ttu-id="c9508-159">Você também pode usar o `?.` para invocar métodos condicionalmente.</span><span class="sxs-lookup"><span data-stu-id="c9508-159">You can also use `?.` to conditionally invoke methods.</span></span> <span data-ttu-id="c9508-160">O uso mais comum das funções de membro com o operador condicional nulo é invocar delegados (ou manipuladores de eventos) com segurança que podem ser `null`.</span><span class="sxs-lookup"><span data-stu-id="c9508-160">The most common use of member functions  with the null conditional operator is to safely invoke delegates (or event handlers) that may be `null`.</span></span>  <span data-ttu-id="c9508-161">Você chamará o método `Invoke` do delegado usando o operador `?.` para acessar o membro.</span><span class="sxs-lookup"><span data-stu-id="c9508-161">You'll call the delegate's `Invoke` method using the `?.` operator to access the member.</span></span> <span data-ttu-id="c9508-162">Veja um exemplo no artigo [padrões de delegado](../delegates-patterns.md#handling-null-delegates).</span><span class="sxs-lookup"><span data-stu-id="c9508-162">You can see an example in the [delegate patterns](../delegates-patterns.md#handling-null-delegates) article.</span></span>

<span data-ttu-id="c9508-163">As regras do operador `?.` garantem que o lado esquerdo do operador é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="c9508-163">The rules of the `?.` operator ensure that the left-hand side of the operator is evaluated only once.</span></span> <span data-ttu-id="c9508-164">Isso permite diversas expressões, incluindo o exemplo a seguir usando manipuladores de eventos:</span><span class="sxs-lookup"><span data-stu-id="c9508-164">It enables many idioms, including the following example using event handlers:</span></span>

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

<span data-ttu-id="c9508-165">Garantir que o lado esquerdo seja avaliado apenas uma vez também permite que você use qualquer expressão, inclusive chamadas de método, no lado esquerdo do `?.`</span><span class="sxs-lookup"><span data-stu-id="c9508-165">Ensuring that the left side is evaluated only once also enables you to use any expression, including method calls, on the left side of the `?.`</span></span>

## <a name="string-interpolation"></a><span data-ttu-id="c9508-166">Interpolação de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="c9508-166">String interpolation</span></span>

<span data-ttu-id="c9508-167">Com o C# 6, o novo recurso de [interpolação de cadeia de caracteres](../language-reference/tokens/interpolated.md) permite que você insira as expressões em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c9508-167">With C# 6, the new [string interpolation](../language-reference/tokens/interpolated.md) feature enables you to embed expressions in a string.</span></span> <span data-ttu-id="c9508-168">Basta preceder a cadeia de caracteres com `$` e usar expressões entre `{` e `}` em vez de ordinais:</span><span class="sxs-lookup"><span data-stu-id="c9508-168">Simply preface the string with `$`and use expressions between `{` and `}` instead of ordinals:</span></span>

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

<span data-ttu-id="c9508-169">Este exemplo usa propriedades para as expressões substituídas.</span><span class="sxs-lookup"><span data-stu-id="c9508-169">This example uses properties for the substituted expressions.</span></span> <span data-ttu-id="c9508-170">Você pode usar qualquer expressão.</span><span class="sxs-lookup"><span data-stu-id="c9508-170">You can use any expression.</span></span> <span data-ttu-id="c9508-171">Por exemplo, você pode calcular a média do aluno como parte da interpolação:</span><span class="sxs-lookup"><span data-stu-id="c9508-171">For example, you could compute a student's grade point average as part of the interpolation:</span></span>

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

<span data-ttu-id="c9508-172">A linha de código anterior formata o valor de `Grades.Average()` como um número de ponto flutuante com duas casas decimais.</span><span class="sxs-lookup"><span data-stu-id="c9508-172">The preceding line of code formats the value for `Grades.Average()` as a floating-point number with two decimal places.</span></span>

<span data-ttu-id="c9508-173">Muitas vezes, pode ser necessário formatar a cadeia de caracteres produzida usando uma cultura específica.</span><span class="sxs-lookup"><span data-stu-id="c9508-173">Often, you may need to format the string produced using a specific culture.</span></span> <span data-ttu-id="c9508-174">Aproveite o fato de que o objeto produzido por uma interpolação de cadeia de caracteres pode ser convertido implicitamente em <xref:System.FormattableString?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c9508-174">You use the fact that the object produced by a string interpolation can be implicitly converted to <xref:System.FormattableString?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c9508-175">A instância de <xref:System.FormattableString> contém a cadeia de caracteres de formato composto e os resultados da avaliação das expressões antes da conversão delas em cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c9508-175">The <xref:System.FormattableString> instance contains the composite format string and the results of evaluating the expressions before converting them to strings.</span></span> <span data-ttu-id="c9508-176">Use o método <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> para especificar a cultura ao formatar uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="c9508-176">Use the <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> method to specify the culture when formatting a string.</span></span> <span data-ttu-id="c9508-177">O exemplo a seguir produz uma cadeia de caracteres usando a cultura de-DE (alemão).</span><span class="sxs-lookup"><span data-stu-id="c9508-177">The following example produces a string using the German (de-DE) culture.</span></span> <span data-ttu-id="c9508-178">(Por padrão, a cultura alemã usa o caractere ',' para o separador decimal e o caractere '.' como o separador de milhares.)</span><span class="sxs-lookup"><span data-stu-id="c9508-178">(By default, the German culture uses the ',' character for the decimal separator, and the '.' character as the thousands separator.)</span></span>

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

<span data-ttu-id="c9508-179">Para familiarizar-se com a interpolação de cadeia de caracteres, confira o tutorial interativo [Interpolação de cadeia de caracteres em C#](../tutorials/exploration/interpolated-strings.yml), o artigo [Interpolação de cadeia de caracteres](../language-reference/tokens/interpolated.md) e o tutorial [Interpolação de cadeia de caracteres em C#](../tutorials/string-interpolation.md).</span><span class="sxs-lookup"><span data-stu-id="c9508-179">To get started with string interpolation, see the [String interpolation in C#](../tutorials/exploration/interpolated-strings.yml) interactive tutorial, the [String interpolation](../language-reference/tokens/interpolated.md) article, and the [String interpolation in C#](../tutorials/string-interpolation.md) tutorial.</span></span>

## <a name="exception-filters"></a><span data-ttu-id="c9508-180">Filtros de exceção</span><span class="sxs-lookup"><span data-stu-id="c9508-180">Exception filters</span></span>

<span data-ttu-id="c9508-181">Os *Filtros de Exceção* são cláusulas que determinam quando uma determinada cláusula catch deve ser aplicada.</span><span class="sxs-lookup"><span data-stu-id="c9508-181">*Exception Filters* are clauses that determine when a given catch clause should be applied.</span></span> <span data-ttu-id="c9508-182">Se a expressão usada para um filtro de exceção é avaliada como `true`, a cláusula catch realiza seu processamento normal em uma exceção.</span><span class="sxs-lookup"><span data-stu-id="c9508-182">If the expression used for an exception filter evaluates to `true`, the catch clause performs its normal processing on an exception.</span></span> <span data-ttu-id="c9508-183">Se a expressão for avaliada como `false`, a cláusula `catch` será ignorada.</span><span class="sxs-lookup"><span data-stu-id="c9508-183">If the expression evaluates to `false`, then the `catch` clause is skipped.</span></span> <span data-ttu-id="c9508-184">Um uso é examinar informações sobre uma exceção para determinar se uma cláusula `catch` pode processar a exceção:</span><span class="sxs-lookup"><span data-stu-id="c9508-184">One use is to examine information about an exception to determine if a `catch` clause can process the exception:</span></span>

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

## <a name="the-nameof-expression"></a><span data-ttu-id="c9508-185">A expressão `nameof`</span><span class="sxs-lookup"><span data-stu-id="c9508-185">The `nameof` expression</span></span>

<span data-ttu-id="c9508-186">A expressão [nameof](../language-reference/operators/nameof.md) é avaliada como o nome de um símbolo.</span><span class="sxs-lookup"><span data-stu-id="c9508-186">The [nameof](../language-reference/operators/nameof.md) expression evaluates to the name of a symbol.</span></span> <span data-ttu-id="c9508-187">É uma ótima maneira de fazer com que as ferramentas funcionem sempre que você precisar do nome de uma variável, de uma propriedade ou de um campo de membro.</span><span class="sxs-lookup"><span data-stu-id="c9508-187">It's a great way to get tools working whenever you need the name of a variable, a property, or a member field.</span></span> <span data-ttu-id="c9508-188">Um dos usos mais comuns para `nameof` é fornecer o nome de um símbolo que causou uma exceção:</span><span class="sxs-lookup"><span data-stu-id="c9508-188">One of the most common uses for `nameof` is to provide the name of a symbol that caused an exception:</span></span>

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

<span data-ttu-id="c9508-189">Outro uso é com aplicativos baseados em XAML que implementam a interface `INotifyPropertyChanged`:</span><span class="sxs-lookup"><span data-stu-id="c9508-189">Another use is with XAML-based applications that implement the `INotifyPropertyChanged` interface:</span></span>

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

## <a name="await-in-catch-and-finally-blocks"></a><span data-ttu-id="c9508-190">Await em blocos catch e finally</span><span class="sxs-lookup"><span data-stu-id="c9508-190">Await in Catch and Finally blocks</span></span>

<span data-ttu-id="c9508-191">O C# 5 tinha várias limitações quanto ao local em que você poderia colocar expressões `await`.</span><span class="sxs-lookup"><span data-stu-id="c9508-191">C# 5 had several limitations around where you could place `await` expressions.</span></span> <span data-ttu-id="c9508-192">Com o C# 6, agora você pode usar `await` em expressões `catch` ou `finally`.</span><span class="sxs-lookup"><span data-stu-id="c9508-192">With C# 6, you can now use `await` in `catch` or `finally` expressions.</span></span> <span data-ttu-id="c9508-193">Isso geralmente é usado com cenários de registro em log:</span><span class="sxs-lookup"><span data-stu-id="c9508-193">This is most often used with logging scenarios:</span></span>

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

<span data-ttu-id="c9508-194">Os detalhes de implementação para adicionar o suporte ao `await` dentro das cláusulas `catch` e `finally` garante que o comportamento seja consistente com o comportamento do código síncrono.</span><span class="sxs-lookup"><span data-stu-id="c9508-194">The implementation details for adding `await` support inside `catch` and `finally` clauses ensure that the behavior is consistent with the behavior for synchronous code.</span></span> <span data-ttu-id="c9508-195">Quando o código que é executado em uma cláusula `catch` ou `finally` realiza o lançamento, a execução procura por uma cláusula `catch` adequada no próximo bloco.</span><span class="sxs-lookup"><span data-stu-id="c9508-195">When code executed in a `catch` or `finally` clause throws, execution looks for a suitable `catch` clause in the next surrounding block.</span></span> <span data-ttu-id="c9508-196">Se houver uma exceção atual, essa exceção será perdida.</span><span class="sxs-lookup"><span data-stu-id="c9508-196">If there was a current exception, that exception is lost.</span></span> <span data-ttu-id="c9508-197">O mesmo acontece com expressões aguardadas em cláusulas `catch` e `finally`: um `catch` adequado é pesquisado e a exceção atual, se houver, será perdida.</span><span class="sxs-lookup"><span data-stu-id="c9508-197">The same happens with awaited expressions in `catch` and `finally` clauses: a suitable `catch` is searched for, and the current exception, if any, is lost.</span></span>  

> [!NOTE]
> <span data-ttu-id="c9508-198">Esse comportamento é a razão pela qual recomenda-se escrever cláusulas `catch` e `finally` com cuidado, a fim de evitar introduzir novas exceções.</span><span class="sxs-lookup"><span data-stu-id="c9508-198">This behavior is the reason it's recommended to write `catch` and `finally` clauses carefully, to avoid introducing new exceptions.</span></span>

## <a name="initialize-associative-collections-using-indexers"></a><span data-ttu-id="c9508-199">Inicializar coleções associativas usando indexadores</span><span class="sxs-lookup"><span data-stu-id="c9508-199">Initialize associative collections using indexers</span></span>

<span data-ttu-id="c9508-200">Os *inicializadores de índice* são um dos dois recursos que deixam os inicializadores de coleção mais consistentes com o uso do índice.</span><span class="sxs-lookup"><span data-stu-id="c9508-200">*Index Initializers* is one of two features that make collection initializers more consistent with index usage.</span></span> <span data-ttu-id="c9508-201">Nas versões anteriores do C#, era possível usar *inicializadores de coleção* com coleções de estilo de sequência, incluindo <xref:System.Collections.Generic.Dictionary%602>, colocando os pares chave-valor entre chaves:</span><span class="sxs-lookup"><span data-stu-id="c9508-201">In earlier releases of C#, you could use *collection initializers* with sequence style collections, including <xref:System.Collections.Generic.Dictionary%602>, by adding braces around key and value pairs:</span></span>

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#CollectionInitializer)]

<span data-ttu-id="c9508-202">Você pode usá-los com coleções <xref:System.Collections.Generic.Dictionary%602> e outros tipos nos quais o método `Add` acessível aceite mais de um argumento.</span><span class="sxs-lookup"><span data-stu-id="c9508-202">You can use them with <xref:System.Collections.Generic.Dictionary%602> collections and other types where the accessible `Add` method accepts more than one argument.</span></span> <span data-ttu-id="c9508-203">A nova sintaxe permite a atribuição usando um índice na coleção:</span><span class="sxs-lookup"><span data-stu-id="c9508-203">The new syntax supports assignment using an index into the collection:</span></span>

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

<span data-ttu-id="c9508-204">Esse recurso significa que os contêineres associativos podem ser inicializados usando uma sintaxe semelhante à que está em vigor para contêineres de sequência de várias versões.</span><span class="sxs-lookup"><span data-stu-id="c9508-204">This feature means that associative containers can be initialized using syntax similar to what's been in place for sequence containers for several versions.</span></span>

## <a name="extension-add-methods-in-collection-initializers"></a><span data-ttu-id="c9508-205">Métodos `Add` de extensão em inicializadores de coleção</span><span class="sxs-lookup"><span data-stu-id="c9508-205">Extension `Add` methods in collection initializers</span></span>

<span data-ttu-id="c9508-206">Outro recurso que facilita a inicialização de coleção é a capacidade de usar um *método de extensão* para o método `Add`.</span><span class="sxs-lookup"><span data-stu-id="c9508-206">Another feature that makes collection initialization easier is the ability to use an *extension method* for the `Add` method.</span></span> <span data-ttu-id="c9508-207">Esse recurso foi adicionado para a paridade com o Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c9508-207">This feature was added for parity with Visual Basic.</span></span> <span data-ttu-id="c9508-208">O recurso é mais útil quando você tem uma classe de coleção personalizada que tem um método com um nome diferente para adicionar novos itens semanticamente.</span><span class="sxs-lookup"><span data-stu-id="c9508-208">The feature is most useful when you have a custom collection class that has a method with a different name to semantically add new items.</span></span>

## <a name="improved-overload-resolution"></a><span data-ttu-id="c9508-209">Resolução de sobrecarga aprimorada</span><span class="sxs-lookup"><span data-stu-id="c9508-209">Improved overload resolution</span></span>

<span data-ttu-id="c9508-210">Esse último recurso provavelmente não será notado.</span><span class="sxs-lookup"><span data-stu-id="c9508-210">This last feature is one you probably won't notice.</span></span> <span data-ttu-id="c9508-211">Havia constructos nos quais a versão anterior do compilador do C# pode ter encontrado algumas chamadas de método que envolviam expressões lambda ambíguas.</span><span class="sxs-lookup"><span data-stu-id="c9508-211">There were constructs where the previous version of the C# compiler may have found some method calls involving lambda expressions ambiguous.</span></span> <span data-ttu-id="c9508-212">Considere este método:</span><span class="sxs-lookup"><span data-stu-id="c9508-212">Consider this method:</span></span>

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

<span data-ttu-id="c9508-213">Em versões anteriores do C#, haveria uma falha ao chamar esse método usando a sintaxe de grupo de método:</span><span class="sxs-lookup"><span data-stu-id="c9508-213">In earlier versions of C#, calling that method using the method group syntax would fail:</span></span>

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]

<span data-ttu-id="c9508-214">O compilador anterior não conseguia distinguir corretamente entre `Task.Run(Action)` e `Task.Run(Func<Task>())`.</span><span class="sxs-lookup"><span data-stu-id="c9508-214">The earlier compiler couldn't distinguish correctly between `Task.Run(Action)` and `Task.Run(Func<Task>())`.</span></span> <span data-ttu-id="c9508-215">Nas versões anteriores, você precisava usar uma expressão lambda como um argumento:</span><span class="sxs-lookup"><span data-stu-id="c9508-215">In previous versions, you'd need to use a lambda expression as an argument:</span></span>

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

<span data-ttu-id="c9508-216">O compilador do C# 6 determina corretamente que `Task.Run(Func<Task>())` é uma opção melhor.</span><span class="sxs-lookup"><span data-stu-id="c9508-216">The C# 6 compiler correctly determines that `Task.Run(Func<Task>())` is a better choice.</span></span>

### <a name="deterministic-compiler-output"></a><span data-ttu-id="c9508-217">Saída do compilador determinístico</span><span class="sxs-lookup"><span data-stu-id="c9508-217">Deterministic compiler output</span></span>

<span data-ttu-id="c9508-218">A opção `-deterministic` instrui o compilador a produzir um assembly de saída idêntico byte a byte para compilações sucessivas dos mesmos arquivos de origem.</span><span class="sxs-lookup"><span data-stu-id="c9508-218">The `-deterministic` option instructs the compiler to produce a byte-for-byte identical output assembly for successive compilations of the same source files.</span></span>

<span data-ttu-id="c9508-219">Por padrão, cada compilação produz uma saída exclusiva em cada compilação.</span><span class="sxs-lookup"><span data-stu-id="c9508-219">By default, every compilation produces unique output on each compilation.</span></span> <span data-ttu-id="c9508-220">O compilador adiciona um carimbo de data/hora e um GUID gerado com base em números aleatórios.</span><span class="sxs-lookup"><span data-stu-id="c9508-220">The compiler adds a timestamp, and a GUID generated from random numbers.</span></span> <span data-ttu-id="c9508-221">Use essa opção se desejar comparar a saída byte a byte para garantir a consistência nos builds.</span><span class="sxs-lookup"><span data-stu-id="c9508-221">You use this option if you want to compare the byte-for-byte output to ensure consistency across builds.</span></span>

<span data-ttu-id="c9508-222">Para obter mais informações, confira o artigo [Opção do compilador -deterministic](../language-reference/compiler-options/deterministic-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="c9508-222">For more information, see the [-deterministic compiler option](../language-reference/compiler-options/deterministic-compiler-option.md) article.</span></span>
