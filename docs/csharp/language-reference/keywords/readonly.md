---
title: Palavra-chave readonly – Referência de C#
ms.date: 04/14/2020
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 66a096e8831f72a2216e8ba5dd9866046504624f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368615"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="d730f-102">readonly (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="d730f-102">readonly (C# Reference)</span></span>

<span data-ttu-id="d730f-103">A `readonly` palavra-chave é um modificador que pode ser usado em quatro contextos:</span><span class="sxs-lookup"><span data-stu-id="d730f-103">The `readonly` keyword is a modifier that can be used in four contexts:</span></span>

- <span data-ttu-id="d730f-104">Em uma [declaração de campo](#readonly-field-example), `readonly` indica que a atribuição para o campo só pode ocorrer como parte da declaração ou em um construtor na mesma classe.</span><span class="sxs-lookup"><span data-stu-id="d730f-104">In a [field declaration](#readonly-field-example), `readonly` indicates that assignment to the field can only occur as part of the declaration or in a constructor in the same class.</span></span> <span data-ttu-id="d730f-105">Um campo readonly pode ser atribuído e reatribuído várias vezes na declaração de campo e no construtor.</span><span class="sxs-lookup"><span data-stu-id="d730f-105">A readonly field can be assigned and reassigned multiple times within the field declaration and constructor.</span></span>
  
  <span data-ttu-id="d730f-106">Um `readonly` campo não pode ser atribuído depois que o construtor é encerrado.</span><span class="sxs-lookup"><span data-stu-id="d730f-106">A `readonly` field can't be assigned after the constructor exits.</span></span> <span data-ttu-id="d730f-107">Essa regra tem implicações diferentes para tipos de valor e tipos de referência:</span><span class="sxs-lookup"><span data-stu-id="d730f-107">This rule has different implications for value types and reference types:</span></span>
  
  - <span data-ttu-id="d730f-108">Como os tipos de valor contêm diretamente seus dados, um campo que é um tipo de valor `readonly` é imutável.</span><span class="sxs-lookup"><span data-stu-id="d730f-108">Because value types directly contain their data, a field that is a  `readonly` value type is immutable.</span></span>
  - <span data-ttu-id="d730f-109">Como os tipos de referência contêm uma referência a seus dados, um campo que é um tipo de referência `readonly` deve sempre se referir ao mesmo objeto.</span><span class="sxs-lookup"><span data-stu-id="d730f-109">Because reference types contain a reference to their data, a field that is a `readonly` reference type must always refer to the same object.</span></span> <span data-ttu-id="d730f-110">Esse objeto não é imutável.</span><span class="sxs-lookup"><span data-stu-id="d730f-110">That object isn't immutable.</span></span> <span data-ttu-id="d730f-111">O modificador `readonly` impede que o campo seja substituído por uma instância diferente do tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="d730f-111">The `readonly` modifier prevents the field from being replaced by a different instance of the reference type.</span></span> <span data-ttu-id="d730f-112">No entanto, o modificador não impede que os dados da instância do campo sejam modificados por meio do campo somente leitura.</span><span class="sxs-lookup"><span data-stu-id="d730f-112">However, the modifier doesn't prevent the instance data of the field from being modified through the read-only field.</span></span>

  > [!WARNING]
  > <span data-ttu-id="d730f-113">Um tipo visível externamente que contém um campo somente leitura visível externamente, que é um tipo de referência mutável, pode ser uma vulnerabilidade de segurança e pode disparar o aviso [CA2104](/visualstudio/code-quality/ca2104) : "Não declare tipos de referência mutáveis somente leitura".</span><span class="sxs-lookup"><span data-stu-id="d730f-113">An externally visible type that contains an externally visible read-only field that is a mutable reference type may be a security vulnerability and may trigger warning [CA2104](/visualstudio/code-quality/ca2104) : "Do not declare read only mutable reference types."</span></span>

- <span data-ttu-id="d730f-114">Em uma `readonly struct` definição de tipo, `readonly` indica que o tipo de estrutura é imutável.</span><span class="sxs-lookup"><span data-stu-id="d730f-114">In a `readonly struct` type definition, `readonly` indicates that the structure type is immutable.</span></span> <span data-ttu-id="d730f-115">Para obter mais informações, consulte a seção [ `readonly` struct](../builtin-types/struct.md#readonly-struct) do artigo [tipos de estrutura](../builtin-types/struct.md) .</span><span class="sxs-lookup"><span data-stu-id="d730f-115">For more information, see the [`readonly` struct](../builtin-types/struct.md#readonly-struct) section of the [Structure types](../builtin-types/struct.md) article.</span></span>
- <span data-ttu-id="d730f-116">Em uma declaração de membro de instância dentro de um tipo de estrutura, `readonly` indica que um membro de instância não modifica o estado da estrutura.</span><span class="sxs-lookup"><span data-stu-id="d730f-116">In an instance member declaration within a structure type, `readonly` indicates that an instance member doesn't modify the state of the structure.</span></span> <span data-ttu-id="d730f-117">Para obter mais informações, consulte a seção [ `readonly` membros da instância](../builtin-types/struct.md#readonly-instance-members) do artigo [tipos de estrutura](../builtin-types/struct.md) .</span><span class="sxs-lookup"><span data-stu-id="d730f-117">For more information, see the [`readonly` instance members](../builtin-types/struct.md#readonly-instance-members) section of the [Structure types](../builtin-types/struct.md) article.</span></span>
- <span data-ttu-id="d730f-118">Em um [ `ref readonly` retorno de método](#ref-readonly-return-example), o `readonly` modificador indica que o método retorna uma referência e as gravações não são permitidas para essa referência.</span><span class="sxs-lookup"><span data-stu-id="d730f-118">In a [`ref readonly` method return](#ref-readonly-return-example), the `readonly` modifier indicates that method returns a reference and writes aren't allowed to that reference.</span></span>

<span data-ttu-id="d730f-119">Os `readonly struct` `ref readonly` contextos e foram adicionados em C# 7,2.</span><span class="sxs-lookup"><span data-stu-id="d730f-119">The `readonly struct` and `ref readonly` contexts were added in C# 7.2.</span></span> <span data-ttu-id="d730f-120">`readonly`Membros de struct foram adicionados em C# 8,0</span><span class="sxs-lookup"><span data-stu-id="d730f-120">`readonly` struct members were added in C# 8.0</span></span>

## <a name="readonly-field-example"></a><span data-ttu-id="d730f-121">Exemplo de campo readonly</span><span class="sxs-lookup"><span data-stu-id="d730f-121">Readonly field example</span></span>

<span data-ttu-id="d730f-122">Neste exemplo, o valor do campo `year` não pode ser alterado no método `ChangeYear` , mesmo que ele tenha sido atribuído a um valor no construtor da classe:</span><span class="sxs-lookup"><span data-stu-id="d730f-122">In this example, the value of the field `year` can't be changed in the method `ChangeYear`, even though it's assigned a value in the class constructor:</span></span>

[!code-csharp[Readonly Field example](snippets/ReadonlyKeywordExamples.cs#ReadonlyField)]

<span data-ttu-id="d730f-123">Você pode atribuir um valor a um campo `readonly` apenas nos seguintes contextos:</span><span class="sxs-lookup"><span data-stu-id="d730f-123">You can assign a value to a `readonly` field only in the following contexts:</span></span>

- <span data-ttu-id="d730f-124">Quando a variável é inicializada na declaração, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="d730f-124">When the variable is initialized in the declaration, for example:</span></span>

  ```csharp
  public readonly int y = 5;
  ```

- <span data-ttu-id="d730f-125">Em um construtor de instância da classe que contém a declaração de campo de instância.</span><span class="sxs-lookup"><span data-stu-id="d730f-125">In an instance constructor of the class that contains the instance field declaration.</span></span>
- <span data-ttu-id="d730f-126">No construtor estático da classe que contém a declaração do campo estático.</span><span class="sxs-lookup"><span data-stu-id="d730f-126">In the static constructor of the class that contains the static field declaration.</span></span>

<span data-ttu-id="d730f-127">Esses contextos de Construtor também são os únicos contextos em que é válido passar um `readonly` campo como um parâmetro [out](out-parameter-modifier.md) ou [ref](ref.md) .</span><span class="sxs-lookup"><span data-stu-id="d730f-127">These constructor contexts are also the only contexts in which it's valid to pass a `readonly` field as an [out](out-parameter-modifier.md) or [ref](ref.md) parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="d730f-128">A palavra-chave `readonly` é diferente da palavra-chave [const](const.md).</span><span class="sxs-lookup"><span data-stu-id="d730f-128">The `readonly` keyword is different from the [const](const.md) keyword.</span></span> <span data-ttu-id="d730f-129">O campo `const` pode ser inicializado apenas na declaração do campo.</span><span class="sxs-lookup"><span data-stu-id="d730f-129">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="d730f-130">Um campo `readonly` pode ser atribuído várias vezes na declaração do campo e em qualquer construtor.</span><span class="sxs-lookup"><span data-stu-id="d730f-130">A `readonly` field can be assigned multiple times in the field declaration and in any constructor.</span></span> <span data-ttu-id="d730f-131">Portanto, campos `readonly` podem ter valores diferentes dependendo do construtor usado.</span><span class="sxs-lookup"><span data-stu-id="d730f-131">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="d730f-132">Além disso, embora um `const` campo seja uma constante de tempo de compilação, o `readonly` campo pode ser usado para constantes de tempo de execução como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="d730f-132">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants as in the following example:</span></span>
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](snippets/ReadonlyKeywordExamples.cs#InitReadonlyField)]

<span data-ttu-id="d730f-133">No exemplo anterior, se você usar uma instrução semelhante ao seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="d730f-133">In the preceding example, if you use a statement like the following example:</span></span>

```csharp
p2.y = 66;        // Error
```

<span data-ttu-id="d730f-134">Você obterá a mensagem de erro do compilador:</span><span class="sxs-lookup"><span data-stu-id="d730f-134">you'll get the compiler error message:</span></span>

<span data-ttu-id="d730f-135">**Um campo ReadOnly não pode ser atribuído (exceto em um construtor ou inicializador de variável)**</span><span class="sxs-lookup"><span data-stu-id="d730f-135">**A readonly field cannot be assigned to (except in a constructor or a variable initializer)**</span></span>

## <a name="ref-readonly-return-example"></a><span data-ttu-id="d730f-136">Exemplo de retorno de readonly de ref</span><span class="sxs-lookup"><span data-stu-id="d730f-136">Ref readonly return example</span></span>

<span data-ttu-id="d730f-137">O `readonly` modificador em um `ref return` indica que a referência retornada não pode ser modificada.</span><span class="sxs-lookup"><span data-stu-id="d730f-137">The `readonly` modifier on a `ref return` indicates that the returned reference can't be modified.</span></span> <span data-ttu-id="d730f-138">O exemplo a seguir retorna uma referência para a origem.</span><span class="sxs-lookup"><span data-stu-id="d730f-138">The following example returns a reference to the origin.</span></span> <span data-ttu-id="d730f-139">Ele usa o `readonly` modificador para indicar que os chamadores não podem modificar a origem:</span><span class="sxs-lookup"><span data-stu-id="d730f-139">It uses the `readonly` modifier to indicate that callers can't modify the origin:</span></span>

[!code-csharp[readonly return example](snippets/ReadonlyKeywordExamples.cs#ReadonlyReturn)]

<span data-ttu-id="d730f-140">O tipo retornado não precisa ser um `readonly struct`.</span><span class="sxs-lookup"><span data-stu-id="d730f-140">The type returned doesn't need to be a `readonly struct`.</span></span> <span data-ttu-id="d730f-141">Qualquer tipo que possa ser retornado por `ref` pode ser retornado por `ref readonly`.</span><span class="sxs-lookup"><span data-stu-id="d730f-141">Any type that can be returned by `ref` can be returned by `ref readonly`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d730f-142">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="d730f-142">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

<span data-ttu-id="d730f-143">Você também pode ver as propostas de especificação de idioma:</span><span class="sxs-lookup"><span data-stu-id="d730f-143">You can also see the language specification proposals:</span></span>

- [<span data-ttu-id="d730f-144">struct de ref e ReadOnly ReadOnly</span><span class="sxs-lookup"><span data-stu-id="d730f-144">readonly ref and readonly struct</span></span>](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [<span data-ttu-id="d730f-145">Membros de struct ReadOnly</span><span class="sxs-lookup"><span data-stu-id="d730f-145">readonly struct members</span></span>](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a><span data-ttu-id="d730f-146">Confira também</span><span class="sxs-lookup"><span data-stu-id="d730f-146">See also</span></span>

- [<span data-ttu-id="d730f-147">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="d730f-147">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d730f-148">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="d730f-148">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d730f-149">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="d730f-149">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="d730f-150">Modificadores</span><span class="sxs-lookup"><span data-stu-id="d730f-150">Modifiers</span></span>](index.md)
- [<span data-ttu-id="d730f-151">const</span><span class="sxs-lookup"><span data-stu-id="d730f-151">const</span></span>](const.md)
- [<span data-ttu-id="d730f-152">Fields</span><span class="sxs-lookup"><span data-stu-id="d730f-152">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)
