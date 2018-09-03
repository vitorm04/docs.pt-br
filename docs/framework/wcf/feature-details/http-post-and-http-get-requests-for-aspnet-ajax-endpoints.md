---
title: Como escolher entre solicitações HTTP POST e HTTP GET para pontos de extremidade AJAX ASP.NET
ms.date: 03/30/2017
ms.assetid: b47de82a-4c92-4af6-bceb-a5cb8bb8ede9
ms.openlocfilehash: 079bbd98b3fc3d5538f87cad39a4a83a0dc1e242
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43481836"
---
# <a name="how-to-choose-between-http-post-and-http-get-requests-for-aspnet-ajax-endpoints"></a>Como escolher entre solicitações HTTP POST e HTTP GET para pontos de extremidade AJAX ASP.NET
Windows Communication Foundation (WCF) permite que você crie um serviço que expõe um ponto de extremidade habilitados para AJAX ASP.NET que pode ser chamado do JavaScript em um site do cliente. Os procedimentos básicos para a criação de tais serviços é discutida [como: usar a configuração para adicionar um ponto de extremidade do ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) e [como: adicionar um ASP.NET AJAX ponto de extremidade sem usando configuração](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
 ASP.NET AJAX oferece suporte a operações que usam os verbos HTTP POST e HTTP GET, POST HTTP sendo o padrão. Durante a criação de uma operação que não tem efeitos colaterais e retorna dados que raramente ou nunca muda, use HTTP GET. Resultados de operações GET podem ser armazenados em cache, o que significa que várias chamadas para a mesma operação podem resultar em apenas uma solicitação ao seu serviço. O armazenamento em cache não é feito pelo WCF, mas pode ocorrer em qualquer nível (em um navegador do usuário, em um servidor proxy e outros níveis.) Armazenamento em cache é vantajoso se você quiser aumentar o desempenho do serviço, mas pode não ser aceitável se dados forem alterados com frequência ou se a operação executa alguma ação.  
  
 Por exemplo, se você estiver criando um serviço para gerenciar a biblioteca de música do usuário, uma operação que procura o artista, com base em título beneficiada de um álbum usando GET, mas uma operação que adiciona um álbum à coleção de pessoal do usuário deve usar POST.  
  
 Para controlar o tempo de vida do cache, use o <xref:System.ServiceModel.Web.OutgoingWebResponseContext> tipo. Por exemplo, durante a criação de um serviço que retorna previsões do tempo atualizado a cada hora, você usaria obter mas limitar a duração do cache para uma hora ou menos para impedir que os usuários do serviço de acesso a dados obsoletos.  
  
 Ao usar os serviços de uma página ASP.NET AJAX que usam o controle do Gerenciador de Script, ele não faz diferença se usa a operação GET ou POST - o mecanismo do Gerenciador de script garante que o tipo de solicitação correta seja emitido.  
  
 Operações HTTP GET usam parâmetros de entrada com suporte pelas operações POST, incluindo tipos de contrato de dados complexos. No entanto, na maioria dos casos é recomendável para evitar o excesso de parâmetros ou parâmetros que são muito complexos em operações GET, pois ele reduz a eficiência de cache.  
  
 Este tópico demonstra como selecionar entre GET e POST, adicionando a <xref:System.ServiceModel.Web.WebGetAttribute> ou <xref:System.ServiceModel.Web.WebInvokeAttribute> atributos para as operações relevantes no contrato de serviço. As outras etapas (para implementar, configurar e hospedar o serviço) que são necessárias para obter o serviço em execução são semelhantes àquelas usadas por qualquer serviço ASP.NET AJAX no WCF.  
  
 Uma operação marcada com o <xref:System.ServiceModel.Web.WebGetAttribute> sempre usa uma solicitação GET. Uma operação marcada com o <xref:System.ServiceModel.Web.WebInvokeAttribute>, ou não marcados com qualquer um dos dois atributos, que usa uma solicitação POST. O <xref:System.ServiceModel.Web.WebInvokeAttribute> permite o uso de outros verbos HTTP, a não ser GET e POST (por exemplo, PUT e DELETE) por meio de <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> propriedade. No entanto, esses verbos não são suportados pelo ASP.NET AJAX. Se você pretende usar o serviço de páginas ASP.NET usando o controle Script Manager, não use o <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> propriedade.  
  
 Para obter um exemplo de funcionamento de alternar para GET, consulte o [serviço de AJAX básico](../../../../docs/framework/wcf/samples/basic-ajax-service.md) exemplo.  
  
 Para obter um exemplo que usa o POST, consulte o [serviço de AJAX usando o HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) exemplo.  
  
### <a name="to-create-a-wcf-service-that-responds-to-http-get-or-http-post-requests"></a>Para criar um serviço WCF que responde a HTTP GET ou HTTP POST solicitações  
  
1.  Definir um contrato de serviço WCF básico com uma interface marcada com o <xref:System.ServiceModel.ServiceContractAttribute> atributo. Marcar cada operação com o <xref:System.ServiceModel.OperationContractAttribute>. Adicionar o <xref:System.ServiceModel.Web.WebGetAttribute> atributo para estipular que uma operação deve responder a solicitações HTTP GET. Você também pode adicionar o <xref:System.ServiceModel.Web.WebInvokeAttribute> de atributo para especificar explicitamente HTTP POST ou não especificar um atributo, cujo padrão é HTTP POST.  
  
    ```  
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
  
2.  Implemente a `IMusicService` contrato de serviço com um `MusicService`.  
  
    ```  
    public class MusicService : IMusicService  
    {  
        public void AddAlbum(string user, string album)  
        {  
            //Add implementation here.  
        }  
  
         //Other operations omitted…  
    }  
    ```  
  
3.  Crie um novo arquivo chamado de serviço com uma extensão. svc no aplicativo. Edite esse arquivo adicionando apropriado [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) informações de diretiva para o serviço. Especificar que o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> deve ser usada em de [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) diretiva para configurar automaticamente um ponto de extremidade do ASP.NET AJAX.  
  
    ```  
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.MusicService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
### <a name="to-call-the-service"></a>Para chamar o serviço  
  
1.  Você pode testar as operações de GET do seu serviço sem nenhum código de cliente, usando o navegador. Por exemplo, se seu serviço é configurado no "http://example.com/service.svc"endereço, em seguida, digitando"http://example.com/service.svc/LookUpArtist?album=SomeAlbum" no navegador a barra de endereços invoca o serviço e faz com que a resposta para ser baixado ou exibido.  
  
2.  Você pode usar os serviços com operações GET da mesma maneira que qualquer outro serviço ASP.NET AJAX - inserindo o serviço de controle de URL para a coleção de Scripts do Gerenciador de Script ASP.NET AJAX. Por exemplo, consulte o [serviço de AJAX básico](../../../../docs/framework/wcf/samples/basic-ajax-service.md).  
  
## <a name="see-also"></a>Consulte também  
 [Criando serviços WCF para o ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [Como migrar serviços Web do ASP.NET habilitados para AJAX para o WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
