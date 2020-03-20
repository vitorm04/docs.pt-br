---
title: Integração de System.Web.Routing
ms.date: 03/30/2017
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
ms.openlocfilehash: a80b5c3b336b4fd18b347a25ceaf509baf6461b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184389"
---
# <a name="systemwebrouting-integration"></a>Integração de System.Web.Routing
Ao hospedar um serviço da Windows Communication Foundation (WCF) no Serviço de Informações da Internet (IIS), você coloca um arquivo .svc no diretório virtual. Este arquivo .svc especifica a fábrica de host de serviço para usar, bem como a classe que implementa o serviço. Ao fazer solicitações ao serviço, você especifica o arquivo `http://contoso.com/EmployeeServce.svc`.svc no URI, por exemplo: . Para programadores que escrevem serviços REST, este tipo de URI não é o ideal. URIs para serviços REST especificam um recurso específico e normalmente não possuem extensões. O <xref:System.Web.Routing> recurso de integração permite que você hospede um serviço WCF REST que responde a URIs sem uma extensão. Para obter mais informações sobre roteamento, consulte [ASP.NET Roteamento](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100)).  
  
## <a name="using-systemwebrouting-integration"></a>Usando a integração system.Web.roteamento  
 Para usar <xref:System.Web.Routing> o recurso de <xref:System.ServiceModel.Activation.ServiceRoute> integração, você usa a classe <xref:System.Web.Routing.RouteTable> para criar uma ou mais rotas e adicioná-las ao arquivo Global.asax. Essas rotas especificam as URIs relativas às quais o serviço responde. O exemplo a seguir mostra como fazer isso.  
  
```aspx-csharp  
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
  
 Isso encaminha todas as solicitações com `Service` um URI relativo que começa com os Clientes para o serviço.  
  
 No arquivo Web.config, você `System.Web.Routing.UrlRoutingModule` deve adicionar `runAllManagedModulesForAllRequests` o `true`módulo, `UrlRoutingHandler` definir o `<system.webServer>` atributo e adicionar o manipulador ao elemento como mostrado no exemplo a seguir.  
  
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
  
 Isso carrega um módulo e um manipulador necessários para o roteamento. Para obter mais informações, consulte [Roteamento](../../../../docs/framework/wcf/feature-details/routing.md). Você também deve `aspNetCompatibilityEnabled` definir `true` o `<serviceHostingEnvironment>` atributo no elemento como mostrado no exemplo a seguir.  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 A classe que implementa o serviço deve habilitar os requisitos de compatibilidade ASP.NET como mostrado no exemplo a seguir.  
  
```csharp
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a>Confira também

- [Modelo de programação WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [roteamento ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100))
