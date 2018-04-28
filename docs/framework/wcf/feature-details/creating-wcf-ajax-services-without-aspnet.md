---
title: Criando serviços WCF AJAX sem ASP.NET
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba4a7d1b-e277-4978-9f62-37684e6dc934
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b652bcd522a8eea81b3d1218fbd054ee0b2caea8
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="creating-wcf-ajax-services-without-aspnet"></a>Criando serviços WCF AJAX sem ASP.NET
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Serviços de AJAX podem ser acessados de qualquer página da Web habilitado para JavaScript, sem a necessidade de ASP.NET AJAX. Este tópico descreve como criar como um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço.  
  
 Para obter instruções sobre como usar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] com o ASP.NET AJAX, consulte [criando serviços WCF para o ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).  
  
 Existem três partes para criar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço AJAX:  
  
-   Criar um ponto de extremidade AJAX que pode ser acessado do navegador.  
  
-   Criar um contrato de serviço compatível com AJAX.  
  
-   Acessando serviços WCF AJAX.  
  
## <a name="creating-an-ajax-endpoint"></a>Criar um ponto de extremidade AJAX  
 A maneira mais simples para habilitar o suporte de AJAX em um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service é usar o <xref:System.ServiceModel.Activation.WebServiceHostFactory> no arquivo. svc associado ao serviço, como no exemplo a seguir.  
  
```  
<%ServiceHost   
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 Como alternativa, você também pode usar a configuração para adicionar um ponto de extremidade AJAX. Use o <xref:System.ServiceModel.WebHttpBinding> no ponto de extremidade de serviço e configurar o ponto de extremidade com o <xref:System.ServiceModel.Description.WebHttpBehavior> conforme mostrado no seguinte trecho de código.  
  
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
  
## <a name="creating-an-ajax-compatible-service-contract"></a>Criar um contrato de serviço compatível com o AJAX  
 Por padrão, os contratos de serviço exposta em dados de retorno um ponto de extremidade AJAX no formato XML. Além disso, por padrão, as operações de serviço são acessíveis por meio de solicitações HTTP POST para URLs que incluem o endereço de ponto de extremidade, seguido pelo nome da operação, conforme mostrado no exemplo a seguir.  
  
```  
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 Esta operação é acessível por meio de um HTTP POST para `http://serviceaddress/endpointaddress/GetCities` e retornar uma mensagem XML.  
  
 Você pode usar o modelo de programação da Web completa para personalizar esses aspectos básicos. Por exemplo, você pode usar o <xref:System.ServiceModel.Web.WebGetAttribute> ou <xref:System.ServiceModel.Web.WebInvokeAttribute> atributos para controlar o verbo HTTP para o qual a operação responde ou usar o `UriTemplate` propriedade desses respectivos atributos para especificar os URIs personalizado. Para obter mais informações, consulte o [modelo de programação do WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md) tópico.  
  
 O formato de dados JSON é geralmente usado em serviços AJAX. Para criar uma operação que retorna JSON em vez de XML, defina o <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> (ou o <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>) propriedade <xref:System.ServiceModel.Web.WebMessageFormat.Json>. O [a serialização JSON autônoma](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) tópico mostra como internos .NET dados e tipos de contrato tipos mapa em JSON.  
  
 Normalmente, solicitações JSON e respostas consistem apenas um item. Para o anterior `GetCities` operação, a solicitação é semelhante a instrução a seguir.  
  
```  
"na"  
```  
  
 A resposta para essa solicitação é semelhante a instrução a seguir.  
  
```  
["Nairobi", "Naples", "Nashville"]  
```  
  
 Se a operação aceita um parâmetro extra, o estilo de solicitação deve ser encapsulado para encapsular ambos os parâmetros em um único objeto JSON. É um exemplo dessa mensagem de JSON de estilo no exemplo a seguir.  
  
```json  
{"firstLetters": "na", "maxNumber": 2}  
```  
  
 O contrato a seguir aceita essa mensagem.  
  
```  
[WebInvoke(BodyStyle=WebMessageBodyStyle.WrappedRequest, ResponseFormat=WebMessageFormat.Json)]  
[OperationContract]  
string[] GetCities(string firstLetters, int maxNumber);  
```  
  
## <a name="accessing-ajax-services"></a>Acessando serviços AJAX  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Pontos de extremidade AJAX sempre aceitam solicitações JSON e XML.  
  
 Solicitações HTTP POST com um tipo de conteúdo de "application/json" são tratadas como JSON, e aqueles com o tipo de conteúdo que indicam XML (por exemplo, "text/xml") são tratados como XML.  
  
 Solicitações HTTP GET contém todos os parâmetros de solicitação na URL em si.  
  
 Cabe ao usuário decidir como criar a solicitação HTTP para o ponto de extremidade. Além disso, o usuário tem controle total sobre a construção JSON que forma o corpo da solicitação. Para obter um exemplo de criação de uma solicitação de JavaScript, consulte o [serviço de AJAX com JSON e XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).
