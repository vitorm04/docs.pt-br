---
title: Interoperabilidade com aplicativos de POX
ms.date: 03/30/2017
ms.assetid: 449276b8-4633-46f0-85c9-81f01d127636
ms.openlocfilehash: 7522233723b6b91d5a7b27d3f82ca328e29ce3f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="interoperability-with-pox-applications"></a>Interoperabilidade com aplicativos de POX
"Plain Old XML" (POX) os aplicativos se comunicam troca de mensagens HTTP brutas que contêm apenas dados de aplicativo XML que não são incluídos em um envelope SOAP. Windows Communication Foundation (WCF) pode fornecer serviços e clientes que usam mensagens POX. O serviço WCF pode ser usado para implementar serviços que expõem pontos de extremidade para os clientes, como navegadores da Web e linguagens de script que enviar e recebem mensagens POX. No cliente, o modelo de programação WCF pode ser usado para implementar a clientes que se comunicam com serviços baseados em POX.  
  
> [!NOTE]
>  Este documento foi gravado originalmente para o [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0.  [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.5 tem suporte interno para trabalhar com aplicativos de POX. Para obter mais informações sobre consulte [modelo de programação do WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
  
## <a name="pox-programming-with-wcf"></a>Programação de POX com WCF  
 Serviços WCF que se comunicam por HTTP usando mensagens POX, use um [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
```xml  
<customBinding>  
   <binding name="poxServerBinding">  
       <textMessageEncoding messageVersion="None" />  
       <httpTransport />  
   </binding>  
</customBinding>  
```  
  
 Essa associação personalizada contém dois elementos:  
  
-   O [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) e  
  
-   O [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).  
  
 O padrão de codificador de mensagem de texto do WCF é especialmente configurado para usar o <xref:System.ServiceModel.Channels.MessageVersion.None%2A> valor, o que permite processar XML cargas de mensagem que não chegam encapsuladas em um envelope SOAP.  
  
 Clientes do WCF que se comunicam por HTTP usando mensagens POX usam uma associação semelhante (mostrada no seguinte código obrigatório).  
  
```  
private static Binding CreatePoxBinding()  
{  
    TextMessageEncodingBindingElement encoder =   
    new TextMessageEncodingBindingElement( MessageVersion.None, Encoding.UTF8 );  
    HttpTransportBindingElement transport = new HttpTransportBindingElement();  
    transport.ManualAddressing = true;  
    return new CustomBinding( new BindingElement[] { encoder, transport } );  
}   
```  
  
 Como clientes POX devem especificar explicitamente os URIs que enviam mensagens, eles geralmente devem configurar o <xref:System.ServiceModel.Channels.HttpTransportBindingElement> para um modo de endereçamento manual definindo a <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> propriedade `true` no elemento. Isso permite que mensagens sejam tratados explicitamente pelo código do aplicativo e não é necessário criar um novo <xref:System.ServiceModel.ChannelFactory> toda vez que um aplicativo envia uma mensagem para um URI diferente de HTTP.  
  
 Como mensagens POX não usar cabeçalhos SOAP para transmitir informações importantes de protocolo, clientes POX e serviços geralmente devem manipular partes da solicitação HTTP subjacente usado para enviar ou receber uma mensagem. Informações de protocolo HTTP específicas, como os cabeçalhos HTTP e códigos de status são expostas no modelo de programação WCF por meio de duas classes:  
  
-   <xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, que contém informações sobre a solicitação HTTP, como os cabeçalhos de solicitação e o método HTTP.  
  
-   <xref:System.ServiceModel.Channels.HttpResponseMessageProperty>, que contém informações sobre a resposta HTTP, como a descrição de status e o código de status HTTP, bem como quaisquer cabeçalhos de resposta HTTP.  
  
 O exemplo de código a seguir mostra como criar uma mensagem de solicitação HTTP GET é endereçada a http://localhost:8100/customers.  
  
```  
Message request = Message.CreateMessage( MessageVersion.None, String.Empty );  
request.Headers.To = "http://localhost:8100/customers";  
  
HttpRequestMessageProperty property = new HttpRequestMessageProperty();  
property.Method = "GET";  
property.SuppressEntityBody = true;  
request.Properties.Add( HttpRequestMessageProperty.Name, property );  
```  
  
 Primeiro, uma solicitação vazia <xref:System.ServiceModel.Channels.Message> é criado chamando <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29>. O <xref:System.ServiceModel.Channels.MessageVersion.None%2A> parâmetro é usado para indicar que não é necessário um envelope SOAP e <xref:System.String.Empty> parâmetro é passado como a ação. A mensagem de solicitação é processada definindo <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> cabeçalho para o URI desejado. Em seguida, uma <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> é criado e o <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> está definido para o verbo HTTP GET método e o <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> é definido como `true` para indicar que nenhum dado deve ser enviado no corpo da mensagem de solicitação HTTP de saída. Por fim, a propriedade de solicitação é adicionada para o <xref:System.ServiceModel.Channels.Message.Properties%2A> coleção da mensagem de solicitação para que ele pode influenciar como o transporte HTTP envia a solicitação. A mensagem está pronta para ser enviados em uma instância apropriada do <xref:System.ServiceModel.Channels.IRequestChannel>.  
  
 Técnicas semelhantes podem ser usadas no serviço para extrair a <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> de uma mensagem de entrada e a construção de uma resposta.
