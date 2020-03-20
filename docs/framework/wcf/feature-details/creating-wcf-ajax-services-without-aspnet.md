---
title: Criando serviços WCF AJAX sem ASP.NET
ms.date: 03/30/2017
ms.assetid: ba4a7d1b-e277-4978-9f62-37684e6dc934
ms.openlocfilehash: f4d1d093132c501844aacbaa9cf28ecc3cede442
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185236"
---
# <a name="creating-wcf-ajax-services-without-aspnet"></a>Criando serviços WCF AJAX sem ASP.NET
Os serviços AJAX da Windows Communication Foundation (WCF) podem ser acessados a partir de qualquer página da Web habilitada para JavaScript, sem precisar ASP.NET AJAX. Este tópico descreve como criar tal serviço WCF.  
  
 Para obter instruções sobre como usar o WCF com ASP.NET AJAX, consulte [Criando serviços WCF para ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).  
  
 Existem três partes para criar um serviço WCF AJAX:  
  
- Criando um ponto final AJAX que pode ser acessado a partir do navegador.  
  
- Criação de um contrato de serviço compatível com AJAX.  
  
- Acessando os serviços WCF AJAX.  
  
## <a name="creating-an-ajax-endpoint"></a>Criando um ponto final do AJAX  
 A maneira mais básica de habilitar o suporte a <xref:System.ServiceModel.Activation.WebServiceHostFactory> AJAX em um serviço WCF é usar o arquivo .svc associado ao serviço, como no exemplo a seguir.  
  
```text
<%ServiceHost
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 Alternativamente, você também pode usar a configuração para adicionar um ponto final AJAX. Use <xref:System.ServiceModel.WebHttpBinding> o ponto final do serviço e configure esse ponto final com o <xref:System.ServiceModel.Description.WebHttpBehavior> mostrado no trecho de código a seguir.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="AjaxBehavior">  
          <webHttp/>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <services>  
      <service name="Microsoft.Ajax.Samples.CityService">  
        <endpoint
          address="ajaxEndpoint"  
          behaviorConfiguration="AjaxBehavior"  
          binding="webHttpBinding"  
          contract="Microsoft.Ajax.Samples.ICityService" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 Para um exemplo de trabalho, consulte o [Serviço AJAX com JSON e XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).  
  
## <a name="creating-an-ajax-compatible-service-contract"></a>Criando um contrato de serviço compatível com AJAX  
 Por padrão, os contratos de serviço expostos sobre os dados de retorno de ponto final do AJAX no formato XML. Além disso, as operações de serviço padrão são acessíveis através de solicitações HTTP POST para URLs que incluem o endereço de ponto final seguido pelo nome da operação, como mostrado no exemplo a seguir.  
  
```csharp
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 Esta operação é acessível `http://serviceaddress/endpointaddress/GetCities` usando um POST HTTP para e retornar uma mensagem XML.  
  
 Você pode usar o modelo completo de programação da Web para personalizar esses aspectos básicos. Por exemplo, você <xref:System.ServiceModel.Web.WebGetAttribute> pode <xref:System.ServiceModel.Web.WebInvokeAttribute> usar o ou atributos para controlar o `UriTemplate` verbo HTTP ao qual a operação responde ou usar a propriedade desses respectivos atributos para especificar URIs personalizados. Para obter mais informações, consulte o tópico [WCF Web HTTP Programming Model.](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
  
 O formato de dados JSON é frequentemente usado em serviços AJAX. Para criar uma operação que devolva json em vez de XML, defina a <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> propriedade (ou a) <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>para <xref:System.ServiceModel.Web.WebMessageFormat.Json>. O [tópico De serialização JSON autônomo](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) mostra como os tipos de .NET incorporados e os tipos de contrato de dados mapeiam para JSON.  
  
 Normalmente, as solicitações e respostas do JSON consistem em apenas um item. Para a `GetCities` operação anterior, a solicitação se assemelha à seguinte declaração.  
  
```json
"na"  
```  
  
 A resposta a esse pedido se assemelha à seguinte declaração.  
  
```json
["Nairobi", "Naples", "Nashville"]  
```  
  
 Se a operação tomar um parâmetro extra, o estilo de solicitação deve ser embrulhado para envolver ambos os parâmetros em um único objeto JSON. Um exemplo dessa mensagem JSON de estilo está no exemplo a seguir.  
  
```json  
{"firstLetters": "na", "maxNumber": 2}  
```  
  
 O contrato a seguir aceita esta mensagem.  
  
```csharp
[WebInvoke(BodyStyle=WebMessageBodyStyle.WrappedRequest, ResponseFormat=WebMessageFormat.Json)]  
[OperationContract]  
string[] GetCities(string firstLetters, int maxNumber);  
```  
  
## <a name="accessing-ajax-services"></a>Acessando os serviços AJAX  
 Os pontos finais do WCF AJAX sempre aceitam solicitações JSON e XML.  
  
 As solicitações HTTP POST com um tipo de conteúdo de "application/json" são tratadas como JSON, e aquelas com tipo de conteúdo que indicam XML (por exemplo, "text/xml") são tratadas como XML.  
  
 As solicitações HTTP GET contêm todos os parâmetros de solicitação na própria URL.  
  
 Cabe ao usuário decidir como criar a solicitação HTTP até o ponto final. Além disso, o usuário tem total controle sobre a construção do JSON que forma o corpo da solicitação. Para um exemplo de criação de uma solicitação do JavaScript, consulte o [Serviço AJAX com JSON e XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).
