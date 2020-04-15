---
title: Palavra-chave readonly – Referência de C#
ms.date: 04/14/2020
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 03b0aa63eda3e7a9d8745baaa33479fd5e85b01b
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389052"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="47e79-102">readonly (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="47e79-102">readonly (C# Reference)</span></span>

<span data-ttu-id="47e79-103">A `readonly` palavra-chave é um modificador que pode ser usado em quatro contextos:</span><span class="sxs-lookup"><span data-stu-id="47e79-103">The `readonly` keyword is a modifier that can be used in four contexts:</span></span>

- <span data-ttu-id="47e79-104">Em uma [declaração de campo,](#readonly-field-example) `readonly` indica que a atribuição ao campo só pode ocorrer como parte da declaração ou em um construtor da mesma classe.</span><span class="sxs-lookup"><span data-stu-id="47e79-104">In a [field declaration](#readonly-field-example), `readonly` indicates that assignment to the field can only occur as part of the declaration or in a constructor in the same class.</span></span> <span data-ttu-id="47e79-105">Um campo readonly pode ser atribuído e reatribuído várias vezes na declaração de campo e no construtor.</span><span class="sxs-lookup"><span data-stu-id="47e79-105">A readonly field can be assigned and reassigned multiple times within the field declaration and constructor.</span></span>
  
  <span data-ttu-id="47e79-106">Um `readonly` campo não pode ser atribuído depois que o construtor sair.</span><span class="sxs-lookup"><span data-stu-id="47e79-106">A `readonly` field can't be assigned after the constructor exits.</span></span> <span data-ttu-id="47e79-107">Esta regra tem diferentes implicações para tipos de valor e tipos de referência:</span><span class="sxs-lookup"><span data-stu-id="47e79-107">This rule has different implications for value types and reference types:</span></span>
  
  - <span data-ttu-id="47e79-108">Como os tipos de valor contêm diretamente seus dados, um campo que é um tipo de valor `readonly` é imutável.</span><span class="sxs-lookup"><span data-stu-id="47e79-108">Because value types directly contain their data, a field that is a  `readonly` value type is immutable.</span></span>
  - <span data-ttu-id="47e79-109">Como os tipos de referência contêm uma referência a seus dados, um campo que é um tipo de referência `readonly` deve sempre se referir ao mesmo objeto.</span><span class="sxs-lookup"><span data-stu-id="47e79-109">Because reference types contain a reference to their data, a field that is a `readonly` reference type must always refer to the same object.</span></span> <span data-ttu-id="47e79-110">Esse objeto não é imutável.</span><span class="sxs-lookup"><span data-stu-id="47e79-110">That object isn't immutable.</span></span> <span data-ttu-id="47e79-111">O modificador `readonly` impede que o campo seja substituído por uma instância diferente do tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="47e79-111">The `readonly` modifier prevents the field from being replaced by a different instance of the reference type.</span></span> <span data-ttu-id="47e79-112">No entanto, o modificador não impede que os dados de ocorrência do campo sejam modificados através do campo somente leitura.</span><span class="sxs-lookup"><span data-stu-id="47e79-112">However, the modifier doesn't prevent the instance data of the field from being modified through the read-only field.</span></span>

  > [!WARNING]
  > <span data-ttu-id="47e79-113">Um tipo externamente visível que contém um campo somente leitura externamente visível que seja um tipo de referência mutável pode ser uma vulnerabilidade de segurança e pode acionar o aviso [CA2104](/visualstudio/code-quality/ca2104) : "Não declare somente tipos de referência mutáveis".</span><span class="sxs-lookup"><span data-stu-id="47e79-113">An externally visible type that contains an externally visible read-only field that is a mutable reference type may be a security vulnerability and may trigger warning [CA2104](/visualstudio/code-quality/ca2104) : "Do not declare read only mutable reference types."</span></span>

- <span data-ttu-id="47e79-114">Em `readonly struct` uma definição `readonly` de tipo, indica que o tipo de estrutura é imutável.</span><span class="sxs-lookup"><span data-stu-id="47e79-114">In a `readonly struct` type definition, `readonly` indicates that the structure type is immutable.</span></span> <span data-ttu-id="47e79-115">Para obter mais [ `readonly` ](../builtin-types/struct.md#readonly-struct) informações, consulte a seção de estrutura do artigo [Tipos de Estrutura.](../builtin-types/struct.md)</span><span class="sxs-lookup"><span data-stu-id="47e79-115">For more information, see the [`readonly` struct](../builtin-types/struct.md#readonly-struct) section of the [Structure types](../builtin-types/struct.md) article.</span></span>
- <span data-ttu-id="47e79-116">Em uma declaração de membro `readonly` de instância dentro de um tipo de estrutura, indica que um membro de instância não modifica o estado da estrutura.</span><span class="sxs-lookup"><span data-stu-id="47e79-116">In an instance member declaration within a structure type, `readonly` indicates that an instance member doesn't modify the state of the structure.</span></span> <span data-ttu-id="47e79-117">Para obter mais [ `readonly` ](../builtin-types/struct.md#readonly-instance-members) informações, consulte a seção de membros de instância do artigo [Tipos de Estrutura.](../builtin-types/struct.md)</span><span class="sxs-lookup"><span data-stu-id="47e79-117">For more information, see the [`readonly` instance members](../builtin-types/struct.md#readonly-instance-members) section of the [Structure types](../builtin-types/struct.md) article.</span></span>
- <span data-ttu-id="47e79-118">Em um [ `ref readonly` retorno do método,](#ref-readonly-return-example)o modificador indica que o `readonly` método retorna uma referência e as gravações não são permitidas a essa referência.</span><span class="sxs-lookup"><span data-stu-id="47e79-118">In a [`ref readonly` method return](#ref-readonly-return-example), the `readonly` modifier indicates that method returns a reference and writes aren't allowed to that reference.</span></span>

<span data-ttu-id="47e79-119">Os `readonly struct` `ref readonly` contextos foram adicionados em C# 7.2.</span><span class="sxs-lookup"><span data-stu-id="47e79-119">The `readonly struct` and `ref readonly` contexts were added in C# 7.2.</span></span> <span data-ttu-id="47e79-120">`readonly`membros de estrutura foram adicionados em C # 8.0</span><span class="sxs-lookup"><span data-stu-id="47e79-120">`readonly` struct members were added in C# 8.0</span></span>

## <a name="readonly-field-example"></a><span data-ttu-id="47e79-121">Exemplo de campo readonly</span><span class="sxs-lookup"><span data-stu-id="47e79-121">Readonly field example</span></span>

<span data-ttu-id="47e79-122">Neste exemplo, o valor `year` do campo não pode `ChangeYear`ser alterado no método, mesmo que seja atribuído um valor no construtor de classe:</span><span class="sxs-lookup"><span data-stu-id="47e79-122">In this example, the value of the field `year` can't be changed in the method `ChangeYear`, even though it's assigned a value in the class constructor:</span></span>

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

<span data-ttu-id="47e79-123">Você pode atribuir um valor a um campo `readonly` apenas nos seguintes contextos:</span><span class="sxs-lookup"><span data-stu-id="47e79-123">You can assign a value to a `readonly` field only in the following contexts:</span></span>

- <span data-ttu-id="47e79-124">Quando a variável é inicializada na declaração, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="47e79-124">When the variable is initialized in the declaration, for example:</span></span>

  ```csharp
  public readonly int y = 5;
  ```

- <span data-ttu-id="47e79-125">Em um construtor de instância da classe que contém a declaração de campo de instância.</span><span class="sxs-lookup"><span data-stu-id="47e79-125">In an instance constructor of the class that contains the instance field declaration.</span></span>
- <span data-ttu-id="47e79-126">No construtor estático da classe que contém a declaração do campo estático.</span><span class="sxs-lookup"><span data-stu-id="47e79-126">In the static constructor of the class that contains the static field declaration.</span></span>

<span data-ttu-id="47e79-127">Esses contextos construtores também são os únicos contextos em `readonly` que é válido passar um campo como um parâmetro [de saída](out-parameter-modifier.md) ou [ref.](ref.md)</span><span class="sxs-lookup"><span data-stu-id="47e79-127">These constructor contexts are also the only contexts in which it's valid to pass a `readonly` field as an [out](out-parameter-modifier.md) or [ref](ref.md) parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="47e79-128">A palavra-chave `readonly` é diferente da palavra-chave [const](const.md).</span><span class="sxs-lookup"><span data-stu-id="47e79-128">The `readonly` keyword is different from the [const](const.md) keyword.</span></span> <span data-ttu-id="47e79-129">O campo `const` pode ser inicializado apenas na declaração do campo.</span><span class="sxs-lookup"><span data-stu-id="47e79-129">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="47e79-130">Um campo `readonly` pode ser atribuído várias vezes na declaração do campo e em qualquer construtor.</span><span class="sxs-lookup"><span data-stu-id="47e79-130">A `readonly` field can be assigned multiple times in the field declaration and in any constructor.</span></span> <span data-ttu-id="47e79-131">Portanto, campos `readonly` podem ter valores diferentes dependendo do construtor usado.</span><span class="sxs-lookup"><span data-stu-id="47e79-131">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="47e79-132">Além disso, `const` enquanto um campo é `readonly` uma constante de tempo de compilação, o campo pode ser usado para constantes de tempo de execução como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="47e79-132">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants as in the following example:</span></span>
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

<span data-ttu-id="47e79-133">No exemplo anterior, se você usar uma instrução semelhante ao seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="47e79-133">In the preceding example, if you use a statement like the following example:</span></span>

```csharp
p2.y = 66;        // Error
```

<span data-ttu-id="47e79-134">você receberá a mensagem de erro do compilador:</span><span class="sxs-lookup"><span data-stu-id="47e79-134">you'll get the compiler error message:</span></span>

<span data-ttu-id="47e79-135">**Um campo somente leitura não pode ser atribuído (exceto em um construtor ou em um inicializador de variáveis)**</span><span class="sxs-lookup"><span data-stu-id="47e79-135">**A readonly field cannot be assigned to (except in a constructor or a variable initializer)**</span></span>

## <a name="ref-readonly-return-example"></a><span data-ttu-id="47e79-136">Exemplo de retorno de readonly de ref</span><span class="sxs-lookup"><span data-stu-id="47e79-136">Ref readonly return example</span></span>

<span data-ttu-id="47e79-137">O `readonly` modificador `ref return` em um indica que a referência retornada não pode ser modificada.</span><span class="sxs-lookup"><span data-stu-id="47e79-137">The `readonly` modifier on a `ref return` indicates that the returned reference can't be modified.</span></span> <span data-ttu-id="47e79-138">O exemplo a seguir retorna uma referência para a origem.</span><span class="sxs-lookup"><span data-stu-id="47e79-138">The following example returns a reference to the origin.</span></span> <span data-ttu-id="47e79-139">Ele usa `readonly` o modificador para indicar que os chamadores não podem modificar a origem:</span><span class="sxs-lookup"><span data-stu-id="47e79-139">It uses the `readonly` modifier to indicate that callers can't modify the origin:</span></span>

[!code-csharp[readonly return example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]

<span data-ttu-id="47e79-140">O tipo retornado não precisa ser um `readonly struct`.</span><span class="sxs-lookup"><span data-stu-id="47e79-140">The type returned doesn't need to be a `readonly struct`.</span></span> <span data-ttu-id="47e79-141">Qualquer tipo que possa ser retornado por `ref` pode ser retornado por `ref readonly`.</span><span class="sxs-lookup"><span data-stu-id="47e79-141">Any type that can be returned by `ref` can be returned by `ref readonly`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="47e79-142">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="47e79-142">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

<span data-ttu-id="47e79-143">Você também pode ver as propostas de especificação do idioma:</span><span class="sxs-lookup"><span data-stu-id="47e79-143">You can also see the language specification proposals:</span></span>

- [<span data-ttu-id="47e79-144">readonly ref e readonly struct</span><span class="sxs-lookup"><span data-stu-id="47e79-144">readonly ref and readonly struct</span></span>](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [<span data-ttu-id="47e79-145">lerapenas membros estrutura</span><span class="sxs-lookup"><span data-stu-id="47e79-145">readonly struct members</span></span>](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a><span data-ttu-id="47e79-146">Confira também</span><span class="sxs-lookup"><span data-stu-id="47e79-146">See also</span></span>

- [<span data-ttu-id="47e79-147">C# Referência</span><span class="sxs-lookup"><span data-stu-id="47e79-147">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="47e79-148">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="47e79-148">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="47e79-149">C# Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="47e79-149">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="47e79-150">Modificadores</span><span class="sxs-lookup"><span data-stu-id="47e79-150">Modifiers</span></span>](index.md)
- [<span data-ttu-id="47e79-151">const</span><span class="sxs-lookup"><span data-stu-id="47e79-151">const</span></span>](const.md)
- [<span data-ttu-id="47e79-152">Fields</span><span class="sxs-lookup"><span data-stu-id="47e79-152">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)
