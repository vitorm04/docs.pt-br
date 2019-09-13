---
title: Serialização em Json com programação de nível de mensagem
ms.date: 03/30/2017
ms.assetid: 5f940ba2-57ee-4c49-a779-957c5e7e71fa
ms.openlocfilehash: f50f6a699dff54e3d0950f5ce0e1049217b9dc45
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928739"
---
# <a name="serializing-in-json-with-message-level-programming"></a>Serialização em Json com programação de nível de mensagem
O WCF dá suporte à serialização de dados no formato JSON. Este tópico descreve como informar ao WCF para serializar seus tipos usando <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>o.  
  
## <a name="typed-message-programming"></a>Programação de mensagens digitadas  
 O <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> é usado quando o <xref:System.ServiceModel.Web.WebGetAttribute> ou o <xref:System.ServiceModel.Web.WebInvokeAttribute> é aplicado a uma operação de serviço. Ambos os atributos permitem que você especifique o e `RequestFormat` `ResponseFormat`o. Para usar JSON para solicitações e respostas. Defina ambos como `WebMessageFormat.Json`.  Para usar o JSON, você deve usar o <xref:System.ServiceModel.WebHttpBinding>, que configura automaticamente o. <xref:System.ServiceModel.Description.WebHttpBehavior> Para obter mais informações sobre a serialização do WCF, consulte [serialização e desserialização](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md). Para obter mais informações sobre JSON e WCF, consulte [Service Station-uma introdução aos serviços RESTful com o WCF](https://msdn.microsoft.com/magazine/dd315413.aspx).  
  
> [!IMPORTANT]
> O uso do JSON requer <xref:System.ServiceModel.WebHttpBinding> o <xref:System.ServiceModel.Description.WebHttpBehavior> uso de e que não oferece suporte à comunicação SOAP. Serviços que se comunicam <xref:System.ServiceModel.WebHttpBinding> com o não dão suporte à exposição de metadados de serviço, portanto, você não poderá usar a funcionalidade de Adicionar referência de serviço do Visual Studio ou a ferramenta de linha de comando svcutil para gerar um proxy do lado do cliente. Para obter mais informações sobre como chamar programaticamente os <xref:System.ServiceModel.WebHttpBinding>serviços que usam o, consulte [como consumir serviços REST com o WCF](https://blogs.msdn.microsoft.com/pedram/2008/04/21/how-to-consume-rest-services-with-wcf/).  
  
## <a name="untyped-message-programming"></a>Programação de mensagens não tipadas  
 Ao trabalhar diretamente com objetos de mensagem não tipados, você deve definir explicitamente as propriedades na mensagem não tipada para serializá-la como JSON. O trecho de código a seguir mostra como fazer isso.  
  
```  
 Message response = Message.CreateMessage(  
                  MessageVersion.None,    // No SOAP message version  
                             "*",                     // SOAP action, ignored since this is JSON  
                             "Response string: JSON format specified", // Message body  
                             new DataContractJsonSerializer(typeof(string))); // Specify DataContractJsonSerializer  
      response.Properties.Add( WebBodyFormatMessageProperty.Name,   
                    new WebBodyFormatMessageProperty(WebContentFormat.Json)); // Use JSON format  
```  
  
## <a name="see-also"></a>Consulte também

- [Integração AJAX e suporte para JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)
- [Serialização JSON autônoma](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)
- [Serialização JSON](../../../../docs/framework/wcf/samples/json-serialization.md)
