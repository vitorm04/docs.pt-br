---
title: Serialização em Json com programação de nível de mensagem
ms.date: 03/30/2017
ms.assetid: 5f940ba2-57ee-4c49-a779-957c5e7e71fa
ms.openlocfilehash: 9c5ad29e2ddbdde3ae560c4ff2af224bc3a71ad9
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43855695"
---
# <a name="serializing-in-json-with-message-level-programming"></a>Serialização em Json com programação de nível de mensagem
O WCF oferece suporte à serialização de dados no formato JSON. Este tópico descreve como informar ao WCF para serializar seus tipos usando o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
## <a name="typed-message-programming"></a>Programação de mensagem digitada  
 O <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> é usado quando o <xref:System.ServiceModel.Web.WebGetAttribute> ou o <xref:System.ServiceModel.Web.WebInvokeAttribute> é aplicado a uma operação de serviço. Ambos os atributos permitem que você especifique o `RequestFormat` e `ResponseFormat`. Para usar JSON para solicitações e respostas, defina ambos como `WebMessageFormat.Json`.  Para usar JSON, você deve usar o <xref:System.ServiceModel.WebHttpBinding> que configura automaticamente o <xref:System.ServiceModel.Description.WebHttpBehavior>. Para obter mais informações sobre a serialização WCF, consulte: [serialização e desserialização](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md), [serialização no Windows Communication Foundation](https://msdn.microsoft.com/magazine/cc163569.aspx). Para obter mais informações sobre JSON e WCF, consulte [uma introdução aos serviços RESTfull com WCF](https://msdn.microsoft.com/magazine/dd315413.aspx), [habilitados por JSON criando serviços do WCF no .NET 3.5](http://www.pluralsight-training.net/community/blogs/fritz/archive/2008/01/31/50121.aspx), e [visão geral do REST no WCF](https://msdn.microsoft.com/netframework/dd547388).  
  
> [!IMPORTANT]
>  Usar o JSON exige o uso de <xref:System.ServiceModel.WebHttpBinding> e <xref:System.ServiceModel.Description.WebHttpBehavior> que não dão suporte a comunicação com o SOAP. Serviços que se comunicam com o <xref:System.ServiceModel.WebHttpBinding> não dão suporte a expor metadados de serviço para que você não poderá usar a funcionalidade Adicionar referência de serviço do Visual Studio ou a ferramenta de linha de comando svcutil para gerar um proxy do lado do cliente. Para obter mais informações, como você pode chamar programaticamente os serviços que usam <xref:System.ServiceModel.WebHttpBinding>, consulte [como consumir serviços REST com WCF](https://blogs.msdn.com/b/pedram/archive/2008/04/21/how-to-consume-rest-services-with-wcf.aspx).  
  
## <a name="untyped-message-programming"></a>Programação de mensagem não tipada  
 Ao trabalhar diretamente com objetos de mensagem sem tipo, você deve definir explicitamente as propriedades na mensagem não tipada serializá-lo como JSON. O trecho de código a seguir mostra como fazer isso.  
  
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
 [Integração AJAX e suporte para JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 [Serialização JSON autônoma](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md)  
 [Serialização JSON](../../../../docs/framework/wcf/samples/json-serialization.md)
