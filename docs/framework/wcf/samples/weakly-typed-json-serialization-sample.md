---
title: Weakly-typed JSON Serialization Sample
ms.date: 03/30/2017
ms.assetid: 0b30e501-4ef5-474d-9fad-a9d559cf9c52
ms.openlocfilehash: 212a5ea362600e833303711b750d1c7a0f7252b6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676049"
---
# <a name="weakly-typed-json-serialization-sample"></a>Weakly-typed JSON Serialization Sample
Ao serializar um tipo definido pelo usuário para um formato com fio fornecida ou desserialização de um formato com fio volta para um tipo definido pelo usuário, de determinado tipo definido pelo usuário deve estar disponível no serviço e no cliente. Normalmente, para fazer isso, o <xref:System.Runtime.Serialization.DataContractAttribute> atributo é aplicado a esses tipos definidos pelo usuário e o <xref:System.Runtime.Serialization.DataMemberAttribute> atributo é aplicado aos seus membros. Esse mecanismo também se aplica ao trabalhar com objetos de notação JSON (JavaScript Object), conforme descrito no tópico [como: Serializar e desserializar dados JSON](../../../../docs/framework/wcf/feature-details/how-to-serialize-and-deserialize-json-data.md).  
  
 Em alguns cenários, um serviço Windows Communication Foundation (WCF) ou o cliente deve acessar objetos JSON gerados por um serviço ou cliente que está fora do controle do desenvolvedor. Conforme mais serviços Web expõem publicamente as APIs de JSON, ele pode se tornar impraticável para o desenvolvedor do WCF construir os tipos de locais definidas pelo usuário no qual desserializar objetos JSON arbitrários. Este exemplo fornece um mecanismo que permite que os desenvolvedores do WCF trabalhar com objetos JSON arbitrários, desserializados, sem criar tipos definidos pelo usuário. Isso é conhecido como *serialização com tipagem fraca* de objetos JSON, porque o tipo no qual desserializa um objeto JSON não é conhecido em tempo de compilação.  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Por exemplo, uma API pública do serviço Web retorna o seguinte objeto JSON que descreve algumas informações sobre um usuário do serviço.  
  
```json  
{"personal": {"name": "Paul", "age": 23, "height": 1.7, "isSingle": true, "luckyNumbers": [5,17,21]}, "favoriteBands": ["Band ABC", "Band XYZ"]}  
```  
  
 Para desserializar esse objeto, um cliente WCF deve implementar os seguintes tipos definidos pelo usuário.  
  
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
  
 O `JsonObject` tipo fornecido por este exemplo apresenta uma representação com tipagem fraca do objeto JSON desserializado. `JsonObject` depende do mapeamento natural entre objetos JSON e [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dicionários e o mapeamento entre matrizes JSON e [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] matrizes. O seguinte código mostra o `JsonObject` tipo.  
  
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
  
 Observe que você pode "Procurar" objetos JSON e matrizes sem a necessidade de declarar o tipo de tempo de compilação. Para obter uma explicação da exigência de nível superior `["root"]` do objeto, consulte o tópico [mapeamento entre JSON e XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).  
  
> [!NOTE]
>  O `JsonObject` classe é fornecida como apenas um exemplo. Ele não foi totalmente testado e não deve ser usado em ambientes de produção. Uma implicação óbvia de serialização de JSON com tipagem fraca é a falta de segurança de tipos ao trabalhar com `JsonObject`.  
  
 Para usar o `JsonObject` tipo de contrato de operação do cliente deve usar <xref:System.ServiceModel.Channels.Message> como seu tipo de retorno.  
  
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
  
 O `JsonObject` construtor usa um <xref:System.Xml.XmlDictionaryReader>, que é obtido por meio de <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> método. O leitor contém uma representação XML da mensagem JSON recebida pelo cliente. Para obter mais informações, consulte o tópico [mapeamento entre JSON e XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).  
  
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
  
1.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Compile a solução WeaklyTypedJson.sln, conforme descrito em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Execute a solução.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Ajax\WeaklyTypedJson`  
  
## <a name="see-also"></a>Consulte também
