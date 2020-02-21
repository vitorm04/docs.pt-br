---
title: Protobuf any e oneof Fields for Variant Types-gRPC for WCF Developers
description: Saiba como usar o tipo any e a palavra-chave oneof para representar tipos de objeto Variant em mensagens.
ms.date: 09/09/2019
ms.openlocfilehash: 6fe7acbd1ec35289f7ad6f3acee8509ab934619d
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543190"
---
# <a name="protobuf-any-and-oneof-fields-for-variant-types"></a><span data-ttu-id="c1304-103">Protobuf os campos any e oneof para tipos Variant</span><span class="sxs-lookup"><span data-stu-id="c1304-103">Protobuf Any and Oneof fields for variant types</span></span>

<span data-ttu-id="c1304-104">A manipulação de tipos de propriedade dinâmica (ou seja, propriedades do tipo `object`) no Windows Communication Foundation (WCF) é complicada.</span><span class="sxs-lookup"><span data-stu-id="c1304-104">Handling dynamic property types (that is, properties of type `object`) in Windows Communication Foundation (WCF) is complicated.</span></span> <span data-ttu-id="c1304-105">Por exemplo, você deve especificar serializadores e fornecer atributos [KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) .</span><span class="sxs-lookup"><span data-stu-id="c1304-105">For example, you must specify serializers and provide [KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) attributes.</span></span>

<span data-ttu-id="c1304-106">O buffer de protocolo (Protobuf) fornece duas opções mais simples para lidar com valores que podem ser de mais de um tipo.</span><span class="sxs-lookup"><span data-stu-id="c1304-106">Protocol Buffer (Protobuf) provides two simpler options for dealing with values that might be of more than one type.</span></span> <span data-ttu-id="c1304-107">O tipo de `Any` pode representar qualquer tipo de mensagem Protobuf conhecido.</span><span class="sxs-lookup"><span data-stu-id="c1304-107">The `Any` type can represent any known Protobuf message type.</span></span> <span data-ttu-id="c1304-108">E você pode usar a palavra-chave `oneof` para especificar que apenas um de vários campos pode ser definido em qualquer mensagem.</span><span class="sxs-lookup"><span data-stu-id="c1304-108">And you can use the `oneof` keyword to specify that only one of a range of fields can be set in any message.</span></span>

## <a name="any"></a><span data-ttu-id="c1304-109">Qualquer</span><span class="sxs-lookup"><span data-stu-id="c1304-109">Any</span></span>

<span data-ttu-id="c1304-110">`Any` é um dos "tipos bem conhecidos" de Protobuf: uma coleção de tipos de mensagens úteis e reutilizáveis com implementações em todos os idiomas com suporte.</span><span class="sxs-lookup"><span data-stu-id="c1304-110">`Any` is one of Protobuf's "well-known types": a collection of useful, reusable message types with implementations in all supported languages.</span></span> <span data-ttu-id="c1304-111">Para usar o tipo de `Any`, você deve importar a definição de `google/protobuf/any.proto`.</span><span class="sxs-lookup"><span data-stu-id="c1304-111">To use the `Any` type, you must import the `google/protobuf/any.proto` definition.</span></span>

```protobuf
syntax "proto3"

import "google/protobuf/any.proto"

message Stock {
    // Stock-specific data
}

message Currency {
    // Currency-specific data
}

message ChangeNotification {
    int32 id = 1;
    google.protobuf.Any instrument = 2;
}
```

<span data-ttu-id="c1304-112">No C# código, a classe `Any` fornece métodos para definir o campo, extrair a mensagem e verificar o tipo.</span><span class="sxs-lookup"><span data-stu-id="c1304-112">In the C# code, the `Any` class provides methods for setting the field, extracting the message, and checking the type.</span></span>

```csharp
public void FormatChangeNotification(ChangeNotification change)
{
    if (change.Instrument.Is(Stock.Descriptor))
    {
        FormatStock(change.Instrument.Unpack<Stock>());
    }
    else if (change.Instrument.Is(Currency.Descriptor))
    {
        FormatCurrency(change.Instrument.Unpack<Currency>());
    }
    else
    {
        throw new ArgumentException("Unknown instrument type");
    }
}
```

<span data-ttu-id="c1304-113">O código de reflexão interno de Protobuf usa o campo estático `Descriptor` em cada tipo gerado para resolver `Any` tipos de campo.</span><span class="sxs-lookup"><span data-stu-id="c1304-113">Protobuf's internal reflection code uses the `Descriptor` static field on each generated type to resolve `Any` field types.</span></span> <span data-ttu-id="c1304-114">Também há um método `TryUnpack<T>`, mas isso cria uma instância não inicializada de `T` mesmo quando ela falha.</span><span class="sxs-lookup"><span data-stu-id="c1304-114">There's also a `TryUnpack<T>` method, but that creates an uninitialized instance of `T` even when it fails.</span></span> <span data-ttu-id="c1304-115">É melhor usar o método `Is`, conforme mostrado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="c1304-115">It's better to use the `Is` method as shown earlier.</span></span>

## <a name="oneof"></a><span data-ttu-id="c1304-116">Oneof</span><span class="sxs-lookup"><span data-stu-id="c1304-116">Oneof</span></span>

<span data-ttu-id="c1304-117">Os campos oneof são um recurso de linguagem: o compilador manipula a palavra-chave `oneof` quando gera a classe de mensagem.</span><span class="sxs-lookup"><span data-stu-id="c1304-117">Oneof fields are a language feature: the compiler handles the `oneof` keyword when it generates the message class.</span></span> <span data-ttu-id="c1304-118">Usar `oneof` para especificar a mensagem de `ChangeNotification` pode ser assim:</span><span class="sxs-lookup"><span data-stu-id="c1304-118">Using `oneof` to specify the `ChangeNotification` message might look like this:</span></span>

```protobuf
message Stock {
    // Stock-specific data
}

message Currency {
    // Currency-specific data
}

message ChangeNotification {
  int32 id = 1;
  oneof instrument {
    Stock stock = 2;
    Currency currency = 3;
  }
}
```

<span data-ttu-id="c1304-119">Os campos dentro do conjunto de `oneof` devem ter números de campo exclusivos na declaração de mensagem geral.</span><span class="sxs-lookup"><span data-stu-id="c1304-119">Fields within the `oneof` set must have unique field numbers in the overall message declaration.</span></span>

<span data-ttu-id="c1304-120">Quando você usa `oneof`, o código C# gerado inclui uma enumeração que especifica quais dos campos foram definidos.</span><span class="sxs-lookup"><span data-stu-id="c1304-120">When you use `oneof`, the generated C# code includes an enum that specifies which of the fields has been set.</span></span> <span data-ttu-id="c1304-121">Você pode testar a enumeração para localizar qual campo está definido.</span><span class="sxs-lookup"><span data-stu-id="c1304-121">You can test the enum to find which field is set.</span></span> <span data-ttu-id="c1304-122">Os campos que não estão definidos retornam `null` ou o valor padrão, em vez de gerar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="c1304-122">Fields that aren't set return `null` or the default value, rather than throwing an exception.</span></span>

```csharp
public void FormatChangeNotification(ChangeNotification change)
{
    switch (change.InstrumentCase)
    {
        case ChangeNotification.InstrumentOneofCase.None:
            return;
        case ChangeNotification.InstrumentOneofCase.Stock:
            FormatStock(change.Stock);
            break;
        case ChangeNotification.InstrumentOneofCase.Currency:
            FormatCurrency(change.Currency);
            break;
        default:
            throw new ArgumentException("Unknown instrument type");
    }
}
```

<span data-ttu-id="c1304-123">Definir qualquer campo que faça parte de um conjunto de `oneof` limpará automaticamente todos os outros campos no conjunto.</span><span class="sxs-lookup"><span data-stu-id="c1304-123">Setting any field that's part of a `oneof` set will automatically clear any other fields in the set.</span></span> <span data-ttu-id="c1304-124">Você não pode usar `repeated` com `oneof`.</span><span class="sxs-lookup"><span data-stu-id="c1304-124">You can't use `repeated` with `oneof`.</span></span> <span data-ttu-id="c1304-125">Em vez disso, você pode criar uma mensagem aninhada com o campo repetido ou o `oneof` definido como contornar essa limitação.</span><span class="sxs-lookup"><span data-stu-id="c1304-125">Instead, you can create a nested message with either the repeated field or the `oneof` set to work around this limitation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c1304-126">[Anterior](protobuf-reserved.md)
>[Próximo](protobuf-enums.md)</span><span class="sxs-lookup"><span data-stu-id="c1304-126">[Previous](protobuf-reserved.md)
[Next](protobuf-enums.md)</span></span>
