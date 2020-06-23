---
title: 'Como: usar DataContractJsonSerializer'
description: Saiba como serializar objetos de tipo .NET em dados codificados em JSON e, em seguida, desserializar esses dados de volta em instâncias de tipos .NET.
ms.date: 03/25/2019
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
ms.openlocfilehash: 4ffa0e9dec0a677a38d244b4a0da476d91852da5
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246799"
---
# <a name="how-to-use-datacontractjsonserializer"></a><span data-ttu-id="351f0-103">Como usar o DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="351f0-103">How to use DataContractJsonSerializer</span></span>

> [!NOTE]
> <span data-ttu-id="351f0-104">Este artigo é sobre <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> .</span><span class="sxs-lookup"><span data-stu-id="351f0-104">This article is about <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span> <span data-ttu-id="351f0-105">Para a maioria dos cenários que envolvem a serialização e desserialização do JSON, recomendamos as APIs na [System.Text.Jsno namespace](../../../standard/serialization/system-text-json-overview.md).</span><span class="sxs-lookup"><span data-stu-id="351f0-105">For most scenarios that involve serializing and deserializing JSON, we recommend the APIs in the [System.Text.Json namespace](../../../standard/serialization/system-text-json-overview.md).</span></span>

<span data-ttu-id="351f0-106">JSON (JavaScript Object Notation) é um formato eficiente de codificação de dados que permite a troca rápida de pequenas quantidades de dados entre navegadores cliente e serviços Web habilitados para AJAX.</span><span class="sxs-lookup"><span data-stu-id="351f0-106">JSON (JavaScript Object Notation) is an efficient data encoding format that enables fast exchanges of small amounts of data between client browsers and AJAX-enabled Web services.</span></span>

<span data-ttu-id="351f0-107">Este artigo demonstra como serializar objetos do tipo .NET em dados codificados em JSON e, em seguida, desserializar os dados no formato JSON de volta em instâncias de tipos .NET.</span><span class="sxs-lookup"><span data-stu-id="351f0-107">This article demonstrates how to serialize .NET type objects into JSON-encoded data and then deserialize data in the JSON format back into instances of .NET types.</span></span> <span data-ttu-id="351f0-108">Este exemplo usa um contrato de dados para demonstrar a serialização e a desserialização de um tipo definido pelo usuário `Person` e usa o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> .</span><span class="sxs-lookup"><span data-stu-id="351f0-108">This example uses a data contract to demonstrate serialization and deserialization of a user-defined `Person` type and uses <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>

<span data-ttu-id="351f0-109">Normalmente, a serialização e desserialização JSON são manipuladas automaticamente pelo Windows Communication Foundation (WCF) quando você usa tipos de contrato de dados em operações de serviço que são expostas em pontos de extremidade habilitados para AJAX.</span><span class="sxs-lookup"><span data-stu-id="351f0-109">Normally, JSON serialization and deserialization are handled automatically by Windows Communication Foundation (WCF) when you use data contract types in service operations that are exposed over AJAX-enabled endpoints.</span></span> <span data-ttu-id="351f0-110">No entanto, em alguns casos, talvez seja necessário trabalhar diretamente com dados JSON.</span><span class="sxs-lookup"><span data-stu-id="351f0-110">However, in some cases you may need to work with JSON data directly.</span></span>

<span data-ttu-id="351f0-111">Este artigo se baseia no [exemplo de DataContractJsonSerializer](../samples/json-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="351f0-111">This article is based on the [DataContractJsonSerializer sample](../samples/json-serialization.md).</span></span>

## <a name="to-define-the-data-contract-for-a-person-type"></a><span data-ttu-id="351f0-112">Para definir o contrato de dados para um tipo Person</span><span class="sxs-lookup"><span data-stu-id="351f0-112">To define the data contract for a Person type</span></span>

1. <span data-ttu-id="351f0-113">Defina o contrato de dados para `Person` anexando <xref:System.Runtime.Serialization.DataContractAttribute> à classe e o atributo <xref:System.Runtime.Serialization.DataMemberAttribute> aos membros que você deseja serializar.</span><span class="sxs-lookup"><span data-stu-id="351f0-113">Define the data contract for `Person` by attaching the <xref:System.Runtime.Serialization.DataContractAttribute> to the class and <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the members you want to serialize.</span></span> <span data-ttu-id="351f0-114">Para obter mais informações sobre contratos de dados, consulte [Designing Service Contracts](../designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="351f0-114">For more information about data contracts, see [Designing service contracts](../designing-service-contracts.md).</span></span>

    ```csharp
    [DataContract]
    internal class Person
    {
        [DataMember]
        internal string name;

        [DataMember]
        internal int age;
    }
    ```

## <a name="to-serialize-an-instance-of-type-person-to-json"></a><span data-ttu-id="351f0-115">Para serializar uma instância do tipo Person para JSON</span><span class="sxs-lookup"><span data-stu-id="351f0-115">To serialize an instance of type Person to JSON</span></span>

> [!NOTE]
> <span data-ttu-id="351f0-116">Se ocorrer um erro durante a serialização de uma resposta de saída no servidor ou por algum outro motivo, ele não poderá ser retornado ao cliente como uma falha.</span><span class="sxs-lookup"><span data-stu-id="351f0-116">If an error occurs during serialization of an outgoing reply on the server or for some other reason, it may not get returned to the client as a fault.</span></span>

1. <span data-ttu-id="351f0-117">Crie uma instância do tipo `Person`.</span><span class="sxs-lookup"><span data-stu-id="351f0-117">Create an instance of the `Person` type.</span></span>

    ```csharp
    var p = new Person();
    p.name = "John";
    p.age = 42;
    ```

2. <span data-ttu-id="351f0-118">Serialize o `Person` objeto para um fluxo de memória usando o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> .</span><span class="sxs-lookup"><span data-stu-id="351f0-118">Serialize the `Person` object to a memory stream by using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>

    ```csharp
    var stream1 = new MemoryStream();
    var ser = new DataContractJsonSerializer(typeof(Person));
    ```

3. <span data-ttu-id="351f0-119">Use o método <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> para gravar dados JSON no fluxo.</span><span class="sxs-lookup"><span data-stu-id="351f0-119">Use the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> method to write JSON data to the stream.</span></span>

    ```csharp
    ser.WriteObject(stream1, p);
    ```

4. <span data-ttu-id="351f0-120">Mostre a saída JSON.</span><span class="sxs-lookup"><span data-stu-id="351f0-120">Show the JSON output.</span></span>

    ```csharp
    stream1.Position = 0;
    var sr = new StreamReader(stream1);
    Console.Write("JSON form of Person object: ");
    Console.WriteLine(sr.ReadToEnd());
    ```

## <a name="to-deserialize-an-instance-of-type-person-from-json"></a><span data-ttu-id="351f0-121">Para desserializar uma instância do tipo Person de JSON</span><span class="sxs-lookup"><span data-stu-id="351f0-121">To deserialize an instance of type Person from JSON</span></span>

1. <span data-ttu-id="351f0-122">Desserialize os dados codificados por JSON em uma nova instância de `Person` usando o método <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> da classe <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="351f0-122">Deserialize the JSON-encoded data into a new instance of `Person` by using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> method of the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>

    ```csharp
    stream1.Position = 0;
    var p2 = (Person)ser.ReadObject(stream1);
    ```

2. <span data-ttu-id="351f0-123">Mostre os resultados.</span><span class="sxs-lookup"><span data-stu-id="351f0-123">Show the results.</span></span>

    ```csharp
    Console.WriteLine($"Deserialized back, got name={p2.name}, age={p2.age}");
    ```

## <a name="example"></a><span data-ttu-id="351f0-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="351f0-124">Example</span></span>

```csharp
// Create a User object and serialize it to a JSON stream.
public static string WriteFromObject()
{
    // Create User object.
    var user = new User("Bob", 42);

    // Create a stream to serialize the object to.
    var ms = new MemoryStream();

    // Serializer the User object to the stream.
    var ser = new DataContractJsonSerializer(typeof(User));
    ser.WriteObject(ms, user);
    byte[] json = ms.ToArray();
    ms.Close();
    return Encoding.UTF8.GetString(json, 0, json.Length);
}

// Deserialize a JSON stream to a User object.
public static User ReadToObject(string json)
{
    var deserializedUser = new User();
    var ms = new MemoryStream(Encoding.UTF8.GetBytes(json));
    var ser = new DataContractJsonSerializer(deserializedUser.GetType());
    deserializedUser = ser.ReadObject(ms) as User;
    ms.Close();
    return deserializedUser;
}
```

> [!NOTE]
> <span data-ttu-id="351f0-125">O serializador JSON gera uma exceção de serialização para contratos de dados que têm vários membros com o mesmo nome, como mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="351f0-125">The JSON serializer throws a serialization exception for data contracts that have multiple members with the same name, as shown in the following sample code.</span></span>

```csharp
[DataContract]
public class TestDuplicateDataBase
{
    [DataMember]
    public int field1 = 123;
}

[DataContract]
public class TestDuplicateDataDerived : TestDuplicateDataBase
{
    [DataMember]
    public new int field1 = 999;
}
```

## <a name="see-also"></a><span data-ttu-id="351f0-126">Veja também</span><span class="sxs-lookup"><span data-stu-id="351f0-126">See also</span></span>

- [<span data-ttu-id="351f0-127">Serialização JSON no .NET</span><span class="sxs-lookup"><span data-stu-id="351f0-127">JSON serialization in .NET</span></span>](../../../standard/serialization/system-text-json-overview.md)
