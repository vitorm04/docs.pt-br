---
title: Descrição do Serviço
ms.date: 03/30/2017
ms.assetid: 7034b5d6-d608-45f3-b57d-ec135f83ff24
ms.openlocfilehash: d77797ed2871f2211ff142e2f45c160a92632138
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144080"
---
# <a name="service-description"></a>Descrição do Serviço
A amostra de Descrição de Serviço demonstra como um serviço pode recuperar suas informações de descrição do serviço em tempo de execução. A amostra é baseada no [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), com uma operação de serviço adicional definida para retornar informações descritivas sobre o serviço. As informações que são devolvidas listam os endereços base e os pontos finais do serviço. O serviço fornece essas <xref:System.ServiceModel.OperationContext> <xref:System.ServiceModel.ServiceHost>informações <xref:System.ServiceModel.Description.ServiceDescription> usando as classes e as classes.  
  
 Nesta amostra, o cliente é um aplicativo de console (.exe) e o serviço é hospedado pelo Internet Information Services (IIS).  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
 Esta amostra tem uma versão modificada `IServiceDescriptionCalculator`do contrato de calculadora chamado . O contrato define uma operação `GetServiceDescriptionInfo` de serviço adicional nomeada que retorna uma seqüência de várias linhas para o cliente que descreve o endereço base ou endereços e ponto final de serviço ou pontos finais para o serviço.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IServiceDescriptionCalculator  
{  
    [OperationContract]  
    int Add(int n1, int n2);  
    [OperationContract]  
    int Subtract(int n1, int n2);  
    [OperationContract]  
    int Multiply(int n1, int n2);  
    [OperationContract]  
    int Divide(int n1, int n2);  
    [OperationContract]  
    string GetServiceDescriptionInfo();  
}  
```  
  
 O código `GetServiceDescriptionInfo` de <xref:System.ServiceModel.Description.ServiceDescription> implementação para usar o para listar os pontos finais do serviço. Como os pontos finais de serviço podem ter endereços relativos, ele primeiro lista os endereços base do serviço. Para obter todas essas informações, o código <xref:System.ServiceModel.OperationContext.Current%2A>obtém seu contexto de operação usando . O <xref:System.ServiceModel.ServiceHost> objeto <xref:System.ServiceModel.Description.ServiceDescription> e seu objeto são recuperados do contexto da operação. Para listar os pontos finais básicos do serviço, o código <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A> itera através da coleção do host de serviço. Para listar os pontos finais do serviço, o código iterates através da coleção de pontos finais da descrição do serviço.  
  
```csharp
public string GetServiceDescriptionInfo()  
{  
    string info = "";  
    OperationContext operationContext = OperationContext.Current;  
    ServiceHost host = (ServiceHost)operationContext.Host;  
    ServiceDescription desc = host.Description;  
    // Enumerate the base addresses in the service host.  
    info += "Base addresses:\n";  
    foreach (Uri uri in host.BaseAddresses)  
    {  
        info += "    " + uri + "\n";  
    }  
    // Enumerate the service endpoints in the service description.  
    info += "Service endpoints:\n";  
    foreach (ServiceEndpoint endpoint in desc.Endpoints)  
    {  
        info += "    Address:  " + endpoint.Address + "\n";  
        info += "    Binding:  " + endpoint.Binding.Name + "\n";  
        info += "    Contract: " + endpoint.Contract.Name + "\n";  
    }  
     return info;  
}  
```  
  
 Quando você executa a amostra, você vê as operações `GetServiceDescriptionInfo` da calculadora e, em seguida, as informações de serviço devolvidas pela operação. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```console  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
Divide(22,7) = 3  
GetServiceDescriptionInfo  
Base addresses:  
    http://<machine-name>/ServiceModelSamples/service.svc  
    https://<machine-name>/ServiceModelSamples/service.svc  
Service endpoints:  
    Address:  http://<machine-name>/ServiceModelSamples/service.svc  
    Binding:  WSHttpBinding  
    Contract: IServiceDescriptionCalculator  
    Address:  http://<machine-name>/ServiceModelSamples/service.svc/mex  
    Binding:  MetadataExchangeHttpBinding  
    Contract: IMetadataExchange  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ServiceDescription`  
