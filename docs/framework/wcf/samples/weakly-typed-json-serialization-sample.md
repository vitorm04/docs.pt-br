---
title: Weakly-typed JSON Serialization Sample
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b30e501-4ef5-474d-9fad-a9d559cf9c52
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dedf1188afd886c44d897aa1d93ffa226e906ada
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="weakly-typed-json-serialization-sample"></a>Weakly-typed JSON Serialization Sample
Ao serializar um tipo definido pelo usuário em um formato de determinado durante a transmissão ou desserialização de um formato com fio volta para um tipo definido pelo usuário, o determinado tipo definido pelo usuário deve estar disponível no serviço e no cliente. Geralmente, para fazer isso, o <xref:System.Runtime.Serialization.DataContractAttribute> atributo é aplicado a esses tipos definidos pelo usuário e o <xref:System.Runtime.Serialization.DataMemberAttribute> atributo é aplicado a seus membros. Esse mecanismo também se aplica ao trabalhar com objetos de JSON JavaScript Object Notation (), conforme descrito no tópico [como: serializar e desserializar dados de JSON](../../../../docs/framework/wcf/feature-details/how-to-serialize-and-deserialize-json-data.md).  
  
 Em alguns cenários, um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] serviço ou cliente deve acessar objetos JSON gerados por um serviço ou cliente que está fora do controle do desenvolvedor. Como os serviços da Web mais publicamente expõem APIs de JSON, ele pode se tornar impraticável para a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] desenvolvedor para construir locais tipos definidos pelo usuário no qual desserializar objetos do JSON arbitrários. Este exemplo fornece um mecanismo que permite [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] desenvolvedores para trabalhar com objetos JSON desserializados, arbitrários, sem criar tipos definidos pelo usuário. Isso é conhecido como *serialização do tipo fraco* de objetos JSON, como o tipo no qual desserializa um objeto JSON não é conhecido em tempo de compilação.  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Por exemplo, uma API pública do serviço Web retorna o seguinte objeto JSON que descreve algumas informações sobre um usuário do serviço.  
  
```json  
{"personal": {"name": "Paul", "age": 23, "height": 1.7, "isSingle": true, "luckyNumbers": [5,17,21]}, "favoriteBands": ["Band ABC", "Band XYZ"]}  
```  
  
 Para desserializar esse objeto, um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente deve implementar os seguintes tipos definidos pelo usuário.  
  
```  
[DataContract]  
 public class MemberProfile  
 {  
     [DataMember]  
     public PersonalInfo personal;  
  
     [DataMember]  
     public string[] favoriteBands;  
 }  
  
 [DataContract]  
 public class PersonalInfo  
 {  
     [DataMember]  
     public string name;  
  
     [DataMember]  
     public int age;  
  
     [DataMember]  
     public double height;  
  
     [DataMember]  
     public bool isSingle;  
  
     [DataMember]  
     public int[] luckyNumbers;  
 }  
```  
  
 Isso pode ser complicado, especialmente se o cliente deve lidar com mais de um tipo de objeto JSON.  
  
 O `JsonObject` tipo fornecido por este exemplo apresenta uma representação de tipo fraco do objeto JSON desserializado. `JsonObject`depende do mapeamento natural entre objetos JSON e [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dicionários e o mapeamento entre as matrizes JSON e [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] matrizes. O código a seguir mostra o `JsonObject` tipo.  
  
```  
// Instantiation of JsonObject json omitted  
  
string name = json["root"]["personal"]["name"];  
int age = json["root"]["personal"]["age"];  
double height = json["root"]["personal"]["height"];  
bool isSingle = json["root"]["personal"]["isSingle"];  
int[] luckyNumbers = {  
                                     json["root"]["personal"]["luckyNumbers"][0],  
                                     json["root"]["personal"]["luckyNumbers"][1],  
                                     json["root"]["personal"]["luckyNumbers"][2]   
                                 };  
string[] favoriteBands = {  
                                        json["root"]["favoriteBands"][0],  
                                        json["root"]["favoriteBands"][1]  
                                    };  
```  
  
 Observe que você pode "Procurar" matrizes sem a necessidade de declarar o tipo em tempo de compilação e objetos JSON. Para obter uma explicação sobre o requisito de nível superior `["root"]` de objeto, consulte o tópico [mapeamento entre JSON e XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).  
  
> [!NOTE]
>  O `JsonObject` classe é fornecida somente como exemplo. Ele não foi totalmente testado e não deve ser usado em ambientes de produção. Uma implicação óbvia de tipo fraco a serialização JSON é a falta de segurança de tipo ao trabalhar com `JsonObject`.  
  
 Para usar o `JsonObject` tipo, o contrato da operação de cliente deve usar <xref:System.ServiceModel.Channels.Message> como seu tipo de retorno.  
  
```  
[ServiceContract]  
    interface IClientSideProfileService  
    {  
        // There is no need to write a DataContract for the complex type returned by the service.  
        // The client will use a JsonObject to browse the JSON in the received message.  
  
        [OperationContract]  
        [WebGet(ResponseFormat = WebMessageFormat.Json)]  
        Message GetMemberProfile();  
    }  
```  
  
 O `JsonObject` é instanciada, em seguida, conforme mostrado no código a seguir.  
  
```  
// Code to instantiate IClientSideProfileService channel omitted…  
  
// Make a request to the service and obtain the Json response  
XmlDictionaryReader reader = channel.GetMemberProfile().GetReaderAtBodyContents();  
  
// Go through the Json as though it is a dictionary. There is no need to map it to a .NET CLR type.  
JsonObject json = new JsonObject(reader);  
```  
  
 O `JsonObject` construtor usa um <xref:System.Xml.XmlDictionaryReader>, que é obtido por meio de <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> método. O leitor contém uma representação XML da mensagem de JSON recebida pelo cliente. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]o tópico [mapeamento entre JSON e XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).  
  
 O programa produz a seguinte saída:  
  
```  
Service listening at http://localhost:8000/.  
To view the JSON output from the sample, navigate to http://localhost:8000/GetMemberProfile  
This is Paul's page. I am 23 years old and I am 1.7 meters tall.  
I am single.  
My lucky numbers are 5, 17, and 21.  
My favorite bands are Band ABC and Band XYZ.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Compile a solução WeaklyTypedJson.sln conforme descrito em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Execute a solução.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Ajax\WeaklyTypedJson`  
  
## <a name="see-also"></a>Consulte também
