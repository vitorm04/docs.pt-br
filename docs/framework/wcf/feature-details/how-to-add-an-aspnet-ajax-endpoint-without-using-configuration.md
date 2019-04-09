---
title: 'Como: adicionar um ponto de extremidade de ASP.NET AJAX sem utilizar a configuração'
ms.date: 03/30/2017
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
ms.openlocfilehash: caaa89573d272c5d11d179b08c2d9e24c76d21e6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59140615"
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a>Como: adicionar um ponto de extremidade de ASP.NET AJAX sem utilizar a configuração
Windows Communication Foundation (WCF) permite que você crie um serviço que expõe um ponto de extremidade habilitados para AJAX ASP.NET que pode ser chamado do JavaScript em um site do cliente. Para criar um ponto de extremidade, você pode usar um arquivo de configuração, assim como acontece com todos os outros pontos de extremidade do WCF ou usar um método que não requer quaisquer elementos de configuração. Este tópico demonstra a segunda abordagem.  
  
 Para criar serviços com pontos de extremidade do ASP.NET AJAX sem configuração, os serviços devem ser hospedados pelo Internet Information Services (IIS). Para ativar um ponto de extremidade do ASP.NET AJAX usando essa abordagem, especifique o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> como o parâmetro de fábrica na [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) diretiva no arquivo. svc. Esta fábrica personalizada é o componente que configura automaticamente um ponto de extremidade do ASP.NET AJAX para que ele pode ser chamado do JavaScript em um site do cliente.  
  
 Para obter um exemplo de funcionamento, consulte o [serviço de AJAX sem configuração](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).  
  
 Para obter uma descrição de como configurar um ponto de extremidade do ASP.NET AJAX usando elementos de configuração, consulte [como: Usar a configuração para adicionar um ponto de extremidade do ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).  
  
### <a name="to-create-a-basic-wcf-service"></a>Para criar um serviço WCF básico  
  
1.  Definir um contrato de serviço WCF básico com uma interface marcada com o <xref:System.ServiceModel.ServiceContractAttribute> atributo. Marcar cada operação com o <xref:System.ServiceModel.OperationContractAttribute>. Certifique-se de definir o <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> propriedade.  
  
    ```csharp  
    [ServiceContract(Namespace = "MyService")]]  
    public interface ICalculator  
    {  
        [OperationContract]  
        // This operation returns the sum of d1 and d2.  
        double Add(double n1, double n2);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2.  Implemente a `ICalculator` contrato de serviço com um `CalculatorService`.  
  
    ```csharp  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3.  Definir um namespace para o `ICalculator` e `CalculatorService` implementações, encapsulando-as em um bloco de namespace.  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a>Para hospedar o serviço nos serviços de informações da Internet sem configuração  
  
1.  Crie um novo arquivo chamado de serviço com uma extensão. svc no aplicativo. Edite esse arquivo adicionando apropriado [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) informações de diretiva para o serviço. Especificar que o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> deve ser usada em de [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) diretiva para configurar automaticamente um ponto de extremidade do ASP.NET AJAX.  
  
    ```  
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2.  O serviço de compilação e chamá-lo a partir do cliente. Serviços de informações da Internet (IIS) ativa o serviço quando chamado. Para obter mais informações sobre como hospedar no IIS, consulte [como: Hospedar um serviço WCF no IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
### <a name="to-call-the-service"></a>Para chamar o serviço  
  
1.  O ponto de extremidade é configurado em um endereço relativo ao arquivo. svc, em branco para que o serviço agora está disponível e pode ser chamado enviando solicitações ao service.svc/\<operação > - por exemplo, service.svc/Add para o `Add` operação. Você pode usá-lo inserindo a URL do serviço para a coleção de Scripts do controle do Gerenciador de Script do AJAX ASP.NET. Por exemplo, consulte o [serviço de AJAX sem configuração](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).  
  
## <a name="example"></a>Exemplo  
  
 O ponto de extremidade configurado automaticamente é criado em um endereço em branco em relação a URL base. Um arquivo de configuração também pode ser adicionado e usado com essa abordagem. Se o arquivo de configuração contém as definições de ponto de extremidade, esses pontos de extremidade são adicionados ao ponto de extremidade configurado automaticamente.  
  
 Por exemplo, SVC usa o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> e o diretório de serviço contém um arquivo Web. config que define um ponto de extremidade para o mesmo serviço usando o <xref:System.ServiceModel.BasicHttpBinding> no endereço relativo "soap". Nesse caso, o serviço contém dois pontos de extremidade: um de cada SVC (que responde às solicitações do ASP.NET AJAX) e outro no service.svc/soap (que responde às solicitações SOAP).  
  
 Se o arquivo de configuração define um ponto de extremidade em um endereço relativo vazio e o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> é usado, uma exceção é lançada e o serviço não for iniciado.  
  
 Você não pode usar a configuração para modificar as configurações no ponto de extremidade configurado automaticamente. Se qualquer configuração (por exemplo, uma cota do leitor) deve ser modificado, você não deve usar a abordagem sem configuração, removendo o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> do arquivo. svc e criando uma entrada de configuração para o ponto de extremidade.  
  
 Se seu serviço requer o modo de compatibilidade do ASP.NET - por exemplo, se ele usa o <xref:System.Web.HttpContext> classe ou mecanismos de autorização do ASP.NET - um arquivo de configuração ainda é necessário para ativar esse modo. O elemento de configuração necessário é a [ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) elemento, que deve ser adicionado da seguinte maneira.  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 Para obter mais informações, consulte o [serviços WCF e ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) tópico.  
  
 O <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> classe é uma classe derivada de <xref:System.ServiceModel.Activation.ServiceHostFactory>. Para obter uma explicação detalhada do mecanismo de fábrica do host de serviço, consulte o [estendendo hospedagem usando ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) tópico.  
  
## <a name="see-also"></a>Consulte também

- [Criando serviços do WCF para o AJAX ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [Como: migrar serviços Web habilitados para AJAX ASP.NET para o WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
