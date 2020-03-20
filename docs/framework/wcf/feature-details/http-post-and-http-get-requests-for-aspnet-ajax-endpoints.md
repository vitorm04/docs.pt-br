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
# <a name="how-to-choose-between-http-post-and-http-get-requests-for-aspnet-ajax-endpoints"></a>Como escolher entre solicitações HTTP POST e HTTP GET para pontos de extremidade AJAX ASP.NET

O Windows Communication Foundation (WCF) permite que você crie um serviço que exponha um ponto final ASP.NET habilitado para AJAX que pode ser chamado de JavaScript em um site do cliente. Os procedimentos básicos para a construção desses serviços são discutidos em [Como: Usar configuração para adicionar um ponto final ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) e [como: Adicionar um ponto final ASP.NET AJAX sem usar a configuração](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
 ASP.NET AJAX suporta operações que usam os verbos HTTP POST e HTTP GET, sendo o HTTP POST o padrão. Ao criar uma operação que não tem efeitos colaterais e retorna dados que raramente ou nunca mudam, use HTTP GET em vez disso. Os resultados das operações GET podem ser armazenados em cache, o que significa que várias chamadas para a mesma operação podem resultar em apenas uma solicitação ao seu serviço. O cache não é feito pelo WCF, mas pode ocorrer em qualquer nível (no navegador de um usuário, em um servidor proxy e em outros níveis.) O cache é vantajoso se você quiser aumentar o desempenho do serviço, mas pode não ser aceitável se os dados mudarem com freqüência ou se a operação realizar alguma ação.  
  
 Por exemplo, se você está projetando um serviço para gerenciar a biblioteca de música de um usuário, uma operação que procura o artista com base no título de um álbum se beneficia do uso do GET, mas uma operação que adiciona um álbum à coleção pessoal do usuário deve usar O POST.  
  
 Para controlar a vida útil <xref:System.ServiceModel.Web.OutgoingWebResponseContext> do cache, use o tipo. Por exemplo, ao projetar um serviço que retorna as previsões meteorológicas atualizadas de hora em hora, você usaria get mas limitaria a duração do cache a uma hora ou menos para impedir que os usuários do serviço acessassem dados obsoletos.  
  
 Ao usar serviços de uma página ajax ASP.NET que usam o controle do Script Manager, não faz diferença se a operação usa GET ou POST - o mecanismo do gerenciador de scripts garante que o tipo de solicitação correta seja emitido.  
  
 As operações HTTP GET usam quaisquer parâmetros de entrada suportados pelas operações POST, incluindo tipos complexos de contratos de dados. No entanto, na maioria dos casos, recomenda-se evitar muitos parâmetros ou parâmetros que são muito complexos nas operações GET porque reduz a eficiência do cache.  
  
 Este tópico demonstra como selecionar entre GET <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> e POST adicionando ou atributos às operações relevantes no contrato de serviço. As outras etapas (para implementar, configurar e hospedar o serviço) que são necessárias para fazer o serviço funcionar são semelhantes às usadas por qualquer ASP.NET serviço AJAX no WCF.  
  
 Uma operação marcada <xref:System.ServiceModel.Web.WebGetAttribute> com o sempre usa uma solicitação GET. Uma operação marcada <xref:System.ServiceModel.Web.WebInvokeAttribute>com o , ou não marcado com qualquer um dos dois atributos, usa uma solicitação POST. O <xref:System.ServiceModel.Web.WebInvokeAttribute> permite o uso de outros verbos HTTP, além de GET <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> e POST (como PUT e DELETE) através da propriedade. No entanto, esses verbos não são suportados por ASP.NET AJAX. Se você pretende usar o serviço a partir de ASP.NET <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> páginas usando o controle script manager, não use a propriedade.  
  
 Para obter um exemplo de mudança para GET, consulte a amostra [basic do Serviço AJAX.](../../../../docs/framework/wcf/samples/basic-ajax-service.md)  
  
 Para obter uma amostra que usa POST, consulte o [serviço AJAX usando a](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) amostra HTTP POST.  
  
## <a name="to-create-a-wcf-service-that-responds-to-http-get-or-http-post-requests"></a>Para criar um serviço WCF que responda às solicitações HTTP GET ou HTTP POST
  
1. Defina um contrato básico de serviço <xref:System.ServiceModel.ServiceContractAttribute> WCF com uma interface marcada com o atributo. Marque cada <xref:System.ServiceModel.OperationContractAttribute>operação com o . Adicione <xref:System.ServiceModel.Web.WebGetAttribute> o atributo para estipular que uma operação deve responder às solicitações HTTP GET. Você também pode <xref:System.ServiceModel.Web.WebInvokeAttribute> adicionar o atributo para especificar explicitamente HTTP POST, ou não especificar um atributo, que é padrão para HTTP POST.
  
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
  
2. Implementar `IMusicService` o contrato `MusicService`de serviço com um .
  
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
  
3. Crie um novo serviço chamado de arquivo com uma extensão .svc no aplicativo. Edite este arquivo adicionando as informações [ \@diretivas serviceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) apropriadas para o serviço. Especifique se o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> é usado na [ \@](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) diretiva ServiceHost para configurar automaticamente um ponto final ASP.NET AJAX.  
  
    ```
    <%@ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Ajax.Samples.MusicService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
## <a name="to-call-the-service"></a>Para chamar o serviço  
  
1. Você pode testar as operações GET do seu serviço sem qualquer código de cliente, usando o navegador. Por exemplo, se o seu `http://example.com/service.svc` serviço estiver `http://example.com/service.svc/LookUpArtist?album=SomeAlbum` configurado no endereço, digitando a barra de endereços do navegador, o serviço invoca o serviço e faz com que a resposta seja baixada ou exibida.
  
2. Você pode usar serviços com operações GET da mesma forma que qualquer outro ASP.NET serviços AJAX - inserindo a URL de serviço na coleção Scripts do controle ASP.NET AJAX Script Manager. Por exemplo, consulte o [Serviço Básico AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md).
  
## <a name="see-also"></a>Confira também

- [Criando serviços do WCF para o AJAX ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [Como migrar serviços habilitados para AJAX ASP.NET para o WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
