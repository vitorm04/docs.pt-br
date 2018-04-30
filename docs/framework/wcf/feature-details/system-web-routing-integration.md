---
title: Integração de System.Web.Routing
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 72403671fe6700ae26cae4471a1d0ac100005f3a
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="systemwebrouting-integration"></a>Integração de System.Web.Routing
Ao hospedar um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] serviço no serviço de informações da Internet (IIS), você coloca um arquivo. svc no diretório virtual. Esse arquivo. svc Especifica a fábrica do host de serviço a ser usado, bem como a classe que implementa o serviço. Ao fazer solicitações para o serviço de você especificar o arquivo. svc no URI, por exemplo: http://contoso.com/EmployeeServce.svc. Esse tipo de URI não é ideal para programadores que criam serviços REST. URIs para serviços REST especifique um recurso específico e normalmente não têm extensões. O <xref:System.Web.Routing> recurso de integração permite que você hospede um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço REST que responde às URIs sem uma extensão. Para obter mais informações sobre roteamento, consulte [roteamento ASP.NET](http://go.microsoft.com/fwlink/?LinkId=184660) e [AspNetRouteIntegration](../../../../docs/framework/wcf/samples/aspnetrouteintegration.md) exemplo.  
  
## <a name="using-systemwebrouting-integration"></a>Usando a integração de Routing  
 Para usar o <xref:System.Web.Routing> recurso de integração, você usa o <xref:System.ServiceModel.Activation.ServiceRoute> classe para criar uma ou mais rotas e adicioná-los para o <xref:System.Web.Routing.RouteTable> em um arquivo global. asax. Essas rotas especificam URIs que o serviço responde a relativa. O exemplo a seguir mostra como fazer isso.  
  
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
  
 Isso encaminha todas as solicitações com um URI relativo que comece com os clientes a `Service` serviço.  
  
 Em seu arquivo Web. config, você deve adicionar o `System.Web.Routing.UrlRoutingModule` módulo, defina o `runAllManagedModulesForAllRequests` atributo `true`e adicione o `UrlRoutingHandler` manipulador para o `<system.webServer>` elemento conforme mostrado no exemplo a seguir.  
  
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
  
 Isso carrega um módulo e o manipulador necessários para roteamento. Para obter mais informações, consulte [Roteamento](../../../../docs/framework/wcf/feature-details/routing.md). Você também deve definir o `aspNetCompatibilityEnabled` atributo `true` no `<serviceHostingEnvironment>` elemento conforme mostrado no exemplo a seguir.  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 A classe que implementa o serviço deve habilitar os requisitos de compatibilidade do ASP.NET, conforme mostrado no exemplo a seguir.  
  
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
 [Roteamento do ASP.NET](http://go.microsoft.com/fwlink/?LinkId=184660)
