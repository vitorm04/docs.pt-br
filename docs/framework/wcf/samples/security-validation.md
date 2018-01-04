---
title: "Validação de segurança"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48dcd496-0c4f-48ce-8b9b-0e25b77ffa58
caps.latest.revision: "35"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 86a10a4117a5bbeb48e9d1d15b1ce8da9d7c7751
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="security-validation"></a>Validação de segurança
Este exemplo demonstra como usar um comportamento personalizado para validar os serviços em um computador para garantir que eles atendam a critérios específicos. Neste exemplo, os serviços são validados pelo comportamento personalizado verificação por meio de cada ponto de extremidade do serviço e para verificar se eles contêm elementos de associação de segurança. Este exemplo se baseia o [Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
>  As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
## <a name="endpoint-validation-custom-behavior"></a>Comportamento de validação de ponto de extremidade personalizado  
 Adicionando o código de usuário para o `Validate` método contido o <xref:System.ServiceModel.Description.IServiceBehavior> interface, comportamento personalizado pode ser passado a um serviço ou um ponto de extremidade para executar as ações definidas pelo usuário. O código a seguir é usado para executar um loop através de cada ponto de extremidade contido em um serviço, que pesquisa por meio de suas coleções de associação para associações de seguras.  
  
```  
public void Validate(ServiceDescription serviceDescription,   
                                       ServiceHostBase serviceHostBase)  
{  
    // Loop through each endpoint individually gathering their    
       binding elements.  
    foreach (ServiceEndpoint endpoint in serviceDescription.Endpoints)  
    {  
        secureElementFound = false;  
  
        // Retrieve the endpoint's binding element collection.  
        BindingElementCollection bindingElements =   
            endpoint.Binding.CreateBindingElements();  
  
        // Look to see if the binding elements collection contains any   
        // secure binding elements. Transport, Asymmetric, and Symmetric      
        // binding elements are all derived from SecurityBindingElement.  
        if ((bindingElements.Find<SecurityBindingElement>() != null) || (bindingElements.Find<HttpsTransportBindingElement>() != null) || (bindingElements.Find<WindowsStreamSecurityBindingElement>() != null) || (bindingElements.Find<SslStreamSecurityBindingElement>() != null))  
        {  
            secureElementFound = true;  
        }  
  
    // Send a message to the system event viewer when an endpoint is deemed insecure.  
    if (!secureElementFound)  
        throw new Exception(System.DateTime.Now.ToString() + ": The endpoint \"" + endpoint.Name + "\" has no secure bindings.");  
    }  
}  
```  
  
 Adicionando o seguinte código ao arquivo Web. config adiciona o `serviceValidate` extensão de comportamento para o serviço reconheça.  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="endpointValidate" type="Microsoft.ServiceModel.Samples.EndpointValidateElement, endpointValidate, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
    </extensions>  
...  
```  
  
 Depois que a extensão de comportamento é adicionada ao serviço, agora é possível adicionar o `endpointValidate` comportamento à lista de comportamentos no arquivo Web. config e, assim, para o serviço.  
  
```xml  
<behaviors>  
    <serviceBehaviors>  
        <behavior name="CalcServiceSEB1">  
            <serviceMetadata httpGetEnabled="true" />  
            <endpointValidate />  
        </behavior>  
    </serviceBehaviors>  
</behaviors>  
```  
  
 Aplicam comportamentos e suas extensões que são adicionados ao arquivo Web. config do comportamento a serviços individuais, enquanto quando adicionado ao arquivo Machine. config aplicar o comportamento para cada serviço ativo no computador.  
  
> [!NOTE]
>  Ao adicionar o comportamento para todos os serviços, é recomendável fazer backup do arquivo Machine. config antes de fazer qualquer alteração.  
  
 Agora execute o cliente fornecido no diretório client\bin deste exemplo. Tem uma exceção ocorre com a seguinte mensagem: "o serviço solicitado, 'http://localhost/servicemodelsamples/service.svc' não pôde ser ativado." Isso é esperado porque um ponto de extremidade é considerado inseguro pelo ponto de extremidade de comportamento de validação e impede que o serviço seja iniciado. O comportamento também gera uma exceção interna que descreve qual ponto de extremidade é não segura e grava uma mensagem no Visualizador de eventos do sistema com a origem de "System. ServiceModel 4.0.0.0" e a categoria "WebHost". Também é possível ativar o rastreamento do serviço neste exemplo. Isso permite que o usuário exibir as exceções geradas pelo comportamento de validação de ponto de extremidade abrindo os rastreamentos resultante do serviço usando a ferramenta do Visualizador de rastreamento de serviço.  
  
#### <a name="to-view-failed-endpoint-validation-exception-messages-in-the-event-viewer"></a>Para exibir mensagens de exceção de validação de ponto de extremidade no Visualizador de eventos de falha  
  
1.  Clique o **iniciar** menu e selecione **executar...** .  
  
2.  Tipo `eventvwr` e clique em **Okey**.  
  
3.  Na janela do Visualizador de eventos, clique em **aplicativo**.  
  
4.  Duas vezes no evento adicionado recentemente "System. ServiceModel 4.0.0.0" sob a categoria "WebHost" no **aplicativo** janela para exibir mensagens de ponto de extremidade insegura.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ServiceValidation`  
  
## <a name="see-also"></a>Consulte também  
 [Exemplos de monitoramento do AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
