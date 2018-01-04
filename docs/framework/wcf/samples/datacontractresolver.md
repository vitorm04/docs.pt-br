---
title: DataContractResolver
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c200c02-bc14-4b8d-bbab-9da31185b805
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e360bed1cbdd11920d983c08cd7f3955b7432a96
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="datacontractresolver"></a><span data-ttu-id="f5ad5-102">DataContractResolver</span><span class="sxs-lookup"><span data-stu-id="f5ad5-102">DataContractResolver</span></span>
<span data-ttu-id="f5ad5-103">Este exemplo demonstra como os processos de serialização e desserialização podem ser personalizados usando o <xref:System.Runtime.Serialization.DataContractResolver> classe.</span><span class="sxs-lookup"><span data-stu-id="f5ad5-103">This sample demonstrates how the serialization and deserialization processes can be customized by using the <xref:System.Runtime.Serialization.DataContractResolver> class.</span></span> <span data-ttu-id="f5ad5-104">Este exemplo mostra como usar um DataContractResolver para mapear tipos CLR para e de uma representação de xsi: Type durante a serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="f5ad5-104">This sample shows how to use a DataContractResolver to map CLR types to and from an xsi:type representation during serialization and deserialization.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="f5ad5-105">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="f5ad5-105">Sample Details</span></span>  
 <span data-ttu-id="f5ad5-106">O exemplo define os seguintes tipos CLR.</span><span class="sxs-lookup"><span data-stu-id="f5ad5-106">The sample defines the following CLR types.</span></span>  
  
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
  
 <span data-ttu-id="f5ad5-107">O exemplo carrega o assembly, extrai cada um desses tipos e, em seguida, serializa e desserializa-los.</span><span class="sxs-lookup"><span data-stu-id="f5ad5-107">The sample loads the assembly, extracts each of these types, and then serializes and deserializes them.</span></span> <span data-ttu-id="f5ad5-108">O <xref:System.Runtime.Serialization.DataContractResolver> está conectado ao processo de serialização, passando uma instância do <xref:System.Runtime.Serialization.DataContractResolver>-derivado da classe para o <xref:System.Runtime.Serialization.DataContractSerializer> construtor, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f5ad5-108">The <xref:System.Runtime.Serialization.DataContractResolver> is plugged into the serialization process by passing an instance of the <xref:System.Runtime.Serialization.DataContractResolver>-derived class to the <xref:System.Runtime.Serialization.DataContractSerializer> constructor, as shown in the following example.</span></span>  
  
```csharp  
this.serializer = new DataContractSerializer(typeof(Object), null, int.MaxValue, false, true, null, new MyDataContractResolver(assembly));  
```  
  
 <span data-ttu-id="f5ad5-109">O exemplo, em seguida, serializa os tipos CLR, conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="f5ad5-109">The sample then serializes the CLR types as shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="f5ad5-110">O exemplo, em seguida, desserializa o xsi:types, conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="f5ad5-110">The sample then deserializes the xsi:types as shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="f5ad5-111">Desde personalizado <xref:System.Runtime.Serialization.DataContractResolver> é passada para o <xref:System.Runtime.Serialization.DataContractSerializer> construtor, o <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> é chamado durante a serialização para mapear um tipo CLR para um equivalente `xsi:type`.</span><span class="sxs-lookup"><span data-stu-id="f5ad5-111">Since the custom <xref:System.Runtime.Serialization.DataContractResolver> is passed in to the <xref:System.Runtime.Serialization.DataContractSerializer> constructor, the <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> is called during serialization to map a CLR type to an equivalent `xsi:type`.</span></span> <span data-ttu-id="f5ad5-112">Da mesma forma a <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> é chamado durante a desserialização para mapear o `xsi:type` para um tipo CLR equivalente.</span><span class="sxs-lookup"><span data-stu-id="f5ad5-112">Similarly the <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> is called during deserialization to map the `xsi:type` to an equivalent CLR type.</span></span> <span data-ttu-id="f5ad5-113">Neste exemplo, o <xref:System.Runtime.Serialization.DataContractResolver> é definido como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f5ad5-113">In this sample, the <xref:System.Runtime.Serialization.DataContractResolver> is defined as shown in the following example.</span></span>  
  
 <span data-ttu-id="f5ad5-114">O exemplo de código a seguir é uma classe derivando de <xref:System.Runtime.Serialization.DataContractResolver>.</span><span class="sxs-lookup"><span data-stu-id="f5ad5-114">The following code example is a class deriving from <xref:System.Runtime.Serialization.DataContractResolver>.</span></span>  
  
```  
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
  
 <span data-ttu-id="f5ad5-115">Como parte do exemplo, o projeto de tipos gera o assembly com todos os tipos que são usados neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="f5ad5-115">As part of the sample, the Types project generates the assembly with all the types that are used in this sample.</span></span> <span data-ttu-id="f5ad5-116">Use este projeto para adicionar, remover ou modificar os tipos que serão serializados.</span><span class="sxs-lookup"><span data-stu-id="f5ad5-116">Use this project to add, remove or modify the types that will be serialized.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="f5ad5-117">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="f5ad5-117">To use this sample</span></span>  
  
1.  <span data-ttu-id="f5ad5-118">Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra o arquivo de solução de DCRSample.sln.</span><span class="sxs-lookup"><span data-stu-id="f5ad5-118">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the DCRSample.sln solution file.</span></span>  
  
2.  <span data-ttu-id="f5ad5-119">Para executar a solução, pressione F5</span><span class="sxs-lookup"><span data-stu-id="f5ad5-119">To run the solution, press F5</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f5ad5-120">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="f5ad5-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f5ad5-121">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="f5ad5-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f5ad5-122">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="f5ad5-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f5ad5-123">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="f5ad5-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractResolver`  
  
## <a name="see-also"></a><span data-ttu-id="f5ad5-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f5ad5-124">See Also</span></span>  
 [<span data-ttu-id="f5ad5-125">Usar um resolvedor de contrato de dados</span><span class="sxs-lookup"><span data-stu-id="f5ad5-125">Using a Data Contract Resolver</span></span>](../../../../docs/framework/wcf/feature-details/using-a-data-contract-resolver.md)
