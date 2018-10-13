---
title: Integração de System.Web.Routing
ms.date: 03/30/2017
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
ms.openlocfilehash: 3b95b3117941ce7d019b87b00181b2cbac652f43
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/13/2018
ms.locfileid: "49308202"
---
# <a name="systemwebrouting-integration"></a>Integração de System.Web.Routing
Ao hospedar um serviço do Windows Communication Foundation (WCF) no serviço de informações da Internet (IIS), você colocar um arquivo. svc no diretório virtual. Esse arquivo. svc Especifica a fábrica do host de serviço para usar, bem como a classe que implementa o serviço. Ao fazer solicitações para o serviço de você especificar o arquivo. svc no URI, por exemplo: `http://contoso.com/EmployeeServce.svc`. Esse tipo de URI não é ideal para programadores que criam serviços REST. URIs para serviços REST especifique um recurso específico e normalmente não têm nenhuma extensão. O <xref:System.Web.Routing> recurso de integração permite que você hospede um serviço REST do WCF que responde às URIs sem uma extensão. Para obter mais informações sobre roteamento, consulte [roteamento ASP.NET](https://go.microsoft.com/fwlink/?LinkId=184660).  
  
## <a name="using-systemwebrouting-integration"></a>Usando a integração de Routing  
 Usar o <xref:System.Web.Routing> recurso de integração, use o <xref:System.ServiceModel.Activation.ServiceRoute> classe para criar uma ou mais rotas e adicioná-los para o <xref:System.Web.Routing.RouteTable> em um arquivo global. asax. Essas rotas especificam o URIs que o serviço responde ao relativo. O exemplo a seguir mostra como fazer isso.  
  
```  
<%@ Application Language="C#" %>  
<%@ Import Namespace="System.Web.Routing" %>  
<%@ Import Namespace="System.ServiceModel.Activation" %>  
<%@ Import Namespace="System.ServiceModel.Web " %>  
  
<script RunAt="server">  
    void Application_Start(object sender, EventArgs e)  
    {  
        RegisterRoutes(RouteTable.Routes);  
    }  
  
    private void RegisterRoutes(RouteCollection routes)  
    {  
        routes.Add(new ServiceRoute("Customers", new WebServiceHostFactory(), typeof(Service)));   
   }  
</script>  
```  
  
 Isso roteia todas as solicitações com um URI relativo que começa com os clientes para o `Service` service.  
  
 Em seu arquivo Web. config, você deve adicionar o `System.Web.Routing.UrlRoutingModule` módulo, defina a `runAllManagedModulesForAllRequests` atributo para `true`e adicione o `UrlRoutingHandler` manipulador para o `<system.webServer>` elemento, conforme mostrado no exemplo a seguir.  
  
```xml  
<system.webServer>  
      <modules runAllManagedModulesForAllRequests="true">  
        <add name="UrlRoutingModule" type="System.Web.Routing.UrlRoutingModule, System.Web, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" />  
      </modules>  
      <handlers>  
        <add name="UrlRoutingHandler" preCondition="integratedMode" verb="*" path="UrlRouting.axd"/>  
      </handlers>  
    </system.webServer>  
```  
  
 Isso carrega um módulo e o manipulador necessários para roteamento. Para obter mais informações, consulte [Roteamento](../../../../docs/framework/wcf/feature-details/routing.md). Você também deve definir a `aspNetCompatibilityEnabled` de atributo para `true` no `<serviceHostingEnvironment>` elemento, conforme mostrado no exemplo a seguir.  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 A classe que implementa o serviço deve habilitar requisitos de compatibilidade do ASP.NET, conforme mostrado no exemplo a seguir.  
  
```  
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a>Consulte também  
 [Modelo de programação HTTP Web do WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [Roteamento do ASP.NET](https://go.microsoft.com/fwlink/?LinkId=184660)
