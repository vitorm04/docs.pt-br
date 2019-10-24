---
title: Palavra-chave enum – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- enum
- enum_CSharpKeyword
helpviewer_keywords:
- enum keyword [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
ms.openlocfilehash: 417f02ce9e8ee88edeb2a4dab88111cae39a8a4b
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771863"
---
# <a name="enum-c-reference"></a><span data-ttu-id="17f3c-102">enum (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="17f3c-102">enum (C# Reference)</span></span>

<span data-ttu-id="17f3c-103">A palavra-chave `enum` é usada para declarar uma enumeração, um tipo distinto que consiste em um conjunto de constantes nomeadas denominado lista de enumeradores.</span><span class="sxs-lookup"><span data-stu-id="17f3c-103">The `enum` keyword is used to declare an enumeration, a distinct type that consists of a set of named constants called the enumerator list.</span></span>

<span data-ttu-id="17f3c-104">Normalmente, é melhor definir um enum diretamente dentro de um namespace para que todas as classes no namespace possam acessá-lo com a mesma conveniência.</span><span class="sxs-lookup"><span data-stu-id="17f3c-104">Usually it is best to define an enum directly within a namespace so that all classes in the namespace can access it with equal convenience.</span></span> <span data-ttu-id="17f3c-105">No entanto, um enum também pode ser aninhado dentro de uma classe ou struct.</span><span class="sxs-lookup"><span data-stu-id="17f3c-105">However, an enum can also be nested within a class or struct.</span></span>

<span data-ttu-id="17f3c-106">Por padrão, o primeiro enumerador tem o valor 0 e o valor de cada enumerador seguinte é aumentado em 1.</span><span class="sxs-lookup"><span data-stu-id="17f3c-106">By default, the first enumerator has the value 0, and the value of each successive enumerator is increased by 1.</span></span> <span data-ttu-id="17f3c-107">Por exemplo, na seguinte enumeração, `Sat` é `0`, `Sun` é `1`, `Mon` é `2` e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="17f3c-107">For example, in the following enumeration, `Sat` is `0`, `Sun` is `1`, `Mon` is `2`, and so forth.</span></span>

```csharp
enum Day {Sat, Sun, Mon, Tue, Wed, Thu, Fri};
```

<span data-ttu-id="17f3c-108">Enumeradores podem usar inicializadores para substituir os valores padrão, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="17f3c-108">Enumerators can use initializers to override the default values, as shown in the following example.</span></span>

```csharp
enum Day {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

<span data-ttu-id="17f3c-109">Nesta enumeração, a sequência de elementos é forçada a iniciar a partir de `1` em vez de `0`.</span><span class="sxs-lookup"><span data-stu-id="17f3c-109">In this enumeration, the sequence of elements is forced to start from `1` instead of `0`.</span></span> <span data-ttu-id="17f3c-110">No entanto, incluir uma constante que tenha o valor de 0 é recomendado.</span><span class="sxs-lookup"><span data-stu-id="17f3c-110">However, including a constant that has the value of 0 is recommended.</span></span> <span data-ttu-id="17f3c-111">Para obter mais informações, consulte [Tipos de enumeração](../../programming-guide/enumeration-types.md).</span><span class="sxs-lookup"><span data-stu-id="17f3c-111">For more information, see [Enumeration Types](../../programming-guide/enumeration-types.md).</span></span>

<span data-ttu-id="17f3c-112">Cada tipo de enumeração tem um tipo subjacente, que pode ser qualquer [tipo numérico integral](../builtin-types/integral-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="17f3c-112">Every enumeration type has an underlying type, which can be any [integral numeric type](../builtin-types/integral-numeric-types.md).</span></span> <span data-ttu-id="17f3c-113">O tipo [char](char.md) não pode ser um tipo subjacente de um enum.</span><span class="sxs-lookup"><span data-stu-id="17f3c-113">The [char](char.md) type cannot be an underlying type of an enum.</span></span> <span data-ttu-id="17f3c-114">O tipo subjacente padrão de elementos de enumeração é [int](../builtin-types/integral-numeric-types.md). Para declarar uma enumeração de outro tipo integral, como [byte](../builtin-types/integral-numeric-types.md), use dois-pontos após o identificador seguido pelo tipo, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="17f3c-114">The default underlying type of enumeration elements is [int](../builtin-types/integral-numeric-types.md). To declare an enum of another integral type, such as [byte](../builtin-types/integral-numeric-types.md), use a colon after the identifier followed by the type, as shown in the following example.</span></span>

```csharp
enum Day : byte {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

<span data-ttu-id="17f3c-115">Uma variável de um tipo de enumeração pode receber qualquer valor no intervalo do tipo subjacente; os valores não são limitados às constantes nomeadas.</span><span class="sxs-lookup"><span data-stu-id="17f3c-115">A variable of an enumeration type can be assigned any value in the range of the underlying type; the values are not limited to the named constants.</span></span>

<span data-ttu-id="17f3c-116">O valor padrão de um `enum E` é o valor produzido pela expressão `(E)0`.</span><span class="sxs-lookup"><span data-stu-id="17f3c-116">The default value of an `enum E` is the value produced by the expression `(E)0`.</span></span>

> [!NOTE]
> <span data-ttu-id="17f3c-117">Um enumerador não pode conter espaços em branco em seu nome.</span><span class="sxs-lookup"><span data-stu-id="17f3c-117">An enumerator cannot contain white space in its name.</span></span>

<span data-ttu-id="17f3c-118">O tipo subjacente especifica quanto armazenamento é alocado para cada enumerador.</span><span class="sxs-lookup"><span data-stu-id="17f3c-118">The underlying type specifies how much storage is allocated for each enumerator.</span></span> <span data-ttu-id="17f3c-119">No entanto, uma conversão explícita é necessária para converter de um tipo `enum` em um tipo integral.</span><span class="sxs-lookup"><span data-stu-id="17f3c-119">However, an explicit cast is necessary to convert from `enum` type to an integral type.</span></span> <span data-ttu-id="17f3c-120">Por exemplo, a instrução a seguir atribui o enumerador `Sun` a uma variável do tipo [int](../builtin-types/integral-numeric-types.md) usando uma conversão para converter de `enum` em `int`.</span><span class="sxs-lookup"><span data-stu-id="17f3c-120">For example, the following statement assigns the enumerator `Sun` to a variable of the type [int](../builtin-types/integral-numeric-types.md) by using a cast to convert from `enum` to `int`.</span></span>

```csharp
int x = (int)Day.Sun;
```

<span data-ttu-id="17f3c-121">Quando você aplica <xref:System.FlagsAttribute?displayProperty=nameWithType> a uma enumeração que contém elementos que podem ser combinados com uma operação `OR` bit a bit, o atributo afeta o comportamento do `enum` quando ele é usado com algumas ferramentas.</span><span class="sxs-lookup"><span data-stu-id="17f3c-121">When you apply <xref:System.FlagsAttribute?displayProperty=nameWithType> to an enumeration that contains elements that can be combined with a bitwise `OR` operation, the attribute affects the behavior of the `enum` when it is used with some tools.</span></span> <span data-ttu-id="17f3c-122">Você pode observar essas alterações quando usa ferramentas como os métodos da classe <xref:System.Console> e o Avaliador de Expressão.</span><span class="sxs-lookup"><span data-stu-id="17f3c-122">You can notice these changes when you use tools such as the <xref:System.Console> class methods and the Expression Evaluator.</span></span> <span data-ttu-id="17f3c-123">(Consulte o terceiro exemplo.)</span><span class="sxs-lookup"><span data-stu-id="17f3c-123">(See the third example.)</span></span>

## <a name="robust-programming"></a><span data-ttu-id="17f3c-124">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="17f3c-124">Robust programming</span></span>

<span data-ttu-id="17f3c-125">Assim como ocorre com qualquer constante, todas as referências aos valores individuais de um enum são convertidas em literais numéricos em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="17f3c-125">Just as with any constant, all references to the individual values of an enum are converted to numeric literals at compile time.</span></span> <span data-ttu-id="17f3c-126">Isso pode criar problemas de controle de versão, conforme descrito em [Constantes](../../programming-guide/classes-and-structs/constants.md).</span><span class="sxs-lookup"><span data-stu-id="17f3c-126">This can create potential versioning issues as described in [Constants](../../programming-guide/classes-and-structs/constants.md).</span></span>

<span data-ttu-id="17f3c-127">Atribuir valores adicionais a novas versões de enums ou alterar os valores dos membros de enum em uma nova versão pode causar problemas para códigos-fonte dependentes.</span><span class="sxs-lookup"><span data-stu-id="17f3c-127">Assigning additional values to new versions of enums, or changing the values of the enum members in a new version, can cause problems for dependent source code.</span></span> <span data-ttu-id="17f3c-128">Valores de enum frequentemente são usados em instruções [switch](switch.md).</span><span class="sxs-lookup"><span data-stu-id="17f3c-128">Enum values often are used in [switch](switch.md) statements.</span></span> <span data-ttu-id="17f3c-129">Se elementos adicionais tiverem sido adicionados ao tipo `enum`, a seção padrão da instrução switch pode ser selecionada inesperadamente.</span><span class="sxs-lookup"><span data-stu-id="17f3c-129">If additional elements have been added to the `enum` type, the default section of the switch statement can be selected unexpectedly.</span></span>

<span data-ttu-id="17f3c-130">Se outros desenvolvedores usarem seu código, você deverá fornecer diretrizes sobre como seu código deve reagir se novos elementos forem adicionados a qualquer tipo `enum`.</span><span class="sxs-lookup"><span data-stu-id="17f3c-130">If other developers use your code, you should provide guidelines about how their code should react if new elements are added to any `enum` types.</span></span>

## <a name="example"></a><span data-ttu-id="17f3c-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="17f3c-131">Example</span></span>

<span data-ttu-id="17f3c-132">No exemplo a seguir, uma enumeração, `Day`, é declarada.</span><span class="sxs-lookup"><span data-stu-id="17f3c-132">In the following example, an enumeration, `Day`, is declared.</span></span> <span data-ttu-id="17f3c-133">Dois enumeradores são convertidos explicitamente em inteiros e atribuídos a variáveis de inteiro.</span><span class="sxs-lookup"><span data-stu-id="17f3c-133">Two enumerators are explicitly converted to integer and assigned to integer variables.</span></span>

[!code-csharp[csrefKeywordsTypes#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#10)]

## <a name="example"></a><span data-ttu-id="17f3c-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="17f3c-134">Example</span></span>

<span data-ttu-id="17f3c-135">No exemplo a seguir, a opção de tipo base é usada para declarar uma `enum` cujos membros são do tipo `long`.</span><span class="sxs-lookup"><span data-stu-id="17f3c-135">In the following example, the base-type option is used to declare an `enum` whose members are of type `long`.</span></span> <span data-ttu-id="17f3c-136">Observe que, mesmo que o tipo subjacente da enumeração seja `long`, os membros da enumeração ainda devem ser convertidos explicitamente no tipo `long` usando uma conversão.</span><span class="sxs-lookup"><span data-stu-id="17f3c-136">Notice that even though the underlying type of the enumeration is `long`, the enumeration members still must be explicitly converted to type `long` by using a cast.</span></span>

[!code-csharp[csrefKeywordsTypes#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#11)]

## <a name="example"></a><span data-ttu-id="17f3c-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="17f3c-137">Example</span></span>

<span data-ttu-id="17f3c-138">O exemplo de código a seguir ilustra o uso e o efeito do atributo <xref:System.FlagsAttribute?displayProperty=nameWithType> em uma declaração `enum`.</span><span class="sxs-lookup"><span data-stu-id="17f3c-138">The following code example illustrates the use and effect of the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute on an `enum` declaration.</span></span>

[!code-csharp[csrefKeywordsTypes#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#12)]

## <a name="comments"></a><span data-ttu-id="17f3c-139">Comentários</span><span class="sxs-lookup"><span data-stu-id="17f3c-139">Comments</span></span>

<span data-ttu-id="17f3c-140">Se você remover `Flags`, o exemplo exibirá os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="17f3c-140">If you remove `Flags`, the example displays the following values:</span></span>

`5`

`5`

## <a name="c-language-specification"></a><span data-ttu-id="17f3c-141">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="17f3c-141">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="17f3c-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="17f3c-142">See also</span></span>

- [<span data-ttu-id="17f3c-143">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="17f3c-143">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="17f3c-144">Tipos de enumeração</span><span class="sxs-lookup"><span data-stu-id="17f3c-144">Enumeration Types</span></span>](../../programming-guide/enumeration-types.md)
- [<span data-ttu-id="17f3c-145">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="17f3c-145">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="17f3c-146">Tipos integrais</span><span class="sxs-lookup"><span data-stu-id="17f3c-146">Integral types</span></span>](../builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="17f3c-147">Tabela de tipos internos</span><span class="sxs-lookup"><span data-stu-id="17f3c-147">Built-In Types Table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="17f3c-148">Convenções de Nomenclatura do Enum</span><span class="sxs-lookup"><span data-stu-id="17f3c-148">Enum Naming Conventions</span></span>](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
