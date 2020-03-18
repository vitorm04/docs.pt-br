---
title: Mensagens protobuf - gRPC para desenvolvedores WCF
description: Saiba como as mensagens Protobuf são definidas no IDL e geradas em C#.
ms.date: 09/09/2019
ms.openlocfilehash: 5b3d4383de39a3785ef804fec21939a740f54669
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147978"
---
# <a name="protobuf-messages"></a><span data-ttu-id="ef5bb-103">Mensagens de Protobuf</span><span class="sxs-lookup"><span data-stu-id="ef5bb-103">Protobuf messages</span></span>

<span data-ttu-id="ef5bb-104">Esta seção abrange como declarar mensagens de Buffer `.proto` de Protocolo (Protobuf) em arquivos.</span><span class="sxs-lookup"><span data-stu-id="ef5bb-104">This section covers how to declare Protocol Buffer (Protobuf) messages in `.proto` files.</span></span> <span data-ttu-id="ef5bb-105">Ele explica os conceitos fundamentais de números de campo e `protoc` tipos, e olha para o código C# que o compilador gera.</span><span class="sxs-lookup"><span data-stu-id="ef5bb-105">It explains the fundamental concepts of field numbers and types, and it looks at the C# code that the `protoc` compiler generates.</span></span>

<span data-ttu-id="ef5bb-106">O resto do capítulo analisará com mais detalhes como diferentes tipos de dados são representados no Protobuf.</span><span class="sxs-lookup"><span data-stu-id="ef5bb-106">The rest of the chapter will look in more detail at how different types of data are represented in Protobuf.</span></span>

## <a name="declaring-a-message"></a><span data-ttu-id="ef5bb-107">Declarando uma mensagem</span><span class="sxs-lookup"><span data-stu-id="ef5bb-107">Declaring a message</span></span>

<span data-ttu-id="ef5bb-108">No Windows Communication Foundation (WCF), uma `Stock` classe para um aplicativo de negociação no mercado de ações pode ser definida como o seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="ef5bb-108">In Windows Communication Foundation (WCF), a `Stock` class for a stock market trading application might be defined like the following example:</span></span>

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

<span data-ttu-id="ef5bb-109">Para implementar a classe equivalente em Protobuf, `.proto` você deve declará-la no arquivo.</span><span class="sxs-lookup"><span data-stu-id="ef5bb-109">To implement the equivalent class in Protobuf, you must declare it in the `.proto` file.</span></span> <span data-ttu-id="ef5bb-110">O `protoc` compilador gerará a classe .NET como parte do processo de compilação.</span><span class="sxs-lookup"><span data-stu-id="ef5bb-110">The `protoc` compiler will then generate the .NET class as part of the build process.</span></span>

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

<span data-ttu-id="ef5bb-111">A primeira linha declara a versão de sintaxe sendo usada.</span><span class="sxs-lookup"><span data-stu-id="ef5bb-111">The first line declares the syntax version being used.</span></span> <span data-ttu-id="ef5bb-112">A versão 3 do idioma foi lançada em 2016.</span><span class="sxs-lookup"><span data-stu-id="ef5bb-112">Version 3 of the language was released in 2016.</span></span> <span data-ttu-id="ef5bb-113">É a versão que recomendamos para os serviços gRPC.</span><span class="sxs-lookup"><span data-stu-id="ef5bb-113">It's the version that we recommend for gRPC services.</span></span>

<span data-ttu-id="ef5bb-114">A `option csharp_namespace` linha especifica o namespace a ser usado para os tipos C# gerados.</span><span class="sxs-lookup"><span data-stu-id="ef5bb-114">The `option csharp_namespace` line specifies the namespace to be used for the generated C# types.</span></span> <span data-ttu-id="ef5bb-115">Essa opção será ignorada `.proto` quando o arquivo for compilado para outros idiomas.</span><span class="sxs-lookup"><span data-stu-id="ef5bb-115">This option will be ignored when the `.proto` file is compiled for other languages.</span></span> <span data-ttu-id="ef5bb-116">Os arquivos protobuf geralmente contêm opções específicas do idioma para vários idiomas.</span><span class="sxs-lookup"><span data-stu-id="ef5bb-116">Protobuf files often contain language-specific options for several languages.</span></span>

<span data-ttu-id="ef5bb-117">A `Stock` definição da mensagem especifica quatro campos.</span><span class="sxs-lookup"><span data-stu-id="ef5bb-117">The `Stock` message definition specifies four fields.</span></span> <span data-ttu-id="ef5bb-118">Cada um tem um tipo, um nome e um número de campo.</span><span class="sxs-lookup"><span data-stu-id="ef5bb-118">Each has a type, a name, and a field number.</span></span>

## <a name="field-numbers"></a><span data-ttu-id="ef5bb-119">Números de campo</span><span class="sxs-lookup"><span data-stu-id="ef5bb-119">Field numbers</span></span>

<span data-ttu-id="ef5bb-120">Os números de campo são uma parte importante do Protobuf.</span><span class="sxs-lookup"><span data-stu-id="ef5bb-120">Field numbers are an important part of Protobuf.</span></span> <span data-ttu-id="ef5bb-121">Eles são usados para identificar campos nos dados codificados binários, o que significa que eles não podem mudar de versão para versão do seu serviço.</span><span class="sxs-lookup"><span data-stu-id="ef5bb-121">They're used to identify fields in the binary encoded data, which means they can't change from version to version of your service.</span></span> <span data-ttu-id="ef5bb-122">A vantagem é que a compatibilidade retrógrada e a compatibilidade avançada são possíveis.</span><span class="sxs-lookup"><span data-stu-id="ef5bb-122">The advantage is that backward compatibility and forward compatibility are possible.</span></span> <span data-ttu-id="ef5bb-123">Clientes e serviços simplesmente ignorarão os números de campo que eles desconhecem, desde que a possibilidade de valores perdidos seja tratada.</span><span class="sxs-lookup"><span data-stu-id="ef5bb-123">Clients and services will simply ignore field numbers that they don't know about, as long as the possibility of missing values is handled.</span></span>

<span data-ttu-id="ef5bb-124">No formato binário, o número de campo é combinado com um identificador de tipo.</span><span class="sxs-lookup"><span data-stu-id="ef5bb-124">In the binary format, the field number is combined with a type identifier.</span></span> <span data-ttu-id="ef5bb-125">Os números de campo de 1 a 15 podem ser codificados com seu tipo como um único byte.</span><span class="sxs-lookup"><span data-stu-id="ef5bb-125">Field numbers from 1 to 15 can be encoded with their type as a single byte.</span></span> <span data-ttu-id="ef5bb-126">Números de 16 a 2.047 levam 2 bytes.</span><span class="sxs-lookup"><span data-stu-id="ef5bb-126">Numbers from 16 to 2,047 take 2 bytes.</span></span> <span data-ttu-id="ef5bb-127">Você pode ir mais alto se precisar de mais de 2.047 campos em uma mensagem por qualquer motivo.</span><span class="sxs-lookup"><span data-stu-id="ef5bb-127">You can go higher if you need more than 2,047 fields on a message for any reason.</span></span> <span data-ttu-id="ef5bb-128">Os identificadores single byte para números de campo de 1 a 15 oferecem melhor desempenho, então você deve usá-los para os campos mais básicos e usados com freqüência.</span><span class="sxs-lookup"><span data-stu-id="ef5bb-128">The single byte identifiers for field numbers 1 to 15 offer better performance, so you should use them for the most basic, frequently used fields.</span></span>

## <a name="types"></a><span data-ttu-id="ef5bb-129">Tipos</span><span class="sxs-lookup"><span data-stu-id="ef5bb-129">Types</span></span>

<span data-ttu-id="ef5bb-130">As declarações do tipo estão usando os tipos de dados escalares nativos da Protobuf, que são discutidos com mais detalhes [na próxima seção](protobuf-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="ef5bb-130">The type declarations are using Protobuf's native scalar data types, which are discussed in more detail in [the next section](protobuf-data-types.md).</span></span> <span data-ttu-id="ef5bb-131">O resto deste capítulo cobrirá os tipos incorporados do Protobuf e mostrará como eles se relacionam com tipos comuns .NET.</span><span class="sxs-lookup"><span data-stu-id="ef5bb-131">The rest of this chapter will cover Protobuf's built-in types and show how they relate to common .NET types.</span></span>

> [!NOTE]
> <span data-ttu-id="ef5bb-132">Protobuf não suporta nativamente `decimal` um tipo, por isso `double` é usado em vez disso.</span><span class="sxs-lookup"><span data-stu-id="ef5bb-132">Protobuf doesn't natively support a `decimal` type, so `double` is used instead.</span></span> <span data-ttu-id="ef5bb-133">Para aplicações que requerem precisão decimal total, consulte a [seção em decimais](protobuf-data-types.md#decimals) na próxima parte deste capítulo.</span><span class="sxs-lookup"><span data-stu-id="ef5bb-133">For applications that require full decimal precision, refer to the [section on decimals](protobuf-data-types.md#decimals) in the next part of this chapter.</span></span>

## <a name="the-generated-code"></a><span data-ttu-id="ef5bb-134">O código gerado</span><span class="sxs-lookup"><span data-stu-id="ef5bb-134">The generated code</span></span>

<span data-ttu-id="ef5bb-135">Quando você constrói seu aplicativo, o Protobuf cria classes para cada uma de suas mensagens, mapeando seus tipos nativos para tipos C#.</span><span class="sxs-lookup"><span data-stu-id="ef5bb-135">When you build your application, Protobuf creates classes for each of your messages, mapping its native types to C# types.</span></span> <span data-ttu-id="ef5bb-136">O `Stock` tipo gerado teria a seguinte assinatura:</span><span class="sxs-lookup"><span data-stu-id="ef5bb-136">The generated `Stock` type would have the following signature:</span></span>

```csharp
public class Stock
{
    public int Id { get; set; }
    public string Symbol { get; set; }
    public string DisplayName { get; set; }
    public int MarketId { get; set; }
}
```

<span data-ttu-id="ef5bb-137">O código real gerado é muito mais complicado do que isso.</span><span class="sxs-lookup"><span data-stu-id="ef5bb-137">The actual code that's generated is far more complicated than this.</span></span> <span data-ttu-id="ef5bb-138">A razão é que cada classe contém todo o código necessário para serializar e desserializar-se ao formato de fio binário.</span><span class="sxs-lookup"><span data-stu-id="ef5bb-138">The reason is that each class contains all the code necessary to serialize and deserialize itself to the binary wire format.</span></span>

### <a name="property-names"></a><span data-ttu-id="ef5bb-139">Nomes de propriedades</span><span class="sxs-lookup"><span data-stu-id="ef5bb-139">Property names</span></span>

<span data-ttu-id="ef5bb-140">Observe que o compilador Protobuf se inscreveu `PascalCase` nos `snake_case` nomes `.proto` da propriedade, embora estivessem no arquivo.</span><span class="sxs-lookup"><span data-stu-id="ef5bb-140">Note that the Protobuf compiler applied `PascalCase` to the property names, although they were `snake_case` in the `.proto` file.</span></span> <span data-ttu-id="ef5bb-141">O [guia de estilo Protobuf](https://developers.google.com/protocol-buffers/docs/style) recomenda usar `snake_case` em suas definições de mensagem para que a geração de código para outras plataformas produza o caso esperado para suas convenções.</span><span class="sxs-lookup"><span data-stu-id="ef5bb-141">The [Protobuf style guide](https://developers.google.com/protocol-buffers/docs/style) recommends using `snake_case` in your message definitions so that the code generation for other platforms produces the expected case for their conventions.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ef5bb-142">[Próximo](protocol-buffers.md)
>[anterior](protobuf-data-types.md)</span><span class="sxs-lookup"><span data-stu-id="ef5bb-142">[Previous](protocol-buffers.md)
[Next](protobuf-data-types.md)</span></span>
