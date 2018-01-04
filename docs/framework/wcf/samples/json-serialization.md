---
title: "Serialização JSON"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b2835b77c1844c74e04c9ccf7ddaaa4f9fb60dba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="json-serialization"></a>Serialização JSON
Este exemplo demonstra como usar o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> para serializar e desserializar dados no formato JSON (JavaScript Object Notation). Esse mecanismo de serialização converte dados JSON em instâncias de tipos [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] e de volta em dados JSON. O <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> dá suporte aos mesmos tipos que o <xref:System.Runtime.Serialization.DataContractSerializer>. O formato de dados JSON é especialmente útil ao escrever aplicativos Web de estilo AJAX (Asynchronous JavaScript and XML). O suporte a AJAX no [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] é otimizado para uso com AJAX do ASP.NET por meio do controle ScriptManager. Para obter exemplos de como usar [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] com o ASP.NET AJAX, consulte o [AJAX exemplos](http://msdn.microsoft.com/en-us/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).  
  
> [!NOTE]
>  Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.  
  
 Este exemplo usa um contrato de dados `Person` para demonstrar a serialização e a desserialização.  
  
```  
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
  
```  
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
  
```  
Person p2 = (Person)ser.ReadObject(stream1);  
```  
  
 Examinar o objeto `p2` revela que os dados JSON foram desserializados corretamente.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar e executar o exemplo  
  
1.  Compile a solução JsonSerialization.sln conforme descrito em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Execute o aplicativo de console resultante.  
  
## <a name="see-also"></a>Consulte também
