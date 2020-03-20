---
title: Como adicionar um ponto de extremidade de ASP.NET AJAX sem utilizar a configuração
ms.date: 03/30/2017
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
ms.openlocfilehash: 9935e2a7738796fff9a037b09237a6acbf7bf988
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185129"
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a>Como adicionar um ponto de extremidade de ASP.NET AJAX sem utilizar a configuração
O Windows Communication Foundation (WCF) permite que você crie um serviço que exponha um ponto final ASP.NET habilitado para AJAX que pode ser chamado de JavaScript em um site do cliente. Para criar tal ponto final, você pode usar um arquivo de configuração, como com todos os outros pontos finais do WCF, ou usar um método que não exija nenhum elemento de configuração. Este tópico demonstra a segunda abordagem.  
  
 Para criar serviços com ASP.NET pontos finais do AJAX sem configuração, os serviços devem ser hospedados pelos Serviços de Informação da Internet (IIS). Para ativar um ponto final ASP.NET AJAX <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> usando essa abordagem, especifique como parâmetro de fábrica na diretiva [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) no arquivo .svc. Esta fábrica personalizada é o componente que configura automaticamente um ponto final ASP.NET AJAX para que ele possa ser chamado de JavaScript em um site da Web do cliente.  
  
 Para um exemplo de trabalho, consulte o [serviço AJAX sem configuração](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).  
  
 Para obter um esboço de como configurar um ponto final ASP.NET AJAX usando elementos de configuração, consulte [Como: Usar configuração para adicionar um ponto final ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).  
  
### <a name="to-create-a-basic-wcf-service"></a>Para criar um serviço básico wcf  
  
1. Defina um contrato básico de serviço <xref:System.ServiceModel.ServiceContractAttribute> WCF com uma interface marcada com o atributo. Marque cada <xref:System.ServiceModel.OperationContractAttribute>operação com o . Certifique-se de <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> definir a propriedade.  
  
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
  
2. Implementar `ICalculator` o contrato `CalculatorService`de serviço com um .  
  
    ```csharp  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3. Defina um namespace para as `ICalculator` implementações e `CalculatorService` embrulhe-os em um bloco de namespace.  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a>Para hospedar o serviço em Serviços de Informação da Internet sem configuração  
  
1. Crie um novo serviço chamado de arquivo com uma extensão .svc no aplicativo. Edite este arquivo adicionando as informações [ \@diretivas serviceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) apropriadas para o serviço. Especifique se o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> é usado na [ \@](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) diretiva ServiceHost para configurar automaticamente um ponto final ASP.NET AJAX.  
  
    ```text
    <%@ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2. Construa o serviço e chame-o do cliente. O Internet Information Services (IIS) ativa o serviço quando chamado. Para obter mais informações sobre hospedagem no IIS, consulte [Como hospedar um Serviço WCF no IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
### <a name="to-call-the-service"></a>Para chamar o serviço  
  
1. O ponto final está configurado em um endereço vazio em relação ao arquivo .svc, de modo que o\<serviço já está disponível e pode `Add` ser invocado enviando solicitações para service.svc/operation> - por exemplo, service.svc/Add para a operação. Você pode usá-lo inserindo a URL de serviço na coleção Scripts do ASP.NET controle do Gerenciador de Scripts AJAX. Por exemplo, consulte o [serviço AJAX sem configuração](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).  
  
## <a name="example"></a>Exemplo  
  
 O ponto final configurado automaticamente é criado em um endereço vazio em relação à URL base. Um arquivo de configuração também pode ser adicionado e usado com essa abordagem. Se o arquivo de configuração contiver definições de ponto final, esses pontos finais serão adicionados ao ponto final configurado automaticamente.  
  
 Por exemplo, service.svc <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> usa o diretório e o diretório de serviço contém um arquivo Web.config que define um ponto final para o mesmo serviço usando o <xref:System.ServiceModel.BasicHttpBinding> endereço relativo "sabão". Neste caso, o serviço contém dois pontos finais: um no service.svc (que responde a pedidos de ASP.NET AJAX) e outro em service.svc/soap (que responde a solicitações SOAP).  
  
 Se o arquivo de configuração definir um ponto <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> final em um endereço relativo vazio e for usado, uma exceção será lançada e o serviço não será acionado.  
  
 Não é possível usar a configuração para modificar as configurações no ponto final configurado automaticamente. Se qualquer configuração (como uma cota de leitor) for modificada, você <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> não deve usar a abordagem sem configuração removendo o arquivo .svc e criando uma entrada de configuração para o ponto final.  
  
 Se o seu serviço exigir ASP.NET modo de <xref:System.Web.HttpContext> compatibilidade - por exemplo, se ele usa os mecanismos de autorização de classe ou ASP.NET - um arquivo de configuração ainda é necessário para ativar este modo. O elemento de configuração necessário é o [ \<elemento serviceHostingEnvironment>,](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) que deve ser adicionado da seguinte forma.  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 Para obter mais informações, consulte o tópico [WCF Services e ASP.NET.](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)  
  
 A <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> classe é uma <xref:System.ServiceModel.Activation.ServiceHostFactory>classe derivada de . Para obter uma explicação detalhada do mecanismo de fábrica do host de serviço, consulte o tópico [Extensão da hospedagem usando serviceHostFactory.](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)  
  
## <a name="see-also"></a>Confira também

- [Criando serviços do WCF para o AJAX ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [Como migrar serviços habilitados para AJAX ASP.NET para o WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
