---
title: 'Atributos reservados do C#: análise estática anulável'
ms.date: 04/14/2020
description: Esses atributos são interpretados pelo compilador para fornecer uma análise estática melhor para tipos de referência anuláveis e não anuláveis.
ms.openlocfilehash: d2405162ece3df209111de65fdef54f70cc86d45
ms.sourcegitcommit: 1e8382d0ce8b5515864f8fbb178b9fd692a7503f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89656296"
---
# <a name="reserved-attributes-contribute-to-the-compilers-null-state-static-analysis"></a><span data-ttu-id="b8a89-103">Atributos reservados contribuem para a análise estática do estado nulo do compilador</span><span class="sxs-lookup"><span data-stu-id="b8a89-103">Reserved attributes contribute to the compiler's null state static analysis</span></span>

<span data-ttu-id="b8a89-104">Em um contexto anulável, o compilador executa a análise estática de código para determinar o estado nulo de todas as variáveis de tipo de referência:</span><span class="sxs-lookup"><span data-stu-id="b8a89-104">In a nullable context, the compiler performs static analysis of code to determine the null state of all reference type variables:</span></span>

- <span data-ttu-id="b8a89-105">*NOT NULL*: a análise estática determinou que a variável foi atribuída a um valor não nulo.</span><span class="sxs-lookup"><span data-stu-id="b8a89-105">*not null*: Static analysis determined that the variable is assigned to a non-null value.</span></span>
- <span data-ttu-id="b8a89-106">*talvez NULL*: a análise estática não pode determinar que uma variável é atribuída a um valor não nulo.</span><span class="sxs-lookup"><span data-stu-id="b8a89-106">*maybe null*: Static analysis cannot determine that a variable is assigned a non-null value.</span></span>

<span data-ttu-id="b8a89-107">Você pode aplicar um número de atributos que fornecem informações ao compilador sobre a semântica de suas APIs.</span><span class="sxs-lookup"><span data-stu-id="b8a89-107">You can apply a number of attributes that provide information to the compiler about the semantics of your APIs.</span></span> <span data-ttu-id="b8a89-108">Essas informações ajudam o compilador a executar análise estática e determinar quando uma variável não é nula.</span><span class="sxs-lookup"><span data-stu-id="b8a89-108">That information helps the compiler perform static analysis and determine when a variable is not null.</span></span> <span data-ttu-id="b8a89-109">Este artigo fornece uma breve descrição de cada um desses atributos e como usá-los.</span><span class="sxs-lookup"><span data-stu-id="b8a89-109">This article provides a brief description of each of those attributes and how to use them.</span></span> <span data-ttu-id="b8a89-110">Todos os exemplos pressupõem C# 8,0 ou mais recente e o código está em um contexto anulável.</span><span class="sxs-lookup"><span data-stu-id="b8a89-110">All the examples assume C# 8.0 or newer, and the code is in a nullable context.</span></span>

<span data-ttu-id="b8a89-111">Vamos começar com um exemplo familiar.</span><span class="sxs-lookup"><span data-stu-id="b8a89-111">Let's start with a familiar example.</span></span> <span data-ttu-id="b8a89-112">Imagine que sua biblioteca tenha a seguinte API para recuperar uma cadeia de caracteres de recurso:</span><span class="sxs-lookup"><span data-stu-id="b8a89-112">Imagine your library has the following API to retrieve a resource string:</span></span>

```csharp
bool TryGetMessage(string key, out string message)
```

<span data-ttu-id="b8a89-113">O exemplo anterior segue o `Try*` padrão familiar no .net.</span><span class="sxs-lookup"><span data-stu-id="b8a89-113">The preceding example follows the familiar `Try*` pattern in .NET.</span></span> <span data-ttu-id="b8a89-114">Há dois argumentos de referência para essa API: o `key` e o `message` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b8a89-114">There are two reference arguments for this API: the `key` and the `message` parameter.</span></span> <span data-ttu-id="b8a89-115">Essa API tem as seguintes regras relacionadas à nulidade desses argumentos:</span><span class="sxs-lookup"><span data-stu-id="b8a89-115">This API has the following rules relating to the nullness of these arguments:</span></span>

- <span data-ttu-id="b8a89-116">Os chamadores não devem passar `null` como o argumento para `key` .</span><span class="sxs-lookup"><span data-stu-id="b8a89-116">Callers shouldn't pass `null` as the argument for `key`.</span></span>
- <span data-ttu-id="b8a89-117">Os chamadores podem passar uma variável cujo valor é `null` como o argumento para `message` .</span><span class="sxs-lookup"><span data-stu-id="b8a89-117">Callers can pass a variable whose value is `null` as the argument for `message`.</span></span>
- <span data-ttu-id="b8a89-118">Se o `TryGetMessage` método retornar `true` , o valor de `message` não será nulo.</span><span class="sxs-lookup"><span data-stu-id="b8a89-118">If the `TryGetMessage` method returns `true`, the value of `message` isn't null.</span></span> <span data-ttu-id="b8a89-119">Se o valor de retorno for `false,` o valor de `message` (e seu estado nulo) for NULL.</span><span class="sxs-lookup"><span data-stu-id="b8a89-119">If the return value is `false,` the value of `message` (and its null state) is null.</span></span>

<span data-ttu-id="b8a89-120">A regra para `key` pode ser expressa pelo tipo de variável: `key` deve ser um tipo de referência não anulável.</span><span class="sxs-lookup"><span data-stu-id="b8a89-120">The rule for `key` can be expressed by the variable type: `key` should be a non-nullable reference type.</span></span> <span data-ttu-id="b8a89-121">O `message` parâmetro é mais complexo.</span><span class="sxs-lookup"><span data-stu-id="b8a89-121">The `message` parameter is more complex.</span></span> <span data-ttu-id="b8a89-122">Ele permite `null` como o argumento, mas garante que, em caso de sucesso, esse `out` argumento não seja nulo.</span><span class="sxs-lookup"><span data-stu-id="b8a89-122">It allows `null` as the argument, but guarantees that, on success, that `out` argument isn't null.</span></span> <span data-ttu-id="b8a89-123">Para esses cenários, você precisa de um vocabulário mais rico para descrever as expectativas.</span><span class="sxs-lookup"><span data-stu-id="b8a89-123">For these scenarios, you need a richer vocabulary to describe the expectations.</span></span>

<span data-ttu-id="b8a89-124">Vários atributos foram adicionados para expressar informações adicionais sobre o estado nulo de variáveis.</span><span class="sxs-lookup"><span data-stu-id="b8a89-124">Several attributes have been added to express additional information about the null state of variables.</span></span> <span data-ttu-id="b8a89-125">Todo o código que você escreveu antes do C# 8 introduziu tipos de referência anuláveis era *nulo alheios*.</span><span class="sxs-lookup"><span data-stu-id="b8a89-125">All code you wrote before C# 8 introduced nullable reference types was *null oblivious*.</span></span> <span data-ttu-id="b8a89-126">Isso significa que qualquer variável de tipo de referência pode ser nula, mas verificações nulas não são necessárias.</span><span class="sxs-lookup"><span data-stu-id="b8a89-126">That means any reference type variable may be null, but null checks aren't required.</span></span> <span data-ttu-id="b8a89-127">Depois que o código estiver com *reconhecimento nulo*, essas regras serão alteradas.</span><span class="sxs-lookup"><span data-stu-id="b8a89-127">Once your code is *nullable aware*, those rules change.</span></span> <span data-ttu-id="b8a89-128">Os tipos de referência nunca devem ser o `null` valor, e os tipos de referência anuláveis devem ser verificados `null` antes de serem desreferenciados.</span><span class="sxs-lookup"><span data-stu-id="b8a89-128">Reference types should never be the `null` value, and nullable reference types must be checked against `null` before being dereferenced.</span></span>

<span data-ttu-id="b8a89-129">As regras para suas APIs são provavelmente mais complicadas, como vimos com o `TryGetValue` cenário de API.</span><span class="sxs-lookup"><span data-stu-id="b8a89-129">The rules for your APIs are likely more complicated, as you saw with the `TryGetValue` API scenario.</span></span> <span data-ttu-id="b8a89-130">Muitas de suas APIs têm regras mais complexas para quando as variáveis podem ou não ser `null` .</span><span class="sxs-lookup"><span data-stu-id="b8a89-130">Many of your APIs have more complex rules for when variables can or can't be `null`.</span></span> <span data-ttu-id="b8a89-131">Nesses casos, você usará um dos seguintes atributos para expressar essas regras:</span><span class="sxs-lookup"><span data-stu-id="b8a89-131">In these cases, you'll use one of the following attributes to express those rules:</span></span>

- <span data-ttu-id="b8a89-132">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): um argumento de entrada não anulável pode ser nulo.</span><span class="sxs-lookup"><span data-stu-id="b8a89-132">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): A non-nullable input argument may be null.</span></span>
- <span data-ttu-id="b8a89-133">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): um argumento de entrada anulável nunca deve ser nulo.</span><span class="sxs-lookup"><span data-stu-id="b8a89-133">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): A nullable input argument should never be null.</span></span>
- <span data-ttu-id="b8a89-134">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): um valor de retorno não anulável pode ser nulo.</span><span class="sxs-lookup"><span data-stu-id="b8a89-134">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): A non-nullable return value may be null.</span></span>
- <span data-ttu-id="b8a89-135">Não [nulo](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): um valor de retorno anulável nunca será nulo.</span><span class="sxs-lookup"><span data-stu-id="b8a89-135">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): A nullable return value will never be null.</span></span>
- <span data-ttu-id="b8a89-136">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): um argumento de entrada não anulável pode ser nulo quando o método retorna o `bool` valor especificado.</span><span class="sxs-lookup"><span data-stu-id="b8a89-136">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): A non-nullable input argument may be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="b8a89-137">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): um argumento de entrada anulável não será nulo quando o método retornar o `bool` valor especificado.</span><span class="sxs-lookup"><span data-stu-id="b8a89-137">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): A nullable input argument will not be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="b8a89-138">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): um valor de retorno não será nulo se o argumento do parâmetro especificado não for nulo.</span><span class="sxs-lookup"><span data-stu-id="b8a89-138">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): A return value isn't null if the argument for the specified parameter isn't null.</span></span>
- <span data-ttu-id="b8a89-139">[DoesNotReturn](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute): um método nunca retorna.</span><span class="sxs-lookup"><span data-stu-id="b8a89-139">[DoesNotReturn](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute): A method never returns.</span></span> <span data-ttu-id="b8a89-140">Em outras palavras, ele sempre gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="b8a89-140">In other words, it always throws an exception.</span></span>
- <span data-ttu-id="b8a89-141">[DoesNotReturnIf](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute): esse método nunca retorna se o `bool` parâmetro associado tiver o valor especificado.</span><span class="sxs-lookup"><span data-stu-id="b8a89-141">[DoesNotReturnIf](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute): This method never returns if the associated `bool` parameter has the specified value.</span></span>

<span data-ttu-id="b8a89-142">As descrições anteriores são uma referência rápida para o que cada atributo faz.</span><span class="sxs-lookup"><span data-stu-id="b8a89-142">The preceding descriptions are a quick reference to what each attribute does.</span></span> <span data-ttu-id="b8a89-143">Cada seção a seguir descreve o comportamento e significa mais detalhadamente.</span><span class="sxs-lookup"><span data-stu-id="b8a89-143">Each following section describes the behavior and meaning more thoroughly.</span></span>

<span data-ttu-id="b8a89-144">A adição desses atributos fornece ao compilador mais informações sobre as regras para sua API.</span><span class="sxs-lookup"><span data-stu-id="b8a89-144">Adding these attributes gives the compiler more information about the rules for your API.</span></span> <span data-ttu-id="b8a89-145">Quando o código de chamada é compilado em um contexto habilitado para valor nulo, o compilador avisa aos chamadores quando eles violam essas regras.</span><span class="sxs-lookup"><span data-stu-id="b8a89-145">When calling code is compiled in a nullable enabled context, the compiler will warn callers when they violate those rules.</span></span> <span data-ttu-id="b8a89-146">Esses atributos não habilitam verificações adicionais em sua implementação.</span><span class="sxs-lookup"><span data-stu-id="b8a89-146">These attributes don't enable additional checks on your implementation.</span></span>

## <a name="specify-preconditions-allownull-and-disallownull"></a><span data-ttu-id="b8a89-147">Especificar pré-condições: `AllowNull` e `DisallowNull`</span><span class="sxs-lookup"><span data-stu-id="b8a89-147">Specify preconditions: `AllowNull` and `DisallowNull`</span></span>

<span data-ttu-id="b8a89-148">Considere uma propriedade de leitura/gravação que nunca retorna `null` porque ela tem um valor padrão razoável.</span><span class="sxs-lookup"><span data-stu-id="b8a89-148">Consider a read/write property that never returns `null` because it has a reasonable default value.</span></span> <span data-ttu-id="b8a89-149">Os chamadores passam `null` para o acessador set ao configurá-lo para esse valor padrão.</span><span class="sxs-lookup"><span data-stu-id="b8a89-149">Callers pass `null` to the set accessor when setting it to that default value.</span></span> <span data-ttu-id="b8a89-150">Por exemplo, considere um sistema de mensagens que solicita um nome de tela em uma sala de chat.</span><span class="sxs-lookup"><span data-stu-id="b8a89-150">For example, consider a messaging system that asks for a screen name in a chat room.</span></span> <span data-ttu-id="b8a89-151">Se nenhum for fornecido, o sistema gerará um nome aleatório:</span><span class="sxs-lookup"><span data-stu-id="b8a89-151">If none is provided, the system generates a random name:</span></span>

```csharp
public string ScreenName
{
   get => _screenName;
   set => _screenName = value ?? GenerateRandomScreenName();
}
private string _screenName;
```

<span data-ttu-id="b8a89-152">Quando você compila o código anterior em um contexto alheios anulável, tudo está bem.</span><span class="sxs-lookup"><span data-stu-id="b8a89-152">When you compile the preceding code in a nullable oblivious context, everything is fine.</span></span> <span data-ttu-id="b8a89-153">Depois que você habilitar tipos de referência anuláveis, a `ScreenName` propriedade se tornará uma referência não anulável.</span><span class="sxs-lookup"><span data-stu-id="b8a89-153">Once you enable nullable reference types, the `ScreenName` property becomes a non-nullable reference.</span></span> <span data-ttu-id="b8a89-154">Isso está correto para o `get` acessador: ele nunca retorna `null` .</span><span class="sxs-lookup"><span data-stu-id="b8a89-154">That's correct for the `get` accessor: it never returns `null`.</span></span> <span data-ttu-id="b8a89-155">Os chamadores não precisam verificar a propriedade retornada `null` .</span><span class="sxs-lookup"><span data-stu-id="b8a89-155">Callers don't need to check the returned property for `null`.</span></span> <span data-ttu-id="b8a89-156">Mas, agora, definir a propriedade para `null` gerar um aviso.</span><span class="sxs-lookup"><span data-stu-id="b8a89-156">But now setting the property to `null` generates a warning.</span></span> <span data-ttu-id="b8a89-157">Para continuar a dar suporte a esse tipo de código, adicione o <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType> atributo à propriedade, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="b8a89-157">In order to continue to support this type of code, you add the <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType> attribute to the property, as shown in the following code:</span></span>

```csharp
[AllowNull]
public string ScreenName
{
   get => _screenName;
   set => _screenName = value ?? GenerateRandomScreenName();
}
private string _screenName = GenerateRandomScreenName();
```

<span data-ttu-id="b8a89-158">Talvez seja necessário adicionar uma `using` diretiva para <xref:System.Diagnostics.CodeAnalysis> que o use este e outros atributos discutidos neste artigo.</span><span class="sxs-lookup"><span data-stu-id="b8a89-158">You may need to add a `using` directive for <xref:System.Diagnostics.CodeAnalysis> to use this and other attributes discussed in this article.</span></span> <span data-ttu-id="b8a89-159">O atributo é aplicado à propriedade, não ao `set` acessador.</span><span class="sxs-lookup"><span data-stu-id="b8a89-159">The attribute is applied to the property, not the `set` accessor.</span></span> <span data-ttu-id="b8a89-160">O `AllowNull` atributo especifica *pré-condições*e só se aplica a entradas.</span><span class="sxs-lookup"><span data-stu-id="b8a89-160">The `AllowNull` attribute specifies *pre-conditions*, and only applies to inputs.</span></span> <span data-ttu-id="b8a89-161">O `get` acessador tem um valor de retorno, mas nenhum argumento de entrada.</span><span class="sxs-lookup"><span data-stu-id="b8a89-161">The `get` accessor has a return value, but no input arguments.</span></span> <span data-ttu-id="b8a89-162">Portanto, o `AllowNull` atributo só se aplica ao `set` acessador.</span><span class="sxs-lookup"><span data-stu-id="b8a89-162">Therefore, the `AllowNull` attribute only applies to the `set` accessor.</span></span>

<span data-ttu-id="b8a89-163">O exemplo anterior demonstra o que procurar ao adicionar o `AllowNull` atributo em um argumento:</span><span class="sxs-lookup"><span data-stu-id="b8a89-163">The preceding example demonstrates what to look for when adding the `AllowNull` attribute on an argument:</span></span>

1. <span data-ttu-id="b8a89-164">O contrato geral para essa variável é que não deveria ser `null` , portanto, você deseja um tipo de referência não anulável.</span><span class="sxs-lookup"><span data-stu-id="b8a89-164">The general contract for that variable is that it shouldn't be `null`, so you want a non-nullable reference type.</span></span>
1. <span data-ttu-id="b8a89-165">Há cenários para a variável de entrada `null` , embora eles não sejam o uso mais comum.</span><span class="sxs-lookup"><span data-stu-id="b8a89-165">There are scenarios for the input variable to be `null`, though they aren't the most common usage.</span></span>

<span data-ttu-id="b8a89-166">Geralmente, você precisará desse atributo para propriedades, ou `in` , `out` e `ref` argumentos.</span><span class="sxs-lookup"><span data-stu-id="b8a89-166">Most often you'll need this attribute for properties, or `in`, `out`, and `ref` arguments.</span></span> <span data-ttu-id="b8a89-167">O `AllowNull` atributo é a melhor opção quando uma variável normalmente é não nula, mas você precisa permitir `null` como uma pré-condição.</span><span class="sxs-lookup"><span data-stu-id="b8a89-167">The `AllowNull` attribute is the best choice when a variable is typically non-null, but you need to allow `null` as a precondition.</span></span>

<span data-ttu-id="b8a89-168">Compare com cenários para usar `DisallowNull` : Use esse atributo para especificar que uma variável de entrada de um tipo de referência anulável não deve ser `null` .</span><span class="sxs-lookup"><span data-stu-id="b8a89-168">Contrast that with scenarios for using `DisallowNull`: You use this attribute to specify that an input variable of a nullable reference type shouldn't be `null`.</span></span> <span data-ttu-id="b8a89-169">Considere uma propriedade em que `null` é o valor padrão, mas os clientes só podem defini-lo como um valor não nulo.</span><span class="sxs-lookup"><span data-stu-id="b8a89-169">Consider a property where `null` is the default value, but clients can only set it to a non-null value.</span></span> <span data-ttu-id="b8a89-170">Considere o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="b8a89-170">Consider the following code:</span></span>

```csharp
public string ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string _comment;
```

<span data-ttu-id="b8a89-171">O código anterior é a melhor maneira de expressar o design que `ReviewComment` pode ser `null` , mas não pode ser definido como `null` .</span><span class="sxs-lookup"><span data-stu-id="b8a89-171">The preceding code is the best way to express your design that the `ReviewComment` could be `null`, but can't be set to `null`.</span></span> <span data-ttu-id="b8a89-172">Depois que esse código é ciente de forma anulável, você pode expressar esse conceito mais claramente para os chamadores usando o <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="b8a89-172">Once this code is nullable aware, you can express this concept more clearly to callers using the <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType>:</span></span>

```csharp
[DisallowNull]
public string? ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string? _comment;
```

<span data-ttu-id="b8a89-173">Em um contexto anulável, o `ReviewComment` `get` acessador pode retornar o valor padrão de `null` .</span><span class="sxs-lookup"><span data-stu-id="b8a89-173">In a nullable context, the `ReviewComment` `get` accessor could return the default value of `null`.</span></span> <span data-ttu-id="b8a89-174">O compilador avisa que ele deve ser verificado antes do acesso.</span><span class="sxs-lookup"><span data-stu-id="b8a89-174">The compiler warns that it must be checked before access.</span></span> <span data-ttu-id="b8a89-175">Além disso, ele avisa aos chamadores que, embora possa ser `null` , os chamadores não devem defini-los explicitamente como `null` .</span><span class="sxs-lookup"><span data-stu-id="b8a89-175">Furthermore, it warns callers that, even though it could be `null`, callers shouldn't explicitly set it to `null`.</span></span> <span data-ttu-id="b8a89-176">O `DisallowNull` atributo também especifica uma *pré-condição*, ele não afeta o `get` acessador.</span><span class="sxs-lookup"><span data-stu-id="b8a89-176">The `DisallowNull` attribute also specifies a *pre-condition*, it does not affect the `get` accessor.</span></span> <span data-ttu-id="b8a89-177">Você usa o `DisallowNull` atributo ao observar essas características sobre:</span><span class="sxs-lookup"><span data-stu-id="b8a89-177">You use the `DisallowNull` attribute when you observe these characteristics about:</span></span>

1. <span data-ttu-id="b8a89-178">A variável pode estar `null` em cenários principais, geralmente quando a primeira instância é instanciada.</span><span class="sxs-lookup"><span data-stu-id="b8a89-178">The variable could be `null` in core scenarios, often when first instantiated.</span></span>
1. <span data-ttu-id="b8a89-179">A variável não deve ser definida explicitamente como `null` .</span><span class="sxs-lookup"><span data-stu-id="b8a89-179">The variable shouldn't be explicitly set to `null`.</span></span>

<span data-ttu-id="b8a89-180">Essas situações são comuns no código que era originalmente *nulo alheios*.</span><span class="sxs-lookup"><span data-stu-id="b8a89-180">These situations are common in code that was originally *null oblivious*.</span></span> <span data-ttu-id="b8a89-181">Pode ser que as propriedades do objeto sejam definidas em duas operações de inicialização distintas.</span><span class="sxs-lookup"><span data-stu-id="b8a89-181">It may be that object properties are set in two distinct initialization operations.</span></span> <span data-ttu-id="b8a89-182">Pode ser que algumas propriedades sejam definidas somente após a conclusão de algum trabalho assíncrono.</span><span class="sxs-lookup"><span data-stu-id="b8a89-182">It may be that some properties are set only after some asynchronous work has completed.</span></span>

<span data-ttu-id="b8a89-183">Os `AllowNull` `DisallowNull` atributos e permitem que você especifique que as pré-condições nas variáveis podem não corresponder às anotações que permitem valor nulo nessas variáveis.</span><span class="sxs-lookup"><span data-stu-id="b8a89-183">The `AllowNull` and `DisallowNull` attributes enable you to specify that preconditions on variables may not match the nullable annotations on those variables.</span></span> <span data-ttu-id="b8a89-184">Eles fornecem mais detalhes sobre as características de sua API.</span><span class="sxs-lookup"><span data-stu-id="b8a89-184">These provide more detail about the characteristics of your API.</span></span> <span data-ttu-id="b8a89-185">Essas informações adicionais ajudam os chamadores a usar sua API corretamente.</span><span class="sxs-lookup"><span data-stu-id="b8a89-185">This additional information helps callers use your API correctly.</span></span> <span data-ttu-id="b8a89-186">Lembre-se de especificar as pré-condições usando os seguintes atributos:</span><span class="sxs-lookup"><span data-stu-id="b8a89-186">Remember you specify preconditions using the following attributes:</span></span>

- <span data-ttu-id="b8a89-187">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): um argumento de entrada não anulável pode ser nulo.</span><span class="sxs-lookup"><span data-stu-id="b8a89-187">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): A non-nullable input argument may be null.</span></span>
- <span data-ttu-id="b8a89-188">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): um argumento de entrada anulável nunca deve ser nulo.</span><span class="sxs-lookup"><span data-stu-id="b8a89-188">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): A nullable input argument should never be null.</span></span>

## <a name="specify-post-conditions-maybenull-and-notnull"></a><span data-ttu-id="b8a89-189">Especificar pós-condições: `MaybeNull` e `NotNull`</span><span class="sxs-lookup"><span data-stu-id="b8a89-189">Specify post-conditions: `MaybeNull` and `NotNull`</span></span>

<span data-ttu-id="b8a89-190">Suponha que você tenha um método com a seguinte assinatura:</span><span class="sxs-lookup"><span data-stu-id="b8a89-190">Suppose you have a method with the following signature:</span></span>

```csharp
public Customer FindCustomer(string lastName, string firstName)
```

<span data-ttu-id="b8a89-191">Você provavelmente escreveu um método como este para retornar `null` quando o nome procurado não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="b8a89-191">You've likely written a method like this to return `null` when the name sought wasn't found.</span></span> <span data-ttu-id="b8a89-192">O `null` claramente indica que o registro não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="b8a89-192">The `null` clearly indicates that the record wasn't found.</span></span> <span data-ttu-id="b8a89-193">Neste exemplo, você provavelmente alteraria o tipo de retorno de `Customer` para `Customer?` .</span><span class="sxs-lookup"><span data-stu-id="b8a89-193">In this example, you'd likely change the return type from `Customer` to `Customer?`.</span></span> <span data-ttu-id="b8a89-194">Declarar o valor de retorno como um tipo de referência anulável especifica claramente a intenção dessa API.</span><span class="sxs-lookup"><span data-stu-id="b8a89-194">Declaring the return value as a nullable reference type specifies the intent of this API clearly.</span></span>

<span data-ttu-id="b8a89-195">Por motivos abordados em [definições genéricas e nulidade](../../nullable-migration-strategies.md#generic-definitions-and-nullability) que a técnica não funciona com métodos genéricos.</span><span class="sxs-lookup"><span data-stu-id="b8a89-195">For reasons covered under [Generic definitions and nullability](../../nullable-migration-strategies.md#generic-definitions-and-nullability) that technique does not work with generic methods.</span></span> <span data-ttu-id="b8a89-196">Você pode ter um método genérico que segue um padrão semelhante:</span><span class="sxs-lookup"><span data-stu-id="b8a89-196">You may have a generic method that follows a similar pattern:</span></span>

```csharp
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> predicate)
```

<span data-ttu-id="b8a89-197">Você não pode especificar que o valor de retorno é `T?` .</span><span class="sxs-lookup"><span data-stu-id="b8a89-197">You can't specify that the return value is `T?`.</span></span> <span data-ttu-id="b8a89-198">O método retorna `null` quando o item procurado não é encontrado.</span><span class="sxs-lookup"><span data-stu-id="b8a89-198">The method returns `null` when the sought item isn't found.</span></span> <span data-ttu-id="b8a89-199">Como não é possível declarar um `T?` tipo de retorno, você adiciona a `MaybeNull` anotação ao método Return:</span><span class="sxs-lookup"><span data-stu-id="b8a89-199">Since you can't declare a `T?` return type, you add the `MaybeNull` annotation to the method return:</span></span>

```csharp
[return: MaybeNull]
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> predicate)
```

<span data-ttu-id="b8a89-200">O código anterior informa aos chamadores que o contrato implica em um tipo não anulável, mas o valor de retorno *pode* ser, na verdade, nulo.</span><span class="sxs-lookup"><span data-stu-id="b8a89-200">The preceding code informs callers that the contract implies a non-nullable type, but the return value *may* actually be null.</span></span>  <span data-ttu-id="b8a89-201">Use o `MaybeNull` atributo quando sua API deve ser um tipo não anulável, normalmente um parâmetro de tipo genérico, mas pode haver instâncias em que `null` seriam retornadas.</span><span class="sxs-lookup"><span data-stu-id="b8a89-201">Use the `MaybeNull` attribute when your API should be a non-nullable type, typically a generic type parameter, but there may be instances where `null` would be returned.</span></span>

<span data-ttu-id="b8a89-202">Você também pode especificar que um valor de retorno ou `out` um `ref` argumento or não seja nulo, embora o tipo seja um tipo de referência anulável.</span><span class="sxs-lookup"><span data-stu-id="b8a89-202">You can also specify that a return value or an `out` or `ref` argument isn't null even though the type is a nullable reference type.</span></span> <span data-ttu-id="b8a89-203">Considere um método que garanta que uma matriz seja grande o suficiente para conter vários elementos.</span><span class="sxs-lookup"><span data-stu-id="b8a89-203">Consider a method that ensures an array is large enough to hold a number of elements.</span></span> <span data-ttu-id="b8a89-204">Se o argumento de entrada não tiver capacidade, a rotina alocaria uma nova matriz e copiaria todos os elementos existentes nela.</span><span class="sxs-lookup"><span data-stu-id="b8a89-204">If the input argument doesn't have capacity, the routine would allocate a new array and copy all the existing elements into it.</span></span> <span data-ttu-id="b8a89-205">Se o argumento de entrada for `null` , a rotina alocaria novo armazenamento.</span><span class="sxs-lookup"><span data-stu-id="b8a89-205">If the input argument is `null`, the routine would allocate new storage.</span></span> <span data-ttu-id="b8a89-206">Se houver capacidade suficiente, a rotina não fará nada:</span><span class="sxs-lookup"><span data-stu-id="b8a89-206">If there's sufficient capacity, the routine does nothing:</span></span>

```csharp
public void EnsureCapacity<T>(ref T[] storage, int size)
```

<span data-ttu-id="b8a89-207">Você pode chamar essa rotina da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="b8a89-207">You could call this routine as follows:</span></span>

```csharp
// messages has the default value (null) when EnsureCapacity is called:
EnsureCapacity<string>(ref messages, 10);
// messages is not null.
EnsureCapacity<string>(messages, 50);
```

<span data-ttu-id="b8a89-208">Depois de habilitar tipos de referência NULL, você deseja garantir que o código anterior seja compilado sem avisos.</span><span class="sxs-lookup"><span data-stu-id="b8a89-208">After enabling null reference types, you want to ensure that the preceding code compiles without warnings.</span></span> <span data-ttu-id="b8a89-209">Quando o método retorna, `storage` é garantido que o argumento não seja nulo.</span><span class="sxs-lookup"><span data-stu-id="b8a89-209">When the method returns, the `storage` argument is guaranteed to be not null.</span></span> <span data-ttu-id="b8a89-210">No entanto, é aceitável chamar `EnsureCapacity` com uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="b8a89-210">However, it's acceptable to call `EnsureCapacity` with a null reference.</span></span> <span data-ttu-id="b8a89-211">Você pode criar `storage` um tipo de referência anulável e adicionar a `NotNull` pós-condição à declaração de parâmetro:</span><span class="sxs-lookup"><span data-stu-id="b8a89-211">You can make `storage` a nullable reference type, and add the `NotNull` post-condition to the parameter declaration:</span></span>

```csharp
public void EnsureCapacity<T>([NotNull] ref T[]? storage, int size)
```

<span data-ttu-id="b8a89-212">O código anterior expressa o contrato existente claramente: os chamadores podem passar uma variável com o `null` valor, mas é garantido que o valor de retorno nunca seja nulo.</span><span class="sxs-lookup"><span data-stu-id="b8a89-212">The preceding code expresses the existing contract clearly: Callers can pass a variable with the `null` value, but the return value is guaranteed to never be null.</span></span> <span data-ttu-id="b8a89-213">O `NotNull` atributo é mais útil para `ref` `out` argumentos e em que `null` pode ser passado como um argumento, mas esse argumento é garantido como não nulo quando o método retorna.</span><span class="sxs-lookup"><span data-stu-id="b8a89-213">The `NotNull` attribute is most useful for `ref` and `out` arguments where `null` may be passed as an argument, but that argument is guaranteed to be not null when the method returns.</span></span>

<span data-ttu-id="b8a89-214">Você especifica condições de erro incondicionais usando os seguintes atributos:</span><span class="sxs-lookup"><span data-stu-id="b8a89-214">You specify unconditional postconditions using the following attributes:</span></span>

- <span data-ttu-id="b8a89-215">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): um valor de retorno não anulável pode ser nulo.</span><span class="sxs-lookup"><span data-stu-id="b8a89-215">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): A non-nullable return value may be null.</span></span>
- <span data-ttu-id="b8a89-216">Não [nulo](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): um valor de retorno anulável nunca será nulo.</span><span class="sxs-lookup"><span data-stu-id="b8a89-216">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): A nullable return value will never be null.</span></span>

## <a name="specify-conditional-post-conditions-notnullwhen-maybenullwhen-and-notnullifnotnull"></a><span data-ttu-id="b8a89-217">Especificar pós-condições condicionais: `NotNullWhen` , `MaybeNullWhen` e `NotNullIfNotNull`</span><span class="sxs-lookup"><span data-stu-id="b8a89-217">Specify conditional post-conditions: `NotNullWhen`, `MaybeNullWhen`, and `NotNullIfNotNull`</span></span>

<span data-ttu-id="b8a89-218">Você provavelmente está familiarizado com o `string` método <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b8a89-218">You're likely familiar with the `string` method <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>.</span></span> <span data-ttu-id="b8a89-219">Esse método retorna `true` quando o argumento é nulo ou uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="b8a89-219">This method returns `true` when the argument is null or an empty string.</span></span> <span data-ttu-id="b8a89-220">É uma forma de verificação nula: os chamadores não precisam ser nulos. Verifique o argumento se o método retornar `false` .</span><span class="sxs-lookup"><span data-stu-id="b8a89-220">It's a form of null-check: Callers don't need to null-check the argument if the method returns `false`.</span></span> <span data-ttu-id="b8a89-221">Para tornar um método como esse reconhecimento anulável, você definiria o argumento como um tipo de referência anulável e adicionaria o `NotNullWhen` atributo:</span><span class="sxs-lookup"><span data-stu-id="b8a89-221">To make a method like this nullable aware, you'd set the argument to a nullable reference type, and add the `NotNullWhen` attribute:</span></span>

```csharp
bool IsNullOrEmpty([NotNullWhen(false)] string? value);
```

<span data-ttu-id="b8a89-222">Isso informa ao compilador que qualquer código em que o valor de retorno `false` não precisa ser marcado como nulo.</span><span class="sxs-lookup"><span data-stu-id="b8a89-222">That informs the compiler that any code where the return value is `false` need not be null-checked.</span></span> <span data-ttu-id="b8a89-223">A adição do atributo informa a análise estática do compilador que `IsNullOrEmpty` executa a verificação nula necessária: quando retorna `false` , o argumento de entrada não é `null` .</span><span class="sxs-lookup"><span data-stu-id="b8a89-223">The addition of the attribute informs the compiler's static analysis that `IsNullOrEmpty` performs the necessary null check: when it returns `false`, the input argument is not `null`.</span></span>

```csharp
string? userInput = GetUserInput();
if (!string.IsNullOrEmpty(userInput))
{
   int messageLength = userInput.Length; // no null check needed.
}
// null check needed on userInput here.
```

<span data-ttu-id="b8a89-224">O <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> método será anotado conforme mostrado acima para o .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="b8a89-224">The <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> method will be annotated as shown above for .NET Core 3.0.</span></span> <span data-ttu-id="b8a89-225">Você pode ter métodos semelhantes em sua base de código que verificam o estado dos objetos em busca de valores nulos.</span><span class="sxs-lookup"><span data-stu-id="b8a89-225">You may have similar methods in your codebase that check the state of objects for null values.</span></span> <span data-ttu-id="b8a89-226">O compilador não reconhecerá os métodos de verificação NULL personalizados e você precisará adicionar as anotações por conta própria.</span><span class="sxs-lookup"><span data-stu-id="b8a89-226">The compiler won't recognize custom null check methods, and you'll need to add the annotations yourself.</span></span> <span data-ttu-id="b8a89-227">Quando você adiciona o atributo, a análise estática do compilador sabe quando a variável testada foi marcada como nula.</span><span class="sxs-lookup"><span data-stu-id="b8a89-227">When you add the attribute, the compiler's static analysis knows when the tested variable has been null checked.</span></span>

<span data-ttu-id="b8a89-228">Outro uso para esses atributos é o `Try*` padrão.</span><span class="sxs-lookup"><span data-stu-id="b8a89-228">Another use for these attributes is the `Try*` pattern.</span></span> <span data-ttu-id="b8a89-229">As condições para `ref` e as `out` variáveis são comunicadas por meio do valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="b8a89-229">The postconditions for `ref` and `out` variables are communicated through the return value.</span></span> <span data-ttu-id="b8a89-230">Considere este método mostrado anteriormente:</span><span class="sxs-lookup"><span data-stu-id="b8a89-230">Consider this method shown earlier:</span></span>

```csharp
bool TryGetMessage(string key, out string message)
```

<span data-ttu-id="b8a89-231">O método anterior segue um idioma .NET típico: o valor de retorno indica se `message` foi definido como o valor encontrado ou, se nenhuma mensagem for encontrada, ao valor padrão.</span><span class="sxs-lookup"><span data-stu-id="b8a89-231">The preceding method follows a typical .NET idiom: the return value indicates if `message` was set to the found value or, if no message is found, to the default value.</span></span> <span data-ttu-id="b8a89-232">Se o método retornar `true` , o valor de `message` não será nulo; caso contrário, o método definirá `message` como nulo.</span><span class="sxs-lookup"><span data-stu-id="b8a89-232">If the method returns `true`, the value of `message` isn't null; otherwise, the method sets `message` to null.</span></span>

<span data-ttu-id="b8a89-233">Você pode comunicar esse idioma usando o `NotNullWhen` atributo.</span><span class="sxs-lookup"><span data-stu-id="b8a89-233">You can communicate that idiom using the `NotNullWhen` attribute.</span></span> <span data-ttu-id="b8a89-234">Quando você atualiza a assinatura para tipos de referência anuláveis, faça `message` um `string?` e adicione um atributo:</span><span class="sxs-lookup"><span data-stu-id="b8a89-234">When you update the signature for nullable reference types, make `message` a `string?` and add an attribute:</span></span>

```csharp
bool TryGetMessage(string key, [NotNullWhen(true)] out string? message)
```

<span data-ttu-id="b8a89-235">No exemplo anterior, o valor de `message` é conhecido como não nulo quando `TryGetMessage` retorna `true` .</span><span class="sxs-lookup"><span data-stu-id="b8a89-235">In the preceding example, the value of `message` is known to be not null when `TryGetMessage` returns `true`.</span></span> <span data-ttu-id="b8a89-236">Você deve anotar métodos semelhantes em sua base de código da mesma maneira: os argumentos podem ser `null` , e são conhecidos como não nulos quando o método retorna `true` .</span><span class="sxs-lookup"><span data-stu-id="b8a89-236">You should annotate similar methods in your codebase in the same way: the arguments could be `null`, and are known to be not null when the method returns `true`.</span></span>

<span data-ttu-id="b8a89-237">Há um atributo final que você também pode precisar.</span><span class="sxs-lookup"><span data-stu-id="b8a89-237">There's one final attribute you may also need.</span></span> <span data-ttu-id="b8a89-238">Às vezes, o estado nulo de um valor de retorno depende do estado nulo de um ou mais argumentos de entrada.</span><span class="sxs-lookup"><span data-stu-id="b8a89-238">Sometimes the null state of a return value depends on the null state of one or more input arguments.</span></span> <span data-ttu-id="b8a89-239">Esses métodos retornarão um valor não nulo sempre que determinados argumentos de entrada não forem `null` .</span><span class="sxs-lookup"><span data-stu-id="b8a89-239">These methods will return a non-null value whenever certain input arguments aren't `null`.</span></span> <span data-ttu-id="b8a89-240">Para anotar corretamente esses métodos, use o `NotNullIfNotNull` atributo.</span><span class="sxs-lookup"><span data-stu-id="b8a89-240">To correctly annotate these methods, you use the `NotNullIfNotNull` attribute.</span></span> <span data-ttu-id="b8a89-241">Considere o seguinte método:</span><span class="sxs-lookup"><span data-stu-id="b8a89-241">Consider the following method:</span></span>

```csharp
string GetTopLevelDomainFromFullUrl(string url);
```

<span data-ttu-id="b8a89-242">Se o `url` argumento não for nulo, a saída não será `null` .</span><span class="sxs-lookup"><span data-stu-id="b8a89-242">If the `url` argument isn't null, the output isn't `null`.</span></span> <span data-ttu-id="b8a89-243">Depois que as referências anuláveis estiverem habilitadas, essa assinatura funcionará corretamente, desde que sua API nunca aceite uma entrada nula.</span><span class="sxs-lookup"><span data-stu-id="b8a89-243">Once nullable references are enabled, that signature works correctly, provided your API never accepts a null input.</span></span> <span data-ttu-id="b8a89-244">No entanto, se a entrada puder ser nula, o valor de retorno também poderá ser nulo.</span><span class="sxs-lookup"><span data-stu-id="b8a89-244">However, if the input could be null, then return value could also be null.</span></span> <span data-ttu-id="b8a89-245">Portanto, você pode alterar a assinatura para o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="b8a89-245">Therefore, you could change the signature to the following code:</span></span>

```csharp
string? GetTopLevelDomainFromFullUrl(string? url);
```

<span data-ttu-id="b8a89-246">Isso também funciona, mas geralmente forçará os chamadores a implementarem `null` verificações adicionais.</span><span class="sxs-lookup"><span data-stu-id="b8a89-246">That also works, but will often force callers to implement extra `null` checks.</span></span> <span data-ttu-id="b8a89-247">O contrato é que o valor de retorno seria `null` apenas quando o argumento de entrada `url` é `null` .</span><span class="sxs-lookup"><span data-stu-id="b8a89-247">The contract is that the return value would be `null` only when the input argument `url` is `null`.</span></span> <span data-ttu-id="b8a89-248">Para expressar esse contrato, você anotaria esse método, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="b8a89-248">To express that contract, you would annotate this method as shown in the following code:</span></span>

```csharp
[return: NotNullIfNotNull("url")]
string? GetTopLevelDomainFromFullUrl(string? url);
```

<span data-ttu-id="b8a89-249">O valor de retorno e o argumento foram anotados com o que `?` indica que pode ser `null` .</span><span class="sxs-lookup"><span data-stu-id="b8a89-249">The return value and the argument have both been annotated with the `?` indicating that either could be `null`.</span></span> <span data-ttu-id="b8a89-250">O atributo esclarece ainda mais que o valor de retorno não será nulo quando o `url` argumento não for `null` .</span><span class="sxs-lookup"><span data-stu-id="b8a89-250">The attribute further clarifies that the return value won't be null when the `url` argument isn't `null`.</span></span>

<span data-ttu-id="b8a89-251">Você especifica condições recondicionais usando estes atributos:</span><span class="sxs-lookup"><span data-stu-id="b8a89-251">You specify conditional postconditions using these attributes:</span></span>

- <span data-ttu-id="b8a89-252">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): um argumento de entrada não anulável pode ser nulo quando o método retorna o `bool` valor especificado.</span><span class="sxs-lookup"><span data-stu-id="b8a89-252">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): A non-nullable input argument may be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="b8a89-253">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): um argumento de entrada anulável não será nulo quando o método retornar o `bool` valor especificado.</span><span class="sxs-lookup"><span data-stu-id="b8a89-253">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): A nullable input argument will not be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="b8a89-254">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): um valor de retorno não será nulo se o argumento de entrada para o parâmetro especificado não for nulo.</span><span class="sxs-lookup"><span data-stu-id="b8a89-254">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): A return value isn't null if the input argument for the specified parameter isn't null.</span></span>

## <a name="verify-unreachable-code"></a><span data-ttu-id="b8a89-255">Verificar código inacessível</span><span class="sxs-lookup"><span data-stu-id="b8a89-255">Verify unreachable code</span></span>

<span data-ttu-id="b8a89-256">Alguns métodos, normalmente os auxiliares de exceção ou outros métodos de utilitário, sempre saem lançando uma exceção.</span><span class="sxs-lookup"><span data-stu-id="b8a89-256">Some methods, typically exception helpers or other utility methods, always exit by throwing an exception.</span></span> <span data-ttu-id="b8a89-257">Ou, um auxiliar pode gerar uma exceção com base no valor de um argumento booliano.</span><span class="sxs-lookup"><span data-stu-id="b8a89-257">Or, a helper may throw an exception based on the value of a Boolean argument.</span></span>

<span data-ttu-id="b8a89-258">No primeiro caso, você pode adicionar o `DoesNotReturn` atributo à declaração do método.</span><span class="sxs-lookup"><span data-stu-id="b8a89-258">In the first case, you can add the `DoesNotReturn` attribute to the method declaration.</span></span> <span data-ttu-id="b8a89-259">O compilador o ajuda de três maneiras.</span><span class="sxs-lookup"><span data-stu-id="b8a89-259">The compiler helps you in three ways.</span></span> <span data-ttu-id="b8a89-260">Primeiro, o compilador emite um aviso se houver um caminho onde o método pode sair sem lançar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="b8a89-260">First, the compiler issues a warning if there is a path where the method can exit without throwing an exception.</span></span> <span data-ttu-id="b8a89-261">Em segundo lugar, o compilador marca qualquer código depois de uma chamada para esse método como *inacessível*, até que uma `catch` cláusula apropriada seja encontrada.</span><span class="sxs-lookup"><span data-stu-id="b8a89-261">Second, the compiler marks any code after a call to that method as *unreachable*, until an appropriate `catch` clause is encountered.</span></span> <span data-ttu-id="b8a89-262">Terceiro, o código inacessível não afetará nenhum estado nulo.</span><span class="sxs-lookup"><span data-stu-id="b8a89-262">Third, the unreachable code won't affect any null states.</span></span> <span data-ttu-id="b8a89-263">Considere este método:</span><span class="sxs-lookup"><span data-stu-id="b8a89-263">Consider this method:</span></span>

```csharp
[DoesNotReturn]
private void FailFast()
{
    throw new InvalidOperationException();
}

public void SetState(object containedField)
{
    if (!isInitialized)
    {
        FailFast();
    }

    // unreachable code:
    _field = containedField;
}
```

<span data-ttu-id="b8a89-264">No segundo caso, você adiciona o `DoesNotReturnIf` atributo a um parâmetro booliano do método.</span><span class="sxs-lookup"><span data-stu-id="b8a89-264">In the second case, you add the `DoesNotReturnIf` attribute to a Boolean parameter of the method.</span></span> <span data-ttu-id="b8a89-265">Você pode modificar o exemplo anterior da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="b8a89-265">You can modify the previous example as follows:</span></span>

```csharp
private void FailFast([DoesNotReturnIf(false)] bool isValid)
{
    if (!isValid)
    {
        throw new InvalidOperationException();
    }
}

public void SetState(object containedField)
{
    FailFast(isInitialized);

    // unreachable code when "isInitialized" is false:
    _field = containedField;
}
```

## <a name="summary"></a><span data-ttu-id="b8a89-266">Resumo</span><span class="sxs-lookup"><span data-stu-id="b8a89-266">Summary</span></span>

[!INCLUDE [C# version alert](../../includes/csharp-version-alert.md)]

<span data-ttu-id="b8a89-267">A adição de tipos de referência anuláveis fornece um vocabulário inicial para descrever suas expectativas de APIs para variáveis que podem ser `null` .</span><span class="sxs-lookup"><span data-stu-id="b8a89-267">Adding nullable reference types provides an initial vocabulary to describe your APIs expectations for variables that could be `null`.</span></span> <span data-ttu-id="b8a89-268">Os atributos adicionais fornecem um vocabulário mais rico para descrever o estado nulo de variáveis como pré-condições e condições.</span><span class="sxs-lookup"><span data-stu-id="b8a89-268">The additional attributes provide a richer vocabulary to describe the null state of variables as preconditions and postconditions.</span></span> <span data-ttu-id="b8a89-269">Esses atributos descrevem mais claramente suas expectativas e fornecem uma experiência melhor para os desenvolvedores que usam suas APIs.</span><span class="sxs-lookup"><span data-stu-id="b8a89-269">These attributes more clearly describe your expectations and provide a better experience for the developers using your APIs.</span></span>

<span data-ttu-id="b8a89-270">Conforme você atualiza as bibliotecas para um contexto anulável, adicione esses atributos para orientar os usuários de suas APIs para o uso correto.</span><span class="sxs-lookup"><span data-stu-id="b8a89-270">As you update libraries for a nullable context, add these attributes to guide users of your APIs to the correct usage.</span></span> <span data-ttu-id="b8a89-271">Esses atributos ajudam você a descrever totalmente o estado nulo dos argumentos de entrada e valores de retorno:</span><span class="sxs-lookup"><span data-stu-id="b8a89-271">These attributes help you fully describe the null-state of input arguments and return values:</span></span>

- <span data-ttu-id="b8a89-272">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): um argumento de entrada não anulável pode ser nulo.</span><span class="sxs-lookup"><span data-stu-id="b8a89-272">[AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): A non-nullable input argument may be null.</span></span>
- <span data-ttu-id="b8a89-273">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): um argumento de entrada anulável nunca deve ser nulo.</span><span class="sxs-lookup"><span data-stu-id="b8a89-273">[DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): A nullable input argument should never be null.</span></span>
- <span data-ttu-id="b8a89-274">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): um valor de retorno não anulável pode ser nulo.</span><span class="sxs-lookup"><span data-stu-id="b8a89-274">[MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): A non-nullable return value may be null.</span></span>
- <span data-ttu-id="b8a89-275">Não [nulo](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): um valor de retorno anulável nunca será nulo.</span><span class="sxs-lookup"><span data-stu-id="b8a89-275">[NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): A nullable return value will never be null.</span></span>
- <span data-ttu-id="b8a89-276">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): um argumento de entrada não anulável pode ser nulo quando o método retorna o `bool` valor especificado.</span><span class="sxs-lookup"><span data-stu-id="b8a89-276">[MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): A non-nullable input argument may be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="b8a89-277">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): um argumento de entrada anulável não será nulo quando o método retornar o `bool` valor especificado.</span><span class="sxs-lookup"><span data-stu-id="b8a89-277">[NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): A nullable input argument will not be null when the method returns the specified `bool` value.</span></span>
- <span data-ttu-id="b8a89-278">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): um valor de retorno não será nulo se o argumento de entrada para o parâmetro especificado não for nulo.</span><span class="sxs-lookup"><span data-stu-id="b8a89-278">[NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): A return value isn't null if the input argument for the specified parameter isn't null.</span></span>
- <span data-ttu-id="b8a89-279">[DoesNotReturn](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute): um método nunca retorna.</span><span class="sxs-lookup"><span data-stu-id="b8a89-279">[DoesNotReturn](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute): A method never returns.</span></span> <span data-ttu-id="b8a89-280">Em outras palavras, ele sempre gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="b8a89-280">In other words, it always throws an exception.</span></span>
- <span data-ttu-id="b8a89-281">[DoesNotReturnIf](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute): esse método nunca retorna se o `bool` parâmetro associado tiver o valor especificado.</span><span class="sxs-lookup"><span data-stu-id="b8a89-281">[DoesNotReturnIf](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute): This method never returns if the associated `bool` parameter has the specified value.</span></span>
