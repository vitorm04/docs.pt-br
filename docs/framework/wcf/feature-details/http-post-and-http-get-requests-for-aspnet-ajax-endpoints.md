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
# <a name="how-to-choose-between-http-post-and-http-get-requests-for-aspnet-ajax-endpoints"></a>Como: escolher entre solicitações HTTP POST e HTTP GET para pontos de extremidade AJAX ASP.NET

Windows Communication Foundation (WCF) permite que você crie um serviço que expõe um ponto de extremidade habilitado para AJAX ASP.NET que pode ser chamado do JavaScript em um site de cliente. Os procedimentos básicos para a criação desses serviços são discutidos em [como: Use a configuração para adicionar um ponto de](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) extremidade [do ASP.NET AJAX e como: Adicione um ponto de extremidade do ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)sem usar a configuração.  
  
 O ASP.NET AJAX dá suporte a operações que usam os verbos HTTP POST e HTTP GET, com HTTP POST sendo o padrão. Ao criar uma operação que não tem efeitos colaterais e retorna dados que raramente ou nunca são alterados, use HTTP GET em vez disso. Os resultados de operações GET podem ser armazenados em cache, o que significa que várias chamadas para a mesma operação podem resultar em apenas uma solicitação para seu serviço. O cache não é feito pelo WCF, mas pode ocorrer em qualquer nível (no navegador de um usuário, em um servidor proxy e em outros níveis). O cache é vantajoso se você deseja aumentar o desempenho do serviço, mas pode não ser aceitável se os dados forem alterados com frequência ou se a operação executar alguma ação.  
  
 Por exemplo, se você estiver criando um serviço para gerenciar a biblioteca de músicas de um usuário, uma operação que pesquisa o artista com base no título de um álbum se beneficia do uso de GET, mas uma operação que adiciona um álbum à coleção pessoal do usuário deve usar POST.  
  
 Para controlar o tempo de vida do cache, use <xref:System.ServiceModel.Web.OutgoingWebResponseContext> o tipo. Por exemplo, ao criar um serviço que retorna previsões do tempo atualizadas por hora, você usaria GET, mas limita a duração do cache a uma hora ou menos para impedir que os usuários do serviço acessem dados obsoletos.  
  
 Ao usar serviços de uma página ASP.NET AJAX que usa o controle Gerenciador de script, não faz diferença se a operação usa GET ou POST-o mecanismo do Gerenciador de scripts garante que o tipo de solicitação correto seja emitido.  
  
 As operações HTTP GET usam quaisquer parâmetros de entrada com suporte pelas operações POST, incluindo tipos de contrato de dados complexos. No entanto, na maioria dos casos, é recomendável evitar muitos parâmetros ou parâmetros que são muito complexos em operações GET, pois reduz a eficiência do cache.  
  
 Este tópico demonstra como selecionar entre Get e post adicionando os <xref:System.ServiceModel.Web.WebGetAttribute> atributos ou <xref:System.ServiceModel.Web.WebInvokeAttribute> às operações relevantes no contrato de serviço. As outras etapas (para implementar, configurar e hospedar o serviço) que são necessárias para obter o serviço em execução são semelhantes àquelas usadas por qualquer serviço AJAX ASP.NET no WCF.  
  
 Uma operação marcada com o <xref:System.ServiceModel.Web.WebGetAttribute> sempre usa uma solicitação get. Uma operação marcada com o <xref:System.ServiceModel.Web.WebInvokeAttribute>, ou não marcada com nenhum dos dois atributos, usa uma solicitação post. O <xref:System.ServiceModel.Web.WebInvokeAttribute> permite o uso de outros verbos HTTP, além de Get e post (como Put e Delete) por meio da <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> propriedade. No entanto, esses verbos não são suportados pelo ASP.NET AJAX. Se você pretende usar o serviço de páginas ASP.NET usando o controle Gerenciador de script, não use a <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> propriedade.  
  
 Para obter um exemplo funcional de como alternar para GET, consulte o exemplo de [serviço básico Ajax](../../../../docs/framework/wcf/samples/basic-ajax-service.md) .  
  
 Para obter um exemplo que usa POST, consulte o [serviço AJAX usando o exemplo http post](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) .  
  
## <a name="to-create-a-wcf-service-that-responds-to-http-get-or-http-post-requests"></a>Para criar um serviço WCF que responde a solicitações HTTP GET ou HTTP POST
  
1. Defina um contrato de serviço WCF básico com uma interface marcada com <xref:System.ServiceModel.ServiceContractAttribute> o atributo. Marque cada operação com o <xref:System.ServiceModel.OperationContractAttribute>. Adicione o <xref:System.ServiceModel.Web.WebGetAttribute> atributo para estipular que uma operação deve responder às solicitações HTTP Get. Você também pode adicionar o <xref:System.ServiceModel.Web.WebInvokeAttribute> atributo para especificar explicitamente http post, ou não especificar um atributo, que assume como padrão http post.
  
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
  
2. Implemente `IMusicService` o contrato de serviço `MusicService`com um.
  
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
  
3. Crie um novo arquivo chamado Service com uma extensão. svc no aplicativo. Edite esse arquivo adicionando as informações de diretiva [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) apropriadas para o serviço. Especifique que o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> deve ser usado [ \@](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) na diretiva ServiceHost para configurar automaticamente um ponto de extremidade do ASP.NET AJAX.  
  
    ```
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.MusicService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
## <a name="to-call-the-service"></a>Para chamar o serviço  
  
1. Você pode testar as operações GET de seu serviço sem qualquer código de cliente, usando o navegador. Por exemplo, se o serviço estiver configurado no `http://example.com/service.svc` endereço, a digitação `http://example.com/service.svc/LookUpArtist?album=SomeAlbum` na barra de endereços do navegador invocará o serviço e fará com que a resposta seja baixada ou exibida.
  
2. Você pode usar os serviços com operações GET da mesma maneira que qualquer outro serviço do ASP.NET AJAX, inserindo a URL do serviço na coleção scripts do controle Gerenciador de script do ASP.NET AJAX. Para obter um exemplo, consulte o [serviço básico do AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md).
  
## <a name="see-also"></a>Consulte também

- [Criando serviços WCF para o ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [Como: Migrar serviços Web do ASP.NET habilitados para AJAX para o WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
