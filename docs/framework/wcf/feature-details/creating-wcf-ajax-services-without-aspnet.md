---
title: Criando serviços WCF AJAX sem ASP.NET
ms.date: 03/30/2017
ms.assetid: ba4a7d1b-e277-4978-9f62-37684e6dc934
ms.openlocfilehash: de7e5dc075a821518928514be532ea1940c1ff17
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64627124"
---
# <a name="creating-wcf-ajax-services-without-aspnet"></a>Criando serviços WCF AJAX sem ASP.NET
Os serviços AJAX Windows Communication Foundation (WCF) podem ser acessados de qualquer página da Web habilitado para JavaScript, sem a necessidade de ASP.NET AJAX. Este tópico descreve como criar um serviço WCF.  
  
 Para obter instruções sobre como usar o WCF com o ASP.NET AJAX, consulte [criação de serviços do WCF para o ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).  
  
 Há três partes para criar um serviço WCF AJAX:  
  
- Criar um ponto de extremidade do AJAX que pode ser acessado do navegador.  
  
- Criando um contrato de serviço compatível com o AJAX.  
  
- Acessando serviços WCF AJAX.  
  
## <a name="creating-an-ajax-endpoint"></a>Criando um ponto de extremidade do AJAX  
 A maneira mais simples para habilitar o suporte do AJAX em um serviço WCF é usar o <xref:System.ServiceModel.Activation.WebServiceHostFactory> no arquivo. svc associado ao serviço, como no exemplo a seguir.  
  
```  
<%ServiceHost   
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 Como alternativa, você também pode usar a configuração para adicionar um ponto de extremidade do AJAX. Use o <xref:System.ServiceModel.WebHttpBinding> no ponto de extremidade de serviço e configurar o ponto de extremidade com o <xref:System.ServiceModel.Description.WebHttpBehavior> conforme mostrado no trecho de código a seguir.  
  
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
  
 Para obter um exemplo de funcionamento, consulte o [serviço de AJAX com JSON e XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).  
  
## <a name="creating-an-ajax-compatible-service-contract"></a>Criando um contrato de serviço compatível com o AJAX  
 Por padrão, os contratos de serviço exposto sobre dados de retorno um ponto de extremidade AJAX no formato XML. Além disso, por padrão, as operações de serviço são acessíveis por meio de solicitações HTTP POST para URLs que incluem o endereço de ponto de extremidade seguido pelo nome da operação, conforme mostrado no exemplo a seguir.  
  
```  
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 Esta operação é acessível por meio de um HTTP POST para `http://serviceaddress/endpointaddress/GetCities` e retornar uma mensagem XML.  
  
 Você pode usar o modelo de programação Web completo para personalizar esses aspectos básicos. Por exemplo, você pode usar o <xref:System.ServiceModel.Web.WebGetAttribute> ou <xref:System.ServiceModel.Web.WebInvokeAttribute> atributos para controlar o verbo HTTP à qual a operação responde ou usar o `UriTemplate` propriedade desses respectivos atributos para especificar os URIs personalizado. Para obter mais informações, consulte o [modelo de programação do WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md) tópico.  
  
 O formato de dados JSON geralmente é usado em serviços AJAX. Para criar uma operação que retorna JSON em vez de XML, defina as <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> (ou o <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>) propriedade <xref:System.ServiceModel.Web.WebMessageFormat.Json>. O [a serialização JSON autônoma](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) tópico mostra como .NET dados e tipos de contrato tipos mapa incorporados em JSON.  
  
 Normalmente, solicitações JSON e respostas consistem em apenas um item. Para o anterior `GetCities` operação, a solicitação é semelhante a instrução a seguir.  
  
```  
"na"  
```  
  
 A resposta a essa solicitação é semelhante a instrução a seguir.  
  
```  
["Nairobi", "Naples", "Nashville"]  
```  
  
 Se a operação leva um parâmetro extra, o estilo de solicitação deve ser encapsulado para encapsular os dois parâmetros em um único objeto JSON. É um exemplo dessa mensagem de JSON de estilo no exemplo a seguir.  
  
```json  
{"firstLetters": "na", "maxNumber": 2}  
```  
  
 O seguinte contrato aceita essa mensagem.  
  
```  
[WebInvoke(BodyStyle=WebMessageBodyStyle.WrappedRequest, ResponseFormat=WebMessageFormat.Json)]  
[OperationContract]  
string[] GetCities(string firstLetters, int maxNumber);  
```  
  
## <a name="accessing-ajax-services"></a>Acessando serviços AJAX  
 Pontos de extremidade WCF AJAX sempre aceitam solicitações JSON e XML.  
  
 Solicitações HTTP POST com um tipo de conteúdo de "application/json" são tratadas como JSON, e aqueles com o tipo de conteúdo que indicam o XML (por exemplo, "text/xml") são tratados como XML.  
  
 Solicitações HTTP GET contém todos os parâmetros de solicitação na URL em si.  
  
 Cabe ao usuário decidir como criar a solicitação HTTP para o ponto de extremidade. Além disso, o usuário tem controle total sobre como construir o JSON que constitui o corpo da solicitação. Para obter um exemplo de criação de uma solicitação de JavaScript, consulte o [serviço de AJAX com JSON e XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).
