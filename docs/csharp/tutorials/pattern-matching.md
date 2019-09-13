---
title: Usar o recurso de correspondência de padrões para estender padrões de dados
description: Este tutorial avançado demonstra como usar as técnicas de correspondência de padrões para criar a funcionalidade usando dados e algoritmos que são criados separadamente.
ms.date: 03/13/2019
ms.custom: mvc
ms.openlocfilehash: 366791b113d3b1f9ccef303553a3656f7e803a32
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926648"
---
# <a name="tutorial-using-pattern-matching-features-to-extend-data-types"></a>Tutorial: Usar os recursos de correspondência de padrões para estender tipo de dados

O C#7 introduziu recursos básicos de correspondência de padrões. Esses recursos foram estendidos no C# 8 com novos padrões e expressões. É possível escrever uma funcionalidade que se comporte como se você tivesse estendido tipos que poderiam estar em outras bibliotecas. Outro uso dos padrões é criar a funcionalidade de que seu aplicativo precisa, mas que não é um recurso fundamental do tipo que está sendo estendido.

Neste tutorial, você aprenderá a:

> [!div class="checklist"]
>
> - Reconhecer situações em que a correspondência de padrões deverá ser usada.
> - Usar expressões de correspondência de padrões para implementar o comportamento com base em tipos e valores de propriedade.
> - Combinar a correspondência de padrões com outras técnicas para criar algoritmos completos.

## <a name="prerequisites"></a>Pré-requisitos

Você precisará configurar o computador para executar o .NET Core, incluindo o compilador da versão prévia do C# 8.0. O compilador da versão prévia do C# 8 está disponível no último [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ou na última [versão prévia do .NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core/3.0).

Este tutorial pressupõe que você esteja familiarizado com o C# e .NET, incluindo o Visual Studio ou a CLI do .NET Core.

## <a name="scenarios-for-pattern-matching"></a>Cenários para a correspondência de padrões

O desenvolvimento moderno geralmente inclui a integração de dados de várias fontes e a apresentação de informações e insights de dados em um único aplicativo coeso. Você e sua equipe não terão controle ou acesso a todos os tipos que representam os dados de entrada.

O design orientado a objeto clássico exigiria a criação de tipos em seu aplicativo que representassem cada tipo de dados das várias fontes de dados. O aplicativo, então, trabalharia com esses novos tipos, criaria hierarquias de herança, métodos virtuais e implementaria abstrações. Essas técnicas funcionam e, às vezes, são as melhores ferramentas. Outras vezes, é possível escrever menos código. Você pode escrever um código mais claro usando técnicas que separam os dados das operações que manipulam esses dados.

Neste tutorial, você vai criar e explorar um aplicativo que usa dados recebidos de várias fontes externas para um único cenário. Você verá como a **correspondência de padrões** fornece uma maneira eficiente para consumir e processar esses dados de maneiras que não eram parte do sistema original.

Imagine, por exemplo, uma área metropolitana principal que está implantando pedágios e preços diferenciados em horário de pico para gerenciar o tráfego. Você escreve um aplicativo que calcula o pedágio de um veículo com base em seu tipo. Posteriormente, as melhorias vão incorporar preços com base no número de ocupantes do veículo. Outros aprimoramentos vão adicionar o preço com base na hora e no dia da semana.

Com base nessa breve descrição, você pode ter elaborado rapidamente uma hierarquia de objetos para modelar esse sistema. No entanto, seus dados são provenientes de várias fontes, como outros sistemas de gerenciamento de registro do veículo. Esses sistemas fornecem classes diferentes para modelar aqueles dados, e você não tem um modelo de objeto único o qual seja possível usar. Neste tutorial, você usará essas classes simplificadas para criar o modelo para os dados do veículo, a partir desses sistemas externos, conforme mostrado no código a seguir:

[!code-csharp[ExternalSystems](~/samples/csharp/tutorials/patterns/start/toll-calculator/ExternalSystems.cs)]

Faça o download do código inicial no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/start) do GitHub. É possível ver que as classes de veículos são de sistemas diferentes, e estão em namespaces diferentes. Nenhuma base comum de classe, além da `System.Object` pode ser aproveitada.

## <a name="pattern-matching-designs"></a>Designs de correspondência de padrões

O cenário usado neste tutorial destaca os tipos de problemas que a correspondência de padrões pode resolver de forma adequada:

- Os objetos com os quais você precisa trabalhar não estão em uma hierarquia de objetos que corresponde aos seus objetivos. É possível que você esteja trabalhando com classes que fazem parte dos sistemas não relacionados.
- A funcionalidade que você está adicionando não faz parte da abstração central dessas classes. A tarifa paga por um veículo *muda* de acordo com diferentes tipos de veículos, mas o pedágio não é uma função principal do veículo.

Quando a *forma* dos dados e as *operações* nos dados não são descritas em conjunto, o recurso de correspondência padrões no C# facilita o trabalho.

## <a name="implement-the-basic-toll-calculations"></a>Implementar os cálculos básicos de pedágio

O cálculo mais básico do pedágio dependerá apenas do tipo do veículo:

- Um `Car` será R$2,00.
- Um `Taxi` será R$3,50.
- Um `Bus` será R$5,00.
- Um `DeliveryTruck` será R$10,00.

Crie uma nova classe `TollCalculator` e implemente a correspondência de padrões no tipo de veículo para obter a quantidade do pedágio. O código a seguir mostra a implementação inicial do `TollCalculator`.

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

O código anterior usa uma **expressão switch** (não igual a uma instrução [`switch`](../language-reference/keywords/switch.md)) que testa o **tipo de padrão**. A **expressão switch** inicia-se com a variável, `vehicle` no código anterior, seguida pela palavra-chave `switch`. Em seguida, estão os **braços switch** dentro de chaves. A expressão `switch` faz outros refinamentos na sintaxe que circunda a instrução `switch`. A palavra-chave `case` é omitida, e o resultado de cada braço é uma expressão. Os dois últimos braços apresentam um novo recurso de linguagem. O caso `{ }` corresponde a qualquer objeto não nulo que não correspondia a um braço anterior. Este braço captura qualquer tipo incorreto passado para esse método.  O caso `{ }` precisa seguir os casos para cada tipo de veículo. Se a ordem for revertida, o caso `{ }` terá precedência. Por fim, o padrão `null` detecta quando um `null` é passado para esse método. O padrão `null` pode ser o último, porque os outros padrões de tipo correspondem apenas a um objeto não nulo do tipo correto.

Você pode testar esse código usando o seguinte código no `Program.cs`:

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

Esse código está incluído no projeto inicial, mas está comentado. Remova os comentários para poder testar o que acabou de escrever.

Você está começando a ver como os padrões podem ajudar a criar algoritmos em que o código e os dados estão separados. A expressão `switch` testa o tipo e produz valores diferentes com base nos resultados. Mas isso é somente o começo.

## <a name="add-occupancy-pricing"></a>Adicionar preços de acordo com a ocupação do veículo

A autoridade de pedágio deseja incentivar que os veículos viagem com a capacidade máxima de pessoas. Eles decidiram cobrar valores mais altos quando os veículos tiverem poucos passageiros e oferecer redução da tarifa para veículos com a capacidade total ocupada:

- Os carros e táxis com nenhum passageiro pagam uma taxa adicional de R$ 0,50.
- Os carros e táxis com dois passageiros obtêm um desconto de R$ 0,50.
- Os carros e táxis com três ou mais passageiros obtêm um desconto de R$ 1,00.
- Os ônibus com menos de 50% da capacidade completa pagam uma taxa adicional de R$ 2,00.
- Os ônibus com 90% da capacidade de passageiros completa, ganham um desconto de R$ 1,00.

Essas regras podem ser implementadas usando o **padrão de propriedade** na mesma expressão switch. O padrão de propriedade examina as propriedades do objeto depois que o tipo foi determinado. O único caso de um `Car` se expande para quatro casos diferentes:

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

Os três primeiros casos testam o tipo como um `Car`, em seguida, verificam o valor da propriedade `Passengers`. Se ambos corresponderem, essa expressão é avaliada e retornada.

Você também expande os casos para táxis de maneira semelhante:

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

No exemplo anterior, a cláusula `when` foi omitida no caso final.

Em seguida, implemente as regras de ocupação expandindo os casos para os ônibus, conforme mostrado no exemplo a seguir:

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

A autoridade de pedágio não está preocupada com o número de passageiros nos caminhões de carga. Em vez disso, ela ajusta a quantidade de pedágios com base na classe de peso dos caminhões da seguinte maneira:

- Os caminhões mais de 5000 quilos pagam uma taxa adicional de R$ 5,00.
- Os caminhões leves abaixo de 3.000 lb recebem um desconto de US$ 2,00.

Essa regra é implementada com o código a seguir:

```csharp
vehicle switch
{
    // ...

    DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
    DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
    DeliveryTruck t => 10.00m,
};
```

O código anterior mostra a cláusula `when` de um braço switch. Você usa a cláusula `when` para testar as condições, com exceção da igualdade, em uma propriedade. Ao terminar, o método será muito semelhante ao seguinte:

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

Muitos desses braços switch são exemplos de **padrões recursivos**. Por exemplo, `Car { Passengers: 1}` mostra um padrão constante dentro de um padrão de propriedade.

É possível fazer esse código menos repetitivo, usando switches aninhados. O `Car` e `Taxi` têm quatro braços diferentes nos exemplos anteriores. Em ambos os casos, é possível criar um padrão de tipo que alimente um padrão de propriedade. Essa técnica é mostrada no código a seguir:

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

Na amostra anterior, o uso de uma expressão recursiva significa não repetir os braços `Car` e `Taxi` contendo braços filho que testam o valor da propriedade. Essa técnica não é usada para os braços `Bus` e `DeliveryTruck` porque esses estão testando intervalos da propriedade, e não valores discretos.

## <a name="add-peak-pricing"></a>Adicionar preço de horário de pico

Para um último recurso, a autoridade de pedágio quer adicionar um preço os horários de pico. Durante os horários de pico da manhã e do final da tarde, os pedágios serão dobrados. Essa regra afetará apenas o tráfego em uma direção: entrada para a cidade, no período da manhã, e de saída da cidade, no período da tarde. Em outros períodos durante o dia útil, os pedágios aumentam 50%. Nos períodos da noite e madrugada e de manhã cedo, as tarifas são 25% mais baratas. Durante o fim de semana, a taxa é normal, independentemente da hora.

Você usará a correspondência de padrões para esse recurso, mas poderá integrá-lo a outras técnicas. É possível criar uma única expressão de correspondência de padrões que leva em conta todas as combinações de direção, dia da semana e hora. O resultado seria uma expressão complicada. Seria difícil de ler e entender. O que dificulta garantir a exatidão. Em vez disso, combine esses métodos para criar uma tupla de valores que descreve de forma concisa todos os estados. Em seguida, use a correspondência de padrões para calcular um multiplicador para o pedágio. A tupla contém três condições distintas:

- O dia é um dia da semana ou do fim de semana.
- A faixa de tempo é quando o pedágio é coletado.
- A direção é para a cidade ou da cidade

A tabela a seguir mostra as combinações de valores de entrada e multiplicador de preços para os horários de pico:

| Day        | Time         | Direction | Premium |
| ---------- | ------------ | --------- |--------:|
| Dia útil    | horário de pico da manhã | entrada   | x 2,00  |
| Dia útil    | horário de pico da manhã | saída  | x 1,00  |
| Dia útil    | hora do dia      | entrada   | x 1,50  |
| Dia útil    | hora do dia      | saída  | x 1,50  |
| Dia útil    | horário de pico do fim da tarde | entrada   | x 1,00  |
| Dia útil    | horário de pico do fim da tarde | saída  | x 2,00  |
| Dia útil    | noite e madrugada    | entrada   | x 0,75  |
| Dia útil    | noite e madrugada    | saída  | x 0,75  |
| Fim de semana    | horário de pico da manhã | entrada   | x 1,00  |
| Fim de semana    | horário de pico da manhã | saída  | x 1,00  |
| Fim de semana    | hora do dia      | entrada   | x 1,00  |
| Fim de semana    | hora do dia      | saída  | x 1,00  |
| Fim de semana    | horário de pico do fim da tarde | entrada   | x 1,00  |
| Fim de semana    | horário de pico do fim da tarde | saída  | x 1,00  |
| Fim de semana    | noite e madrugada    | entrada   | x 1,00  |
| Fim de semana    | noite e madrugada    | saída  | x 1,00  |

Há 16 combinações diferentes das três variáveis. Ao combinar algumas das condições, você simplificará a expressão switch.

O sistema que coleta os pedágios usa uma estrutura <xref:System.DateTime> para a hora em que o pedágio foi cobrado. Construa métodos de membro que criam as variáveis da tabela anterior. A seguinte função usa como correspondência de padrões a expressão switch para expressar se um <xref:System.DateTime> representa um fim de semana ou um dia útil:

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

Esse método funciona, mas é redundante. Para simplificar, faça conforme mostrado no código a seguir:

[!code-csharp[IsWeekDay](~/samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#IsWeekDay)]

Depois, adicione uma função semelhante para categorizar o tempo nos blocos:

[!code-csharp[GetTimeBand](~/samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#GetTimeBand)]

O método anterior não usa a correspondência de padrões. Fica mais claro usando uma cascata familiar de instruções `if`. Adicione um `enum` privado para converter cada intervalo de tempo em um valor discreto.

Depois de criar esses métodos, é possível usar outra expressão `switch` com o **padrão de tupla** para calcular o preço premium. Você pode construir uma expressão `switch` com todos os 16 braços:

[!code-csharp[FullTuplePattern](~/samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#TuplePatternOne)]

O código acima funciona, mas pode ser simplificado. Todas as oito combinações para o fim de semana têm o mesmo pedágio. É possível substituir todas as oito pela seguinte linha:

```csharp
(false, _, _) => 1.0m,
```

Tanto o tráfego de entrada quanto o de saída têm o mesmo multiplicador durante o dia e a noite, nos dias úteis. Esses quatro braços switch podem ser substituídos por estas duas linhas:

```csharp
(true, TimeBand.Overnight, _) => 0.75m,
(true, TimeBand.Daytime, _)   => 1.5m,
```

O código deverá ser semelhante ao seguinte após essas duas alterações:

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

Por fim, você pode remover os dois horários de pico em que é pago o preço normal. Quando remover essas braços, substitua o `false` por um descarte (`_`) no braço switch final. O método concluído será o seguinte:

[!code-csharp[SimplifiedTuplePattern](../../../samples/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#FinalTuplePattern)]

Este exemplo destaca uma das vantagens da correspondência de padrões: os branches de padrões são avaliados na ordem. Se você os reorganizar para que um branch anterior trate um dos casos posteriores, o compilador emitirá um aviso sobre o código inacessível. Essas regras de linguagem tornam as simplificações anteriores mais fáceis com a certeza de que o código não foi alterado.

A correspondência de padrões torna alguns tipos de código mais legíveis e oferece uma alternativa às técnicas orientadas a objeto quando não é possível adicionar o código às classes. A nuvem está fazendo com que os dados e a funcionalidade existam separadamente. A *forma* dos dados e as *operações* nela não são necessariamente descritas juntas. Neste tutorial, você utilizou os dados existentes de maneiras completamente diferentes de sua função original. A correspondência de padrões proporcionou a capacidade de escrever a funcionalidade que substituiu esses tipos, ainda que não tenha sido possível estendê-los.

## <a name="next-steps"></a>Próximas etapas

Baixe o código concluído no repositório [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/finished) do GitHub. Explore os padrões por conta própria e adicione essa técnica em suas atividades regulares de codificação. Aprender essas técnicas lhe oferece outra maneira de abordar problemas e criar novas funcionalidades.
