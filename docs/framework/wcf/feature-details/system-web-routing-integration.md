---
title: "Integração de System.Web.Routing"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 73ec25ab5376841b2970fedf17ad1de176923f16
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="systemwebrouting-integration"></a><span data-ttu-id="f2eac-102">Integração de System.Web.Routing</span><span class="sxs-lookup"><span data-stu-id="f2eac-102">System.Web.Routing Integration</span></span>
<span data-ttu-id="f2eac-103">Ao hospedar um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] serviço no serviço de informações da Internet (IIS), você coloca um arquivo. svc no diretório virtual.</span><span class="sxs-lookup"><span data-stu-id="f2eac-103">When hosting a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service in Internet Information Service (IIS) you place a .svc file in the virtual directory.</span></span> <span data-ttu-id="f2eac-104">Esse arquivo. svc Especifica a fábrica do host de serviço a ser usado, bem como a classe que implementa o serviço.</span><span class="sxs-lookup"><span data-stu-id="f2eac-104">This .svc file specifies the service host factory to use as well as the class that implements the service.</span></span> <span data-ttu-id="f2eac-105">Ao fazer solicitações para o serviço de você especificar o arquivo. svc no URI, por exemplo: http://contoso.com/EmployeeServce.svc.</span><span class="sxs-lookup"><span data-stu-id="f2eac-105">When making requests to the service you specify the .svc file in the URI, for example: http://contoso.com/EmployeeServce.svc.</span></span> <span data-ttu-id="f2eac-106">Esse tipo de URI não é ideal para programadores que criam serviços REST.</span><span class="sxs-lookup"><span data-stu-id="f2eac-106">For programmers writing REST services this type of URI is not optimal.</span></span> <span data-ttu-id="f2eac-107">URIs para serviços REST especifique um recurso específico e normalmente não têm extensões.</span><span class="sxs-lookup"><span data-stu-id="f2eac-107">URIs for REST services specify a specific resource and normally do not have any extensions.</span></span> <span data-ttu-id="f2eac-108">O <xref:System.Web.Routing> recurso de integração permite que você hospede um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço REST que responde às URIs sem uma extensão.</span><span class="sxs-lookup"><span data-stu-id="f2eac-108">The <xref:System.Web.Routing> integration feature allows you to host a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] REST service that responds to URIs without an extension.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="f2eac-109">Consulte roteamento [roteamento ASP.NET](http://go.microsoft.com/fwlink/?LinkId=184660) e [AspNetRouteIntegration](../../../../docs/framework/wcf/samples/aspnetrouteintegration.md) exemplo.</span><span class="sxs-lookup"><span data-stu-id="f2eac-109"> routing see [ASP.NET Routing](http://go.microsoft.com/fwlink/?LinkId=184660) and the [AspNetRouteIntegration](../../../../docs/framework/wcf/samples/aspnetrouteintegration.md) sample.</span></span>  
  
## <a name="using-systemwebrouting-integration"></a><span data-ttu-id="f2eac-110">Usando a integração de Routing</span><span class="sxs-lookup"><span data-stu-id="f2eac-110">Using System.Web.Routing Integration</span></span>  
 <span data-ttu-id="f2eac-111">Para usar o <xref:System.Web.Routing> recurso de integração, você usa o <xref:System.ServiceModel.Activation.ServiceRoute> classe para criar uma ou mais rotas e adicioná-los para o <xref:System.Web.Routing.RouteTable> em um arquivo global. asax.</span><span class="sxs-lookup"><span data-stu-id="f2eac-111">To use the <xref:System.Web.Routing> integration feature, you use the <xref:System.ServiceModel.Activation.ServiceRoute> class to create one or more routes and add them to the <xref:System.Web.Routing.RouteTable> in a Global.asax file.</span></span> <span data-ttu-id="f2eac-112">Essas rotas especificam URIs que o serviço responde a relativa.</span><span class="sxs-lookup"><span data-stu-id="f2eac-112">These routes specify the relative URIs that the service responds to.</span></span> <span data-ttu-id="f2eac-113">O exemplo a seguir mostra como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="f2eac-113">The following example shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="f2eac-114">Isso encaminha todas as solicitações com um URI relativo que comece com os clientes a `Service` serviço.</span><span class="sxs-lookup"><span data-stu-id="f2eac-114">This routes all requests with a relative URI that begins with Customers to the `Service` service.</span></span>  
  
 <span data-ttu-id="f2eac-115">Em seu arquivo Web. config, você deve adicionar o `System.Web.Routing.UrlRoutingModule` módulo, defina o `runAllManagedModulesForAllRequests` atributo `true`e adicione o `UrlRoutingHandler` manipulador para o `<system.webServer>` elemento conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f2eac-115">In your Web.config file you must add the `System.Web.Routing.UrlRoutingModule` module, set the `runAllManagedModulesForAllRequests` attribute to `true`, and add the `UrlRoutingHandler` handler to the `<system.webServer>` element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="f2eac-116">Isso carrega um módulo e o manipulador necessários para roteamento.</span><span class="sxs-lookup"><span data-stu-id="f2eac-116">This loads a module and handler required for routing.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="f2eac-117">[Roteamento](../../../../docs/framework/wcf/feature-details/routing.md).</span><span class="sxs-lookup"><span data-stu-id="f2eac-117"> [Routing](../../../../docs/framework/wcf/feature-details/routing.md).</span></span> <span data-ttu-id="f2eac-118">Você também deve definir o `aspNetCompatibilityEnabled` atributo `true` no `<serviceHostingEnvironment>` elemento conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f2eac-118">You must also set the `aspNetCompatibilityEnabled` attribute to `true` in the `<serviceHostingEnvironment>` element as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 <span data-ttu-id="f2eac-119">A classe que implementa o serviço deve habilitar os requisitos de compatibilidade do ASP.NET, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f2eac-119">The class that implements the service must enable ASP.NET compatibility requirements as shown in the following example.</span></span>  
  
```  
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="f2eac-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f2eac-120">See Also</span></span>  
 [<span data-ttu-id="f2eac-121">Modelo de programação WCF Web HTTP</span><span class="sxs-lookup"><span data-stu-id="f2eac-121">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [<span data-ttu-id="f2eac-122">Roteamento do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f2eac-122">ASP.NET Routing</span></span>](http://go.microsoft.com/fwlink/?LinkId=184660)
