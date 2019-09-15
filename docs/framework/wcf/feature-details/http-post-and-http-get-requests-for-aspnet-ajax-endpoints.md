---
title: 'Como: escolher entre solicitações HTTP POST e HTTP GET para pontos de extremidade AJAX ASP.NET'
ms.date: 03/30/2017
ms.assetid: b47de82a-4c92-4af6-bceb-a5cb8bb8ede9
ms.openlocfilehash: 6de32c798e7d0db5ad2d8f6666d6c5d1714250d5
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991574"
---
# <a name="how-to-choose-between-http-post-and-http-get-requests-for-aspnet-ajax-endpoints"></a><span data-ttu-id="b63b7-102">Como: escolher entre solicitações HTTP POST e HTTP GET para pontos de extremidade AJAX ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b63b7-102">How to: Choose between HTTP POST and HTTP GET requests for ASP.NET AJAX Endpoints</span></span>

<span data-ttu-id="b63b7-103">Windows Communication Foundation (WCF) permite que você crie um serviço que expõe um ponto de extremidade habilitado para AJAX ASP.NET que pode ser chamado do JavaScript em um site de cliente.</span><span class="sxs-lookup"><span data-stu-id="b63b7-103">Windows Communication Foundation (WCF) allows you to create a service that exposes an ASP.NET AJAX-enabled endpoint that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="b63b7-104">Os procedimentos básicos para a criação desses serviços são discutidos em [como: Use a configuração para adicionar um ponto de](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) extremidade [do ASP.NET AJAX e como: Adicione um ponto de extremidade do ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)sem usar a configuração.</span><span class="sxs-lookup"><span data-stu-id="b63b7-104">The basic procedures for building such services is discussed in [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) and [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
 <span data-ttu-id="b63b7-105">O ASP.NET AJAX dá suporte a operações que usam os verbos HTTP POST e HTTP GET, com HTTP POST sendo o padrão.</span><span class="sxs-lookup"><span data-stu-id="b63b7-105">ASP.NET AJAX supports operations that use the HTTP POST and HTTP GET verbs, with HTTP POST being the default.</span></span> <span data-ttu-id="b63b7-106">Ao criar uma operação que não tem efeitos colaterais e retorna dados que raramente ou nunca são alterados, use HTTP GET em vez disso.</span><span class="sxs-lookup"><span data-stu-id="b63b7-106">When creating an operation that has no side effects and returns data that rarely or never changes, use HTTP GET instead.</span></span> <span data-ttu-id="b63b7-107">Os resultados de operações GET podem ser armazenados em cache, o que significa que várias chamadas para a mesma operação podem resultar em apenas uma solicitação para seu serviço.</span><span class="sxs-lookup"><span data-stu-id="b63b7-107">Results of GET operations can be cached, which means that multiple calls to the same operation may result in only one request to your service.</span></span> <span data-ttu-id="b63b7-108">O cache não é feito pelo WCF, mas pode ocorrer em qualquer nível (no navegador de um usuário, em um servidor proxy e em outros níveis). O cache é vantajoso se você deseja aumentar o desempenho do serviço, mas pode não ser aceitável se os dados forem alterados com frequência ou se a operação executar alguma ação.</span><span class="sxs-lookup"><span data-stu-id="b63b7-108">The caching is not done by WCF but can take place at any level (in a user's browser, on a proxy server, and other levels.) Caching is advantageous if you want to increase service performance, but may not be acceptable if data changes frequently or if the operation performs some action.</span></span>  
  
 <span data-ttu-id="b63b7-109">Por exemplo, se você estiver criando um serviço para gerenciar a biblioteca de músicas de um usuário, uma operação que pesquisa o artista com base no título de um álbum se beneficia do uso de GET, mas uma operação que adiciona um álbum à coleção pessoal do usuário deve usar POST.</span><span class="sxs-lookup"><span data-stu-id="b63b7-109">For example, if you are designing service to manage a user's music library, an operation that looks up the artist based on an album's title benefits from using GET, but an operation that adds an album to the user's personal collection must use POST.</span></span>  
  
 <span data-ttu-id="b63b7-110">Para controlar o tempo de vida do cache, use <xref:System.ServiceModel.Web.OutgoingWebResponseContext> o tipo.</span><span class="sxs-lookup"><span data-stu-id="b63b7-110">To control the lifetime of the cache, use the <xref:System.ServiceModel.Web.OutgoingWebResponseContext> type.</span></span> <span data-ttu-id="b63b7-111">Por exemplo, ao criar um serviço que retorna previsões do tempo atualizadas por hora, você usaria GET, mas limita a duração do cache a uma hora ou menos para impedir que os usuários do serviço acessem dados obsoletos.</span><span class="sxs-lookup"><span data-stu-id="b63b7-111">For example, when designing a service that returns weather forecasts updated hourly, you would use GET but limit the cache duration to an hour or less to prevent the users of the service from accessing stale data.</span></span>  
  
 <span data-ttu-id="b63b7-112">Ao usar serviços de uma página ASP.NET AJAX que usa o controle Gerenciador de script, não faz diferença se a operação usa GET ou POST-o mecanismo do Gerenciador de scripts garante que o tipo de solicitação correto seja emitido.</span><span class="sxs-lookup"><span data-stu-id="b63b7-112">When using services from an ASP.NET AJAX page that use the Script Manager control, it makes no difference whether the operation uses GET or POST - the script manager mechanism ensures that the correct request type is issued.</span></span>  
  
 <span data-ttu-id="b63b7-113">As operações HTTP GET usam quaisquer parâmetros de entrada com suporte pelas operações POST, incluindo tipos de contrato de dados complexos.</span><span class="sxs-lookup"><span data-stu-id="b63b7-113">HTTP GET operations use any input parameters supported by POST operations, including complex data contract types.</span></span> <span data-ttu-id="b63b7-114">No entanto, na maioria dos casos, é recomendável evitar muitos parâmetros ou parâmetros que são muito complexos em operações GET, pois reduz a eficiência do cache.</span><span class="sxs-lookup"><span data-stu-id="b63b7-114">However, in most cases it is recommended to avoid too many parameters or parameters that are too complex in GET operations because it reduces caching efficiency.</span></span>  
  
 <span data-ttu-id="b63b7-115">Este tópico demonstra como selecionar entre Get e post adicionando os <xref:System.ServiceModel.Web.WebGetAttribute> atributos ou <xref:System.ServiceModel.Web.WebInvokeAttribute> às operações relevantes no contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="b63b7-115">This topic demonstrates how to select between GET and POST by adding the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes to the relevant operations in the service contract.</span></span> <span data-ttu-id="b63b7-116">As outras etapas (para implementar, configurar e hospedar o serviço) que são necessárias para obter o serviço em execução são semelhantes àquelas usadas por qualquer serviço AJAX ASP.NET no WCF.</span><span class="sxs-lookup"><span data-stu-id="b63b7-116">The other steps (to implement, configure and host the service) that are required to get the service running are similar to those used by any ASP.NET AJAX service in WCF.</span></span>  
  
 <span data-ttu-id="b63b7-117">Uma operação marcada com o <xref:System.ServiceModel.Web.WebGetAttribute> sempre usa uma solicitação get.</span><span class="sxs-lookup"><span data-stu-id="b63b7-117">An operation marked with the <xref:System.ServiceModel.Web.WebGetAttribute> always uses a GET request.</span></span> <span data-ttu-id="b63b7-118">Uma operação marcada com o <xref:System.ServiceModel.Web.WebInvokeAttribute>, ou não marcada com nenhum dos dois atributos, usa uma solicitação post.</span><span class="sxs-lookup"><span data-stu-id="b63b7-118">An operation marked with the <xref:System.ServiceModel.Web.WebInvokeAttribute>, or not marked with any of the two attributes, uses a POST request.</span></span> <span data-ttu-id="b63b7-119">O <xref:System.ServiceModel.Web.WebInvokeAttribute> permite o uso de outros verbos HTTP, além de Get e post (como Put e Delete) por meio da <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="b63b7-119">The <xref:System.ServiceModel.Web.WebInvokeAttribute> allows the use of other HTTP verbs, other than GET and POST (such as PUT and DELETE) through the <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> property.</span></span> <span data-ttu-id="b63b7-120">No entanto, esses verbos não são suportados pelo ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="b63b7-120">However, these verbs are not supported by ASP.NET AJAX.</span></span> <span data-ttu-id="b63b7-121">Se você pretende usar o serviço de páginas ASP.NET usando o controle Gerenciador de script, não use a <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="b63b7-121">If you intend to use the service from ASP.NET pages using the Script Manager control, do not use the <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> property.</span></span>  
  
 <span data-ttu-id="b63b7-122">Para obter um exemplo funcional de como alternar para GET, consulte o exemplo de [serviço básico Ajax](../../../../docs/framework/wcf/samples/basic-ajax-service.md) .</span><span class="sxs-lookup"><span data-stu-id="b63b7-122">For a working example of switching to GET, see the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>  
  
 <span data-ttu-id="b63b7-123">Para obter um exemplo que usa POST, consulte o [serviço AJAX usando o exemplo http post](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) .</span><span class="sxs-lookup"><span data-stu-id="b63b7-123">For a sample that uses POST, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) sample.</span></span>  
  
## <a name="to-create-a-wcf-service-that-responds-to-http-get-or-http-post-requests"></a><span data-ttu-id="b63b7-124">Para criar um serviço WCF que responde a solicitações HTTP GET ou HTTP POST</span><span class="sxs-lookup"><span data-stu-id="b63b7-124">To create a WCF service that responds to HTTP GET or HTTP POST requests</span></span>
  
1. <span data-ttu-id="b63b7-125">Defina um contrato de serviço WCF básico com uma interface marcada com <xref:System.ServiceModel.ServiceContractAttribute> o atributo.</span><span class="sxs-lookup"><span data-stu-id="b63b7-125">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="b63b7-126">Marque cada operação com o <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b63b7-126">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="b63b7-127">Adicione o <xref:System.ServiceModel.Web.WebGetAttribute> atributo para estipular que uma operação deve responder às solicitações HTTP Get.</span><span class="sxs-lookup"><span data-stu-id="b63b7-127">Add the <xref:System.ServiceModel.Web.WebGetAttribute> attribute to stipulate that an operation should respond to HTTP GET requests.</span></span> <span data-ttu-id="b63b7-128">Você também pode adicionar o <xref:System.ServiceModel.Web.WebInvokeAttribute> atributo para especificar explicitamente http post, ou não especificar um atributo, que assume como padrão http post.</span><span class="sxs-lookup"><span data-stu-id="b63b7-128">You can also add the <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute to explicitly specify HTTP POST, or not specify an attribute, which defaults to HTTP POST.</span></span>
  
    ```csharp
    [ServiceContract]  
    public interface IMusicService  
    {  
        //This operation uses a GET method.  
        [OperationContract]  
        [WebGet]  
        string LookUpArtist(string album);  
  
        //This operation will use a POST method.  
        [OperationContract]  
        [WebInvoke]  
        void AddAlbum(string user, string album);  
  
        //This operation will use POST method by default  
        //since nothing else is explicitly specified.  
        [OperationContract]  
        string[] GetAlbums(string user);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2. <span data-ttu-id="b63b7-129">Implemente `IMusicService` o contrato de serviço `MusicService`com um.</span><span class="sxs-lookup"><span data-stu-id="b63b7-129">Implement the `IMusicService` service contract with a `MusicService`.</span></span>
  
    ```csharp
    public class MusicService : IMusicService  
    {  
        public void AddAlbum(string user, string album)  
        {  
            //Add implementation here.  
        }  
  
         //Other operations omitted…  
    }  
    ```  
  
3. <span data-ttu-id="b63b7-130">Crie um novo arquivo chamado Service com uma extensão. svc no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b63b7-130">Create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="b63b7-131">Edite esse arquivo adicionando as informações de diretiva [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) apropriadas para o serviço.</span><span class="sxs-lookup"><span data-stu-id="b63b7-131">Edit this file by adding the appropriate [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="b63b7-132">Especifique que o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> deve ser usado [ \@](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) na diretiva ServiceHost para configurar automaticamente um ponto de extremidade do ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="b63b7-132">Specify that the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is to be used in the [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive to automatically configure an ASP.NET AJAX endpoint.</span></span>  
  
    ```
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.MusicService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
## <a name="to-call-the-service"></a><span data-ttu-id="b63b7-133">Para chamar o serviço</span><span class="sxs-lookup"><span data-stu-id="b63b7-133">To call the service</span></span>  
  
1. <span data-ttu-id="b63b7-134">Você pode testar as operações GET de seu serviço sem qualquer código de cliente, usando o navegador.</span><span class="sxs-lookup"><span data-stu-id="b63b7-134">You can test your service's GET operations without any client code, by using the browser.</span></span> <span data-ttu-id="b63b7-135">Por exemplo, se o serviço estiver configurado no `http://example.com/service.svc` endereço, a digitação `http://example.com/service.svc/LookUpArtist?album=SomeAlbum` na barra de endereços do navegador invocará o serviço e fará com que a resposta seja baixada ou exibida.</span><span class="sxs-lookup"><span data-stu-id="b63b7-135">For example, if your service is configured at the `http://example.com/service.svc` address, then typing `http://example.com/service.svc/LookUpArtist?album=SomeAlbum` into the browser address bar invokes the service and causes the response to be downloaded or displayed.</span></span>
  
2. <span data-ttu-id="b63b7-136">Você pode usar os serviços com operações GET da mesma maneira que qualquer outro serviço do ASP.NET AJAX, inserindo a URL do serviço na coleção scripts do controle Gerenciador de script do ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="b63b7-136">You can use services with GET operations in the same way as any other ASP.NET AJAX services - by entering the service URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="b63b7-137">Para obter um exemplo, consulte o [serviço básico do AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md).</span><span class="sxs-lookup"><span data-stu-id="b63b7-137">For an example, see the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b63b7-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b63b7-138">See also</span></span>

- [<span data-ttu-id="b63b7-139">Criando serviços WCF para o ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="b63b7-139">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="b63b7-140">Como: Migrar serviços Web do ASP.NET habilitados para AJAX para o WCF</span><span class="sxs-lookup"><span data-stu-id="b63b7-140">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
