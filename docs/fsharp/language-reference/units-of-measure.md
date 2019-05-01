---
title: Unidades de medida
description: Saiba de ponto flutuante como e assinado valores inteiros F# podem ter associadas a unidades de medida, que normalmente são usadas para indicar o comprimento, volume e em massa.
ms.date: 05/16/2016
ms.openlocfilehash: 935dbff3545f92736ce8c51de86a168429dc194f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61982534"
---
# <a name="units-of-measure"></a><span data-ttu-id="ca938-103">Unidades de medida</span><span class="sxs-lookup"><span data-stu-id="ca938-103">Units of Measure</span></span>

<span data-ttu-id="ca938-104">Ponto flutuante e assinado valores inteiros F# podem ter associadas a unidades de medida, que normalmente são usadas para indicar o comprimento, volume, em massa e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="ca938-104">Floating point and signed integer values in F# can have associated units of measure, which are typically used to indicate length, volume, mass, and so on.</span></span> <span data-ttu-id="ca938-105">Ao usar as quantidades com unidades, você habilita o compilador verificar se o aritméticas relações tem as unidades corretas, que ajuda a evitar erros de programação.</span><span class="sxs-lookup"><span data-stu-id="ca938-105">By using quantities with units, you enable the compiler to verify that arithmetic relationships have the correct units, which helps prevent programming errors.</span></span>

## <a name="syntax"></a><span data-ttu-id="ca938-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ca938-106">Syntax</span></span>

```fsharp
[<Measure>] type unit-name [ = measure ]
```

## <a name="remarks"></a><span data-ttu-id="ca938-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="ca938-107">Remarks</span></span>

<span data-ttu-id="ca938-108">A sintaxe anterior define *nome da unidade* como uma unidade de medida.</span><span class="sxs-lookup"><span data-stu-id="ca938-108">The previous syntax defines *unit-name* as a unit of measure.</span></span> <span data-ttu-id="ca938-109">A parte opcional é usada para definir uma nova medida em termos de unidades definidas anteriormente.</span><span class="sxs-lookup"><span data-stu-id="ca938-109">The optional part is used to define a new measure in terms of previously defined units.</span></span> <span data-ttu-id="ca938-110">Por exemplo, a linha a seguir define a medida `cm` (centímetro).</span><span class="sxs-lookup"><span data-stu-id="ca938-110">For example, the following line defines the measure `cm` (centimeter).</span></span>

```fsharp
[<Measure>] type cm
```

<span data-ttu-id="ca938-111">A linha a seguir define a medida `ml` (milliliter) como um centímetro cúbico (`cm^3`).</span><span class="sxs-lookup"><span data-stu-id="ca938-111">The following line defines the measure `ml` (milliliter) as a cubic centimeter (`cm^3`).</span></span>

```fsharp
[<Measure>] type ml = cm^3
```

<span data-ttu-id="ca938-112">Na sintaxe anterior, *medida* é uma fórmula que envolve a unidades.</span><span class="sxs-lookup"><span data-stu-id="ca938-112">In the previous syntax, *measure* is a formula that involves units.</span></span> <span data-ttu-id="ca938-113">Em fórmulas que envolvem unidades, integrais potências têm suporte (positivo e negativo), espaços entre unidades indicam um produto de duas unidades, `*` também indica um produto de unidades, e `/` indica um quociente de unidades.</span><span class="sxs-lookup"><span data-stu-id="ca938-113">In formulas that involve units, integral powers are supported (positive and negative), spaces between units indicate a product of the two units, `*` also indicates a product of units, and `/` indicates a quotient of units.</span></span> <span data-ttu-id="ca938-114">Em uma unidade recíproca, você pode usar uma potência de número inteiro negativo ou um `/` que indica uma separação entre o numerador e o denominador de uma fórmula de unidade.</span><span class="sxs-lookup"><span data-stu-id="ca938-114">For a reciprocal unit, you can either use a negative integer power or a `/` that indicates a separation between the numerator and denominator of a unit formula.</span></span> <span data-ttu-id="ca938-115">Várias unidades no denominador devem ficar entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="ca938-115">Multiple units in the denominator should be surrounded by parentheses.</span></span> <span data-ttu-id="ca938-116">Unidades separadas por espaços após um `/` são interpretados como parte do denominador, mas nenhuma unidade seguindo um `*` são interpretados como parte do numerador.</span><span class="sxs-lookup"><span data-stu-id="ca938-116">Units separated by spaces after a `/` are interpreted as being part of the denominator, but any units following a `*` are interpreted as being part of the numerator.</span></span>

<span data-ttu-id="ca938-117">Você pode usar 1 em expressões de unidade, qualquer um sozinho para indicar uma quantidade sem dimensão, ou em conjunto com outras unidades, como o numerador.</span><span class="sxs-lookup"><span data-stu-id="ca938-117">You can use 1 in unit expressions, either alone to indicate a dimensionless quantity, or together with other units, such as in the numerator.</span></span> <span data-ttu-id="ca938-118">Por exemplo, as unidades para uma taxa seriam escritas como `1/s`, onde `s` indica segundos.</span><span class="sxs-lookup"><span data-stu-id="ca938-118">For example, the units for a rate would be written as `1/s`, where `s` indicates seconds.</span></span> <span data-ttu-id="ca938-119">Parênteses não são usados em fórmulas de unidade.</span><span class="sxs-lookup"><span data-stu-id="ca938-119">Parentheses are not used in unit formulas.</span></span> <span data-ttu-id="ca938-120">Você não especificar constantes de conversão numérica nas fórmulas de unidade; No entanto, você pode definir constantes de conversão com unidades separadamente e usá-los em cálculos de unidade-checked.</span><span class="sxs-lookup"><span data-stu-id="ca938-120">You do not specify numeric conversion constants in the unit formulas; however, you can define conversion constants with units separately and use them in unit-checked computations.</span></span>

<span data-ttu-id="ca938-121">Fórmulas de unidade que significam a mesma coisa podem ser escritas de várias maneiras equivalentes.</span><span class="sxs-lookup"><span data-stu-id="ca938-121">Unit formulas that mean the same thing can be written in various equivalent ways.</span></span> <span data-ttu-id="ca938-122">Portanto, o compilador converte as fórmulas de unidade em um formato consistente, que converte potências negativas recíprocos, unidades de grupos em um único numerador e um denominador e coloca em ordem alfabética as unidades no numerador e do denominador.</span><span class="sxs-lookup"><span data-stu-id="ca938-122">Therefore, the compiler converts unit formulas into a consistent form, which converts negative powers to reciprocals, groups units into a single numerator and a denominator, and alphabetizes the units in the numerator and denominator.</span></span>

<span data-ttu-id="ca938-123">Por exemplo, as fórmulas de unidade `kg m s^-2` e `m /s s * kg` são convertidos em `kg m/s^2`.</span><span class="sxs-lookup"><span data-stu-id="ca938-123">For example, the unit formulas `kg m s^-2` and `m /s s * kg` are both converted to `kg m/s^2`.</span></span>

<span data-ttu-id="ca938-124">Você pode usar unidades de medida em expressões de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="ca938-124">You use units of measure in floating point expressions.</span></span> <span data-ttu-id="ca938-125">Usar os números de ponto flutuante junto com as unidades associadas de medida adiciona outro nível de segurança de tipo e ajuda a evitar os erros de incompatibilidade de unidade que podem ocorrer em fórmulas quando você usa números de ponto flutuante sem rigidez de tipos.</span><span class="sxs-lookup"><span data-stu-id="ca938-125">Using floating point numbers together with associated units of measure adds another level of type safety and helps avoid the unit mismatch errors that can occur in formulas when you use weakly typed floating point numbers.</span></span> <span data-ttu-id="ca938-126">Se você escrever flutuante expressão de ponto que usa unidades, as unidades na expressão devem corresponder.</span><span class="sxs-lookup"><span data-stu-id="ca938-126">If you write a floating point expression that uses units, the units in the expression must match.</span></span>

<span data-ttu-id="ca938-127">É possível anotar literais com uma fórmula de unidade em colchetes angulares, conforme mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="ca938-127">You can annotate literals with a unit formula in angle brackets, as shown in the following examples.</span></span>

```fsharp
1.0<cm>
55.0<miles/hour>
```

<span data-ttu-id="ca938-128">Você não colocar um espaço entre o número e o colchete angular; No entanto, você pode incluir um sufixo literal, como `f`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ca938-128">You do not put a space between the number and the angle bracket; however, you can include a literal suffix such as `f`, as in the following example.</span></span>

```fsharp
// The f indicates single-precision floating point.
55.0f<miles/hour>
```

<span data-ttu-id="ca938-129">Tal uma anotação altera o tipo do literal do seu tipo primitivo (como `float`) para um tipo dimensionado, tais como `float<cm>` ou, nesse caso, `float<miles/hour>`.</span><span class="sxs-lookup"><span data-stu-id="ca938-129">Such an annotation changes the type of the literal from its primitive type (such as `float`) to a dimensioned type, such as `float<cm>` or, in this case, `float<miles/hour>`.</span></span> <span data-ttu-id="ca938-130">A anotação de uma unidade de `<1>` indica uma quantidade sem dimensão e seu tipo é equivalente ao tipo primitivo sem um parâmetro de unidade.</span><span class="sxs-lookup"><span data-stu-id="ca938-130">A unit annotation of `<1>` indicates a dimensionless quantity, and its type is equivalent to the primitive type without a unit parameter.</span></span>

<span data-ttu-id="ca938-131">O tipo de uma unidade de medida é um ponto flutuante ou integral tipo junto com uma anotação de unidade extra, indicada entre parênteses com sinal.</span><span class="sxs-lookup"><span data-stu-id="ca938-131">The type of a unit of measure is a floating point or signed integral type together with an extra unit annotation, indicated in brackets.</span></span> <span data-ttu-id="ca938-132">Assim, quando você escreve o tipo de uma conversão de `g` (gramas) para `kg` (quilogramas), você descreve os tipos da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="ca938-132">Thus, when you write the type of a conversion from `g` (grams) to `kg` (kilograms), you describe the types as follows.</span></span>

```fsharp
let convertg2kg (x : float<g>) = x / 1000.0<g/kg>
```

<span data-ttu-id="ca938-133">Unidades de medida são usadas para verificação de unidade de tempo de compilação, mas não são mantidas no ambiente de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ca938-133">Units of measure are used for compile-time unit checking but are not persisted in the run-time environment.</span></span> <span data-ttu-id="ca938-134">Portanto, elas não afetam o desempenho.</span><span class="sxs-lookup"><span data-stu-id="ca938-134">Therefore, they do not affect performance.</span></span>

<span data-ttu-id="ca938-135">Unidades de medida podem ser aplicadas a qualquer tipo, não apenas tipos de ponto; de flutuante No entanto, somente tipos de ponto flutuante assinado tipos integrais e quantidades de suporte dimensionada de tipos decimais.</span><span class="sxs-lookup"><span data-stu-id="ca938-135">Units of measure can be applied to any type, not just floating point types; however, only floating point types, signed integral types, and decimal types support dimensioned quantities.</span></span> <span data-ttu-id="ca938-136">Portanto, só faz sentido usar unidades de medida dos tipos primitivos e agregações que contêm esses tipos primitivos.</span><span class="sxs-lookup"><span data-stu-id="ca938-136">Therefore, it only makes sense to use units of measure on the primitive types and on aggregates that contain these primitive types.</span></span>

<span data-ttu-id="ca938-137">O exemplo a seguir ilustra o uso de unidades de medida.</span><span class="sxs-lookup"><span data-stu-id="ca938-137">The following example illustrates the use of units of measure.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6901.fs)]

<span data-ttu-id="ca938-138">O exemplo de código a seguir ilustra como converter de um número de ponto flutuante sem dimensão em um valor de ponto flutuante dimensionadas.</span><span class="sxs-lookup"><span data-stu-id="ca938-138">The following code example illustrates how to convert from a dimensionless floating point number to a dimensioned floating point value.</span></span> <span data-ttu-id="ca938-139">Você apenas multiplicar por 1,0, aplicando as dimensões para a 1.0.</span><span class="sxs-lookup"><span data-stu-id="ca938-139">You just multiply by 1.0, applying the dimensions to the 1.0.</span></span> <span data-ttu-id="ca938-140">Você pode abstrair isso em uma função como `degreesFahrenheit`.</span><span class="sxs-lookup"><span data-stu-id="ca938-140">You can abstract this into a function like `degreesFahrenheit`.</span></span>

<span data-ttu-id="ca938-141">Além disso, quando você passa valores dimensionadas para funções que esperam sem dimensão números de ponto flutuante, você deve cancelar a unidades ou convertido para `float` usando o `float` operador.</span><span class="sxs-lookup"><span data-stu-id="ca938-141">Also, when you pass dimensioned values to functions that expect dimensionless floating point numbers, you must cancel out the units or cast to `float` by using the `float` operator.</span></span> <span data-ttu-id="ca938-142">Neste exemplo, dividir por `1.0<degC>` para os argumentos a serem `printf` porque `printf` espera que as quantidades sem dimensão.</span><span class="sxs-lookup"><span data-stu-id="ca938-142">In this example, you divide by `1.0<degC>` for the arguments to `printf` because `printf` expects dimensionless quantities.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6902.fs)]

<span data-ttu-id="ca938-143">A sessão de exemplo a seguir mostra as saídas do e entradas para este código.</span><span class="sxs-lookup"><span data-stu-id="ca938-143">The following example session shows the outputs from and inputs to this code.</span></span>

```
Enter a temperature in degrees Fahrenheit.
90
That temperature in degrees Celsius is    32.22.
```

## <a name="using-generic-units"></a><span data-ttu-id="ca938-144">Usando unidades genéricas</span><span class="sxs-lookup"><span data-stu-id="ca938-144">Using Generic Units</span></span>

<span data-ttu-id="ca938-145">Você pode escrever funções genéricas que operam nos dados que tem uma unidade de medida associada.</span><span class="sxs-lookup"><span data-stu-id="ca938-145">You can write generic functions that operate on data that has an associated unit of measure.</span></span> <span data-ttu-id="ca938-146">Fazer isso especificando um tipo junto com uma unidade genérico como um parâmetro de tipo, conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="ca938-146">You do this by specifying a type together with a generic unit as a type parameter, as shown in the following code example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6903.fs)]

## <a name="creating-aggregate-types-with-generic-units"></a><span data-ttu-id="ca938-147">Criar tipos de agregação com unidades genéricas</span><span class="sxs-lookup"><span data-stu-id="ca938-147">Creating Aggregate Types with Generic Units</span></span>

<span data-ttu-id="ca938-148">O código a seguir mostra como criar um tipo de agregação que consiste em individuais valores de ponto flutuante que têm unidades que são genéricas.</span><span class="sxs-lookup"><span data-stu-id="ca938-148">The following code shows how to create an aggregate type that consists of individual floating point values that have units that are generic.</span></span> <span data-ttu-id="ca938-149">Isso permite que um único tipo a ser criado que funciona com uma variedade de unidades.</span><span class="sxs-lookup"><span data-stu-id="ca938-149">This enables a single type to be created that works with a variety of units.</span></span> <span data-ttu-id="ca938-150">Além disso, unidades genéricas preservam a segurança de tipos, garantindo que um tipo genérico que tem um conjunto de unidades é um tipo diferente do mesmo tipo genérico com um conjunto diferente de unidades.</span><span class="sxs-lookup"><span data-stu-id="ca938-150">Also, generic units preserve type safety by ensuring that a generic type that has one set of units is a different type than the same generic type with a different set of units.</span></span> <span data-ttu-id="ca938-151">A base dessa técnica é que o `Measure` atributo pode ser aplicado ao parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="ca938-151">The basis of this technique is that the `Measure` attribute can be applied to the type parameter.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6904.fs)]

## <a name="units-at-runtime"></a><span data-ttu-id="ca938-152">Unidades em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="ca938-152">Units at Runtime</span></span>

<span data-ttu-id="ca938-153">Unidades de medida são usadas para verificação de tipo estático.</span><span class="sxs-lookup"><span data-stu-id="ca938-153">Units of measure are used for static type checking.</span></span> <span data-ttu-id="ca938-154">Quando valores de ponto flutuante são compiladas, as unidades de medida são eliminadas, para que as unidades sejam perdidas em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ca938-154">When floating point values are compiled, the units of measure are eliminated, so the units are lost at run time.</span></span> <span data-ttu-id="ca938-155">Portanto, qualquer tentativa para implementar a funcionalidade que depende de verificando as unidades de tempo de execução não é possível.</span><span class="sxs-lookup"><span data-stu-id="ca938-155">Therefore, any attempt to implement functionality that depends on checking the units at run time is not possible.</span></span> <span data-ttu-id="ca938-156">Por exemplo, Implementando um `ToString` função para imprimir as unidades não é possível.</span><span class="sxs-lookup"><span data-stu-id="ca938-156">For example, implementing a `ToString` function to print out the units is not possible.</span></span>

## <a name="conversions"></a><span data-ttu-id="ca938-157">Conversões</span><span class="sxs-lookup"><span data-stu-id="ca938-157">Conversions</span></span>

<span data-ttu-id="ca938-158">Para converter um tipo que tem as unidades (por exemplo, `float<'u>`) para um tipo que não tem unidades, você pode usar a função de conversão padrão.</span><span class="sxs-lookup"><span data-stu-id="ca938-158">To convert a type that has units (for example, `float<'u>`) to a type that does not have units, you can use the standard conversion function.</span></span> <span data-ttu-id="ca938-159">Por exemplo, você pode usar `float` para converter em um `float` valor que não tem unidades, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="ca938-159">For example, you can use `float` to convert to a `float` value that does not have units, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6905.fs)]

<span data-ttu-id="ca938-160">Para converter um valor sem unidade em um valor que tem as unidades, você pode multiplicar por um valor de 1 ou 1.0 é anotado com as unidades apropriadas.</span><span class="sxs-lookup"><span data-stu-id="ca938-160">To convert a unitless value to a value that has units, you can multiply by a 1 or 1.0 value that is annotated with the appropriate units.</span></span> <span data-ttu-id="ca938-161">No entanto, para gravar as camadas de interoperabilidade, também há algumas funções explícita que você pode usar para converter valores sem unidade em valores com as unidades.</span><span class="sxs-lookup"><span data-stu-id="ca938-161">However, for writing interoperability layers, there are also some explicit functions that you can use to convert unitless values to values with units.</span></span> <span data-ttu-id="ca938-162">Eles estão na [Microsoft.FSharp.Core.LanguagePrimitives](https://msdn.microsoft.com/library/69d08ac5-5d51-4c20-bf1e-850fd312ece3) módulo.</span><span class="sxs-lookup"><span data-stu-id="ca938-162">These are in the [Microsoft.FSharp.Core.LanguagePrimitives](https://msdn.microsoft.com/library/69d08ac5-5d51-4c20-bf1e-850fd312ece3) module.</span></span> <span data-ttu-id="ca938-163">Por exemplo, para converter de um sem unidade `float` para um `float<cm>`, use [FloatWithMeasure](https://msdn.microsoft.com/library/69520bc7-d67b-46b8-9004-7cac9646b8d9), conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="ca938-163">For example, to convert from a unitless `float` to a `float<cm>`, use [FloatWithMeasure](https://msdn.microsoft.com/library/69520bc7-d67b-46b8-9004-7cac9646b8d9), as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6906.fs)]

## <a name="units-of-measure-in-the-f-core-library"></a><span data-ttu-id="ca938-164">Unidades de medida no F# biblioteca principal</span><span class="sxs-lookup"><span data-stu-id="ca938-164">Units of Measure in the F# Core library</span></span>

<span data-ttu-id="ca938-165">Uma biblioteca de unidade está disponível no `FSharp.Data.UnitSystems.SI` namespace.</span><span class="sxs-lookup"><span data-stu-id="ca938-165">A unit library is available in the `FSharp.Data.UnitSystems.SI` namespace.</span></span> <span data-ttu-id="ca938-166">Ele inclui as unidades de SI em sua forma do símbolo (como `m` de medidor) na `UnitSymbols` namespace secundário e seu nome completo (como `meter` de medidor) na `UnitNames` namespace secundário.</span><span class="sxs-lookup"><span data-stu-id="ca938-166">It includes SI units in both their symbol form (like `m` for meter) in the `UnitSymbols` sub-namespace, and their full name (like `meter` for meter) in the `UnitNames` sub-namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="ca938-167">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ca938-167">See also</span></span>

- [<span data-ttu-id="ca938-168">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="ca938-168">F# Language Reference</span></span>](index.md)