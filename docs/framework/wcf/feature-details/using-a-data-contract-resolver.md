---
title: Utilizando um resolvedor de contrato de dados
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e68a16c-36f0-4df4-b763-32021bff2b89
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28bba68c985191b69fea3b7ab85812917a827b30
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="using-a-data-contract-resolver"></a>Utilizando um resolvedor de contrato de dados
Um resolvedor de contrato de dados permite que você configure tipos conhecidos dinamicamente. Tipos conhecidos são necessários ao serializar ou desserializar um tipo que não se espera por um contrato de dados. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md). Tipos conhecidos normalmente são especificados estaticamente. Isso significa que você precisa saber os possíveis tipos de uma operação pode ser exibida ao implementar a operação. Há cenários em que isso não é verdadeiro e ser capaz de especificar tipos conhecidos dinamicamente é importante.  
  
## <a name="creating-a-data-contract-resolver"></a>Criação de um resolvedor de contrato de dados  
 A criação de um resolvedor de contrato de dados envolve a implementação de dois métodos, <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> e <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>. Esses dois métodos implementam retornos de chamada que são usados durante a serialização e desserialização, respectivamente. O <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> método é chamado durante a serialização e usa um tipo de contrato de dados e mapeia para um `xsi:type` nome e namespace. O <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> método é chamado durante a desserialização e usa um `xsi:type` nome e namespace e resolve para um tipo de contrato de dados. Esses dois métodos têm um `knownTypeResolver` parâmetro que pode ser usado para usar o padrão conhecido de resolvedor de tipo em sua implementação.  
  
 O exemplo a seguir mostra como implementar um <xref:System.Runtime.Serialization.DataContractResolver> para mapear para e de um tipo de contrato de dados denominado `Customer` derivado de um tipo de contrato de dados `Person`.  
  
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
  
 Depois que você tenha definido um <xref:System.Runtime.Serialization.DataContractResolver> você pode usá-lo, passando-o para o <xref:System.Runtime.Serialization.DataContractSerializer> construtor conforme mostrado no exemplo a seguir.  
  
```  
XmlObjectSerializer serializer = new DataContractSerializer(typeof(Customer), null, Int32.MaxValue, false, false, null, new MyCustomerResolver());  
```  
  
 Você pode especificar um <xref:System.Runtime.Serialization.DataContractSerializer> em uma chamada para o <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A> ou <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A> métodos, como mostrado no exemplo a seguir.  
  
```  
MemoryStream ms = new MemoryStream();  
DataContractSerializer serializer = new DataContractSerializer(typeof(Customer));  
XmlDictionaryWriter writer = XmlDictionaryWriter.CreateDictionaryWriter(XmlWriter.Create(ms));  
serializer.WriteObject(writer, new Customer(), new MyCustomerResolver());  
writer.Flush();  
ms.Position = 0;  
Console.WriteLine(((Customer)serializer.ReadObject(XmlDictionaryReader.CreateDictionaryReader(XmlReader.Create(ms)), false, new MyCustomerResolver()));  
```  
  
 Ou você pode definir o <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> conforme mostrado no exemplo a seguir.  
  
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
  
 Você pode especificar um resolvedor de contrato de dados declarativamente implementando um atributo que pode ser aplicado a um serviço.  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]o [KnownAssemblyAttribute](../../../../docs/framework/wcf/samples/knownassemblyattribute.md) exemplo. Este exemplo implementa um atributo chamado "KnownAssembly" que adiciona um resolvedor de contrato de dados personalizados para o comportamento do serviço.  
  
## <a name="see-also"></a>Consulte também  
 [Tipos conhecidos de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [Exemplo de DataContractSerializer](../../../../docs/framework/wcf/samples/datacontractserializer-sample.md)  
 [KnownAssemblyAttribute](../../../../docs/framework/wcf/samples/knownassemblyattribute.md)
