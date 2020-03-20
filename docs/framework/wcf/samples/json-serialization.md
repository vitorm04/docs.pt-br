---
title: Amostra de DataContractJsonSerializer
ms.date: 03/30/2017
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
ms.openlocfilehash: d3456582d73640f1802c17d7f29f4931a6f920b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144624"
---
# <a name="datacontractjsonserializer-sample"></a>Amostra de DataContractJsonSerializer

> [!NOTE]
> Esta amostra <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>é para. Para a maioria dos cenários que envolvem serialização e desserialização do JSON, recomendamos as APIs no [namespace System.Text.Json](../../../standard/serialization/system-text-json-overview.md).

O <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> dá suporte aos mesmos tipos que o <xref:System.Runtime.Serialization.DataContractSerializer>. O formato de dados JSON é especialmente útil ao escrever aplicativos Web de estilo AJAX (Asynchronous JavaScript and XML). O suporte a AJAX no Windows Communication Foundation (WCF) é otimizado para uso com ASP.NET AJAX através do controle ScriptManager. Para exemplos de como usar o Windows Communication Foundation (WCF) com ASP.NET AJAX, consulte as [amostras AJAX](ajax.md).  
  
Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.  
  
Este exemplo usa um contrato de dados `Person` para demonstrar a serialização e a desserialização.  

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

 Para serializar uma instância do tipo `Person` para JSON, crie primeiro o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> e use o método `WriteObject` para gravar dados JSON em um fluxo.  

```csharp
Person p = new Person();
//Set up Person object...
MemoryStream stream1 = new MemoryStream();
DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));
ser.WriteObject(stream1, p);
```

 O fluxo de memória contém dados JSON válidos.
  
```json  
{"age":42,"name":"John"}  
```  
  
 O exemplo demonstra a desserialização de dados JSON em um objeto. Em seguida, você volta o fluxo e chama `ReadObject`.  

```csharp
Person p2 = (Person)ser.ReadObject(stream1);
```

 Examinar o objeto `p2` revela que os dados JSON foram desserializados corretamente.  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar e executar o exemplo  
  
1. Construa a solução JsonSerialization.sln conforme descrito na [Construção do Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Execute o aplicativo de console resultante.  
