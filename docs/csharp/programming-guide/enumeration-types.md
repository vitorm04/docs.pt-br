---
title: Tipos de enumeração – Guia de Programação em C#
ms.custom: seodec18
ms.date: 09/10/2017
helpviewer_keywords:
- enumerations [C#]
- enums [C#]
- C# Language, enums
- bit flags [C#]
ms.assetid: 64a9b731-9e3c-4336-8a09-018db2aa10b7
ms.openlocfilehash: 7c40e16e9c495c5e69dcdd74c3698d51b0d49785
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240054"
---
# <a name="enumeration-types-c-programming-guide"></a><span data-ttu-id="1c0ba-102">Tipos de enumeração (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="1c0ba-102">Enumeration types (C# Programming Guide)</span></span>

<span data-ttu-id="1c0ba-103">Um tipo de enumeração (também chamado de uma enumeração ou enum) fornece uma maneira eficiente para definir um conjunto de constantes integrais nomeadas que podem ser atribuídas a um valor.</span><span class="sxs-lookup"><span data-stu-id="1c0ba-103">An enumeration type (also named an enumeration or an enum) provides an efficient way to define a set of named integral constants that may be assigned to a variable.</span></span> <span data-ttu-id="1c0ba-104">Por exemplo, suponha que você precisa definir uma variável cujo valor representará um dia da semana.</span><span class="sxs-lookup"><span data-stu-id="1c0ba-104">For example, assume that you have to define a variable whose value will represent a day of the week.</span></span> <span data-ttu-id="1c0ba-105">Há apenas sete valores significativos que essa variável armazenará.</span><span class="sxs-lookup"><span data-stu-id="1c0ba-105">There are only seven meaningful values which that variable will ever store.</span></span> <span data-ttu-id="1c0ba-106">Para definir esses valores, você pode usar um tipo de enumeração, que é declarado usando a palavra-chave [enum](../../csharp/language-reference/keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="1c0ba-106">To define those values, you can use an enumeration type, which is declared by using the [enum](../../csharp/language-reference/keywords/enum.md) keyword.</span></span>

[!code-csharp[csProgGuideEnums#1](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#1)]

<span data-ttu-id="1c0ba-107">Por padrão o tipo subjacente de cada elemento na enumeração é [int](../../csharp/language-reference/keywords/int.md). Você pode especificar outro tipo numérico integral usando dois-pontos, como mostrado no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="1c0ba-107">By default the underlying type of each element in the enum is [int](../../csharp/language-reference/keywords/int.md). You can specify another integral numeric type by using a colon, as shown in the previous example.</span></span> <span data-ttu-id="1c0ba-108">Para obter uma lista completa dos tipos possíveis, consulte [enum (Referência de C#)](../../csharp/language-reference/keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="1c0ba-108">For a full list of possible types, see [enum (C# Reference)](../../csharp/language-reference/keywords/enum.md).</span></span>

<span data-ttu-id="1c0ba-109">Você pode verificar os valores numéricos subjacentes com a conversão em tipo subjacente, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="1c0ba-109">You can verify the underlying numeric values by casting  to the underlying type, as the following example shows.</span></span>

```csharp
Day today = Day.Monday;
int dayNumber =(int)today;
Console.WriteLine("{0} is day number #{1}.", today, dayNumber);

Month thisMonth = Month.Dec;
byte monthNumber = (byte)thisMonth;
Console.WriteLine("{0} is month number #{1}.", thisMonth, monthNumber);

// Output:
// Monday is day number #1.
// Dec is month number #11.
```

<span data-ttu-id="1c0ba-110">A seguir estão as vantagens de usar uma enumeração, em vez de um tipo numérico:</span><span class="sxs-lookup"><span data-stu-id="1c0ba-110">The following are advantages of using an enum instead of a numeric type:</span></span>

- <span data-ttu-id="1c0ba-111">Você especifica claramente para o código do cliente quais valores são válidos para a variável.</span><span class="sxs-lookup"><span data-stu-id="1c0ba-111">You clearly specify for client code which values are valid for the variable.</span></span>

- <span data-ttu-id="1c0ba-112">No Visual Studio, o IntelliSense lista os valores definidos.</span><span class="sxs-lookup"><span data-stu-id="1c0ba-112">In Visual Studio, IntelliSense lists the defined values.</span></span>

<span data-ttu-id="1c0ba-113">Quando você não especifica valores para os elementos na lista de enumerador, os valores são automaticamente incrementados em 1.</span><span class="sxs-lookup"><span data-stu-id="1c0ba-113">When you do not specify values for the elements in the enumerator list, the values are automatically incremented by 1.</span></span> <span data-ttu-id="1c0ba-114">No exemplo anterior, `Day.Sunday` tem um valor de 0, `Day.Monday` tem um valor de 1 e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="1c0ba-114">In the previous example, `Day.Sunday` has a value of 0, `Day.Monday` has a value of 1, and so on.</span></span> <span data-ttu-id="1c0ba-115">Ao criar um novo objeto `Day`, ele terá um valor padrão de `Day.Sunday` (0) se você não atribuir explicitamente um valor a ele.</span><span class="sxs-lookup"><span data-stu-id="1c0ba-115">When you create a new `Day` object, it will have a default value of `Day.Sunday` (0) if you do not explicitly assign it a value.</span></span> <span data-ttu-id="1c0ba-116">Quando você criar uma enumeração, selecione o valor padrão mais lógico e forneça a ele um valor igual a zero.</span><span class="sxs-lookup"><span data-stu-id="1c0ba-116">When you create an enum, select the most logical default value and give it a value of zero.</span></span> <span data-ttu-id="1c0ba-117">Isso fará com que todos os enumeradores tenham esse valor padrão se eles não tiverem um valor explicitamente atribuído quando forem criados.</span><span class="sxs-lookup"><span data-stu-id="1c0ba-117">That will cause all enums to have that default value if they are not explicitly assigned a value when they are created.</span></span>

<span data-ttu-id="1c0ba-118">Se a variável `meetingDay` for do tipo `Day`, (sem uma conversão explícita) você pode apenas atribuir a ele um dos valores definidos por `Day`.</span><span class="sxs-lookup"><span data-stu-id="1c0ba-118">If the variable `meetingDay` is of type `Day`, then (without an explicit cast) you can only assign it one of the values defined by `Day`.</span></span> <span data-ttu-id="1c0ba-119">E se o dia da reunião for alterado, você poderá atribuir um novo valor de `Day` para `meetingDay`:</span><span class="sxs-lookup"><span data-stu-id="1c0ba-119">And if the meeting day changes, you can assign a new value from `Day` to `meetingDay`:</span></span>

[!code-csharp[csProgGuideEnums#4](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#4)]

> [!NOTE]
> <span data-ttu-id="1c0ba-120">É possível atribuir qualquer valor inteiro arbitrário a `meetingDay`.</span><span class="sxs-lookup"><span data-stu-id="1c0ba-120">It's possible to assign any arbitrary integer value to `meetingDay`.</span></span> <span data-ttu-id="1c0ba-121">Por exemplo, esta linha de código não produz um erro: `meetingDay = (Day) 42`.</span><span class="sxs-lookup"><span data-stu-id="1c0ba-121">For example, this line of code does not produce an error: `meetingDay = (Day) 42`.</span></span> <span data-ttu-id="1c0ba-122">No entanto, você não deve fazer isso porque a expectativa implícita é que uma variável enum conterá apenas um dos valores definidos pela enumeração.</span><span class="sxs-lookup"><span data-stu-id="1c0ba-122">However, you should not do this because the implicit expectation is that an enum variable will only hold one of the values defined by the enum.</span></span> <span data-ttu-id="1c0ba-123">Atribuir um valor arbitrário a uma variável de um tipo de enumeração é introduzir um alto risco de erros.</span><span class="sxs-lookup"><span data-stu-id="1c0ba-123">To assign an arbitrary value to a variable of an enumeration type is to introduce a high risk for errors.</span></span>

<span data-ttu-id="1c0ba-124">Você pode atribuir quaisquer valores aos elementos na lista de enumeradores de um tipo de enumeração e também pode usar valores computados:</span><span class="sxs-lookup"><span data-stu-id="1c0ba-124">You can assign any values to the elements in the enumerator list of an enumeration type, and you can also use computed values:</span></span>

[!code-csharp[csProgGuideEnums#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#3)]

## <a name="enumeration-types-as-bit-flags"></a><span data-ttu-id="1c0ba-125">Tipos de Enumeração como Sinalizadores de Bit</span><span class="sxs-lookup"><span data-stu-id="1c0ba-125">Enumeration types as bit flags</span></span>

<span data-ttu-id="1c0ba-126">Você pode usar um tipo de enumeração para definir sinalizadores de bits, que permite que uma instância do tipo de enumeração armazenar qualquer combinação dos valores que são definidos na lista de enumeradores.</span><span class="sxs-lookup"><span data-stu-id="1c0ba-126">You can use an enumeration type to define bit flags, which enables an instance of the enumeration type to store any combination of the values that are defined in the enumerator list.</span></span> <span data-ttu-id="1c0ba-127">(Claro, algumas combinações podem não ser significativas ou permitidas em seu código de programa.)</span><span class="sxs-lookup"><span data-stu-id="1c0ba-127">(Of course, some combinations may not be meaningful or allowed in your program code.)</span></span>

<span data-ttu-id="1c0ba-128">Crie uma enumeração de sinalizadores de bits aplicando o atributo <xref:System.FlagsAttribute?displayProperty=nameWithType> e definindo os valores apropriadamente para que operações bit a bit `AND`, `OR`, `NOT` e `XOR` possam ser executadas neles.</span><span class="sxs-lookup"><span data-stu-id="1c0ba-128">You create a bit flags enum by applying the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute and defining the values appropriately so that `AND`, `OR`, `NOT` and `XOR` bitwise operations can be performed on them.</span></span> <span data-ttu-id="1c0ba-129">Em uma enumeração de sinalizadores de bits, inclua uma constante nomeada com um valor de zero que significa “nenhum sinalizador está definido”.</span><span class="sxs-lookup"><span data-stu-id="1c0ba-129">In a bit flags enum, include a named constant with a value of zero that means "no flags are set."</span></span> <span data-ttu-id="1c0ba-130">Não forneça um valor de zero a um sinalizador se isso não significar “nenhum sinalizador está definido”.</span><span class="sxs-lookup"><span data-stu-id="1c0ba-130">Do not give a flag a value of zero if it does not mean "no flags are set".</span></span>

<span data-ttu-id="1c0ba-131">No exemplo a seguir, outra versão da enumeração `Day`, que é chamada de `Days`, é definida.</span><span class="sxs-lookup"><span data-stu-id="1c0ba-131">In the following example, another version of the `Day` enum, which is named `Days`, is defined.</span></span> <span data-ttu-id="1c0ba-132">`Days` tem o atributo `Flags` e a cada valor é atribuída a próxima maior potência de 2.</span><span class="sxs-lookup"><span data-stu-id="1c0ba-132">`Days` has the `Flags` attribute, and each value is assigned the next greater power of 2.</span></span> <span data-ttu-id="1c0ba-133">Isso permite que você crie uma variável `Days` cujo valor é `Days.Tuesday | Days.Thursday`.</span><span class="sxs-lookup"><span data-stu-id="1c0ba-133">This enables you to create a `Days` variable whose value is `Days.Tuesday | Days.Thursday`.</span></span>

[!code-csharp[csProgGuideEnums#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#2)]

<span data-ttu-id="1c0ba-134">Para definir um sinalizador em uma enumeração, use o operador `OR` de bit a bit mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="1c0ba-134">To set a flag on an enum, use the bitwise `OR` operator as shown in the following example:</span></span>

[!code-csharp[csProgGuideEnums#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#6)]

<span data-ttu-id="1c0ba-135">Para determinar se um sinalizador específico é definido, use uma operação `AND` bit a bit, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="1c0ba-135">To determine whether a specific flag is set, use a bitwise `AND` operation, as shown in the following example:</span></span>

[!code-csharp[csProgGuideEnums#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#7)]

<span data-ttu-id="1c0ba-136">Para saber mais sobre o que considerar ao definir tipos de enumeração com o atributo <xref:System.FlagsAttribute?displayProperty=nameWithType>, veja <xref:System.Enum?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1c0ba-136">For more information about what to consider when you define enumeration types with the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute, see <xref:System.Enum?displayProperty=nameWithType>.</span></span>

## <a name="using-the-systemenum-methods-to-discover-and-manipulate-enum-values"></a><span data-ttu-id="1c0ba-137">Usando os Métodos System.Enum Methods para Descobrir e Manipular Valores Enum</span><span class="sxs-lookup"><span data-stu-id="1c0ba-137">Using the System.Enum methods to discover and manipulate enum values</span></span>

<span data-ttu-id="1c0ba-138">Todas as enumerações são instâncias do tipo <xref:System.Enum?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1c0ba-138">All enums are instances of the <xref:System.Enum?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="1c0ba-139">Não é possível derivar novas classes de <xref:System.Enum?displayProperty=nameWithType>, mas você pode usar seus métodos para descobrir informações sobre e manipular valores em uma instância de enumeração.</span><span class="sxs-lookup"><span data-stu-id="1c0ba-139">You cannot derive new classes from <xref:System.Enum?displayProperty=nameWithType>, but you can use its methods to discover information about and manipulate values in an enum instance.</span></span>

[!code-csharp[csProgGuideEnums#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#5)]

<span data-ttu-id="1c0ba-140">Para obter mais informações, consulte <xref:System.Enum?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1c0ba-140">For more information, see <xref:System.Enum?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="1c0ba-141">Você também pode criar um novo método para uma enumeração usando um método de extensão.</span><span class="sxs-lookup"><span data-stu-id="1c0ba-141">You can also create a new method for an enum by using an extension method.</span></span> <span data-ttu-id="1c0ba-142">Confira mais informações em [Como: criar um novo método para uma enumeração](../../csharp/programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="1c0ba-142">For more information, see [How to: Create a New Method for an Enumeration](../../csharp/programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1c0ba-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1c0ba-143">See Also</span></span>

- <xref:System.Enum?displayProperty=nameWithType>  
- [<span data-ttu-id="1c0ba-144">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="1c0ba-144">C# Programming Guide</span></span>](../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="1c0ba-145">enum</span><span class="sxs-lookup"><span data-stu-id="1c0ba-145">enum</span></span>](../../csharp/language-reference/keywords/enum.md)
