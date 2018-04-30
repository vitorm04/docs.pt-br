---
title: Como utilizar a configuração para adicionar um ponto de extremidade AJAX ASP.NET
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 28051dbed626dc0073a38e72f2cdc21ea108a32e
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a>Como utilizar a configuração para adicionar um ponto de extremidade AJAX ASP.NET
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] permite que você crie um serviço que permite que um ponto de extremidade AJAX ASP.NET habilitado disponível que pode ser chamado do JavaScript em um site do cliente. Para criar um ponto de extremidade, você pode usar um arquivo de configuração, assim como acontece com todos os outros [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pontos de extremidade, ou use um método que não requer nenhum elemento de configuração. Este tópico demonstra o método de configuração.  
  
 A parte do procedimento que permite que o ponto de extremidade de serviço seja habilitado pelo AJAX ASP.NET consiste em configurar o ponto de extremidade para usar o <xref:System.ServiceModel.WebHttpBinding> e adicionar o [ \<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) comportamento de ponto de extremidade. Depois de configurar o ponto de extremidade, as etapas para implementar e hospedar o serviço são semelhantes àquelas usadas por qualquer [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço. Para obter um exemplo de funcionamento, consulte o [AJAX Service usando HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
 Para obter mais informações sobre como configurar um ponto de extremidade do ASP.NET AJAX sem utilizar a configuração, consulte [como: adicionar um ASP.NET AJAX ponto de extremidade sem usando a configuração](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
### <a name="to-create-a-basic-wcf-service"></a>Para criar um serviço WCF básico  
  
1.  Definir um basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] contrato de serviço com uma interface marcada com o <xref:System.ServiceModel.ServiceContractAttribute> atributo. Marcar cada operação com o <xref:System.ServiceModel.OperationContractAttribute>. Certifique-se de definir o <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> propriedade.  
  
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
  
2.  Implementar o `ICalculator` contrato de serviço com um `CalculatorService`.  
  
    ```  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3.  Definir um namespace para o `ICalculator` e `CalculatorService` implementações encapsulando-os em um bloco de namespace.  
  
    ```  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a>Para criar um ponto de extremidade AJAX ASP.NET para o serviço  
  
1.  Criar uma configuração de comportamento e especificar o [ \<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) comportamento para habilitado para AJAX ASP.NET pontos de extremidade do serviço.  
  
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
  
2.  Criar um ponto de extremidade para o serviço que usa o <xref:System.ServiceModel.WebHttpBinding> e o comportamento de ASP.NET AJAX definido na etapa anterior.  
  
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
  
1.  Para hospedar o serviço no IIS, crie um novo arquivo chamado serviço com uma extensão. svc no aplicativo. Editar esse arquivo adicionando apropriada [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) informações de diretiva para o serviço. Por exemplo, o conteúdo do arquivo de serviço para o `CalculatorService` exemplo contém as informações a seguir.  
  
    ```  
    <%@ServiceHost   
    language=c#   
    Debug="true"   
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2.  Para obter mais informações sobre como hospedar no IIS, consulte [como: hospedar um serviço WCF no IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
### <a name="to-call-the-service"></a>Para chamar o serviço  
  
1.  O ponto de extremidade é configurado em um endereço vazio em relação ao arquivo. svc, portanto, o serviço agora está disponível e pode ser chamado enviando solicitações para service.svc/\<operação > - por exemplo, service.svc/Add para o `Add` operação. Você pode usá-lo digitando a URL de ponto de extremidade para a coleção de Scripts do controle de Gerenciador de Script do ASP.NET AJAX. Para obter um exemplo, consulte o [AJAX Service usando HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
## <a name="see-also"></a>Consulte também  
 [Criando serviços WCF para o ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [Como migrar serviços Web do ASP.NET habilitados para AJAX para o WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
