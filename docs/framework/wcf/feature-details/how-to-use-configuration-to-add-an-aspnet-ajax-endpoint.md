---
title: Como utilizar a configuração para adicionar um ponto de extremidade AJAX ASP.NET
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: 5314bb000371ee2d3eef2576e1edfa455aa65b90
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184831"
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a>Como utilizar a configuração para adicionar um ponto de extremidade AJAX ASP.NET
O Windows Communication Foundation (WCF) permite que você crie um serviço que disponibilize um ponto final habilitado para ASP.NET AJAX que pode ser chamado de JavaScript em um site da Web do cliente. Para criar tal ponto final, você pode usar um arquivo de configuração, como com todos os outros pontos finais do Windows Communication Foundation (WCF) ou usar um método que não exija nenhum elemento de configuração. Este tópico demonstra a abordagem de configuração.  
  
 A parte do procedimento que permite que o ponto final do serviço se torne ASP.NET <xref:System.ServiceModel.WebHttpBinding> habilitado para AJAX consiste em configurar o ponto final para usar o e adicionar o [ \<ambienteWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) comportamento de ponto final. Após a configuração do ponto final, as etapas para implementar e hospedar o serviço são semelhantes às usadas por qualquer serviço WCF. Para obter um exemplo de trabalho, consulte o [serviço AJAX usando HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
 Para obter mais informações sobre como configurar um ponto final ASP.NET AJAX sem usar a configuração, consulte [Como: Adicionar um ASP.NET endpoint AJAX sem usar a configuração](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
## <a name="to-create-a-basic-wcf-service"></a>Para criar um serviço básico wcf  
  
1. Defina um contrato básico de serviço <xref:System.ServiceModel.ServiceContractAttribute> WCF com uma interface marcada com o atributo. Marque cada <xref:System.ServiceModel.OperationContractAttribute>operação com o . Certifique-se de <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> definir a propriedade.  
  
    ```csharp
    [ServiceContract(Namespace = "MyService")]  
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
        // Other operations omitted…
    }
    ```  
  
3. Defina um namespace para as `ICalculator` implementações e `CalculatorService` embrulhe-os em um bloco de namespace.  
  
    ```csharp
    namespace Microsoft.Ajax.Samples
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
## <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a>Para criar um ponto final ASP.NET AJAX para o serviço  
  
1. Crie uma configuração [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) de comportamento e especifique o comportamento de>do WebScript para ASP.NET pontos finais habilitados para AJAX do serviço.  
  
    ```xml  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="AspNetAjaxBehavior">  
                    <enableWebScript />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
    </system.serviceModel>  
    ```  
  
2. Crie um ponto final para <xref:System.ServiceModel.WebHttpBinding> o serviço que usa o ASP.NET comportamento AJAX definido na etapa anterior.  
  
    ```xml  
    <system.serviceModel>  
        <services>  
            <service name="Microsoft.Ajax.Samples.CalculatorService">  
                <endpoint address=""  
                    behaviorConfiguration="AspNetAjaxBehavior"
                    binding="webHttpBinding"  
                    contract="Microsoft.Ajax.Samples.ICalculator" />  
            </service>  
        </services>  
    </system.serviceModel>
    ```  
  
## <a name="to-host-the-service-in-iis"></a>Para hospedar o serviço no IIS  
  
1. Para hospedar o serviço no IIS, crie um novo serviço chamado de arquivo com uma extensão .svc no aplicativo. Edite este arquivo adicionando as informações [ \@diretivas serviceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) apropriadas para o serviço. Por exemplo, o conteúdo no `CalculatorService` arquivo de serviço para a amostra contém as seguintes informações.  
  
    ```
    <%@ServiceHost
    language=c#
    Debug="true"
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2. Para obter mais informações sobre hospedagem no IIS, consulte [Como hospedar um Serviço WCF no IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
## <a name="to-call-the-service"></a>Para chamar o serviço  
  
1. O ponto final está configurado em um endereço vazio em relação ao arquivo .svc, de modo que o\<serviço já está disponível e pode `Add` ser invocado enviando solicitações para service.svc/operation> - por exemplo, service.svc/Add para a operação. Você pode usá-lo inserindo a URL de ponto final na coleção Scripts do ASP.NET controle do Gerenciador de Scripts AJAX. Por exemplo, consulte o [serviço AJAX usando HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
## <a name="see-also"></a>Confira também

- [Criando serviços do WCF para o AJAX ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [Como migrar serviços habilitados para AJAX ASP.NET para o WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
