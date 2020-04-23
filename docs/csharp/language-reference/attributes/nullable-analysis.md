---
title: 'C# Atributos reservados: Análise estática anulada'
ms.date: 04/14/2020
description: Esses atributos são interpretados pelo compilador para fornecer melhor análise estática para tipos de referência anulados e não anulados.
ms.openlocfilehash: 33521133a6a01196e6e1ab9c3cdc191a24f1ecf3
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102704"
---
# <a name="reserved-attributes-contribute-to-the-compilers-null-state-static-analysis"></a><span data-ttu-id="d86f6-103">Atributos reservados contribuem para a análise estática do estado nulo do compilador</span><span class="sxs-lookup"><span data-stu-id="d86f6-103">Reserved attributes contribute to the compiler's null state static analysis</span></span>

<span data-ttu-id="d86f6-104">Em um contexto nulo, o compilador realiza análisees estáticas de código para determinar o estado nulo de todas as variáveis do tipo de referência:</span><span class="sxs-lookup"><span data-stu-id="d86f6-104">In a nullable context, the compiler performs static analysis of code to determine the null state of all reference type variables:</span></span>

- <span data-ttu-id="d86f6-105">*não nulo*: A análise estática determinou que a variável é atribuída a um valor não nulo.</span><span class="sxs-lookup"><span data-stu-id="d86f6-105">*not null*: Static analysis determined that the variable is assigned to a non-null value.</span></span>
- <span data-ttu-id="d86f6-106">*talvez nulo*: A análise estática não pode determinar que uma variável é atribuída a um valor não nulo.</span><span class="sxs-lookup"><span data-stu-id="d86f6-106">*maybe null*: Static analysis cannot determine that a variable is assigned a non-null value.</span></span>

<span data-ttu-id="d86f6-107">Você pode aplicar uma série de atributos que fornecem informações ao compilador sobre a semântica de suas APIs.</span><span class="sxs-lookup"><span data-stu-id="d86f6-107">You can apply a number of attributes that provide information to the compiler about the semantics of your APIs.</span></span> <span data-ttu-id="d86f6-108">Essas informações ajudam o compilador a realizar análises estáticas e determinar quando uma variável não é nula.</span><span class="sxs-lookup"><span data-stu-id="d86f6-108">That information helps the compiler perform static analysis and determine when a variable is not null.</span></span> <span data-ttu-id="d86f6-109">Este artigo fornece uma breve descrição de cada um desses atributos e como usá-los.</span><span class="sxs-lookup"><span data-stu-id="d86f6-109">This article provides a brief description of each of those attributes and how to use them.</span></span> <span data-ttu-id="d86f6-110">Todos os exemplos assumem C# 8.0 ou mais novo, e o código está em um contexto anulado.</span><span class="sxs-lookup"><span data-stu-id="d86f6-110">All the examples assume C# 8.0 or newer, and the code is in a nullable context.</span></span>

<span data-ttu-id="d86f6-111">Vamos começar com um exemplo familiar.</span><span class="sxs-lookup"><span data-stu-id="d86f6-111">Let's start with a familiar example.</span></span> <span data-ttu-id="d86f6-112">Imagine que sua biblioteca tem a seguinte API para recuperar uma seqüência de recursos:</span><span class="sxs-lookup"><span data-stu-id="d86f6-112">Imagine your library has the following API to retrieve a resource string:</span></span>

```csharp
bool TryGetMessage(string key, out string message)
```

<span data-ttu-id="d86f6-113">O exemplo anterior segue `Try*` o padrão familiar em .NET.</span><span class="sxs-lookup"><span data-stu-id="d86f6-113">The preceding example follows the familiar `Try*` pattern in .NET.</span></span> <span data-ttu-id="d86f6-114">Existem dois argumentos de referência `key` para `message` esta API: o e o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="d86f6-114">There are two reference arguments for this API: the `key` and the `message` parameter.</span></span> <span data-ttu-id="d86f6-115">Esta API tem as seguintes regras relativas à nulidade desses argumentos:</span><span class="sxs-lookup"><span data-stu-id="d86f6-115">This API has the following rules relating to the nullness of these arguments:</span></span>

- <span data-ttu-id="d86f6-116">Os chamadores `null` não devem `key`passar como argumento para .</span><span class="sxs-lookup"><span data-stu-id="d86f6-116">Callers shouldn't pass `null` as the argument for `key`.</span></span>
- <span data-ttu-id="d86f6-117">Os chamadores podem passar `null` uma variável `message`cujo valor é como o argumento para .</span><span class="sxs-lookup"><span data-stu-id="d86f6-117">Callers can pass a variable whose value is `null` as the argument for `message`.</span></span>
- <span data-ttu-id="d86f6-118">Se `TryGetMessage` o `true`método retornar, `message` o valor de não é nulo.</span><span class="sxs-lookup"><span data-stu-id="d86f6-118">If the `TryGetMessage` method returns `true`, the value of `message` isn't null.</span></span> <span data-ttu-id="d86f6-119">Se o valor `false,` de `message` devolução for o valor de (e seu estado nulo) é nulo.</span><span class="sxs-lookup"><span data-stu-id="d86f6-119">If the return value is `false,` the value of `message` (and its null state) is null.</span></span>

<span data-ttu-id="d86f6-120">A regra `key` para pode ser expressa `key` pelo tipo de variável: deve ser um tipo de referência não anulado.</span><span class="sxs-lookup"><span data-stu-id="d86f6-120">The rule for `key` can be expressed by the variable type: `key` should be a non-nullable reference type.</span></span> <span data-ttu-id="d86f6-121">O `message` parâmetro é mais complexo.</span><span class="sxs-lookup"><span data-stu-id="d86f6-121">The `message` parameter is more complex.</span></span> <span data-ttu-id="d86f6-122">Permite `null` como argumento, mas garante que, `out` no sucesso, esse argumento não é nulo.</span><span class="sxs-lookup"><span data-stu-id="d86f6-122">It allows `null` as the argument, but guarantees that, on success, that `out` argument isn't null.</span></span> <span data-ttu-id="d86f6-123">Para esses cenários, você precisa de um vocabulário mais rico para descrever as expectativas.</span><span class="sxs-lookup"><span data-stu-id="d86f6-123">For these scenarios, you need a richer vocabulary to describe the expectations.</span></span>

<span data-ttu-id="d86f6-124">Vários atributos foram adicionados para expressar informações adicionais sobre o estado nulo das variáveis.</span><span class="sxs-lookup"><span data-stu-id="d86f6-124">Several attributes have been added to express additional information about the null state of variables.</span></span> <span data-ttu-id="d86f6-125">Todo o código que você escreveu antes de C# 8 introduzir tipos de referência nulos foi *nulo alheio*.</span><span class="sxs-lookup"><span data-stu-id="d86f6-125">All code you wrote before C# 8 introduced nullable reference types was *null oblivious*.</span></span> <span data-ttu-id="d86f6-126">Isso significa que qualquer variável de tipo de referência pode ser nula, mas verificações nulas não são necessárias.</span><span class="sxs-lookup"><span data-stu-id="d86f6-126">That means any reference type variable may be null, but null checks aren't required.</span></span> <span data-ttu-id="d86f6-127">Uma vez que seu código é *anulado ciente,* essas regras mudam.</span><span class="sxs-lookup"><span data-stu-id="d86f6-127">Once your code is *nullable aware*, those rules change.</span></span> <span data-ttu-id="d86f6-128">Os tipos de `null` referência nunca devem ser o valor, e os tipos de referência anulados devem ser verificados `null` antes de serem desreferenciados.</span><span class="sxs-lookup"><span data-stu-id="d86f6-128">Reference types should never be the `null` value, and nullable reference types must be checked against `null` before being dereferenced.</span></span>

<span data-ttu-id="d86f6-129">As regras para suas APIs são provavelmente `TryGetValue` mais complicadas, como você viu com o cenário da API.</span><span class="sxs-lookup"><span data-stu-id="d86f6-129">The rules for your APIs are likely more complicated, as you saw with the `TryGetValue` API scenario.</span></span> <span data-ttu-id="d86f6-130">Muitas de suas APIs têm regras mais complexas para `null`quando as variáveis podem ou não ser .</span><span class="sxs-lookup"><span data-stu-id="d86f6-130">Many of your APIs have more complex rules for when variables can or can't be `null`.</span></span> <span data-ttu-id="d86f6-131">Nestes casos, você usará um dos seguintes atributos para expressar essas regras:</span><span class="sxs-lookup"><span data-stu-id="d86f6-131">In these cases, you'll use one of the following attributes to express those rules:</span></span>

- <span data-ttu-id="d86f6-132">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Um argumento de entrada não anulado pode ser nulo.</span><span class="sxs-lookup"><span data-stu-id="d86f6-132">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): A non-nullable input argument may be null.</span></span>
- <span data-ttu-id="d86f6-133">[DesautorizarNu:](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute)Um argumento de entrada nulo nunca deve ser nulo.</span><span class="sxs-lookup"><span data-stu-id="d86f6-133">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): A nullable input argument should never be null.</span></span>
- <span data-ttu-id="d86f6-134">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Um valor de retorno não anulado pode ser nulo.</span><span class="sxs-lookup"><span data-stu-id="d86f6-134">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): A non-nullable return value may be null.</span></span>
- <span data-ttu-id="d86f6-135">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): Um valor de retorno nulo nunca será nulo.</span><span class="sxs-lookup"><span data-stu-id="d86f6-135">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): A nullable return value will never be null.</span></span>
- <span data-ttu-id="d86f6-136">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Um argumento de entrada não anulado pode ser `bool` nulo quando o método retorna o valor especificado.</span><span class="sxs-lookup"><span data-stu-id="d86f6-136">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): A non-nullable input argument may be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="d86f6-137">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Um argumento de entrada anulado não será `bool` nulo quando o método retornar o valor especificado.</span><span class="sxs-lookup"><span data-stu-id="d86f6-137">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): A nullable input argument will not be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="d86f6-138">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Um valor de retorno não é nulo se o argumento para o parâmetro especificado não for nulo.</span><span class="sxs-lookup"><span data-stu-id="d86f6-138">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): A return value isn't null if the argument for the specified parameter isn't null.</span></span>
- <span data-ttu-id="d86f6-139">[Não Retorna:](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute)Um método nunca retorna.</span><span class="sxs-lookup"><span data-stu-id="d86f6-139">[DoesNotReturn](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute): A method never returns.</span></span> <span data-ttu-id="d86f6-140">Em outras palavras, sempre abre uma exceção.</span><span class="sxs-lookup"><span data-stu-id="d86f6-140">In other words, it always throws an exception.</span></span>
- <span data-ttu-id="d86f6-141">[Não RetornaSe](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute): Este método nunca `bool` retorna se o parâmetro associado tiver o valor especificado.</span><span class="sxs-lookup"><span data-stu-id="d86f6-141">[DoesNotReturnIf](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute): This method never returns if the associated `bool` parameter has the specified value.</span></span>

<span data-ttu-id="d86f6-142">As descrições anteriores são uma referência rápida ao que cada atributo faz.</span><span class="sxs-lookup"><span data-stu-id="d86f6-142">The preceding descriptions are a quick reference to what each attribute does.</span></span> <span data-ttu-id="d86f6-143">Cada seção a seguir descreve o comportamento e o significado mais detalhadamente.</span><span class="sxs-lookup"><span data-stu-id="d86f6-143">Each following section describes the behavior and meaning more thoroughly.</span></span>

<span data-ttu-id="d86f6-144">A adição desses atributos dá ao compilador mais informações sobre as regras para sua API.</span><span class="sxs-lookup"><span data-stu-id="d86f6-144">Adding these attributes gives the compiler more information about the rules for your API.</span></span> <span data-ttu-id="d86f6-145">Quando o código de chamada é compilado em um contexto ativado anulado, o compilador avisará os chamadores quando eles violarem essas regras.</span><span class="sxs-lookup"><span data-stu-id="d86f6-145">When calling code is compiled in a nullable enabled context, the compiler will warn callers when they violate those rules.</span></span> <span data-ttu-id="d86f6-146">Esses atributos não permitem verificações adicionais na sua implementação.</span><span class="sxs-lookup"><span data-stu-id="d86f6-146">These attributes don't enable additional checks on your implementation.</span></span>

## <a name="specify-preconditions-allownull-and-disallownull"></a><span data-ttu-id="d86f6-147">Especificar pré-condições: `AllowNull` e`DisallowNull`</span><span class="sxs-lookup"><span data-stu-id="d86f6-147">Specify preconditions: `AllowNull` and `DisallowNull`</span></span>

<span data-ttu-id="d86f6-148">Considere uma propriedade de leitura/gravação que nunca retorna `null` porque tem um valor padrão razoável.</span><span class="sxs-lookup"><span data-stu-id="d86f6-148">Consider a read/write property that never returns `null` because it has a reasonable default value.</span></span> <span data-ttu-id="d86f6-149">Os chamadores passam `null` para o acessório definido ao defini-lo para esse valor padrão.</span><span class="sxs-lookup"><span data-stu-id="d86f6-149">Callers pass `null` to the set accessor when setting it to that default value.</span></span> <span data-ttu-id="d86f6-150">Por exemplo, considere um sistema de mensagens que pede um nome de tela em uma sala de bate-papo.</span><span class="sxs-lookup"><span data-stu-id="d86f6-150">For example, consider a messaging system that asks for a screen name in a chat room.</span></span> <span data-ttu-id="d86f6-151">Se nenhum for fornecido, o sistema gera um nome aleatório:</span><span class="sxs-lookup"><span data-stu-id="d86f6-151">If none is provided, the system generates a random name:</span></span>

```csharp
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName;
```

<span data-ttu-id="d86f6-152">Quando você compila o código anterior em um contexto alheio nulo, tudo está bem.</span><span class="sxs-lookup"><span data-stu-id="d86f6-152">When you compile the preceding code in a nullable oblivious context, everything is fine.</span></span> <span data-ttu-id="d86f6-153">Uma vez habilitado tipos `ScreenName` de referência anulados, a propriedade se torna uma referência não anulada.</span><span class="sxs-lookup"><span data-stu-id="d86f6-153">Once you enable nullable reference types, the `ScreenName` property becomes a non-nullable reference.</span></span> <span data-ttu-id="d86f6-154">Isso é correto `get` para o acessório: ele nunca retorna `null`.</span><span class="sxs-lookup"><span data-stu-id="d86f6-154">That's correct for the `get` accessor: it never returns `null`.</span></span> <span data-ttu-id="d86f6-155">Os chamadores não precisam verificar a `null`propriedade devolvida para .</span><span class="sxs-lookup"><span data-stu-id="d86f6-155">Callers don't need to check the returned property for `null`.</span></span> <span data-ttu-id="d86f6-156">Mas agora definir `null` a propriedade para gera um aviso.</span><span class="sxs-lookup"><span data-stu-id="d86f6-156">But now setting the property to `null` generates a warning.</span></span> <span data-ttu-id="d86f6-157">Para continuar a suportar esse tipo de <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType> código, você adiciona o atributo à propriedade, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="d86f6-157">In order to continue to support this type of code, you add the <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType> attribute to the property, as shown in the following code:</span></span>

```csharp
[AllowNull]
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName = GenerateRandomScreenName();
```

<span data-ttu-id="d86f6-158">Você pode precisar `using` adicionar <xref:System.Diagnostics.CodeAnalysis> uma diretiva para usar este e outros atributos discutidos neste artigo.</span><span class="sxs-lookup"><span data-stu-id="d86f6-158">You may need to add a `using` directive for <xref:System.Diagnostics.CodeAnalysis> to use this and other attributes discussed in this article.</span></span> <span data-ttu-id="d86f6-159">O atributo é aplicado à `set` propriedade, não ao acessório.</span><span class="sxs-lookup"><span data-stu-id="d86f6-159">The attribute is applied to the property, not the `set` accessor.</span></span> <span data-ttu-id="d86f6-160">O `AllowNull` atributo especifica *pré-condições*e só se aplica a entradas.</span><span class="sxs-lookup"><span data-stu-id="d86f6-160">The `AllowNull` attribute specifies *pre-conditions*, and only applies to inputs.</span></span> <span data-ttu-id="d86f6-161">O `get` acessório tem um valor de retorno, mas sem argumentos de entrada.</span><span class="sxs-lookup"><span data-stu-id="d86f6-161">The `get` accessor has a return value, but no input arguments.</span></span> <span data-ttu-id="d86f6-162">Portanto, o `AllowNull` atributo só `set` se aplica ao acessório.</span><span class="sxs-lookup"><span data-stu-id="d86f6-162">Therefore, the `AllowNull` attribute only applies to the `set` accessor.</span></span>

<span data-ttu-id="d86f6-163">O exemplo anterior demonstra o que `AllowNull` procurar ao adicionar o atributo em um argumento:</span><span class="sxs-lookup"><span data-stu-id="d86f6-163">The preceding example demonstrates what to look for when adding the `AllowNull` attribute on an argument:</span></span>

1. <span data-ttu-id="d86f6-164">O contrato geral para essa variável é `null`que não deveria ser, então você quer um tipo de referência não anulado.</span><span class="sxs-lookup"><span data-stu-id="d86f6-164">The general contract for that variable is that it shouldn't be `null`, so you want a non-nullable reference type.</span></span>
1. <span data-ttu-id="d86f6-165">Existem cenários para a `null`variável de entrada ser , embora eles não sejam o uso mais comum.</span><span class="sxs-lookup"><span data-stu-id="d86f6-165">There are scenarios for the input variable to be `null`, though they aren't the most common usage.</span></span>

<span data-ttu-id="d86f6-166">Na maioria das vezes você precisará `in`deste `out`atributo para propriedades, ou , e `ref` argumentos.</span><span class="sxs-lookup"><span data-stu-id="d86f6-166">Most often you'll need this attribute for properties, or `in`, `out`, and `ref` arguments.</span></span> <span data-ttu-id="d86f6-167">O `AllowNull` atributo é a melhor escolha quando uma variável é `null` tipicamente não nula, mas você precisa permitir como uma pré-condição.</span><span class="sxs-lookup"><span data-stu-id="d86f6-167">The `AllowNull` attribute is the best choice when a variable is typically non-null, but you need to allow `null` as a precondition.</span></span>

<span data-ttu-id="d86f6-168">Contraste isso com `DisallowNull`cenários para usar : Você usa este atributo para especificar que uma variável de entrada de um tipo de referência anulada não deve ser `null`.</span><span class="sxs-lookup"><span data-stu-id="d86f6-168">Contrast that with scenarios for using `DisallowNull`: You use this attribute to specify that an input variable of a nullable reference type shouldn't be `null`.</span></span> <span data-ttu-id="d86f6-169">Considere um `null` imóvel onde está o valor padrão, mas os clientes só podem defini-lo como um valor não nulo.</span><span class="sxs-lookup"><span data-stu-id="d86f6-169">Consider a property where `null` is the default value, but clients can only set it to a non-null value.</span></span> <span data-ttu-id="d86f6-170">Considere o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="d86f6-170">Consider the following code:</span></span>

```csharp
public string ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string _comment;
```

<span data-ttu-id="d86f6-171">O código anterior é a melhor maneira `ReviewComment` de `null`expressar o seu design `null`que o poderia ser , mas não pode ser definido para .</span><span class="sxs-lookup"><span data-stu-id="d86f6-171">The preceding code is the best way to express your design that the `ReviewComment` could be `null`, but can't be set to `null`.</span></span> <span data-ttu-id="d86f6-172">Uma vez que este código esteja ciente nulo, você <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType>pode expressar este conceito mais claramente aos chamadores usando o :</span><span class="sxs-lookup"><span data-stu-id="d86f6-172">Once this code is nullable aware, you can express this concept more clearly to callers using the <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType>:</span></span>

```csharp
[DisallowNull]
public string? ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string? _comment;
```

<span data-ttu-id="d86f6-173">Em um contexto nulo, o `ReviewComment` `get` acessório `null`poderia retornar o valor padrão de .</span><span class="sxs-lookup"><span data-stu-id="d86f6-173">In a nullable context, the `ReviewComment` `get` accessor could return the default value of `null`.</span></span> <span data-ttu-id="d86f6-174">O compilador avisa que deve ser verificado antes do acesso.</span><span class="sxs-lookup"><span data-stu-id="d86f6-174">The compiler warns that it must be checked before access.</span></span> <span data-ttu-id="d86f6-175">Além disso, ele adverte os chamadores `null`que, embora possa ser, os `null`chamadores não devem explicitamente defini-lo para .</span><span class="sxs-lookup"><span data-stu-id="d86f6-175">Furthermore, it warns callers that, even though it could be `null`, callers shouldn't explicitly set it to `null`.</span></span> <span data-ttu-id="d86f6-176">O `DisallowNull` atributo também especifica uma *pré-condição,* não afeta o `get` acessório.</span><span class="sxs-lookup"><span data-stu-id="d86f6-176">The `DisallowNull` attribute also specifies a *pre-condition*, it does not affect the `get` accessor.</span></span> <span data-ttu-id="d86f6-177">Você usa `DisallowNull` o atributo quando observa essas características sobre:</span><span class="sxs-lookup"><span data-stu-id="d86f6-177">You use the `DisallowNull` attribute when you observe these characteristics about:</span></span>

1. <span data-ttu-id="d86f6-178">A variável `null` pode estar em cenários centrais, muitas vezes quando instanciado pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="d86f6-178">The variable could be `null` in core scenarios, often when first instantiated.</span></span>
1. <span data-ttu-id="d86f6-179">A variável não deve ser `null`explicitamente definida para .</span><span class="sxs-lookup"><span data-stu-id="d86f6-179">The variable shouldn't be explicitly set to `null`.</span></span>

<span data-ttu-id="d86f6-180">Essas situações são comuns em códigos que originalmente *eram nulos.*</span><span class="sxs-lookup"><span data-stu-id="d86f6-180">These situations are common in code that was originally *null oblivious*.</span></span> <span data-ttu-id="d86f6-181">Pode ser que as propriedades do objeto sejam definidas em duas operações de inicialização distintas.</span><span class="sxs-lookup"><span data-stu-id="d86f6-181">It may be that object properties are set in two distinct initialization operations.</span></span> <span data-ttu-id="d86f6-182">Pode ser que algumas propriedades sejam definidas somente após algum trabalho assíncrono ter sido concluído.</span><span class="sxs-lookup"><span data-stu-id="d86f6-182">It may be that some properties are set only after some asynchronous work has completed.</span></span>

<span data-ttu-id="d86f6-183">Os `AllowNull` `DisallowNull` atributos permitem especificar que as pré-condições nas variáveis podem não corresponder às anotações anuladas nessas variáveis.</span><span class="sxs-lookup"><span data-stu-id="d86f6-183">The `AllowNull` and `DisallowNull` attributes enable you to specify that preconditions on variables may not match the nullable annotations on those variables.</span></span> <span data-ttu-id="d86f6-184">Estes fornecem mais detalhes sobre as características de sua API.</span><span class="sxs-lookup"><span data-stu-id="d86f6-184">These provide more detail about the characteristics of your API.</span></span> <span data-ttu-id="d86f6-185">Essas informações adicionais ajudam os chamadores a usar sua API corretamente.</span><span class="sxs-lookup"><span data-stu-id="d86f6-185">This additional information helps callers use your API correctly.</span></span> <span data-ttu-id="d86f6-186">Lembre-se de especificar pré-condições usando os seguintes atributos:</span><span class="sxs-lookup"><span data-stu-id="d86f6-186">Remember you specify preconditions using the following attributes:</span></span>

- <span data-ttu-id="d86f6-187">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Um argumento de entrada não anulado pode ser nulo.</span><span class="sxs-lookup"><span data-stu-id="d86f6-187">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): A non-nullable input argument may be null.</span></span>
- <span data-ttu-id="d86f6-188">[DesautorizarNu:](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute)Um argumento de entrada nulo nunca deve ser nulo.</span><span class="sxs-lookup"><span data-stu-id="d86f6-188">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): A nullable input argument should never be null.</span></span>

## <a name="specify-post-conditions-maybenull-and-notnull"></a><span data-ttu-id="d86f6-189">Especificar pós-condições: `MaybeNull` e`NotNull`</span><span class="sxs-lookup"><span data-stu-id="d86f6-189">Specify post-conditions: `MaybeNull` and `NotNull`</span></span>

<span data-ttu-id="d86f6-190">Suponha que você tenha um método com a seguinte assinatura:</span><span class="sxs-lookup"><span data-stu-id="d86f6-190">Suppose you have a method with the following signature:</span></span>

```csharp
public Customer FindCustomer(string lastName, string firstName)
```

<span data-ttu-id="d86f6-191">Você provavelmente escreveu um método `null` como este para retornar quando o nome procurado não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="d86f6-191">You've likely written a method like this to return `null` when the name sought wasn't found.</span></span> <span data-ttu-id="d86f6-192">O `null` registro indica que o registro não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="d86f6-192">The `null` clearly indicates that the record wasn't found.</span></span> <span data-ttu-id="d86f6-193">Neste exemplo, você provavelmente mudaria o `Customer` `Customer?`tipo de retorno de .</span><span class="sxs-lookup"><span data-stu-id="d86f6-193">In this example, you'd likely change the return type from `Customer` to `Customer?`.</span></span> <span data-ttu-id="d86f6-194">Declarar o valor de retorno como um tipo de referência anulado especifica claramente a intenção desta API.</span><span class="sxs-lookup"><span data-stu-id="d86f6-194">Declaring the return value as a nullable reference type specifies the intent of this API clearly.</span></span>

<span data-ttu-id="d86f6-195">Por razões cobertas por [definições genéricas e nulidade](../../nullable-migration-strategies.md#generic-definitions-and-nullability) essa técnica não funciona com métodos genéricos.</span><span class="sxs-lookup"><span data-stu-id="d86f6-195">For reasons covered under [Generic definitions and nullability](../../nullable-migration-strategies.md#generic-definitions-and-nullability) that technique does not work with generic methods.</span></span> <span data-ttu-id="d86f6-196">Você pode ter um método genérico que segue um padrão semelhante:</span><span class="sxs-lookup"><span data-stu-id="d86f6-196">You may have a generic method that follows a similar pattern:</span></span>

```csharp
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

<span data-ttu-id="d86f6-197">Você não pode especificar que `T?`o valor de retorno é .</span><span class="sxs-lookup"><span data-stu-id="d86f6-197">You can't specify that the return value is `T?`.</span></span> <span data-ttu-id="d86f6-198">O método `null` retorna quando o item procurado não é encontrado.</span><span class="sxs-lookup"><span data-stu-id="d86f6-198">The method returns `null` when the sought item isn't found.</span></span> <span data-ttu-id="d86f6-199">Como você não pode `T?` declarar um tipo `MaybeNull` de retorno, você adiciona a anotação ao retorno do método:</span><span class="sxs-lookup"><span data-stu-id="d86f6-199">Since you can't declare a `T?` return type, you add the `MaybeNull` annotation to the method return:</span></span>

```csharp
[return: MaybeNull]
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

<span data-ttu-id="d86f6-200">O código precedente informa aos chamadores que o contrato implica um tipo não anulado, mas o valor de devolução *pode* realmente ser nulo.</span><span class="sxs-lookup"><span data-stu-id="d86f6-200">The preceding code informs callers that the contract implies a non-nullable type, but the return value *may* actually be null.</span></span>  <span data-ttu-id="d86f6-201">Use `MaybeNull` o atributo quando sua API deve ser um tipo não anulado, tipicamente `null` um parâmetro de tipo genérico, mas pode haver casos em que a Sua API seria devolvida.</span><span class="sxs-lookup"><span data-stu-id="d86f6-201">Use the `MaybeNull` attribute when your API should be a non-nullable type, typically a generic type parameter, but there may be instances where `null` would be returned.</span></span>

<span data-ttu-id="d86f6-202">Você também pode especificar que `out` `ref` um valor de retorno ou um argumento ou argumento não é nulo, mesmo que o tipo seja um tipo de referência anulado.</span><span class="sxs-lookup"><span data-stu-id="d86f6-202">You can also specify that a return value or an `out` or `ref` argument isn't null even though the type is a nullable reference type.</span></span> <span data-ttu-id="d86f6-203">Considere um método que garanta que uma matriz seja grande o suficiente para conter uma série de elementos.</span><span class="sxs-lookup"><span data-stu-id="d86f6-203">Consider a method that ensures an array is large enough to hold a number of elements.</span></span> <span data-ttu-id="d86f6-204">Se o argumento de entrada não tiver capacidade, a rotina alocaria uma nova matriz e copiaria todos os elementos existentes nele.</span><span class="sxs-lookup"><span data-stu-id="d86f6-204">If the input argument doesn't have capacity, the routine would allocate a new array and copy all the existing elements into it.</span></span> <span data-ttu-id="d86f6-205">Se o argumento `null`de entrada for, a rotina alocaria um novo armazenamento.</span><span class="sxs-lookup"><span data-stu-id="d86f6-205">If the input argument is `null`, the routine would allocate new storage.</span></span> <span data-ttu-id="d86f6-206">Se há capacidade suficiente, a rotina não faz nada:</span><span class="sxs-lookup"><span data-stu-id="d86f6-206">If there's sufficient capacity, the routine does nothing:</span></span>

```csharp
public void EnsureCapacity<T>(ref T[] storage, int size)
```

<span data-ttu-id="d86f6-207">Você pode chamar essa rotina da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="d86f6-207">You could call this routine as follows:</span></span>

```csharp
// messages has the default value (null) when EnsureCapacity is called:
EnsureCapacity<string>(ref messages, 10);
// messages is not null.
EnsureCapacity<string>(messages, 50);
```

<span data-ttu-id="d86f6-208">Depois de habilitar tipos de referência nulos, você deseja garantir que o código anterior seja compilado sem avisos.</span><span class="sxs-lookup"><span data-stu-id="d86f6-208">After enabling null reference types, you want to ensure that the preceding code compiles without warnings.</span></span> <span data-ttu-id="d86f6-209">Quando o método `storage` retorna, o argumento é garantido não ser nulo.</span><span class="sxs-lookup"><span data-stu-id="d86f6-209">When the method returns, the `storage` argument is guaranteed to be not null.</span></span> <span data-ttu-id="d86f6-210">No entanto, é aceitável `EnsureCapacity` ligar com uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="d86f6-210">However, it's acceptable to call `EnsureCapacity` with a null reference.</span></span> <span data-ttu-id="d86f6-211">Você pode `storage` fazer um tipo de `NotNull` referência anulada e adicionar a pós-condição à declaração de parâmetro:</span><span class="sxs-lookup"><span data-stu-id="d86f6-211">You can make `storage` a nullable reference type, and add the `NotNull` post-condition to the parameter declaration:</span></span>

```csharp
public void EnsureCapacity<T>([NotNull]ref T[]? storage, int size)
```

<span data-ttu-id="d86f6-212">O código anterior expressa claramente o contrato existente: os `null` chamadores podem passar uma variável com o valor, mas o valor de retorno é garantido para nunca ser nulo.</span><span class="sxs-lookup"><span data-stu-id="d86f6-212">The preceding code expresses the existing contract clearly: Callers can pass a variable with the `null` value, but the return value is guaranteed to never be null.</span></span> <span data-ttu-id="d86f6-213">O `NotNull` atributo é `ref` `out` mais útil `null` para e argumentos onde pode ser passado como argumento, mas esse argumento é garantido não ser nulo quando o método retorna.</span><span class="sxs-lookup"><span data-stu-id="d86f6-213">The `NotNull` attribute is most useful for `ref` and `out` arguments where `null` may be passed as an argument, but that argument is guaranteed to be not null when the method returns.</span></span>

<span data-ttu-id="d86f6-214">Você especifica postcondições incondicionais usando os seguintes atributos:</span><span class="sxs-lookup"><span data-stu-id="d86f6-214">You specify unconditional postconditions using the following attributes:</span></span>

- <span data-ttu-id="d86f6-215">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Um valor de retorno não anulado pode ser nulo.</span><span class="sxs-lookup"><span data-stu-id="d86f6-215">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): A non-nullable return value may be null.</span></span>
- <span data-ttu-id="d86f6-216">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): Um valor de retorno nulo nunca será nulo.</span><span class="sxs-lookup"><span data-stu-id="d86f6-216">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): A nullable return value will never be null.</span></span>

## <a name="specify-conditional-post-conditions-notnullwhen-maybenullwhen-and-notnullifnotnull"></a><span data-ttu-id="d86f6-217">Especificar pós-condições `NotNullWhen`condicionais: , `MaybeNullWhen`e`NotNullIfNotNull`</span><span class="sxs-lookup"><span data-stu-id="d86f6-217">Specify conditional post-conditions: `NotNullWhen`, `MaybeNullWhen`, and `NotNullIfNotNull`</span></span>

<span data-ttu-id="d86f6-218">Você provavelmente está `string` familiarizado <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>com o método.</span><span class="sxs-lookup"><span data-stu-id="d86f6-218">You're likely familiar with the `string` method <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>.</span></span> <span data-ttu-id="d86f6-219">Este método `true` retorna quando o argumento é nulo ou uma seqüência vazia.</span><span class="sxs-lookup"><span data-stu-id="d86f6-219">This method returns `true` when the argument is null or an empty string.</span></span> <span data-ttu-id="d86f6-220">É uma forma de verificação nula: os chamadores não precisam verificar `false`nulo o argumento se o método retornar .</span><span class="sxs-lookup"><span data-stu-id="d86f6-220">It's a form of null-check: Callers don't need to null-check the argument if the method returns `false`.</span></span> <span data-ttu-id="d86f6-221">Para tornar um método como este anulado, você definiria o argumento para `NotNullWhen` um tipo de referência anulado e adicionaria o atributo:</span><span class="sxs-lookup"><span data-stu-id="d86f6-221">To make a method like this nullable aware, you'd set the argument to a nullable reference type, and add the `NotNullWhen` attribute:</span></span>

```csharp
bool IsNullOrEmpty([NotNullWhen(false)]string? value);
```

<span data-ttu-id="d86f6-222">Isso informa o compilador de que qualquer `false` código onde o valor de devolução é não precisa ser verificado nulo.</span><span class="sxs-lookup"><span data-stu-id="d86f6-222">That informs the compiler that any code where the return value is `false` need not be null-checked.</span></span> <span data-ttu-id="d86f6-223">A adição do atributo informa a análise `IsNullOrEmpty` estática do compilador `false`que realiza a `null`verificação nula necessária: quando ele retorna, o argumento de entrada não é .</span><span class="sxs-lookup"><span data-stu-id="d86f6-223">The addition of the attribute informs the compiler's static analysis that `IsNullOrEmpty` performs the necessary null check: when it returns `false`, the input argument is not `null`.</span></span>

```csharp
string? userInput = GetUserInput();
if (!string.IsNullOrEmpty(userInput))
{
   int messageLength = userInput.Length; // no null check needed.
}
// null check needed on userInput here.
```

<span data-ttu-id="d86f6-224">O <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> método será anotado conforme mostrado acima para .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="d86f6-224">The <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> method will be annotated as shown above for .NET Core 3.0.</span></span> <span data-ttu-id="d86f6-225">Você pode ter métodos semelhantes em sua base de código que verificam o estado dos objetos em busca de valores nulos.</span><span class="sxs-lookup"><span data-stu-id="d86f6-225">You may have similar methods in your codebase that check the state of objects for null values.</span></span> <span data-ttu-id="d86f6-226">O compilador não reconhecerá métodos de verificação nulas personalizados, e você precisará adicionar as anotações você mesmo.</span><span class="sxs-lookup"><span data-stu-id="d86f6-226">The compiler won't recognize custom null check methods, and you'll need to add the annotations yourself.</span></span> <span data-ttu-id="d86f6-227">Quando você adiciona o atributo, a análise estática do compilador sabe quando a variável testada foi verificada.</span><span class="sxs-lookup"><span data-stu-id="d86f6-227">When you add the attribute, the compiler's static analysis knows when the tested variable has been null checked.</span></span>

<span data-ttu-id="d86f6-228">Outro uso para esses `Try*` atributos é o padrão.</span><span class="sxs-lookup"><span data-stu-id="d86f6-228">Another use for these attributes is the `Try*` pattern.</span></span> <span data-ttu-id="d86f6-229">As condições `ref` e `out` variáveis são comunicadas através do valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="d86f6-229">The postconditions for `ref` and `out` variables are communicated through the return value.</span></span> <span data-ttu-id="d86f6-230">Considere este método mostrado anteriormente:</span><span class="sxs-lookup"><span data-stu-id="d86f6-230">Consider this method shown earlier:</span></span>

```csharp
bool TryGetMessage(string key, out string message)
```

<span data-ttu-id="d86f6-231">O método anterior segue um idioma típico .NET: `message` o valor de retorno indica se foi definido como valor encontrado ou, se nenhuma mensagem for encontrada, para o valor padrão.</span><span class="sxs-lookup"><span data-stu-id="d86f6-231">The preceding method follows a typical .NET idiom: the return value indicates if `message` was set to the found value or, if no message is found, to the default value.</span></span> <span data-ttu-id="d86f6-232">Se o `true`método retornar, `message` o valor de não é nulo; caso contrário, o `message` método define como nulo.</span><span class="sxs-lookup"><span data-stu-id="d86f6-232">If the method returns `true`, the value of `message` isn't null; otherwise, the method sets `message` to null.</span></span>

<span data-ttu-id="d86f6-233">Você pode comunicar esse `NotNullWhen` idioma usando o atributo.</span><span class="sxs-lookup"><span data-stu-id="d86f6-233">You can communicate that idiom using the `NotNullWhen` attribute.</span></span> <span data-ttu-id="d86f6-234">Quando você atualizar a assinatura para `message` tipos `string?` de referência anulados, faça a e adicione um atributo:</span><span class="sxs-lookup"><span data-stu-id="d86f6-234">When you update the signature for nullable reference types, make `message` a `string?` and add an attribute:</span></span>

```csharp
bool TryGetMessage(string key, [NotNullWhen(true)] out string? message)
```

<span data-ttu-id="d86f6-235">No exemplo anterior, sabe-se que o valor de `message` não é nulo quando `TryGetMessage` retorna. `true`</span><span class="sxs-lookup"><span data-stu-id="d86f6-235">In the preceding example, the value of `message` is known to be not null when `TryGetMessage` returns `true`.</span></span> <span data-ttu-id="d86f6-236">Você deve anotar métodos semelhantes em sua base de código `null`da mesma forma: os argumentos `true`podem ser , e são conhecidos por não serem nulos quando o método retorna .</span><span class="sxs-lookup"><span data-stu-id="d86f6-236">You should annotate similar methods in your codebase in the same way: the arguments could be `null`, and are known to be not null when the method returns `true`.</span></span>

<span data-ttu-id="d86f6-237">Há um atributo final que você também pode precisar.</span><span class="sxs-lookup"><span data-stu-id="d86f6-237">There's one final attribute you may also need.</span></span> <span data-ttu-id="d86f6-238">Às vezes, o estado nulo de um valor de retorno depende do estado nulo de um ou mais argumentos de entrada.</span><span class="sxs-lookup"><span data-stu-id="d86f6-238">Sometimes the null state of a return value depends on the null state of one or more input arguments.</span></span> <span data-ttu-id="d86f6-239">Esses métodos retornarão um valor não nulo sempre `null`que determinados argumentos de entrada não forem .</span><span class="sxs-lookup"><span data-stu-id="d86f6-239">These methods will return a non-null value whenever certain input arguments aren't `null`.</span></span> <span data-ttu-id="d86f6-240">Para anotar corretamente esses métodos, `NotNullIfNotNull` você usa o atributo.</span><span class="sxs-lookup"><span data-stu-id="d86f6-240">To correctly annotate these methods, you use the `NotNullIfNotNull` attribute.</span></span> <span data-ttu-id="d86f6-241">Considere o seguinte método:</span><span class="sxs-lookup"><span data-stu-id="d86f6-241">Consider the following method:</span></span>

```csharp
string GetTopLevelDomainFromFullUrl(string url);
```

<span data-ttu-id="d86f6-242">Se `url` o argumento não é nulo, `null`a saída não é .</span><span class="sxs-lookup"><span data-stu-id="d86f6-242">If the `url` argument isn't null, the output isn't `null`.</span></span> <span data-ttu-id="d86f6-243">Uma vez que as referências anuladas são habilitadas, essa assinatura funciona corretamente, desde que sua API nunca aceite uma entrada nula.</span><span class="sxs-lookup"><span data-stu-id="d86f6-243">Once nullable references are enabled, that signature works correctly, provided your API never accepts a null input.</span></span> <span data-ttu-id="d86f6-244">No entanto, se a entrada pode ser nula, então o valor de devolução também pode ser nulo.</span><span class="sxs-lookup"><span data-stu-id="d86f6-244">However, if the input could be null, then return value could also be null.</span></span> <span data-ttu-id="d86f6-245">Portanto, você pode alterar a assinatura para o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="d86f6-245">Therefore, you could change the signature to the following code:</span></span>

```csharp
string? GetTopLevelDomainFromFullUrl(string? url);
```

<span data-ttu-id="d86f6-246">Isso também funciona, mas muitas vezes `null` forçará os chamadores a implementar verificações extras.</span><span class="sxs-lookup"><span data-stu-id="d86f6-246">That also works, but will often force callers to implement extra `null` checks.</span></span> <span data-ttu-id="d86f6-247">O contrato é que o `null` valor de `url` retorno `null`seria apenas quando o argumento de entrada é .</span><span class="sxs-lookup"><span data-stu-id="d86f6-247">The contract is that the return value would be `null` only when the input argument `url` is `null`.</span></span> <span data-ttu-id="d86f6-248">Para expressar esse contrato, você anotaria este método como mostrado no seguinte código:</span><span class="sxs-lookup"><span data-stu-id="d86f6-248">To express that contract, you would annotate this method as shown in the following code:</span></span>

```csharp
[return: NotNullIfNotNull("url")]
string? GetTopLevelDomainFromFullUrl(string? url);
```

<span data-ttu-id="d86f6-249">O valor de devolução e o argumento `?` foram ambos anotados com a indicação de que qualquer um poderia ser `null`.</span><span class="sxs-lookup"><span data-stu-id="d86f6-249">The return value and the argument have both been annotated with the `?` indicating that either could be `null`.</span></span> <span data-ttu-id="d86f6-250">O atributo esclarece ainda que o valor de `url` retorno não `null`será nulo quando o argumento não for .</span><span class="sxs-lookup"><span data-stu-id="d86f6-250">The attribute further clarifies that the return value won't be null when the `url` argument isn't `null`.</span></span>

<span data-ttu-id="d86f6-251">Você especifica postcondições condicionais usando esses atributos:</span><span class="sxs-lookup"><span data-stu-id="d86f6-251">You specify conditional postconditions using these attributes:</span></span>

- <span data-ttu-id="d86f6-252">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Um argumento de entrada não anulado pode ser `bool` nulo quando o método retorna o valor especificado.</span><span class="sxs-lookup"><span data-stu-id="d86f6-252">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): A non-nullable input argument may be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="d86f6-253">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Um argumento de entrada anulado não será `bool` nulo quando o método retornar o valor especificado.</span><span class="sxs-lookup"><span data-stu-id="d86f6-253">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): A nullable input argument will not be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="d86f6-254">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Um valor de retorno não é nulo se o argumento de entrada para o parâmetro especificado não for nulo.</span><span class="sxs-lookup"><span data-stu-id="d86f6-254">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): A return value isn't null if the input argument for the specified parameter isn't null.</span></span>

## <a name="verify-unreachable-code"></a><span data-ttu-id="d86f6-255">Verificar código inalcançável</span><span class="sxs-lookup"><span data-stu-id="d86f6-255">Verify unreachable code</span></span>

<span data-ttu-id="d86f6-256">Alguns métodos, normalmente ajudantes de exceção ou outros métodos de utilidade, sempre saem lançando uma exceção.</span><span class="sxs-lookup"><span data-stu-id="d86f6-256">Some methods, typically exception helpers or other utility methods, always exit by throwing an exception.</span></span> <span data-ttu-id="d86f6-257">Ou, um ajudante pode abrir uma exceção com base no valor de um argumento booleano.</span><span class="sxs-lookup"><span data-stu-id="d86f6-257">Or, a helper may throw an exception based on the value of a Boolean argument.</span></span>

<span data-ttu-id="d86f6-258">No primeiro caso, você `DoesNotReturn` pode adicionar o atributo à declaração do método.</span><span class="sxs-lookup"><span data-stu-id="d86f6-258">In the first case, you can add the `DoesNotReturn` attribute to the method declaration.</span></span> <span data-ttu-id="d86f6-259">O compilador ajuda você de três maneiras.</span><span class="sxs-lookup"><span data-stu-id="d86f6-259">The compiler helps you in three ways.</span></span> <span data-ttu-id="d86f6-260">Primeiro, o compilador emite um aviso se houver um caminho onde o método possa sair sem abrir uma exceção.</span><span class="sxs-lookup"><span data-stu-id="d86f6-260">First, the compiler issues a warning if there is a path where the method can exit without throwing an exception.</span></span> <span data-ttu-id="d86f6-261">Em segundo lugar, o compilador marca qualquer código após uma chamada `catch` para esse método como *inalcançável,* até que uma cláusula apropriada seja encontrada.</span><span class="sxs-lookup"><span data-stu-id="d86f6-261">Second, the compiler marks any code after a call to that method as *unreachable*, until an appropriate `catch` clause is encountered.</span></span> <span data-ttu-id="d86f6-262">Terceiro, o código inalcançável não afetará nenhum estado nulo.</span><span class="sxs-lookup"><span data-stu-id="d86f6-262">Third, the unreachable code won't affect any null states.</span></span> <span data-ttu-id="d86f6-263">Considere este método:</span><span class="sxs-lookup"><span data-stu-id="d86f6-263">Consider this method:</span></span>

```csharp
[DoesNotReturn]
private void FailFast()
{
   throw new InvalidOperationException();
}

public void SetState(object containedField)
{
   if (!isInitialized)
      FailFast();

   // unreachable code:
   this.field = containedField;
}
```

<span data-ttu-id="d86f6-264">No segundo caso, você `DoesNotReturnIf` adiciona o atributo a um parâmetro booleano do método.</span><span class="sxs-lookup"><span data-stu-id="d86f6-264">In the second case, you add the `DoesNotReturnIf` attribute to a Boolean parameter of the method.</span></span> <span data-ttu-id="d86f6-265">Você pode modificar o exemplo anterior da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="d86f6-265">You can modify the previous example as follows:</span></span>

```csharp
private void FailFast([DoesNotReturnIf(false)]bool isValid)
{
   if (!isValid)
       throw new InvalidOperationException();
}

public void SetState(object containedField)
{
   FailFast(isInitialized);

   // unreachable code when "isInitialized" is false:
   this.field = containedField;
}
```

## <a name="summary"></a><span data-ttu-id="d86f6-266">Resumo</span><span class="sxs-lookup"><span data-stu-id="d86f6-266">Summary</span></span>

<span data-ttu-id="d86f6-267">Adicionar tipos de referência anulados fornece um vocabulário inicial para descrever `null`suas expectativas de APIs para variáveis que poderiam ser .</span><span class="sxs-lookup"><span data-stu-id="d86f6-267">Adding nullable reference types provides an initial vocabulary to describe your APIs expectations for variables that could be `null`.</span></span> <span data-ttu-id="d86f6-268">Os atributos adicionais fornecem um vocabulário mais rico para descrever o estado nulo das variáveis como pré-condições e pós-condições.</span><span class="sxs-lookup"><span data-stu-id="d86f6-268">The additional attributes provide a richer vocabulary to describe the null state of variables as preconditions and postconditions.</span></span> <span data-ttu-id="d86f6-269">Esses atributos descrevem mais claramente suas expectativas e fornecem uma melhor experiência para os desenvolvedores que usam suas APIs.</span><span class="sxs-lookup"><span data-stu-id="d86f6-269">These attributes more clearly describe your expectations and provide a better experience for the developers using your APIs.</span></span>

<span data-ttu-id="d86f6-270">À medida que você atualiza bibliotecas para um contexto anulado, adicione esses atributos para orientar os usuários de suas APIs ao uso correto.</span><span class="sxs-lookup"><span data-stu-id="d86f6-270">As you update libraries for a nullable context, add these attributes to guide users of your APIs to the correct usage.</span></span> <span data-ttu-id="d86f6-271">Esses atributos ajudam a descrever completamente o estado nulo dos argumentos de entrada e valores de retorno:</span><span class="sxs-lookup"><span data-stu-id="d86f6-271">These attributes help you fully describe the null-state of input arguments and return values:</span></span>

- <span data-ttu-id="d86f6-272">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Um argumento de entrada não anulado pode ser nulo.</span><span class="sxs-lookup"><span data-stu-id="d86f6-272">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): A non-nullable input argument may be null.</span></span>
- <span data-ttu-id="d86f6-273">[DesautorizarNu:](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute)Um argumento de entrada nulo nunca deve ser nulo.</span><span class="sxs-lookup"><span data-stu-id="d86f6-273">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): A nullable input argument should never be null.</span></span>
- <span data-ttu-id="d86f6-274">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Um valor de retorno não anulado pode ser nulo.</span><span class="sxs-lookup"><span data-stu-id="d86f6-274">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): A non-nullable return value may be null.</span></span>
- <span data-ttu-id="d86f6-275">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): Um valor de retorno nulo nunca será nulo.</span><span class="sxs-lookup"><span data-stu-id="d86f6-275">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): A nullable return value will never be null.</span></span>
- <span data-ttu-id="d86f6-276">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Um argumento de entrada não anulado pode ser `bool` nulo quando o método retorna o valor especificado.</span><span class="sxs-lookup"><span data-stu-id="d86f6-276">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): A non-nullable input argument may be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="d86f6-277">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Um argumento de entrada anulado não será `bool` nulo quando o método retornar o valor especificado.</span><span class="sxs-lookup"><span data-stu-id="d86f6-277">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): A nullable input argument will not be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="d86f6-278">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Um valor de retorno não é nulo se o argumento de entrada para o parâmetro especificado não for nulo.</span><span class="sxs-lookup"><span data-stu-id="d86f6-278">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): A return value isn't null if the input argument for the specified parameter isn't null.</span></span>
- <span data-ttu-id="d86f6-279">[Não Retorna:](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute)Um método nunca retorna.</span><span class="sxs-lookup"><span data-stu-id="d86f6-279">[DoesNotReturn](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute): A method never returns.</span></span> <span data-ttu-id="d86f6-280">Em outras palavras, sempre abre uma exceção.</span><span class="sxs-lookup"><span data-stu-id="d86f6-280">In other words, it always throws an exception.</span></span>
- <span data-ttu-id="d86f6-281">[Não RetornaSe](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute): Este método nunca `bool` retorna se o parâmetro associado tiver o valor especificado.</span><span class="sxs-lookup"><span data-stu-id="d86f6-281">[DoesNotReturnIf](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute): This method never returns if the associated `bool` parameter has the specified value.</span></span>
