---
title: 'Campos explícitos: a palavra-chave val (F#)'
description: "Saiba mais sobre F # 'val' palavra-chave, que é usada para declarar um local para armazenar um valor em um tipo de classe ou estrutura sem inicializar o tipo."
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: dc277680121976c0469b18c77bd84443cd251afb
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="explicit-fields-the-val-keyword"></a><span data-ttu-id="e0bc4-103">Campos explícitos: a palavra-chave val</span><span class="sxs-lookup"><span data-stu-id="e0bc4-103">Explicit Fields: The val Keyword</span></span>

<span data-ttu-id="e0bc4-104">O `val` palavra-chave é usada para declarar um local para armazenar um valor em um tipo de classe ou estrutura, sem inicializá-la.</span><span class="sxs-lookup"><span data-stu-id="e0bc4-104">The `val` keyword is used to declare a location to store a value in a class or structure type, without initializing it.</span></span> <span data-ttu-id="e0bc4-105">Locais de armazenamento declarados dessa maneira são chamadas *campos explícitos*.</span><span class="sxs-lookup"><span data-stu-id="e0bc4-105">Storage locations declared in this manner are called *explicit fields*.</span></span> <span data-ttu-id="e0bc4-106">Outro uso do `val` palavra-chave é em conjunto com o `member` palavra-chave para declarar uma propriedade implementada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="e0bc4-106">Another use of the `val` keyword is in conjunction with the `member` keyword to declare an auto-implemented property.</span></span> <span data-ttu-id="e0bc4-107">Para obter mais informações sobre propriedades implementadas automaticamente, consulte [propriedades](properties.md).</span><span class="sxs-lookup"><span data-stu-id="e0bc4-107">For more information on auto-implemented properties, see [Properties](properties.md).</span></span>


## <a name="syntax"></a><span data-ttu-id="e0bc4-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e0bc4-108">Syntax</span></span>

```fsharp
val [ mutable ] [ access-modifier ] field-name : type-name
```

## <a name="remarks"></a><span data-ttu-id="e0bc4-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="e0bc4-109">Remarks</span></span>
<span data-ttu-id="e0bc4-110">A maneira usual para definir campos em um tipo de classe ou estrutura é usar um `let` associação.</span><span class="sxs-lookup"><span data-stu-id="e0bc4-110">The usual way to define fields in a class or structure type is to use a `let` binding.</span></span> <span data-ttu-id="e0bc4-111">No entanto, `let` associações devem ser inicializadas como parte do construtor de classe, que não é sempre possível, necessária ou desejada.</span><span class="sxs-lookup"><span data-stu-id="e0bc4-111">However, `let` bindings must be initialized as part of the class constructor, which is not always possible, necessary, or desirable.</span></span> <span data-ttu-id="e0bc4-112">Você pode usar o `val` palavra-chave quando desejar que um campo que não foi inicializado.</span><span class="sxs-lookup"><span data-stu-id="e0bc4-112">You can use the `val` keyword when you want a field that is uninitialized.</span></span>

<span data-ttu-id="e0bc4-113">Campos explícitos podem ser estático ou não-estático.</span><span class="sxs-lookup"><span data-stu-id="e0bc4-113">Explicit fields can be static or non-static.</span></span> <span data-ttu-id="e0bc4-114">O *modificador de acesso* pode ser `public`, `private`, ou `internal`.</span><span class="sxs-lookup"><span data-stu-id="e0bc4-114">The *access-modifier* can be `public`, `private`, or `internal`.</span></span> <span data-ttu-id="e0bc4-115">Por padrão, os campos explícitos são públicos.</span><span class="sxs-lookup"><span data-stu-id="e0bc4-115">By default, explicit fields are public.</span></span> <span data-ttu-id="e0bc4-116">Isso é diferente do `let` associações em classes, que são sempre privadas.</span><span class="sxs-lookup"><span data-stu-id="e0bc4-116">This differs from `let` bindings in classes, which are always private.</span></span>

<span data-ttu-id="e0bc4-117">O [DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) atributo é necessário em campos explícitos em tipos de classe que tem um construtor primário.</span><span class="sxs-lookup"><span data-stu-id="e0bc4-117">The [DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) attribute is required on explicit fields in class types that have a primary constructor.</span></span> <span data-ttu-id="e0bc4-118">Esse atributo especifica que o campo é inicializado a zero.</span><span class="sxs-lookup"><span data-stu-id="e0bc4-118">This attribute specifies that the field is initialized to zero.</span></span> <span data-ttu-id="e0bc4-119">O tipo do campo deve oferecer suporte a inicialização de zero.</span><span class="sxs-lookup"><span data-stu-id="e0bc4-119">The type of the field must support zero-initialization.</span></span> <span data-ttu-id="e0bc4-120">Um tipo oferece suporte à inicialização zero se ele for um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="e0bc4-120">A type supports zero-initialization if it is one of the following:</span></span>

- <span data-ttu-id="e0bc4-121">Um tipo primitivo que tem um valor igual a zero.</span><span class="sxs-lookup"><span data-stu-id="e0bc4-121">A primitive type that has a zero value.</span></span>

- <span data-ttu-id="e0bc4-122">Um tipo que oferece suporte a um valor nulo, como um valor normal, como um valor anormal ou como uma representação de um valor.</span><span class="sxs-lookup"><span data-stu-id="e0bc4-122">A type that supports a null value, either as a normal value, as an abnormal value, or as a representation of a value.</span></span> <span data-ttu-id="e0bc4-123">Isso inclui classes, tuplas, registros, funções, interfaces, tipos de referência do .NET, o `unit` tipo e tipos de união discriminados.</span><span class="sxs-lookup"><span data-stu-id="e0bc4-123">This includes classes, tuples, records, functions, interfaces, .NET reference types, the `unit` type, and discriminated union types.</span></span>

- <span data-ttu-id="e0bc4-124">Um tipo de valor de .NET.</span><span class="sxs-lookup"><span data-stu-id="e0bc4-124">A .NET value type.</span></span>

- <span data-ttu-id="e0bc4-125">Uma estrutura cujos todos campos suportam a um padrão de valor zero.</span><span class="sxs-lookup"><span data-stu-id="e0bc4-125">A structure whose fields all support a default zero value.</span></span>


<span data-ttu-id="e0bc4-126">Por exemplo, um campo imutável chamado `someField` tem um campo existente no .NET compilados representação com o nome `someField@`, e você acessar o valor armazenado usando uma propriedade chamada `someField`.</span><span class="sxs-lookup"><span data-stu-id="e0bc4-126">For example, an immutable field called `someField` has a backing field in the .NET compiled representation with the name `someField@`, and you access the stored value using a property named `someField`.</span></span>

<span data-ttu-id="e0bc4-127">Para um campo mutável, a representação do .NET compilado é um campo de .NET.</span><span class="sxs-lookup"><span data-stu-id="e0bc4-127">For a mutable field, the .NET compiled representation is a .NET field.</span></span>


>[!WARNING] 
<span data-ttu-id="e0bc4-128">`Note` O namespace do .NET Framework `System.ComponentModel` contém um atributo que tem o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="e0bc4-128">`Note` The .NET Framework namespace `System.ComponentModel` contains an attribute that has the same name.</span></span> <span data-ttu-id="e0bc4-129">Para obter informações sobre esse atributo, consulte `System.ComponentModel.DefaultValueAttribute`.</span><span class="sxs-lookup"><span data-stu-id="e0bc4-129">For information about this attribute, see `System.ComponentModel.DefaultValueAttribute`.</span></span>


<span data-ttu-id="e0bc4-130">O código a seguir mostra o uso de campos explícitos e, para comparação, um `let` associação em uma classe que tem um construtor primário.</span><span class="sxs-lookup"><span data-stu-id="e0bc4-130">The following code shows the use of explicit fields and, for comparison, a `let` binding in a class that has a primary constructor.</span></span> <span data-ttu-id="e0bc4-131">Observe que o `let`-campo associado `myInt1` é privado.</span><span class="sxs-lookup"><span data-stu-id="e0bc4-131">Note that the `let`-bound field `myInt1` is private.</span></span> <span data-ttu-id="e0bc4-132">Quando o `let`-campo associado `myInt1` é referenciado por um método de membro, o identificador automático `this` não é necessária.</span><span class="sxs-lookup"><span data-stu-id="e0bc4-132">When the `let`-bound field `myInt1` is referenced from a member method, the self identifier `this` is not required.</span></span> <span data-ttu-id="e0bc4-133">Mas quando você está fazendo referência os campos explícitos `myInt2` e `myString`, o identificador de autoatendimento é necessário.</span><span class="sxs-lookup"><span data-stu-id="e0bc4-133">But when you are referencing the explicit fields `myInt2` and `myString`, the self identifier is required.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6701.fs)]

<span data-ttu-id="e0bc4-134">A saída é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="e0bc4-134">The output is as follows:</span></span>

```
11 12 abc
30 def
```

<span data-ttu-id="e0bc4-135">O código a seguir mostra o uso de campos explícitos em uma classe que não tem um construtor primário.</span><span class="sxs-lookup"><span data-stu-id="e0bc4-135">The following code shows the use of explicit fields in a class that does not have a primary constructor.</span></span> <span data-ttu-id="e0bc4-136">Nesse caso, o `DefaultValue` atributo não é necessário, mas todos os campos devem ser inicializados em construtores definidos para o tipo.</span><span class="sxs-lookup"><span data-stu-id="e0bc4-136">In this case, the `DefaultValue` attribute is not required, but all the fields must be initialized in the constructors that are defined for the type.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6702.fs)]

<span data-ttu-id="e0bc4-137">A saída é `35 22`.</span><span class="sxs-lookup"><span data-stu-id="e0bc4-137">The output is `35 22`.</span></span>

<span data-ttu-id="e0bc4-138">O código a seguir mostra o uso de campos explícitos em uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="e0bc4-138">The following code shows the use of explicit fields in a structure.</span></span> <span data-ttu-id="e0bc4-139">Como uma estrutura é um tipo de valor, ela automaticamente tem um construtor padrão que define os valores de seus campos como zero.</span><span class="sxs-lookup"><span data-stu-id="e0bc4-139">Because a structure is a value type, it automatically has a default constructor that sets the values of its fields to zero.</span></span> <span data-ttu-id="e0bc4-140">Portanto, o `DefaultValue` atributo não é necessário.</span><span class="sxs-lookup"><span data-stu-id="e0bc4-140">Therefore, the `DefaultValue` attribute is not required.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6703.fs)]

<span data-ttu-id="e0bc4-141">A saída é `11 xyz`.</span><span class="sxs-lookup"><span data-stu-id="e0bc4-141">The output is `11 xyz`.</span></span>

<span data-ttu-id="e0bc4-142">Campos explícitos não se destinam ao uso de rotina.</span><span class="sxs-lookup"><span data-stu-id="e0bc4-142">Explicit fields are not intended for routine use.</span></span> <span data-ttu-id="e0bc4-143">Em geral, quando for possível usar um `let` associação em uma classe em vez de um campo explícita.</span><span class="sxs-lookup"><span data-stu-id="e0bc4-143">In general, when possible you should use a `let` binding in a class instead of an explicit field.</span></span> <span data-ttu-id="e0bc4-144">Campos explícitos são úteis em determinados cenários de interoperabilidade, como quando você precisa definir uma estrutura que será usada em uma plataforma de invocar a chamada para uma API nativa ou em cenários de interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="e0bc4-144">Explicit fields are useful in certain interoperability scenarios, such as when you need to define a structure that will be used in a platform invoke call to a native API, or in COM interop scenarios.</span></span> <span data-ttu-id="e0bc4-145">Para obter mais informações, consulte [funções externas](../functions/external-functions.md).</span><span class="sxs-lookup"><span data-stu-id="e0bc4-145">For more information, see [External Functions](../functions/external-functions.md).</span></span> <span data-ttu-id="e0bc4-146">Outra situação em que um campo explícito pode ser necessário é quando você estiver trabalhando com um gerador de código F # que emite classes sem um construtor primário.</span><span class="sxs-lookup"><span data-stu-id="e0bc4-146">Another situation in which an explicit field might be necessary is when you are working with an F# code generator which emits classes without a primary constructor.</span></span> <span data-ttu-id="e0bc4-147">Campos explícitos também são úteis para variáveis de thread estático ou construções semelhantes.</span><span class="sxs-lookup"><span data-stu-id="e0bc4-147">Explicit fields are also useful for thread-static variables or similar constructs.</span></span> <span data-ttu-id="e0bc4-148">Para obter mais informações, consulte `System.ThreadStaticAttribute`.</span><span class="sxs-lookup"><span data-stu-id="e0bc4-148">For more information, see `System.ThreadStaticAttribute`.</span></span>

<span data-ttu-id="e0bc4-149">Quando as palavras-chave `member val` aparecem juntos em uma definição de tipo, que é uma definição de uma propriedade implementada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="e0bc4-149">When the keywords `member val` appear together in a type definition, it is a definition of an automatically implemented property.</span></span> <span data-ttu-id="e0bc4-150">Para obter mais informações, consulte [propriedades](properties.md).</span><span class="sxs-lookup"><span data-stu-id="e0bc4-150">For more information, see [Properties](properties.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="e0bc4-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e0bc4-151">See Also</span></span>
[<span data-ttu-id="e0bc4-152">Propriedades</span><span class="sxs-lookup"><span data-stu-id="e0bc4-152">Properties</span></span>](properties.md)

[<span data-ttu-id="e0bc4-153">Membros</span><span class="sxs-lookup"><span data-stu-id="e0bc4-153">Members</span></span>](index.md)

[<span data-ttu-id="e0bc4-154">`let`Associações em Classes</span><span class="sxs-lookup"><span data-stu-id="e0bc4-154">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)
