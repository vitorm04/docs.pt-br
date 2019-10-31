---
title: Palavra-chave readonly – Referência de C#
ms.custom: seodec18
ms.date: 06/21/2018
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 8ecf399e48da12a9dee19bb217b8668c6a53d3ad
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73191864"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="6bc2c-102">readonly (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="6bc2c-102">readonly (C# Reference)</span></span>

<span data-ttu-id="6bc2c-103">A palavra-chave `readonly` é um modificador que pode ser usado em quatro contextos:</span><span class="sxs-lookup"><span data-stu-id="6bc2c-103">The `readonly` keyword is a modifier that can be used in four contexts:</span></span>

- <span data-ttu-id="6bc2c-104">Em uma [declaração de campo](#readonly-field-example), `readonly` indica que a atribuição ao campo só pode ocorrer como parte da declaração ou em um construtor na mesma classe.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-104">In a [field declaration](#readonly-field-example), `readonly` indicates that assignment to the field can only occur as part of the declaration or in a constructor in the same class.</span></span> <span data-ttu-id="6bc2c-105">Um campo readonly pode ser atribuído e reatribuído várias vezes na declaração de campo e no construtor.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-105">A readonly field can be assigned and reassigned multiple times within the field declaration and constructor.</span></span> 
  
  <span data-ttu-id="6bc2c-106">Um campo de `readonly` não pode ser atribuído depois que o construtor é encerrado.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-106">A `readonly` field can't be assigned after the constructor exits.</span></span> <span data-ttu-id="6bc2c-107">Essa regra tem implicações diferentes para tipos de valor e tipos de referência:</span><span class="sxs-lookup"><span data-stu-id="6bc2c-107">This rule has different implications for value types and reference types:</span></span>
  
  - <span data-ttu-id="6bc2c-108">Como os tipos de valor contêm diretamente seus dados, um campo que é um tipo de valor `readonly` é imutável.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-108">Because value types directly contain their data, a field that is a  `readonly` value type is immutable.</span></span> 
  - <span data-ttu-id="6bc2c-109">Como os tipos de referência contêm uma referência a seus dados, um campo que é um tipo de referência `readonly` deve sempre se referir ao mesmo objeto.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-109">Because reference types contain a reference to their data, a field that is a `readonly` reference type must always refer to the same object.</span></span> <span data-ttu-id="6bc2c-110">Esse objeto não é imutável.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-110">That object isn't immutable.</span></span> <span data-ttu-id="6bc2c-111">O modificador `readonly` impede que o campo seja substituído por uma instância diferente do tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-111">The `readonly` modifier prevents the field from being replaced by a different instance of the reference type.</span></span> <span data-ttu-id="6bc2c-112">No entanto, o modificador não impede que os dados da instância do campo sejam modificados por meio do campo somente leitura.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-112">However, the modifier doesn't prevent the instance data of the field from being modified through the read-only field.</span></span>

  > [!WARNING]
  > <span data-ttu-id="6bc2c-113">Um tipo visível externamente que contém um campo somente leitura visível externamente, que é um tipo de referência mutável, pode ser uma vulnerabilidade de segurança e pode disparar o aviso [CA2104](/visualstudio/code-quality/ca2104) : "Não declare tipos de referência mutáveis somente leitura".</span><span class="sxs-lookup"><span data-stu-id="6bc2c-113">An externally visible type that contains an externally visible read-only field that is a mutable reference type may be a security vulnerability and may trigger warning [CA2104](/visualstudio/code-quality/ca2104) : "Do not declare read only mutable reference types."</span></span>

- <span data-ttu-id="6bc2c-114">Em uma [definição `readonly struct`](#readonly-struct-example), `readonly` indica que o `struct` é imutável.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-114">In a [`readonly struct` definition](#readonly-struct-example), `readonly` indicates that the `struct` is immutable.</span></span>
- <span data-ttu-id="6bc2c-115">Em uma [definição de membro`readonly`](#readonly-member-examples), `readonly` indica que um membro de um `struct` não modifica o estado interno da estrutura.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-115">In a [`readonly` member definition](#readonly-member-examples), `readonly` indicates that a member of a `struct` doesn't mutate the struct's internal state.</span></span>
- <span data-ttu-id="6bc2c-116">Em um [retorno de método`ref readonly`](#ref-readonly-return-example), o modificador `readonly` indica que o método retorna uma referência e as gravações não são permitidas para essa referência.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-116">In a [`ref readonly` method return](#ref-readonly-return-example), the `readonly` modifier indicates that method returns a reference and writes aren't allowed to that reference.</span></span>

<span data-ttu-id="6bc2c-117">Os contextos de `readonly sturct` e `ref readonly` foram adicionados C# em 7,2.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-117">The `readonly sturct` and `ref readonly` contexts were added in C# 7.2.</span></span> <span data-ttu-id="6bc2c-118">`readonly` membros de struct foram adicionados C# em 8,0</span><span class="sxs-lookup"><span data-stu-id="6bc2c-118">`readonly` struct members were added in C# 8.0</span></span>

## <a name="readonly-field-example"></a><span data-ttu-id="6bc2c-119">Exemplo de campo readonly</span><span class="sxs-lookup"><span data-stu-id="6bc2c-119">Readonly field example</span></span>

<span data-ttu-id="6bc2c-120">Neste exemplo, o valor do campo `year` não pode ser alterado no método `ChangeYear`, embora ele tenha sido atribuído a um valor no construtor da classe:</span><span class="sxs-lookup"><span data-stu-id="6bc2c-120">In this example, the value of the field `year` can't be changed in the method `ChangeYear`, even though it's assigned a value in the class constructor:</span></span>

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

<span data-ttu-id="6bc2c-121">Você pode atribuir um valor a um campo `readonly` apenas nos seguintes contextos:</span><span class="sxs-lookup"><span data-stu-id="6bc2c-121">You can assign a value to a `readonly` field only in the following contexts:</span></span>

- <span data-ttu-id="6bc2c-122">Quando a variável é inicializada na declaração, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="6bc2c-122">When the variable is initialized in the declaration, for example:</span></span>

  ```csharp
  public readonly int y = 5;
  ```

- <span data-ttu-id="6bc2c-123">Em um construtor de instância da classe que contém a declaração de campo de instância.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-123">In an instance constructor of the class that contains the instance field declaration.</span></span>
- <span data-ttu-id="6bc2c-124">No construtor estático da classe que contém a declaração do campo estático.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-124">In the static constructor of the class that contains the static field declaration.</span></span>

<span data-ttu-id="6bc2c-125">Esses contextos de Construtor também são os únicos contextos em que é válido passar um campo de `readonly` como um parâmetro [out](out-parameter-modifier.md) ou [ref](ref.md) .</span><span class="sxs-lookup"><span data-stu-id="6bc2c-125">These constructor contexts are also the only contexts in which it's valid to pass a `readonly` field as an [out](out-parameter-modifier.md) or [ref](ref.md) parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="6bc2c-126">A palavra-chave `readonly` é diferente da palavra-chave [const](const.md).</span><span class="sxs-lookup"><span data-stu-id="6bc2c-126">The `readonly` keyword is different from the [const](const.md) keyword.</span></span> <span data-ttu-id="6bc2c-127">O campo `const` pode ser inicializado apenas na declaração do campo.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-127">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="6bc2c-128">Um campo `readonly` pode ser atribuído várias vezes na declaração do campo e em qualquer construtor.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-128">A `readonly` field can be assigned multiple times in the field declaration and in any constructor.</span></span> <span data-ttu-id="6bc2c-129">Portanto, campos `readonly` podem ter valores diferentes dependendo do construtor usado.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-129">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="6bc2c-130">Além disso, enquanto um campo `const` é uma constante em tempo de compilação, o campo `readonly` pode ser usado para constantes de tempo de execução, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="6bc2c-130">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for runtime constants as in the following example:</span></span>
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

<span data-ttu-id="6bc2c-131">No exemplo anterior, se você usar uma instrução semelhante ao seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="6bc2c-131">In the preceding example, if you use a statement like the following example:</span></span>

```csharp
p2.y = 66;        // Error
```

<span data-ttu-id="6bc2c-132">Você obterá a mensagem de erro do compilador:</span><span class="sxs-lookup"><span data-stu-id="6bc2c-132">you'll get the compiler error message:</span></span>

`A readonly field cannot be assigned to (except in a constructor or a variable initializer)`

## <a name="readonly-struct-example"></a><span data-ttu-id="6bc2c-133">Exemplo de struct readonly</span><span class="sxs-lookup"><span data-stu-id="6bc2c-133">Readonly struct example</span></span>

<span data-ttu-id="6bc2c-134">O modificador `readonly` em uma definição `struct` declara que o struct é **imutável**.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-134">The `readonly` modifier on a `struct` definition declares that the struct is **immutable**.</span></span> <span data-ttu-id="6bc2c-135">Cada campo da instância de `struct` precisa ser marcado como `readonly`, conforme é mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="6bc2c-135">Every instance field of the `struct` must be marked `readonly`, as shown in the following example:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyStruct)]

<span data-ttu-id="6bc2c-136">O exemplo anterior usa as [propriedades automáticas de readonly](../../properties.md#read-only) para declarar seu armazenamento.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-136">The preceding example uses [readonly auto properties](../../properties.md#read-only) to declare its storage.</span></span> <span data-ttu-id="6bc2c-137">Isso instrui o compilador a criar campos de suporte `readonly` para essas propriedades.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-137">That instructs the compiler to create `readonly` backing fields for those properties.</span></span> <span data-ttu-id="6bc2c-138">Você também pode declarar campos `readonly` diretamente:</span><span class="sxs-lookup"><span data-stu-id="6bc2c-138">You could also declare `readonly` fields directly:</span></span>

```csharp
public readonly struct Point
{
    public readonly double X;
    public readonly double Y;

    public Point(double x, double y) => (X, Y) = (x, y);

    public override string ToString() => $"({X}, {Y})";
}
```

<span data-ttu-id="6bc2c-139">Adicionar um campo não marcado como `readonly` gera o erro do compilador `CS8340`: "Os campos da instância de structs readonly devem ser readonly."</span><span class="sxs-lookup"><span data-stu-id="6bc2c-139">Adding a field not marked `readonly` generates compiler error `CS8340`: "Instance fields of readonly structs must be readonly."</span></span>

## <a name="readonly-member-examples"></a><span data-ttu-id="6bc2c-140">Exemplos de membros ReadOnly</span><span class="sxs-lookup"><span data-stu-id="6bc2c-140">Readonly member examples</span></span>

<span data-ttu-id="6bc2c-141">Em outras ocasiões, você pode criar uma estrutura que dá suporte a mutação.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-141">Other times, you may create a struct that supports mutation.</span></span> <span data-ttu-id="6bc2c-142">Nesses casos, vários dos membros da instância provavelmente não modificarão o estado interno da estrutura.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-142">In those cases, several of the instance members likely won't modify the internal state of the struct.</span></span> <span data-ttu-id="6bc2c-143">Você pode declarar os membros da instância com o modificador de `readonly`.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-143">You can declare those instance members with the `readonly` modifier.</span></span> <span data-ttu-id="6bc2c-144">O compilador impõe sua intenção.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-144">The compiler enforces your intent.</span></span> <span data-ttu-id="6bc2c-145">Se esse membro modifica o estado diretamente ou acessa um membro que também não é declarado com o modificador de `readonly`, o resultado é um erro de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-145">If that member modifies state directly or accesses a member that isn't also declared with the `readonly` modifier, the result is a compile-time error.</span></span> <span data-ttu-id="6bc2c-146">O modificador de `readonly` é válido em Membros `struct`, não `class` ou `interface` declarações de membro.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-146">The `readonly` modifier is valid on `struct` members, not `class` or `interface` member declarations.</span></span>

<span data-ttu-id="6bc2c-147">Você tem duas vantagens aplicando o modificador de `readonly` aos métodos `struct` aplicáveis.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-147">You gain two advantages by applying the `readonly` modifier to applicable `struct` methods.</span></span> <span data-ttu-id="6bc2c-148">O mais importante é que o compilador impõe sua intenção.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-148">Most importantly, the compiler enforces your intent.</span></span> <span data-ttu-id="6bc2c-149">O código que modifica o estado não é válido em um método `readonly`.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-149">Code that modifies state isn't valid in a `readonly` method.</span></span> <span data-ttu-id="6bc2c-150">O compilador também pode fazer uso do modificador de `readonly` para habilitar otimizações de desempenho.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-150">The compiler may also make use of the `readonly` modifier to enable performance optimizations.</span></span> <span data-ttu-id="6bc2c-151">Quando grandes `struct` tipos são passados por `in` referência, o compilador deve gerar uma cópia defensiva se o estado da estrutura puder ser modificado.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-151">When large `struct` types are passed by `in` reference, the compiler must generate a defensive copy if the state of the struct might be modified.</span></span> <span data-ttu-id="6bc2c-152">Se apenas `readonly` Membros forem acessados, o compilador poderá não criar a cópia defensiva.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-152">If only `readonly` members are accessed, the compiler may not create the defensive copy.</span></span>

<span data-ttu-id="6bc2c-153">O modificador de `readonly` é válido na maioria dos membros de um `struct`, incluindo métodos que substituem os métodos declarados em <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-153">The `readonly` modifier is valid on most members of a `struct`, including methods that override methods declared in <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6bc2c-154">Há algumas restrições:</span><span class="sxs-lookup"><span data-stu-id="6bc2c-154">There are some restrictions:</span></span>

- <span data-ttu-id="6bc2c-155">Você não pode declarar `readonly` membros estáticos.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-155">You can't declare `readonly` static members.</span></span>
- <span data-ttu-id="6bc2c-156">Você não pode declarar construtores de `readonly`.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-156">You can't declare `readonly` constructors.</span></span>

<span data-ttu-id="6bc2c-157">Você pode adicionar o modificador de `readonly` a uma propriedade ou declaração de indexador:</span><span class="sxs-lookup"><span data-stu-id="6bc2c-157">You can add the `readonly` modifier to a property or indexer declaration:</span></span>

```csharp
readonly public int Counter
{
  get { return 0; }
  set {} // not useful, but legal
}
```

<span data-ttu-id="6bc2c-158">Você também pode adicionar o modificador de `readonly` a `get` individuais ou `set` acessadores de uma propriedade ou um indexador:</span><span class="sxs-lookup"><span data-stu-id="6bc2c-158">You may also add the `readonly` modifier to individual `get` or `set` accessors of a property or indexer:</span></span>

```csharp
public int Counter
{
  readonly get { return _counter; }
  set { _counter = value; }
}
int _counter;
```

<span data-ttu-id="6bc2c-159">Você não pode adicionar o modificador `readonly` a uma propriedade e um ou mais dos acessadores da mesma propriedade.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-159">You may not add the `readonly` modifier to both a property and one or more of that same property's accessors.</span></span> <span data-ttu-id="6bc2c-160">Essa mesma restrição se aplica a indexadores.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-160">That same restriction applies to indexers.</span></span>

<span data-ttu-id="6bc2c-161">O compilador aplica implicitamente o modificador de `readonly` a propriedades implementadas automaticamente em que o código implementado pelo compilador não modifica o estado.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-161">The compiler implicitly applies the `readonly` modifier to auto-implemented properties where the compiler implemented code doesn't modify state.</span></span> <span data-ttu-id="6bc2c-162">É equivalente às seguintes declarações:</span><span class="sxs-lookup"><span data-stu-id="6bc2c-162">It's equivalent to the following declarations:</span></span>

```csharp
public readonly int Index { get; }
// Or:
public int Number { readonly get; }
public string Message { readonly get; set; }
``` 

<span data-ttu-id="6bc2c-163">Você pode adicionar o modificador de `readonly` nesses locais, mas ele não terá nenhum efeito significativo.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-163">You may add the `readonly` modifier in those locations, but it will have no meaningful effect.</span></span> <span data-ttu-id="6bc2c-164">Você não pode adicionar o modificador `readonly` a um setter de propriedade autoimplementado ou a uma propriedade autoimplementada de leitura/gravação.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-164">You may not add the `readonly` modifier to an auto-implemented property setter, or to a read/write auto-implemented property.</span></span>

## <a name="ref-readonly-return-example"></a><span data-ttu-id="6bc2c-165">Exemplo de retorno de readonly de ref</span><span class="sxs-lookup"><span data-stu-id="6bc2c-165">Ref readonly return example</span></span>

<span data-ttu-id="6bc2c-166">O modificador de `readonly` em um `ref return` indica que a referência retornada não pode ser modificada.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-166">The `readonly` modifier on a `ref return` indicates that the returned reference can't be modified.</span></span> <span data-ttu-id="6bc2c-167">O exemplo a seguir retorna uma referência para a origem.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-167">The following example returns a reference to the origin.</span></span> <span data-ttu-id="6bc2c-168">Ele usa o modificador `readonly` para indicar que os chamadores não podem modificar a origem:</span><span class="sxs-lookup"><span data-stu-id="6bc2c-168">It uses the `readonly` modifier to indicate that callers can't modify the origin:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]
<span data-ttu-id="6bc2c-169">O tipo retornado não precisa ser um `readonly struct`.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-169">The type returned doesn't need to be a `readonly struct`.</span></span> <span data-ttu-id="6bc2c-170">Qualquer tipo que possa ser retornado por `ref` pode ser retornado por `ref readonly`.</span><span class="sxs-lookup"><span data-stu-id="6bc2c-170">Any type that can be returned by `ref` can be returned by `ref readonly`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6bc2c-171">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="6bc2c-171">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

<span data-ttu-id="6bc2c-172">Você também pode ver as propostas de especificação de idioma:</span><span class="sxs-lookup"><span data-stu-id="6bc2c-172">You can also see the language specification proposals:</span></span>

- [<span data-ttu-id="6bc2c-173">struct de ref e ReadOnly ReadOnly</span><span class="sxs-lookup"><span data-stu-id="6bc2c-173">readonly ref and readonly struct</span></span>](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [<span data-ttu-id="6bc2c-174">Membros de struct ReadOnly</span><span class="sxs-lookup"><span data-stu-id="6bc2c-174">readonly struct members</span></span>](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a><span data-ttu-id="6bc2c-175">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6bc2c-175">See also</span></span>

- [<span data-ttu-id="6bc2c-176">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="6bc2c-176">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6bc2c-177">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="6bc2c-177">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6bc2c-178">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="6bc2c-178">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="6bc2c-179">Modificadores</span><span class="sxs-lookup"><span data-stu-id="6bc2c-179">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="6bc2c-180">const</span><span class="sxs-lookup"><span data-stu-id="6bc2c-180">const</span></span>](const.md)
- [<span data-ttu-id="6bc2c-181">Campos</span><span class="sxs-lookup"><span data-stu-id="6bc2c-181">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)
