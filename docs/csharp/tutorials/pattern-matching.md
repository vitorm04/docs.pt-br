---
title: Usar o recurso de correspondência de padrões para estender padrões de dados
description: Este tutorial avançado demonstra como usar as técnicas de correspondência de padrões para criar a funcionalidade usando dados e algoritmos que são criados separadamente.
ms.date: 03/13/2019
ms.custom: mvc
ms.openlocfilehash: 58e4a9175752c7845507f48a3684747092dc609a
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66378079"
---
# <a name="tutorial-using-pattern-matching-features-to-extend-data-types"></a><span data-ttu-id="c0685-103">Tutorial: Usar os recursos de correspondência de padrões para estender tipo de dados</span><span class="sxs-lookup"><span data-stu-id="c0685-103">Tutorial: Using pattern matching features to extend data types</span></span>

<span data-ttu-id="c0685-104">O C#7 introduziu recursos básicos de correspondência de padrões.</span><span class="sxs-lookup"><span data-stu-id="c0685-104">C# 7 introduced basic pattern matching features.</span></span> <span data-ttu-id="c0685-105">Esses recursos foram estendidos no C# 8 com novos padrões e expressões.</span><span class="sxs-lookup"><span data-stu-id="c0685-105">Those features are extended in C# 8 with new expressions and patterns.</span></span> <span data-ttu-id="c0685-106">É possível escrever uma funcionalidade que se comporte como se você tivesse estendido tipos que poderiam estar em outras bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="c0685-106">You can write functionality that behaves as though you extended types that may be in other libraries.</span></span> <span data-ttu-id="c0685-107">Outro uso dos padrões é criar a funcionalidade de que seu aplicativo precisa, mas que não é um recurso fundamental do tipo que está sendo estendido.</span><span class="sxs-lookup"><span data-stu-id="c0685-107">Another use for patterns is to create functionality your application requires that isn't a fundamental feature of the type being extended.</span></span>

<span data-ttu-id="c0685-108">Neste tutorial, você aprenderá a:</span><span class="sxs-lookup"><span data-stu-id="c0685-108">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="c0685-109">Reconhecer situações em que a correspondência de padrões deverá ser usada.</span><span class="sxs-lookup"><span data-stu-id="c0685-109">Recognize situations where pattern matching should be used.</span></span>
> * <span data-ttu-id="c0685-110">Usar expressões de correspondência de padrões para implementar o comportamento com base em tipos e valores de propriedade.</span><span class="sxs-lookup"><span data-stu-id="c0685-110">Use pattern matching expressions to implement behavior based on types and property values.</span></span>
> * <span data-ttu-id="c0685-111">Combinar a correspondência de padrões com outras técnicas para criar algoritmos completos.</span><span class="sxs-lookup"><span data-stu-id="c0685-111">Combine pattern matching with other techniques to create complete algorithms.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c0685-112">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="c0685-112">Prerequisites</span></span>

<span data-ttu-id="c0685-113">Você precisará configurar o computador para executar o .NET Core, incluindo o compilador da versão prévia do C# 8.0.</span><span class="sxs-lookup"><span data-stu-id="c0685-113">You'll need to set up your machine to run .NET Core, including the C# 8.0 preview compiler.</span></span> <span data-ttu-id="c0685-114">O compilador da versão prévia do C# 8 está disponível no último [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ou na última [versão prévia do .NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="c0685-114">The C# 8 preview compiler is available with the latest [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), or the latest [.NET Core 3.0 preview](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

<span data-ttu-id="c0685-115">Este tutorial pressupõe que você esteja familiarizado com o C# e .NET, incluindo o Visual Studio ou a CLI do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c0685-115">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="scenarios-for-pattern-matching"></a><span data-ttu-id="c0685-116">Cenários para a correspondência de padrões</span><span class="sxs-lookup"><span data-stu-id="c0685-116">Scenarios for pattern matching</span></span>

<span data-ttu-id="c0685-117">O desenvolvimento moderno geralmente inclui a integração de dados de várias fontes e a apresentação de informações e insights de dados em um único aplicativo coeso.</span><span class="sxs-lookup"><span data-stu-id="c0685-117">Modern development often includes integrating data from multiple sources and presenting information and insights from that data in a single cohesive application.</span></span> <span data-ttu-id="c0685-118">Você e sua equipe não terão controle ou acesso a todos os tipos que representam os dados de entrada.</span><span class="sxs-lookup"><span data-stu-id="c0685-118">You and your team won't have control or access for all the types that represent the incoming data.</span></span>

<span data-ttu-id="c0685-119">O design orientado a objeto clássico exigiria a criação de tipos em seu aplicativo que representassem cada tipo de dados das várias fontes de dados.</span><span class="sxs-lookup"><span data-stu-id="c0685-119">The classic object-oriented design would call for creating types in your application that represent each data type from those multiple data sources.</span></span> <span data-ttu-id="c0685-120">O aplicativo, então, trabalharia com esses novos tipos, criaria hierarquias de herança, métodos virtuais e implementaria abstrações.</span><span class="sxs-lookup"><span data-stu-id="c0685-120">Then, your application would work with those new types, build inheritance hierarchies, create virtual methods, and implement abstractions.</span></span> <span data-ttu-id="c0685-121">Essas técnicas funcionam e, às vezes, são as melhores ferramentas.</span><span class="sxs-lookup"><span data-stu-id="c0685-121">Those techniques work, and sometimes they are the best tools.</span></span> <span data-ttu-id="c0685-122">Outras vezes, é possível escrever menos código.</span><span class="sxs-lookup"><span data-stu-id="c0685-122">Other times you can write less code.</span></span> <span data-ttu-id="c0685-123">Você pode escrever um código mais claro usando técnicas que separam os dados das operações que manipulam esses dados.</span><span class="sxs-lookup"><span data-stu-id="c0685-123">You can write more clear code using techniques that separate the data from the operations that manipulate that data.</span></span>

<span data-ttu-id="c0685-124">Neste tutorial, você vai criar e explorar um aplicativo que usa dados recebidos de várias fontes externas para um único cenário.</span><span class="sxs-lookup"><span data-stu-id="c0685-124">In this tutorial, you'll create and explore an application that takes incoming data from several external sources for a single scenario.</span></span> <span data-ttu-id="c0685-125">Você verá como a **correspondência de padrões** fornece uma maneira eficiente para consumir e processar esses dados de maneiras que não eram parte do sistema original.</span><span class="sxs-lookup"><span data-stu-id="c0685-125">You'll see how **pattern matching** provides an efficient way to consume and process that data in ways that weren't part of the original system.</span></span>

<span data-ttu-id="c0685-126">Imagine, por exemplo, uma área metropolitana principal que está implantando pedágios e preços diferenciados em horário de pico para gerenciar o tráfego.</span><span class="sxs-lookup"><span data-stu-id="c0685-126">Consider a major metropolitan area that is using tolls and peak time pricing to manage traffic.</span></span> <span data-ttu-id="c0685-127">Você escreve um aplicativo que calcula o pedágio de um veículo com base em seu tipo.</span><span class="sxs-lookup"><span data-stu-id="c0685-127">You write an application that calculates tolls for a vehicle based on its type.</span></span> <span data-ttu-id="c0685-128">Posteriormente, as melhorias vão incorporar preços com base no número de ocupantes do veículo.</span><span class="sxs-lookup"><span data-stu-id="c0685-128">Later enhancements incorporate pricing based on the number of occupants in the vehicle.</span></span> <span data-ttu-id="c0685-129">Outros aprimoramentos vão adicionar o preço com base na hora e no dia da semana.</span><span class="sxs-lookup"><span data-stu-id="c0685-129">Further enhancements add pricing based on the time and the day of the week.</span></span>

<span data-ttu-id="c0685-130">Com base nessa breve descrição, você pode ter elaborado rapidamente uma hierarquia de objetos para modelar esse sistema.</span><span class="sxs-lookup"><span data-stu-id="c0685-130">From that brief description, you may have quickly sketched out an object hierarchy to model this system.</span></span> <span data-ttu-id="c0685-131">No entanto, seus dados são provenientes de várias fontes, como outros sistemas de gerenciamento de registro do veículo.</span><span class="sxs-lookup"><span data-stu-id="c0685-131">However, your data is coming from multiple sources like other vehicle registration management systems.</span></span> <span data-ttu-id="c0685-132">Esses sistemas fornecem classes diferentes para modelar aqueles dados, e você não tem um modelo de objeto único o qual seja possível usar.</span><span class="sxs-lookup"><span data-stu-id="c0685-132">These systems provide different classes to model that data and you don't have a single object model you can use.</span></span> <span data-ttu-id="c0685-133">Neste tutorial, você usará essas classes simplificadas para criar o modelo para os dados do veículo, a partir desses sistemas externos, conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="c0685-133">In this tutorial, you'll use these simplified classes to model for the vehicle data from these external systems, as shown in the following code:</span></span>

[!code-csharp[ExternalSystems](~/samples/csharp/tutorials/patterns/start/toll-calculator/ExternalSystems.cs)]

<span data-ttu-id="c0685-134">Faça o download do código inicial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/start) do GitHub.</span><span class="sxs-lookup"><span data-stu-id="c0685-134">You can download the starter code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/start) GitHub repository.</span></span> <span data-ttu-id="c0685-135">É possível ver que as classes de veículos são de sistemas diferentes, e estão em namespaces diferentes.</span><span class="sxs-lookup"><span data-stu-id="c0685-135">You can see that the vehicle classes are from different systems, and are in different namespaces.</span></span> <span data-ttu-id="c0685-136">Nenhuma base comum de classe, além da `System.Object` pode ser aproveitada.</span><span class="sxs-lookup"><span data-stu-id="c0685-136">No common base class, other than `System.Object` can be leveraged.</span></span>

## <a name="pattern-matching-designs"></a><span data-ttu-id="c0685-137">Designs de correspondência de padrões</span><span class="sxs-lookup"><span data-stu-id="c0685-137">Pattern matching designs</span></span>

<span data-ttu-id="c0685-138">O cenário usado neste tutorial destaca os tipos de problemas que a correspondência de padrões pode resolver de forma adequada:</span><span class="sxs-lookup"><span data-stu-id="c0685-138">The scenario used in this tutorial highlights the kinds of problems that pattern matching is well-suited to solve:</span></span>

- <span data-ttu-id="c0685-139">Os objetos com os quais você precisa trabalhar não estão em uma hierarquia de objetos que corresponde aos seus objetivos.</span><span class="sxs-lookup"><span data-stu-id="c0685-139">The objects you need to work with aren't in an object hierarchy that matches your goals.</span></span> <span data-ttu-id="c0685-140">É possível que você esteja trabalhando com classes que fazem parte dos sistemas não relacionados.</span><span class="sxs-lookup"><span data-stu-id="c0685-140">You may be working with classes that are part of unrelated systems.</span></span>
- <span data-ttu-id="c0685-141">A funcionalidade que você está adicionando não faz parte da abstração central dessas classes.</span><span class="sxs-lookup"><span data-stu-id="c0685-141">The functionality you're adding isn't part of the core abstraction for these classes.</span></span> <span data-ttu-id="c0685-142">A tarifa paga por um veículo *muda* de acordo com diferentes tipos de veículos, mas o pedágio não é uma função principal do veículo.</span><span class="sxs-lookup"><span data-stu-id="c0685-142">The toll paid by a vehicle *changes* for different types of vehicles, but the toll isn't a core function of the vehicle.</span></span>

<span data-ttu-id="c0685-143">Quando a *forma* dos dados e as *operações* nos dados não são descritas em conjunto, o recurso de correspondência padrões no C# facilita o trabalho.</span><span class="sxs-lookup"><span data-stu-id="c0685-143">When the *shape* of the data and the *operations* on that data are not described together, the pattern matching features in C# make it easier to work with.</span></span>

## <a name="implement-the-basic-toll-calculations"></a><span data-ttu-id="c0685-144">Implementar os cálculos básicos de pedágio</span><span class="sxs-lookup"><span data-stu-id="c0685-144">Implement the basic toll calculations</span></span>

<span data-ttu-id="c0685-145">O cálculo mais básico do pedágio dependerá apenas do tipo do veículo:</span><span class="sxs-lookup"><span data-stu-id="c0685-145">The most basic toll calculation relies only on the vehicle type:</span></span>

- <span data-ttu-id="c0685-146">Um `Car` será R$2,00.</span><span class="sxs-lookup"><span data-stu-id="c0685-146">A `Car` is $2.00.</span></span>
- <span data-ttu-id="c0685-147">Um `Taxi` será R$3,50.</span><span class="sxs-lookup"><span data-stu-id="c0685-147">A `Taxi` is $3.50.</span></span>
- <span data-ttu-id="c0685-148">Um `Bus` será R$5,00.</span><span class="sxs-lookup"><span data-stu-id="c0685-148">A `Bus` is $5.00.</span></span>
- <span data-ttu-id="c0685-149">Um `DeliveryTruck` será R$10,00.</span><span class="sxs-lookup"><span data-stu-id="c0685-149">A `DeliveryTruck` is $10.00</span></span>

<span data-ttu-id="c0685-150">Crie uma nova classe `TollCalculator` e implemente a correspondência de padrões no tipo de veículo para obter a quantidade do pedágio.</span><span class="sxs-lookup"><span data-stu-id="c0685-150">Create a new `TollCalculator` class, and implement pattern matching on the vehicle type to get the toll amount.</span></span> <span data-ttu-id="c0685-151">O código a seguir mostra a implementação inicial do `TollCalculator`.</span><span class="sxs-lookup"><span data-stu-id="c0685-151">The following code shows the initial implementation of the `TollCalculator`.</span></span>

```csharp
using System;
using CommercialRegistration;
using ConsumerVehicleRegistration;
using LiveryRegistration;

namespace toll_calculator
{
    public class TollCalculator
    {
        public decimal CalculateToll(object vehicle) =>
            vehicle switch
        {
            Car c           => 2.00m,
            Taxi t          => 3.50m,
            Bus b           => 5.00m,
            DeliveryTruck t => 10.00m,
            { }             => throw new ArgumentException(message: "Not a known vehicle type", paramName: nameof(vehicle)),
            null            => throw new ArgumentNullException(nameof(vehicle))
        };
    }
}
```

<span data-ttu-id="c0685-152">O código anterior usa uma **expressão switch** (não igual a uma instrução [`switch`](../language-reference/keywords/switch.md)) que testa o **tipo de padrão**.</span><span class="sxs-lookup"><span data-stu-id="c0685-152">The preceding code uses a **switch expression** (not the same as a [`switch`](../language-reference/keywords/switch.md) statement) that tests the **type pattern**.</span></span> <span data-ttu-id="c0685-153">A **expressão switch** inicia-se com a variável, `vehicle` no código anterior, seguida pela palavra-chave `switch`.</span><span class="sxs-lookup"><span data-stu-id="c0685-153">A **switch expression** begins with the variable, `vehicle` in the preceding code, followed by the `switch` keyword.</span></span> <span data-ttu-id="c0685-154">Em seguida, estão os **braços switch** dentro de chaves.</span><span class="sxs-lookup"><span data-stu-id="c0685-154">Next comes all the **switch arms** inside curly braces.</span></span> <span data-ttu-id="c0685-155">A expressão `switch` faz outros refinamentos na sintaxe que circunda a instrução `switch`.</span><span class="sxs-lookup"><span data-stu-id="c0685-155">The `switch` expression makes other refinements to the syntax that surrounds the `switch` statement.</span></span> <span data-ttu-id="c0685-156">A palavra-chave `case` é omitida, e o resultado de cada braço é uma expressão.</span><span class="sxs-lookup"><span data-stu-id="c0685-156">The `case` keyword is omitted, and the result of each arm is an expression.</span></span> <span data-ttu-id="c0685-157">Os dois últimos braços apresentam um novo recurso de linguagem.</span><span class="sxs-lookup"><span data-stu-id="c0685-157">The last two arms show a new language feature.</span></span> <span data-ttu-id="c0685-158">O caso `{ }` corresponde a qualquer objeto não nulo que não correspondia a um braço anterior.</span><span class="sxs-lookup"><span data-stu-id="c0685-158">The `{ }` case matches any non-null object that didn't match an earlier arm.</span></span> <span data-ttu-id="c0685-159">Este braço captura qualquer tipo incorreto passado para esse método.</span><span class="sxs-lookup"><span data-stu-id="c0685-159">This arm catches any incorrect types passed to this method.</span></span>  <span data-ttu-id="c0685-160">O caso `{ }` precisa seguir os casos para cada tipo de veículo.</span><span class="sxs-lookup"><span data-stu-id="c0685-160">The `{ }` case must follow the cases for each vehicle type.</span></span> <span data-ttu-id="c0685-161">Se a ordem for revertida, o caso `{ }` terá precedência.</span><span class="sxs-lookup"><span data-stu-id="c0685-161">If the order were reversed, the `{ }` case would take precedence.</span></span> <span data-ttu-id="c0685-162">Por fim, o padrão `null` detecta quando um `null` é passado para esse método.</span><span class="sxs-lookup"><span data-stu-id="c0685-162">Finally, the `null` pattern detects when a `null` is passed to this method.</span></span> <span data-ttu-id="c0685-163">O padrão `null` pode ser o último, porque os outros padrões de tipo correspondem apenas a um objeto não nulo do tipo correto.</span><span class="sxs-lookup"><span data-stu-id="c0685-163">The `null` pattern can be last because the other type patterns match only a non-null object of the correct type.</span></span>

<span data-ttu-id="c0685-164">Você pode testar esse código usando o seguinte código no `Program.cs`:</span><span class="sxs-lookup"><span data-stu-id="c0685-164">You can test this code using the following code in `Program.cs`:</span></span>

```csharp
using System;
using CommercialRegistration;
using ConsumerVehicleRegistration;
using LiveryRegistration;

namespace toll_calculator
{
    class Program
    {
        static void Main(string[] args)
        {
            var tollCalc = new TollCalculator();

            var car = new Car();
            var taxi = new Taxi();
            var bus = new Bus();
            var truck = new DeliveryTruck();

            Console.WriteLine($"The toll for a car is {tollCalc.CalculateToll(car)}");
            Console.WriteLine($"The toll for a taxi is {tollCalc.CalculateToll(taxi)}");
            Console.WriteLine($"The toll for a bus is {tollCalc.CalculateToll(bus)}");
            Console.WriteLine($"The toll for a truck is {tollCalc.CalculateToll(truck)}");

            try
            {
                tollCalc.CalculateToll("this will fail");
            }
            catch (ArgumentException e)
            {
                Console.WriteLine("Caught an argument exception when using the wrong type");
            }
            try
            {
                tollCalc.CalculateToll(null);
            }
            catch (ArgumentNullException e)
            {
                Console.WriteLine("Caught an argument exception when using null");
            }
        }
    }
}
```

<span data-ttu-id="c0685-165">Esse código está incluído no projeto inicial, mas está comentado. Remova os comentários para poder testar o que acabou de escrever.</span><span class="sxs-lookup"><span data-stu-id="c0685-165">That code is included in the starter project, but is commented out. Remove the comments, and you can test what you've written.</span></span>

<span data-ttu-id="c0685-166">Você está começando a ver como os padrões podem ajudar a criar algoritmos em que o código e os dados estão separados.</span><span class="sxs-lookup"><span data-stu-id="c0685-166">You're starting to see how patterns can help you create algorithms where the code and the data are separate.</span></span> <span data-ttu-id="c0685-167">A expressão `switch` testa o tipo e produz valores diferentes com base nos resultados.</span><span class="sxs-lookup"><span data-stu-id="c0685-167">The `switch` expression tests the type and produces different values based on the results.</span></span> <span data-ttu-id="c0685-168">Mas isso é somente o começo.</span><span class="sxs-lookup"><span data-stu-id="c0685-168">That's only the beginning.</span></span>

## <a name="add-occupancy-pricing"></a><span data-ttu-id="c0685-169">Adicionar preços de acordo com a ocupação do veículo</span><span class="sxs-lookup"><span data-stu-id="c0685-169">Add occupancy pricing</span></span>

<span data-ttu-id="c0685-170">A autoridade de pedágio deseja incentivar que os veículos viagem com a capacidade máxima de pessoas.</span><span class="sxs-lookup"><span data-stu-id="c0685-170">The toll authority wants to encourage vehicles to travel at maximum capacity.</span></span> <span data-ttu-id="c0685-171">Eles decidiram cobrar valores mais altos quando os veículos tiverem poucos passageiros e oferecer redução da tarifa para veículos com a capacidade total ocupada:</span><span class="sxs-lookup"><span data-stu-id="c0685-171">They've decided to charge more when vehicles have fewer passengers, and encourage full vehicles by offering lower pricing:</span></span>

- <span data-ttu-id="c0685-172">Os carros e táxis com nenhum passageiro pagam uma taxa adicional de R$ 0,50.</span><span class="sxs-lookup"><span data-stu-id="c0685-172">Cars and taxis with no passengers pay an extra $0.50.</span></span>
- <span data-ttu-id="c0685-173">Os carros e táxis com dois passageiros obtêm um desconto de R$ 0,50.</span><span class="sxs-lookup"><span data-stu-id="c0685-173">Cars and taxis with two passengers get a 0.50 discount.</span></span>
- <span data-ttu-id="c0685-174">Os carros e táxis com três ou mais passageiros obtêm um desconto de R$ 1,00.</span><span class="sxs-lookup"><span data-stu-id="c0685-174">Cars and taxis with three or more passengers get a $1.00 discount.</span></span>
- <span data-ttu-id="c0685-175">Os ônibus com menos de 50% da capacidade completa pagam uma taxa adicional de R$ 2,00.</span><span class="sxs-lookup"><span data-stu-id="c0685-175">Buses that are less than 50% full pay an extra $2.00.</span></span>
- <span data-ttu-id="c0685-176">Os ônibus com 90% da capacidade de passageiros completa, ganham um desconto de R$ 1,00.</span><span class="sxs-lookup"><span data-stu-id="c0685-176">Buses that are more than 90% full get a $1.00 discount.</span></span>

<span data-ttu-id="c0685-177">Essas regras podem ser implementadas usando o **padrão de propriedade** na mesma expressão switch.</span><span class="sxs-lookup"><span data-stu-id="c0685-177">These rules can be implemented using the **property pattern** in the same switch expression.</span></span> <span data-ttu-id="c0685-178">O padrão de propriedade examina as propriedades do objeto depois que o tipo foi determinado.</span><span class="sxs-lookup"><span data-stu-id="c0685-178">The property pattern examines properties of the object once the type has been determined.</span></span> <span data-ttu-id="c0685-179">O único caso de um `Car` se expande para quatro casos diferentes:</span><span class="sxs-lookup"><span data-stu-id="c0685-179">The single case for a `Car` expands to four different cases:</span></span>

```csharp
vehicle switch
{
    Car { Passengers: 0}        => 2.00m + 0.50m,
    Car { Passengers: 1 }       => 2.0m,
    Car { Passengers: 2}        => 2.0m - 0.50m,
    Car c                       => 2.00m - 1.0m,

    // ...
};
```

<span data-ttu-id="c0685-180">Os três primeiros casos testam o tipo como um `Car`, em seguida, verificam o valor da propriedade `Passengers`.</span><span class="sxs-lookup"><span data-stu-id="c0685-180">The first three cases test the type as a `Car`, then check the value of the `Passengers` property.</span></span> <span data-ttu-id="c0685-181">Se ambos corresponderem, essa expressão é avaliada e retornada.</span><span class="sxs-lookup"><span data-stu-id="c0685-181">If both match, that expression is evaluated and returned.</span></span>

<span data-ttu-id="c0685-182">Você também expande os casos para táxis de maneira semelhante:</span><span class="sxs-lookup"><span data-stu-id="c0685-182">You would also expand the cases for taxis in a similar manner:</span></span>

```csharp
vehicle switch
{
    // ...

    Taxi { Fares: 0}  => 3.50m + 1.00m,
    Taxi { Fares: 1 } => 3.50m,
    Taxi { Fares: 2}  => 3.50m - 0.50m,
    Taxi t            => 3.50m - 1.00m,

    // ...
};
```

<span data-ttu-id="c0685-183">No exemplo anterior, a cláusula `when` foi omitida no caso final.</span><span class="sxs-lookup"><span data-stu-id="c0685-183">In the preceding example, the `when` clause was omitted on the final case.</span></span>

<span data-ttu-id="c0685-184">Em seguida, implemente as regras de ocupação expandindo os casos para os ônibus, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="c0685-184">Next, implement the occupancy rules by expanding the cases for buses, as shown in the following example:</span></span>

```csharp
vehicle switch
{
    // ...

    Bus b when ((double)b.Riders / (double)b.Capacity) < 0.50 => 5.00m + 2.00m,
    Bus b when ((double)b.Riders / (double)b.Capacity) > 0.90 => 5.00m - 1.00m,
    Bus b => 5.00m,

    // ...
};
```

<span data-ttu-id="c0685-185">A autoridade de pedágio não está preocupada com o número de passageiros nos caminhões de carga.</span><span class="sxs-lookup"><span data-stu-id="c0685-185">The toll authority isn't concerned with the number of passengers in the delivery trucks.</span></span> <span data-ttu-id="c0685-186">Em vez disso, eles cobram mais com base na classe de peso desses caminhões.</span><span class="sxs-lookup"><span data-stu-id="c0685-186">Instead, they charge more based on the weight class of the trucks.</span></span> <span data-ttu-id="c0685-187">Os caminhões mais de 5000 quilos pagam uma taxa adicional de R$ 5,00.</span><span class="sxs-lookup"><span data-stu-id="c0685-187">Trucks over 5000 lbs are charged an extra $5.00.</span></span> <span data-ttu-id="c0685-188">Os caminhões leves abaixo de 3.000 lb recebem um desconto de US$ 2,00.</span><span class="sxs-lookup"><span data-stu-id="c0685-188">Light trucks under 3000 lbs are given a $2.00 discount.</span></span> <span data-ttu-id="c0685-189">Essa regra é implementada com o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="c0685-189">That rule is implemented with the following code:</span></span>

```csharp
vehicle switch
{
    // ...

    DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
    DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
    DeliveryTruck t => 10.00m,
};
```

<span data-ttu-id="c0685-190">O código anterior mostra a cláusula `when` de um braço switch.</span><span class="sxs-lookup"><span data-stu-id="c0685-190">The preceding code shows the `when` clause of a switch arm.</span></span> <span data-ttu-id="c0685-191">Você usa a cláusula `when` para testar as condições, com exceção da igualdade, em uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="c0685-191">You use the `when` clause to test conditions other than equality on a property.</span></span> <span data-ttu-id="c0685-192">Ao terminar, o método será muito semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="c0685-192">When you've finished, you'll have a method that looks much like the following:</span></span>

```csharp
vehicle switch
{
    Car { Passengers: 0}        => 2.00m + 0.50m,
    Car { Passengers: 1}        => 2.0m,
    Car { Passengers: 2}        => 2.0m - 0.50m,
    Car c                       => 2.00m - 1.0m,

    Taxi { Fares: 0}  => 3.50m + 1.00m,
    Taxi { Fares: 1 } => 3.50m,
    Taxi { Fares: 2}  => 3.50m - 0.50m,
    Taxi t            => 3.50m - 1.00m,

    Bus b when ((double)b.Riders / (double)b.Capacity) < 0.50 => 5.00m + 2.00m,
    Bus b when ((double)b.Riders / (double)b.Capacity) > 0.90 => 5.00m - 1.00m,
    Bus b => 5.00m,

    DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
    DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
    DeliveryTruck t => 10.00m,
};
```

<span data-ttu-id="c0685-193">Muitos desses braços switch são exemplos de **padrões recursivos**.</span><span class="sxs-lookup"><span data-stu-id="c0685-193">Many of these switch arms are examples of **recursive patterns**.</span></span> <span data-ttu-id="c0685-194">Por exemplo, `Car { Passengers: 1}` mostra um padrão constante dentro de um padrão de propriedade.</span><span class="sxs-lookup"><span data-stu-id="c0685-194">For example, `Car { Passengers: 1}` shows a constant pattern inside a property pattern.</span></span>

<span data-ttu-id="c0685-195">É possível fazer esse código menos repetitivo, usando switches aninhados.</span><span class="sxs-lookup"><span data-stu-id="c0685-195">You can make this code less repetitive by using nested switches.</span></span> <span data-ttu-id="c0685-196">O `Car` e `Taxi` têm quatro braços diferentes nos exemplos anteriores.</span><span class="sxs-lookup"><span data-stu-id="c0685-196">The `Car` and `Taxi` both have four different arms in the preceding examples.</span></span> <span data-ttu-id="c0685-197">Em ambos os casos, é possível criar um padrão de tipo que alimente um padrão de propriedade.</span><span class="sxs-lookup"><span data-stu-id="c0685-197">In both cases, you can create a type pattern that feeds into a property pattern.</span></span> <span data-ttu-id="c0685-198">Essa técnica é mostrada no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="c0685-198">This technique is shown in the following code:</span></span>

```csharp
public decimal CalculateToll(object vehicle) =>
    vehicle switch
    {
        Car c => c.Passengers switch
        {
            0 => 2.00m + 0.5m,
            1 => 2.0m,
            2 => 2.0m - 0.5m,
            _ => 2.00m - 1.0m
        },

        Taxi t => t.Fares switch
        {
            0 => 3.50m + 1.00m,
            1 => 3.50m,
            2 => 3.50m - 0.50m,
            _ => 3.50m - 1.00m
        },

        Bus b when ((double)b.Riders / (double)b.Capacity) < 0.50 => 5.00m + 2.00m,
        Bus b when ((double)b.Riders / (double)b.Capacity) > 0.90 => 5.00m - 1.00m,
        Bus b => 5.00m,

        DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
        DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
        DeliveryTruck t => 10.00m,

        { }  => throw new ArgumentException(message: "Not a known vehicle type", paramName: nameof(vehicle)),
        null => throw new ArgumentNullException(nameof(vehicle))
    };
```

<span data-ttu-id="c0685-199">Na amostra anterior, o uso de uma expressão recursiva significa não repetir os braços `Car` e `Taxi` contendo braços filho que testam o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="c0685-199">In the preceding sample, using a recursive expression means you don't repeat the `Car` and `Taxi` arms containing child arms that test the property value.</span></span> <span data-ttu-id="c0685-200">Essa técnica não é usada para os braços `Bus` e `DeliveryTruck` porque esses estão testando intervalos da propriedade, e não valores discretos.</span><span class="sxs-lookup"><span data-stu-id="c0685-200">This technique isn't used for the `Bus` and `DeliveryTruck` arms because those arms are testing ranges for the property, not discrete values.</span></span>

## <a name="add-peak-pricing"></a><span data-ttu-id="c0685-201">Adicionar preço de horário de pico</span><span class="sxs-lookup"><span data-stu-id="c0685-201">Add peak pricing</span></span>

<span data-ttu-id="c0685-202">Para um último recurso, a autoridade de pedágio quer adicionar um preço os horários de pico.</span><span class="sxs-lookup"><span data-stu-id="c0685-202">For the final feature, the toll authority wants to add time sensitive peak pricing.</span></span> <span data-ttu-id="c0685-203">Durante os horários de pico da manhã e do final da tarde, os pedágios serão dobrados.</span><span class="sxs-lookup"><span data-stu-id="c0685-203">During the morning and evening rush hours, the tolls are doubled.</span></span> <span data-ttu-id="c0685-204">Essa regra afetará apenas o tráfego em uma direção: entrada para a cidade, no período da manhã, e de saída da cidade, no período da tarde.</span><span class="sxs-lookup"><span data-stu-id="c0685-204">That rule only affects traffic in one direction: inbound to the city in the morning, and outbound in the evening rush hour.</span></span> <span data-ttu-id="c0685-205">Em outros períodos durante o dia útil, os pedágios aumentam 50%.</span><span class="sxs-lookup"><span data-stu-id="c0685-205">During other times during the workday, tolls increase by 50%.</span></span> <span data-ttu-id="c0685-206">Nos períodos da noite e madrugada e de manhã cedo, as tarifas são 25% mais baratas.</span><span class="sxs-lookup"><span data-stu-id="c0685-206">Late night and early morning, tolls are reduced by 25%.</span></span> <span data-ttu-id="c0685-207">Durante o fim de semana, a taxa é normal, independentemente da hora.</span><span class="sxs-lookup"><span data-stu-id="c0685-207">During the weekend, it's the normal rate, regardless of the time.</span></span>

<span data-ttu-id="c0685-208">Você usará a correspondência de padrões para esse recurso, mas poderá integrá-lo a outras técnicas.</span><span class="sxs-lookup"><span data-stu-id="c0685-208">You'll use pattern matching for this feature, but you'll integrate it with other techniques.</span></span> <span data-ttu-id="c0685-209">É possível criar uma única expressão de correspondência de padrões que leva em conta todas as combinações de direção, dia da semana e hora.</span><span class="sxs-lookup"><span data-stu-id="c0685-209">You could build a single pattern match expression that would account for all the combinations of direction, day of the week, and time.</span></span> <span data-ttu-id="c0685-210">O resultado seria uma expressão complicada.</span><span class="sxs-lookup"><span data-stu-id="c0685-210">The result would be a complicated expression.</span></span> <span data-ttu-id="c0685-211">Seria difícil de ler e entender.</span><span class="sxs-lookup"><span data-stu-id="c0685-211">It would be hard to read and difficult to understand.</span></span> <span data-ttu-id="c0685-212">O que dificulta garantir a exatidão.</span><span class="sxs-lookup"><span data-stu-id="c0685-212">That makes it hard to ensure correctness.</span></span> <span data-ttu-id="c0685-213">Em vez disso, combine esses métodos para criar uma tupla de valores que descreve de forma concisa todos os estados.</span><span class="sxs-lookup"><span data-stu-id="c0685-213">Instead, combine those methods to build a tuple of values that concisely describes all those states.</span></span> <span data-ttu-id="c0685-214">Em seguida, use a correspondência de padrões para calcular um multiplicador para o pedágio.</span><span class="sxs-lookup"><span data-stu-id="c0685-214">Then use pattern matching to calculate a multiplier for the toll.</span></span> <span data-ttu-id="c0685-215">A tupla contém três condições distintas:</span><span class="sxs-lookup"><span data-stu-id="c0685-215">The tuple contains three discrete conditions:</span></span>

- <span data-ttu-id="c0685-216">O dia é um dia da semana ou do fim de semana.</span><span class="sxs-lookup"><span data-stu-id="c0685-216">The day is either a weekday or a weekend.</span></span>
- <span data-ttu-id="c0685-217">A faixa de tempo é quando o pedágio é coletado.</span><span class="sxs-lookup"><span data-stu-id="c0685-217">The band of time when the toll is collected.</span></span>
- <span data-ttu-id="c0685-218">A direção é para a cidade ou da cidade</span><span class="sxs-lookup"><span data-stu-id="c0685-218">The direction is into the city or out of the city</span></span>

<span data-ttu-id="c0685-219">A tabela a seguir mostra as combinações de valores de entrada e multiplicador de preços para os horários de pico:</span><span class="sxs-lookup"><span data-stu-id="c0685-219">The following table shows the combinations of input values and the peak pricing multiplier:</span></span>

| <span data-ttu-id="c0685-220">Dia</span><span class="sxs-lookup"><span data-stu-id="c0685-220">Day</span></span>        | <span data-ttu-id="c0685-221">Hora</span><span class="sxs-lookup"><span data-stu-id="c0685-221">Time</span></span>         | <span data-ttu-id="c0685-222">Direção</span><span class="sxs-lookup"><span data-stu-id="c0685-222">Direction</span></span> | <span data-ttu-id="c0685-223">Premium</span><span class="sxs-lookup"><span data-stu-id="c0685-223">Premium</span></span> |
| ---------- | ------------ | --------- |--------:|
| <span data-ttu-id="c0685-224">Dia útil</span><span class="sxs-lookup"><span data-stu-id="c0685-224">Weekday</span></span>    | <span data-ttu-id="c0685-225">horário de pico da manhã</span><span class="sxs-lookup"><span data-stu-id="c0685-225">morning rush</span></span> | <span data-ttu-id="c0685-226">entrada</span><span class="sxs-lookup"><span data-stu-id="c0685-226">inbound</span></span>   | <span data-ttu-id="c0685-227">x 2,00</span><span class="sxs-lookup"><span data-stu-id="c0685-227">x 2.00</span></span>  |
| <span data-ttu-id="c0685-228">Dia útil</span><span class="sxs-lookup"><span data-stu-id="c0685-228">Weekday</span></span>    | <span data-ttu-id="c0685-229">horário de pico da manhã</span><span class="sxs-lookup"><span data-stu-id="c0685-229">morning rush</span></span> | <span data-ttu-id="c0685-230">saída</span><span class="sxs-lookup"><span data-stu-id="c0685-230">outbound</span></span>  | <span data-ttu-id="c0685-231">x 1,00</span><span class="sxs-lookup"><span data-stu-id="c0685-231">x 1.00</span></span>  |
| <span data-ttu-id="c0685-232">Dia útil</span><span class="sxs-lookup"><span data-stu-id="c0685-232">Weekday</span></span>    | <span data-ttu-id="c0685-233">hora do dia</span><span class="sxs-lookup"><span data-stu-id="c0685-233">daytime</span></span>      | <span data-ttu-id="c0685-234">entrada</span><span class="sxs-lookup"><span data-stu-id="c0685-234">inbound</span></span>   | <span data-ttu-id="c0685-235">x 1,50</span><span class="sxs-lookup"><span data-stu-id="c0685-235">x 1.50</span></span>  |
| <span data-ttu-id="c0685-236">Dia útil</span><span class="sxs-lookup"><span data-stu-id="c0685-236">Weekday</span></span>    | <span data-ttu-id="c0685-237">hora do dia</span><span class="sxs-lookup"><span data-stu-id="c0685-237">daytime</span></span>      | <span data-ttu-id="c0685-238">saída</span><span class="sxs-lookup"><span data-stu-id="c0685-238">outbound</span></span>  | <span data-ttu-id="c0685-239">x 1,50</span><span class="sxs-lookup"><span data-stu-id="c0685-239">x 1.50</span></span>  |
| <span data-ttu-id="c0685-240">Dia útil</span><span class="sxs-lookup"><span data-stu-id="c0685-240">Weekday</span></span>    | <span data-ttu-id="c0685-241">horário de pico do fim da tarde</span><span class="sxs-lookup"><span data-stu-id="c0685-241">evening rush</span></span> | <span data-ttu-id="c0685-242">entrada</span><span class="sxs-lookup"><span data-stu-id="c0685-242">inbound</span></span>   | <span data-ttu-id="c0685-243">x 1,00</span><span class="sxs-lookup"><span data-stu-id="c0685-243">x 1.00</span></span>  |
| <span data-ttu-id="c0685-244">Dia útil</span><span class="sxs-lookup"><span data-stu-id="c0685-244">Weekday</span></span>    | <span data-ttu-id="c0685-245">horário de pico do fim da tarde</span><span class="sxs-lookup"><span data-stu-id="c0685-245">evening rush</span></span> | <span data-ttu-id="c0685-246">saída</span><span class="sxs-lookup"><span data-stu-id="c0685-246">outbound</span></span>  | <span data-ttu-id="c0685-247">x 2,00</span><span class="sxs-lookup"><span data-stu-id="c0685-247">x 2.00</span></span>  |
| <span data-ttu-id="c0685-248">Dia útil</span><span class="sxs-lookup"><span data-stu-id="c0685-248">Weekday</span></span>    | <span data-ttu-id="c0685-249">noite e madrugada</span><span class="sxs-lookup"><span data-stu-id="c0685-249">overnight</span></span>    | <span data-ttu-id="c0685-250">entrada</span><span class="sxs-lookup"><span data-stu-id="c0685-250">inbound</span></span>   | <span data-ttu-id="c0685-251">x 0,75</span><span class="sxs-lookup"><span data-stu-id="c0685-251">x 0.75</span></span>  |
| <span data-ttu-id="c0685-252">Dia útil</span><span class="sxs-lookup"><span data-stu-id="c0685-252">Weekday</span></span>    | <span data-ttu-id="c0685-253">noite e madrugada</span><span class="sxs-lookup"><span data-stu-id="c0685-253">overnight</span></span>    | <span data-ttu-id="c0685-254">saída</span><span class="sxs-lookup"><span data-stu-id="c0685-254">outbound</span></span>  | <span data-ttu-id="c0685-255">x 0,75</span><span class="sxs-lookup"><span data-stu-id="c0685-255">x 0.75</span></span>  |
| <span data-ttu-id="c0685-256">Fim de semana</span><span class="sxs-lookup"><span data-stu-id="c0685-256">Weekend</span></span>    | <span data-ttu-id="c0685-257">horário de pico da manhã</span><span class="sxs-lookup"><span data-stu-id="c0685-257">morning rush</span></span> | <span data-ttu-id="c0685-258">entrada</span><span class="sxs-lookup"><span data-stu-id="c0685-258">inbound</span></span>   | <span data-ttu-id="c0685-259">x 1,00</span><span class="sxs-lookup"><span data-stu-id="c0685-259">x 1.00</span></span>  |
| <span data-ttu-id="c0685-260">Fim de semana</span><span class="sxs-lookup"><span data-stu-id="c0685-260">Weekend</span></span>    | <span data-ttu-id="c0685-261">horário de pico da manhã</span><span class="sxs-lookup"><span data-stu-id="c0685-261">morning rush</span></span> | <span data-ttu-id="c0685-262">saída</span><span class="sxs-lookup"><span data-stu-id="c0685-262">outbound</span></span>  | <span data-ttu-id="c0685-263">x 1,00</span><span class="sxs-lookup"><span data-stu-id="c0685-263">x 1.00</span></span>  |
| <span data-ttu-id="c0685-264">Fim de semana</span><span class="sxs-lookup"><span data-stu-id="c0685-264">Weekend</span></span>    | <span data-ttu-id="c0685-265">hora do dia</span><span class="sxs-lookup"><span data-stu-id="c0685-265">daytime</span></span>      | <span data-ttu-id="c0685-266">entrada</span><span class="sxs-lookup"><span data-stu-id="c0685-266">inbound</span></span>   | <span data-ttu-id="c0685-267">x 1,00</span><span class="sxs-lookup"><span data-stu-id="c0685-267">x 1.00</span></span>  |
| <span data-ttu-id="c0685-268">Fim de semana</span><span class="sxs-lookup"><span data-stu-id="c0685-268">Weekend</span></span>    | <span data-ttu-id="c0685-269">hora do dia</span><span class="sxs-lookup"><span data-stu-id="c0685-269">daytime</span></span>      | <span data-ttu-id="c0685-270">saída</span><span class="sxs-lookup"><span data-stu-id="c0685-270">outbound</span></span>  | <span data-ttu-id="c0685-271">x 1,00</span><span class="sxs-lookup"><span data-stu-id="c0685-271">x 1.00</span></span>  |
| <span data-ttu-id="c0685-272">Fim de semana</span><span class="sxs-lookup"><span data-stu-id="c0685-272">Weekend</span></span>    | <span data-ttu-id="c0685-273">horário de pico do fim da tarde</span><span class="sxs-lookup"><span data-stu-id="c0685-273">evening rush</span></span> | <span data-ttu-id="c0685-274">entrada</span><span class="sxs-lookup"><span data-stu-id="c0685-274">inbound</span></span>   | <span data-ttu-id="c0685-275">x 1,00</span><span class="sxs-lookup"><span data-stu-id="c0685-275">x 1.00</span></span>  |
| <span data-ttu-id="c0685-276">Fim de semana</span><span class="sxs-lookup"><span data-stu-id="c0685-276">Weekend</span></span>    | <span data-ttu-id="c0685-277">horário de pico do fim da tarde</span><span class="sxs-lookup"><span data-stu-id="c0685-277">evening rush</span></span> | <span data-ttu-id="c0685-278">saída</span><span class="sxs-lookup"><span data-stu-id="c0685-278">outbound</span></span>  | <span data-ttu-id="c0685-279">x 1,00</span><span class="sxs-lookup"><span data-stu-id="c0685-279">x 1.00</span></span>  |
| <span data-ttu-id="c0685-280">Fim de semana</span><span class="sxs-lookup"><span data-stu-id="c0685-280">Weekend</span></span>    | <span data-ttu-id="c0685-281">noite e madrugada</span><span class="sxs-lookup"><span data-stu-id="c0685-281">overnight</span></span>    | <span data-ttu-id="c0685-282">entrada</span><span class="sxs-lookup"><span data-stu-id="c0685-282">inbound</span></span>   | <span data-ttu-id="c0685-283">x 1,00</span><span class="sxs-lookup"><span data-stu-id="c0685-283">x 1.00</span></span>  |
| <span data-ttu-id="c0685-284">Fim de semana</span><span class="sxs-lookup"><span data-stu-id="c0685-284">Weekend</span></span>    | <span data-ttu-id="c0685-285">noite e madrugada</span><span class="sxs-lookup"><span data-stu-id="c0685-285">overnight</span></span>    | <span data-ttu-id="c0685-286">saída</span><span class="sxs-lookup"><span data-stu-id="c0685-286">outbound</span></span>  | <span data-ttu-id="c0685-287">x 1,00</span><span class="sxs-lookup"><span data-stu-id="c0685-287">x 1.00</span></span>  |

<span data-ttu-id="c0685-288">Há 16 combinações diferentes das três variáveis.</span><span class="sxs-lookup"><span data-stu-id="c0685-288">There are 16 different combinations of the three variables.</span></span> <span data-ttu-id="c0685-289">Ao combinar algumas das condições, você simplificará a expressão switch.</span><span class="sxs-lookup"><span data-stu-id="c0685-289">By combining some of the conditions, you'll simplify the final switch expression.</span></span>

<span data-ttu-id="c0685-290">O sistema que coleta os pedágios usa uma estrutura <xref:System.DateTime> para a hora em que o pedágio foi cobrado.</span><span class="sxs-lookup"><span data-stu-id="c0685-290">The system that collects the tolls uses a <xref:System.DateTime> structure for the time when the toll was collected.</span></span> <span data-ttu-id="c0685-291">Construa métodos de membro que criam as variáveis da tabela anterior.</span><span class="sxs-lookup"><span data-stu-id="c0685-291">Build member methods that create the variables from the preceding table.</span></span> <span data-ttu-id="c0685-292">A seguinte função usa como correspondência de padrões a expressão switch para expressar se um <xref:System.DateTime> representa um fim de semana ou um dia útil:</span><span class="sxs-lookup"><span data-stu-id="c0685-292">The following function uses a pattern matching switch expression to express whether a <xref:System.DateTime> represents a weekend or a weekday:</span></span>

```csharp
private static bool IsWeekDay(DateTime timeOfToll) =>
    timeOfToll.DayOfWeek switch
    {
        DayOfWeek.Monday    => true,
        DayOfWeek.Tuesday   => true,
        DayOfWeek.Wednesday => true,
        DayOfWeek.Thursday  => true,
        DayOfWeek.Friday    => true,
        DayOfWeek.Saturday  => false,
        DayOfWeek.Sunday    => false
    };
```

<span data-ttu-id="c0685-293">Esse método funciona, mas é redundante.</span><span class="sxs-lookup"><span data-stu-id="c0685-293">That method works, but it's repetitious.</span></span> <span data-ttu-id="c0685-294">Para simplificar, faça conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="c0685-294">You can simplify it, as shown in the following code:</span></span>

[!code-csharp[IsWeekDay](~/samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#IsWeekDay)]

<span data-ttu-id="c0685-295">Depois, adicione uma função semelhante para categorizar o tempo nos blocos:</span><span class="sxs-lookup"><span data-stu-id="c0685-295">Next, add a similar function to categorize the time into the blocks:</span></span>

[!code-csharp[GetTimeBand](~/samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#GetTimeBand)]

<span data-ttu-id="c0685-296">O método anterior não usa a correspondência de padrões.</span><span class="sxs-lookup"><span data-stu-id="c0685-296">The previous method doesn't use pattern matching.</span></span> <span data-ttu-id="c0685-297">Fica mais claro usando uma cascata familiar de instruções `if`.</span><span class="sxs-lookup"><span data-stu-id="c0685-297">It's clearer using a familiar cascade of `if` statements.</span></span> <span data-ttu-id="c0685-298">Adicione um `enum` privado para converter cada intervalo de tempo em um valor discreto.</span><span class="sxs-lookup"><span data-stu-id="c0685-298">You do add a private `enum` to convert each range of time to a discrete value.</span></span>

<span data-ttu-id="c0685-299">Depois de criar esses métodos, é possível usar outra expressão `switch` com o **padrão de tupla** para calcular o preço premium.</span><span class="sxs-lookup"><span data-stu-id="c0685-299">After you create those methods, you can use another `switch` expression with the **tuple pattern** to calculate the pricing premium.</span></span> <span data-ttu-id="c0685-300">Você pode construir uma expressão `switch` com todos os 16 braços:</span><span class="sxs-lookup"><span data-stu-id="c0685-300">You could build a `switch` expression with all 16 arms:</span></span>

[!code-csharp[FullTuplePattern](~/samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#TuplePatternOne)]

<span data-ttu-id="c0685-301">O código acima funciona, mas pode ser simplificado.</span><span class="sxs-lookup"><span data-stu-id="c0685-301">The above code works, but it can be simplified.</span></span> <span data-ttu-id="c0685-302">Todas as oito combinações para o fim de semana têm o mesmo pedágio.</span><span class="sxs-lookup"><span data-stu-id="c0685-302">All eight combinations for the weekend have the same toll.</span></span> <span data-ttu-id="c0685-303">É possível substituir todas as oito pela seguinte linha:</span><span class="sxs-lookup"><span data-stu-id="c0685-303">You can replace all eight with the following line:</span></span>

```csharp
(false, _, _) => 1.0m,
```

<span data-ttu-id="c0685-304">Tanto o tráfego de entrada quanto o de saída têm o mesmo multiplicador durante o dia e a noite, nos dias úteis.</span><span class="sxs-lookup"><span data-stu-id="c0685-304">Both inbound and outbound traffic have the same multiplier during the weekday daytime and overnight hours.</span></span> <span data-ttu-id="c0685-305">Esses quatro braços switch podem ser substituídos por estas duas linhas:</span><span class="sxs-lookup"><span data-stu-id="c0685-305">Those four switch arms can be replaced with the following two lines:</span></span>

```csharp
(true, TimeBand.Overnight, _) => 0.75m,
(true, TimeBand.Daytime, _)   => 1.5m,
```

<span data-ttu-id="c0685-306">O código deverá ser semelhante ao seguinte após essas duas alterações:</span><span class="sxs-lookup"><span data-stu-id="c0685-306">The code should look like the following code after those two changes:</span></span>

```csharp
public decimal PeakTimePremium(DateTime timeOfToll, bool inbound) =>
    (IsWeekDay(timeOfToll), GetTimeBand(timeOfToll), inbound) switch
    {
        (true, TimeBand.MorningRush, true)  => 2.00m,
        (true, TimeBand.MorningRush, false) => 1.00m,
        (true, TimeBand.Daytime,     _)     => 1.50m,
        (true, TimeBand.EveningRush, true)  => 1.00m,
        (true, TimeBand.EveningRush, false) => 2.00m,
        (true, TimeBand.Overnight,   _)     => 0.75m,
        (false, _,                   _)     => 1.00m,
    };
```

<span data-ttu-id="c0685-307">Por fim, você pode remover os dois horários de pico em que é pago o preço normal.</span><span class="sxs-lookup"><span data-stu-id="c0685-307">Finally, you can remove the two rush hour times that pay the regular price.</span></span> <span data-ttu-id="c0685-308">Quando remover essas braços, substitua o `false` por um descarte (`_`) no braço switch final.</span><span class="sxs-lookup"><span data-stu-id="c0685-308">Once you remove those arms, you can replace the `false` with a discard (`_`) in the final switch arm.</span></span> <span data-ttu-id="c0685-309">O método concluído será o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c0685-309">You'll have the following finished method:</span></span>

[!code-csharp[SimplifiedTuplePattern](../../../samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#FinalTuplePattern)]

<span data-ttu-id="c0685-310">Este exemplo destaca uma das vantagens da correspondência de padrões: os branches de padrões são avaliados na ordem.</span><span class="sxs-lookup"><span data-stu-id="c0685-310">This example highlights one of the advantages of pattern matching: the pattern branches are evaluated in order.</span></span> <span data-ttu-id="c0685-311">Se você os reorganizar para que um branch anterior trate um dos casos posteriores, o compilador emitirá um aviso sobre o código inacessível.</span><span class="sxs-lookup"><span data-stu-id="c0685-311">If you rearrange them so that an earlier branch handles one of your later cases, the compiler warns you about the unreachable code.</span></span> <span data-ttu-id="c0685-312">Essas regras de linguagem tornam as simplificações anteriores mais fáceis com a certeza de que o código não foi alterado.</span><span class="sxs-lookup"><span data-stu-id="c0685-312">Those language rules made it easier to do the preceding simplifications with confidence that the code didn't change.</span></span>

<span data-ttu-id="c0685-313">A correspondência de padrões torna alguns tipos de código mais legíveis e oferece uma alternativa às técnicas orientadas a objeto quando não é possível adicionar o código às classes.</span><span class="sxs-lookup"><span data-stu-id="c0685-313">Pattern matching makes some types of code more readable and offers an alternative to object-oriented techniques when you can't add code to your classes.</span></span> <span data-ttu-id="c0685-314">A nuvem está fazendo com que os dados e a funcionalidade existam separadamente.</span><span class="sxs-lookup"><span data-stu-id="c0685-314">The cloud is causing data and functionality to live apart.</span></span> <span data-ttu-id="c0685-315">A *forma* dos dados e as *operações* nela não são necessariamente descritas juntas.</span><span class="sxs-lookup"><span data-stu-id="c0685-315">The *shape* of the data and the *operations* on it aren't necessarily described together.</span></span> <span data-ttu-id="c0685-316">Neste tutorial, você utilizou os dados existentes de maneiras completamente diferentes de sua função original.</span><span class="sxs-lookup"><span data-stu-id="c0685-316">In this tutorial, you consumed existing data in entirely different ways from its original function.</span></span> <span data-ttu-id="c0685-317">A correspondência de padrões proporcionou a capacidade de escrever a funcionalidade que substituiu esses tipos, ainda que não tenha sido possível estendê-los.</span><span class="sxs-lookup"><span data-stu-id="c0685-317">Pattern matching gave you the ability to write functionality that overrode those types, even though you couldn't extend them.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c0685-318">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="c0685-318">Next steps</span></span>

<span data-ttu-id="c0685-319">Baixe o código concluído no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/finished) do GitHub.</span><span class="sxs-lookup"><span data-stu-id="c0685-319">You can download the finished code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/finished) GitHub repository.</span></span> <span data-ttu-id="c0685-320">Explore os padrões por conta própria e adicione essa técnica em suas atividades regulares de codificação.</span><span class="sxs-lookup"><span data-stu-id="c0685-320">Explore patterns on your own and add this technique into your regular coding activities.</span></span> <span data-ttu-id="c0685-321">Aprender essas técnicas lhe oferece outra maneira de abordar problemas e criar novas funcionalidades.</span><span class="sxs-lookup"><span data-stu-id="c0685-321">Learning these techniques gives you another way to approach problems and create new functionality.</span></span>
