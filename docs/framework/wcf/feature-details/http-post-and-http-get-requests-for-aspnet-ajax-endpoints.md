---
title: Como escolher entre solicitações HTTP POST e HTTP GET para pontos de extremidade AJAX ASP.NET
ms.date: 03/30/2017
ms.assetid: b47de82a-4c92-4af6-bceb-a5cb8bb8ede9
ms.openlocfilehash: 0f7a221d1fd14b4a978683f008858e35cbd2df19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184749"
---
# <a name="how-to-choose-between-http-post-and-http-get-requests-for-aspnet-ajax-endpoints"></a><span data-ttu-id="ebecd-102">Como escolher entre solicitações HTTP POST e HTTP GET para pontos de extremidade AJAX ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ebecd-102">How to: Choose between HTTP POST and HTTP GET requests for ASP.NET AJAX Endpoints</span></span>

<span data-ttu-id="ebecd-103">O Windows Communication Foundation (WCF) permite que você crie um serviço que exponha um ponto final ASP.NET habilitado para AJAX que pode ser chamado de JavaScript em um site do cliente.</span><span class="sxs-lookup"><span data-stu-id="ebecd-103">Windows Communication Foundation (WCF) allows you to create a service that exposes an ASP.NET AJAX-enabled endpoint that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="ebecd-104">Os procedimentos básicos para a construção desses serviços são discutidos em [Como: Usar configuração para adicionar um ponto final ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) e [como: Adicionar um ponto final ASP.NET AJAX sem usar a configuração](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="ebecd-104">The basic procedures for building such services is discussed in [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) and [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
 <span data-ttu-id="ebecd-105">ASP.NET AJAX suporta operações que usam os verbos HTTP POST e HTTP GET, sendo o HTTP POST o padrão.</span><span class="sxs-lookup"><span data-stu-id="ebecd-105">ASP.NET AJAX supports operations that use the HTTP POST and HTTP GET verbs, with HTTP POST being the default.</span></span> <span data-ttu-id="ebecd-106">Ao criar uma operação que não tem efeitos colaterais e retorna dados que raramente ou nunca mudam, use HTTP GET em vez disso.</span><span class="sxs-lookup"><span data-stu-id="ebecd-106">When creating an operation that has no side effects and returns data that rarely or never changes, use HTTP GET instead.</span></span> <span data-ttu-id="ebecd-107">Os resultados das operações GET podem ser armazenados em cache, o que significa que várias chamadas para a mesma operação podem resultar em apenas uma solicitação ao seu serviço.</span><span class="sxs-lookup"><span data-stu-id="ebecd-107">Results of GET operations can be cached, which means that multiple calls to the same operation may result in only one request to your service.</span></span> <span data-ttu-id="ebecd-108">O cache não é feito pelo WCF, mas pode ocorrer em qualquer nível (no navegador de um usuário, em um servidor proxy e em outros níveis.) O cache é vantajoso se você quiser aumentar o desempenho do serviço, mas pode não ser aceitável se os dados mudarem com freqüência ou se a operação realizar alguma ação.</span><span class="sxs-lookup"><span data-stu-id="ebecd-108">The caching is not done by WCF but can take place at any level (in a user's browser, on a proxy server, and other levels.) Caching is advantageous if you want to increase service performance, but may not be acceptable if data changes frequently or if the operation performs some action.</span></span>  
  
 <span data-ttu-id="ebecd-109">Por exemplo, se você está projetando um serviço para gerenciar a biblioteca de música de um usuário, uma operação que procura o artista com base no título de um álbum se beneficia do uso do GET, mas uma operação que adiciona um álbum à coleção pessoal do usuário deve usar O POST.</span><span class="sxs-lookup"><span data-stu-id="ebecd-109">For example, if you are designing service to manage a user's music library, an operation that looks up the artist based on an album's title benefits from using GET, but an operation that adds an album to the user's personal collection must use POST.</span></span>  
  
 <span data-ttu-id="ebecd-110">Para controlar a vida útil <xref:System.ServiceModel.Web.OutgoingWebResponseContext> do cache, use o tipo.</span><span class="sxs-lookup"><span data-stu-id="ebecd-110">To control the lifetime of the cache, use the <xref:System.ServiceModel.Web.OutgoingWebResponseContext> type.</span></span> <span data-ttu-id="ebecd-111">Por exemplo, ao projetar um serviço que retorna as previsões meteorológicas atualizadas de hora em hora, você usaria get mas limitaria a duração do cache a uma hora ou menos para impedir que os usuários do serviço acessassem dados obsoletos.</span><span class="sxs-lookup"><span data-stu-id="ebecd-111">For example, when designing a service that returns weather forecasts updated hourly, you would use GET but limit the cache duration to an hour or less to prevent the users of the service from accessing stale data.</span></span>  
  
 <span data-ttu-id="ebecd-112">Ao usar serviços de uma página ajax ASP.NET que usam o controle do Script Manager, não faz diferença se a operação usa GET ou POST - o mecanismo do gerenciador de scripts garante que o tipo de solicitação correta seja emitido.</span><span class="sxs-lookup"><span data-stu-id="ebecd-112">When using services from an ASP.NET AJAX page that use the Script Manager control, it makes no difference whether the operation uses GET or POST - the script manager mechanism ensures that the correct request type is issued.</span></span>  
  
 <span data-ttu-id="ebecd-113">As operações HTTP GET usam quaisquer parâmetros de entrada suportados pelas operações POST, incluindo tipos complexos de contratos de dados.</span><span class="sxs-lookup"><span data-stu-id="ebecd-113">HTTP GET operations use any input parameters supported by POST operations, including complex data contract types.</span></span> <span data-ttu-id="ebecd-114">No entanto, na maioria dos casos, recomenda-se evitar muitos parâmetros ou parâmetros que são muito complexos nas operações GET porque reduz a eficiência do cache.</span><span class="sxs-lookup"><span data-stu-id="ebecd-114">However, in most cases it is recommended to avoid too many parameters or parameters that are too complex in GET operations because it reduces caching efficiency.</span></span>  
  
 <span data-ttu-id="ebecd-115">Este tópico demonstra como selecionar entre GET <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> e POST adicionando ou atributos às operações relevantes no contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="ebecd-115">This topic demonstrates how to select between GET and POST by adding the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes to the relevant operations in the service contract.</span></span> <span data-ttu-id="ebecd-116">As outras etapas (para implementar, configurar e hospedar o serviço) que são necessárias para fazer o serviço funcionar são semelhantes às usadas por qualquer ASP.NET serviço AJAX no WCF.</span><span class="sxs-lookup"><span data-stu-id="ebecd-116">The other steps (to implement, configure and host the service) that are required to get the service running are similar to those used by any ASP.NET AJAX service in WCF.</span></span>  
  
 <span data-ttu-id="ebecd-117">Uma operação marcada <xref:System.ServiceModel.Web.WebGetAttribute> com o sempre usa uma solicitação GET.</span><span class="sxs-lookup"><span data-stu-id="ebecd-117">An operation marked with the <xref:System.ServiceModel.Web.WebGetAttribute> always uses a GET request.</span></span> <span data-ttu-id="ebecd-118">Uma operação marcada <xref:System.ServiceModel.Web.WebInvokeAttribute>com o , ou não marcado com qualquer um dos dois atributos, usa uma solicitação POST.</span><span class="sxs-lookup"><span data-stu-id="ebecd-118">An operation marked with the <xref:System.ServiceModel.Web.WebInvokeAttribute>, or not marked with any of the two attributes, uses a POST request.</span></span> <span data-ttu-id="ebecd-119">O <xref:System.ServiceModel.Web.WebInvokeAttribute> permite o uso de outros verbos HTTP, além de GET <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> e POST (como PUT e DELETE) através da propriedade.</span><span class="sxs-lookup"><span data-stu-id="ebecd-119">The <xref:System.ServiceModel.Web.WebInvokeAttribute> allows the use of other HTTP verbs, other than GET and POST (such as PUT and DELETE) through the <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> property.</span></span> <span data-ttu-id="ebecd-120">No entanto, esses verbos não são suportados por ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="ebecd-120">However, these verbs are not supported by ASP.NET AJAX.</span></span> <span data-ttu-id="ebecd-121">Se você pretende usar o serviço a partir de ASP.NET <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> páginas usando o controle script manager, não use a propriedade.</span><span class="sxs-lookup"><span data-stu-id="ebecd-121">If you intend to use the service from ASP.NET pages using the Script Manager control, do not use the <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> property.</span></span>  
  
 <span data-ttu-id="ebecd-122">Para obter um exemplo de mudança para GET, consulte a amostra [basic do Serviço AJAX.](../../../../docs/framework/wcf/samples/basic-ajax-service.md)</span><span class="sxs-lookup"><span data-stu-id="ebecd-122">For a working example of switching to GET, see the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>  
  
 <span data-ttu-id="ebecd-123">Para obter uma amostra que usa POST, consulte o [serviço AJAX usando a](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) amostra HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="ebecd-123">For a sample that uses POST, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) sample.</span></span>  
  
## <a name="to-create-a-wcf-service-that-responds-to-http-get-or-http-post-requests"></a><span data-ttu-id="ebecd-124">Para criar um serviço WCF que responda às solicitações HTTP GET ou HTTP POST</span><span class="sxs-lookup"><span data-stu-id="ebecd-124">To create a WCF service that responds to HTTP GET or HTTP POST requests</span></span>
  
1. <span data-ttu-id="ebecd-125">Defina um contrato básico de serviço <xref:System.ServiceModel.ServiceContractAttribute> WCF com uma interface marcada com o atributo.</span><span class="sxs-lookup"><span data-stu-id="ebecd-125">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="ebecd-126">Marque cada <xref:System.ServiceModel.OperationContractAttribute>operação com o .</span><span class="sxs-lookup"><span data-stu-id="ebecd-126">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="ebecd-127">Adicione <xref:System.ServiceModel.Web.WebGetAttribute> o atributo para estipular que uma operação deve responder às solicitações HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="ebecd-127">Add the <xref:System.ServiceModel.Web.WebGetAttribute> attribute to stipulate that an operation should respond to HTTP GET requests.</span></span> <span data-ttu-id="ebecd-128">Você também pode <xref:System.ServiceModel.Web.WebInvokeAttribute> adicionar o atributo para especificar explicitamente HTTP POST, ou não especificar um atributo, que é padrão para HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="ebecd-128">You can also add the <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute to explicitly specify HTTP POST, or not specify an attribute, which defaults to HTTP POST.</span></span>
  
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
  
2. <span data-ttu-id="ebecd-129">Implementar `IMusicService` o contrato `MusicService`de serviço com um .</span><span class="sxs-lookup"><span data-stu-id="ebecd-129">Implement the `IMusicService` service contract with a `MusicService`.</span></span>
  
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
  
3. <span data-ttu-id="ebecd-130">Crie um novo serviço chamado de arquivo com uma extensão .svc no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ebecd-130">Create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="ebecd-131">Edite este arquivo adicionando as informações [ \@diretivas serviceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) apropriadas para o serviço.</span><span class="sxs-lookup"><span data-stu-id="ebecd-131">Edit this file by adding the appropriate [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="ebecd-132">Especifique se o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> é usado na [ \@](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) diretiva ServiceHost para configurar automaticamente um ponto final ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="ebecd-132">Specify that the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is to be used in the [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive to automatically configure an ASP.NET AJAX endpoint.</span></span>  
  
    ```
    <%@ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Ajax.Samples.MusicService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
## <a name="to-call-the-service"></a><span data-ttu-id="ebecd-133">Para chamar o serviço</span><span class="sxs-lookup"><span data-stu-id="ebecd-133">To call the service</span></span>  
  
1. <span data-ttu-id="ebecd-134">Você pode testar as operações GET do seu serviço sem qualquer código de cliente, usando o navegador.</span><span class="sxs-lookup"><span data-stu-id="ebecd-134">You can test your service's GET operations without any client code, by using the browser.</span></span> <span data-ttu-id="ebecd-135">Por exemplo, se o seu `http://example.com/service.svc` serviço estiver `http://example.com/service.svc/LookUpArtist?album=SomeAlbum` configurado no endereço, digitando a barra de endereços do navegador, o serviço invoca o serviço e faz com que a resposta seja baixada ou exibida.</span><span class="sxs-lookup"><span data-stu-id="ebecd-135">For example, if your service is configured at the `http://example.com/service.svc` address, then typing `http://example.com/service.svc/LookUpArtist?album=SomeAlbum` into the browser address bar invokes the service and causes the response to be downloaded or displayed.</span></span>
  
2. <span data-ttu-id="ebecd-136">Você pode usar serviços com operações GET da mesma forma que qualquer outro ASP.NET serviços AJAX - inserindo a URL de serviço na coleção Scripts do controle ASP.NET AJAX Script Manager.</span><span class="sxs-lookup"><span data-stu-id="ebecd-136">You can use services with GET operations in the same way as any other ASP.NET AJAX services - by entering the service URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="ebecd-137">Por exemplo, consulte o [Serviço Básico AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md).</span><span class="sxs-lookup"><span data-stu-id="ebecd-137">For an example, see the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ebecd-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="ebecd-138">See also</span></span>

- [<span data-ttu-id="ebecd-139">Criando serviços do WCF para o AJAX ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ebecd-139">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="ebecd-140">Como migrar serviços habilitados para AJAX ASP.NET para o WCF</span><span class="sxs-lookup"><span data-stu-id="ebecd-140">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
