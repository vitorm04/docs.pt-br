---
title: Criando serviços do WCF para o AJAX ASP.NET
ms.date: 03/30/2017
ms.assetid: 04c0402c-e617-4ba5-aedf-d17692234776
ms.openlocfilehash: 1f98a27197115c56686d593105f438fee633f34a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59174142"
---
# <a name="creating-wcf-services-for-aspnet-ajax"></a>Criando serviços do WCF para o AJAX ASP.NET
Microsoft ASP.NET AJAX permite que você rapidamente crie páginas da Web que incluem uma experiência de usuário com elementos de interface do usuário familiares. O ASP.NET AJAX fornece bibliotecas de script de cliente que incorporam navegadores ECMAScript (JavaScript) e tecnologias dinâmicas do DHTML (HTML) e ele se integra-los com a plataforma de desenvolvimento baseada em servidor do ASP.NET 2.0. Usando o ASP.NET AJAX, você pode melhorar a experiência do usuário e a eficiência de seus aplicativos Web.  
  
 ASP.NET AJAX consiste em bibliotecas de script de cliente e de componentes de servidor que são integradas para fornecer uma estrutura de desenvolvimento robusto. Para acessar um serviço em uma página ASP.NET: depois que a URL do serviço é adicionada ao controle na página do Gerenciador de Script do ASP.NET, operações de serviço podem ser invocadas usando código JavaScript que se parece exatamente com uma chamada de função JavaScript regular. Ver [aprender ASP.NET AJAX](https://go.microsoft.com/fwlink/?LinkId=186475) sobre o uso de serviços da Web dentro da estrutura do AJAX.  
  
 A maioria dos serviços do Windows Communication Foundation (WCF) pode ser exposta como um serviço compatível com o ASP.NET AJAX, adicionando um ponto de extremidade apropriado do ASP.NET AJAX.  
  
 Se você estiver usando o Visual Studio, você pode usar um modelo criado previamente para os serviços WCF habilitados para AJAX, disponíveis na **Adicionar Novo Item** caixa de diálogo ao trabalhar com Sites da Web ASP.NET ou aplicativos da Web.  
  
 Se você não estiver usando modelos do Visual Studio, há duas maneiras de criar um ponto de extremidade do ASP.NET AJAX:  
  
-   Crie o ponto de extremidade usando a ativação de host dinâmico sem usar qualquer configuração. Isso é a abordagem mais básica, se você estiver familiarizado com o sistema de configuração do WCF. Para obter mais informações, confira [Como: Adicionar um ponto de extremidade do ASP.NET AJAX sem utilizar a configuração](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
-   Adicione um ponto de extremidade habilitados para AJAX a um serviço WCF usando a configuração. Para obter mais informações, confira [Como: Usar a configuração para adicionar um ponto de extremidade do ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).  
  
 O modelo de programação Web descrito o [WCF Web HTTP de programação visão geral do modelo](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md) podem ser usadas com os serviços ASP.NET AJAX. Especificamente:  
  
-   Você pode usar o <xref:System.ServiceModel.Web.WebGetAttribute> e <xref:System.ServiceModel.Web.WebInvokeAttribute> atributos para selecionar entre verbos HTTP GET e HTTP POST. Se usados corretamente, isso pode melhorar significativamente o desempenho do aplicativo. Para obter mais informações, confira [Como: Escolha entre HTTP POST e HTTP GET solicitações para pontos de extremidade do ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md).  
  
-   Você pode usar o <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> e <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> propriedades para fazer com que seu serviço retornar dados XML em vez do padrão objeto notação JSON (JavaScript). Fazendo isso com a estrutura ASP.NET AJAX faz com que o cliente JavaScript receber um objeto XML DOM.  
  
    > [!WARNING]
    >  A operação deve definir o tipo de conteúdo como texto/xml para este trabalho. Caso contrário, o cliente JavaScript receberá uma cadeia de caracteres que contém o XML em vez de um objeto XML DOM.  
  
     Este é um exemplo de uma operação que retorna dados XML com o tipo de conteúdo definido adequadamente:  
  
    ```  
    [OperationContract, WebGet(ResponseFormat=WebMessageFormat.Xml)]  
    public XElement GetData()  
    {  
    XElement x;  
    //Get some data here...  
  
    WebOperationContext.Current.OutgoingResponse.ContentType = "text/xml";      
    return x;  
    }  
    ```  
  
-   Nenhuma outra propriedade sobre a <xref:System.ServiceModel.Web.WebGetAttribute> e <xref:System.ServiceModel.Web.WebInvokeAttribute> atributos podem ser alterados se a compatibilidade com o ASP.NET AJAX é necessária. Outros aspectos do modelo de programação da Web podem ser usados, desde as convenções de chamada do AJAX ASP.NET não sejam violadas.  
  
 Cenários mais avançados exigem alguns detalhes adicionais de suporte a AJAX no WCF ser compreendidos:  
  
-   Para entender como os dados são transferidos entre um cliente de página do AJAX e um serviço WCF usando JavaScript e para obter detalhes sobre como os tipos do .NET Framework são mapeados para tipos de JavaScript, consulte [suporte para JSON e outros dados transferir formata](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md).  
  
-   Para tirar proveito dos recursos do ASP.NET, por exemplo, autenticação baseada em URL e acessar as informações de sessão do ASP.NET, você talvez queira habilitar o modo de compatibilidade do ASP.NET por meio da configuração.  
  
 Pontos de extremidade do AJAX no WCF podem ser consumidos até mesmo sem a estrutura ASP.NET AJAX. Isso requer uma compreensão da arquitetura do suporte do suporte a AJAX no WCF. Para uma discussão sobre essa arquitetura, consulte [modelo de objeto de programação do WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md). Para obter um exemplo de código que demonstra essa abordagem, consulte o [serviço de AJAX com JSON e XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).  
  
## <a name="see-also"></a>Consulte também

- [Modelo de programação HTTP Web do WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [Como: Adicionar um ponto de extremidade do ASP.NET AJAX sem utilizar a configuração](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)
- [Como: Usar a configuração para adicionar um ponto de extremidade do ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
- [Como: Escolha entre HTTP POST e HTTP GET solicitações para pontos de extremidade do ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md)
