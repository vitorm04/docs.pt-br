---
title: 'Como: serializar e desserializar dados JSON'
ms.date: 03/25/2019
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
ms.openlocfilehash: 7edce66a23021fa03a6f98b3b847a5b671c17124
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59336948"
---
# <a name="how-to-serialize-and-deserialize-json-data"></a><span data-ttu-id="33896-102">Como: Serializar e desserializar dados JSON</span><span class="sxs-lookup"><span data-stu-id="33896-102">How to: Serialize and deserialize JSON data</span></span>
<span data-ttu-id="33896-103">JSON (JavaScript Object Notation) é um formato eficiente de codificação de dados que permite a troca rápida de pequenas quantidades de dados entre navegadores cliente e serviços Web habilitados para AJAX.</span><span class="sxs-lookup"><span data-stu-id="33896-103">JSON (JavaScript Object Notation) is an efficient data encoding format that enables fast exchanges of small amounts of data between client browsers and AJAX-enabled Web services.</span></span>  
  
 <span data-ttu-id="33896-104">Este artigo demonstra como serializar objetos do tipo .NET em dados codificados por JSON e depois desserializar os dados no formato JSON em instâncias de tipos do .NET.</span><span class="sxs-lookup"><span data-stu-id="33896-104">This article demonstrates how to serialize .NET type objects into JSON-encoded data and then deserialize data in the JSON format back into instances of .NET types.</span></span> <span data-ttu-id="33896-105">Este exemplo usa um contrato de dados para demonstrar a serialização e desserialização de um usuário definido `Person` tipo e usa <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="33896-105">This example uses a data contract to demonstrate serialization and deserialization of a user-defined `Person` type and uses <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
 <span data-ttu-id="33896-106">Normalmente, desserialização e serialização JSON são tratadas automaticamente pelo Windows Communication Foundation (WCF) quando você usa tipos de contrato de dados em operações de serviço que são expostas em pontos de extremidade habilitados para AJAX.</span><span class="sxs-lookup"><span data-stu-id="33896-106">Normally, JSON serialization and deserialization are handled automatically by Windows Communication Foundation (WCF) when you use data contract types in service operations that are exposed over AJAX-enabled endpoints.</span></span> <span data-ttu-id="33896-107">No entanto, em alguns casos você talvez precise trabalhar com dados JSON diretamente.</span><span class="sxs-lookup"><span data-stu-id="33896-107">However, in some cases you may need to work with JSON data directly.</span></span>   
  
> [!NOTE]
>  <span data-ttu-id="33896-108">Se ocorrer um erro durante a serialização de uma resposta de saída no servidor ou por algum outro motivo, ela não pode obter retornada ao cliente como uma falha.</span><span class="sxs-lookup"><span data-stu-id="33896-108">If an error occurs during serialization of an outgoing reply on the server or for some other reason, it may not get returned to the client as a fault.</span></span>  
  
 <span data-ttu-id="33896-109">Este artigo se baseia a [serialização JSON](../samples/json-serialization.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="33896-109">This article is based on the [JSON serialization](../samples/json-serialization.md) sample.</span></span>  
  
## <a name="to-define-the-data-contract-for-a-person-type"></a><span data-ttu-id="33896-110">Para definir o contrato de dados para um tipo de pessoa</span><span class="sxs-lookup"><span data-stu-id="33896-110">To define the data contract for a Person type</span></span> 
  
1. <span data-ttu-id="33896-111">Defina o contrato de dados para `Person` anexando <xref:System.Runtime.Serialization.DataContractAttribute> à classe e o atributo <xref:System.Runtime.Serialization.DataMemberAttribute> aos membros que você deseja serializar.</span><span class="sxs-lookup"><span data-stu-id="33896-111">Define the data contract for `Person` by attaching the <xref:System.Runtime.Serialization.DataContractAttribute> to the class and <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the members you want to serialize.</span></span> <span data-ttu-id="33896-112">Para obter mais informações sobre contratos de dados, consulte [Criando contratos de serviço](../designing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="33896-112">For more information about data contracts, see [Designing service contracts](../designing-service-contracts.md).</span></span>  
  
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
  
## <a name="to-serialize-an-instance-of-type-person-to-json"></a><span data-ttu-id="33896-113">Para serializar uma instância do tipo Person para JSON</span><span class="sxs-lookup"><span data-stu-id="33896-113">To serialize an instance of type Person to JSON</span></span>  
  
1. <span data-ttu-id="33896-114">Crie uma instância do tipo `Person`.</span><span class="sxs-lookup"><span data-stu-id="33896-114">Create an instance of the `Person` type.</span></span>  
  
    ```csharp  
    Person p = new Person();  
    p.name = "John";  
    p.age = 42;  
    ```  
  
2. <span data-ttu-id="33896-115">Serializar o `Person` objeto em um fluxo de memória usando o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="33896-115">Serialize the `Person` object to a memory stream by using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
    ```csharp  
    MemoryStream stream1 = new MemoryStream();  
    DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));  
    ```  
  
3. <span data-ttu-id="33896-116">Use o método <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> para gravar dados JSON no fluxo.</span><span class="sxs-lookup"><span data-stu-id="33896-116">Use the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> method to write JSON data to the stream.</span></span>  
  
    ```csharp  
    ser.WriteObject(stream1, p);  
    ```  
  
4. <span data-ttu-id="33896-117">Mostre a saída JSON.</span><span class="sxs-lookup"><span data-stu-id="33896-117">Show the JSON output.</span></span>  
  
    ```csharp  
    stream1.Position = 0;  
    StreamReader sr = new StreamReader(stream1);  
    Console.Write("JSON form of Person object: ");  
    Console.WriteLine(sr.ReadToEnd());  
    ```  
  
## <a name="to-deserialize-an-instance-of-type-person-from-json"></a><span data-ttu-id="33896-118">Para desserializar uma instância do tipo Person de JSON</span><span class="sxs-lookup"><span data-stu-id="33896-118">To deserialize an instance of type Person from JSON</span></span>  
  
1. <span data-ttu-id="33896-119">Desserialize os dados codificados por JSON em uma nova instância de `Person` usando o método <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> da classe <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="33896-119">Deserialize the JSON-encoded data into a new instance of `Person` by using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> method of the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
    ```csharp  
    stream1.Position = 0;  
    Person p2 = (Person)ser.ReadObject(stream1);  
    ```  
  
2. <span data-ttu-id="33896-120">Mostre os resultados.</span><span class="sxs-lookup"><span data-stu-id="33896-120">Show the results.</span></span>  
  
    ```csharp  
    Console.WriteLine($"Deserialized back, got name={p2.name}, age={p2.age}");  
    ```  
  
## <a name="example"></a><span data-ttu-id="33896-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="33896-121">Example</span></span>  
  
```csharp  
// Create a User object and serialize it to a JSON stream.  
public static string WriteFromObject()  
{  
    //Create User object.  
    User user = new User("Bob", 42);  
  
    //Create a stream to serialize the object to.  
    MemoryStream ms = new MemoryStream();  
  
    // Serializer the User object to the stream.  
    DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(User));  
    ser.WriteObject(ms, user);  
    byte[] json = ms.ToArray();  
    ms.Close();  
    return Encoding.UTF8.GetString(json, 0, json.Length);  
}  
  
// Deserialize a JSON stream to a User object.  
public static User ReadToObject(string json)  
{  
    User deserializedUser = new User();  
    MemoryStream ms = new MemoryStream(Encoding.UTF8.GetBytes(json));  
    DataContractJsonSerializer ser = new DataContractJsonSerializer(deserializedUser.GetType());  
    deserializedUser = ser.ReadObject(ms) as User;  
    ms.Close();  
    return deserializedUser;  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="33896-122">O serializador JSON gera uma exceção de serialização para contratos de dados que têm vários membros com o mesmo nome, como mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="33896-122">The JSON serializer throws a serialization exception for data contracts that have multiple members with the same name, as shown in the following sample code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="33896-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="33896-123">See also</span></span>

- [<span data-ttu-id="33896-124">Serialização JSON autônoma</span><span class="sxs-lookup"><span data-stu-id="33896-124">Stand-alone JSON serialization</span></span>](stand-alone-json-serialization.md)
- [<span data-ttu-id="33896-125">Formatos de transferência de suporte para JSON e outros dados</span><span class="sxs-lookup"><span data-stu-id="33896-125">Support for JSON and other data transfer formats</span></span>](support-for-json-and-other-data-transfer-formats.md)
