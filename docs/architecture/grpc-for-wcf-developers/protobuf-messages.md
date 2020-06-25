---
title: Mensagens Protobuf-gRPC para desenvolvedores do WCF
description: Saiba como as mensagens Protobuf são definidas em IDL e geradas em C#.
ms.date: 09/09/2019
ms.openlocfilehash: 6fc7b9c34810abaa8d674af56d1517a5cf87521b
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325032"
---
# <a name="protobuf-messages"></a><span data-ttu-id="26007-103">Mensagens de Protobuf</span><span class="sxs-lookup"><span data-stu-id="26007-103">Protobuf messages</span></span>

<span data-ttu-id="26007-104">Esta seção aborda como declarar mensagens de buffer de protocolo (Protobuf) em `.proto` arquivos.</span><span class="sxs-lookup"><span data-stu-id="26007-104">This section covers how to declare Protocol Buffer (Protobuf) messages in `.proto` files.</span></span> <span data-ttu-id="26007-105">Ele explica os conceitos fundamentais de números e tipos de campo e examina o código C# que o `protoc` compilador gera.</span><span class="sxs-lookup"><span data-stu-id="26007-105">It explains the fundamental concepts of field numbers and types, and it looks at the C# code that the `protoc` compiler generates.</span></span>

<span data-ttu-id="26007-106">O restante do capítulo examinará mais detalhadamente como os diferentes tipos de dados são representados em Protobuf.</span><span class="sxs-lookup"><span data-stu-id="26007-106">The rest of the chapter will look in more detail at how different types of data are represented in Protobuf.</span></span>

## <a name="declaring-a-message"></a><span data-ttu-id="26007-107">Declarando uma mensagem</span><span class="sxs-lookup"><span data-stu-id="26007-107">Declaring a message</span></span>

<span data-ttu-id="26007-108">No Windows Communication Foundation (WCF), uma `Stock` classe para um aplicativo de comércio no mercado de ações pode ser definida como o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="26007-108">In Windows Communication Foundation (WCF), a `Stock` class for a stock market trading application might be defined like the following example:</span></span>

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

<span data-ttu-id="26007-109">Para implementar a classe equivalente em Protobuf, você deve declará-la no `.proto` arquivo.</span><span class="sxs-lookup"><span data-stu-id="26007-109">To implement the equivalent class in Protobuf, you must declare it in the `.proto` file.</span></span> <span data-ttu-id="26007-110">O `protoc` compilador então irá gerar a classe .net como parte do processo de compilação.</span><span class="sxs-lookup"><span data-stu-id="26007-110">The `protoc` compiler will then generate the .NET class as part of the build process.</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys";

message Stock {

    int32 id = 1;
    string symbol = 2;
    string display_name = 3;
    int32 market_id = 4;

}  
```

<span data-ttu-id="26007-111">A primeira linha declara a versão de sintaxe que está sendo usada.</span><span class="sxs-lookup"><span data-stu-id="26007-111">The first line declares the syntax version being used.</span></span> <span data-ttu-id="26007-112">A versão 3 da linguagem foi lançada em 2016.</span><span class="sxs-lookup"><span data-stu-id="26007-112">Version 3 of the language was released in 2016.</span></span> <span data-ttu-id="26007-113">É a versão que recomendamos para os serviços gRPCs.</span><span class="sxs-lookup"><span data-stu-id="26007-113">It's the version that we recommend for gRPC services.</span></span>

<span data-ttu-id="26007-114">A `option csharp_namespace` linha especifica o namespace a ser usado para os tipos C# gerados.</span><span class="sxs-lookup"><span data-stu-id="26007-114">The `option csharp_namespace` line specifies the namespace to be used for the generated C# types.</span></span> <span data-ttu-id="26007-115">Essa opção será ignorada quando o `.proto` arquivo for compilado para outros idiomas.</span><span class="sxs-lookup"><span data-stu-id="26007-115">This option will be ignored when the `.proto` file is compiled for other languages.</span></span> <span data-ttu-id="26007-116">Os arquivos Protobuf geralmente contêm opções específicas de idioma para vários idiomas.</span><span class="sxs-lookup"><span data-stu-id="26007-116">Protobuf files often contain language-specific options for several languages.</span></span>

<span data-ttu-id="26007-117">A `Stock` definição da mensagem Especifica quatro campos.</span><span class="sxs-lookup"><span data-stu-id="26007-117">The `Stock` message definition specifies four fields.</span></span> <span data-ttu-id="26007-118">Cada um tem um tipo, um nome e um número de campo.</span><span class="sxs-lookup"><span data-stu-id="26007-118">Each has a type, a name, and a field number.</span></span>

## <a name="field-numbers"></a><span data-ttu-id="26007-119">Números de campo</span><span class="sxs-lookup"><span data-stu-id="26007-119">Field numbers</span></span>

<span data-ttu-id="26007-120">Os números de campo são uma parte importante do Protobuf.</span><span class="sxs-lookup"><span data-stu-id="26007-120">Field numbers are an important part of Protobuf.</span></span> <span data-ttu-id="26007-121">Eles são usados para identificar campos nos dados binários codificados, o que significa que eles não podem mudar de versão para versão do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="26007-121">They're used to identify fields in the binary encoded data, which means they can't change from version to version of your service.</span></span> <span data-ttu-id="26007-122">A vantagem é que a compatibilidade com versões anteriores e a compatibilidade com o encaminhamento são possíveis.</span><span class="sxs-lookup"><span data-stu-id="26007-122">The advantage is that backward compatibility and forward compatibility are possible.</span></span> <span data-ttu-id="26007-123">Os clientes e serviços simplesmente ignorarão os números de campo que não conhecem, desde que a possibilidade de valores ausentes seja manipulada.</span><span class="sxs-lookup"><span data-stu-id="26007-123">Clients and services will simply ignore field numbers that they don't know about, as long as the possibility of missing values is handled.</span></span>

<span data-ttu-id="26007-124">No formato binário, o número do campo é combinado com um identificador de tipo.</span><span class="sxs-lookup"><span data-stu-id="26007-124">In the binary format, the field number is combined with a type identifier.</span></span> <span data-ttu-id="26007-125">Os números de campo de 1 a 15 podem ser codificados com seu tipo como um único byte.</span><span class="sxs-lookup"><span data-stu-id="26007-125">Field numbers from 1 to 15 can be encoded with their type as a single byte.</span></span> <span data-ttu-id="26007-126">Os números de 16 a 2.047 levam 2 bytes.</span><span class="sxs-lookup"><span data-stu-id="26007-126">Numbers from 16 to 2,047 take 2 bytes.</span></span> <span data-ttu-id="26007-127">Você pode ficar mais alto se precisar de mais de 2.047 campos em uma mensagem por qualquer motivo.</span><span class="sxs-lookup"><span data-stu-id="26007-127">You can go higher if you need more than 2,047 fields on a message for any reason.</span></span> <span data-ttu-id="26007-128">Os identificadores de byte único para os números de campo de 1 a 15 oferecem melhor desempenho, portanto, você deve usá-los para os campos mais básicos e usados com frequência.</span><span class="sxs-lookup"><span data-stu-id="26007-128">The single byte identifiers for field numbers 1 to 15 offer better performance, so you should use them for the most basic, frequently used fields.</span></span>

## <a name="types"></a><span data-ttu-id="26007-129">Tipos</span><span class="sxs-lookup"><span data-stu-id="26007-129">Types</span></span>

<span data-ttu-id="26007-130">As declarações de tipo estão usando os tipos de dados escalares nativos do Protobuf, que são abordados em mais detalhes na [próxima seção](protobuf-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="26007-130">The type declarations are using Protobuf's native scalar data types, which are discussed in more detail in [the next section](protobuf-data-types.md).</span></span> <span data-ttu-id="26007-131">O restante deste capítulo abordará os tipos internos do Protobuf e mostrará como eles se relacionam com os tipos .NET comuns.</span><span class="sxs-lookup"><span data-stu-id="26007-131">The rest of this chapter will cover Protobuf's built-in types and show how they relate to common .NET types.</span></span>

> [!NOTE]
> <span data-ttu-id="26007-132">O Protobuf não dá suporte nativo a um `decimal` tipo, portanto, `double` é usado em vez disso.</span><span class="sxs-lookup"><span data-stu-id="26007-132">Protobuf doesn't natively support a `decimal` type, so `double` is used instead.</span></span> <span data-ttu-id="26007-133">Para aplicativos que exigem precisão decimal completa, consulte a [seção sobre decimais](protobuf-data-types.md#decimals) na próxima parte deste capítulo.</span><span class="sxs-lookup"><span data-stu-id="26007-133">For applications that require full decimal precision, refer to the [section on decimals](protobuf-data-types.md#decimals) in the next part of this chapter.</span></span>

## <a name="the-generated-code"></a><span data-ttu-id="26007-134">O código gerado</span><span class="sxs-lookup"><span data-stu-id="26007-134">The generated code</span></span>

<span data-ttu-id="26007-135">Quando você cria seu aplicativo, o Protobuf cria classes para cada uma de suas mensagens, mapeando seus tipos nativos para tipos C#.</span><span class="sxs-lookup"><span data-stu-id="26007-135">When you build your application, Protobuf creates classes for each of your messages, mapping its native types to C# types.</span></span> <span data-ttu-id="26007-136">O `Stock` tipo gerado teria a seguinte assinatura:</span><span class="sxs-lookup"><span data-stu-id="26007-136">The generated `Stock` type would have the following signature:</span></span>

```csharp
public class Stock
{
    public int Id { get; set; }
    public string Symbol { get; set; }
    public string DisplayName { get; set; }
    public int MarketId { get; set; }
}
```

<span data-ttu-id="26007-137">O código real gerado é muito mais complicado do que isso.</span><span class="sxs-lookup"><span data-stu-id="26007-137">The actual code that's generated is far more complicated than this.</span></span> <span data-ttu-id="26007-138">O motivo é que cada classe contém todo o código necessário para serializar e desserializar para o formato de fio binário.</span><span class="sxs-lookup"><span data-stu-id="26007-138">The reason is that each class contains all the code necessary to serialize and deserialize itself to the binary wire format.</span></span>

### <a name="property-names"></a><span data-ttu-id="26007-139">Nomes de propriedade</span><span class="sxs-lookup"><span data-stu-id="26007-139">Property names</span></span>

<span data-ttu-id="26007-140">Observe que o compilador Protobuf aplicado `PascalCase` aos nomes de propriedade, embora eles estivessem `snake_case` no `.proto` arquivo.</span><span class="sxs-lookup"><span data-stu-id="26007-140">Note that the Protobuf compiler applied `PascalCase` to the property names, although they were `snake_case` in the `.proto` file.</span></span> <span data-ttu-id="26007-141">O [Guia de estilo Protobuf](https://developers.google.com/protocol-buffers/docs/style) recomenda o uso `snake_case` em suas definições de mensagem para que a geração de código para outras plataformas produza o caso esperado para suas convenções.</span><span class="sxs-lookup"><span data-stu-id="26007-141">The [Protobuf style guide](https://developers.google.com/protocol-buffers/docs/style) recommends using `snake_case` in your message definitions so that the code generation for other platforms produces the expected case for their conventions.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="26007-142">[Anterior](protocol-buffers.md) 
> [Avançar](protobuf-data-types.md)</span><span class="sxs-lookup"><span data-stu-id="26007-142">[Previous](protocol-buffers.md)
[Next](protobuf-data-types.md)</span></span>
