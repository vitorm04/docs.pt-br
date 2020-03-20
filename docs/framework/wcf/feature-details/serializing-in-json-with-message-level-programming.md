---
title: Serialização em Json com programação de nível de mensagem
ms.date: 03/30/2017
ms.assetid: 5f940ba2-57ee-4c49-a779-957c5e7e71fa
ms.openlocfilehash: 36459dbc0ddee883678a98a27f9abb74fde78e86
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184491"
---
# <a name="serializing-in-json-with-message-level-programming"></a>Serialização em Json com programação de nível de mensagem
O WCF suporta serialização de dados no formato JSON. Este tópico descreve como dizer ao WCF para <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>serializar seus tipos usando o .  
  
## <a name="typed-message-programming"></a>Programação de mensagens digitadas  
 O <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> é usado <xref:System.ServiceModel.Web.WebGetAttribute> quando <xref:System.ServiceModel.Web.WebInvokeAttribute> o ou o é aplicado a uma operação de serviço. Ambos os atributos permitem que você especifique `RequestFormat` e `ResponseFormat`. Para usar JSON para solicitações e respostas. definir ambos para `WebMessageFormat.Json`.  Para usar o JSON, você <xref:System.ServiceModel.WebHttpBinding>deve usar o <xref:System.ServiceModel.Description.WebHttpBehavior>, que configura automaticamente o . Para obter mais informações sobre a serialização do WCF, consulte [Serialização e Desserialização](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md). Para obter mais informações sobre json e WCF, consulte [Service Station - Uma introdução aos serviços restécis com WCF](https://docs.microsoft.com/archive/msdn-magazine/2009/january/service-station-an-introduction-to-restful-services-with-wcf).  
  
> [!IMPORTANT]
> O uso do <xref:System.ServiceModel.WebHttpBinding> JSON requer o uso e <xref:System.ServiceModel.Description.WebHttpBehavior> que não suporta maquetes de comunicação SOAP. Os serviços <xref:System.ServiceModel.WebHttpBinding> que se comunicam com o não suportam expor metadados de serviço para que você não possa usar a funcionalidade de Referência de Serviço do Visual Studio ou a ferramenta de linha de comando svcutil para gerar um proxy do lado do cliente. Para obter mais informações sobre como chamar <xref:System.ServiceModel.WebHttpBinding>programaticamente os serviços que usam, consulte [Como Consumir Serviços de Descanso com o WCF](https://docs.microsoft.com/archive/blogs/pedram/how-to-consume-rest-services-with-wcf).  
  
## <a name="untyped-message-programming"></a>Programação de mensagens não digitadas  
 Ao trabalhar diretamente com objetos de mensagem não digitados, você deve definir explicitamente as propriedades na mensagem não digitada para serializá-la como JSON. O seguinte trecho de código mostra como fazer isso.  
  
```csharp
 Message response = Message.CreateMessage(  
                  MessageVersion.None,    // No SOAP message version  
                             "*",                     // SOAP action, ignored since this is JSON  
                             "Response string: JSON format specified", // Message body  
                             new DataContractJsonSerializer(typeof(string))); // Specify DataContractJsonSerializer  
      response.Properties.Add( WebBodyFormatMessageProperty.Name,
                    new WebBodyFormatMessageProperty(WebContentFormat.Json)); // Use JSON format  
```  
  
## <a name="see-also"></a>Confira também

- [Integração AJAX e suporte para JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)
- [Serialização JSON autônoma](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)
- [Serialização JSON](../../../../docs/framework/wcf/samples/json-serialization.md)
