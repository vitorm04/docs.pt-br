---
title: Protobuf any e oneof Fields for Variant Types-gRPC for WCF Developers
description: Saiba como usar o tipo any e a palavra-chave oneof para representar tipos de objeto Variant em mensagens.
ms.date: 09/09/2019
ms.openlocfilehash: af3ba22c238aa80a8c6119f62d5d8914770cad68
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971612"
---
# <a name="protobuf-any-and-oneof-fields-for-variant-types"></a><span data-ttu-id="56155-103">Protobuf os campos any e oneof para tipos Variant</span><span class="sxs-lookup"><span data-stu-id="56155-103">Protobuf Any and Oneof fields for variant types</span></span>

<span data-ttu-id="56155-104">A manipulação de tipos de propriedade dinâmica (ou seja, propriedades do tipo `object`) no WCF é complicada.</span><span class="sxs-lookup"><span data-stu-id="56155-104">Handling dynamic property types (that is, properties of type `object`) in WCF is complicated.</span></span> <span data-ttu-id="56155-105">Os serializadores devem ser especificados, os atributos [KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) devem ser fornecidos e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="56155-105">Serializers must be specified, [KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) attributes must be provided, and so on.</span></span>

<span data-ttu-id="56155-106">O Protobuf fornece duas opções mais simples para lidar com valores que podem ser de mais de um tipo.</span><span class="sxs-lookup"><span data-stu-id="56155-106">Protobuf provides two simpler options for dealing with values that may be of more than one type.</span></span> <span data-ttu-id="56155-107">O tipo de `Any` pode representar qualquer tipo de mensagem Protobuf conhecido, enquanto a palavra-chave `oneof` permite que você especifique que apenas um de vários campos pode ser definido em qualquer determinada mensagem.</span><span class="sxs-lookup"><span data-stu-id="56155-107">The `Any` type can represent any known Protobuf message type, while the `oneof` keyword allows you to specify that only one of a range of fields can be set in any given message.</span></span>

## <a name="any"></a><span data-ttu-id="56155-108">Qualquer</span><span class="sxs-lookup"><span data-stu-id="56155-108">Any</span></span>

<span data-ttu-id="56155-109">`Any` é um dos "tipos bem conhecidos" de Protobuf: uma coleção de tipos de mensagens úteis e reutilizáveis com implementações em todos os idiomas com suporte.</span><span class="sxs-lookup"><span data-stu-id="56155-109">`Any` is one of Protobuf's "well-known types": a collection of useful, reusable message types with implementations in all supported languages.</span></span> <span data-ttu-id="56155-110">Para usar o tipo de `Any`, você deve importar a definição de `google/protobuf/any.proto`.</span><span class="sxs-lookup"><span data-stu-id="56155-110">To use the `Any` type, you must import the `google/protobuf/any.proto` definition.</span></span>

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

<span data-ttu-id="56155-111">No C# código, a classe `Any` fornece métodos para definir o campo, extrair a mensagem e verificar o tipo.</span><span class="sxs-lookup"><span data-stu-id="56155-111">In the C# code, the `Any` class provides methods for setting the field, extracting the message, and checking the type.</span></span>

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

<span data-ttu-id="56155-112">O `Descriptor` campo estático em cada tipo gerado é usado pelo código de reflexão interno do Protobuf para resolver `Any` tipos de campo.</span><span class="sxs-lookup"><span data-stu-id="56155-112">The `Descriptor` static field on each generated type is used by Protobuf's internal reflection code to resolve `Any` field types.</span></span> <span data-ttu-id="56155-113">Há também um método `TryUnpack<T>`, mas isso cria uma instância não inicializada de `T` mesmo quando ela falha, portanto, é melhor usar o método `Is`, conforme mostrado acima.</span><span class="sxs-lookup"><span data-stu-id="56155-113">There's also a `TryUnpack<T>` method, but that creates an uninitialized instance of `T` even when it fails, so it's better to use the `Is` method as shown above.</span></span>

## <a name="oneof"></a><span data-ttu-id="56155-114">Oneof</span><span class="sxs-lookup"><span data-stu-id="56155-114">Oneof</span></span>

<span data-ttu-id="56155-115">Os campos oneof são um recurso de linguagem: a palavra-chave `oneof` é manipulada pelo compilador quando ele gera a classe Message.</span><span class="sxs-lookup"><span data-stu-id="56155-115">Oneof fields are a language feature: the `oneof` keyword is handled by the compiler when it generates the message class.</span></span> <span data-ttu-id="56155-116">Usar `oneof` para especificar a mensagem de `ChangeNotification` pode ser assim:</span><span class="sxs-lookup"><span data-stu-id="56155-116">Using `oneof` to specify the `ChangeNotification` message might look like this:</span></span>

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

<span data-ttu-id="56155-117">Os campos dentro do conjunto de `oneof` devem ter números de campo exclusivos dentro da declaração de mensagem geral.</span><span class="sxs-lookup"><span data-stu-id="56155-117">Fields within the `oneof` set must have unique field numbers within the overall message declaration.</span></span>

<span data-ttu-id="56155-118">Quando você usa `oneof`, o código C# gerado inclui uma enumeração que especifica quais dos campos foram definidos.</span><span class="sxs-lookup"><span data-stu-id="56155-118">When you use `oneof`, the generated C# code includes an enum that specifies which of the fields has been set.</span></span> <span data-ttu-id="56155-119">Você pode testar a enumeração para localizar qual campo está definido.</span><span class="sxs-lookup"><span data-stu-id="56155-119">You can test the enum to find which field is set.</span></span> <span data-ttu-id="56155-120">Os campos que não estão definidos retornam `null` ou o valor padrão, em vez de gerar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="56155-120">Fields that aren't set return `null` or the default value, rather than throwing an exception.</span></span>

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

<span data-ttu-id="56155-121">Definir qualquer campo que faça parte de um conjunto de `oneof` limpará automaticamente todos os outros campos no conjunto.</span><span class="sxs-lookup"><span data-stu-id="56155-121">Setting any field that is part of a `oneof` set will automatically clear any other fields in the set.</span></span> <span data-ttu-id="56155-122">Você não pode usar `repeated` com `oneof`.</span><span class="sxs-lookup"><span data-stu-id="56155-122">You can't use `repeated` with `oneof`.</span></span> <span data-ttu-id="56155-123">Em vez disso, você pode criar uma mensagem aninhada com o campo repetido ou o `oneof` definido como contornar essa limitação.</span><span class="sxs-lookup"><span data-stu-id="56155-123">Instead, you can create a nested message with either the repeated field or the `oneof` set to work around this limitation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="56155-124">[Anterior](protobuf-reserved.md)
>[Próximo](protobuf-enums.md)</span><span class="sxs-lookup"><span data-stu-id="56155-124">[Previous](protobuf-reserved.md)
[Next](protobuf-enums.md)</span></span>
