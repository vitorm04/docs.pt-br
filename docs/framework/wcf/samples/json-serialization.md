---
title: Exemplo de DataContractJsonSerializer
ms.date: 03/30/2017
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
ms.openlocfilehash: 509f80812bb815e4fa56fa3ebdc9236ac0622ace
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141826"
---
# <a name="datacontractjsonserializer-sample"></a><span data-ttu-id="2dfde-102">Exemplo de DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="2dfde-102">DataContractJsonSerializer sample</span></span>

> [!NOTE]
> <span data-ttu-id="2dfde-103">Este exemplo é para <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="2dfde-103">This sample is for <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span> <span data-ttu-id="2dfde-104">Para a maioria dos cenários que envolvem a serialização e desserialização do JSON, recomendamos as ferramentas no [namespace System. Text. JSON](../../../standard/serialization/system-text-json-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2dfde-104">For most scenarios that involve serializing and deserializing JSON, we recommend the tools in the [System.Text.Json namespace](../../../standard/serialization/system-text-json-overview.md).</span></span> 

<span data-ttu-id="2dfde-105">O <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> dá suporte aos mesmos tipos que o <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="2dfde-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> supports the same types as <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="2dfde-106">O formato de dados JSON é especialmente útil ao escrever aplicativos Web de estilo AJAX (Asynchronous JavaScript and XML).</span><span class="sxs-lookup"><span data-stu-id="2dfde-106">The JSON data format is especially useful when writing Asynchronous JavaScript and XML (AJAX)-style Web applications.</span></span> <span data-ttu-id="2dfde-107">O suporte ao AJAX no Windows Communication Foundation (WCF) é otimizado para uso com o ASP.NET AJAX por meio do controle ScriptManager.</span><span class="sxs-lookup"><span data-stu-id="2dfde-107">AJAX support in Windows Communication Foundation (WCF) is optimized for use with ASP.NET AJAX through the ScriptManager control.</span></span> <span data-ttu-id="2dfde-108">Para obter exemplos de como usar o Windows Communication Foundation (WCF) com o ASP.NET AJAX, consulte os [exemplos do AJAX](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="2dfde-108">For examples of how to use Windows Communication Foundation (WCF) with ASP.NET AJAX, see the [AJAX Samples](ajax.md).</span></span>  
  
<span data-ttu-id="2dfde-109">Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="2dfde-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
<span data-ttu-id="2dfde-110">Este exemplo usa um contrato de dados `Person` para demonstrar a serialização e a desserialização.</span><span class="sxs-lookup"><span data-stu-id="2dfde-110">The sample uses a `Person` data contract to demonstrate serialization and deserialization.</span></span>  

```csharp
[DataContract]
class Person
{
    [DataMember]
    internal string name;

    [DataMember]
    internal int age;
}
```

 <span data-ttu-id="2dfde-111">Para serializar uma instância do tipo `Person` para JSON, crie primeiro o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> e use o método `WriteObject` para gravar dados JSON em um fluxo.</span><span class="sxs-lookup"><span data-stu-id="2dfde-111">To serialize an instance of the `Person` type to JSON, create the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> first and use the `WriteObject` method to write JSON data to a stream.</span></span>  

```csharp
Person p = new Person();
//Set up Person object...
MemoryStream stream1 = new MemoryStream();
DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));
ser.WriteObject(stream1, p);
```

 <span data-ttu-id="2dfde-112">O fluxo de memória contém dados JSON válidos.</span><span class="sxs-lookup"><span data-stu-id="2dfde-112">The memory stream contains valid JSON data.</span></span>
  
```json  
{"age":42,"name":"John"}  
```  
  
 <span data-ttu-id="2dfde-113">O exemplo demonstra a desserialização de dados JSON em um objeto.</span><span class="sxs-lookup"><span data-stu-id="2dfde-113">The sample demonstrates deserializing from JSON data into an object.</span></span> <span data-ttu-id="2dfde-114">Em seguida, você volta o fluxo e chama `ReadObject`.</span><span class="sxs-lookup"><span data-stu-id="2dfde-114">You then rewind the stream and call `ReadObject`.</span></span>  

```csharp
Person p2 = (Person)ser.ReadObject(stream1);
```

 <span data-ttu-id="2dfde-115">Examinar o objeto `p2` revela que os dados JSON foram desserializados corretamente.</span><span class="sxs-lookup"><span data-stu-id="2dfde-115">Examining the `p2` object reveals that the JSON data has been deserialized correctly.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2dfde-116">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="2dfde-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2dfde-117">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="2dfde-117">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="2dfde-118">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="2dfde-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2dfde-119">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="2dfde-119">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2dfde-120">Para configurar, compilar e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="2dfde-120">To set up, build and run the sample</span></span>  
  
1. <span data-ttu-id="2dfde-121">Crie a solução JsonSerialization. sln, conforme descrito em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2dfde-121">Build the solution JsonSerialization.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="2dfde-122">Execute o aplicativo de console resultante.</span><span class="sxs-lookup"><span data-stu-id="2dfde-122">Run the resulting console application.</span></span>  
