---
title: 'Como: adicionar um ponto de extremidade de ASP.NET AJAX sem utilizar a configuração'
ms.date: 03/30/2017
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
ms.openlocfilehash: 4a7ff48e529ab58c8744edea22d52ad12a4d7b96
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895082"
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a>Como: adicionar um ponto de extremidade de ASP.NET AJAX sem utilizar a configuração
Windows Communication Foundation (WCF) permite que você crie um serviço que expõe um ponto de extremidade habilitado para AJAX ASP.NET que pode ser chamado do JavaScript em um site de cliente. Para criar esse ponto de extremidade, você pode usar um arquivo de configuração, assim como com todos os outros pontos de extremidade do WCF, ou usar um método que não exija nenhum elemento de configuração. Este tópico demonstra a segunda abordagem.  
  
 Para criar serviços com pontos de extremidade do ASP.NET AJAX sem configuração, os serviços devem ser hospedados pelo Serviços de Informações da Internet (IIS). Para ativar um ponto de extremidade ASP.NET AJAX usando essa abordagem, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> especifique o como o parâmetro Factory [ \@](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) na diretiva ServiceHost no arquivo. svc. Essa fábrica personalizada é o componente que configura automaticamente um ponto de extremidade do ASP.NET AJAX para que ele possa ser chamado do JavaScript em um site do cliente.  
  
 Para obter um exemplo funcional, consulte o [serviço AJAX sem configuração](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).  
  
 Para obter uma descrição de como configurar um ponto de extremidade do ASP.NET AJAX usando elementos [de configuração, consulte Como: Use a configuração para adicionar um ponto de](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)extremidade do ASP.NET AJAX.  
  
### <a name="to-create-a-basic-wcf-service"></a>Para criar um serviço WCF básico  
  
1. Defina um contrato de serviço WCF básico com uma interface marcada com <xref:System.ServiceModel.ServiceContractAttribute> o atributo. Marque cada operação com o <xref:System.ServiceModel.OperationContractAttribute>. Certifique-se de definir <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> a propriedade.  
  
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
  
2. Implemente `ICalculator` o contrato de serviço `CalculatorService`com um.  
  
    ```csharp  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3. Defina um namespace para as `ICalculator` implementações e `CalculatorService` encapsulando-as em um bloco de namespace.  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a>Para hospedar o serviço em Serviços de Informações da Internet sem configuração  
  
1. Crie um novo arquivo chamado Service com uma extensão. svc no aplicativo. Edite esse arquivo adicionando as informações de diretiva [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) apropriadas para o serviço. Especifique que o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> deve ser usado [ \@](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) na diretiva ServiceHost para configurar automaticamente um ponto de extremidade do ASP.NET AJAX.  
  
    ```text
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2. Crie o serviço e chame-o do cliente. Serviços de Informações da Internet (IIS) ativa o serviço quando chamado. Para obter mais informações sobre hospedagem no IIS, [consulte Como: Hospede um serviço WCF no IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
### <a name="to-call-the-service"></a>Para chamar o serviço  
  
1. O ponto de extremidade é configurado em um endereço vazio relativo ao arquivo. svc, portanto, o serviço agora está disponível e pode ser invocado enviando solicitações para Service.\<svc/operation >-por exemplo, Service. svc/Add `Add` para a operação. Você pode usá-lo inserindo a URL do serviço na coleção de scripts do controle Gerenciador de script do ASP.NET AJAX. Para obter um exemplo, consulte o [serviço AJAX sem configuração](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).  
  
## <a name="example"></a>Exemplo  
  
 O ponto de extremidade configurado automaticamente é criado em um endereço vazio relativo à URL base. Um arquivo de configuração também pode ser adicionado e usado com essa abordagem. Se o arquivo de configuração contiver definições de ponto de extremidade, esses pontos de extremidade serão adicionados ao ponto de extremidades configurado automaticamente.  
  
 Por exemplo, o Service. svc usa <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> o e o diretório de serviço contém um arquivo Web. config que define um ponto de extremidade para o <xref:System.ServiceModel.BasicHttpBinding> mesmo serviço usando o no endereço relativo "SOAP". Nesse caso, o serviço contém dois pontos de extremidade: um no Service. svc (que responde às solicitações do AJAX ASP.NET) e outro em Service. svc/SOAP (que responde às solicitações SOAP).  
  
 Se o arquivo de configuração definir um ponto de extremidade em um endereço relativo <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> vazio e o for usado, uma exceção será lançada e o serviço não será iniciado.  
  
 Você não pode usar a configuração para modificar as configurações no ponto de extremidade configurado automaticamente. Se qualquer configuração (como uma cota de leitor) precisar ser modificada, você não deverá usar a abordagem sem configuração removendo o <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> do arquivo. svc e criando uma entrada de configuração para o ponto de extremidade.  
  
 Se o serviço exigir o modo de compatibilidade ASP.net, por exemplo, se ele <xref:System.Web.HttpContext> usar os mecanismos de autorização de classe ou ASP.net, um arquivo de configuração ainda será necessário para ativar esse modo. O elemento de configuração necessário é o elemento [ \<> do ServiceHostingEnvironment](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) , que deve ser adicionado da seguinte maneira.  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 Para obter mais informações, consulte o tópico [Serviços do WCF e ASP.net](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) .  
  
 A <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> classe é uma classe derivada de <xref:System.ServiceModel.Activation.ServiceHostFactory>. Para obter uma explicação detalhada do mecanismo de fábrica do host de serviço, consulte o tópico [ampliando a hospedagem usando o ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) .  
  
## <a name="see-also"></a>Consulte também

- [Criando serviços WCF para o ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [Como: Migrar serviços Web do ASP.NET habilitados para AJAX para o WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
