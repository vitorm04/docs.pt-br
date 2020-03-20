---
title: DataContractResolver
ms.date: 03/30/2017
ms.assetid: 6c200c02-bc14-4b8d-bbab-9da31185b805
ms.openlocfilehash: 716bcb2bb43656051beffb15da9c7a988942ecd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183792"
---
# <a name="datacontractresolver"></a><span data-ttu-id="d4f52-102">DataContractResolver</span><span class="sxs-lookup"><span data-stu-id="d4f52-102">DataContractResolver</span></span>
<span data-ttu-id="d4f52-103">Esta amostra demonstra como os processos de serialização e <xref:System.Runtime.Serialization.DataContractResolver> desserialização podem ser personalizados usando a classe.</span><span class="sxs-lookup"><span data-stu-id="d4f52-103">This sample demonstrates how the serialization and deserialization processes can be customized by using the <xref:System.Runtime.Serialization.DataContractResolver> class.</span></span> <span data-ttu-id="d4f52-104">Esta amostra mostra como usar um DataContractResolved para mapear tipos clr de e para uma representação xsi:type durante a serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="d4f52-104">This sample shows how to use a DataContractResolver to map CLR types to and from an xsi:type representation during serialization and deserialization.</span></span>

## <a name="sample-details"></a><span data-ttu-id="d4f52-105">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="d4f52-105">Sample Details</span></span>
 <span data-ttu-id="d4f52-106">A amostra define os seguintes tipos de CLR.</span><span class="sxs-lookup"><span data-stu-id="d4f52-106">The sample defines the following CLR types.</span></span>

```csharp
using System;
using System.Runtime.Serialization;

namespace Types
{
    [DataContract]
    public class Customer
    {
        [DataMember]
        public string Name { get; set; }
    }

    [DataContract]
    public class VIPCustomer : Customer
    {
        [DataMember]
        public string VipInfo { get; set; }
    }

    [DataContract]
    public class RegularCustomer : Customer
    {
    }

    [DataContract]
    public class PreferredVIPCustomer : VIPCustomer
    {
    }
}
```

 <span data-ttu-id="d4f52-107">A amostra carrega o conjunto, extrai cada um desses tipos e, em seguida, serializa e desserializa-os.</span><span class="sxs-lookup"><span data-stu-id="d4f52-107">The sample loads the assembly, extracts each of these types, and then serializes and deserializes them.</span></span> <span data-ttu-id="d4f52-108">O <xref:System.Runtime.Serialization.DataContractResolver> é conectado ao processo de serialização <xref:System.Runtime.Serialization.DataContractResolver>passando uma instância <xref:System.Runtime.Serialization.DataContractSerializer> da classe derivada para o construtor, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="d4f52-108">The <xref:System.Runtime.Serialization.DataContractResolver> is plugged into the serialization process by passing an instance of the <xref:System.Runtime.Serialization.DataContractResolver>-derived class to the <xref:System.Runtime.Serialization.DataContractSerializer> constructor, as shown in the following example.</span></span>

```csharp
this.serializer = new DataContractSerializer(typeof(Object), null, int.MaxValue, false, true, null, new MyDataContractResolver(assembly));
```

 <span data-ttu-id="d4f52-109">Em seguida, a amostra serializa os tipos CLR como mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="d4f52-109">The sample then serializes the CLR types as shown in the following code example.</span></span>

```csharp
Assembly assembly = Assembly.Load(new AssemblyName("Types"));

public void serialize(Type type)
{
    Object instance = Activator.CreateInstance(type);

    Console.WriteLine("----------------------------------------");
    Console.WriteLine();
    Console.WriteLine("Serializing type: {0}", type.Name);
    Console.WriteLine();
    this.buffer = new StringBuilder();
    using (XmlWriter xmlWriter = XmlWriter.Create(this.buffer))
    {
        try
        {
            this.serializer.WriteObject(xmlWriter, instance);
        }
        catch (SerializationException error)
        {
            Console.WriteLine(error.ToString());
        }
    }
    Console.WriteLine(this.buffer.ToString());
}
```

 <span data-ttu-id="d4f52-110">Em seguida, a amostra desserializa os xsi:tipos como mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="d4f52-110">The sample then deserializes the xsi:types as shown in the following code example.</span></span>

```csharp
public void deserialize(Type type)
{
    Console.WriteLine();
    Console.WriteLine("Deserializing type: {0}", type.Name);
    Console.WriteLine();
    using (XmlReader xmlReader = XmlReader.Create(new StringReader(this.buffer.ToString())))
    {
        Object obj = this.serializer.ReadObject(xmlReader);
    }
}
```

 <span data-ttu-id="d4f52-111">Uma vez <xref:System.Runtime.Serialization.DataContractResolver> que o <xref:System.Runtime.Serialization.DataContractSerializer> costume é <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> passado para o construtor, o é chamado `xsi:type`durante a serialização para mapear um tipo CLR para um equivalente .</span><span class="sxs-lookup"><span data-stu-id="d4f52-111">Since the custom <xref:System.Runtime.Serialization.DataContractResolver> is passed in to the <xref:System.Runtime.Serialization.DataContractSerializer> constructor, the <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> is called during serialization to map a CLR type to an equivalent `xsi:type`.</span></span> <span data-ttu-id="d4f52-112">Da mesma <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> forma, o é chamado `xsi:type` durante a desserialização para mapear o tipo CLR equivalente.</span><span class="sxs-lookup"><span data-stu-id="d4f52-112">Similarly the <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> is called during deserialization to map the `xsi:type` to an equivalent CLR type.</span></span> <span data-ttu-id="d4f52-113">Nesta amostra, <xref:System.Runtime.Serialization.DataContractResolver> o é definido como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="d4f52-113">In this sample, the <xref:System.Runtime.Serialization.DataContractResolver> is defined as shown in the following example.</span></span>

 <span data-ttu-id="d4f52-114">O exemplo de código a <xref:System.Runtime.Serialization.DataContractResolver>seguir é uma classe derivada de .</span><span class="sxs-lookup"><span data-stu-id="d4f52-114">The following code example is a class deriving from <xref:System.Runtime.Serialization.DataContractResolver>.</span></span>

```csharp
class MyDataContractResolver : DataContractResolver
{
    private Dictionary<string, XmlDictionaryString> dictionary = new Dictionary<string, XmlDictionaryString>();
    Assembly assembly;

    public MyDataContractResolver(Assembly assembly)
    {
        this.assembly = assembly;
    }

    // Used at deserialization
    // Allows users to map xsi:type name to any Type
    public override Type ResolveName(string typeName, string typeNamespace, DataContractResolver knownTypeResolver)
    {
        XmlDictionaryString tName;
        XmlDictionaryString tNamespace;
        if (dictionary.TryGetValue(typeName, out tName) && dictionary.TryGetValue(typeNamespace, out tNamespace))
        {
            return this.assembly.GetType(tNamespace.Value + "." + tName.Value);
        }
        else
        {
            return null;
        }
    }

    // Used at serialization
    // Maps any Type to a new xsi:type representation
    public override void ResolveType(Type dataContractType, DataContractResolver knownTypeResolver, out XmlDictionaryString typeName, out XmlDictionaryString typeNamespace)
    {
        string name = dataContractType.Name;
        string namesp = dataContractType.Namespace;
        typeName = new XmlDictionaryString(XmlDictionary.Empty, name, 0);
        typeNamespace = new XmlDictionaryString(XmlDictionary.Empty, namesp, 0);
        if (!dictionary.ContainsKey(dataContractType.Name))
        {
            dictionary.Add(name, typeName);
        }
        if (!dictionary.ContainsKey(dataContractType.Namespace))
        {
            dictionary.Add(namesp, typeNamespace);
        }
    }
}
```

 <span data-ttu-id="d4f52-115">Como parte da amostra, o projeto Tipos gera a montagem com todos os tipos utilizados nesta amostra.</span><span class="sxs-lookup"><span data-stu-id="d4f52-115">As part of the sample, the Types project generates the assembly with all the types that are used in this sample.</span></span> <span data-ttu-id="d4f52-116">Use este projeto para adicionar, remover ou modificar os tipos que serão serializados.</span><span class="sxs-lookup"><span data-stu-id="d4f52-116">Use this project to add, remove or modify the types that will be serialized.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="d4f52-117">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="d4f52-117">To use this sample</span></span>

1. <span data-ttu-id="d4f52-118">Usando o Visual Studio 2012, abra o arquivo de solução DCRSample.sLn.</span><span class="sxs-lookup"><span data-stu-id="d4f52-118">Using Visual Studio 2012, open the DCRSample.sln solution file.</span></span>

2. <span data-ttu-id="d4f52-119">Para executar a solução, pressione F5</span><span class="sxs-lookup"><span data-stu-id="d4f52-119">To run the solution, press F5</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d4f52-120">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="d4f52-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d4f52-121">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="d4f52-121">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="d4f52-122">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="d4f52-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d4f52-123">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="d4f52-123">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractResolver`  
  
## <a name="see-also"></a><span data-ttu-id="d4f52-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="d4f52-124">See also</span></span>

- [<span data-ttu-id="d4f52-125">Usar um resolvedor de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="d4f52-125">Using a Data Contract Resolver</span></span>](../../../../docs/framework/wcf/feature-details/using-a-data-contract-resolver.md)
