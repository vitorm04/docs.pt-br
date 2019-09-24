---
title: 'Campos explícitos: A palavra-chave Val'
description: Saiba mais sobre F# a palavra-chave ' Val ', que é usada para declarar um local para armazenar um valor em um tipo de classe ou estrutura sem inicializar o tipo.
ms.date: 05/16/2016
ms.openlocfilehash: fe339e33dae27ae226022a68dd8247d1ab1994b3
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216470"
---
# <a name="explicit-fields-the-val-keyword"></a><span data-ttu-id="4a708-103">Campos explícitos: A palavra-chave Val</span><span class="sxs-lookup"><span data-stu-id="4a708-103">Explicit Fields: The val Keyword</span></span>

<span data-ttu-id="4a708-104">A `val` palavra-chave é usada para declarar um local para armazenar um valor em um tipo de classe ou estrutura, sem inicializá-lo.</span><span class="sxs-lookup"><span data-stu-id="4a708-104">The `val` keyword is used to declare a location to store a value in a class or structure type, without initializing it.</span></span> <span data-ttu-id="4a708-105">Os locais de armazenamento declarados dessa maneira são chamados de *campos explícitos*.</span><span class="sxs-lookup"><span data-stu-id="4a708-105">Storage locations declared in this manner are called *explicit fields*.</span></span> <span data-ttu-id="4a708-106">Outro uso da `val` palavra-chave é em conjunto com `member` a palavra-chave para declarar uma propriedade implementada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="4a708-106">Another use of the `val` keyword is in conjunction with the `member` keyword to declare an auto-implemented property.</span></span> <span data-ttu-id="4a708-107">Para obter mais informações sobre propriedades implementadas automaticamente, consulte [Propriedades](properties.md).</span><span class="sxs-lookup"><span data-stu-id="4a708-107">For more information on auto-implemented properties, see [Properties](properties.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="4a708-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4a708-108">Syntax</span></span>

```fsharp
val [ mutable ] [ access-modifier ] field-name : type-name
```

## <a name="remarks"></a><span data-ttu-id="4a708-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="4a708-109">Remarks</span></span>

<span data-ttu-id="4a708-110">A maneira usual de definir campos em um tipo de classe ou estrutura é usar uma `let` associação.</span><span class="sxs-lookup"><span data-stu-id="4a708-110">The usual way to define fields in a class or structure type is to use a `let` binding.</span></span> <span data-ttu-id="4a708-111">No entanto, `let` as associações devem ser inicializadas como parte do construtor da classe, o que nem sempre é possível, necessário ou desejável.</span><span class="sxs-lookup"><span data-stu-id="4a708-111">However, `let` bindings must be initialized as part of the class constructor, which is not always possible, necessary, or desirable.</span></span> <span data-ttu-id="4a708-112">Você pode usar a `val` palavra-chave quando desejar um campo que não foi inicializado.</span><span class="sxs-lookup"><span data-stu-id="4a708-112">You can use the `val` keyword when you want a field that is uninitialized.</span></span>

<span data-ttu-id="4a708-113">Os campos explícitos podem ser estáticos ou não estáticos.</span><span class="sxs-lookup"><span data-stu-id="4a708-113">Explicit fields can be static or non-static.</span></span> <span data-ttu-id="4a708-114">O *modificador de acesso* pode `public`ser `private`, ou `internal`.</span><span class="sxs-lookup"><span data-stu-id="4a708-114">The *access-modifier* can be `public`, `private`, or `internal`.</span></span> <span data-ttu-id="4a708-115">Por padrão, os campos explícitos são públicos.</span><span class="sxs-lookup"><span data-stu-id="4a708-115">By default, explicit fields are public.</span></span> <span data-ttu-id="4a708-116">Isso difere das `let` associações em classes, que são sempre particulares.</span><span class="sxs-lookup"><span data-stu-id="4a708-116">This differs from `let` bindings in classes, which are always private.</span></span>

<span data-ttu-id="4a708-117">O atributo [DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) é necessário em campos explícitos em tipos de classe que têm um construtor principal.</span><span class="sxs-lookup"><span data-stu-id="4a708-117">The [DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) attribute is required on explicit fields in class types that have a primary constructor.</span></span> <span data-ttu-id="4a708-118">Esse atributo especifica que o campo é inicializado como zero.</span><span class="sxs-lookup"><span data-stu-id="4a708-118">This attribute specifies that the field is initialized to zero.</span></span> <span data-ttu-id="4a708-119">O tipo do campo deve dar suporte à inicialização zero.</span><span class="sxs-lookup"><span data-stu-id="4a708-119">The type of the field must support zero-initialization.</span></span> <span data-ttu-id="4a708-120">Um tipo oferece suporte à inicialização zero se for um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="4a708-120">A type supports zero-initialization if it is one of the following:</span></span>

- <span data-ttu-id="4a708-121">Um tipo primitivo que tem um valor zero.</span><span class="sxs-lookup"><span data-stu-id="4a708-121">A primitive type that has a zero value.</span></span>

- <span data-ttu-id="4a708-122">Um tipo que dá suporte a um valor nulo, seja como um valor normal, como um valor anormal, ou como uma representação de um valor.</span><span class="sxs-lookup"><span data-stu-id="4a708-122">A type that supports a null value, either as a normal value, as an abnormal value, or as a representation of a value.</span></span> <span data-ttu-id="4a708-123">Isso inclui classes, tuplas, registros, funções, interfaces, tipos de referência do `unit` .net, tipo e tipos de União discriminados.</span><span class="sxs-lookup"><span data-stu-id="4a708-123">This includes classes, tuples, records, functions, interfaces, .NET reference types, the `unit` type, and discriminated union types.</span></span>

- <span data-ttu-id="4a708-124">Um tipo de valor do .NET.</span><span class="sxs-lookup"><span data-stu-id="4a708-124">A .NET value type.</span></span>

- <span data-ttu-id="4a708-125">Uma estrutura cujos campos oferecem suporte a um valor zero padrão.</span><span class="sxs-lookup"><span data-stu-id="4a708-125">A structure whose fields all support a default zero value.</span></span>

<span data-ttu-id="4a708-126">Por exemplo, um campo imutável chamado `someField` tem um campo de apoio na representação compilada do .NET com o nome `someField@`e você acessa o valor armazenado usando uma propriedade chamada. `someField`</span><span class="sxs-lookup"><span data-stu-id="4a708-126">For example, an immutable field called `someField` has a backing field in the .NET compiled representation with the name `someField@`, and you access the stored value using a property named `someField`.</span></span>

<span data-ttu-id="4a708-127">Para um campo mutável, a representação compilada do .NET é um campo .NET.</span><span class="sxs-lookup"><span data-stu-id="4a708-127">For a mutable field, the .NET compiled representation is a .NET field.</span></span>

>[!WARNING]
><span data-ttu-id="4a708-128">O namespace `System.ComponentModel` .NET Framework contém um atributo que tem o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="4a708-128">The .NET Framework namespace `System.ComponentModel` contains an attribute that has the same name.</span></span> <span data-ttu-id="4a708-129">Para obter informações sobre esse atributo, `System.ComponentModel.DefaultValueAttribute`consulte.</span><span class="sxs-lookup"><span data-stu-id="4a708-129">For information about this attribute, see `System.ComponentModel.DefaultValueAttribute`.</span></span>

<span data-ttu-id="4a708-130">O código a seguir mostra o uso de campos explícitos e, para comparação `let` , uma associação em uma classe que tem um construtor principal.</span><span class="sxs-lookup"><span data-stu-id="4a708-130">The following code shows the use of explicit fields and, for comparison, a `let` binding in a class that has a primary constructor.</span></span> <span data-ttu-id="4a708-131">Observe que o `let`campo `myInt1` -Bound é privado.</span><span class="sxs-lookup"><span data-stu-id="4a708-131">Note that the `let`-bound field `myInt1` is private.</span></span> <span data-ttu-id="4a708-132">Quando o `let`campo `myInt1` -Bound é referenciado de um método de membro, o `this` autoidentifier não é necessário.</span><span class="sxs-lookup"><span data-stu-id="4a708-132">When the `let`-bound field `myInt1` is referenced from a member method, the self identifier `this` is not required.</span></span> <span data-ttu-id="4a708-133">Mas quando você está fazendo referência a campos `myInt2` explícitos e `myString`, o autoidentifier é necessário.</span><span class="sxs-lookup"><span data-stu-id="4a708-133">But when you are referencing the explicit fields `myInt2` and `myString`, the self identifier is required.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6701.fs)]

<span data-ttu-id="4a708-134">A saída é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="4a708-134">The output is as follows:</span></span>

```console
11 12 abc
30 def
```

<span data-ttu-id="4a708-135">O código a seguir mostra o uso de campos explícitos em uma classe que não tem um construtor principal.</span><span class="sxs-lookup"><span data-stu-id="4a708-135">The following code shows the use of explicit fields in a class that does not have a primary constructor.</span></span> <span data-ttu-id="4a708-136">Nesse caso, o `DefaultValue` atributo não é necessário, mas todos os campos devem ser inicializados nos construtores que são definidos para o tipo.</span><span class="sxs-lookup"><span data-stu-id="4a708-136">In this case, the `DefaultValue` attribute is not required, but all the fields must be initialized in the constructors that are defined for the type.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6702.fs)]

<span data-ttu-id="4a708-137">A saída é `35 22`.</span><span class="sxs-lookup"><span data-stu-id="4a708-137">The output is `35 22`.</span></span>

<span data-ttu-id="4a708-138">O código a seguir mostra o uso de campos explícitos em uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="4a708-138">The following code shows the use of explicit fields in a structure.</span></span> <span data-ttu-id="4a708-139">Como uma estrutura é um tipo de valor, ela automaticamente tem um construtor padrão que define os valores de seus campos como zero.</span><span class="sxs-lookup"><span data-stu-id="4a708-139">Because a structure is a value type, it automatically has a default constructor that sets the values of its fields to zero.</span></span> <span data-ttu-id="4a708-140">Portanto, o `DefaultValue` atributo não é necessário.</span><span class="sxs-lookup"><span data-stu-id="4a708-140">Therefore, the `DefaultValue` attribute is not required.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6703.fs)]

<span data-ttu-id="4a708-141">A saída é `11 xyz`.</span><span class="sxs-lookup"><span data-stu-id="4a708-141">The output is `11 xyz`.</span></span>

<span data-ttu-id="4a708-142">**Cuidado**. se você for inicializar sua estrutura com `mutable` campos sem `mutable` palavra-chave, suas atribuições funcionarão em uma cópia da estrutura que será descartada logo após a atribuição.</span><span class="sxs-lookup"><span data-stu-id="4a708-142">**Beware**, if you are going to initialize your structure with `mutable` fields without `mutable` keyword, your assignments will work on a copy of the structure which will be discarded right after assignment.</span></span> <span data-ttu-id="4a708-143">Portanto, sua estrutura não será alterada.</span><span class="sxs-lookup"><span data-stu-id="4a708-143">Therefore your structure won't change.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6704.fs)]

<span data-ttu-id="4a708-144">Os campos explícitos não são destinados ao uso de rotina.</span><span class="sxs-lookup"><span data-stu-id="4a708-144">Explicit fields are not intended for routine use.</span></span> <span data-ttu-id="4a708-145">Em geral, quando possível, você deve usar `let` uma associação em uma classe em vez de um campo explícito.</span><span class="sxs-lookup"><span data-stu-id="4a708-145">In general, when possible you should use a `let` binding in a class instead of an explicit field.</span></span> <span data-ttu-id="4a708-146">Os campos explícitos são úteis em determinados cenários de interoperabilidade, como quando você precisa definir uma estrutura que será usada em uma chamada de plataforma Invoke para uma API nativa ou em cenários de interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="4a708-146">Explicit fields are useful in certain interoperability scenarios, such as when you need to define a structure that will be used in a platform invoke call to a native API, or in COM interop scenarios.</span></span> <span data-ttu-id="4a708-147">Para obter mais informações, consulte [external Functions](../functions/external-functions.md).</span><span class="sxs-lookup"><span data-stu-id="4a708-147">For more information, see [External Functions](../functions/external-functions.md).</span></span> <span data-ttu-id="4a708-148">Outra situação em que um campo explícito pode ser necessário é quando você está trabalhando com um F# gerador de código que emite classes sem um construtor principal.</span><span class="sxs-lookup"><span data-stu-id="4a708-148">Another situation in which an explicit field might be necessary is when you are working with an F# code generator which emits classes without a primary constructor.</span></span> <span data-ttu-id="4a708-149">Os campos explícitos também são úteis para variáveis de thread estático ou construções semelhantes.</span><span class="sxs-lookup"><span data-stu-id="4a708-149">Explicit fields are also useful for thread-static variables or similar constructs.</span></span> <span data-ttu-id="4a708-150">Para obter mais informações, consulte `System.ThreadStaticAttribute`.</span><span class="sxs-lookup"><span data-stu-id="4a708-150">For more information, see `System.ThreadStaticAttribute`.</span></span>

<span data-ttu-id="4a708-151">Quando as palavras-chave `member val` aparecem juntas em uma definição de tipo, é uma definição de uma propriedade implementada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="4a708-151">When the keywords `member val` appear together in a type definition, it is a definition of an automatically implemented property.</span></span> <span data-ttu-id="4a708-152">Para obter mais informações, consulte [Propriedades](properties.md).</span><span class="sxs-lookup"><span data-stu-id="4a708-152">For more information, see [Properties](properties.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4a708-153">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4a708-153">See also</span></span>

- [<span data-ttu-id="4a708-154">Propriedades</span><span class="sxs-lookup"><span data-stu-id="4a708-154">Properties</span></span>](properties.md)
- [<span data-ttu-id="4a708-155">Membros</span><span class="sxs-lookup"><span data-stu-id="4a708-155">Members</span></span>](index.md)
- [<span data-ttu-id="4a708-156">`let`Associações em Classes</span><span class="sxs-lookup"><span data-stu-id="4a708-156">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)
