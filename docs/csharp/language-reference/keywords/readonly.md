---
title: Palavra-chave readonly – Referência de C#
ms.date: 06/21/2018
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 165b6287e1610e013b289601e1535a08fdd3b5c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399353"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="d5f39-102">readonly (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="d5f39-102">readonly (C# Reference)</span></span>

<span data-ttu-id="d5f39-103">A `readonly` palavra-chave é um modificador que pode ser usado em quatro contextos:</span><span class="sxs-lookup"><span data-stu-id="d5f39-103">The `readonly` keyword is a modifier that can be used in four contexts:</span></span>

- <span data-ttu-id="d5f39-104">Em uma [declaração de campo,](#readonly-field-example) `readonly` indica que a atribuição ao campo só pode ocorrer como parte da declaração ou em um construtor da mesma classe.</span><span class="sxs-lookup"><span data-stu-id="d5f39-104">In a [field declaration](#readonly-field-example), `readonly` indicates that assignment to the field can only occur as part of the declaration or in a constructor in the same class.</span></span> <span data-ttu-id="d5f39-105">Um campo readonly pode ser atribuído e reatribuído várias vezes na declaração de campo e no construtor.</span><span class="sxs-lookup"><span data-stu-id="d5f39-105">A readonly field can be assigned and reassigned multiple times within the field declaration and constructor.</span></span>
  
  <span data-ttu-id="d5f39-106">Um `readonly` campo não pode ser atribuído depois que o construtor sair.</span><span class="sxs-lookup"><span data-stu-id="d5f39-106">A `readonly` field can't be assigned after the constructor exits.</span></span> <span data-ttu-id="d5f39-107">Esta regra tem diferentes implicações para tipos de valor e tipos de referência:</span><span class="sxs-lookup"><span data-stu-id="d5f39-107">This rule has different implications for value types and reference types:</span></span>
  
  - <span data-ttu-id="d5f39-108">Como os tipos de valor contêm diretamente seus dados, um campo que é um tipo de valor `readonly` é imutável.</span><span class="sxs-lookup"><span data-stu-id="d5f39-108">Because value types directly contain their data, a field that is a  `readonly` value type is immutable.</span></span>
  - <span data-ttu-id="d5f39-109">Como os tipos de referência contêm uma referência a seus dados, um campo que é um tipo de referência `readonly` deve sempre se referir ao mesmo objeto.</span><span class="sxs-lookup"><span data-stu-id="d5f39-109">Because reference types contain a reference to their data, a field that is a `readonly` reference type must always refer to the same object.</span></span> <span data-ttu-id="d5f39-110">Esse objeto não é imutável.</span><span class="sxs-lookup"><span data-stu-id="d5f39-110">That object isn't immutable.</span></span> <span data-ttu-id="d5f39-111">O modificador `readonly` impede que o campo seja substituído por uma instância diferente do tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="d5f39-111">The `readonly` modifier prevents the field from being replaced by a different instance of the reference type.</span></span> <span data-ttu-id="d5f39-112">No entanto, o modificador não impede que os dados de ocorrência do campo sejam modificados através do campo somente leitura.</span><span class="sxs-lookup"><span data-stu-id="d5f39-112">However, the modifier doesn't prevent the instance data of the field from being modified through the read-only field.</span></span>

  > [!WARNING]
  > <span data-ttu-id="d5f39-113">Um tipo externamente visível que contém um campo somente leitura externamente visível que seja um tipo de referência mutável pode ser uma vulnerabilidade de segurança e pode acionar o aviso [CA2104](/visualstudio/code-quality/ca2104) : "Não declare somente tipos de referência mutáveis".</span><span class="sxs-lookup"><span data-stu-id="d5f39-113">An externally visible type that contains an externally visible read-only field that is a mutable reference type may be a security vulnerability and may trigger warning [CA2104](/visualstudio/code-quality/ca2104) : "Do not declare read only mutable reference types."</span></span>

- <span data-ttu-id="d5f39-114">Em uma `readonly` `struct` [ `readonly struct` definição,](#readonly-struct-example)indica que o é imutável.</span><span class="sxs-lookup"><span data-stu-id="d5f39-114">In a [`readonly struct` definition](#readonly-struct-example), `readonly` indicates that the `struct` is immutable.</span></span>
- <span data-ttu-id="d5f39-115">Em uma `readonly` `struct` [ `readonly` definição de membro,](#readonly-member-examples)indica que um membro de um não muta o estado interno da estrutura.</span><span class="sxs-lookup"><span data-stu-id="d5f39-115">In a [`readonly` member definition](#readonly-member-examples), `readonly` indicates that a member of a `struct` doesn't mutate the struct's internal state.</span></span>
- <span data-ttu-id="d5f39-116">Em um [ `ref readonly` retorno do método,](#ref-readonly-return-example)o modificador indica que o `readonly` método retorna uma referência e as gravações não são permitidas a essa referência.</span><span class="sxs-lookup"><span data-stu-id="d5f39-116">In a [`ref readonly` method return](#ref-readonly-return-example), the `readonly` modifier indicates that method returns a reference and writes aren't allowed to that reference.</span></span>

<span data-ttu-id="d5f39-117">Os `readonly struct` `ref readonly` contextos foram adicionados em C# 7.2.</span><span class="sxs-lookup"><span data-stu-id="d5f39-117">The `readonly struct` and `ref readonly` contexts were added in C# 7.2.</span></span> <span data-ttu-id="d5f39-118">`readonly`membros de estrutura foram adicionados em C # 8.0</span><span class="sxs-lookup"><span data-stu-id="d5f39-118">`readonly` struct members were added in C# 8.0</span></span>

## <a name="readonly-field-example"></a><span data-ttu-id="d5f39-119">Exemplo de campo readonly</span><span class="sxs-lookup"><span data-stu-id="d5f39-119">Readonly field example</span></span>

<span data-ttu-id="d5f39-120">Neste exemplo, o valor `year` do campo não pode `ChangeYear`ser alterado no método, mesmo que seja atribuído um valor no construtor de classe:</span><span class="sxs-lookup"><span data-stu-id="d5f39-120">In this example, the value of the field `year` can't be changed in the method `ChangeYear`, even though it's assigned a value in the class constructor:</span></span>

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

<span data-ttu-id="d5f39-121">Você pode atribuir um valor a um campo `readonly` apenas nos seguintes contextos:</span><span class="sxs-lookup"><span data-stu-id="d5f39-121">You can assign a value to a `readonly` field only in the following contexts:</span></span>

- <span data-ttu-id="d5f39-122">Quando a variável é inicializada na declaração, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="d5f39-122">When the variable is initialized in the declaration, for example:</span></span>

  ```csharp
  public readonly int y = 5;
  ```

- <span data-ttu-id="d5f39-123">Em um construtor de instância da classe que contém a declaração de campo de instância.</span><span class="sxs-lookup"><span data-stu-id="d5f39-123">In an instance constructor of the class that contains the instance field declaration.</span></span>
- <span data-ttu-id="d5f39-124">No construtor estático da classe que contém a declaração do campo estático.</span><span class="sxs-lookup"><span data-stu-id="d5f39-124">In the static constructor of the class that contains the static field declaration.</span></span>

<span data-ttu-id="d5f39-125">Esses contextos construtores também são os únicos contextos em `readonly` que é válido passar um campo como um parâmetro [de saída](out-parameter-modifier.md) ou [ref.](ref.md)</span><span class="sxs-lookup"><span data-stu-id="d5f39-125">These constructor contexts are also the only contexts in which it's valid to pass a `readonly` field as an [out](out-parameter-modifier.md) or [ref](ref.md) parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="d5f39-126">A palavra-chave `readonly` é diferente da palavra-chave [const](const.md).</span><span class="sxs-lookup"><span data-stu-id="d5f39-126">The `readonly` keyword is different from the [const](const.md) keyword.</span></span> <span data-ttu-id="d5f39-127">O campo `const` pode ser inicializado apenas na declaração do campo.</span><span class="sxs-lookup"><span data-stu-id="d5f39-127">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="d5f39-128">Um campo `readonly` pode ser atribuído várias vezes na declaração do campo e em qualquer construtor.</span><span class="sxs-lookup"><span data-stu-id="d5f39-128">A `readonly` field can be assigned multiple times in the field declaration and in any constructor.</span></span> <span data-ttu-id="d5f39-129">Portanto, campos `readonly` podem ter valores diferentes dependendo do construtor usado.</span><span class="sxs-lookup"><span data-stu-id="d5f39-129">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="d5f39-130">Além disso, `const` enquanto um campo é `readonly` uma constante de tempo de compilação, o campo pode ser usado para constantes de tempo de execução como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="d5f39-130">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants as in the following example:</span></span>
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

<span data-ttu-id="d5f39-131">No exemplo anterior, se você usar uma instrução semelhante ao seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="d5f39-131">In the preceding example, if you use a statement like the following example:</span></span>

```csharp
p2.y = 66;        // Error
```

<span data-ttu-id="d5f39-132">você receberá a mensagem de erro do compilador:</span><span class="sxs-lookup"><span data-stu-id="d5f39-132">you'll get the compiler error message:</span></span>

<span data-ttu-id="d5f39-133">**Um campo somente leitura não pode ser atribuído (exceto em um construtor ou em um inicializador de variáveis)**</span><span class="sxs-lookup"><span data-stu-id="d5f39-133">**A readonly field cannot be assigned to (except in a constructor or a variable initializer)**</span></span>

## <a name="readonly-struct-example"></a><span data-ttu-id="d5f39-134">Exemplo de struct readonly</span><span class="sxs-lookup"><span data-stu-id="d5f39-134">Readonly struct example</span></span>

<span data-ttu-id="d5f39-135">O modificador `readonly` em uma definição `struct` declara que o struct é **imutável**.</span><span class="sxs-lookup"><span data-stu-id="d5f39-135">The `readonly` modifier on a `struct` definition declares that the struct is **immutable**.</span></span> <span data-ttu-id="d5f39-136">Cada campo da instância de `struct` precisa ser marcado como `readonly`, conforme é mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="d5f39-136">Every instance field of the `struct` must be marked `readonly`, as shown in the following example:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyStruct)]

<span data-ttu-id="d5f39-137">O exemplo anterior usa as [propriedades automáticas de readonly](../../properties.md#read-only) para declarar seu armazenamento.</span><span class="sxs-lookup"><span data-stu-id="d5f39-137">The preceding example uses [readonly auto properties](../../properties.md#read-only) to declare its storage.</span></span> <span data-ttu-id="d5f39-138">Isso instrui o compilador a criar campos de suporte `readonly` para essas propriedades.</span><span class="sxs-lookup"><span data-stu-id="d5f39-138">That instructs the compiler to create `readonly` backing fields for those properties.</span></span> <span data-ttu-id="d5f39-139">Você também pode declarar campos `readonly` diretamente:</span><span class="sxs-lookup"><span data-stu-id="d5f39-139">You could also declare `readonly` fields directly:</span></span>

```csharp
public readonly struct Point
{
    public readonly double X;
    public readonly double Y;

    public Point(double x, double y) => (X, Y) = (x, y);

    public override string ToString() => $"({X}, {Y})";
}
```

<span data-ttu-id="d5f39-140">Adicionar um campo não marcado como `readonly` gera o erro do compilador `CS8340`: "Os campos da instância de structs readonly devem ser readonly."</span><span class="sxs-lookup"><span data-stu-id="d5f39-140">Adding a field not marked `readonly` generates compiler error `CS8340`: "Instance fields of readonly structs must be readonly."</span></span>

## <a name="readonly-member-examples"></a><span data-ttu-id="d5f39-141">Leia apenas exemplos de membros</span><span class="sxs-lookup"><span data-stu-id="d5f39-141">Readonly member examples</span></span>

<span data-ttu-id="d5f39-142">Outras vezes, você pode criar uma estrutura que suporta mutação.</span><span class="sxs-lookup"><span data-stu-id="d5f39-142">Other times, you may create a struct that supports mutation.</span></span> <span data-ttu-id="d5f39-143">Nesses casos, vários dos membros da instância provavelmente não modificarão o estado interno da estrutura.</span><span class="sxs-lookup"><span data-stu-id="d5f39-143">In those cases, several of the instance members likely won't modify the internal state of the struct.</span></span> <span data-ttu-id="d5f39-144">Você pode declarar esses `readonly` membros de instância com o modificador.</span><span class="sxs-lookup"><span data-stu-id="d5f39-144">You can declare those instance members with the `readonly` modifier.</span></span> <span data-ttu-id="d5f39-145">O compilador reforça sua intenção.</span><span class="sxs-lookup"><span data-stu-id="d5f39-145">The compiler enforces your intent.</span></span> <span data-ttu-id="d5f39-146">Se esse membro modificar o estado diretamente ou acessar um membro `readonly` que também não é declarado com o modificador, o resultado será um erro de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="d5f39-146">If that member modifies state directly or accesses a member that isn't also declared with the `readonly` modifier, the result is a compile-time error.</span></span> <span data-ttu-id="d5f39-147">O `readonly` modificador é `struct` válido `class` em `interface` declarações de membros, não de membros.</span><span class="sxs-lookup"><span data-stu-id="d5f39-147">The `readonly` modifier is valid on `struct` members, not `class` or `interface` member declarations.</span></span>

<span data-ttu-id="d5f39-148">Você ganha duas vantagens `readonly` aplicando o `struct` modificador aos métodos aplicáveis.</span><span class="sxs-lookup"><span data-stu-id="d5f39-148">You gain two advantages by applying the `readonly` modifier to applicable `struct` methods.</span></span> <span data-ttu-id="d5f39-149">Mais importante, o compilador reforça sua intenção.</span><span class="sxs-lookup"><span data-stu-id="d5f39-149">Most importantly, the compiler enforces your intent.</span></span> <span data-ttu-id="d5f39-150">Código que modifica estado não é `readonly` válido em um método.</span><span class="sxs-lookup"><span data-stu-id="d5f39-150">Code that modifies state isn't valid in a `readonly` method.</span></span> <span data-ttu-id="d5f39-151">O compilador também pode fazer `readonly` uso do modificador para permitir otimizações de desempenho.</span><span class="sxs-lookup"><span data-stu-id="d5f39-151">The compiler may also make use of the `readonly` modifier to enable performance optimizations.</span></span> <span data-ttu-id="d5f39-152">Quando `struct` grandes tipos `in` são passados por referência, o compilador deve gerar uma cópia defensiva se o estado da estrutura pode ser modificado.</span><span class="sxs-lookup"><span data-stu-id="d5f39-152">When large `struct` types are passed by `in` reference, the compiler must generate a defensive copy if the state of the struct might be modified.</span></span> <span data-ttu-id="d5f39-153">Se `readonly` apenas membros forem acessados, o compilador não poderá criar a cópia defensiva.</span><span class="sxs-lookup"><span data-stu-id="d5f39-153">If only `readonly` members are accessed, the compiler may not create the defensive copy.</span></span>

<span data-ttu-id="d5f39-154">O `readonly` modificador é válido na `struct`maioria dos membros de a, <xref:System.Object?displayProperty=nameWithType>incluindo métodos que sobrepõem métodos declarados em .</span><span class="sxs-lookup"><span data-stu-id="d5f39-154">The `readonly` modifier is valid on most members of a `struct`, including methods that override methods declared in <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d5f39-155">Existem algumas restrições:</span><span class="sxs-lookup"><span data-stu-id="d5f39-155">There are some restrictions:</span></span>

- <span data-ttu-id="d5f39-156">Você não pode `readonly` declarar métodos ou propriedades estáticas.</span><span class="sxs-lookup"><span data-stu-id="d5f39-156">You can't declare `readonly` static methods or properties.</span></span>
- <span data-ttu-id="d5f39-157">Você não pode `readonly` declarar construtores.</span><span class="sxs-lookup"><span data-stu-id="d5f39-157">You can't declare `readonly` constructors.</span></span>

<span data-ttu-id="d5f39-158">Você pode `readonly` adicionar o modificador a uma declaração de propriedade ou indexador:</span><span class="sxs-lookup"><span data-stu-id="d5f39-158">You can add the `readonly` modifier to a property or indexer declaration:</span></span>

```csharp
readonly public int Counter
{
  get { return 0; }
  set {} // not useful, but legal
}
```

<span data-ttu-id="d5f39-159">Você também pode `readonly` adicionar o `get` `set` modificador a um indivíduo ou acessórios de uma propriedade ou indexador:</span><span class="sxs-lookup"><span data-stu-id="d5f39-159">You may also add the `readonly` modifier to individual `get` or `set` accessors of a property or indexer:</span></span>

```csharp
public int Counter
{
  readonly get { return _counter; }
  set { _counter = value; }
}
int _counter;
```

<span data-ttu-id="d5f39-160">Você não pode `readonly` adicionar o modificador a uma propriedade e a um ou mais dos acessórios dessa mesma propriedade.</span><span class="sxs-lookup"><span data-stu-id="d5f39-160">You may not add the `readonly` modifier to both a property and one or more of that same property's accessors.</span></span> <span data-ttu-id="d5f39-161">Essa mesma restrição se aplica aos indexadores.</span><span class="sxs-lookup"><span data-stu-id="d5f39-161">That same restriction applies to indexers.</span></span>

<span data-ttu-id="d5f39-162">O compilador aplica implicitamente o `readonly` modificador a propriedades implementadas automaticamente onde o código implementado pelo compilador não modifica o estado.</span><span class="sxs-lookup"><span data-stu-id="d5f39-162">The compiler implicitly applies the `readonly` modifier to auto-implemented properties where the compiler implemented code doesn't modify state.</span></span> <span data-ttu-id="d5f39-163">Equivale às seguintes declarações:</span><span class="sxs-lookup"><span data-stu-id="d5f39-163">It's equivalent to the following declarations:</span></span>

```csharp
public readonly int Index { get; }
// Or:
public int Number { readonly get; }
public string Message { readonly get; set; }
```

<span data-ttu-id="d5f39-164">Você pode `readonly` adicionar o modificador nesses locais, mas não terá nenhum efeito significativo.</span><span class="sxs-lookup"><span data-stu-id="d5f39-164">You may add the `readonly` modifier in those locations, but it will have no meaningful effect.</span></span> <span data-ttu-id="d5f39-165">Você não pode `readonly` adicionar o modificador a um definidor de propriedade implementado automaticamente ou a uma propriedade de leitura/gravação implementada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="d5f39-165">You may not add the `readonly` modifier to an auto-implemented property setter, or to a read/write auto-implemented property.</span></span>

## <a name="ref-readonly-return-example"></a><span data-ttu-id="d5f39-166">Exemplo de retorno de readonly de ref</span><span class="sxs-lookup"><span data-stu-id="d5f39-166">Ref readonly return example</span></span>

<span data-ttu-id="d5f39-167">O `readonly` modificador `ref return` em um indica que a referência retornada não pode ser modificada.</span><span class="sxs-lookup"><span data-stu-id="d5f39-167">The `readonly` modifier on a `ref return` indicates that the returned reference can't be modified.</span></span> <span data-ttu-id="d5f39-168">O exemplo a seguir retorna uma referência para a origem.</span><span class="sxs-lookup"><span data-stu-id="d5f39-168">The following example returns a reference to the origin.</span></span> <span data-ttu-id="d5f39-169">Ele usa `readonly` o modificador para indicar que os chamadores não podem modificar a origem:</span><span class="sxs-lookup"><span data-stu-id="d5f39-169">It uses the `readonly` modifier to indicate that callers can't modify the origin:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]
<span data-ttu-id="d5f39-170">O tipo retornado não precisa ser um `readonly struct`.</span><span class="sxs-lookup"><span data-stu-id="d5f39-170">The type returned doesn't need to be a `readonly struct`.</span></span> <span data-ttu-id="d5f39-171">Qualquer tipo que possa ser retornado por `ref` pode ser retornado por `ref readonly`.</span><span class="sxs-lookup"><span data-stu-id="d5f39-171">Any type that can be returned by `ref` can be returned by `ref readonly`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d5f39-172">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="d5f39-172">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

<span data-ttu-id="d5f39-173">Você também pode ver as propostas de especificação do idioma:</span><span class="sxs-lookup"><span data-stu-id="d5f39-173">You can also see the language specification proposals:</span></span>

- [<span data-ttu-id="d5f39-174">readonly ref e readonly struct</span><span class="sxs-lookup"><span data-stu-id="d5f39-174">readonly ref and readonly struct</span></span>](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [<span data-ttu-id="d5f39-175">lerapenas membros estrutura</span><span class="sxs-lookup"><span data-stu-id="d5f39-175">readonly struct members</span></span>](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a><span data-ttu-id="d5f39-176">Confira também</span><span class="sxs-lookup"><span data-stu-id="d5f39-176">See also</span></span>

- [<span data-ttu-id="d5f39-177">C# Referência</span><span class="sxs-lookup"><span data-stu-id="d5f39-177">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d5f39-178">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="d5f39-178">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d5f39-179">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="d5f39-179">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="d5f39-180">Modificadores</span><span class="sxs-lookup"><span data-stu-id="d5f39-180">Modifiers</span></span>](index.md)
- [<span data-ttu-id="d5f39-181">const</span><span class="sxs-lookup"><span data-stu-id="d5f39-181">const</span></span>](const.md)
- [<span data-ttu-id="d5f39-182">Campos</span><span class="sxs-lookup"><span data-stu-id="d5f39-182">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)
