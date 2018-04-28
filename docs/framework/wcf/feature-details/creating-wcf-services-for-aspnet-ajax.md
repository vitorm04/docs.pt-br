---
title: Criando serviços do WCF para o AJAX ASP.NET
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 04c0402c-e617-4ba5-aedf-d17692234776
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 64ab5c6bf4b555504562dbf68a60d032743df865
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="creating-wcf-services-for-aspnet-ajax"></a>Criando serviços do WCF para o AJAX ASP.NET
Microsoft ASP.NET AJAX permite que você crie rapidamente páginas da Web que incluem uma rica experiência de usuário com elementos de interface do usuário familiares. ASP.NET AJAX fornece bibliotecas de scripts de cliente que incorporam entre navegadores ECMAScript (JavaScript) e tecnologias HTML (DHTML) dinâmicas, e ele se integra-los com a plataforma de desenvolvimento baseada em servidor ASP.NET 2.0. Usando o ASP.NET AJAX, você pode melhorar a experiência do usuário e a eficiência de seus aplicativos Web.  
  
 ASP.NET AJAX consiste em bibliotecas de scripts de cliente e componentes do servidor que são integrados para fornecer uma estrutura de desenvolvimento robusta. Para acessar um serviço em uma página ASP.NET: quando a URL do serviço é adicionada ao controle na página Gerenciador de Script do ASP.NET, operações de serviço podem ser invocadas usando código JavaScript exatamente como uma chamada de função JavaScript regular. Consulte [Saiba ASP.NET AJAX](http://go.microsoft.com/fwlink/?LinkId=186475) sobre o uso de serviços Web dentro da estrutura de AJAX.  
  
 A maioria dos [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services pode ser exposto como um serviço compatível com o ASP.NET AJAX com a adição de um ponto de extremidade do ASP.NET AJAX apropriado.  
  
 Se você estiver usando o Visual Studio, você pode usar um modelo criado previamente para os serviços do WCF habilitado pelo AJAX, disponível no **Adicionar Novo Item** caixa de diálogo ao trabalhar com Sites da Web ASP.NET ou aplicativos da Web.  
  
 Se você não estiver usando os modelos do Visual Studio, há duas maneiras de criar um ponto de extremidade do ASP.NET AJAX:  
  
-   Crie o ponto de extremidade usando a ativação de host dinâmico sem usar qualquer configuração. Essa é a abordagem mais simples se você estiver familiarizado com o sistema de configuração do WCF. Para obter mais informações, consulte [como: adicionar um ASP.NET AJAX ponto de extremidade sem usando a configuração](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
-   Adicionar um ponto de extremidade habilitado para AJAX para um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usando a configuração de serviço. Para obter mais informações, consulte [como: usar a configuração para adicionar um ponto de extremidade do ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).  
  
 O modelo de programação Web descrito o [WCF Web HTTP de programação visão geral do modelo](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md) podem ser usadas com os serviços ASP.NET AJAX. Especificamente:  
  
-   Você pode usar o <xref:System.ServiceModel.Web.WebGetAttribute> e <xref:System.ServiceModel.Web.WebInvokeAttribute> atributos para selecionar entre os verbos HTTP GET e POST HTTP. Se usados corretamente, isso pode melhorar significativamente o desempenho do aplicativo. Para obter mais informações, consulte [como: escolha entre HTTP POST e HTTP GET solicitações para pontos de extremidade do ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md).  
  
-   Você pode usar o <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> e <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> propriedades para fazer com que o seu serviço retornar dados XML em vez do padrão JSON JavaScript Object Notation (). Fazer isso com a estrutura do ASP.NET AJAX faz com que o cliente JavaScript receber um objeto XML DOM.  
  
    > [!WARNING]
    >  A operação deve definir o tipo de conteúdo como text/xml para este trabalho. Caso contrário, o cliente JavaScript receberá uma cadeia de caracteres que contém o XML em vez de um objeto XML DOM.  
  
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
  
-   Não há outras propriedades a <xref:System.ServiceModel.Web.WebGetAttribute> e <xref:System.ServiceModel.Web.WebInvokeAttribute> atributos podem ser alterados se a compatibilidade com ASP.NET AJAX é necessária. Outros aspectos do modelo de programação da Web podem ser usados como as convenções de chamada AJAX ASP.NET não forem violadas.  
  
 Cenários mais avançados requerem alguns detalhes adicionais de suporte AJAX [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ser compreendidos:  
  
-   Para entender como os dados são transferidos entre um cliente de página do AJAX e um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service usando JavaScript e para obter detalhes sobre como os tipos do .NET Framework são mapeados para tipos de JavaScript, consulte [suporte para JSON e transferência de dados de outros formatos](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md) .  
  
-   Para tirar proveito dos recursos do ASP.NET, por exemplo, autenticação com base em URL e acessar as informações de sessão do ASP.NET, convém habilitar o modo de compatibilidade ASP.NET por meio de configuração.  
  
 Pontos de extremidade AJAX em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ainda pode ser consumido sem a estrutura do ASP.NET AJAX. Isso requer uma compreensão da arquitetura do suporte de suporte AJAX [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Para obter uma discussão dessa arquitetura, consulte [modelo de objeto de programação do WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md). Para obter um exemplo de código que demonstra essa abordagem, consulte o [serviço de AJAX com JSON e XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).  
  
## <a name="see-also"></a>Consulte também  
 [Modelo de programação HTTP Web do WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [Como adicionar um ponto de extremidade do ASP.NET AJAX sem utilizar a configuração](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)  
 [Como usar a configuração para adicionar um ponto de extremidade do ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)  
 [Como escolher entre solicitações HTTP POST e HTTP GET para pontos de extremidade do ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md)
