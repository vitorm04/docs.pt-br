---
title: Criando serviços do WCF para o AJAX ASP.NET
ms.date: 03/30/2017
ms.assetid: 04c0402c-e617-4ba5-aedf-d17692234776
ms.openlocfilehash: 64be5c8ec0d3ee105e026794912a9820bd7892d0
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045961"
---
# <a name="creating-wcf-services-for-aspnet-ajax"></a>Criando serviços do WCF para o AJAX ASP.NET

Microsoft ASP.NET AJAX permite que você crie rapidamente páginas da Web que incluem uma experiência de usuário avançada com elementos de interface do usuário altamente responsivos e familiares. O ASP.NET AJAX fornece bibliotecas de scripts de cliente que incorporam o JavaScript (linguagem cruzada) e as tecnologias HTML dinâmicos (DHTML), e integra-os com a plataforma de desenvolvimento baseada em servidor ASP.NET 2,0. Usando o ASP.NET AJAX, você pode melhorar a experiência do usuário e a eficiência dos seus aplicativos Web.

O ASP.NET AJAX consiste em bibliotecas de scripts de cliente e de componentes de servidor que são integrados para fornecer uma estrutura de desenvolvimento robusta. Para acessar um serviço de uma página do ASP.NET: depois que a URL do serviço é adicionada ao controle do Gerenciador de scripts do ASP.NET na página, as operações de serviço podem ser invocadas usando o código JavaScript que é exatamente como uma chamada de função JavaScript regular. Consulte [saiba mais sobre o ASP.NET AJAX](https://go.microsoft.com/fwlink/?LinkId=186475) sobre o uso de serviços Web na estrutura AJAX.

A maioria dos serviços de Windows Communication Foundation (WCF) pode ser exposta como um serviço compatível com o ASP.NET AJAX, adicionando um ponto de extremidade do ASP.NET AJAX apropriado.

Se você estiver usando o Visual Studio, poderá usar um modelo predefinido para serviços WCF habilitados para AJAX, disponível na caixa de diálogo **Adicionar novo item** ao trabalhar com sites ou aplicativos web do ASP.net.

Se você não estiver usando os modelos do Visual Studio, há duas maneiras de criar um ponto de extremidade do ASP.NET AJAX:

- Crie o ponto de extremidade usando a ativação dinâmica do host sem usar nenhuma configuração. Essa é a abordagem mais básica se você não estiver familiarizado com o sistema de configuração do WCF. Para obter mais informações, confira [Como: Adicione um ponto de extremidade do ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)sem usar a configuração.

- Adicione um ponto de extremidade habilitado para AJAX a um serviço WCF usando a configuração. Para obter mais informações, confira [Como: Use a configuração para adicionar um ponto de](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)extremidade do ASP.NET AJAX.

O modelo de programação da Web descrito na [visão geral do modelo de programação Web http do WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md) pode ser usado com serviços AJAX ASP.net. Especificamente:

- Você pode usar os <xref:System.ServiceModel.Web.WebGetAttribute> atributos <xref:System.ServiceModel.Web.WebInvokeAttribute> e para selecionar entre os verbos HTTP Get e http post. Se usado corretamente, isso pode melhorar significativamente o desempenho do seu aplicativo. Para obter mais informações, confira [Como: Escolha entre solicitações HTTP POST e HTTP GET para pontos de extremidade](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md)do ASP.NET AJAX.

- Você pode usar as <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> propriedades <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> e para fazer com que o serviço retorne dados XML em vez do JavaScript Object Notation padrão (JSON). Fazer isso com a estrutura do ASP.NET AJAX faz com que o cliente JavaScript receba um objeto XML DOM.

  > [!WARNING]
  > Sua operação deve definir o tipo de conteúdo como text/xml para que isso funcione. Caso contrário, o cliente JavaScript receberá uma cadeia de caracteres contendo o XML em vez de um objeto XML DOM.

    Veja a seguir um exemplo de uma operação que retorna dados XML com o tipo de conteúdo definido adequadamente:

  ```csharp
  [OperationContract, WebGet(ResponseFormat=WebMessageFormat.Xml)]
  public XElement GetData()
  {
      XElement x;
      //Get some data here...

      WebOperationContext.Current.OutgoingResponse.ContentType = "text/xml";
      return x;
  }
  ```

- Nenhuma outra propriedade nos atributos <xref:System.ServiceModel.Web.WebGetAttribute> e <xref:System.ServiceModel.Web.WebInvokeAttribute> poderá ser alterada se a compatibilidade com o AJAX ASP.NET for necessária. Outros aspectos do modelo de programação da Web podem ser usados desde que as convenções de chamada do AJAX ASP.NET não sejam violadas.

 Cenários mais avançados exigem alguns detalhes adicionais de suporte a AJAX no WCF que serão compreendidos:

- Para entender como os dados são transferidos entre um cliente de página AJAX e um serviço WCF usando JavaScript e para obter detalhes sobre como .NET Framework tipos são mapeados para tipos JavaScript, consulte [suporte para JSON e outros formatos de transferência de dados](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md).

- Para aproveitar os recursos do ASP.NET, por exemplo, a autenticação baseada em URL e o acesso às informações de sessão do ASP.NET, talvez você queira habilitar o modo de compatibilidade do ASP.NET por meio da configuração.

Os pontos de extremidade AJAX no WCF podem até mesmo ser consumidos sem a estrutura do ASP.NET AJAX. Isso requer uma compreensão da arquitetura de suporte do suporte AJAX no WCF. Para obter uma discussão sobre essa arquitetura, consulte [modelo de objeto de programação do WCF Web http](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md). Para obter um exemplo de código que demonstra essa abordagem, consulte o [serviço AJAX com JSON e XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).

## <a name="see-also"></a>Consulte também

- [Modelo de programação HTTP Web do WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [Como: Adicionar um ponto de extremidade do ASP.NET AJAX sem usar a configuração](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)
- [Como: Usar a configuração para adicionar um ponto de extremidade do ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
- [Como: Escolha entre solicitações HTTP POST e HTTP GET para pontos de extremidade do ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md)
