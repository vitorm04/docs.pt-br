---
title: Validação de segurança
ms.date: 03/30/2017
ms.assetid: 48dcd496-0c4f-48ce-8b9b-0e25b77ffa58
ms.openlocfilehash: 17e6e250c6b345477f7c9b377eb8e16ff4331ca7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183375"
---
# <a name="security-validation"></a>Validação de segurança
Esta amostra demonstra como usar um comportamento personalizado para validar serviços em um computador para garantir que eles atendam a critérios específicos. Nesta amostra, os serviços são validados pelo comportamento personalizado, escaneando cada ponto final do serviço e verificando se contêm elementos de ligação seguras. Esta amostra é baseada no [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
## <a name="endpoint-validation-custom-behavior"></a>Comportamento personalizado de validação de ponto final  
 Adicionando código de `Validate` usuário ao <xref:System.ServiceModel.Description.IServiceBehavior> método contido na interface, o comportamento personalizado pode ser dado a um serviço ou ponto final para executar ações definidas pelo usuário. O código a seguir é usado para fazer loop através de cada ponto final contido em um serviço, que pesquisa através de suas coleções de vinculação para vinculações seguras.  
  
```csharp
public void Validate(ServiceDescription serviceDescription,
                                       ServiceHostBase serviceHostBase)  
{  
    // Loop through each endpoint individually, gathering their
    // binding elements.  
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
  
 Adicionar o seguinte código ao arquivo `serviceValidate` Web.config adiciona a extensão de comportamento para que o serviço seja reconhecido.  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="endpointValidate" type="Microsoft.ServiceModel.Samples.EndpointValidateElement, endpointValidate, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
    </extensions>  
...  
```  
  
 Uma vez que a extensão de comportamento é `endpointValidate` adicionada ao serviço, agora é possível adicionar o comportamento à lista de comportamentos no arquivo Web.config e, assim, ao serviço.  
  
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
  
 Comportamentos e suas extensões adicionadas ao arquivo Web.config aplicam comportamento a serviços individuais, enquanto quando adicionados ao arquivo Machine.config aplicam comportamento a todos os serviços ativos no computador.  
  
> [!NOTE]
> Ao adicionar comportamento a todos os serviços, é sugerido fazer backup do arquivo Machine.config antes de fazer qualquer alteração.  
  
 Agora execute o cliente fornecido no diretório cliente\bin desta amostra. Uma exceção ocorre com a seguinte mensagem:http://localhost/servicemodelsamples/service.svc"O serviço solicitado' não pôde ser ativado." Isso é esperado porque um ponto final é considerado inseguro pelo ponto final validando o comportamento e impede que o serviço seja iniciado. O comportamento também lança uma exceção interna que descreve qual ponto final é inseguro e grava uma mensagem para o sistema Event Viewer a fonte System.ServiceModel 4.0.0.0 e a categoria WebHost. Também é possível ativar o rastreamento do serviço nesta amostra. Isso permite que o usuário visualize as exceções lançadas pelo comportamento de validação de ponto final, abrindo os traços de serviço resultantes usando a ferramenta Visualizador de rastreamento de serviço.  
  
#### <a name="to-view-failed-endpoint-validation-exception-messages-in-the-event-viewer"></a>Para exibir mensagens de exceção de validação de ponto final com falha no Visualizador de eventos  
  
1. Clique no menu **Iniciar** e selecione **Executar...**.  
  
2. Digite `eventvwr` e clique em **OK**.  
  
3. Na janela Visualizador de eventos, clique **em Aplicativo**.  
  
4. Clique duas vezes no evento "System.ServiceModel 4.0.0.0" adicionado recentemente na categoria "WebHost" na janela **Aplicativo** para exibir mensagens de ponto final inseguras.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ServiceValidation`  
  
## <a name="see-also"></a>Confira também

- [AppFabric que monitora Exemplos](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
