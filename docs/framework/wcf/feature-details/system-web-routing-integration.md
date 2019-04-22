---
title: Integração de System.Web.Routing
ms.date: 03/30/2017
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
ms.openlocfilehash: 3d5c3d7586189e0939fd52bc2b5feac51ae00613
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59097506"
---
# <a name="systemwebrouting-integration"></a><span data-ttu-id="fea9e-102">Integração de System.Web.Routing</span><span class="sxs-lookup"><span data-stu-id="fea9e-102">System.Web.Routing Integration</span></span>
<span data-ttu-id="fea9e-103">Ao hospedar um serviço do Windows Communication Foundation (WCF) no serviço de informações da Internet (IIS), você colocar um arquivo. svc no diretório virtual.</span><span class="sxs-lookup"><span data-stu-id="fea9e-103">When hosting a Windows Communication Foundation (WCF) service in Internet Information Service (IIS) you place a .svc file in the virtual directory.</span></span> <span data-ttu-id="fea9e-104">Esse arquivo. svc Especifica a fábrica do host de serviço para usar, bem como a classe que implementa o serviço.</span><span class="sxs-lookup"><span data-stu-id="fea9e-104">This .svc file specifies the service host factory to use as well as the class that implements the service.</span></span> <span data-ttu-id="fea9e-105">Ao fazer solicitações para o serviço de você especificar o arquivo. svc no URI, por exemplo: `http://contoso.com/EmployeeServce.svc`.</span><span class="sxs-lookup"><span data-stu-id="fea9e-105">When making requests to the service you specify the .svc file in the URI, for example: `http://contoso.com/EmployeeServce.svc`.</span></span> <span data-ttu-id="fea9e-106">Esse tipo de URI não é ideal para programadores que criam serviços REST.</span><span class="sxs-lookup"><span data-stu-id="fea9e-106">For programmers writing REST services this type of URI is not optimal.</span></span> <span data-ttu-id="fea9e-107">URIs para serviços REST especifique um recurso específico e normalmente não têm nenhuma extensão.</span><span class="sxs-lookup"><span data-stu-id="fea9e-107">URIs for REST services specify a specific resource and normally do not have any extensions.</span></span> <span data-ttu-id="fea9e-108">O <xref:System.Web.Routing> recurso de integração permite que você hospede um serviço REST do WCF que responde às URIs sem uma extensão.</span><span class="sxs-lookup"><span data-stu-id="fea9e-108">The <xref:System.Web.Routing> integration feature allows you to host a WCF REST service that responds to URIs without an extension.</span></span> <span data-ttu-id="fea9e-109">Para obter mais informações sobre roteamento, consulte [roteamento ASP.NET](https://go.microsoft.com/fwlink/?LinkId=184660).</span><span class="sxs-lookup"><span data-stu-id="fea9e-109">For more information about routing see [ASP.NET Routing](https://go.microsoft.com/fwlink/?LinkId=184660).</span></span>  
  
## <a name="using-systemwebrouting-integration"></a><span data-ttu-id="fea9e-110">Usando a integração de Routing</span><span class="sxs-lookup"><span data-stu-id="fea9e-110">Using System.Web.Routing Integration</span></span>  
 <span data-ttu-id="fea9e-111">Usar o <xref:System.Web.Routing> recurso de integração, use o <xref:System.ServiceModel.Activation.ServiceRoute> classe para criar uma ou mais rotas e adicioná-los para o <xref:System.Web.Routing.RouteTable> em um arquivo global. asax.</span><span class="sxs-lookup"><span data-stu-id="fea9e-111">To use the <xref:System.Web.Routing> integration feature, you use the <xref:System.ServiceModel.Activation.ServiceRoute> class to create one or more routes and add them to the <xref:System.Web.Routing.RouteTable> in a Global.asax file.</span></span> <span data-ttu-id="fea9e-112">Essas rotas especificam o URIs que o serviço responde ao relativo.</span><span class="sxs-lookup"><span data-stu-id="fea9e-112">These routes specify the relative URIs that the service responds to.</span></span> <span data-ttu-id="fea9e-113">O exemplo a seguir mostra como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="fea9e-113">The following example shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="fea9e-114">Isso roteia todas as solicitações com um URI relativo que começa com os clientes para o `Service` service.</span><span class="sxs-lookup"><span data-stu-id="fea9e-114">This routes all requests with a relative URI that begins with Customers to the `Service` service.</span></span>  
  
 <span data-ttu-id="fea9e-115">Em seu arquivo Web. config, você deve adicionar o `System.Web.Routing.UrlRoutingModule` módulo, defina a `runAllManagedModulesForAllRequests` atributo para `true`e adicione o `UrlRoutingHandler` manipulador para o `<system.webServer>` elemento, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="fea9e-115">In your Web.config file you must add the `System.Web.Routing.UrlRoutingModule` module, set the `runAllManagedModulesForAllRequests` attribute to `true`, and add the `UrlRoutingHandler` handler to the `<system.webServer>` element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="fea9e-116">Isso carrega um módulo e o manipulador necessários para roteamento.</span><span class="sxs-lookup"><span data-stu-id="fea9e-116">This loads a module and handler required for routing.</span></span> <span data-ttu-id="fea9e-117">Para obter mais informações, consulte [Roteamento](../../../../docs/framework/wcf/feature-details/routing.md).</span><span class="sxs-lookup"><span data-stu-id="fea9e-117">For more information, see [Routing](../../../../docs/framework/wcf/feature-details/routing.md).</span></span> <span data-ttu-id="fea9e-118">Você também deve definir a `aspNetCompatibilityEnabled` de atributo para `true` no `<serviceHostingEnvironment>` elemento, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="fea9e-118">You must also set the `aspNetCompatibilityEnabled` attribute to `true` in the `<serviceHostingEnvironment>` element as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 <span data-ttu-id="fea9e-119">A classe que implementa o serviço deve habilitar requisitos de compatibilidade do ASP.NET, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="fea9e-119">The class that implements the service must enable ASP.NET compatibility requirements as shown in the following example.</span></span>  
  
```  
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="fea9e-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fea9e-120">See also</span></span>

- [<span data-ttu-id="fea9e-121">Modelo de programação HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="fea9e-121">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [<span data-ttu-id="fea9e-122">Roteamento do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="fea9e-122">ASP.NET Routing</span></span>](https://go.microsoft.com/fwlink/?LinkId=184660)
