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
# <a name="systemwebrouting-integration"></a><span data-ttu-id="528ff-102">Integração de System.Web.Routing</span><span class="sxs-lookup"><span data-stu-id="528ff-102">System.Web.Routing Integration</span></span>
<span data-ttu-id="528ff-103">Ao hospedar um serviço da Windows Communication Foundation (WCF) no Serviço de Informações da Internet (IIS), você coloca um arquivo .svc no diretório virtual.</span><span class="sxs-lookup"><span data-stu-id="528ff-103">When hosting a Windows Communication Foundation (WCF) service in Internet Information Service (IIS) you place a .svc file in the virtual directory.</span></span> <span data-ttu-id="528ff-104">Este arquivo .svc especifica a fábrica de host de serviço para usar, bem como a classe que implementa o serviço.</span><span class="sxs-lookup"><span data-stu-id="528ff-104">This .svc file specifies the service host factory to use as well as the class that implements the service.</span></span> <span data-ttu-id="528ff-105">Ao fazer solicitações ao serviço, você especifica o arquivo `http://contoso.com/EmployeeServce.svc`.svc no URI, por exemplo: .</span><span class="sxs-lookup"><span data-stu-id="528ff-105">When making requests to the service you specify the .svc file in the URI, for example: `http://contoso.com/EmployeeServce.svc`.</span></span> <span data-ttu-id="528ff-106">Para programadores que escrevem serviços REST, este tipo de URI não é o ideal.</span><span class="sxs-lookup"><span data-stu-id="528ff-106">For programmers writing REST services, this type of URI is not optimal.</span></span> <span data-ttu-id="528ff-107">URIs para serviços REST especificam um recurso específico e normalmente não possuem extensões.</span><span class="sxs-lookup"><span data-stu-id="528ff-107">URIs for REST services specify a specific resource and normally do not have any extensions.</span></span> <span data-ttu-id="528ff-108">O <xref:System.Web.Routing> recurso de integração permite que você hospede um serviço WCF REST que responde a URIs sem uma extensão.</span><span class="sxs-lookup"><span data-stu-id="528ff-108">The <xref:System.Web.Routing> integration feature allows you to host a WCF REST service that responds to URIs without an extension.</span></span> <span data-ttu-id="528ff-109">Para obter mais informações sobre roteamento, consulte [ASP.NET Roteamento](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="528ff-109">For more information about routing see [ASP.NET Routing](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100)).</span></span>  
  
## <a name="using-systemwebrouting-integration"></a><span data-ttu-id="528ff-110">Usando a integração system.Web.roteamento</span><span class="sxs-lookup"><span data-stu-id="528ff-110">Using System.Web.Routing Integration</span></span>  
 <span data-ttu-id="528ff-111">Para usar <xref:System.Web.Routing> o recurso de <xref:System.ServiceModel.Activation.ServiceRoute> integração, você usa a classe <xref:System.Web.Routing.RouteTable> para criar uma ou mais rotas e adicioná-las ao arquivo Global.asax.</span><span class="sxs-lookup"><span data-stu-id="528ff-111">To use the <xref:System.Web.Routing> integration feature, you use the <xref:System.ServiceModel.Activation.ServiceRoute> class to create one or more routes and add them to the <xref:System.Web.Routing.RouteTable> in a Global.asax file.</span></span> <span data-ttu-id="528ff-112">Essas rotas especificam as URIs relativas às quais o serviço responde.</span><span class="sxs-lookup"><span data-stu-id="528ff-112">These routes specify the relative URIs that the service responds to.</span></span> <span data-ttu-id="528ff-113">O exemplo a seguir mostra como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="528ff-113">The following example shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="528ff-114">Isso encaminha todas as solicitações com `Service` um URI relativo que começa com os Clientes para o serviço.</span><span class="sxs-lookup"><span data-stu-id="528ff-114">This routes all requests with a relative URI that begins with Customers to the `Service` service.</span></span>  
  
 <span data-ttu-id="528ff-115">No arquivo Web.config, você `System.Web.Routing.UrlRoutingModule` deve adicionar `runAllManagedModulesForAllRequests` o `true`módulo, `UrlRoutingHandler` definir o `<system.webServer>` atributo e adicionar o manipulador ao elemento como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="528ff-115">In your Web.config file you must add the `System.Web.Routing.UrlRoutingModule` module, set the `runAllManagedModulesForAllRequests` attribute to `true`, and add the `UrlRoutingHandler` handler to the `<system.webServer>` element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="528ff-116">Isso carrega um módulo e um manipulador necessários para o roteamento.</span><span class="sxs-lookup"><span data-stu-id="528ff-116">This loads a module and handler required for routing.</span></span> <span data-ttu-id="528ff-117">Para obter mais informações, consulte [Roteamento](../../../../docs/framework/wcf/feature-details/routing.md).</span><span class="sxs-lookup"><span data-stu-id="528ff-117">For more information, see [Routing](../../../../docs/framework/wcf/feature-details/routing.md).</span></span> <span data-ttu-id="528ff-118">Você também deve `aspNetCompatibilityEnabled` definir `true` o `<serviceHostingEnvironment>` atributo no elemento como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="528ff-118">You must also set the `aspNetCompatibilityEnabled` attribute to `true` in the `<serviceHostingEnvironment>` element as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 <span data-ttu-id="528ff-119">A classe que implementa o serviço deve habilitar os requisitos de compatibilidade ASP.NET como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="528ff-119">The class that implements the service must enable ASP.NET compatibility requirements as shown in the following example.</span></span>  
  
```csharp
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="528ff-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="528ff-120">See also</span></span>

- [<span data-ttu-id="528ff-121">Modelo de programação WCF Web HTTP</span><span class="sxs-lookup"><span data-stu-id="528ff-121">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- <span data-ttu-id="528ff-122">[roteamento ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="528ff-122">[ASP.NET Routing](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100))</span></span>
