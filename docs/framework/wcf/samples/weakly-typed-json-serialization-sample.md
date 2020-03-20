---
title: Weakly-typed JSON Serialization Sample
ms.date: 03/30/2017
ms.assetid: 0b30e501-4ef5-474d-9fad-a9d559cf9c52
ms.openlocfilehash: bdeaffe31ba9bced28eebcfe294fc9944e5d05d0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143584"
---
# <a name="weakly-typed-json-serialization-sample"></a>Weakly-typed JSON Serialization Sample
Ao serializar um tipo definido pelo usuário para um determinado formato de fio ou desserializar um formato de fio de volta para um tipo definido pelo usuário, o determinado tipo definido pelo usuário deve estar disponível tanto no serviço quanto no cliente. Normalmente, para <xref:System.Runtime.Serialization.DataContractAttribute> isso, o atributo é aplicado <xref:System.Runtime.Serialization.DataMemberAttribute> a esses tipos definidos pelo usuário e o atributo é aplicado aos seus membros. Esse mecanismo também se aplica ao trabalhar com objetos JSON (JavaScript Object Notation, notação de objetos javascript), conforme descrito no tópico [Como: Serializar e Desserializar dados JSON](../../../../docs/framework/wcf/feature-details/how-to-serialize-and-deserialize-json-data.md).  
  
 Em alguns cenários, um serviço ou cliente da Windows Communication Foundation (WCF) deve acessar objetos JSON gerados por um serviço ou cliente que esteja fora do controle do desenvolvedor. À medida que mais serviços da Web expõem publicamente as APIs JSON, pode se tornar impraticável para o desenvolvedor wcf construir tipos locais definidos pelo usuário para desserializar objetos JSON arbitrários. Esta amostra fornece um mecanismo que permite que os desenvolvedores do WCF trabalhem com objetos JSON desserializados e arbitrários, sem criar tipos definidos pelo usuário. Isso é conhecido como *serialização fracamente digitada* de objetos JSON, porque o tipo no qual um objeto JSON desserializa não é conhecido no momento da compilação.  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
 Por exemplo, uma API de serviço web público retorna o seguinte objeto JSON, que descreve algumas informações sobre um usuário do serviço.  
  
```json  
{"personal": {"name": "Paul", "age": 23, "height": 1.7, "isSingle": true, "luckyNumbers": [5,17,21]}, "favoriteBands": ["Band ABC", "Band XYZ"]}  
```  
  
 Para desserializar esse objeto, um cliente WCF deve implementar os seguintes tipos definidos pelo usuário.  
  
```csharp  
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
  
 Isso pode ser complicado, especialmente se o cliente tiver que lidar com mais de um tipo de objeto JSON.  
  
 O `JsonObject` tipo fornecido por esta amostra introduz uma representação fracamente digitada do objeto JSON desserializado. `JsonObject`depende do mapeamento natural entre objetos JSON e dicionários .NET Framework, e no mapeamento entre matrizes JSON e matrizes .NET Framework. O código a `JsonObject` seguir mostra o tipo.  
  
```csharp  
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
  
 Observe que você pode "navegar" objetos e matrizes JSON sem a necessidade de declarar seu tipo na hora da compilação. Para obter uma explicação sobre a `["root"]` exigência do objeto de nível superior, consulte o tópico [Mapeamento entre JSON e XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).  
  
> [!NOTE]
> A `JsonObject` classe é fornecida apenas como um exemplo. Não foi minuciosamente testado e não deve ser utilizado em ambientes de produção. Uma implicação óbvia da serialização JSON de tipo fraca é `JsonObject`a falta de segurança do tipo ao trabalhar com .  
  
 Para utilizar `JsonObject` o tipo, o <xref:System.ServiceModel.Channels.Message> contrato de operação do cliente deve usar como seu tipo de retorno.  
  
```csharp  
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
  
 O `JsonObject` é então instanciado como mostrado no código a seguir.  
  
```csharp  
// Code to instantiate IClientSideProfileService channel omitted…  
  
// Make a request to the service and obtain the Json response  
XmlDictionaryReader reader = channel.GetMemberProfile().GetReaderAtBodyContents();  
  
// Go through the Json as though it is a dictionary. There is no need to map it to a .NET CLR type.  
JsonObject json = new JsonObject(reader);  
```  
  
 O `JsonObject` construtor pega <xref:System.Xml.XmlDictionaryReader>um , que <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> é obtido através do método. O leitor contém uma representação XML da mensagem JSON recebida pelo cliente. Para obter mais informações, consulte o tópico [Mapeamento entre JSON e XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).  
  
 O programa produz a seguinte saída:  
  
```console  
Service listening at http://localhost:8000/.  
To view the JSON output from the sample, navigate to http://localhost:8000/GetMemberProfile  
This is Paul's page. I am 23 years old and I am 1.7 meters tall.  
I am single.  
My lucky numbers are 5, 17, and 21.  
My favorite bands are Band ABC and Band XYZ.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Construa a solução WeaklyTypedJson.sln conforme descrito na [Construção da Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Execute a solução.  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Ajax\WeaklyTypedJson`  
