---
title: "Como escolher entre solicitações HTTP POST e HTTP GET para pontos de extremidade AJAX ASP.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b47de82a-4c92-4af6-bceb-a5cb8bb8ede9
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fa8aceace03d1abb3bb83de1262331485f12ded3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-choose-between-http-post-and-http-get-requests-for-aspnet-ajax-endpoints"></a>Como escolher entre solicitações HTTP POST e HTTP GET para pontos de extremidade AJAX ASP.NET
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]permite que você crie um serviço que expõe um ponto de extremidade habilitado para AJAX do ASP.NET que pode ser chamado do JavaScript em um site do cliente. Os procedimentos básicos para a criação de tais serviços é abordado em [como: usar a configuração para adicionar um ponto de extremidade do ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) e [como: adicionar um ASP.NET AJAX ponto de extremidade sem usando a configuração](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
 ASP.NET AJAX oferece suporte a operações que usam os verbos HTTP POST e HTTP GET, com HTTP POST, sendo o padrão. Ao criar uma operação que não tem efeitos colaterais e retorna dados que raramente ou nunca muda, use HTTP GET. Resultados das operações GET podem ser armazenados em cache, o que significa que várias chamadas para a mesma operação poderão resultar em apenas uma solicitação ao serviço. O armazenamento em cache não é feito por [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] , mas podem ocorrer em qualquer nível (em um navegador do usuário, em um servidor de proxy e outros níveis.) O cache é vantajoso para aumentar o desempenho do serviço, mas pode não ser aceitável se dados forem alterados com frequência ou se alguma ação de executar a operação.  
  
 Por exemplo, se você estiver criando um serviço para gerenciar a biblioteca de música de um usuário, uma operação que procura artista com base em benefícios de título de um álbum usa GET, mas uma operação que adiciona um álbum à coleção pessoal do usuário deve usar POST.  
  
 Para controlar o tempo de vida do cache, use o <xref:System.ServiceModel.Web.OutgoingWebResponseContext> tipo. Por exemplo, durante a criação de um serviço que retorna a previsão atualizada a cada hora, você usaria obter mas limitar a duração do cache para uma hora ou menos para impedir que os usuários do serviço de acesso a dados obsoletos.  
  
 Ao usar os serviços de uma página AJAX ASP.NET que usam o controle do Gerenciador de Script, ele não faz diferença se usa a operação GET ou POST - o mecanismo de script do Gerenciador garante que o tipo de solicitação correto seja emitido.  
  
 Operações HTTP GET usam parâmetros de entrada com suporte a operações POST, incluindo tipos de contrato de dados complexos. No entanto, na maioria dos casos é recomendável para evitar excesso de parâmetros ou parâmetros que são muito complexos em operações GET porque ele reduz a eficiência do cache.  
  
 Este tópico demonstra como selecionar entre GET e POST, adicionando o <xref:System.ServiceModel.Web.WebGetAttribute> ou <xref:System.ServiceModel.Web.WebInvokeAttribute> atributos para as operações relevantes no contrato de serviço. As outras etapas (para implementar, configurar e hospedar o serviço) que são necessárias para que o serviço em execução são semelhantes àquelas usadas por qualquer serviço ASP.NET AJAX no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 Uma operação marcada com o <xref:System.ServiceModel.Web.WebGetAttribute> sempre usa uma solicitação GET. Uma operação marcada com o <xref:System.ServiceModel.Web.WebInvokeAttribute>, ou não marcada com nenhum dos dois atributos, usa uma solicitação POST. O <xref:System.ServiceModel.Web.WebInvokeAttribute> permite o uso de outros verbos HTTP, outro que GET e POST (como PUT e DELETE) por meio de <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> propriedade. No entanto, esses verbos não têm suporte pelo ASP.NET AJAX. Se você pretende usar o serviço de páginas ASP.NET usando o controle do Gerenciador de Script, não use o <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> propriedade.  
  
 Para obter um exemplo de funcionamento de alternar para GET, consulte o [serviço AJAX básico](../../../../docs/framework/wcf/samples/basic-ajax-service.md) exemplo.  
  
 Para obter um exemplo que usa POST, consulte o [AJAX Service usando HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) exemplo.  
  
### <a name="to-create-a-wcf-service-that-responds-to-http-get-or-http-post-requests"></a>Para criar um serviço WCF que responde a HTTP GET ou POST HTTP solicitações  
  
1.  Definir um basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] contrato de serviço com uma interface marcada com o <xref:System.ServiceModel.ServiceContractAttribute> atributo. Marcar cada operação com o <xref:System.ServiceModel.OperationContractAttribute>. Adicionar o <xref:System.ServiceModel.Web.WebGetAttribute> atributo para estipular que uma operação deve responder a solicitações HTTP GET. Você também pode adicionar o <xref:System.ServiceModel.Web.WebInvokeAttribute> de atributo para especificar explicitamente o HTTP POST ou não especificar um atributo, cujo padrão é HTTP POST.  
  
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
  
2.  Implementar o `IMusicService` contrato de serviço com um `MusicService`.  
  
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
  
3.  Crie um novo arquivo chamado serviço com uma extensão. svc no aplicativo. Editar esse arquivo adicionando apropriada [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) informações de diretiva para o serviço. Especifique que o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> deve ser usada no [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) diretiva para configurar automaticamente um ponto de extremidade do ASP.NET AJAX.  
  
    ```  
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.MusicService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
### <a name="to-call-the-service"></a>Para chamar o serviço  
  
1.  Você pode testar as operações GET do serviço qualquer código de cliente, usando o navegador. Por exemplo, se o serviço estiver configurado no endereço "http://example.com/service.svc", digitando "http://example.com/service.svc/LookUpArtist?album=SomeAlbum" na barra de endereços do navegador chama o serviço e faz com que a resposta baixado ou exibido.  
  
2.  Você pode usar os serviços com operações GET da mesma maneira como outros serviços ASP.NET AJAX - inserindo o serviço de controlar o URL para a coleção de Scripts do Gerenciador de Script ASP.NET AJAX. Para obter um exemplo, consulte o [serviço AJAX básico](../../../../docs/framework/wcf/samples/basic-ajax-service.md).  
  
## <a name="see-also"></a>Consulte também  
 [Criando serviços WCF para o ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [Como migrar serviços Web do ASP.NET habilitados para AJAX para o WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
