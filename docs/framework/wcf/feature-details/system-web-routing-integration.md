---
title: Integração de System.Web.Routing
ms.date: 03/30/2017
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
ms.openlocfilehash: 85137689a31573dc10e8f7384007830ab40d31df
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976029"
---
# <a name="systemwebrouting-integration"></a><span data-ttu-id="8d984-102">Integração de System.Web.Routing</span><span class="sxs-lookup"><span data-stu-id="8d984-102">System.Web.Routing Integration</span></span>
<span data-ttu-id="8d984-103">Ao hospedar um serviço de Windows Communication Foundation (WCF) no serviço de informações da Internet (IIS), você coloca um arquivo. svc no diretório virtual.</span><span class="sxs-lookup"><span data-stu-id="8d984-103">When hosting a Windows Communication Foundation (WCF) service in Internet Information Service (IIS) you place a .svc file in the virtual directory.</span></span> <span data-ttu-id="8d984-104">Esse arquivo. svc especifica a fábrica de hosts de serviço a ser usada, bem como a classe que implementa o serviço.</span><span class="sxs-lookup"><span data-stu-id="8d984-104">This .svc file specifies the service host factory to use as well as the class that implements the service.</span></span> <span data-ttu-id="8d984-105">Ao fazer solicitações para o serviço, você especifica o arquivo. svc no URI, por exemplo: `http://contoso.com/EmployeeServce.svc`.</span><span class="sxs-lookup"><span data-stu-id="8d984-105">When making requests to the service you specify the .svc file in the URI, for example: `http://contoso.com/EmployeeServce.svc`.</span></span> <span data-ttu-id="8d984-106">Para programadores que escrevem serviços REST, esse tipo de URI não é o ideal.</span><span class="sxs-lookup"><span data-stu-id="8d984-106">For programmers writing REST services this type of URI is not optimal.</span></span> <span data-ttu-id="8d984-107">Os URIs para serviços REST especificam um recurso específico e normalmente não têm nenhuma extensão.</span><span class="sxs-lookup"><span data-stu-id="8d984-107">URIs for REST services specify a specific resource and normally do not have any extensions.</span></span> <span data-ttu-id="8d984-108">O recurso de integração do <xref:System.Web.Routing> permite que você hospede um serviço REST do WCF que responde a URIs sem uma extensão.</span><span class="sxs-lookup"><span data-stu-id="8d984-108">The <xref:System.Web.Routing> integration feature allows you to host a WCF REST service that responds to URIs without an extension.</span></span> <span data-ttu-id="8d984-109">Para obter mais informações sobre roteamento, consulte [ASP.net Routing](https://go.microsoft.com/fwlink/?LinkId=184660).</span><span class="sxs-lookup"><span data-stu-id="8d984-109">For more information about routing see [ASP.NET Routing](https://go.microsoft.com/fwlink/?LinkId=184660).</span></span>  
  
## <a name="using-systemwebrouting-integration"></a><span data-ttu-id="8d984-110">Usando a integração de System. Web. Routing</span><span class="sxs-lookup"><span data-stu-id="8d984-110">Using System.Web.Routing Integration</span></span>  
 <span data-ttu-id="8d984-111">Para usar o recurso de integração de <xref:System.Web.Routing>, use a classe <xref:System.ServiceModel.Activation.ServiceRoute> para criar uma ou mais rotas e adicioná-las ao <xref:System.Web.Routing.RouteTable> em um arquivo global. asax.</span><span class="sxs-lookup"><span data-stu-id="8d984-111">To use the <xref:System.Web.Routing> integration feature, you use the <xref:System.ServiceModel.Activation.ServiceRoute> class to create one or more routes and add them to the <xref:System.Web.Routing.RouteTable> in a Global.asax file.</span></span> <span data-ttu-id="8d984-112">Essas rotas especificam os URIs relativos aos quais o serviço responde.</span><span class="sxs-lookup"><span data-stu-id="8d984-112">These routes specify the relative URIs that the service responds to.</span></span> <span data-ttu-id="8d984-113">O exemplo a seguir mostra como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="8d984-113">The following example shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="8d984-114">Isso roteia todas as solicitações com um URI relativo que começa com os clientes para o serviço de `Service`.</span><span class="sxs-lookup"><span data-stu-id="8d984-114">This routes all requests with a relative URI that begins with Customers to the `Service` service.</span></span>  
  
 <span data-ttu-id="8d984-115">No arquivo Web. config, você deve adicionar o módulo `System.Web.Routing.UrlRoutingModule`, definir o atributo `runAllManagedModulesForAllRequests` como `true`e adicionar o manipulador de `UrlRoutingHandler` ao elemento `<system.webServer>`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="8d984-115">In your Web.config file you must add the `System.Web.Routing.UrlRoutingModule` module, set the `runAllManagedModulesForAllRequests` attribute to `true`, and add the `UrlRoutingHandler` handler to the `<system.webServer>` element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="8d984-116">Isso carrega um módulo e um manipulador necessários para o roteamento.</span><span class="sxs-lookup"><span data-stu-id="8d984-116">This loads a module and handler required for routing.</span></span> <span data-ttu-id="8d984-117">Para obter mais informações, consulte [Roteamento](../../../../docs/framework/wcf/feature-details/routing.md).</span><span class="sxs-lookup"><span data-stu-id="8d984-117">For more information, see [Routing](../../../../docs/framework/wcf/feature-details/routing.md).</span></span> <span data-ttu-id="8d984-118">Você também deve definir o atributo `aspNetCompatibilityEnabled` como `true` no elemento `<serviceHostingEnvironment>`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="8d984-118">You must also set the `aspNetCompatibilityEnabled` attribute to `true` in the `<serviceHostingEnvironment>` element as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 <span data-ttu-id="8d984-119">A classe que implementa o serviço deve habilitar os requisitos de compatibilidade do ASP.NET, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="8d984-119">The class that implements the service must enable ASP.NET compatibility requirements as shown in the following example.</span></span>  
  
```csharp 
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="8d984-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d984-120">See also</span></span>

- [<span data-ttu-id="8d984-121">Modelo de programação HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="8d984-121">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [<span data-ttu-id="8d984-122">Roteamento de ASP.NET</span><span class="sxs-lookup"><span data-stu-id="8d984-122">ASP.NET Routing</span></span>](https://go.microsoft.com/fwlink/?LinkId=184660)
