---
title: Tuplas no Visual Basic
ms.custom: 
ms.date: 04/23/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- tuples [Visual Basic]
ms.assetid: 3e66cd1b-3432-4e1d-8c37-5ebacae8f53f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2653b9dc8a6ecbcb718c20be8bd6275edf4cfb6e
ms.sourcegitcommit: be1fb5d9447ad459bef22b91a91c72e3e0b2d916
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2018
---
# <a name="tuples-visual-basic"></a><span data-ttu-id="11e5c-102">Tuplas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11e5c-102">Tuples (Visual Basic)</span></span>

<span data-ttu-id="11e5c-103">A partir do Visual Basic de 2017, a linguagem Visual Basic oferece suporte interno para tuplas que faz com que criar tuplas e acessar os elementos de tuplas mais fácil.</span><span class="sxs-lookup"><span data-stu-id="11e5c-103">Starting with Visual Basic 2017, the Visual Basic language offers built-in support for tuples that makes creating tuples and accessing the elements of tuples easier.</span></span> <span data-ttu-id="11e5c-104">Uma tupla é uma estrutura de dados leve que tem um número específico e a sequência de valores.</span><span class="sxs-lookup"><span data-stu-id="11e5c-104">A tuple is a light-weight data structure that has a specific number and sequence of values.</span></span> <span data-ttu-id="11e5c-105">Quando você cria uma instância de coleção de itens, você deve definir o número e o tipo de dados de cada valor (ou elemento).</span><span class="sxs-lookup"><span data-stu-id="11e5c-105">When you instantiate the tuple, you define the number and the data type of each value (or element).</span></span> <span data-ttu-id="11e5c-106">Por exemplo, uma tupla de 2 (ou par) tem dois elementos.</span><span class="sxs-lookup"><span data-stu-id="11e5c-106">For example, a 2-tuple (or pair) has two elements.</span></span> <span data-ttu-id="11e5c-107">O primeiro pode ser um `Boolean` de valor, enquanto o segundo é um `String`.</span><span class="sxs-lookup"><span data-stu-id="11e5c-107">The first might be a `Boolean` value, while the second is a `String`.</span></span> <span data-ttu-id="11e5c-108">Porque tuplas facilitam armazenar vários valores em um único objeto, eles geralmente são usados como uma maneira simples de retornar vários valores de um método.</span><span class="sxs-lookup"><span data-stu-id="11e5c-108">Because tuples make it easy to store multiple values in a single object, they are often used as a lightweight way to return multiple values from a method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="11e5c-109">Suporte de tupla requer o <xref:System.ValueTuple> tipo.</span><span class="sxs-lookup"><span data-stu-id="11e5c-109">Tuple support requires the <xref:System.ValueTuple> type.</span></span> <span data-ttu-id="11e5c-110">Se o .NET Framework 4.7 não estiver instalado, você deve adicionar o pacote NuGet `System.ValueTuple`, que está disponível na Galeria do NuGet.</span><span class="sxs-lookup"><span data-stu-id="11e5c-110">If the .NET Framework 4.7 is not installed, you must add the NuGet package `System.ValueTuple`, which is available on the NuGet Gallery.</span></span> <span data-ttu-id="11e5c-111">Sem esse pacote, você pode receber um erro de compilação semelhante a "Tipo predefinido 'ValueTuple(Of,,,)' não está definido ou importado."</span><span class="sxs-lookup"><span data-stu-id="11e5c-111">Without this package, you may get a compilation error similar to, "Predefined type 'ValueTuple(Of,,,)' is not defined or imported."</span></span>

## <a name="instantiating-and-using-a-tuple"></a><span data-ttu-id="11e5c-112">Criando e usando uma tupla</span><span class="sxs-lookup"><span data-stu-id="11e5c-112">Instantiating and using a tuple</span></span>

<span data-ttu-id="11e5c-113">Você pode instanciar uma tupla colocando os parênteses de im valores delimitados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="11e5c-113">You instantiate a tuple by enclosing its comma-delimited values im parentheses.</span></span> <span data-ttu-id="11e5c-114">Cada um desses valores, em seguida, torna-se um campo da tupla.</span><span class="sxs-lookup"><span data-stu-id="11e5c-114">Each of those values then becomes a field of the tuple.</span></span> <span data-ttu-id="11e5c-115">Por exemplo, o código a seguir define um triplo (ou uma tupla de 3) com um `Date` como o primeiro valor, um `String` como seu segundo e um `Boolean` como seu terceiro.</span><span class="sxs-lookup"><span data-stu-id="11e5c-115">For example, the following code defines a triple (or 3-tuple) with a `Date` as its first value, a `String` as its second, and a `Boolean` as its third.</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#1)]

<span data-ttu-id="11e5c-116">Por padrão, o nome de cada campo em uma tupla consiste da cadeia de caracteres `Item` juntamente com base em uma posição na tupla.</span><span class="sxs-lookup"><span data-stu-id="11e5c-116">By default, the name of each field in a tuple consists of the string `Item` along with the field's one-based position in the tuple.</span></span> <span data-ttu-id="11e5c-117">Para essa tupla de 3, o `Date` campo é `Item1`, o `String` campo é `Item2`e o `Boolean` campo é `Item3`.</span><span class="sxs-lookup"><span data-stu-id="11e5c-117">For this 3-tuple, the `Date` field is `Item1`, the `String` field is `Item2`, and the `Boolean` field is `Item3`.</span></span> <span data-ttu-id="11e5c-118">O exemplo a seguir exibe os valores dos campos da tupla instanciado na linha de código anterior</span><span class="sxs-lookup"><span data-stu-id="11e5c-118">The following example displays the values of fields of the tuple instantiated in the previous line of code</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#2)]

<span data-ttu-id="11e5c-119">Os campos de uma tupla de Visual Basic são de leitura-gravação; Depois de instanciar uma tupla, você pode modificar seus valores.</span><span class="sxs-lookup"><span data-stu-id="11e5c-119">The fields of a Visual Basic tuple are read-write; after you've instantiated a tuple, you can modify its values.</span></span> <span data-ttu-id="11e5c-120">O exemplo a seguir modifica duas os três campos da tupla criado no exemplo anterior e exibe o resultado.</span><span class="sxs-lookup"><span data-stu-id="11e5c-120">The following example modifies two of the three fields of the tuple created in the previous example and displays the result.</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#3)]

## <a name="instantiating-and-using-a-named-tuple"></a><span data-ttu-id="11e5c-121">Criando e usando uma tupla nomeada</span><span class="sxs-lookup"><span data-stu-id="11e5c-121">Instantiating and using a named tuple</span></span>

<span data-ttu-id="11e5c-122">Em vez de usar os nomes padrão para campos de uma tupla, você pode instanciar uma *chamado tupla* atribuindo seus próprios nomes de elementos da tupla.</span><span class="sxs-lookup"><span data-stu-id="11e5c-122">Rather than using default names for a tuple's fields, you can instantiate a *named tuple* by assigning your own names to the tuple's elements.</span></span> <span data-ttu-id="11e5c-123">Os campos da tupla possam ser acessados pelos nomes atribuídos *ou* por seus nomes padrão.</span><span class="sxs-lookup"><span data-stu-id="11e5c-123">The tuple's fields can then be accessed by their assigned names *or* by their default names.</span></span> <span data-ttu-id="11e5c-124">O exemplo a seguir cria a mesmo tupla de 3 como anteriormente, exceto que ele explicitamente nomeia o primeiro campo `EventDate`, a segunda `Name`e o terceiro `IsHoliday`.</span><span class="sxs-lookup"><span data-stu-id="11e5c-124">The following example instantiates the same 3-tuple as previously, except that it explicitly names the first field `EventDate`, the second `Name`, and the third `IsHoliday`.</span></span> <span data-ttu-id="11e5c-125">Em seguida, exibe os valores de campo, modifica e exibe os valores de campo novamente.</span><span class="sxs-lookup"><span data-stu-id="11e5c-125">It then displays the field values, modifies them, and displays the field values again.</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#4)]

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="11e5c-126">Nomes de elemento de tupla deduzido</span><span class="sxs-lookup"><span data-stu-id="11e5c-126">Inferred tuple element names</span></span>

<span data-ttu-id="11e5c-127">Começando com 15,3 do Visual Basic, Visual Basic pode deduzir os nomes dos elementos de tupla; Você não precisa atribuí-las explicitamente.</span><span class="sxs-lookup"><span data-stu-id="11e5c-127">Starting with Visual Basic 15.3, Visual Basic can infer the names of tuple elements; you do not have to assign them explicitly.</span></span> <span data-ttu-id="11e5c-128">Nomes de tupla deduzidos são úteis quando você inicializar uma tupla de um conjunto de variáveis, e você deseja que o nome do elemento de tupla para ser o mesmo que o nome da variável.</span><span class="sxs-lookup"><span data-stu-id="11e5c-128">Inferred tuple names are useful when you initialize a tuple from a set of variables, and you want the tuple element name to be the same as the variable name.</span></span> 

<span data-ttu-id="11e5c-129">O exemplo a seguir cria um `stateInfo` tupla que contém três explicitamente chamado elementos, `state`, `stateName`, e `capital`.</span><span class="sxs-lookup"><span data-stu-id="11e5c-129">The following example creates a `stateInfo` tuple that contains three explicitly named elements, `state`, `stateName`, and `capital`.</span></span> <span data-ttu-id="11e5c-130">Observe que, em nomes de elementos, a instrução de inicialização de tupla simplesmente atribui os elementos nomeados os valores das variáveis com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="11e5c-130">Note that, in naming the elements, the tuple initialization statement simply assigns the named elements the values of the identically named variables.</span></span>

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#1)]
 
<span data-ttu-id="11e5c-131">Como variáveis e os elementos têm o mesmo nome, o compilador do Visual Basic pode deduzir os nomes de campos, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="11e5c-131">Because elements and variables have the same name, the Visual Basic compiler can infer the names of the fields, as the following example shows.</span></span>

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#2)]

<span data-ttu-id="11e5c-132">Para habilitar os nomes de elemento de tupla interred, você deve definir a versão do compilador do Visual Basic para usar em seu projeto do Visual Basic (\*. vbproj) arquivo:</span><span class="sxs-lookup"><span data-stu-id="11e5c-132">To enable interred tuple element names, you must define the version of the Visual Basic compiler to use in your Visual Basic project (\*.vbproj) file:</span></span> 

```xml 
<PropertyGroup> 
  <LangVersion>15.3</LangVersion> 
</PropertyGroup> 

The version number can be any version of the Visual Basic compiler starting with 15.3. Rather than hard-coding a specific compiler version, you can also specify "Latest" as the value of `LangVersion` to compile with the most recent version of the Visual Basic compiler installed on your system.

In some cases, the Visual Basic compiler cannot infer the tuple element name from the candidate name, and the tuple field can only be referenced using its default name, such as `Item1`, `Item2`, etc. These include:

- The candidate name is the same as the name of a tuple member, such as `Item3`, `Rest`, or `ToString`.

- The candidate name is duplicated in the tuple.
 
When field name inference fails, Visual Basic does not generate a compiler error, nor is an exception thrown at runtime. Instead, tuple fields must be referenced by their predefined names, such as `Item1` and `Item2`. 
  
## Tuples versus structures

A Visual Basic tuple is a value type that is an instance of one of the a **System.ValueTuple** generic types. For example, the `holiday` tuple defined in the previous example is an instance of the <xref:System.ValueTuple%603> structure. It is designed to be a lightweight container for data. Since the tuple aims to make it easy to create an object with multiple data items, it lacks some of the features that a custom structure might have. These include:

- Customer members. You cannot define your own properties, methods, or events for a tuple.

- Validation. You cannot validate the data assigned to fields.

- Immutability. Visual Basic tuples are mutable. In contrast, a custom structure allows you to control whether an instance is mutable or immutable.

If custom members, property and field validation, or immutability are important, you should use the Visual Basic [Structure](../../../language-reference/statements/structure-statement.md) statement to define a custom value type.

A Visual Basic tuple does inherit the members of its **ValueTuple** type. In addition to its fields, these include the following methods:

| Member | Description |
| ---|---|
| CompareTo | Compares the current tuple to another tuple with the same number of elements. |
| Equals | Determines whether the current tuple is equal to another tuple or object. |
| GetHashCode | Calculates the hash code for the current instance. |
| ToString | Returns the string representation of this tuple, which takes the form `(Item1, Item2...)`, where `Item1` and `Item2` represent the values of the tuple's fields. |

In addition, the **ValueTuple** types implement <xref:System.Collections.IStructuralComparable> and <xref:System.Collections.IStructuralEquatable> interfaces, which allow you to define customer comparers.

## Assignment and tuples

Visual Basic supports assignment between tuple types that have the same number of fields. The field types can be converted if one of the following is true:

- The source and target field are of the same type.

- A widening (or implicit) conversion of the source type to the target type is defined. 

- `Option Strict` is `On`, and a narrowing (or explicit) conversion of the source type to the target type is defined. This conversion can throw an exception if the source value is outside the range of the target type.

Other conversions are not considered for assignments. Let's look at the kinds of assignments that are allowed between tuple types.

Consider these variables used in the following examples:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#1)]

The first two variables, `unnamed` and `anonymous`, do not have semantic names provided for the fields. Their field names are the default `Item1` and `Item2`. The last two variables, `named` and `differentName` have semantic field names. Note that these two tuples have different names for the fields.

All four of these tuples have the same number of fields (referred to as 'arity'), and the types of those fields are identical. Therefore, all of these assignments work:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#2)]

Notice that the names of the tuples are not assigned. The values of the fields are assigned following the order of the fields in the tuple.

Finally, notice that we can assign the `named` tuple to the `conversion` tuple, even though the first field of `named` is an `Integer`, and the first field of `conversion` is a `Long`. This assignment succeeds because converting an `Integer` to a `Long` is a widening conversion.

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#3)]

Tuples with different numbers of fields are not assignable:

```vb
' Does not compile.
' VB30311: Value of type '(Integer, Integer, Integer)' cannot be converted
'          to '(Answer As Integer, Message As String)'
var differentShape = (1, 2, 3)
named = differentShape
```

## <a name="tuples-as-method-return-values"></a><span data-ttu-id="11e5c-133">Tuplas como valores retornados do método</span><span class="sxs-lookup"><span data-stu-id="11e5c-133">Tuples as method return values</span></span>

<span data-ttu-id="11e5c-134">Um método pode retornar apenas um único valor.</span><span class="sxs-lookup"><span data-stu-id="11e5c-134">A method can return only a single value.</span></span> <span data-ttu-id="11e5c-135">Com frequência, no entanto, você gostaria que uma chamada de método para retornar vários valores.</span><span class="sxs-lookup"><span data-stu-id="11e5c-135">Frequently, though, you'd like a method call to return multiple values.</span></span> <span data-ttu-id="11e5c-136">Há várias maneiras de contornar essa limitação:</span><span class="sxs-lookup"><span data-stu-id="11e5c-136">There are several ways to work around this limitation:</span></span>

- <span data-ttu-id="11e5c-137">Você pode criar uma classe personalizada ou estrutura cujas propriedades ou campos representam os valores retornados pelo método.</span><span class="sxs-lookup"><span data-stu-id="11e5c-137">You can create a custom class or structure whose properties or fields represent values returned by the method.</span></span> <span data-ttu-id="11e5c-138">Portanto, é uma solução de peso; ele requer que você defina um tipo personalizado cujo único propósito é recuperar valores de uma chamada de método.</span><span class="sxs-lookup"><span data-stu-id="11e5c-138">Thus is a heavyweight solution; it requires that you define a custom type whose only purpose is to retrieve values from a method call.</span></span>

- <span data-ttu-id="11e5c-139">Você pode retornar um único valor do método e retornar os valores restantes, passando-os por referência para o método.</span><span class="sxs-lookup"><span data-stu-id="11e5c-139">You can return a single value from the method, and return the remaining values by passing them by reference to the method.</span></span> <span data-ttu-id="11e5c-140">Isso envolve a sobrecarga de criar uma instância de uma variável e riscos sobrescrever inadvertidamente o valor da variável é passada por referência.</span><span class="sxs-lookup"><span data-stu-id="11e5c-140">This involves the overhead of instantiating a variable and risks inadvertently overwriting the value of the variable that you pass by reference.</span></span>

- <span data-ttu-id="11e5c-141">Você pode usar uma tupla, que fornece uma solução simples para recuperar vários valores de retorno.</span><span class="sxs-lookup"><span data-stu-id="11e5c-141">You can use a tuple, which provides a lightweight solution to retrieving multiple return values.</span></span>

<span data-ttu-id="11e5c-142">Por exemplo, o **TryParse** métodos de retorno de .NET um `Boolean` valor que indica se a operação de análise foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="11e5c-142">For example, the **TryParse** methods in .NET return a `Boolean` value that indicates whether the parsing operation succeeded.</span></span> <span data-ttu-id="11e5c-143">O resultado da operação de análise é retornado em uma variável passada por referência para o método.</span><span class="sxs-lookup"><span data-stu-id="11e5c-143">The result of the parsing operation is returned in a variable passed by reference to the method.</span></span> <span data-ttu-id="11e5c-144">Normalmente, uma chamada para a um método de análise, como <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> parece com o seguinte:</span><span class="sxs-lookup"><span data-stu-id="11e5c-144">Normally, a call to the a parsing method such as <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> looks like the following:</span></span>

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#1)]

<span data-ttu-id="11e5c-145">É possível retornar uma tupla da operação de análise se encerrar a chamada para o <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> método no nosso próprio método.</span><span class="sxs-lookup"><span data-stu-id="11e5c-145">We can return a tuple from the parsing operation if we wrap the call to the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method in our own method.</span></span> <span data-ttu-id="11e5c-146">No exemplo a seguir, `NumericLibrary.ParseInteger` chama o <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> método e retorna uma tupla nomeada com dois elementos.</span><span class="sxs-lookup"><span data-stu-id="11e5c-146">In the following example, `NumericLibrary.ParseInteger` calls the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method and returns a named tuple with two elements.</span></span> 

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

<span data-ttu-id="11e5c-147">Em seguida, você pode chamar o método com o código como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="11e5c-147">You can then call the method with code like the following:</span></span>

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)]

## <a name="visual-basic-tuples-and-tuples-in-the-net-framework"></a><span data-ttu-id="11e5c-148">Tuplas de Visual Basic e tuplas no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="11e5c-148">Visual Basic tuples and tuples in the .NET Framework</span></span>

<span data-ttu-id="11e5c-149">Uma coleção de itens do Visual Basic é uma instância de uma a **System.ValueTuple** tipos genéricos, que foram introduzidos no .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="11e5c-149">A Visual Basic tuple is an instance of one of the **System.ValueTuple** generic types, which were introduced in the .NET Framework 4.7.</span></span> <span data-ttu-id="11e5c-150">O .NET Framework também inclui um conjunto de genérica **System.Tuple** classes.</span><span class="sxs-lookup"><span data-stu-id="11e5c-150">The .NET Framework also includes a set of generic **System.Tuple** classes.</span></span> <span data-ttu-id="11e5c-151">Essas classes, no entanto, são diferentes de tuplas do Visual Basic e o **System.ValueTuple** tipos genéricos de várias maneiras:</span><span class="sxs-lookup"><span data-stu-id="11e5c-151">These classes, however, differ from Visual Basic tuples and the **System.ValueTuple** generic types in a number of ways:</span></span>

- <span data-ttu-id="11e5c-152">Os elementos do **tupla** classes são propriedades chamadas `Item1`, `Item2`e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="11e5c-152">The elements of the **Tuple** classes are properties named `Item1`, `Item2`, and so on.</span></span> <span data-ttu-id="11e5c-153">No Visual Basic tuplas e **ValueTuple** tipos de elementos de tupla são campos.</span><span class="sxs-lookup"><span data-stu-id="11e5c-153">In Visual Basic tuples and the **ValueTuple** types, tuple elements are fields.</span></span>

- <span data-ttu-id="11e5c-154">Você não pode atribuir nomes significativos para os elementos de um **tupla** instância ou de um **ValueTuple** instância.</span><span class="sxs-lookup"><span data-stu-id="11e5c-154">You cannot assign meaningful names to the elements of a **Tuple** instance or of a **ValueTuple** instance.</span></span> <span data-ttu-id="11e5c-155">Visual Basic permite que você atribua nomes que se comunicam o significado dos campos.</span><span class="sxs-lookup"><span data-stu-id="11e5c-155">Visual Basic allows you to assign names that communicate the meaning of the fields.</span></span>

- <span data-ttu-id="11e5c-156">As propriedades de um **tupla** instância são somente leitura; as tuplas imutáveis.</span><span class="sxs-lookup"><span data-stu-id="11e5c-156">The properties of a **Tuple** instance are read-only; the tuples are immutable.</span></span> <span data-ttu-id="11e5c-157">No Visual Basic tuplas e **ValueTuple** tipos, campos de tupla são leitura / gravação; as tuplas são mutáveis.</span><span class="sxs-lookup"><span data-stu-id="11e5c-157">In Visual Basic tuples and the **ValueTuple** types, tuple fields are read-write; the tuples are mutable.</span></span>

- <span data-ttu-id="11e5c-158">Genérica **tupla** tipos são tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="11e5c-158">The generic **Tuple** types are reference types.</span></span> <span data-ttu-id="11e5c-159">Usando esses **tupla** tipos significa que a alocação de objetos.</span><span class="sxs-lookup"><span data-stu-id="11e5c-159">Using these **Tuple** types means allocating objects.</span></span> <span data-ttu-id="11e5c-160">Em caminhos de acesso, isso pode ter um impacto mensurável no desempenho do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="11e5c-160">On hot paths, this can have a measurable impact on your application's performance.</span></span> <span data-ttu-id="11e5c-161">Tuplas de Visual Basic e o **ValueTuple** tipos são tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="11e5c-161">Visual Basic tuples and the **ValueTuple** types are value types.</span></span>

<span data-ttu-id="11e5c-162">Métodos de extensão no <xref:System.TupleExtensions> classe facilitam a conversão entre tuplas do Visual Basic e o .NET **tupla** objetos.</span><span class="sxs-lookup"><span data-stu-id="11e5c-162">Extension methods in the <xref:System.TupleExtensions> class make it easy to convert between Visual Basic tuples and .NET **Tuple** objects.</span></span> <span data-ttu-id="11e5c-163">O **ToTuple** método converte uma tupla de Visual Basic .NET **tupla** objeto e o **ToValueTuple** método converte .NET **tupla** objeto para uma coleção de itens do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="11e5c-163">The **ToTuple** method converts a Visual Basic tuple to a .NET **Tuple** object, and the **ToValueTuple** method converts a .NET **Tuple** object to a Visual Basic tuple.</span></span>

<span data-ttu-id="11e5c-164">O exemplo a seguir cria uma tupla, converte-o em .NET **tupla** objeto e converte-o novamente para uma coleção de itens do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="11e5c-164">The following example creates a tuple, converts it to a .NET **Tuple** object, and converts it back to a Visual Basic tuple.</span></span> <span data-ttu-id="11e5c-165">O exemplo, em seguida, compara essa tupla com o original para garantir que eles são iguais.</span><span class="sxs-lookup"><span data-stu-id="11e5c-165">The example then compares this tuple with the original one to ensure that they are equal.</span></span>

[!code-vb[Convert](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple2.vb#1)]

## <a name="see-also"></a><span data-ttu-id="11e5c-166">Consulte também</span><span class="sxs-lookup"><span data-stu-id="11e5c-166">See also</span></span>

[<span data-ttu-id="11e5c-167">Referência da linguagem Visual Basic</span><span class="sxs-lookup"><span data-stu-id="11e5c-167">Visual Basic Language Reference</span></span>](index.md)  
