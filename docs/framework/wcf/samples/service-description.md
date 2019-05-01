---
title: Descrição do serviço
ms.date: 03/30/2017
ms.assetid: 7034b5d6-d608-45f3-b57d-ec135f83ff24
ms.openlocfilehash: d68bc3f304a9ade8ab17729fb23b5bd89b007d0b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007949"
---
# <a name="service-description"></a>Descrição do serviço
A descrição do serviço que demonstra como um serviço pode recuperar suas informações de descrição de serviço em tempo de execução. O exemplo se baseia a [guia de Introdução](../../../../docs/framework/wcf/samples/getting-started-sample.md), com uma operação de serviço adicional definida para retornar informações descritivas sobre o serviço. As informações retornadas listam os endereços base e os pontos de extremidade para o serviço. O serviço fornece essas informações usando o <xref:System.ServiceModel.OperationContext>, <xref:System.ServiceModel.ServiceHost>, e <xref:System.ServiceModel.Description.ServiceDescription> classes.  
  
 Neste exemplo, o cliente é um aplicativo de console (.exe) e o serviço é hospedado pelo Internet Information Services (IIS).  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Este exemplo tem uma versão modificada do contrato de calculadora chamado `IServiceDescriptionCalculator`. O contrato define uma operação de serviço adicional denominada `GetServiceDescriptionInfo` que retorna uma cadeia de caracteres de várias linha para o cliente que descreve o endereço base endereços e ponto de extremidade de serviço ou pontos de extremidade para o serviço.  
  
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
  
 O código de implementação para `GetServiceDescriptionInfo` usa o <xref:System.ServiceModel.Description.ServiceDescription> para listar os pontos de extremidade de serviço. Como os pontos de extremidade de serviço podem ter endereços relativos, ele primeiro lista os endereços base para o serviço. Para obter todas essas informações, o código obtém seu contexto de operação usando <xref:System.ServiceModel.OperationContext.Current%2A>. O <xref:System.ServiceModel.ServiceHost> e seu <xref:System.ServiceModel.Description.ServiceDescription> objeto são recuperados do contexto da operação. Para listar os pontos de extremidade de base para o serviço, o código itera por meio do host de serviço <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A> coleção. Para listar os pontos de extremidade de serviço para o serviço, o código itera pela coleção de pontos de extremidade da descrição do serviço.  
  
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
  
 Quando você executar o exemplo, você verá as operações de Calculadora e, em seguida, as informações de serviço retornado pelo `GetServiceDescriptionInfo` operação. Pressione ENTER na janela do cliente para desligar o cliente.  
  
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
  
1. Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ServiceDescription`  
