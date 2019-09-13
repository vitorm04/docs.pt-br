---
title: Criando serviços WCF AJAX sem ASP.NET
ms.date: 03/30/2017
ms.assetid: ba4a7d1b-e277-4978-9f62-37684e6dc934
ms.openlocfilehash: 04d2831407f4aa32c72aabbbff0e6fdde769bd23
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895094"
---
# <a name="creating-wcf-ajax-services-without-aspnet"></a>Criando serviços WCF AJAX sem ASP.NET
Os serviços do Windows Communication Foundation (WCF) AJAX podem ser acessados em qualquer página da Web habilitada para JavaScript, sem a necessidade do AJAX ASP.NET. Este tópico descreve como criar um serviço WCF desse tipo.  
  
 Para obter instruções sobre como usar o WCF com o ASP.NET AJAX, consulte [CREATING WCF Services for ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).  
  
 Há três partes para criar um serviço WCF AJAX:  
  
- Criar um ponto de extremidade AJAX que pode ser acessado no navegador.  
  
- Criando um contrato de serviço compatível com AJAX.  
  
- Acessando os serviços WCF AJAX.  
  
## <a name="creating-an-ajax-endpoint"></a>Criando um ponto de extremidade AJAX  
 A maneira mais básica de habilitar o suporte a Ajax em um serviço WCF é usar <xref:System.ServiceModel.Activation.WebServiceHostFactory> o no arquivo. svc associado ao serviço, como no exemplo a seguir.  
  
```text
<%ServiceHost   
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 Como alternativa, você também pode usar a configuração para adicionar um ponto de extremidade AJAX. Use o <xref:System.ServiceModel.WebHttpBinding> no ponto de extremidade de serviço e configure esse ponto <xref:System.ServiceModel.Description.WebHttpBehavior> de extremidade com o conforme mostrado no trecho de código a seguir.  
  
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
  
 Para obter um exemplo funcional, consulte o [serviço AJAX com JSON e XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).  
  
## <a name="creating-an-ajax-compatible-service-contract"></a>Criando um contrato de serviço compatível com AJAX  
 Por padrão, os contratos de serviço expostos em um ponto de extremidade AJAX retornam dados no formato XML. Além disso, por padrão, as operações de serviço são acessíveis por meio de solicitações HTTP POST para URLs que incluem o endereço do ponto de extremidade seguido pelo nome da operação, conforme mostrado no exemplo a seguir.  
  
```csharp
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 Essa operação pode ser acessada usando um `http://serviceaddress/endpointaddress/GetCities` http post para e retornar uma mensagem XML.  
  
 Você pode usar o modelo de programação da Web completo para personalizar esses aspectos básicos. Por exemplo, você pode usar os <xref:System.ServiceModel.Web.WebGetAttribute> atributos <xref:System.ServiceModel.Web.WebInvokeAttribute> ou para controlar o verbo HTTP para o qual a operação responde ou usa `UriTemplate` a propriedade desses respectivos atributos para especificar URIs personalizados. Para obter mais informações, consulte o tópico [modelo de programação Web http do WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md) .  
  
 O formato de dados JSON é geralmente usado em serviços AJAX. Para criar uma operação que retorne JSON em vez de XML, <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> defina a propriedade <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>(ou) <xref:System.ServiceModel.Web.WebMessageFormat.Json>como. O tópico de [SERIALIZAÇÃO JSON](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) autônoma mostra como os tipos .net internos e os tipos de contrato de dados são mapeados para JSON.  
  
 Normalmente, as solicitações e respostas JSON consistem em apenas um item. Para a operação `GetCities` anterior, a solicitação é semelhante à instrução a seguir.  
  
```json
"na"  
```  
  
 A resposta a essa solicitação é semelhante à instrução a seguir.  
  
```json
["Nairobi", "Naples", "Nashville"]  
```  
  
 Se a operação usar um parâmetro extra, o estilo da solicitação deverá ser encapsulado para encapsular ambos os parâmetros em um único objeto JSON. Um exemplo dessa mensagem de estilo JSON está no exemplo a seguir.  
  
```json  
{"firstLetters": "na", "maxNumber": 2}  
```  
  
 O contrato a seguir aceita esta mensagem.  
  
```csharp
[WebInvoke(BodyStyle=WebMessageBodyStyle.WrappedRequest, ResponseFormat=WebMessageFormat.Json)]  
[OperationContract]  
string[] GetCities(string firstLetters, int maxNumber);  
```  
  
## <a name="accessing-ajax-services"></a>Acessando serviços AJAX  
 Os pontos de extremidade do WCF AJAX sempre aceitam solicitações JSON e XML.  
  
 As solicitações HTTP POST com um tipo de conteúdo de "Application/JSON" são tratadas como JSON, e aquelas com Content-Type que indicam XML (por exemplo, "text/xml") são tratadas como XML.  
  
 As solicitações HTTP GET contêm todos os parâmetros de solicitação na própria URL.  
  
 Cabe ao usuário decidir como criar a solicitação HTTP para o ponto de extremidade. Além disso, o usuário tem controle total sobre a construção do JSON que forma o corpo da solicitação. Para obter um exemplo de como criar uma solicitação do JavaScript, consulte o [serviço AJAX com JSON e XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).
