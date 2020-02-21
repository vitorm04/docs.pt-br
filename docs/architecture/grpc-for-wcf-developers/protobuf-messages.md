---
title: Mensagens Protobuf-gRPC para desenvolvedores do WCF
description: Saiba como as mensagens Protobuf são definidas em IDL e geradas C#no.
ms.date: 09/09/2019
ms.openlocfilehash: c7375bafb7572b0eaa0458b0310a0114e3fd078c
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543034"
---
# <a name="protobuf-messages"></a><span data-ttu-id="fe5bb-103">Mensagens de Protobuf</span><span class="sxs-lookup"><span data-stu-id="fe5bb-103">Protobuf messages</span></span>

<span data-ttu-id="fe5bb-104">Esta seção aborda como declarar mensagens de buffer de protocolo (Protobuf) em arquivos `.proto`.</span><span class="sxs-lookup"><span data-stu-id="fe5bb-104">This section covers how to declare Protocol Buffer (Protobuf) messages in `.proto` files.</span></span> <span data-ttu-id="fe5bb-105">Ele explica os conceitos fundamentais de números e tipos de campo e examina o C# código que o compilador de `protoc` gera.</span><span class="sxs-lookup"><span data-stu-id="fe5bb-105">It explains the fundamental concepts of field numbers and types, and it looks at the C# code that the `protoc` compiler generates.</span></span> 

<span data-ttu-id="fe5bb-106">O restante do capítulo examinará mais detalhadamente como os diferentes tipos de dados são representados em Protobuf.</span><span class="sxs-lookup"><span data-stu-id="fe5bb-106">The rest of the chapter will look in more detail at how different types of data are represented in Protobuf.</span></span>

## <a name="declaring-a-message"></a><span data-ttu-id="fe5bb-107">Declarando uma mensagem</span><span class="sxs-lookup"><span data-stu-id="fe5bb-107">Declaring a message</span></span>

<span data-ttu-id="fe5bb-108">No Windows Communication Foundation (WCF), uma classe `Stock` para um aplicativo de comércio no mercado de ações pode ser definida como o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="fe5bb-108">In Windows Communication Foundation (WCF), a `Stock` class for a stock market trading application might be defined like the following example:</span></span>

```csharp
namespace TraderSys
{
    [DataContract]
    public class Stock
    {
        [DataMember]
        public int Id { get; set;}
        [DataMember]
        public string Symbol { get; set;}
        [DataMember]
        public string DisplayName { get; set;}
        [DataMember]
        public int MarketId { get; set; }
    }
}
```

<span data-ttu-id="fe5bb-109">Para implementar a classe equivalente em Protobuf, você deve declará-la no arquivo `.proto`.</span><span class="sxs-lookup"><span data-stu-id="fe5bb-109">To implement the equivalent class in Protobuf, you must declare it in the `.proto` file.</span></span> <span data-ttu-id="fe5bb-110">O compilador de `protoc` irá gerar a classe .NET como parte do processo de compilação.</span><span class="sxs-lookup"><span data-stu-id="fe5bb-110">The `protoc` compiler will then generate the .NET class as part of the build process.</span></span>

```protobuf
syntax "proto3";

option csharp_namespace = "TraderSys";

message Stock {

    int32 id = 1;
    string symbol = 2;
    string display_name = 3;
    int32 market_id = 4;

}  
```

<span data-ttu-id="fe5bb-111">A primeira linha declara a versão de sintaxe que está sendo usada.</span><span class="sxs-lookup"><span data-stu-id="fe5bb-111">The first line declares the syntax version being used.</span></span> <span data-ttu-id="fe5bb-112">A versão 3 da linguagem foi lançada em 2016.</span><span class="sxs-lookup"><span data-stu-id="fe5bb-112">Version 3 of the language was released in 2016.</span></span> <span data-ttu-id="fe5bb-113">É a versão que recomendamos para os serviços gRPCs.</span><span class="sxs-lookup"><span data-stu-id="fe5bb-113">It's the version that we recommend for gRPC services.</span></span>

<span data-ttu-id="fe5bb-114">A linha de `option csharp_namespace` especifica o namespace a ser usado para os C# tipos gerados.</span><span class="sxs-lookup"><span data-stu-id="fe5bb-114">The `option csharp_namespace` line specifies the namespace to be used for the generated C# types.</span></span> <span data-ttu-id="fe5bb-115">Essa opção será ignorada quando o arquivo de `.proto` for compilado para outros idiomas.</span><span class="sxs-lookup"><span data-stu-id="fe5bb-115">This option will be ignored when the `.proto` file is compiled for other languages.</span></span> <span data-ttu-id="fe5bb-116">Os arquivos Protobuf geralmente contêm opções específicas de idioma para vários idiomas.</span><span class="sxs-lookup"><span data-stu-id="fe5bb-116">Protobuf files often contain language-specific options for several languages.</span></span>

<span data-ttu-id="fe5bb-117">A definição da mensagem de `Stock` especifica quatro campos.</span><span class="sxs-lookup"><span data-stu-id="fe5bb-117">The `Stock` message definition specifies four fields.</span></span> <span data-ttu-id="fe5bb-118">Cada um tem um tipo, um nome e um número de campo.</span><span class="sxs-lookup"><span data-stu-id="fe5bb-118">Each has a type, a name, and a field number.</span></span>

## <a name="field-numbers"></a><span data-ttu-id="fe5bb-119">Números de campo</span><span class="sxs-lookup"><span data-stu-id="fe5bb-119">Field numbers</span></span>

<span data-ttu-id="fe5bb-120">Os números de campo são uma parte importante do Protobuf.</span><span class="sxs-lookup"><span data-stu-id="fe5bb-120">Field numbers are an important part of Protobuf.</span></span> <span data-ttu-id="fe5bb-121">Eles são usados para identificar campos nos dados binários codificados, o que significa que eles não podem mudar de versão para versão do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="fe5bb-121">They're used to identify fields in the binary encoded data, which means they can't change from version to version of your service.</span></span> <span data-ttu-id="fe5bb-122">A vantagem é que a compatibilidade com versões anteriores e a compatibilidade com o encaminhamento são possíveis.</span><span class="sxs-lookup"><span data-stu-id="fe5bb-122">The advantage is that backward compatibility and forward compatibility are possible.</span></span> <span data-ttu-id="fe5bb-123">Os clientes e serviços simplesmente ignorarão os números de campo que não conhecem, desde que a possibilidade de valores ausentes seja manipulada.</span><span class="sxs-lookup"><span data-stu-id="fe5bb-123">Clients and services will simply ignore field numbers that they don't know about, as long as the possibility of missing values is handled.</span></span>

<span data-ttu-id="fe5bb-124">No formato binário, o número do campo é combinado com um identificador de tipo.</span><span class="sxs-lookup"><span data-stu-id="fe5bb-124">In the binary format, the field number is combined with a type identifier.</span></span> <span data-ttu-id="fe5bb-125">Os números de campo de 1 a 15 podem ser codificados com seu tipo como um único byte.</span><span class="sxs-lookup"><span data-stu-id="fe5bb-125">Field numbers from 1 to 15 can be encoded with their type as a single byte.</span></span> <span data-ttu-id="fe5bb-126">Os números de 16 a 2.047 levam 2 bytes.</span><span class="sxs-lookup"><span data-stu-id="fe5bb-126">Numbers from 16 to 2,047 take 2 bytes.</span></span> <span data-ttu-id="fe5bb-127">Você pode ficar mais alto se precisar de mais de 2.047 campos em uma mensagem por qualquer motivo.</span><span class="sxs-lookup"><span data-stu-id="fe5bb-127">You can go higher if you need more than 2,047 fields on a message for any reason.</span></span> <span data-ttu-id="fe5bb-128">Os identificadores de byte único para os números de campo de 1 a 15 oferecem melhor desempenho, portanto, você deve usá-los para os campos mais básicos e usados com frequência.</span><span class="sxs-lookup"><span data-stu-id="fe5bb-128">The single byte identifiers for field numbers 1 to 15 offer better performance, so you should use them for the most basic, frequently used fields.</span></span>

## <a name="types"></a><span data-ttu-id="fe5bb-129">Tipos</span><span class="sxs-lookup"><span data-stu-id="fe5bb-129">Types</span></span>

<span data-ttu-id="fe5bb-130">As declarações de tipo estão usando os tipos de dados escalares nativos do Protobuf, que são abordados em mais detalhes na [próxima seção](protobuf-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="fe5bb-130">The type declarations are using Protobuf's native scalar data types, which are discussed in more detail in [the next section](protobuf-data-types.md).</span></span> <span data-ttu-id="fe5bb-131">O restante deste capítulo abordará os tipos internos do Protobuf e mostrará como eles se relacionam com os tipos .NET comuns.</span><span class="sxs-lookup"><span data-stu-id="fe5bb-131">The rest of this chapter will cover Protobuf's built-in types and show how they relate to common .NET types.</span></span>

> [!NOTE]
> <span data-ttu-id="fe5bb-132">O Protobuf não dá suporte nativo a um tipo de `decimal`, portanto, `double` é usado em vez disso.</span><span class="sxs-lookup"><span data-stu-id="fe5bb-132">Protobuf doesn't natively support a `decimal` type, so `double` is used instead.</span></span> <span data-ttu-id="fe5bb-133">Para aplicativos que exigem precisão decimal completa, consulte a [seção sobre decimais](protobuf-data-types.md#decimals) na próxima parte deste capítulo.</span><span class="sxs-lookup"><span data-stu-id="fe5bb-133">For applications that require full decimal precision, refer to the [section on decimals](protobuf-data-types.md#decimals) in the next part of this chapter.</span></span>

## <a name="the-generated-code"></a><span data-ttu-id="fe5bb-134">O código gerado</span><span class="sxs-lookup"><span data-stu-id="fe5bb-134">The generated code</span></span>

<span data-ttu-id="fe5bb-135">Quando você cria seu aplicativo, o Protobuf cria classes para cada uma de suas mensagens, mapeando seus C# tipos nativos para tipos.</span><span class="sxs-lookup"><span data-stu-id="fe5bb-135">When you build your application, Protobuf creates classes for each of your messages, mapping its native types to C# types.</span></span> <span data-ttu-id="fe5bb-136">O tipo de `Stock` gerado teria a seguinte assinatura:</span><span class="sxs-lookup"><span data-stu-id="fe5bb-136">The generated `Stock` type would have the following signature:</span></span>

```csharp
public class Stock
{
    public int Id { get; set; }
    public string Symbol { get; set; }
    public string DisplayName { get; set; }
    public int MarketId { get; set; }
}
```

<span data-ttu-id="fe5bb-137">O código real gerado é muito mais complicado do que isso.</span><span class="sxs-lookup"><span data-stu-id="fe5bb-137">The actual code that's generated is far more complicated than this.</span></span> <span data-ttu-id="fe5bb-138">O motivo é que cada classe contém todo o código necessário para serializar e desserializar para o formato de fio binário.</span><span class="sxs-lookup"><span data-stu-id="fe5bb-138">The reason is that each class contains all the code necessary to serialize and deserialize itself to the binary wire format.</span></span>

### <a name="property-names"></a><span data-ttu-id="fe5bb-139">Nomes de propriedade</span><span class="sxs-lookup"><span data-stu-id="fe5bb-139">Property names</span></span>

<span data-ttu-id="fe5bb-140">Observe que o compilador Protobuf aplicou `PascalCase` aos nomes de propriedade, embora eles fossem `snake_case` no arquivo `.proto`.</span><span class="sxs-lookup"><span data-stu-id="fe5bb-140">Note that the Protobuf compiler applied `PascalCase` to the property names, although they were `snake_case` in the `.proto` file.</span></span> <span data-ttu-id="fe5bb-141">O [Guia de estilo Protobuf](https://developers.google.com/protocol-buffers/docs/style) recomenda o uso de `snake_case` em suas definições de mensagem para que a geração de código para outras plataformas produza o caso esperado para suas convenções.</span><span class="sxs-lookup"><span data-stu-id="fe5bb-141">The [Protobuf style guide](https://developers.google.com/protocol-buffers/docs/style) recommends using `snake_case` in your message definitions so that the code generation for other platforms produces the expected case for their conventions.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="fe5bb-142">[Anterior](protocol-buffers.md)
>[Próximo](protobuf-data-types.md)</span><span class="sxs-lookup"><span data-stu-id="fe5bb-142">[Previous](protocol-buffers.md)
[Next](protobuf-data-types.md)</span></span>
