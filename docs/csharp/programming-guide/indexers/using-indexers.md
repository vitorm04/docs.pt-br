---
title: Como usar indexadores – Guia de Programação em C#
ms.date: 07/15/2020
helpviewer_keywords:
- indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
ms.openlocfilehash: e742e4dd5ea92ec3baf37c915e024e713022b7b6
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416234"
---
# <a name="using-indexers-c-programming-guide"></a><span data-ttu-id="eb7e2-102">Usando indexadores (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="eb7e2-102">Using indexers (C# Programming Guide)</span></span>

<span data-ttu-id="eb7e2-103">Os indexadores são uma conveniência sintática que permitem que você crie uma [classe](../../language-reference/keywords/class.md), [estrutura](../../language-reference/builtin-types/struct.md)ou [interface](../../language-reference/keywords/interface.md) que os aplicativos cliente possam acessar como uma matriz.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-103">Indexers are a syntactic convenience that enable you to create a [class](../../language-reference/keywords/class.md), [struct](../../language-reference/builtin-types/struct.md), or [interface](../../language-reference/keywords/interface.md) that client applications can access as an array.</span></span> <span data-ttu-id="eb7e2-104">O compilador gerará uma `Item` Propriedade (ou uma propriedade nomeada de forma alternativa <xref:System.Runtime.CompilerServices.IndexerNameAttribute> , se estiver presente) e os métodos acessadores apropriados.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-104">The compiler will generate an `Item` property (or an alternatively named property if <xref:System.Runtime.CompilerServices.IndexerNameAttribute> is present), and the appropriate accessor methods.</span></span> <span data-ttu-id="eb7e2-105">Os indexadores são implementados em tipos cuja principal finalidade é encapsular uma coleção ou matriz interna.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-105">Indexers are most frequently implemented in types whose primary purpose is to encapsulate an internal collection or array.</span></span> <span data-ttu-id="eb7e2-106">Por exemplo, suponha que você tenha uma classe `TempRecord` que representa a temperatura em Fahrenheit, conforme registrada em 10 horas diferentes durante um período de 24 horas.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-106">For example, suppose you have a class `TempRecord` that represents the temperature in Fahrenheit as recorded at 10 different times during a 24-hour period.</span></span> <span data-ttu-id="eb7e2-107">A classe contém uma `temps` matriz do tipo `float[]` para armazenar os valores de temperatura.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-107">The class contains a `temps` array of type `float[]` to store the temperature values.</span></span> <span data-ttu-id="eb7e2-108">Ao implementar um indexador nessa classe, os clientes podem acessar as temperaturas em uma instância `TempRecord` como `float temp = tempRecord[4]`, e não como `float temp = tempRecord.temps[4]`.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-108">By implementing an indexer in this class, clients can access the temperatures in a `TempRecord` instance as `float temp = tempRecord[4]` instead of as `float temp = tempRecord.temps[4]`.</span></span> <span data-ttu-id="eb7e2-109">A notação do indexador não apenas simplifica a sintaxe para aplicativos cliente; Ele também torna a classe e sua finalidade mais intuitiva para que outros desenvolvedores entendam.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-109">The indexer notation not only simplifies the syntax for client applications; it also makes the class, and its purpose more intuitive for other developers to understand.</span></span>

<span data-ttu-id="eb7e2-110">Para declarar um indexador em uma classe ou struct, use a palavra-chave [this](../../language-reference/keywords/this.md), como mostra o seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="eb7e2-110">To declare an indexer on a class or struct, use the [this](../../language-reference/keywords/this.md) keyword, as the following example shows:</span></span>

```csharp
// Indexer declaration
public int this[int index]
{
    // get and set accessors
}
```

> [!IMPORTANT]
> <span data-ttu-id="eb7e2-111">A declaração de um indexador irá gerar automaticamente uma propriedade chamada `Item` no objeto.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-111">Declaring an indexer will automatically generate a property named `Item` on the object.</span></span> <span data-ttu-id="eb7e2-112">A `Item` propriedade não pode ser acessada diretamente da [expressão de acesso de membro](../../language-reference/operators/member-access-operators.md#member-access-expression-)de instância.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-112">The `Item` property is not directly accessible from the instance [member access expression](../../language-reference/operators/member-access-operators.md#member-access-expression-).</span></span> <span data-ttu-id="eb7e2-113">Além disso, se você adicionar sua própria `Item` Propriedade a um objeto com um indexador, obterá um [erro do compilador CS0102](../../misc/cs0102.md).</span><span class="sxs-lookup"><span data-stu-id="eb7e2-113">Additionally, if you add your own `Item` property to an object with an indexer, you'll get a [CS0102 compiler error](../../misc/cs0102.md).</span></span> <span data-ttu-id="eb7e2-114">Para evitar esse erro, use <xref:System.Runtime.CompilerServices.IndexerNameAttribute> renomear o indexador conforme detalhado abaixo.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-114">To avoid this error, use the <xref:System.Runtime.CompilerServices.IndexerNameAttribute> rename the indexer as detailed below.</span></span>

## <a name="remarks"></a><span data-ttu-id="eb7e2-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="eb7e2-115">Remarks</span></span>

<span data-ttu-id="eb7e2-116">O tipo de um indexador e o tipo dos seus parâmetros devem ser pelo menos tão acessíveis quanto o próprio indexador.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-116">The type of an indexer and the type of its parameters must be at least as accessible as the indexer itself.</span></span> <span data-ttu-id="eb7e2-117">Para obter mais informações sobre níveis de acessibilidade, consulte [Modificadores de acesso](../../language-reference/keywords/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="eb7e2-117">For more information about accessibility levels, see [Access Modifiers](../../language-reference/keywords/access-modifiers.md).</span></span>

<span data-ttu-id="eb7e2-118">Para obter mais informações sobre como usar indexadores com uma interface, consulte [Indexadores de Interface](./indexers-in-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="eb7e2-118">For more information about how to use indexers with an interface, see [Interface Indexers](./indexers-in-interfaces.md).</span></span>

<span data-ttu-id="eb7e2-119">A assinatura de um indexador consiste do número e dos tipos de seus parâmetros formais.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-119">The signature of an indexer consists of the number and types of its formal parameters.</span></span> <span data-ttu-id="eb7e2-120">Ela não inclui o tipo de indexador nem os nomes dos parâmetros formais.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-120">It doesn't include the indexer type or the names of the formal parameters.</span></span> <span data-ttu-id="eb7e2-121">Se você declarar mais de um indexador na mesma classe, eles terão diferentes assinaturas.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-121">If you declare more than one indexer in the same class, they must have different signatures.</span></span>

<span data-ttu-id="eb7e2-122">Um valor de indexador não é classificado como uma variável; portanto, não é possível passar um valor de indexador como um parâmetro [ref](../../language-reference/keywords/ref.md) ou [out](../../language-reference/keywords/out-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="eb7e2-122">An indexer value is not classified as a variable; therefore, you cannot pass an indexer value as a [ref](../../language-reference/keywords/ref.md) or [out](../../language-reference/keywords/out-parameter-modifier.md) parameter.</span></span>

<span data-ttu-id="eb7e2-123">Para fornecer o indexador com um nome que outras linguagens possam usar, use <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>, como mostra o seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="eb7e2-123">To provide the indexer with a name that other languages can use, use <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType>, as the following example shows:</span></span>

```csharp
// Indexer declaration
[System.Runtime.CompilerServices.IndexerName("TheItem")]
public int this[int index]
{
    // get and set accessors
}
```

<span data-ttu-id="eb7e2-124">Esse indexador terá o nome `TheItem` , pois ele é substituído pelo atributo de nome do indexador.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-124">This indexer will have the name `TheItem`, as it is overridden by the indexer name attribute.</span></span> <span data-ttu-id="eb7e2-125">Por padrão, o nome do indexador é `Item` .</span><span class="sxs-lookup"><span data-stu-id="eb7e2-125">By default, the indexer name is `Item`.</span></span>

## <a name="example-1"></a><span data-ttu-id="eb7e2-126">Exemplo 1</span><span class="sxs-lookup"><span data-stu-id="eb7e2-126">Example 1</span></span>

<span data-ttu-id="eb7e2-127">O exemplo a seguir mostra como declarar um campo de matriz privada, `temps` e um indexador.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-127">The following example shows how to declare a private array field, `temps`, and an indexer.</span></span> <span data-ttu-id="eb7e2-128">O indexador permite acesso direto à instância `tempRecord[i]`.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-128">The indexer enables direct access to the instance `tempRecord[i]`.</span></span> <span data-ttu-id="eb7e2-129">A alternativa ao uso do indexador é declarar a matriz como um membro [público](../../language-reference/keywords/public.md) e acessar seus membros, `tempRecord.temps[i]`, diretamente.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-129">The alternative to using the indexer is to declare the array as a [public](../../language-reference/keywords/public.md) member and access its members, `tempRecord.temps[i]`, directly.</span></span>

:::code language="csharp" source="snippets/Temperatures/TempRecord.cs":::

<span data-ttu-id="eb7e2-130">Observe que, quando o acesso de um indexador é avaliado, por exemplo, em uma instrução `Console.Write`, o acessador [get](../../language-reference/keywords/get.md) é invocado.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-130">Notice that when an indexer's access is evaluated, for example, in a `Console.Write` statement, the [get](../../language-reference/keywords/get.md) accessor is invoked.</span></span> <span data-ttu-id="eb7e2-131">Portanto, se não existir nenhum acessador `get`, ocorrerá um erro em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-131">Therefore, if no `get` accessor exists, a compile-time error occurs.</span></span>

:::code language="csharp" source="snippets/Temperatures/Program.cs":::

## <a name="indexing-using-other-values"></a><span data-ttu-id="eb7e2-132">Indexando usando outros valores</span><span class="sxs-lookup"><span data-stu-id="eb7e2-132">Indexing using other values</span></span>

<span data-ttu-id="eb7e2-133">O C# não limita o tipo de parâmetro do indexador ao inteiro.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-133">C# doesn't limit the indexer parameter type to integer.</span></span> <span data-ttu-id="eb7e2-134">Por exemplo, talvez seja útil usar uma cadeia de caracteres com um indexador.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-134">For example, it may be useful to use a string with an indexer.</span></span> <span data-ttu-id="eb7e2-135">Esse indexador pode ser implementado pesquisando a cadeia de caracteres na coleção e retornando o valor adequado.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-135">Such an indexer might be implemented by searching for the string in the collection, and returning the appropriate value.</span></span> <span data-ttu-id="eb7e2-136">Como os acessadores podem ser sobrecarregados, as versões de cadeia de caracteres e inteiros podem coexistir.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-136">As accessors can be overloaded, the string and integer versions can coexist.</span></span>

## <a name="example-2"></a><span data-ttu-id="eb7e2-137">Exemplo 2</span><span class="sxs-lookup"><span data-stu-id="eb7e2-137">Example 2</span></span>

<span data-ttu-id="eb7e2-138">O exemplo a seguir declara uma classe que armazena os dias da semana.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-138">The following example declares a class that stores the days of the week.</span></span> <span data-ttu-id="eb7e2-139">Um acessador `get` aceita uma cadeia de caracteres, o nome de um dia e retorna o inteiro correspondente.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-139">A `get` accessor takes a string, the name of a day, and returns the corresponding integer.</span></span> <span data-ttu-id="eb7e2-140">Por exemplo, "Sunday" retorna 0, "Monday" retorna 1 e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-140">For example, "Sunday" returns 0, "Monday" returns 1, and so on.</span></span>

:::code language="csharp" source="snippets/StringIndexers/DayCollection.cs":::

### <a name="consuming-example-2"></a><span data-ttu-id="eb7e2-141">Exemplo de consumo 2</span><span class="sxs-lookup"><span data-stu-id="eb7e2-141">Consuming example 2</span></span>

:::code language="csharp" source="snippets/StringIndexers/Program.cs":::

## <a name="example-3"></a><span data-ttu-id="eb7e2-142">Exemplo 3</span><span class="sxs-lookup"><span data-stu-id="eb7e2-142">Example 3</span></span>

<span data-ttu-id="eb7e2-143">O exemplo a seguir declara uma classe que armazena os dias da semana usando a <xref:System.DayOfWeek?displayProperty=fullName> enumeração.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-143">The following example declares a class that stores the days of the week using the <xref:System.DayOfWeek?displayProperty=fullName> enum.</span></span> <span data-ttu-id="eb7e2-144">Um `get` acessador pega um `DayOfWeek` , o valor de um dia e retorna o inteiro correspondente.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-144">A `get` accessor takes a `DayOfWeek`, the value of a day, and returns the corresponding integer.</span></span> <span data-ttu-id="eb7e2-145">Por exemplo, `DayOfWeek.Sunday` retorna 0, `DayOfWeek.Monday` retorna 1 e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-145">For example, `DayOfWeek.Sunday` returns 0, `DayOfWeek.Monday` returns 1, and so on.</span></span>

:::code language="csharp" source="snippets/DayOfWeekIndexers/DayOfWeekCollection.cs":::

### <a name="consuming-example-3"></a><span data-ttu-id="eb7e2-146">Exemplo de consumo 3</span><span class="sxs-lookup"><span data-stu-id="eb7e2-146">Consuming example 3</span></span>

:::code language="csharp" source="snippets/DayOfWeekIndexers/Program.cs":::

## <a name="robust-programming"></a><span data-ttu-id="eb7e2-147">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="eb7e2-147">Robust programming</span></span>

<span data-ttu-id="eb7e2-148">Há duas maneiras principais nas quais a segurança e a confiabilidade de indexadores podem ser melhoradas:</span><span class="sxs-lookup"><span data-stu-id="eb7e2-148">There are two main ways in which the security and reliability of indexers can be improved:</span></span>

- <span data-ttu-id="eb7e2-149">Certifique-se de incorporar algum tipo de estratégia de tratamento de erros para manipular a chance de passagem de código cliente em um valor de índice inválido.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-149">Be sure to incorporate some type of error-handling strategy to handle the chance of client code passing in an invalid index value.</span></span> <span data-ttu-id="eb7e2-150">Anteriormente, no primeiro exemplo neste tópico, a classe TempRecord oferece uma propriedade Length que permite que o código cliente verifique a saída antes de passá-la para o indexador.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-150">In the first example earlier in this topic, the TempRecord class provides a Length property that enables the client code to verify the input before passing it to the indexer.</span></span> <span data-ttu-id="eb7e2-151">Também é possível colocador o código de tratamento de erro dentro do próprio indexador.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-151">You can also put the error handling code inside the indexer itself.</span></span> <span data-ttu-id="eb7e2-152">Certifique-se documentar para os usuários as exceções que você gera dentro de um acessador do indexador.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-152">Be sure to document for users any exceptions that you throw inside an indexer accessor.</span></span>

- <span data-ttu-id="eb7e2-153">Defina a acessibilidade dos acessadores [get](../../language-reference/keywords/get.md) e [set](../../language-reference/keywords/set.md) para que ela seja mais restritiva possível.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-153">Set the accessibility of the [get](../../language-reference/keywords/get.md) and [set](../../language-reference/keywords/set.md) accessors to be as restrictive as is reasonable.</span></span> <span data-ttu-id="eb7e2-154">Isso é importante para o acessador `set` em particular.</span><span class="sxs-lookup"><span data-stu-id="eb7e2-154">This is important for the `set` accessor in particular.</span></span> <span data-ttu-id="eb7e2-155">Para obter mais informações, consulte [Restringindo a acessibilidade aos acessadores](../classes-and-structs/restricting-accessor-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="eb7e2-155">For more information, see [Restricting Accessor Accessibility](../classes-and-structs/restricting-accessor-accessibility.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="eb7e2-156">Confira também</span><span class="sxs-lookup"><span data-stu-id="eb7e2-156">See also</span></span>

- [<span data-ttu-id="eb7e2-157">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="eb7e2-157">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="eb7e2-158">Indexadores</span><span class="sxs-lookup"><span data-stu-id="eb7e2-158">Indexers</span></span>](./index.md)
- [<span data-ttu-id="eb7e2-159">Propriedades</span><span class="sxs-lookup"><span data-stu-id="eb7e2-159">Properties</span></span>](../classes-and-structs/properties.md)
