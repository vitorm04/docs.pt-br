---
title: Como utilizar a configuração para adicionar um ponto de extremidade AJAX ASP.NET
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: 3ccfb34614707c17885da3ed37f545bbab808869
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978262"
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a>Como utilizar a configuração para adicionar um ponto de extremidade AJAX ASP.NET
Windows Communication Foundation (WCF) permite que você crie um serviço que disponibiliza um ponto de extremidade habilitado para AJAX ASP.NET que pode ser chamado do JavaScript em um site de cliente. Para criar esse ponto de extremidade, você pode usar um arquivo de configuração, assim como com todos os outros pontos de extremidade do Windows Communication Foundation (WCF) ou usar um método que não exija nenhum elemento de configuração. Este tópico demonstra a abordagem de configuração.  
  
 A parte do procedimento que permite que o ponto de extremidade de serviço se torne ASP.NET habilitado para AJAX consiste em configurar o ponto de extremidade para usar a <xref:System.ServiceModel.WebHttpBinding> e adicionar o comportamento de ponto de extremidade [\<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) . Depois de configurar o ponto de extremidade, as etapas para implementar e hospedar o serviço são semelhantes às usadas por qualquer serviço WCF. Para obter um exemplo funcional, consulte o [serviço AJAX usando http post](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
 Para obter mais informações sobre como configurar um ponto de extremidade do ASP.NET AJAX sem usar a configuração, consulte [como adicionar um ponto de extremidade do ASP.NET AJAX sem usar a configuração](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
## <a name="to-create-a-basic-wcf-service"></a>Para criar um serviço WCF básico  
  
1. Defina um contrato de serviço WCF básico com uma interface marcada com o atributo <xref:System.ServiceModel.ServiceContractAttribute>. Marque cada operação com a <xref:System.ServiceModel.OperationContractAttribute>. Certifique-se de definir a propriedade <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A>.  
  
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
  
2. Implemente o contrato de serviço `ICalculator` com um `CalculatorService`.  
  
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
  
3. Defina um namespace para as implementações de `ICalculator` e `CalculatorService` encapsulando-as em um bloco de namespace.  
  
    ```csharp
    namespace Microsoft.Ajax.Samples
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
## <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a>Para criar um ponto de extremidade do ASP.NET AJAX para o serviço  
  
1. Crie uma configuração de comportamento e especifique o comportamento [\<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) para pontos de extremidade habilitados para AJAX ASP.net do serviço.  
  
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
  
2. Crie um ponto de extremidade para o serviço que usa o <xref:System.ServiceModel.WebHttpBinding> e o comportamento ASP.NET AJAX definido na etapa anterior.  
  
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
  
1. Para hospedar o serviço no IIS, crie um novo arquivo chamado serviço com uma extensão. svc no aplicativo. Edite esse arquivo adicionando as informações de diretiva [ServiceHost do\@](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) apropriadas para o serviço. Por exemplo, o conteúdo no arquivo de serviço para o exemplo de `CalculatorService` contém as informações a seguir.  
  
    ```
    <%@ServiceHost   
    language=c#   
    Debug="true"   
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2. Para obter mais informações sobre hospedagem no IIS, consulte [como hospedar um serviço WCF no IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
## <a name="to-call-the-service"></a>Para chamar o serviço  
  
1. O ponto de extremidade é configurado em um endereço vazio em relação ao arquivo. svc, portanto, o serviço agora está disponível e pode ser invocado enviando solicitações à operação Service. svc/\<>-por exemplo, Service. svc/Add para a operação `Add`. Você pode usá-lo inserindo a URL do ponto de extremidade na coleção de scripts do controle Gerenciador de script do ASP.NET AJAX. Para obter um exemplo, consulte o [serviço AJAX usando http post](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
## <a name="see-also"></a>Consulte também

- [Criando serviços WCF para o ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [Como migrar serviços Web do ASP.NET habilitados para AJAX para o WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
