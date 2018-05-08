---
title: Como serializar e desserializar dados JSON
ms.date: 03/30/2017
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
ms.openlocfilehash: f51ffb180adfc8310c91ff3c1ec7b7725f6b8b15
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-serialize-and-deserialize-json-data"></a>Como serializar e desserializar dados JSON
JSON (JavaScript Object Notation) é um formato eficiente de codificação de dados que permite a troca rápida de pequenas quantidades de dados entre navegadores cliente e serviços Web habilitados para AJAX.  
  
 Este tópico demonstra como serializar objetos do tipo .NET em dados codificados por JSON e depois desserializar os dados no formato JSON em instâncias de tipos .NET usando a classe <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>. Este exemplo usa um contrato de dados para demonstrar a serialização e a desserialização de um tipo `Person` definido pelo usuário.  
  
 Normalmente, desserialização e serialização JSON é tratado automaticamente pelo Windows Communication Foundation (WCF) quando você usar tipos de contrato de dados em operações de serviço que são expostas em pontos de extremidade habilitado para AJAX. Entretanto, em alguns casos, convém trabalhar com dados JSON diretamente. Este tópico demonstra um cenário desse tipo.  
  
> [!NOTE]
>  Se ocorrer um erro durante a serialização de uma resposta de saída no servidor ou se a operação de resposta gerar uma exceção por algum outro motivo, ela poderá não ser retornada ao cliente como uma falha.  
  
 Este tópico se baseia o [serialização JSON](../../../../docs/framework/wcf/samples/json-serialization.md) exemplo.  
  
### <a name="to-define-the-data-contract-for-a-person"></a>Para definir o contrato de dados para uma pessoa  
  
1.  Defina o contrato de dados para `Person` anexando <xref:System.Runtime.Serialization.DataContractAttribute> à classe e o atributo <xref:System.Runtime.Serialization.DataMemberAttribute> aos membros que você deseja serializar. Para obter mais informações sobre contratos de dados, consulte [criar contratos de serviço](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
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
  
### <a name="to-serialize-an-instance-of-type-person-to-json"></a>Para serializar uma instância do tipo Person para JSON  
  
1.  Crie uma instância do tipo `Person`.  
  
    ```csharp  
    Person p = new Person();  
    p.name = "John";  
    p.age = 42;  
    ```  
  
2.  Serialize o objeto `Person` em um fluxo de memória usando <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
    ```csharp  
    MemoryStream stream1 = new MemoryStream();  
    DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));  
    ```  
  
3.  Use o método <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> para gravar dados JSON no fluxo.  
  
    ```csharp  
    ser.WriteObject(stream1, p);  
    ```  
  
4.  Mostre a saída JSON.  
  
    ```csharp  
    stream1.Position = 0;  
    StreamReader sr = new StreamReader(stream1);  
    Console.Write("JSON form of Person object: ");  
    Console.WriteLine(sr.ReadToEnd());  
    ```  
  
### <a name="to-deserialize-an-instance-of-type-person-from-json"></a>Para desserializar uma instância do tipo Person de JSON  
  
1.  Desserialize os dados codificados por JSON em uma nova instância de `Person` usando o método <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> da classe <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
    ```csharp  
    stream1.Position = 0;  
    Person p2 = (Person)ser.ReadObject(stream1);  
    ```  
  
2.  Mostre os resultados.  
  
    ```csharp  
    Console.WriteLine($"Deserialized back, got name={p2.name}, age={p2.age}");  
    ```  
  
## <a name="example"></a>Exemplo  
  
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
>  O serializador JSON gera uma exceção de serialização para contratos de dados que têm vários membros com o mesmo nome, como mostrado no código de exemplo a seguir.  
  
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
  
## <a name="see-also"></a>Consulte também  
 [Serialização JSON autônoma](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)  
 [Suporte para JSON e outros formatos de transferência de dados](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)
