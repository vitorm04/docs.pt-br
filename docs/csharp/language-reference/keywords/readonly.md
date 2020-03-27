---
title: Palavra-chave readonly – Referência de C#
ms.date: 03/26/2020
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 344d5e54fcd500e283c52fa7953c6366823f13f0
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345146"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="19fb8-102">readonly (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="19fb8-102">readonly (C# Reference)</span></span>

<span data-ttu-id="19fb8-103">A `readonly` palavra-chave é um modificador que pode ser usado em quatro contextos:</span><span class="sxs-lookup"><span data-stu-id="19fb8-103">The `readonly` keyword is a modifier that can be used in four contexts:</span></span>

- <span data-ttu-id="19fb8-104">Em uma [declaração de campo,](#readonly-field-example) `readonly` indica que a atribuição ao campo só pode ocorrer como parte da declaração ou em um construtor da mesma classe.</span><span class="sxs-lookup"><span data-stu-id="19fb8-104">In a [field declaration](#readonly-field-example), `readonly` indicates that assignment to the field can only occur as part of the declaration or in a constructor in the same class.</span></span> <span data-ttu-id="19fb8-105">Um campo readonly pode ser atribuído e reatribuído várias vezes na declaração de campo e no construtor.</span><span class="sxs-lookup"><span data-stu-id="19fb8-105">A readonly field can be assigned and reassigned multiple times within the field declaration and constructor.</span></span>
  
  <span data-ttu-id="19fb8-106">Um `readonly` campo não pode ser atribuído depois que o construtor sair.</span><span class="sxs-lookup"><span data-stu-id="19fb8-106">A `readonly` field can't be assigned after the constructor exits.</span></span> <span data-ttu-id="19fb8-107">Esta regra tem diferentes implicações para tipos de valor e tipos de referência:</span><span class="sxs-lookup"><span data-stu-id="19fb8-107">This rule has different implications for value types and reference types:</span></span>
  
  - <span data-ttu-id="19fb8-108">Como os tipos de valor contêm diretamente seus dados, um campo que é um tipo de valor `readonly` é imutável.</span><span class="sxs-lookup"><span data-stu-id="19fb8-108">Because value types directly contain their data, a field that is a  `readonly` value type is immutable.</span></span>
  - <span data-ttu-id="19fb8-109">Como os tipos de referência contêm uma referência a seus dados, um campo que é um tipo de referência `readonly` deve sempre se referir ao mesmo objeto.</span><span class="sxs-lookup"><span data-stu-id="19fb8-109">Because reference types contain a reference to their data, a field that is a `readonly` reference type must always refer to the same object.</span></span> <span data-ttu-id="19fb8-110">Esse objeto não é imutável.</span><span class="sxs-lookup"><span data-stu-id="19fb8-110">That object isn't immutable.</span></span> <span data-ttu-id="19fb8-111">O modificador `readonly` impede que o campo seja substituído por uma instância diferente do tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="19fb8-111">The `readonly` modifier prevents the field from being replaced by a different instance of the reference type.</span></span> <span data-ttu-id="19fb8-112">No entanto, o modificador não impede que os dados de ocorrência do campo sejam modificados através do campo somente leitura.</span><span class="sxs-lookup"><span data-stu-id="19fb8-112">However, the modifier doesn't prevent the instance data of the field from being modified through the read-only field.</span></span>

  > [!WARNING]
  > <span data-ttu-id="19fb8-113">Um tipo externamente visível que contém um campo somente leitura externamente visível que seja um tipo de referência mutável pode ser uma vulnerabilidade de segurança e pode acionar o aviso [CA2104](/visualstudio/code-quality/ca2104) : "Não declare somente tipos de referência mutáveis".</span><span class="sxs-lookup"><span data-stu-id="19fb8-113">An externally visible type that contains an externally visible read-only field that is a mutable reference type may be a security vulnerability and may trigger warning [CA2104](/visualstudio/code-quality/ca2104) : "Do not declare read only mutable reference types."</span></span>

- <span data-ttu-id="19fb8-114">Em `readonly struct` uma definição `readonly` de tipo, indica que o tipo de estrutura é imutável.</span><span class="sxs-lookup"><span data-stu-id="19fb8-114">In a `readonly struct` type definition, `readonly` indicates that the structure type is immutable.</span></span> <span data-ttu-id="19fb8-115">Para obter mais [ `readonly` ](../builtin-types/struct.md#readonly-struct) informações, consulte a seção de estrutura do artigo [Tipos de Estrutura.](../builtin-types/struct.md)</span><span class="sxs-lookup"><span data-stu-id="19fb8-115">For more information, see the [`readonly` struct](../builtin-types/struct.md#readonly-struct) section of the [Structure types](../builtin-types/struct.md) article.</span></span>
- <span data-ttu-id="19fb8-116">Em uma `readonly` `struct` [ `readonly` definição de membro,](#readonly-member-examples)indica que um membro de um não muta o estado interno da estrutura.</span><span class="sxs-lookup"><span data-stu-id="19fb8-116">In a [`readonly` member definition](#readonly-member-examples), `readonly` indicates that a member of a `struct` doesn't mutate the struct's internal state.</span></span>
- <span data-ttu-id="19fb8-117">Em um [ `ref readonly` retorno do método,](#ref-readonly-return-example)o modificador indica que o `readonly` método retorna uma referência e as gravações não são permitidas a essa referência.</span><span class="sxs-lookup"><span data-stu-id="19fb8-117">In a [`ref readonly` method return](#ref-readonly-return-example), the `readonly` modifier indicates that method returns a reference and writes aren't allowed to that reference.</span></span>

<span data-ttu-id="19fb8-118">Os `readonly struct` `ref readonly` contextos foram adicionados em C# 7.2.</span><span class="sxs-lookup"><span data-stu-id="19fb8-118">The `readonly struct` and `ref readonly` contexts were added in C# 7.2.</span></span> <span data-ttu-id="19fb8-119">`readonly`membros de estrutura foram adicionados em C # 8.0</span><span class="sxs-lookup"><span data-stu-id="19fb8-119">`readonly` struct members were added in C# 8.0</span></span>

## <a name="readonly-field-example"></a><span data-ttu-id="19fb8-120">Exemplo de campo readonly</span><span class="sxs-lookup"><span data-stu-id="19fb8-120">Readonly field example</span></span>

<span data-ttu-id="19fb8-121">Neste exemplo, o valor `year` do campo não pode `ChangeYear`ser alterado no método, mesmo que seja atribuído um valor no construtor de classe:</span><span class="sxs-lookup"><span data-stu-id="19fb8-121">In this example, the value of the field `year` can't be changed in the method `ChangeYear`, even though it's assigned a value in the class constructor:</span></span>

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

<span data-ttu-id="19fb8-122">Você pode atribuir um valor a um campo `readonly` apenas nos seguintes contextos:</span><span class="sxs-lookup"><span data-stu-id="19fb8-122">You can assign a value to a `readonly` field only in the following contexts:</span></span>

- <span data-ttu-id="19fb8-123">Quando a variável é inicializada na declaração, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="19fb8-123">When the variable is initialized in the declaration, for example:</span></span>

  ```csharp
  public readonly int y = 5;
  ```

- <span data-ttu-id="19fb8-124">Em um construtor de instância da classe que contém a declaração de campo de instância.</span><span class="sxs-lookup"><span data-stu-id="19fb8-124">In an instance constructor of the class that contains the instance field declaration.</span></span>
- <span data-ttu-id="19fb8-125">No construtor estático da classe que contém a declaração do campo estático.</span><span class="sxs-lookup"><span data-stu-id="19fb8-125">In the static constructor of the class that contains the static field declaration.</span></span>

<span data-ttu-id="19fb8-126">Esses contextos construtores também são os únicos contextos em `readonly` que é válido passar um campo como um parâmetro [de saída](out-parameter-modifier.md) ou [ref.](ref.md)</span><span class="sxs-lookup"><span data-stu-id="19fb8-126">These constructor contexts are also the only contexts in which it's valid to pass a `readonly` field as an [out](out-parameter-modifier.md) or [ref](ref.md) parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="19fb8-127">A palavra-chave `readonly` é diferente da palavra-chave [const](const.md).</span><span class="sxs-lookup"><span data-stu-id="19fb8-127">The `readonly` keyword is different from the [const](const.md) keyword.</span></span> <span data-ttu-id="19fb8-128">O campo `const` pode ser inicializado apenas na declaração do campo.</span><span class="sxs-lookup"><span data-stu-id="19fb8-128">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="19fb8-129">Um campo `readonly` pode ser atribuído várias vezes na declaração do campo e em qualquer construtor.</span><span class="sxs-lookup"><span data-stu-id="19fb8-129">A `readonly` field can be assigned multiple times in the field declaration and in any constructor.</span></span> <span data-ttu-id="19fb8-130">Portanto, campos `readonly` podem ter valores diferentes dependendo do construtor usado.</span><span class="sxs-lookup"><span data-stu-id="19fb8-130">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="19fb8-131">Além disso, `const` enquanto um campo é `readonly` uma constante de tempo de compilação, o campo pode ser usado para constantes de tempo de execução como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="19fb8-131">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants as in the following example:</span></span>
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

<span data-ttu-id="19fb8-132">No exemplo anterior, se você usar uma instrução semelhante ao seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="19fb8-132">In the preceding example, if you use a statement like the following example:</span></span>

```csharp
p2.y = 66;        // Error
```

<span data-ttu-id="19fb8-133">você receberá a mensagem de erro do compilador:</span><span class="sxs-lookup"><span data-stu-id="19fb8-133">you'll get the compiler error message:</span></span>

<span data-ttu-id="19fb8-134">**Um campo somente leitura não pode ser atribuído (exceto em um construtor ou em um inicializador de variáveis)**</span><span class="sxs-lookup"><span data-stu-id="19fb8-134">**A readonly field cannot be assigned to (except in a constructor or a variable initializer)**</span></span>

## <a name="readonly-member-examples"></a><span data-ttu-id="19fb8-135">Leia apenas exemplos de membros</span><span class="sxs-lookup"><span data-stu-id="19fb8-135">Readonly member examples</span></span>

<span data-ttu-id="19fb8-136">Outras vezes, você pode criar uma estrutura que suporta mutação.</span><span class="sxs-lookup"><span data-stu-id="19fb8-136">Other times, you may create a struct that supports mutation.</span></span> <span data-ttu-id="19fb8-137">Nesses casos, vários dos membros da instância provavelmente não modificarão o estado interno da estrutura.</span><span class="sxs-lookup"><span data-stu-id="19fb8-137">In those cases, several of the instance members likely won't modify the internal state of the struct.</span></span> <span data-ttu-id="19fb8-138">Você pode declarar esses `readonly` membros de instância com o modificador.</span><span class="sxs-lookup"><span data-stu-id="19fb8-138">You can declare those instance members with the `readonly` modifier.</span></span> <span data-ttu-id="19fb8-139">O compilador reforça sua intenção.</span><span class="sxs-lookup"><span data-stu-id="19fb8-139">The compiler enforces your intent.</span></span> <span data-ttu-id="19fb8-140">Se esse membro modificar o estado diretamente ou acessar um membro `readonly` que também não é declarado com o modificador, o resultado será um erro de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="19fb8-140">If that member modifies state directly or accesses a member that isn't also declared with the `readonly` modifier, the result is a compile-time error.</span></span> <span data-ttu-id="19fb8-141">O `readonly` modificador é `struct` válido `class` em `interface` declarações de membros, não de membros.</span><span class="sxs-lookup"><span data-stu-id="19fb8-141">The `readonly` modifier is valid on `struct` members, not `class` or `interface` member declarations.</span></span>

<span data-ttu-id="19fb8-142">Você ganha duas vantagens `readonly` aplicando o `struct` modificador aos métodos aplicáveis.</span><span class="sxs-lookup"><span data-stu-id="19fb8-142">You gain two advantages by applying the `readonly` modifier to applicable `struct` methods.</span></span> <span data-ttu-id="19fb8-143">Mais importante, o compilador reforça sua intenção.</span><span class="sxs-lookup"><span data-stu-id="19fb8-143">Most importantly, the compiler enforces your intent.</span></span> <span data-ttu-id="19fb8-144">Código que modifica estado não é `readonly` válido em um método.</span><span class="sxs-lookup"><span data-stu-id="19fb8-144">Code that modifies state isn't valid in a `readonly` method.</span></span> <span data-ttu-id="19fb8-145">O compilador também pode fazer `readonly` uso do modificador para permitir otimizações de desempenho.</span><span class="sxs-lookup"><span data-stu-id="19fb8-145">The compiler may also make use of the `readonly` modifier to enable performance optimizations.</span></span> <span data-ttu-id="19fb8-146">Quando `struct` grandes tipos `in` são passados por referência, o compilador deve gerar uma cópia defensiva se o estado da estrutura pode ser modificado.</span><span class="sxs-lookup"><span data-stu-id="19fb8-146">When large `struct` types are passed by `in` reference, the compiler must generate a defensive copy if the state of the struct might be modified.</span></span> <span data-ttu-id="19fb8-147">Se `readonly` apenas membros forem acessados, o compilador não poderá criar a cópia defensiva.</span><span class="sxs-lookup"><span data-stu-id="19fb8-147">If only `readonly` members are accessed, the compiler may not create the defensive copy.</span></span>

<span data-ttu-id="19fb8-148">O `readonly` modificador é válido na `struct`maioria dos membros de a, <xref:System.Object?displayProperty=nameWithType>incluindo métodos que sobrepõem métodos declarados em .</span><span class="sxs-lookup"><span data-stu-id="19fb8-148">The `readonly` modifier is valid on most members of a `struct`, including methods that override methods declared in <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="19fb8-149">Existem algumas restrições:</span><span class="sxs-lookup"><span data-stu-id="19fb8-149">There are some restrictions:</span></span>

- <span data-ttu-id="19fb8-150">Você não pode `readonly` declarar métodos ou propriedades estáticas.</span><span class="sxs-lookup"><span data-stu-id="19fb8-150">You can't declare `readonly` static methods or properties.</span></span>
- <span data-ttu-id="19fb8-151">Você não pode `readonly` declarar construtores.</span><span class="sxs-lookup"><span data-stu-id="19fb8-151">You can't declare `readonly` constructors.</span></span>

<span data-ttu-id="19fb8-152">Você pode `readonly` adicionar o modificador a uma declaração de propriedade ou indexador:</span><span class="sxs-lookup"><span data-stu-id="19fb8-152">You can add the `readonly` modifier to a property or indexer declaration:</span></span>

```csharp
readonly public int Counter
{
  get { return 0; }
  set {} // not useful, but legal
}
```

<span data-ttu-id="19fb8-153">Você também pode `readonly` adicionar o `get` `set` modificador a um indivíduo ou acessórios de uma propriedade ou indexador:</span><span class="sxs-lookup"><span data-stu-id="19fb8-153">You may also add the `readonly` modifier to individual `get` or `set` accessors of a property or indexer:</span></span>

```csharp
public int Counter
{
  readonly get { return _counter; }
  set { _counter = value; }
}
int _counter;
```

<span data-ttu-id="19fb8-154">Você não pode `readonly` adicionar o modificador a uma propriedade e a um ou mais dos acessórios dessa mesma propriedade.</span><span class="sxs-lookup"><span data-stu-id="19fb8-154">You may not add the `readonly` modifier to both a property and one or more of that same property's accessors.</span></span> <span data-ttu-id="19fb8-155">Essa mesma restrição se aplica aos indexadores.</span><span class="sxs-lookup"><span data-stu-id="19fb8-155">That same restriction applies to indexers.</span></span>

<span data-ttu-id="19fb8-156">O compilador aplica implicitamente o `readonly` modificador a propriedades implementadas automaticamente onde o código implementado pelo compilador não modifica o estado.</span><span class="sxs-lookup"><span data-stu-id="19fb8-156">The compiler implicitly applies the `readonly` modifier to auto-implemented properties where the compiler implemented code doesn't modify state.</span></span> <span data-ttu-id="19fb8-157">Equivale às seguintes declarações:</span><span class="sxs-lookup"><span data-stu-id="19fb8-157">It's equivalent to the following declarations:</span></span>

```csharp
public readonly int Index { get; }
// Or:
public int Number { readonly get; }
public string Message { readonly get; set; }
```

<span data-ttu-id="19fb8-158">Você pode `readonly` adicionar o modificador nesses locais, mas não terá nenhum efeito significativo.</span><span class="sxs-lookup"><span data-stu-id="19fb8-158">You may add the `readonly` modifier in those locations, but it will have no meaningful effect.</span></span> <span data-ttu-id="19fb8-159">Você não pode `readonly` adicionar o modificador a um definidor de propriedade implementado automaticamente ou a uma propriedade de leitura/gravação implementada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="19fb8-159">You may not add the `readonly` modifier to an auto-implemented property setter, or to a read/write auto-implemented property.</span></span>

## <a name="ref-readonly-return-example"></a><span data-ttu-id="19fb8-160">Exemplo de retorno de readonly de ref</span><span class="sxs-lookup"><span data-stu-id="19fb8-160">Ref readonly return example</span></span>

<span data-ttu-id="19fb8-161">O `readonly` modificador `ref return` em um indica que a referência retornada não pode ser modificada.</span><span class="sxs-lookup"><span data-stu-id="19fb8-161">The `readonly` modifier on a `ref return` indicates that the returned reference can't be modified.</span></span> <span data-ttu-id="19fb8-162">O exemplo a seguir retorna uma referência para a origem.</span><span class="sxs-lookup"><span data-stu-id="19fb8-162">The following example returns a reference to the origin.</span></span> <span data-ttu-id="19fb8-163">Ele usa `readonly` o modificador para indicar que os chamadores não podem modificar a origem:</span><span class="sxs-lookup"><span data-stu-id="19fb8-163">It uses the `readonly` modifier to indicate that callers can't modify the origin:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]

<span data-ttu-id="19fb8-164">O tipo retornado não precisa ser um `readonly struct`.</span><span class="sxs-lookup"><span data-stu-id="19fb8-164">The type returned doesn't need to be a `readonly struct`.</span></span> <span data-ttu-id="19fb8-165">Qualquer tipo que possa ser retornado por `ref` pode ser retornado por `ref readonly`.</span><span class="sxs-lookup"><span data-stu-id="19fb8-165">Any type that can be returned by `ref` can be returned by `ref readonly`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="19fb8-166">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="19fb8-166">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

<span data-ttu-id="19fb8-167">Você também pode ver as propostas de especificação do idioma:</span><span class="sxs-lookup"><span data-stu-id="19fb8-167">You can also see the language specification proposals:</span></span>

- [<span data-ttu-id="19fb8-168">readonly ref e readonly struct</span><span class="sxs-lookup"><span data-stu-id="19fb8-168">readonly ref and readonly struct</span></span>](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [<span data-ttu-id="19fb8-169">lerapenas membros estrutura</span><span class="sxs-lookup"><span data-stu-id="19fb8-169">readonly struct members</span></span>](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a><span data-ttu-id="19fb8-170">Confira também</span><span class="sxs-lookup"><span data-stu-id="19fb8-170">See also</span></span>

- [<span data-ttu-id="19fb8-171">C# Referência</span><span class="sxs-lookup"><span data-stu-id="19fb8-171">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="19fb8-172">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="19fb8-172">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="19fb8-173">C# Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="19fb8-173">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="19fb8-174">Modificadores</span><span class="sxs-lookup"><span data-stu-id="19fb8-174">Modifiers</span></span>](index.md)
- [<span data-ttu-id="19fb8-175">const</span><span class="sxs-lookup"><span data-stu-id="19fb8-175">const</span></span>](const.md)
- [<span data-ttu-id="19fb8-176">Campos</span><span class="sxs-lookup"><span data-stu-id="19fb8-176">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)
