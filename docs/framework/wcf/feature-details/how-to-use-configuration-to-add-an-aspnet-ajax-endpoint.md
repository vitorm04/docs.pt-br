---
title: 'Como: usar a configuração para adicionar um ponto de extremidade AJAX ASP.NET'
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: 26a7b0d3fef67cf9dae0913e22e3cd7ec443c111
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59202970"
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a>Como: usar a configuração para adicionar um ponto de extremidade AJAX ASP.NET
Windows Communication Foundation (WCF) permite que você crie um serviço que permite que um ponto de extremidade habilitados para AJAX ASP.NET disponível que podem ser chamados do JavaScript em um site do cliente. Para criar um ponto de extremidade, você pode usar um arquivo de configuração, assim como acontece com todos os outros pontos de extremidade do Windows Communication Foundation (WCF) ou usar um método que não requer quaisquer elementos de configuração. Este tópico demonstra a abordagem de configuração.  
  
 A parte do procedimento que permite que o ponto de extremidade de serviço se torne habilitada para AJAX ASP.NET consiste em configurar o ponto de extremidade para usar o <xref:System.ServiceModel.WebHttpBinding> e adicione o [ \<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) comportamento de ponto de extremidade. Depois de configurar o ponto de extremidade, as etapas para implementar e hospedar o serviço são semelhantes às usadas por qualquer serviço do WCF. Para obter um exemplo de funcionamento, consulte o [serviço de AJAX usando o HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
 Para obter mais informações sobre como configurar um ponto de extremidade do ASP.NET AJAX sem utilizar a configuração, consulte [como: Adicionar um ponto de extremidade do ASP.NET AJAX sem utilizar a configuração](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
### <a name="to-create-a-basic-wcf-service"></a>Para criar um serviço WCF básico  
  
1.  Definir um contrato de serviço WCF básico com uma interface marcada com o <xref:System.ServiceModel.ServiceContractAttribute> atributo. Marcar cada operação com o <xref:System.ServiceModel.OperationContractAttribute>. Certifique-se de definir o <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> propriedade.  
  
    ```  
    [ServiceContract(Namespace = "MyService")]  
    public interface ICalculator  
    {  
        [OperationContract]  
         // This operation returns the sum of d1 and d2.  
        double Add(double n1, double n2);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2.  Implemente a `ICalculator` contrato de serviço com um `CalculatorService`.  
  
    ```  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3.  Definir um namespace para o `ICalculator` e `CalculatorService` implementações, encapsulando-as em um bloco de namespace.  
  
    ```  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a>Para criar um ponto de extremidade do ASP.NET AJAX para o serviço  
  
1.  Criar uma configuração de comportamento e especificar o [ \<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) comportamento para pontos de extremidade habilitados para AJAX ASP.NET do serviço.  
  
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
  
2.  Criar um ponto de extremidade para o serviço que usa o <xref:System.ServiceModel.WebHttpBinding> e o comportamento do AJAX ASP.NET definido na etapa anterior.  
  
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
  
### <a name="to-host-the-service-in-iis"></a>Para hospedar o serviço no IIS  
  
1.  Para hospedar o serviço no IIS, crie um novo arquivo chamado de serviço com uma extensão. svc no aplicativo. Edite esse arquivo adicionando apropriado [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) informações de diretiva para o serviço. Por exemplo, o conteúdo no arquivo de serviço para o `CalculatorService` exemplo contém as informações a seguir.  
  
    ```  
    <%@ServiceHost   
    language=c#   
    Debug="true"   
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2.  Para obter mais informações sobre como hospedar no IIS, consulte [como: Hospedar um serviço WCF no IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
### <a name="to-call-the-service"></a>Para chamar o serviço  
  
1.  O ponto de extremidade é configurado em um endereço relativo ao arquivo. svc, em branco para que o serviço agora está disponível e pode ser chamado enviando solicitações ao service.svc/\<operação > - por exemplo, service.svc/Add para o `Add` operação. Você pode usá-lo inserindo a URL do ponto de extremidade para a coleção de Scripts do controle do Gerenciador de Script do AJAX ASP.NET. Por exemplo, consulte o [serviço de AJAX usando o HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
## <a name="see-also"></a>Consulte também

- [Criando serviços do WCF para o AJAX ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [Como: migrar serviços Web habilitados para AJAX ASP.NET para o WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
