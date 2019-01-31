---
title: Utilizando um resolvedor de contrato de dados
ms.date: 03/30/2017
ms.assetid: 2e68a16c-36f0-4df4-b763-32021bff2b89
ms.openlocfilehash: 844c4e0861c2cf4e6acb2b128ff1f5cefa0f7fa0
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55279143"
---
# <a name="using-a-data-contract-resolver"></a><span data-ttu-id="67c9b-102">Utilizando um resolvedor de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="67c9b-102">Using a Data Contract Resolver</span></span>
<span data-ttu-id="67c9b-103">Um resolvedor de contrato de dados permite que você configure tipos conhecidos dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="67c9b-103">A data contract resolver allows you to configure known types dynamically.</span></span> <span data-ttu-id="67c9b-104">Tipos conhecidos são necessários ao serializar ou desserializar um tipo que não se espera por um contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="67c9b-104">Known types are required when serializing or deserializing a type not expected by a data contract.</span></span> <span data-ttu-id="67c9b-105">Para obter mais informações sobre tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="67c9b-105">For more information about known types, see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span> <span data-ttu-id="67c9b-106">Tipos conhecidos normalmente são especificados estaticamente.</span><span class="sxs-lookup"><span data-stu-id="67c9b-106">Known types are normally specified statically.</span></span> <span data-ttu-id="67c9b-107">Isso significa que você precisaria saber todos os tipos possíveis de uma operação pode receber ao implementar a operação.</span><span class="sxs-lookup"><span data-stu-id="67c9b-107">This means you would have to know all the possible types an operation may receive while implementing the operation.</span></span> <span data-ttu-id="67c9b-108">Há cenários em que isso não é verdadeiro e é importante ser capaz de especificar tipos conhecidos dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="67c9b-108">There are scenarios in which this is not true and being able to specify known types dynamically is important.</span></span>  
  
## <a name="creating-a-data-contract-resolver"></a><span data-ttu-id="67c9b-109">Criação de um resolvedor de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="67c9b-109">Creating a Data Contract Resolver</span></span>  
 <span data-ttu-id="67c9b-110">A criação de um resolvedor de contrato de dados envolve implementar dois métodos, <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> e <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>.</span><span class="sxs-lookup"><span data-stu-id="67c9b-110">Creating a data contract resolver involves implementing two methods, <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> and <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>.</span></span> <span data-ttu-id="67c9b-111">Esses dois métodos implementam retornos de chamada que são usados durante a serialização e desserialização, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="67c9b-111">These two methods implement callbacks that are used during serialization and deserialization, respectively.</span></span> <span data-ttu-id="67c9b-112">O <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> método é invocado durante a serialização e usa um tipo de contrato de dados e mapeia-o para um `xsi:type` nome e namespace.</span><span class="sxs-lookup"><span data-stu-id="67c9b-112">The <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> method is invoked during serialization and takes a data contract type and maps it to an `xsi:type` name and namespace.</span></span> <span data-ttu-id="67c9b-113">O <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> método é invocado durante a desserialização e leva um `xsi:type` nome e o namespace e resolve para um tipo de contrato de dados.</span><span class="sxs-lookup"><span data-stu-id="67c9b-113">The <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> method is invoked during deserialization and takes an `xsi:type` name and namespace and resolves it to a data contract type.</span></span> <span data-ttu-id="67c9b-114">Esses dois métodos têm um `knownTypeResolver` parâmetro que pode ser usado para usar o padrão conhecido de resolvedor de tipo em sua implementação.</span><span class="sxs-lookup"><span data-stu-id="67c9b-114">Both of these methods have a `knownTypeResolver` parameter that can be used to use the default known type resolver in your implementation.</span></span>  
  
 <span data-ttu-id="67c9b-115">O exemplo a seguir mostra como implementar uma <xref:System.Runtime.Serialization.DataContractResolver> para mapear de e para um tipo de contrato de dados denominado `Customer` derivado de um tipo de contrato de dados `Person`.</span><span class="sxs-lookup"><span data-stu-id="67c9b-115">The following example shows how to implement a <xref:System.Runtime.Serialization.DataContractResolver> to map to and from a data contract type named `Customer` derived from a data contract type `Person`.</span></span>  
  
```csharp  
public class MyCustomerResolver : DataContractResolver  
{  
    public override bool TryResolveType(Type dataContractType, Type declaredType, DataContractResolver knownTypeResolver, out XmlDictionaryString typeName, out XmlDictionaryString typeNamespace)  
    {  
        if (dataContractType == typeof(Customer))  
        {  
            XmlDictionary dictionary = new XmlDictionary();  
            typeName = dictionary.Add("SomeCustomer");  
            typeNamespace = dictionary.Add("http://tempuri.com");  
            return true;  
        }  
        else  
        {  
            return knownTypeResolver.TryResolveType(dataContractType, declaredType, null, out typeName, out typeNamespace);  
        }  
    }  
  
    public override Type ResolveName(string typeName, string typeNamespace, DataContractResolver knownTypeResolver)  
    {  
        if (typeName == "SomeCustomer" && typeNamespace == "http://tempuri.com")  
        {  
            return typeof(Customer);  
        }  
        else  
        {  
            return knownTypeResolver.ResolveName(typeName, typeNamespace, null);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="67c9b-116">Depois que você tiver definido uma <xref:System.Runtime.Serialization.DataContractResolver> você pode usá-lo, passando-o para o <xref:System.Runtime.Serialization.DataContractSerializer> construtor, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="67c9b-116">Once you have defined a <xref:System.Runtime.Serialization.DataContractResolver> you can use it by passing it to the <xref:System.Runtime.Serialization.DataContractSerializer> constructor as shown in the following example.</span></span>  
  
```  
XmlObjectSerializer serializer = new DataContractSerializer(typeof(Customer), null, Int32.MaxValue, false, false, null, new MyCustomerResolver());  
```  
  
 <span data-ttu-id="67c9b-117">Você pode especificar uma <xref:System.Runtime.Serialization.DataContractResolver> em uma chamada para o <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A?displayProperty=nameWithType> ou <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A?displayProperty=nameWithType> métodos, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="67c9b-117">You can specify a <xref:System.Runtime.Serialization.DataContractResolver> in a call to the <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A?displayProperty=nameWithType> or <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A?displayProperty=nameWithType> methods, as shown in the following example.</span></span>  
  
```  
MemoryStream ms = new MemoryStream();  
DataContractSerializer serializer = new DataContractSerializer(typeof(Customer));  
XmlDictionaryWriter writer = XmlDictionaryWriter.CreateDictionaryWriter(XmlWriter.Create(ms));  
serializer.WriteObject(writer, new Customer(), new MyCustomerResolver());  
writer.Flush();  
ms.Position = 0;  
Console.WriteLine(((Customer)serializer.ReadObject(XmlDictionaryReader.CreateDictionaryReader(XmlReader.Create(ms)), false, new MyCustomerResolver()));  
```  
  
 <span data-ttu-id="67c9b-118">Ou você pode defini-lo sobre a <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="67c9b-118">Or you can set it on the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> as shown in the following example.</span></span>  
  
```  
ServiceHost host = new ServiceHost(typeof(MyService));  
  
ContractDescription cd = host.Description.Endpoints[0].Contract;  
OperationDescription myOperationDescription = cd.Operations.Find("Echo");  
  
DataContractSerializerOperationBehavior serializerBehavior = myOperationDescription.Behaviors.Find<DataContractSerializerOperationBehavior>();  
if (serializerBehavior == null)  
{  
    serializerBehavior = new DataContractSerializerOperationBehavior(myOperationDescription);  
    myOperationDescription.Behaviors.Add(serializerBehavior);  
}  
  
SerializerBehavior.DataContractResolver = new MyCustomerResolver();  
```  
  
 <span data-ttu-id="67c9b-119">Declarativamente, você pode especificar um resolvedor de contrato de dados com a implementação de um atributo que pode ser aplicado a um serviço.</span><span class="sxs-lookup"><span data-stu-id="67c9b-119">You can declaratively specify a data contract resolver by implementing an attribute that can be applied to a service.</span></span>  <span data-ttu-id="67c9b-120">Para obter mais informações, consulte o [KnownAssemblyAttribute](../../../../docs/framework/wcf/samples/knownassemblyattribute.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="67c9b-120">For more information, see the [KnownAssemblyAttribute](../../../../docs/framework/wcf/samples/knownassemblyattribute.md) sample.</span></span> <span data-ttu-id="67c9b-121">Este exemplo implementa um atributo chamado "KnownAssembly" que adiciona um resolvedor de contrato de dados personalizados ao comportamento do serviço.</span><span class="sxs-lookup"><span data-stu-id="67c9b-121">This sample implements an attribute called "KnownAssembly" that adds a custom data contract resolver to the service’s behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67c9b-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="67c9b-122">See also</span></span>
- [<span data-ttu-id="67c9b-123">Tipos conhecidos de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="67c9b-123">Data Contract Known Types</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="67c9b-124">Exemplo de DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="67c9b-124">DataContractSerializer Sample</span></span>](../../../../docs/framework/wcf/samples/datacontractserializer-sample.md)
- [<span data-ttu-id="67c9b-125">KnownAssemblyAttribute</span><span class="sxs-lookup"><span data-stu-id="67c9b-125">KnownAssemblyAttribute</span></span>](../../../../docs/framework/wcf/samples/knownassemblyattribute.md)
