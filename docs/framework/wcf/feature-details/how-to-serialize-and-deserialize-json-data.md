---
title: 'Como: usar DataContractJsonSerializer'
ms.date: 03/25/2019
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
ms.openlocfilehash: 5e521621dd3ec8e82a860590e66c1c4da95fd3b8
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72180214"
---
# <a name="how-to-use-datacontractjsonserializer"></a><span data-ttu-id="9159e-102">Como: usar DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="9159e-102">How to: use DataContractJsonSerializer</span></span>
<span data-ttu-id="9159e-103">JSON (JavaScript Object Notation) é um formato eficiente de codificação de dados que permite a troca rápida de pequenas quantidades de dados entre navegadores cliente e serviços Web habilitados para AJAX.</span><span class="sxs-lookup"><span data-stu-id="9159e-103">JSON (JavaScript Object Notation) is an efficient data encoding format that enables fast exchanges of small amounts of data between client browsers and AJAX-enabled Web services.</span></span>  
  
 <span data-ttu-id="9159e-104">Este artigo demonstra como serializar objetos do tipo .NET em dados codificados em JSON e, em seguida, desserializar os dados no formato JSON de volta em instâncias de tipos .NET.</span><span class="sxs-lookup"><span data-stu-id="9159e-104">This article demonstrates how to serialize .NET type objects into JSON-encoded data and then deserialize data in the JSON format back into instances of .NET types.</span></span> <span data-ttu-id="9159e-105">Este exemplo usa um contrato de dados para demonstrar a serialização e a desserialização de um tipo `Person` definido pelo usuário e usa <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="9159e-105">This example uses a data contract to demonstrate serialization and deserialization of a user-defined `Person` type and uses <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
 <span data-ttu-id="9159e-106">Normalmente, a serialização e desserialização JSON são manipuladas automaticamente pelo Windows Communication Foundation (WCF) quando você usa tipos de contrato de dados em operações de serviço que são expostas em pontos de extremidade habilitados para AJAX.</span><span class="sxs-lookup"><span data-stu-id="9159e-106">Normally, JSON serialization and deserialization are handled automatically by Windows Communication Foundation (WCF) when you use data contract types in service operations that are exposed over AJAX-enabled endpoints.</span></span> <span data-ttu-id="9159e-107">No entanto, em alguns casos, talvez seja necessário trabalhar diretamente com dados JSON.</span><span class="sxs-lookup"><span data-stu-id="9159e-107">However, in some cases you may need to work with JSON data directly.</span></span>

> [!NOTE]
> <span data-ttu-id="9159e-108">Este artigo é sobre <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="9159e-108">This article is about <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span> <span data-ttu-id="9159e-109">Para a maioria dos cenários que envolvem a serialização e desserialização do JSON, recomendamos as ferramentas no [namespace System. Text. JSON](../../../standard/serialization/system-text-json-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9159e-109">For most scenarios that involve serializing and deserializing JSON, we recommend the tools in the [System.Text.Json namespace](../../../standard/serialization/system-text-json-overview.md).</span></span> 
  
 <span data-ttu-id="9159e-110">Este artigo se baseia no [exemplo de DataContractJsonSerializer](../samples/json-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="9159e-110">This article is based on the [DataContractJsonSerializer sample](../samples/json-serialization.md).</span></span>  
  
## <a name="to-define-the-data-contract-for-a-person-type"></a><span data-ttu-id="9159e-111">Para definir o contrato de dados para um tipo Person</span><span class="sxs-lookup"><span data-stu-id="9159e-111">To define the data contract for a Person type</span></span> 
  
1. <span data-ttu-id="9159e-112">Defina o contrato de dados para `Person` anexando <xref:System.Runtime.Serialization.DataContractAttribute> à classe e o atributo <xref:System.Runtime.Serialization.DataMemberAttribute> aos membros que você deseja serializar.</span><span class="sxs-lookup"><span data-stu-id="9159e-112">Define the data contract for `Person` by attaching the <xref:System.Runtime.Serialization.DataContractAttribute> to the class and <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the members you want to serialize.</span></span> <span data-ttu-id="9159e-113">Para obter mais informações sobre contratos de dados, consulte [Designing Service Contracts](../designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="9159e-113">For more information about data contracts, see [Designing service contracts](../designing-service-contracts.md).</span></span>  
  
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
  
## <a name="to-serialize-an-instance-of-type-person-to-json"></a><span data-ttu-id="9159e-114">Para serializar uma instância do tipo Person para JSON</span><span class="sxs-lookup"><span data-stu-id="9159e-114">To serialize an instance of type Person to JSON</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9159e-115">Se ocorrer um erro durante a serialização de uma resposta de saída no servidor ou por algum outro motivo, ele não poderá ser retornado ao cliente como uma falha.</span><span class="sxs-lookup"><span data-stu-id="9159e-115">If an error occurs during serialization of an outgoing reply on the server or for some other reason, it may not get returned to the client as a fault.</span></span>  

1. <span data-ttu-id="9159e-116">Crie uma instância do tipo `Person`.</span><span class="sxs-lookup"><span data-stu-id="9159e-116">Create an instance of the `Person` type.</span></span>  
  
    ```csharp  
    var p = new Person();  
    p.name = "John";  
    p.age = 42;  
    ```  
  
2. <span data-ttu-id="9159e-117">Serialize o objeto `Person` para um fluxo de memória usando o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="9159e-117">Serialize the `Person` object to a memory stream by using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
    ```csharp  
    var stream1 = new MemoryStream();  
    var ser = new DataContractJsonSerializer(typeof(Person));  
    ```  
  
3. <span data-ttu-id="9159e-118">Use o método <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> para gravar dados JSON no fluxo.</span><span class="sxs-lookup"><span data-stu-id="9159e-118">Use the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> method to write JSON data to the stream.</span></span>  
  
    ```csharp  
    ser.WriteObject(stream1, p);  
    ```  
  
4. <span data-ttu-id="9159e-119">Mostre a saída JSON.</span><span class="sxs-lookup"><span data-stu-id="9159e-119">Show the JSON output.</span></span>  
  
    ```csharp  
    stream1.Position = 0;  
    var sr = new StreamReader(stream1);  
    Console.Write("JSON form of Person object: ");  
    Console.WriteLine(sr.ReadToEnd());  
    ```  
  
## <a name="to-deserialize-an-instance-of-type-person-from-json"></a><span data-ttu-id="9159e-120">Para desserializar uma instância do tipo Person de JSON</span><span class="sxs-lookup"><span data-stu-id="9159e-120">To deserialize an instance of type Person from JSON</span></span>  
  
1. <span data-ttu-id="9159e-121">Desserialize os dados codificados por JSON em uma nova instância de `Person` usando o método <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> da classe <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="9159e-121">Deserialize the JSON-encoded data into a new instance of `Person` by using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> method of the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
    ```csharp  
    stream1.Position = 0;  
    var p2 = (Person)ser.ReadObject(stream1);  
    ```  
  
2. <span data-ttu-id="9159e-122">Mostre os resultados.</span><span class="sxs-lookup"><span data-stu-id="9159e-122">Show the results.</span></span>  
  
    ```csharp  
    Console.WriteLine($"Deserialized back, got name={p2.name}, age={p2.age}");  
    ```  
  
## <a name="example"></a><span data-ttu-id="9159e-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9159e-123">Example</span></span>  
  
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
> <span data-ttu-id="9159e-124">O serializador JSON gera uma exceção de serialização para contratos de dados que têm vários membros com o mesmo nome, como mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="9159e-124">The JSON serializer throws a serialization exception for data contracts that have multiple members with the same name, as shown in the following sample code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9159e-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9159e-125">See also</span></span>

- [<span data-ttu-id="9159e-126">Serialização JSON no .NET</span><span class="sxs-lookup"><span data-stu-id="9159e-126">JSON serialization in .NET</span></span>](../../../standard/serialization/system-text-json-overview.md)

