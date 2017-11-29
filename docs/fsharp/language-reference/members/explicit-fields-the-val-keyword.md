---
title: "Campos explícitos: a palavra-chave val (F#)"
description: "Saiba mais sobre F # 'val' palavra-chave, que é usada para declarar um local para armazenar um valor em um tipo de classe ou estrutura sem inicializar o tipo."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3bdbc745-436b-407f-bf54-5d11ca829cd0
ms.openlocfilehash: cee53a48f08aec89b0bdd40189ed331cadee877d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="explicit-fields-the-val-keyword"></a><span data-ttu-id="21a9b-104">Campos explícitos: a palavra-chave val</span><span class="sxs-lookup"><span data-stu-id="21a9b-104">Explicit Fields: The val Keyword</span></span>

<span data-ttu-id="21a9b-105">O `val` palavra-chave é usada para declarar um local para armazenar um valor em um tipo de classe ou estrutura, sem inicializá-la.</span><span class="sxs-lookup"><span data-stu-id="21a9b-105">The `val` keyword is used to declare a location to store a value in a class or structure type, without initializing it.</span></span> <span data-ttu-id="21a9b-106">Locais de armazenamento declarados dessa maneira são chamadas *campos explícitos*.</span><span class="sxs-lookup"><span data-stu-id="21a9b-106">Storage locations declared in this manner are called *explicit fields*.</span></span> <span data-ttu-id="21a9b-107">Outro uso do `val` palavra-chave é em conjunto com o `member` palavra-chave para declarar uma propriedade implementada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="21a9b-107">Another use of the `val` keyword is in conjunction with the `member` keyword to declare an auto-implemented property.</span></span> <span data-ttu-id="21a9b-108">Para obter mais informações sobre propriedades implementadas automaticamente, consulte [propriedades](properties.md).</span><span class="sxs-lookup"><span data-stu-id="21a9b-108">For more information on auto-implemented properties, see [Properties](properties.md).</span></span>


## <a name="syntax"></a><span data-ttu-id="21a9b-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="21a9b-109">Syntax</span></span>

```fsharp
val [ mutable ] [ access-modifier ] field-name : type-name
```

## <a name="remarks"></a><span data-ttu-id="21a9b-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="21a9b-110">Remarks</span></span>
<span data-ttu-id="21a9b-111">A maneira usual para definir campos em um tipo de classe ou estrutura é usar um `let` associação.</span><span class="sxs-lookup"><span data-stu-id="21a9b-111">The usual way to define fields in a class or structure type is to use a `let` binding.</span></span> <span data-ttu-id="21a9b-112">No entanto, `let` associações devem ser inicializadas como parte do construtor de classe, que não é sempre possível, necessária ou desejada.</span><span class="sxs-lookup"><span data-stu-id="21a9b-112">However, `let` bindings must be initialized as part of the class constructor, which is not always possible, necessary, or desirable.</span></span> <span data-ttu-id="21a9b-113">Você pode usar o `val` palavra-chave quando desejar que um campo que não foi inicializado.</span><span class="sxs-lookup"><span data-stu-id="21a9b-113">You can use the `val` keyword when you want a field that is uninitialized.</span></span>

<span data-ttu-id="21a9b-114">Campos explícitos podem ser estático ou não-estático.</span><span class="sxs-lookup"><span data-stu-id="21a9b-114">Explicit fields can be static or non-static.</span></span> <span data-ttu-id="21a9b-115">O *modificador de acesso* pode ser `public`, `private`, ou `internal`.</span><span class="sxs-lookup"><span data-stu-id="21a9b-115">The *access-modifier* can be `public`, `private`, or `internal`.</span></span> <span data-ttu-id="21a9b-116">Por padrão, os campos explícitos são públicos.</span><span class="sxs-lookup"><span data-stu-id="21a9b-116">By default, explicit fields are public.</span></span> <span data-ttu-id="21a9b-117">Isso é diferente do `let` associações em classes, que são sempre privadas.</span><span class="sxs-lookup"><span data-stu-id="21a9b-117">This differs from `let` bindings in classes, which are always private.</span></span>

<span data-ttu-id="21a9b-118">O [DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) atributo é necessário em campos explícitos em tipos de classe que tem um construtor primário.</span><span class="sxs-lookup"><span data-stu-id="21a9b-118">The [DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) attribute is required on explicit fields in class types that have a primary constructor.</span></span> <span data-ttu-id="21a9b-119">Esse atributo especifica que o campo é inicializado a zero.</span><span class="sxs-lookup"><span data-stu-id="21a9b-119">This attribute specifies that the field is initialized to zero.</span></span> <span data-ttu-id="21a9b-120">O tipo do campo deve oferecer suporte a inicialização de zero.</span><span class="sxs-lookup"><span data-stu-id="21a9b-120">The type of the field must support zero-initialization.</span></span> <span data-ttu-id="21a9b-121">Um tipo oferece suporte à inicialização zero se ele for um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="21a9b-121">A type supports zero-initialization if it is one of the following:</span></span>

- <span data-ttu-id="21a9b-122">Um tipo primitivo que tem um valor igual a zero.</span><span class="sxs-lookup"><span data-stu-id="21a9b-122">A primitive type that has a zero value.</span></span>

- <span data-ttu-id="21a9b-123">Um tipo que oferece suporte a um valor nulo, como um valor normal, como um valor anormal ou como uma representação de um valor.</span><span class="sxs-lookup"><span data-stu-id="21a9b-123">A type that supports a null value, either as a normal value, as an abnormal value, or as a representation of a value.</span></span> <span data-ttu-id="21a9b-124">Isso inclui classes, tuplas, registros, funções, interfaces, tipos de referência do .NET, o `unit` tipo e tipos de união discriminados.</span><span class="sxs-lookup"><span data-stu-id="21a9b-124">This includes classes, tuples, records, functions, interfaces, .NET reference types, the `unit` type, and discriminated union types.</span></span>

- <span data-ttu-id="21a9b-125">Um tipo de valor de .NET.</span><span class="sxs-lookup"><span data-stu-id="21a9b-125">A .NET value type.</span></span>

- <span data-ttu-id="21a9b-126">Uma estrutura cujos todos campos suportam a um padrão de valor zero.</span><span class="sxs-lookup"><span data-stu-id="21a9b-126">A structure whose fields all support a default zero value.</span></span>


<span data-ttu-id="21a9b-127">Por exemplo, um campo imutável chamado `someField` tem um campo existente no .NET compilados representação com o nome `someField@`, e você acessar o valor armazenado usando uma propriedade chamada `someField`.</span><span class="sxs-lookup"><span data-stu-id="21a9b-127">For example, an immutable field called `someField` has a backing field in the .NET compiled representation with the name `someField@`, and you access the stored value using a property named `someField`.</span></span>

<span data-ttu-id="21a9b-128">Para um campo mutável, a representação do .NET compilado é um campo de .NET.</span><span class="sxs-lookup"><span data-stu-id="21a9b-128">For a mutable field, the .NET compiled representation is a .NET field.</span></span>


>[!WARNING] 
<span data-ttu-id="21a9b-129">`Note`O namespace do .NET Framework `System.ComponentModel` contém um atributo que tem o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="21a9b-129">`Note` The .NET Framework namespace `System.ComponentModel` contains an attribute that has the same name.</span></span> <span data-ttu-id="21a9b-130">Para obter informações sobre esse atributo, consulte `System.ComponentModel.DefaultValueAttribute`.</span><span class="sxs-lookup"><span data-stu-id="21a9b-130">For information about this attribute, see `System.ComponentModel.DefaultValueAttribute`.</span></span>


<span data-ttu-id="21a9b-131">O código a seguir mostra o uso de campos explícitos e, para comparação, um `let` associação em uma classe que tem um construtor primário.</span><span class="sxs-lookup"><span data-stu-id="21a9b-131">The following code shows the use of explicit fields and, for comparison, a `let` binding in a class that has a primary constructor.</span></span> <span data-ttu-id="21a9b-132">Observe que o `let`-campo associado `myInt1` é privado.</span><span class="sxs-lookup"><span data-stu-id="21a9b-132">Note that the `let`-bound field `myInt1` is private.</span></span> <span data-ttu-id="21a9b-133">Quando o `let`-campo associado `myInt1` é referenciado por um método de membro, o identificador automático `this` não é necessária.</span><span class="sxs-lookup"><span data-stu-id="21a9b-133">When the `let`-bound field `myInt1` is referenced from a member method, the self identifier `this` is not required.</span></span> <span data-ttu-id="21a9b-134">Mas quando você está fazendo referência os campos explícitos `myInt2` e `myString`, o identificador de autoatendimento é necessário.</span><span class="sxs-lookup"><span data-stu-id="21a9b-134">But when you are referencing the explicit fields `myInt2` and `myString`, the self identifier is required.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6701.fs)]

<span data-ttu-id="21a9b-135">A saída é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="21a9b-135">The output is as follows:</span></span>

```
11 12 abc
30 def
```

<span data-ttu-id="21a9b-136">O código a seguir mostra o uso de campos explícitos em uma classe que não tem um construtor primário.</span><span class="sxs-lookup"><span data-stu-id="21a9b-136">The following code shows the use of explicit fields in a class that does not have a primary constructor.</span></span> <span data-ttu-id="21a9b-137">Nesse caso, o `DefaultValue` atributo não é necessário, mas todos os campos devem ser inicializados em construtores definidos para o tipo.</span><span class="sxs-lookup"><span data-stu-id="21a9b-137">In this case, the `DefaultValue` attribute is not required, but all the fields must be initialized in the constructors that are defined for the type.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6702.fs)]

<span data-ttu-id="21a9b-138">A saída é `35 22`.</span><span class="sxs-lookup"><span data-stu-id="21a9b-138">The output is `35 22`.</span></span>

<span data-ttu-id="21a9b-139">O código a seguir mostra o uso de campos explícitos em uma estrutura.</span><span class="sxs-lookup"><span data-stu-id="21a9b-139">The following code shows the use of explicit fields in a structure.</span></span> <span data-ttu-id="21a9b-140">Como uma estrutura é um tipo de valor, ela automaticamente tem um construtor padrão que define os valores de seus campos como zero.</span><span class="sxs-lookup"><span data-stu-id="21a9b-140">Because a structure is a value type, it automatically has a default constructor that sets the values of its fields to zero.</span></span> <span data-ttu-id="21a9b-141">Portanto, o `DefaultValue` atributo não é necessário.</span><span class="sxs-lookup"><span data-stu-id="21a9b-141">Therefore, the `DefaultValue` attribute is not required.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6703.fs)]

<span data-ttu-id="21a9b-142">A saída é `11 xyz`.</span><span class="sxs-lookup"><span data-stu-id="21a9b-142">The output is `11 xyz`.</span></span>

<span data-ttu-id="21a9b-143">Campos explícitos não se destinam ao uso de rotina.</span><span class="sxs-lookup"><span data-stu-id="21a9b-143">Explicit fields are not intended for routine use.</span></span> <span data-ttu-id="21a9b-144">Em geral, quando for possível usar um `let` associação em uma classe em vez de um campo explícita.</span><span class="sxs-lookup"><span data-stu-id="21a9b-144">In general, when possible you should use a `let` binding in a class instead of an explicit field.</span></span> <span data-ttu-id="21a9b-145">Campos explícitos são úteis em determinados cenários de interoperabilidade, como quando você precisa definir uma estrutura que será usada em uma plataforma de invocar a chamada para uma API nativa ou em cenários de interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="21a9b-145">Explicit fields are useful in certain interoperability scenarios, such as when you need to define a structure that will be used in a platform invoke call to a native API, or in COM interop scenarios.</span></span> <span data-ttu-id="21a9b-146">Para obter mais informações, consulte [funções externas](../functions/external-functions.md).</span><span class="sxs-lookup"><span data-stu-id="21a9b-146">For more information, see [External Functions](../functions/external-functions.md).</span></span> <span data-ttu-id="21a9b-147">Outra situação em que um campo explícito pode ser necessário é quando você estiver trabalhando com um gerador de código F # que emite classes sem um construtor primário.</span><span class="sxs-lookup"><span data-stu-id="21a9b-147">Another situation in which an explicit field might be necessary is when you are working with an F# code generator which emits classes without a primary constructor.</span></span> <span data-ttu-id="21a9b-148">Campos explícitos também são úteis para variáveis de thread estático ou construções semelhantes.</span><span class="sxs-lookup"><span data-stu-id="21a9b-148">Explicit fields are also useful for thread-static variables or similar constructs.</span></span> <span data-ttu-id="21a9b-149">Para obter mais informações, consulte `System.ThreadStaticAttribute`.</span><span class="sxs-lookup"><span data-stu-id="21a9b-149">For more information, see `System.ThreadStaticAttribute`.</span></span>

<span data-ttu-id="21a9b-150">Quando as palavras-chave `member val` aparecem juntos em uma definição de tipo, que é uma definição de uma propriedade implementada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="21a9b-150">When the keywords `member val` appear together in a type definition, it is a definition of an automatically implemented property.</span></span> <span data-ttu-id="21a9b-151">Para obter mais informações, consulte [propriedades](properties.md).</span><span class="sxs-lookup"><span data-stu-id="21a9b-151">For more information, see [Properties](properties.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="21a9b-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="21a9b-152">See Also</span></span>
[<span data-ttu-id="21a9b-153">Propriedades</span><span class="sxs-lookup"><span data-stu-id="21a9b-153">Properties</span></span>](properties.md)

[<span data-ttu-id="21a9b-154">Membros</span><span class="sxs-lookup"><span data-stu-id="21a9b-154">Members</span></span>](index.md)

[<span data-ttu-id="21a9b-155">`let`Associações em Classes</span><span class="sxs-lookup"><span data-stu-id="21a9b-155">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)
